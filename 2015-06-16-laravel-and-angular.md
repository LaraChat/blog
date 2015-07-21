---
title: Laravel Backend with or without Angular.JS Front End
categories:
  - Tutorials
---
<p>[=I was initially hesitant to post this little tutorial as it's kind of outdated but folks in LaraChat keep asking me about using Angular and Laravel together so here it is for everyone! Do keep in mind that this was written last year before Laravel 5 was released and is out of date. The syntax can easily be modernized. Note: blade syntax has changed from <code>{{ }}</code> to <code>{!! !!}</code> with Laravel 5 and no longer needs to be escaped.=]</p>  

<p>There are not many set practices regarding model validation and Laravel so we will have to roll our own. I think that validation should be handled by the model in order to adhere to the ideals of the MVC architecture that Laravel uses.</p>

<p>Putting a private array in the model class containing validation rules and creating an isValid method is one handy way to do this. As an example here is a simple model for a blog post.</p>

<i>Example of Simple Model with Validation</i>

<pre>
class Posts extends Eloquent {
    // Table that this Post data model reads from and writes to
    protected   $table = 'Posts';
    // Which fields/properties of the table allow mass assignment
    protected   $fillable = [ 'title', 'category', 'content' ];
    // Any errors that occurred during the model's validation
    public      $errors;
    // Validation rules for the Post model
    private     $rules = array(
        'create'=> [
            'title'=>'required|unique:Posts',
            'category'=>'required',
            'content'=>'required',
        ],
        'update'=>[
            ... some other rules ...
        ]
    );

    /**
     * Checks whether or not post data for a model is valid according to the model rules.
     *
     * @returns boolean
     */
    public function isValid($scenario)
    {
        $validator = Validator::make( $this->attributes, $this->rules[$scenario] );
        if( $validator->passes() )
            return true;
        $this->errors = $validator->messages();
        return false;
    }
}
</pre>

<p>With the model setup as such it is easy to perform validation from the controller for a view response or for an API. As an example for both I will use the store method which is called with a post request to make a new Post record.
Controller Validation for View Responses</p>

<pre>
/**
 * Stores a newly created post from the create form.
 * @return Response
 */
public function store()
{
    // Store the input from the post request
    $input = Input::all();
    // Use mass assignment to fill the Post model and check if it is valid or not
    if( !$this->post->fill($input)->isValid() ) 
        // If it is not valid, redirect the user back to the form with errors
        return Redirect::back()->withInput()->withErrors($this->post->errors); 
    // Setup a slug for the url based on the title attribute and save the blog post
    $this->post->slug = $this->post->slugify($input['title']);
    $this->post->save();
 
    // Show the newly created blog post
    return View::make('blog.show', array('post'=>$this->post));
}
</pre>

<i>Validating in the Controller for JSON API Responses</i>


<pre>
/**
 * Store a newly created resource in storage.
 *
 * @return Response
 */
public function store()
{
    // Store the input from the post request
    $input = Input::all();
 
    // Use mass assignment to fill the Post model and check if it is valid or not
    if( !$this->post->fill($input)->isValid() )
        // If it is not valid, return a 400 response with the errors as JSON
        return Response::json($this->post->errors, 400);
 
    // Setup a slug for the url based on the title attribute and save the blog post
    $this->post->slug = $this->post->slugify($input['title']);
    $this->post->save();
 
    // Return a redirect url as JSON (Or the new blog post if you wish) with status 201 Resource Created
    return Response::json(array('redirectUrl'=>'/blog/'.$this->post->slug), 201);
}
</pre>

<p>Responding to the JSON API response with Angular.JS is quite simple. If you try to post to the first example from Angular.js the Post will be created but not much else will happen because a fully rendered view is not useful to Angular.JS.</p>

<p>If your app is fully rendered HTML on the front end use the first example. If you are using Angular you will have to receive a JSON API response and react based on the HTML status codes of the response as such in your javascript:</p>

<i>Responding to the API Response from an Angular.JS Controller</i>


<pre>
app.controller('CreatePostController', ['$http', '$window', function($http, $window) {
    var self = this;
    // Initialize a controller property to hold the post
    this.post = {};
    // And a property for the errors
    this.errors = {};
 
    // This function will be called when the form is submitted and makes the POST request to the API
    this.makePost = function() {
        // POST the blog post to the Laravel API
        $http.post('/api/blog', self.post).
        success(function(data, status, headers, config) {
            // When a successful response is received, redirect to the returned url
            $window.location.href = data.redirectUrl;
        }).
        error(function(data, status, headers, config) {
            // When an error response is received set the errors property to the JSON received
            self.errors = data;
        });
    };
} ]);
</pre>

<p>Note that this is a blade view, so in order for Angular.JS' <code>{{ }}</code> to render they need to be escaped with <code>@{{ }}</code></p>

<i>The Angular View for Creating a Post</i>

<pre>&lt;form name="postForm"&gt;
   &lt;div&gt;
       &lt;label for="post-title"&gt;Title:&lt;/label&gt;
       &lt;input id="post-title" ng-model="create.post.title" /&gt;
       &lt;!-- Only show the errors if they exist, if not, then don't render the error label --&gt;
       &lt;label ng-show="create.errors.title.length"&gt;@{{ create.errors.title }}&lt;/label&gt;
   &lt;/div&gt;
   &lt;div&gt;
       &lt;label for="post-category"&gt;Category:&lt;/label&gt;
       &lt;input id="post-category" ng-model="create.post.category" /&gt;
       &lt;label ng-show="create.errors.category.length"&gt;@{{ create.errors.category }}&lt;/label&gt;
    &lt;/div&gt;
    &lt;div&gt;
        &lt;label for="post-content"&gt;Content:&lt;/label&gt;
        &lt;textarea id="post-content" ng-model="create.post.content"&gt;&lt;/textarea&gt;
        &lt;label ng-show="create.errors.content.length"&gt;@{{ create.errors.content }}&lt;/label&gt;
    &lt;/div&gt;
 
    &lt;!-- When the submit button is clicked, call the controller method makePost to POST to the API for storage --&gt;
    &lt;input type="submit" value="submit" ng-click="create.makePost()" /&gt;
 
    &lt;!-- Show a live preview of the data as it is being typed so the user knows how it is to be displayed --&gt;
    &lt;blockquote&gt;
        &lt;b&gt;@{{ create.post.title }}&lt;/b&gt;
        @{{ create.post.category }}&lt;br /&gt;
        &lt;!-- Trusted is a custom filter that marks HTML as safe to render. This is actually really unsafe but is pulled from a demo. --&gt;
        &lt;div ng-bind-html="create.post.content | trusted"&gt;&lt;/div&gt;
    &lt;/blockquote&gt;
&lt;/form&gt;
</pre>