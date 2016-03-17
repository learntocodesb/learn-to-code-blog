---
layout: post
title: Adding A Favicon to the Blog
author: John Magee
author_github: jemagee
categories:
---

Max generously set up this Jekyll blog as a way for members of our Learn To Code Meetup of all levels to contribute to an open source project easily, which is great, so I'm going to not only undertake one of the issues Max set up, but walk through the steps involved for those who might have little to no experience with contributing to a Github project.  I'm going to go painstakingly step-by-step, to make sure users of all Github experience can (hopefully) follow along.

### Presumptions

* You have a github account already.  If you do not, [Sign Up Now](http://www.github.com).  It's quick, easy, and painless, and you don't have to do anything yet.
* You have set up your SSH keys.  I, personally, am dangerous enough on the command line to install homebrew packages, gems, and follow specific instructions to do things.  Github helpfully provides a [tutorial](https://help.github.com/articles/generating-an-ssh-key/) for both Mac and Windows.  There are other ways to set up keys obviously and you're free to use them, but I used this to set up my keys (I have two keys because I use two separate computers with github) and it worked out swimmingly, so if this works for you, I'd just use it.
* Your development environment is set up with Ruby, a way to switch between versions of ruby, and rubygems already installed.  If these aren't installed, I think, in the future, we will set up a static page that provides links to setting up various development environments.
* You have a little bit of knowledge of github.  If you haven't yet, you should at least complete this [basic tutorial](https://try.github.io/levels/1/challenges/1), which doesn't take too long, and introduces you to the loveable octocat.

## Step 1 - **Fork** the repository.

Before you can work on any project, you, ideally, will put a resident **copy** on your computer.  This is done by forking the repository (repo, git hub page) of the project you want to work on.  

To fork this blog, make sure you are already logged into Github and [go to the repo](https://github.com/learntocodesb/learn-to-code-blog) for the blog.  In the upper right hand corner of the window you should see a button that says *Fork*.  It will have an icon to the left of it and perhaps a number to the right of it (which indicates I presume the existing forks.  I'm not a github expert, but that makes sense).  Click that button. Your screen should change and you should see an animation that is sort of like a copier machine.  This is github creating the fork of the repository.  This shouldn't take too long and after it's done your screen will change and look **almost** exactly the same.  If you look at the top left of the screen you will now see that the page says **your_git_name/learn-to-code-blog**, and underneath it in smaller letters it will say **forked from learndtocodesb/learn-to-code-blog**.  

Congratulations, you have forked the repo.  I bet you think you can start working now huh?  Sorry, not quite yet, there's just a little more work to do before we can get started.

## Step 2 - **Clone** your fork.

Yes, you can edit files on github if you really want to (as long as it's your repository or a repository you have that permission on), but you really dont' want to do you?  In the long run, with practice and experience, changes you make will possibly need to be tested as well, and the code you'll write will be more useful done on your machine in your favorite text editor. (Personally, on my macs, I love me some Sublime Text 2)

Now then, remember that page in your github from the end of step one, and the fact that we are working with the ssh keys?  That's good, cause that's where this comes in handy now.

About 1/3 of the way down that page of your fork, you'll see a variety of buttons that end a button that says either HTTPS or SSH with a drop down arrow indicating you can change it.  As I said earlier, I'm going to run this through the SSH version, you can use the HTTPS version if you want, the steps are pretty much the same.

So, at this point you may be saying to yourself, but John (cause that's my name, right?) if they're pretty much the same, why does it matter which we use.  Now, like I said above, I am not github expert, but from conversations with people who are much more experienced with github (and smarter) than me, I believe the difference boils down to this.  If you use the **HTTPS** option, you will have to provide credentials every time you push (and perhaps pull?) to and from your repository.  The **SSH** setup serves to identify your computer to github automatically so you are authenticated without having to do anything.  (If I'm wrong, I'm sorry, someone else edit this and correct me please)

Ok, enough stalling, it's time to clone your fork.

1.  Next to that HTTPS/SSH button is a field with text that starts out https::/github or git@github.com.  Click in that field and copy the text
2.  Open your **Terminal** program.  On my mac, it's named terminal.
3.  Navigate to the folder you wish your forked project to reside in.
4.  Type `git clone [paste copied text here]` and hit return.

At this point you'll see some messages on your screen that starts with `Cloning into 'learn-to-code-blog', followed by some lines that indicate that the fork is being downloaded and copied onto your machine.  

That's it, your fork has now been cloned (copied as it were) onto your machine, and you're almost ready to get started.  Yeah, that's right, I said almost right.

## Step 3 - Set up your clone to be worked with.

Your Jekyll blog is dependent on Gems.  These gems need to be installed into your local folder where you Jekyll blog copy is stored.  I know it seems daunting to have to install all those Gems, but I promise it isn't.

1.  Type `cd learn-to-code-blog' and hit enter.  That's right, your clone came down from the heavens (or Github) as its own folder.  Wasn't that nice of it?
2.  Type `bundle` and hit enter.  You should see a list of Gems being installed.  Some you might have heard of, and some not, that's ok.  

Now, you might recieve an error that says `Your Ruby version is x.x.x but your Gemfile specificed 2.3.0'.  This is an easy fix assuming your version manager (rbenv or rvm) are installed. 

* rbenv - type `rbenv local 2.3.0'.  This means the folder you are currently in will use ruby 2.3.0.  I do it this way in case other folders I have are using different versions of ruby (and they are, because you may work on other projects that are behind or ahead of this one in their ruby usage)
* rvm - type `rvm use 2.3.0', which I thik does the same thing as the rbenv command'.


## Step 4 - Make some changes

Ok, so *now* we are ready to actually work on the Jekyll project itself.  Personally, when I'm working on a project I use my handy dandy `subl .` from the top level folder of the project I want to work on.  This open all the folders/files in Sublime Text so I can easily navigate between all files.  I'm presuming your text editor has something similar.  (Keep in mind I had to set up my Mac to accept subl as a command to open Sublime when I first installed it but that was done by a very good tutorial a few years ago so I'm sorry I can't remember which one)

So, with the idea of keeping the focus on the github function of it all, I won't go through the actual work of what I did, but suffice to say, I found a small graphic that could be used (temporarily) as a favicon because it's one of the two issues set up and I wanted to work on an existing issue.