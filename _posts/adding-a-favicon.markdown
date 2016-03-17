---
layout: post
title: An (overly) detailed explanation of how to submit a Pull Request
author: John Magee
author_github: jemagee
categories:
---

Max generously set up this Jekyll blog as a way for members of our Learn To Code Meetup of all levels to contribute to an open source project easily, which is great, so I'm going to not only undertake one of the issues Max set up, but walk through the steps involved for those who might have little to no experience with contributing to a Github project.  I'm going to go painstakingly step-by-step slow, to make sure users of all levels of Github experience can (hopefully) follow along.

# Presumptions

1.  You have a github account already.  If you do not, [sign up now](http://www.github.com){:target="_blank"}.  It's quick, easy, and painless, I promise.
2.   You have set up your SSH keys.  I, personally, am dangerous enough on the command line to install homebrew packages, gems, and follow specific instructions to do things.  Github helpfully provides a [tutorial](https://help.github.com/articles/generating-an-ssh-key/){:target="_blank"} for both Mac and Windows.  There are other ways to set up keys and I'd use whatever works best for you, but I used this to set up my keys (I have two keys because I use two separate computers with github) and it worked out swimmingly, so if this works for you, I'd just use it.
3.  Your development environment is set up with Ruby, a way to switch between versions of ruby, and rubygems already installed.  If these aren't installed, you can search online how to do this on your computer. (As an aside, I think a 'useful links page' would be helpful for folks and links to solid tutorials could be provided).  You also have to install git on your computer so you can access Github.  As always, there's a [good tutorial](https://help.github.com/articles/set-up-git/){:target="_blank"} that will walk you through the steps to install git on your machine.
4.  You have a little bit of knowledge of Github.  If you haven't yet, you should at least complete this [basic tutorial](https://try.github.io/levels/1/challenges/1){:target="_blank"}, which doesn't take too long, and introduces you to the loveable octocat.
5.  You have to know enough about your specific computer to access the command line and navigate between files which you should be able to do if you completed step 3.  

# TL:DR

I don't generally like the TL:DR concept for my own personal reasons, but this article sort of went long after I finished it (I over explain sometimes) so I wanted to provide a quick summary of what is covered in the following content so that some people can decide to read the whole thing, specific sections, or just research the concepts on their on on the web.  Again, after doing it a few times, this stuff becomes pretty rote and easy to remember, but the first time I tried to get a github respository of my own on a resident machine, I messed it up properly because I didn't understand about cloning a repository (Step 2), and it took Dillon 15 minutes to explain it to me, and he's much smarter than me at this stuff.

1. [Fork the repository](#step1)
2. [Clone the fork](#step2)
3. [Setup the clone](#step3) 
4. [Make Changes](#step4)
5. [Submit a Pull Request](#step5)

### <a name="step1"></a>Step 1 - **Fork** the repository.

Before you can work on any project, you, ideally, will put a resident **copy** on your computer.  This is done by first forking the repository (repo, git hub page) of the project you want to work on.  

To fork this blog, make sure you are already logged into Github and [go to the repo](https://github.com/learntocodesb/learn-to-code-blog){:target="_blank"} for the blog.  In the upper right hand corner of the window you should see a button that says *Fork*.  It will have an icon to the left of it and perhaps a number to the right of it (which indicates I presume the existing forks.  I'm not a Github expert, but that makes sense).  Click that button. Your screen should change and you should see an animation that is sort of like a copier machine.  This is github creating the fork of the repository.  This shouldn't take too long and after it's done your screen will change and look **almost** exactly the same.  If you look at the top left of the screen you will now see that the page says **your_git_name/learn-to-code-blog**, and underneath it in smaller letters it will say **forked from learntocodesb/learn-to-code-blog**.  

Congratulations, you have forked the repo.  I bet you're excited to start making changes aren't you?  Sorry, not quite yet, there's  a little more work to do before we can get started.

### <a name="step2"></a>Step 2 - **Clone** your fork.

Yes, you can edit files on github if you really want to (as long as it's your repository or a repository you have that permission on), but you really don't want to do you?  In the long run, with practice and experience, changes you make will possibly also need to be tested before it will be accepted (that's a whole other issue not to talk about today), and the code you'll write will be more easily done on your machine in your favorite text editor. (Personally, on my macs, I love me some Sublime Text 2)

Now then, remember that page in your github from the end of [step 1](#step1), and the fact that we are working with the ssh keys?  That's good, cause that's where this comes in handy now.

About 1/3 of the way down that page of your fork, you'll see a variety of buttons that end a button that says either HTTPS or SSH with a drop down arrow indicating you can change it.  As I said earlier, I'm going to run this through the SSH version, you can use the HTTPS version if you want, the steps are pretty much the same.

>So, at this point you may be saying to yourself, but John (cause that's my name, right?) if they're pretty much the same, why does it matter which we use.  Now, like I said above, I am not github expert, but from conversations with people who are much more experienced with github (and smarter) than me, I believe the difference boils down to this.  If you use the **HTTPS** option, you will have to provide credentials every time you push (and perhaps pull?) to and from your repository.  The **SSH** setup serves to identify your computer to github automatically so you are authenticated without having to do anything.  (If I'm wrong, I'm sorry, someone else fork the repo, edit this and correct me please)

Ok, enough stalling, it's time to clone your fork.

1.  Next to that HTTPS/SSH button is a field with text that starts out *https://github* or *git@github.com*.  Click in that field and copy the text
2.  Access your command line.  On my Mac I use a creatively named program called **Terminal**
3.  Navigate to the folder you wish your forked project to reside in. 
4.  Type `git clone [paste copied text here]` and hit return.

At this point you'll see some messages on your screen that starts with `Cloning into 'learn-to-code-blog'`, followed by some lines that indicate that the fork is being downloaded and copied onto your machine.  

That's it, your fork has now been cloned (copied as it were) onto your machine, and you're almost ready to get started.  Yeah, that's right, I said almost right.

### <a name="step3"></a>Step 3 - Set up your clone to be worked with.

Your Jekyll blog is dependent on Gems.  These gems need to be installed into your local folder where your Jekyll blog copy is stored.  I know it seems daunting to have to install all those Gems, but I promise it isn't.

1.  Type `cd learn-to-code-blog` and hit enter.  That's right, your clone came down from the heavens (or Github) as its own folder.  Wasn't that nice of it?
2.  Type `bundle` and hit enter.  You should see a list of Gems being installed.  Some you might have heard of, and some not, that's ok.  

Now, you might recieve an error that says `Your Ruby version is x.x.x but your Gemfile specificed 2.3.0'.  This is an easy fix assuming your version manager (rbenv or rvm) are installed. 

* rbenv - type `rbenv local 2.3.0`.  This means the folder you are currently in will use ruby 2.3.0.  I do it this way in case other folders I have are using different versions of ruby (and they are, because you may work on other projects that are behind or ahead of this one in their ruby usage)
* rvm - type `rvm use 2.3.0`, which I think does the same thing as the rbenv command above.


### <a name="step4"></a>Step 4 - Make some changes

Ok, so *now* we are ready to actually work on the Jekyll project itself.  Personally, when I'm working on a project I use my handy dandy `subl .` from the top level folder of the project I want to work on.  This open all the folders/files in Sublime Text so I can easily navigate between all files.  I'm presuming your text editor has something similar.  (Keep in mind I had to set up my Mac to accept subl as a command to open Sublime when I first installed it but that was done by a very good tutorial a few years ago so I'm sorry I can't remember which one)

So, with the idea of keeping the focus on the github function of it all, I won't go through the actual work of what I did, but suffice to say, I found a small graphic that could be used (temporarily) as a favicon because it's one of the two issues set up and I wanted to work on an existing issue.

And, after taking more time than I'd care to admit since I never set up a favicon before, I had my change made. (Ok Ok, I'll give you a hint.  It took more than 3,600 seconds but less than 7,200.)

### <a name="step5"></a> Step 5 - Commit your changes

So, this is pretty standard github stuff with one added thing if you've never worked with a cloned repository before.

1.  git add .
2.  git commit -m "Commit Message that indicates what you're commiting"
3.  git push 

If `git push` is new to you, the simple explanation, based on my understanding, is this.  When you cloned your forked repository in Step 2, you created a 'link' between your local copy and the copy on Github.  If you don't believe me type `git remote -v` in the local folder for the blog and see what returns.  You'll see a push and a fetch but we're just working with push for now.

Now, if this is your own project you're working on, git push should be relatively simple.  However, if you're working on a group project and try to push to something someone else changed, Github will probably alert you and ask you to deal with it (I'm guessing, cause Github is smart that way and that's why people use it, so that conflicting code is dealt with and not just erased when someone else submits a change.)

Ok, so now you've made your super duper change and you want to check it out on the blog.  Ok, that's very cool, but you gotta do one more thing.

### <a name="step5"></a>Step 5 - Make A Pull request.

Remember, the changes you made are not to the original blog, but your forked copy of the blog.  You have to get your changes merged with the original blog, but github makes sure that there is a process that prevents you from overriding any changes made by others in the mean time (your fork is a 'forked copy' of the original project at the time you forked it, other changes may be made to the project while you're working on yours), and prevents you from doing anything disastorous to someone else's code.  If you've been to graduate school, consider the Pull request a 'peer review' of the changes you want to make.

1.  Return to the original repository your forked from (remember from step 2, you can find the link on your own forked copy)
2.  In that row of buttons about 1/3 of the page down, click the button that says *New Pull Request*.  It will look strange at first and like nothing is happening, but you'll see a link under the Compare Changes that says *compare across forks*.  Click that link and select your fork from the dropdown list 
3.  Some new information pops up, seems like your basic 'comment field' from a blog with a title and a box where you can write a description of what you've done.  The title for me automatically populated the -m entry from my most recent commit/push combination.  Your description should contain more detail about what you changed.  I admit to have only done a few basic pull requests so I don't know the full etiquette, but as you can see I tend to over explain so maybe I'm not the best person give advice on this topic.
4.  Click *Create Pull Request.*  This will do all the magic Github stuff of setting up the pull request to be reviewed.  You can see all pending pull requests (including yours) on the tab near the top part of the repository called, fittingly enough, *Pull Requests*.  If you go there now you'll see that you can have a conversation regarding the pull request if there's an issue, and you can also look at *Files changed* which is pretty awesome.  Github will indicate easily what files you changed compared to the source files.  I think that's pretty awesome.  

That's it, you're done, you've submitted a pull request.  However, your pull request needs to be accepted by the owner (or people with permission) of the project before you'll see it live, so be patient and don't worry, you'll automatically be notified as to what happens with your pull request (sometimes it'll just be accepted or sometimes it'll have an issue and the comments will indicate what you need to fix, but let's assume no issues for now)