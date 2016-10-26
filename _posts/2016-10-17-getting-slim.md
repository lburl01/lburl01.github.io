---
layout: post
title: "Getting Slim"
date: 2016-10-17
---

<hr>
<h4>Uh, weeks in October that I've already lost track of</h4>
<p><strong>Panic Level:</strong> 4-5 out of 6</p>
<hr>

**It's week 5, y'all!**

Okay, so, I'm halfway through the program as I write this blog post. It was a crazy weekend for our bridge project between week 5 and 6. Basically we had to take everything we've learned, focus on our weaknesses, and, oh yeah, let's research and test out these 10+ new concepts that we'll need for Rails.

It was quite a learning experience and one that proved worthy enough for me to post about.

So, what are my current weaknesses and what new challenges did I take on?
* TDD (or test-driven development)
  * I quite enjoy testing, to be honest. Yes, it can be time-consuming (twice the code for the same output?!) but it's so valuable, especially when setting your app up. I've not exactly avoided TDD but I have just let it slide compared to the other requirements on projects. So this weekend was all about testing. And I succeeded! I used <a class="post-link" href="http://jnicklas.github.io/capybara/">Capybara</a> to help automate some of my form inputs and traveling between pages and used RSPEC for some testing on my models.
    * Capybara wins: I got it to work! I did automated testing. It was great and I definitely saved a lot of time and effort by running those automated tests.
    * Capybara struggles: I spend so.much.time just getting Capybara to work. Setting up my testing environment was super difficult. I'm going to chalk that up to getting more practice integrating Capybara into a project. In the end, thanks to who knows how many articles, I succeeded in automated testing with Capybara. (For future me: To get Capybara to work, I ended up wiping my spec_helper and replacing it with pretty much the straight code from Capybara's github. And then it worked and I moved on and forgot about those struggles!)
* Slim
  * <a class="post-link" href="http://slim-lang.com/">Slim</a> is "a lightweight templating engine" like ERB or HAML, but different (duh). As a native html-er, it was an adjustment to not close tags and have whitespace matter. But also SO NICE! I mean, typing up my html pages was way faster using Slim compared with regular 'ol html. But I had issues...oh, I ran into lots of problems. And apparently there's a framework for php called slim so documentation and reporting on slim was a bit interesting to find.
  * Slim Wins:
    * I got a page to render and use my slim template instead of an html page! What?! That alone was awesome. It took a simple line in my api file that looked something like this:
    ```rb
    slim :home
    # or in the case of nested file structures in my views folder - which was super hard to find:
    slim :'users/home'
    ```
    * I could print multiple ruby items dynamically depending upon my api call. So, in my weekend project, I wanted to print a new paragraph that contained the contents of each item of my row. So if I had one item, print just one item magically out of thin air. Then, if I had three items, print three items! What?! Yes, that's a thing. Programming is awesome. So, I had previously known how to do this with javascript and ajax, but the slim docs noted that you could do the same thing just with slim. So I made it happen. And it was great. There was a huge caveat that made me undo some of that work that I'll talk about below.
  * Slim Struggles: Slim and Javascript did not talk very well. Slim accommodates in-page javascript, but I rode the struggle bus on printing items to the page dynamically with Slim/Ruby and then accessing those items with javascript. I ended up scrapping the dynamic printing in Slim for doing that with Javascript.

**Resources I Loved**
* <a class="post-link" href="https://code.tutsplus.com/articles/an-introduction-to-slim-templates--cms-26028">Tutsplus "An Introduction to Slim Templates"</a>
  * <a class="post-link" href="https://code.tutsplus.com/articles/ruby-templating-with-slim-part-2--cms-26094">Part Two</a>
