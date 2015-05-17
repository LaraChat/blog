---
title: Developer Stories - CachetHQ
categories:
  - Stories
---
<p>
    [=What makes the Laravel community so great is the people. In an ongoing series of blog posts we will be talking about some of the fantastic products the people are creating.
</p>
<p>
    For our first Developer Story, we are featuring Cachet and the creator James Brooks.=]
</p>
<p>
   <h5>Tell us a bit about your development background and your favourite languages/tools.</h5>
   <ul>
        <li>
            <p>Development has always been a big part of my life, probably because I've been writing code since I was 7 (I'm now 23). During this time I've been freelancing between school, college and full time employment. A few years back I worked as a VB6 programmer (and support technician) writing EPOS software. I've now spent the last four years working as Lead Web Developer which is so much fun for me!</p>

            <p>My favourite languages are PHP (but only when I'm using Laravel), JavaScript and Python.</p>

            <p>On a daily basis you'd see me use:</p>

            <ul>
                <li><a href="http://www.sublimetext.com/3" target="_blank">Sublime Text 3</a> <em>(fun fact, I picked up the net mag award for them last May)</em></li>
                <li><a href="http://www.sequelpro.com" target="_blank">Sequel Pro</a></li>
                <li><a href="http://airmailapp.com" target="_blank">Airmail 2</a></li>
                <li><a href="http://www.google.com/chrome/" target="_blank">Google Chrome</a></li>
                <li><a href="https://slack.com" target="_blank">Slack</a></li>
                <li><a href="https://www.wunderlist.com" target="_blank">Wunderlist</a></li>
                <li><a href="https://itunes.apple.com/ca/app/paw-http-rest-client/id584653203?mt=12" target="_blank">Paw</a></li>
                <li><a href="http://panic.com/transmit/" target="_blank">Transmit</a> </li>
                <li><a href="https://github.com" target="_blank">GitHub</a> </li>
            </ul>
        </li>
    </ul>

    <h5>What is the one tool that you cannot live without?</h5>
    <ul>
        <li>
            <p>Sublime Text. I've tried so many other editors but I just cannot leave Sublime because it makes me 100 times more productive.</p>
        </li>
    </ul>

    <h5>Tell us about Cachet</h5>
    <ul>
        <li>
            <p>Cachet is an open source status page system. It's beautiful on the inside and out. Currently it speaks in three languages, but it's learning more all of the time. We've had over 3000 clones from GitHub. It can be deployed to Heroku with the Heroku Button. Two clicks and you're done. Cachet supports MySQL, SQLite and PostgreSQL. And so much more...</p>
        </li>
    </ul>

    <h5>What inspired you to develop Cachet?</h5>
    <ul>
        <li>
            <p>I was working on one of my many projects and realised I'd need some way to update customers that a part (or all) of it had gone down. I'd spent some time looking through a few services but they were all so expensive - at least for a hobby project. Being a developer my first thought was "wait a second... I'm a developer, I'll make my own." - so I did.</p>
        </li>
    </ul>

    <h5>What was the hardest part of developing Cachet?</h5>
    <ul>
        <li>
            <p>Honestly thinking that everybody would laugh at the code and me. Completely the opposite happened though and I'm so happy that I released it for everybody to use.</p>
            <p>Specific to Cachet though it'd probably have to be supporting multiple database drivers. Although Eloquent does amazing work, we had one problem where the migrations declared a field with default(0) and if that field was left empty after submitting a form it'd throw a fit. That's when I learnt about the really useful $attributes property on models - thanks Laravel! The <code>$attributes</code> property allows you to define default fields on your model which Eloquent will insert into the database within your query, this is great for when you support different drivers such as PgSQL which won't set the default value at query execution time - Laravel saves the day.</p>
            <p>Also on par with that was fully supporting Heroku's one click deploy. We've had to fork a buildpack and get it working just the way we need it.</p>
        </li>
    </ul>

    <h5>What was your favourite commit to the Cachet repo?</h5>
    <ul>
        <li>
            <p>This is a tough question. There has been several awesome commits, most recently by Graham Campbell and Joe Cohen, but if I think of it as the pinnacle moment for Cachet, it'd be when Graham refactored to use PSR-4 and all the good stuff I hadn't done. I learnt a lot that day.</p>
        </li>
    </ul>

    <h5>What can you tell us about the future of Cachet?</h5>
    <ul>
        <li>
            <p>Right now I can tell you a few things but there is a lot more to come in the future.</p>
            <ol>
                <li>We're nearing a solid V1 release. </li>
                <li>We'll be bringing Cachet to even more languages.</li>
                <li>Once we've reached V1 we'll be working with Taylor to get Cachet as an application on Forge.</li>
            </ol>
            <p>If you want to keep up to date with all of Cachet's news then you should absolutely check out our <a href="https://cachethq.us9.list-manage.com/subscribe/post?u=654f358550ef074d6601475cd&amp;id=711cf8b66d" target="_blank">newsletter</a>.</p>
        </li>
    </ul>

    <h5>What is your favourite Slack channel and why is it <a href="http://larachat.co/" target="_blank">LaraChat</a>?</h5>
    <ul>
        <li>
            <p>The channel is made up of really nice, friendly people. It's been really nice to be part of a collective where everyone has such mutual respect for each other.</p>
            <hr>
            <p>Check out Cachet at it's <a href="https://github.com/cachethq/Cachet" target="_blank">GitHub Repo</a> or check out the <a href="https://cachethq.io/" target="_blank">CachetHQ</a> website for more information. Follow <a href="https://twitter.com/jbrooksuk" target="_blank">James on Twitter</a>) to find out more about his awesomeness, ask him about it, he'll tell you!</p>
        </li>
    </ul>
</p>