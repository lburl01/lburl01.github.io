---
layout: post
title: "OMG Halfway"
date: 2016-10-17
---
<hr>
<h4>Week 6 | Sometime in October...</h4>
<p><strong>Panic Level:</strong> 5 out of 6</p>
<hr>

Wow. Halfway. I'm not surprised that I've made it this far, but it's still surreal to think about. The days blur together and remembering what day of the week it is takes an absurdly long period of time for me to decipher.

I've begun looking for jobs and researching companies in the area. I've started networking more (Yay, Meetups and thank goodness for the wonderfully giving alumni and the time they offer to me) and narrowing in on the things I might prioritize when looking for a job. (But, let's be honest, I need and desperately want a job, so I'm not preparing to be picky.)

Now, prepare yourself; this will be a long post!

### Introducing Rails

This last week we started Rails. To be honest, I had mixed feelings about that. Our instructor is the type who likes balancing control and effort - I think I'm the same way. To explain, there are multiple frameworks for the Ruby language. So far, our class has explored the Sinatra framework. It's made it really easy to create our homemade APIs but it doesn't do a lot of heavy-lifting for us the way that Rails does. We have to manually add our models, views, and controllers. We have to manually generate our migrations and schema. What I learned this week is that Rails has a way of generating those files for me.

Where before, with Sinatra, I had to manually create and edit my controller (the file that links my database to what the user may see on the webpage). Now, with Rails, I can run the command:
```bash
$ rails generate controller Users show create
```
And I would get a controller file called UsersController.rb and it would have the methods show and create pre-populated for me in that file.

So fancy! But also, what the heck is happening under the covers to make that happen? That is the biggest difference between Rails and Sinatra that I've seen. Pros? Super fast to create a website with lots of functionality. This is one of the reasons why I've heard many startups utilize Rails - you can create a whole website in, like, 10 minutes. But with that comes a sacrifice of not necessarily knowing what all was added to your files/program and you may have to go customize multiple parts of your website.

Trade-offs exist with everything and this is just one example.

In general, though, I'm really glad we spent "so much" time on Sinatra because at least I partially understand what Rails is doing if I choose to run rails generate. Hopefully it will be make me all the stronger as a programmer to have spent the sweat and tears on manually doing what Rails accomplishes "automagically" for us.

### Another Group Project

To finish off the week, we had another group project with the Front End Engineering class. Super fun! It's always nerve-wracking to start a new project with teammates I haven't worked with before but I think my project management experience from my past life at the Museum really helps us get started on the right foot.

Our assignment was to create a game for an end user to play and the requirements of the program were that users could log in/out, have a user profile page, ability to edit the user's own information, and then we'd have a leaderboard of all users' scores compared against one another. My team ended up going with a game called Ph.Drinks. It was a mixology game where we had 20 drinks, each with 3 ingredients, and the user has to match the three ingredients out of 33 ingredient choices, with each drink. A game was five drinks long.

To make this happen, the database was quite complicated for me to figure out. It had a bit of logic I hadn't used before, so I ended up spending a day and a half just getting the database set up in what I thought was the best way. I used postgresql as my database and ended up having quite a few tables
* Users
  * Email address, password, and some columns keeping track of when a user is added, when they update their account, and more
* Drinks
  * Name of each drink with a unique id (in this case numbers 1-20)
* Ingredients
  * Name of each ingredient with a unique id
* Mixed Drinks  
  * Unique id, drink_id (the id of each drink from the Drinks table), ingredient_id (the id from the Ingredients table)
  * Setting up this joined table allowed me to assign a single ingredient to multiple drinks (whisky can be in more than one drink).
* Games
  * This was the most difficult table to figure out because there are lots of ways to accomplish what I was looking for. My two main goals were to associate a user with a set of 5 drinks AND the user's score for each drink and secondly I needed to be able to add the scores from that game of 5 drinks to a total score for the user. I hit a few interesting snags with this that I will explain below.
  * Unique game id, user_id (from Users table), session (a number I generated that I'll talk about later), a correct? column (stores a 1 or a 0 depending on if you got the drink correct or not), and timestamps.

So, let's talk a little more about my Games table. Because there are a few things I was proud of making happen the way I'd set out - despite being more complicated than I'd hoped for!

**Correctly Generated Session Number**

So, thing number one I was super proud of devising was a way to generate a sequential "session" that could be applied to our five drinks. I did not set that session column in the table to be automatically generated, so I needed to pass in the right number that drinks 1-5 for user 1 were all part of session 3. I needed to be able to have user 1 play another game that had session 4 for a set of five drinks.

To do this I basically took the maximum number in the session column for a user and then incremented it by 1. Then I passed that session number to my Front End friends who basically "saved" that number and then passed it back with each post we did to save the user's five drinks and scores with the same session on each of the five drinks. Does that make sense to anyone but me?!
