---
title: Developer Stories - Toby Zerner (Flarum)
categories:
  - Stories
---
<img src="https://pbs.twimg.com/profile_images/596302747235799040/ARPWrCfi_400x400.jpg" />
<p>
    [=What makes the Laravel community so great is the people. In an ongoing series of blog posts we will be talking about some of the fantastic products the people are creating.
</p>
<p>
    Today, we are featuring Flarum and the creator Toby Zerner.=]
</p>
<p>
  <h5>Tell us a bit about your development background and your favourite languages/tools.</h5>
   <ul>
        <li>
            <p>I’m a 22-year-old medical student doing web development on the side. My brother taught me PHP at a young age as we worked on a bunch of projects together — video game fan-sites, forums, client work. Since then I’ve kept up a healthy interest in web dev and forum software.</p>
        
            <p>I discovered Laravel in its infancy (version 2) years ago and immediately fell in love. It’s been one of my favourite tools since, and I’ve enjoyed being able to watch it grow and learn about good software design from it. More recently I dove into front-end JavaScript frameworks like <a href="http://emberjs.com" target="_blank">Ember.js</a> and <a href="http://mithril.js.org" target="_blank">Mithril</a>, and I think I love them even more! They make it incredibly easy to create amazing user experiences, a process which I find very rewarding.</p>
        </li>
    </ul>
</p>

<p>
  <h5>What is the one tool that you cannot live without?</h5>
   <ul>
        <li>
          <p><a href="http://www.alfredapp.com/" target="_blank">Alfred for Mac</a>. I use it to launch apps, files, open URLs, Google stuff, etc. I love how powerful its workflows feature is: I can quickly find Font Awesome icons, generate lorem ipsum text, open ssh connections, and search Dash docs. Even cooler, I have a custom workflow which launches my Flarum development environment — open the Sublime project, vagrant up, gulp watch, and open Chrome and Postman — all in one key press. Honestly, I can’t imagine how inefficient I’d be without it!</p>
        </li>
    </ul>
</p>

<p>
  <h5>Tell us about Flarum</h5>
   <ul>
        <li>
          <p><a href="http://flarum.org" target="_blank">Flarum</a> is modern forum software, powered by Laravel. The goal is to make it simple and extensible, so any average Joe can set up a discussion forum for their website/team/company/class, and then scale it and customise it really easily. It's fast, has a beautiful UI, and it's being built from the ground up with an open API. Developers will be able to create and sell “extensions” which let forum admins add community-specific features (things like user rankings, polls, Q&A, themes), without making the core software clunky and bloated.</p>
          
          <p>Flarum is <a href="http://github.com/flarum/core" target="_blank">open-source</a> under the MIT license and there’s an early-stage live demo which you can check out at <a href="http://demo.flarum.org" target="_blank">http://demo.flarum.org</a>.</p>
        </li>
    </ul>
</p>

<p>
  <h5>What inspired you to develop Flarum?</h5>
   <ul>
        <li>
          <p>Forum software sucks — especially in PHP land — and I want to do something about it. I grew up running a few video game fan-sites which involved setting up and administrating community forums. The available software was bloated and frustrating and I hated using it. Ten years later and nothing’s really changed: The big names which power most forums (phpBB, IP.Board, vBulletin) have slowly evolved, but they haven’t innovated, and they’re still clunky and complicated. No one really wants to use these kinds of forums anymore, especially when they can have a much more pleasant time broadcasting themselves on social media.</p>
          
          <p>On the other hand, I’ve always liked the in-depth conversational format and the rich, niche sense of community that forums create. I want to make that accessible, engaging, and actually feel good for users. So I've spent the last few years iterating on forum software for fun by making <a href="http://esotalk.org" target="_blank">esoTalk</a>. Its popularity (in spite of its flaws) tells me that other people see the value in forums, and that there’s still a lot of room for better forum software.</p>
        </li>
    </ul>
</p>

<p>
  <h5>What was the hardest part of developing Flarum?</h5>
   <ul>
        <li>
          <p>1. Finding the right JavaScript framework. I had never had any experience with JavaScript frameworks until I dove into Ember. Ember seemed like a good choice for Flarum, and through a steep learning curve I was able to build a fully-functional front-end for Flarum. But eventually we ran into <a href="http://discuss.flarum.org/139-introducing-flarum-s-fast-new-front-end/p1#p347" target="_blank">some problems</a> with Ember and <a href="http://tobyzerner.com/mithril" target="_blank">started over</a> with a much more lightweight framework called Mithril. It set us back a few weeks but I definitely think it was a good decision!</p>
          <p>2. Finding the right compromise between the Active Record and Repository patterns. I’ve struggled with this for so long, and I still am somewhat. I love the theory behind the Repository pattern (separating the persistence layer), but I hate the idea of losing Eloquent’s magical goodness. With Flarum, there’s also the consideration of making things easy enough for potential extension authors who don’t necessarily want to spend hours crafting a rock solid domain layer. So in the end, I’ve opted to use “repositories” purely as classes that encapsulate data fetching queries (for testability), and use Active Record everywhere else.</p>
        </li>
    </ul>
</p>

<p>
  <h5>What can you tell us about the future of Flarum?</h5>
   <ul>
        <li>
          <p>It’s bright! I’m taking a year off from my uni course to work full-time on Flarum, and I've teamed together with the FluxBB developer, Franz Liedke. We're hoping to have a beta out in July, and then build a great ecosystem of extensions. I wrote a <a href="http://tobyzerner.com/flarum" target="_blank">blog post</a> with more detail about what's ahead.</p>
        </li>
    </ul>
</p>

<p>
  <h5>What is the best Twitter account to follow and why is it @LaraChatSlack?</h5>
   <ul>
        <li>
          <p><a href="http://twitter.com/LaraChatSlack" target="_blank">@LaraChatSlack</a> is definitely *the best* Twitter account to follow. It will change your perspective on life and make you an overall better person. By some unexplainable quantum phenomenon, <a href="http://twitter.com/Flarum" target="_blank">@Flarum</a> is also definitely *the best* Twitter account to follow. It has similar magical properties which scientists have thus far been unable to explain.</p>
        </li>
    </ul>
</p>
