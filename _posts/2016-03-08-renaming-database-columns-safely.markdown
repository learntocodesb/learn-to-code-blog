---
layout: post
title: Renaming Database Columns Safely
author: Max Helmetag
author_github: mhelmetag
date: 2016-03-08 22:55:41 -0800
categories:
---

## My Big Break
I had always wanted to break into contributing code and I finally found some low hanging fruit on [Exercism](https://github.com/exercism/exercism.io). I made a small change, got some feedback and "squashed" my commits. Soon after, I wanted a bit larger of a project to work on so I found [this issue](https://github.com/exercism/exercism.io/issues/2501).

The task seemed fairly straightforward:

* Rename a database column called `mastery` to `track_mentor`. A
* Add a route (kind of like a controller and a route in Rails but... Sinatra).
* Build some frontend interface for users to invite each other to this track mentor thing.

So I thought, "Let's make a lot of these changes all at once!" Rename the column, change all the references of `mastery` to `track_mentor` and go from there!


## Uptime
Max (me):

>I changed the column mastery to track mentor, updated some tests and created a migration. All tests passed locally after db:migrate. I think this is a good jump off point. Let me know what you think :)

Katrina (Exercism creator):

>At the moment, if we deploy this change, then there is a bit of time between when the site is deployed and the migration finishes running where queries and methods are referencing a field that doesn't exist. I'd rather not have to take the site down for maintenance if we can avoid it.

**Note: If there's one reason to contribute to projects on GitHub, it's the code review.**

Oh, okay... so in other words... let's not do that...


## Production
I never really thought of the word "migration" until I worked on Exercism. I always just thought of it as "change". While that's not wrong, it's also not entirely right (at least not in a production environment).

On my own projects, whenever I make changes I usually nuke my database, run my migrations and reseed. I don't ever think twice about preserving data... see why that won't work in production?

So what's the solution?

At first I was thinking of a simple migration:
{% highlight ruby %}
def change
  rename_column :users, :mastery, :track_mentor
end
{% endhighlight %}

So if that won't work... then what?
Create a new `track_mentor` column and copy all of the `mastery` data with a rake task:
{% highlight ruby %}
# migration
def change
  add_column :users, :track_mentor, :text
end

# user
serialize :mastery, Array
serialize :track_mentor, Array

# rake
desc "migrate info from mastery to track mentor"
task :track_mentor do
  require 'bundler'
  Bundler.require
  require_relative '../exercism'

  User.update_all("track_mentor=mastery")
end
{% endhighlight %}

After running that migration and copying the data from one column to the other, I was finally able to make the code changes to reference my newly minted `track_mentor` column!

# So?
Well... so nothing. I'm just saying that even the simplest things are usually more complex. After further reading about migrations and hearing about [feature flags](http://martinfowler.com/bliki/FeatureToggle.html), I started thinking about incremental changes in other places throughout the codebase.

It seems like with all the focus on agile and continuous integration, web development is moving in the direction of merging small experiments into production. It definitely makes testing easier by seeing how new changes work in the wild incrementally versus all in one heap (so there's less code to sift through when things break) and real users are some of the best test cases around (no mocking required!).
