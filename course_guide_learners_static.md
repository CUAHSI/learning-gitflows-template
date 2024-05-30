<details>
<summary><h2>1. How to start working on a new project</h2></summary>

Scenario: You are pointed to a code repository on GitHub (this one) for a project that you just joined. You need to start contributing to this codebase. Where do you start? 

You may know that you can use git version control and/or GitHub to make and save changes (commit), and merge those changes into the main code (pull request). Within the realm of these technologies, there are several different workflows that can be followed. The one we are focusing on here is known as the "fork-and-pull workflow". This will give you a broad base that will enable you to adapt to other workflows as necessary.

![image](https://user-images.githubusercontent.com/13220910/81212295-4bf05a80-8f9a-11ea-8302-99a231f61480.png)

There is a main version of the code that people are collaboratively developing. Each contributor has their own version of this code online and locally. Changes are made locally, sent to their online version, and then combined with the collaborative version of the code. Contributors are able to get the changes from other users by syncing their local version with the collaborative version of the code. Now let's look at that workflow using Git + GitHub terminology.

![image](https://user-images.githubusercontent.com/13220910/155410782-77ba4334-9253-4e1e-a5f0-ac779569fc6d.png)

There is a main version of the code that people are collaboratively developing (`upstream repository`). Each contributor has their own version of this code online (`forked repository`) and locally (`cloned repository`). Changes are saved locally (`commit`), sent to their online version (`pushed to their fork`), and then combined with the collaborative version of the code (`merged with a pull request`). Contributors are able to get the changes from other users by syncing their local version with the collaborative version of the code (`pull the upstream repository`).

We are going to walk through each of these steps within the workflow in this lesson. We will also learn about merge conflicts and what a `.gitignore` file is all about. 

</details>

<hr>

<details>
<summary><h2>2. Create a copy of the main repository (fork)</h2></summary>

The first step in our workflow when working on a new project is to fork the canonical repository. This creates a copy of the repository that is specific to your user on GitHub. Everyone that is working on the project has their own fork of the repository where they can safely make changes without impacting the main code or other contributor's code.

----
**Action:** Fork this repo!

1. Open the main repository home page. You should have been given this link to start the training and you are almost there if you are reading this sentence while on GitHub now. To navigate to the home page view, click `<> Code` at the top of the page (maybe right click and open in a new tab so you don't lose these instructions). The URL should look something like, `https://github.com/[org]/learning-gitflows-[username]` where `[org]` and `[username]` will have values unique to your training.
2. Click the "Fork" button at the top right (see image below).

![image](https://user-images.githubusercontent.com/13220910/81218905-94147a80-8fa4-11ea-9685-09ae5b335bdf.png)

3. If prompted with `Where should we fork ...`, choose your user account.
4. When it is complete, you should be on a new webpage. Instead of `https://github.com/[org]/learning-gitflows-[username]`, you will now see `https://github.com/[username]/learning-gitflows-[username]` at the top.

Congratulations! You've made your own copy of the main repository. Now on to the next section!

</details>

<hr>

<details>
<summary><h2>3. Create a local copy (clone)</h2></summary>

The next step in our workflow is to clone your fork. This creates a local copy of the repository that is specific to your user on GitHub. The local copy is where you will make changes to the codebase. 

----
**Action:** Clone this repo!

![image](https://github.com/CUAHSI/learning-gitflows-template/assets/28936967/53cd6b35-03ec-45d5-bd64-8b889162efd9)

1. Open the GitHub page for your fork, e.g. `https://github.com/[username]/learning-gitflows-[username]`. *A navigation note*: from your fork, you can easily navigate back to the canonical repository by clicking the link next to "forked from" at the top, just below your forked repository name. From the canonical repo page, you can get back to your fork by clicking the fork button on the canonical repo and choosing your existing fork from the list.
2. Click the green `Code` button that has a drop down arrow. Again, make sure you are ***on your fork***. This means that you see `[username]/learning-gitflows-[username]` at the top of the page with `forked from [org]/learning-gitflows-[username]` underneath.
3. Copy the SSH address, not the HTTPS one (see image below). We should have already set up your SSH keys, but if not, follow [these instructions to generate an SSH key](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) and [these instructions to add the SSH key to your GitHub account](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account). When you come back to the page, you should have the SSH option.

![image](https://github.com/CUAHSI/learning-gitflows-template/assets/13220910/03273273-ebc7-4d7f-955c-dfaedf68edaa)

4. Open the command line (Windows --> Command Prompt, Mac or Linux --> Terminal). We will instruct you to use specific commands but if you want an overview, [this is a good resource](https://www.g2.com/articles/command-line-interface#cli-vs-gui). Note that the term 'Git Bash' is also used to refer to the command line in this training.
5. Change the working directory ([use `cd`](https://stackoverflow.com/questions/17753986/how-to-change-directory-using-windows-command-line)) to the location where you would like to create the cloned directory (see step 1 in snapshot of command prompt). I would recommend creating a folder somewhere in your D drive to put GitHub projects.
6. Type `git clone [insert URL]` and hit enter (step 2 in snapshot of command prompt), e.g. `git clone git@github.com:[username]/learning-gitflows-[username].git`. Note that you cannot CTRL+V to paste into Git Bash. Right click and choose paste instead.
7. A new folder with the same name as the repository is now available in your working directory. Verify that you are in this folder by running `pwd` (or "print working directory") in the command line. You should see a file path ending with `learning-gitflows-[username]`. If you do not, try running `cd learning-gitflows-[username]` or other combinations of `cd` to "change directories" and navigate to that folder.
8. In the folder, you will find the same files and file structure that you can see on GitHub (step 3 and 4 in snapshot of command prompt; use the command `ls` or `dir` depending on your operating system to inspect the folder contents).
9. The rest of your commands should be run within this folder, `learning-gitflows-[username]`. Run the command `git config pull.rebase false`. This will keep a confusing error message from arising later on.

You have now successfully cloned your fork! Move to the next section.

</details>

<hr>

<details>
<summary><h2>4. Link your clone to the canonical repo</h2></summary>

We refer to online versions of GitHub repositories as "remotes". If you open Git Bash to your project directory (you may need to `cd learning-gitflows-[username]` from the end of the last section) and run `git remote -v`, you will see a list of remotes and their URLs that are currently associated with your local copy. Currently, you have one remote - your fork of the repository - though you will see both a fetch and push option for it. It is referred to as the `origin` because your local copy *originated* from it. 

What we need to do now is link the canonical repository to your local copy. This closes the loop and enables you to pull down changes that collaborators have merged to the main repo into your local version. We refer to the online canonical version as the `upstream` repo and it is a `remote` because it is online.

----
**Action:** Link your cloned repository to the upstream remote.

1. Open the GitHub page for the main (or canonical) repository, `https://github.com/[org]/learning-gitflows-[username]` (reminder: this is the original link you were given to start this course!)
2. Just like in the previous step, click the green dropdown that says `<> Code`
3. Copy the SSH URL (not the HTTPS URL)
4. Open Git Bash to your project's working directory.  
5. Type `git remote add upstream [insert URL]`, e.g. `git remote add upstream https://github.com/[org]/learning-gitflows-[username]`. *Reminder:* you cannot CTRL+V to paste into Git Bash. Right click and choose paste instead.
6. Hit enter.
7. Now, when you run `git remote -v` you should see a list with both an `upstream` remote and an `origin` remote.

You have now set up your new project for collaborative development! We are ready to start making changes. 

</details>

<hr>

<details>
<summary><h2>5. Your first commit</h2></summary>

You are now ready to start contributing your own content to the project! Normally, you would be adding new files, editing lines of code, etc; however, to keep this tutorial programming language-agnostic, we will be editing text in a Markdown document. You may have already learned about Markdown but if not, visit [this quick article](https://guides.github.com/features/mastering-markdown/) to learn about it. In addition, we are going to start introducing a lot of new `git` commands. We will share the ones you need to know but [this is a helpful reference sheet](https://education.github.com/git-cheat-sheet-education.pdf) of other git commands!

We will be using the `dryville_story.md` file to illustrate changes to a repository. First, you will make a change and then save it with Git.

----
**Action:** Add text to the story and commit your change.

1. Before we make any changes, let's check that we are starting from a clean slate. Run `git status` in Git Bash in your project directory. You should see a message that says "nothing to commit". This means that there are no changes on your local copy and it exactly matches the content on your remote fork (the `origin` repo). This is good!
1. Now, open the `dryville_story.md` file locally on your computer in a text editor. Any text editor will do, such as [Notepad++](https://notepad-plus-plus.org/downloads/) or TextEdit on Macs. Currently, there is a title (denoted by `#`) and two sub-headers (denoted by `##`) with text. You can also see the syntax for hyperlinks, `[text that appears](link/to/the/website)`. To see how this syntax is rendered on GitHub, open the `dryville_story.md` file on GitHub by going to the main repo (`https://github.com/[org]/learning-gitflows-[username]`) and clicking the file name.
1. Now, we will add the next section of the story (we are recreating the story available [here on the USGS Water Science School](https://www.usgs.gov/special-topic/water-science-school/science/story-water-dryville)). Open that link. The next section in the story that we don't have in our file yet is called "Getting Water to Your Homes". Add the title (use `##`), the body text, and the appropriate link for the words "over 8 pounds a gallon" to the `dryville_story.md` file locally. Save the file.
1. Now, we have made a change in our local repo. If you run `git status` in Git Bash, you should see the words "modified: dryville_story.md". This means that Git detects a new change. At this point, you could run `git diff` to visually see the changes you made: red = original, green = changed (if you do this and see a `:` at the bottom of your bash window, type `q` to get out of the diff view before proceeding). You will also see the words "no changes added to commit". This is because we have not told Git to record these changes; we have not "staged" them. 
1. We now need to stage these changes so that they can be included in our commit. To stage our changes, run `git add dryville_story.md`. Now when you run `git status`, you see that the "modified: dryville_story.md" change is listed under "Changes to be committed". We are now ready to make a commit. A commit is really just a way to click "save" on a certain change or set of changes and give them a description (read more [here](https://www.w3schools.com/git/git_commit.asp)). 
1. To make a commit, run `git commit -m "[insert your message here]"`. For this change, we will run `git commit -m "add getting-water-to-your-homes section"`. Any change that was listed under the "Changes to be committed" section when we ran `git status` will be included in this commit.
1. Run `git status` again. We should be back to where we started. There is "nothing to commit" because we don't have any additional changes to the repository content - we already committed our only changes. However, you will also see that it says "Your branch is ahead of 'origin/main' by 1 commit". We'll talk about that later.

You have now made a commit and recorded your changes with Git! Go ahead and move on to the next section.

</details>

<hr>

<details>
<summary><h2>6. Make a second commit for practice</h2></summary>

Practice makes perfect - let's make a second commit to our local repo.

----
**Action:** Add the next section's text and commit this change.

1. If you run `git status` in Git Bash  right now, you should see a message that says "nothing to commit" and also "Your branch is ahead of 'origin/main' by 1 commit". 
1. Open the `dryville_story.md` file on your computer and add the next section of [the story](https://www.usgs.gov/special-topic/water-science-school/science/story-water-dryville), which is called "Dryville's First Water Works". Keep the same formatting as before (`##` for the title, `[inline text](url)` for hyperlinks). Save the file.
1. We have now made a second change in our local repo. If you run `git status` in Git Bash, you should see the words "modified: dryville_story.md". This means that Git detects your change. You will also see the words "no changes added to commit". This is because we still need to stage our changes. Note that you will still see "Your branch is ahead of 'origin/main' by 1 commit" - more on that later.
1. Run `git add dryville_story.md` to stage these changes so that they can be included in our next commit. Now when you run `git status`, you see that the "modified: dryville_story.md" change is listed under "Changes to be committed". We are now ready to make a commit.
1. Run `git commit -m "add dryvilles-first-water-works section"` to make a second commit.
1. Run `git status` again. We should be back to where we started. There is "nothing to commit" because we don't have any additional changes to the repository content - we already committed our changes. However, you will now see that it says "Your branch is ahead of 'origin/main' by 2 commits". We'll talk about that next.

You have now made two commits and recorded your changes with Git! Head to the next section.

</details>

<hr>

<details>
<summary><h2>7. Move your local changes to your online repo</h2></summary>

At this point, we have made our file changes and are satisfied with the state of our local repository. It is time to join these changes with the main repository so that our collaborators can use them. Before we can merge our changes with the main repository, we need to get our local changes onto our fork on GitHub.

----
**Action:** Push your changes to your GitHub fork. 

1. If you run `git status` in Git Bash  right now, you should see a message that says "nothing to commit" and also "Your branch is ahead of 'origin/main' by 2 commits". This means that our local version has 2 new changes that do not appear in our remote fork (called the `origin` because our local version *originated* from it). 
1. Go to your fork's webpage (`https://github.com/[username]/learning-gitflows-[username]`) and click on the `X commits` button (see image below). At this time, you should only see commits that occurred before you started working on the repository (instructors prepped the repo by making commits).
1. To get our local changes to appear on our remote fork, we need to "push" them there. To do so, run `git push`. By default, it will push changes up to the `origin` remote `main` branch (we aren't using branching just yet, so everything is the `main` branch). If you want to be more explicit, you can run `git push [remote name] [branch name]`. For example, `git push origin main` will do the same as `git push`.
1. After you run this successfully, you will see `To github.com:[username]/learning-gitflows-[username].git` near the bottom. It is telling you where those changes went, which is to your remote fork. Yay!
1. Go to your fork's webpage (`https://github.com/[username]/learning-gitflows-[username]`) and click on the `X commits` button (see image below). You should see your two commit messages appear there.

![image](https://github.com/CUAHSI/learning-gitflows-template/assets/13220910/6d19c388-6332-486b-b82e-3c8794a79f5e)

You have pushed your changes up to GitHub! Carry on to the next section.

</details>

<hr>

<details>
<summary><h2>8. Request to add your changes to the canonical repo</h2></summary>

With the new changes on your fork, you are now ready to create a pull request (PR). A PR bundles all of your commits together and *requests* that they be *pulled* into the canonical repository. When a PR is opened, you typically request that a collaborator review your changes. They can look at your PR and examine how the sum of all of your commits differ from the existing canonical repo. They can make suggestions for revisions to specific lines and ask for changes before they merge your contributions into the main repo. 

For now, we will discuss how to open a pull request.

----
**Action:** Open a pull request. 

1. Go to **your fork's** webpage (`https://github.com/[username]/learning-gitflows-[username]`). Near the top, you will see a "Contribute" button (see image below). Click that button, and then click "Open pull request".

![image](https://user-images.githubusercontent.com/5882743/154136024-be54e8a7-7c24-4cca-a1d2-5e376547f59c.png)

2. Before your pull request is actually created, you should verify that you are requesting the correct changes be merged with the correct repository. For now, we are not working with branches, so don't worry about the fields that say "main". However, you should verify that the `base repository` is set to the project canonical repo (`[org]/learning-gitflows-[username]` in this case) and that the `head repository` is set to your fork (`[username]/learning-gitflows-[username]`). You also need to verify the commits lists. It should list the two that you just created.
3. When you have checked those things, you can click the green "Create pull request" button.
4. You still haven't made the pull request yet - one more step. You now need to title your pull request and add a description about your changes. [Here is an article about some common best practices when it comes to PRs](https://www.atlassian.com/blog/git/written-unwritten-guide-pull-requests). In your description, make sure to reference this issue by typing `#[issue number]`. 
5. Once you add a title and description, click the cog next to the `Reviewers` feature on the right bar and select your course contact as the reviewer from the drop-down menu. **Note - if you do not have the option to add a reviewer, do step 6 and then add the reviewer after.** You may not have the correct permissions to add a reviewer and should reach out to your course contact.
6. Now you are ready - click "Create pull request"

You have now successfully created a PR! Wait for your PR to be reviewed and merged. Once your PR has been merged, start on the next section.

</details>

<hr>

<details>
<summary><h2>9. Closing the loop</h2></summary>

Congratulations - your PR was merged and you have successfully changed the canonical repository. You are almost a Git Pro! 

Merging a PR creates a commit on the canonical repository. Even though the most recent changes were your additions, technically your fork and local repository do not have that "merge" commit and are now out-of-date with the canonical repo. So, what we will do now is learn how to close the loop after your PR is merged. This step is represented in the image below by the arrow that goes from the `Upstream Repository` cloud down to the `User 1/2 Local Repository` computers in the image below (this is the same image we saw at the beginning of the training).

![image](https://user-images.githubusercontent.com/13220910/155410782-77ba4334-9253-4e1e-a5f0-ac779569fc6d.png)

----
**Action:** Close the loop. 

1. Open Git Bash and make sure you are in your project's directory. Reminder: use `pwd` to see where you are and if you don't see `learning-gitflows-[username]` as the final part of the path, then you will need to use `cd` to navigate to that project directory.
1. Pull down changes from the canonical repository (aka the "upstream" remote) by running `git pull upstream main`.
1. We now have changes locally that do not appear on our fork (aka the "origin" remote). So if we run `git status`, we get the message "Your branch is ahead of 'origin/main' by X commits".
1. Just like we did earlier, we can push our local changes to our fork by running `git push` (or `git push origin main` to be explicit).
1. Now when you run `git status`, you should see that everything is up-to-date and there is nothing to commit. 

You have successfully closed the loop after your PR was merged! ***Before you go on to the next section, your instructor will need to take an action. Ping them to get them to do it*** (maybe something like `Hey [course instructor], I just finished step 9 where I closed the loop between the main repo and my local copy!`), and wait until after they have confirmed things are ready before you move on to the next section.

</details>

<hr>

<details>
<summary><h2>10. Get a collaborator's content locally</h2></summary>

Scenario: After your content was merged, a collaborator tells you that they added additional content. You want to keep working, but you don't want to duplicate anything they did. You now need to pull in their content to your local repository before you continue working. Don't worry, we have done this before. We just need to pull down any new changes from the canonical repository!

----
**Action:** Pull down a collaborator's contributions to the canonical repository. 

1. First, verify that you did indeed close the loop after merging your PR (see previous section).
1. Now, visit that canonical repository on GitHub and look at the commits (go to `https://github.com/[org]/learning-gitflows-[username]` and click on "X commits" just below the green `<> Code` button). You should see a new commit that was not created by you. 
1. Click on the commit name to see what changes were made. Looks like your collaborator added the next section of the story! 
1. Our goal is to continue this work and add another section but first, we need to get our collaborator's changes locally. Before pulling down changes, verify that you don't have any uncommitted changes locally. Run `git status` and look for the phrase, "nothing to commit". If that does not appear, go back to step 1 in this list.
1. Next, pull their changes down using `git pull upstream main`. Remember, the "canonical repository" is referred to as the "upstream" remote in git commands.
1. Now when you open your `dryville_story.md` file locally, you should see the "Be Gone, Dirty Water" section is the last in the file. 

Great! You successfully pulled down contributions that someone else on your team made to the repository. Next, we will add another section. 

</details>

<hr>

<details>
<summary><h2>11. Add two new sections of the story</h2></summary>

Time to add on to this story. We've done this a couple times now, so the edit-save-add-commit pattern should be getting familiar.

----
**Action:** Add text for the next two sections and commit those changes.

1. ***Ping your instructor and let them know that you have arrived at this step. There is something that they need to do.***
1. If you run `git status` in Git Bash  right now, you should see a message that says "nothing to commit" and also "Your branch is ahead of 'origin/main' by 1 commit" (that one commit is the one from your collaborator that has not yet been pushed to your fork). 
1. Open the `dryville_story.md` file on your computer and add the next section of [the story](https://www.usgs.gov/special-topic/water-science-school/science/story-water-dryville), which is called "Your First Flood". Keep the same formatting as before (`##` for the title, `[inline text](url)` for hyperlinks). Save the file.
1. If you run `git status` in Git Bash, you should see the words "modified: dryville_story.md". This means that Git detects your change. You will also see the words "no changes added to commit". This is because we still need to stage our changes. Note that you will still see "Your branch is ahead of 'origin/main' by 1 commit" - we still haven't pushed since we pulled down our collaborator's changes. At this point, you could also run `git diff` to visually see the changes you made: red = original, green = changed (if you do this and see a `:` at the bottom of your bash window, type `q` to get out of the diff view before proceeding). 
1. Run `git add dryville_story.md` to stage these changes so that they can be included in our next commit. Now when you run `git status`, you see that the "modified: dryville_story.md" change is listed under "Changes to be committed". We are now ready to make a commit.
1. Run `git commit -m "add your-first-flood section"` to make a commit.
1. Run `git status` again. We should be back to where we started. There is "nothing to commit" because we don't have any additional changes to the repository content - we already committed our changes. However, you will now see that it says "Your branch is ahead of 'origin/main' by 2 commits".
1. Now repeat for "Storing Water for a Rainy Day". Copy and paste text from [the complete story](https://www.usgs.gov/special-topic/water-science-school/science/story-water-dryville). Keep the same formatting as before (`##` for the title, `[inline text](url)` for hyperlinks). Save the file.
1. Run `git add dryville_story.md` to stage these changes.
1. Run `git commit -m "add storing-water-for-a-rainy-day section"` to make a commit.
1. Now `git status` shows that we are ahead of `origin/main` by 3 commits.

You have now made two new commits. There's still more to learn - on to the next part!

</details>

<hr>

<details>
<summary><h2>12. Pull down more new changes from your collaborator</h2></summary>

We just made two commits that added two new sections of the story to our `dryville_story.md` file. Huzzah! Everything is peachy. However, while you were doing that, your collaborator also decided to add to the story and they committed before you. Now, we need to once again pull down their changes before moving on.

----
**Action:** Pull down your collaborator's most recent additions. 

1. Do not proceed with this step until your instructor has verified that it's OK to go on! (You pinged them in the last step, remember?)
1. Before pulling down changes, verify that you don't have any uncommitted changes locally. Run `git status` and look for the phrase, "nothing to commit".
1. Next, pull their changes down using `git pull upstream main`. 
1. Uh oh, there seems to be an issue. When we pulled down those changes, the message "CONFLICT (content): Merge conflict in dryville_story.md" appeared. We must have been editing the same line of the file as our collaborator.

Your first merge conflict! Everything will be OK, promise :) 

</details>

<hr>

<details>
<summary><h2>13. Conquer a merge conflict!</h2></summary>

In the last step, we pulled down changes from our collaborator and realized that there was a merge conflict. This occurs when you edit the same line of code. In this case, you both added on to the last line of the file. Don't worry - merge conflicts are not as intimidating as they may seem. Let's do this!

----
**Action:** Fix the merge conflict. 

1. Open your local `dryville_story.md` file.
1. Scroll through the file and look for where the merge conflict happens. Merge conflicts are denoted by `<<<<<<<` at the start and `>>>>>>>` at the end. Sometimes, there are multiple conflicts and each will be sectioned off with the left and right pointing carrots.
1. We have one merge conflict in this situation, so that makes this easier. Merge conflicts happen because Git doesn't know which are the correct lines. A human needs to intervene and decide what to keep and what not to keep. Look at your conflict in `dryville_story.md`. The content between `<<<<<<< HEAD` and `=======` is the content that existed in your version of the file before you attempted to pull other changes. The content between `=======` and `>>>>>>>` is what you pulled down and tried to merge. Examine the differences between the content in those sections.
1. The most obvious difference is that your version has the `Your First Flood` section, while the version you are trying to merge does not. So, you would want to keep the `Your First Flood` text. Cut and paste that section so that it is outside and above the `<<<<<<< HEAD` section (see below).

```
## Your First Flood

You're again happy until the first desert downpour hits. The rain flows down the hills (runoff) into Dryville's town center and suddenly you have your first flood — more unwanted water (and the mud it carries with it) to deal with. You decide to build a set of storm drains to fix this problem. Lay some more (this time BIG) pipes through town with intakes where the water collects in low spots. Storm water will flow into these pipes and be sent on its way downhill into your creek. Another problem solved.

But when the storm hit, Dryville Creek overflowed and flooded some houses that were built on the flood plain, the flat ground alongside of the creek. You can do two things here. Look at the lay of the land and decide what parts of the creek bed will flood most often when it really rains and don't allow people to build houses there, or build a dam upstream to create a reservoir to trap storm water before it floods into town. Your reservoir can then release the water slowly over a long period of time, thus preventing floods and recharging ground water.

<<<<<<< HEAD
## Storing Water for a Rainy Day

You start thinking... a reservoir (you can call it a lake) above town could really serve a lot of purposes. A lake will provide a place for you to have fun — go swimming, boating, catch catfish, and relax. You can run your water-supply intake pipes from the lake instead of from your creek, especially since the flood destroyed your water-intake pumping station. With a dam you can release only the amount of water you want into the creek below the dam, thus making sure you have just the right amount of water running in Dryville Creek at all times. A dam would even help prevent flooding downstream because you can hold extra rainfall and runoff during a storm and slowly release it afterward. You can build a bigger paddle wheel, or, better yet, construct a real [hydroelectric power plant](https://www.usgs.gov/special-topic/water-science-school/science/hydroelectric-power-water-use) in your dam to start generating electricity! More problems solved.
=======
## Storing Water for a Rainy Day

You start thinking... a reservoir (you can call it a lake) above town could really serve a lot of purposes. A lake will provide a place for you to have fun — go swimming, boating, catch catfish, and relax. You can run your water-supply intake pipes from the lake instead of from your creek, especially since the flood destroyed your water-intake pumping station. With a dam you can release only the amount of water you want into the creek below the dam, thus making sure you have just the right amount of water running in Dryville Creek at all times. A dam would even help prevent flooding downstream because you can hold extra rainfall and runoff during a storm and slowly release it afterward. You can build a bigger paddle wheel, or, better yet, construct a real hydroelectric power plant in your dam to start generating electricity! More problems solved.
>>>>>>> afd002e4b66f31f815e4236ffa6ea3e17f127e1d
```

5. Now, continuing on. Examine the differences between the "Storing Water for a Rainy Day" sections. Can you find any?
6. The only difference should be that your version (the top one) has a hyperlink for the hydroelectric power plant, while the version that is being merged does not. So, we actually want to keep only the version that you created. 
7. Delete the content between `=======` and `>>>>>>>` (the bottom section).
8. Now you are left with the merge conflict symbols and the correct version of the "Storing Water for a Rainy Day" section. Delete all of the symbols related to the merge conflict (`<<<<<<< HEAD`, `=======`, and `>>>>>>> [random letters/numbers]`). Now, you should be back to where you started (which happens in merge conflict resolution sometimes).
9. Save the file.
10. The last step for resolving a merge confict is to commit your changes. Follow the same pattern as before. Running `git status` will show you that you have an unresolved merge conflict. Just as before, run `git add dryville_story.md` to stage your changed file. Then commit by running `git commit -m "resolve merge conflict"`. 
11. Now, when you run `git status` you will see that you don't have any changes to commit (but your branch is still ahead of `origin/main` - which is fine and will be addressed next).

You successfully resolved a conflict! Continue the course in the next section.

</details>

<hr>

<details>
<summary><h2>14. Request newest set of changes be merged to the canonical repo</h2></summary>

We are now ready to push our local changes (including the resolved merge conflict) up to our fork (aka remote "origin"). Then, we can open a pull request (PR). 

----
**Action:** Push your changes to your GitHub fork and open a PR. 

1. If you run `git status` in Git Bash  right now, you should see a message that says "nothing to commit" and also "Your branch is ahead of 'origin/main' by X commits". Our local version has new changes that do not appear in our fork (aka the remote `origin` because our local version *originated* from it). 
1. Just as before, we need to "push" our local changes to our remote fork. Run `git push origin main` to do so. 
1. Go to **your fork's** webpage (`https://github.com/[username]/learning-gitflows-[username]`) and click on the `X commits` button (just below the green `<> Code` button). You should see your new commit messages appear there.
1. Now, click the "Code" tab to go back to your fork's home page. Near the top, you will see a "Contribute" button. Click that button, and then click "Open pull request".
1. Before your pull request is actually created, you need to verify that you are requesting the correct changes be merged with the correct repository. Remember, we are not working with branches, so don't worry about the fields that say "main". However, you should verify that the `base repository` is set to the project canonical repo (`[org]/learning-gitflows-[username]`) and that the `head repository` is set to your fork (`[username]/learning-gitflows-[username]`).
1. After verifying, click the green "Create pull request" button.
1. Add a title to your pull request and a description about your changes.
1. Once you add a title and description, click the cog next to the `Reviewers` feature on the right bar and select your course contact as the reviewer from the drop-down menu. If you do not have the option to add a reviewer, do step 9 and then add the reviewer after.
1. Now, click "Create pull request".

You have successfully made a second pull request! Wait for your PR to be reviewed and merged. Once your PR has been merged, read the next section.

</details>

<hr>

<details>
<summary><h2>15. Close another loop after a merged MR</h2></summary>

Your PR was merged! Yay! Now, remember that "closing the loop" thing we did after our last PR was merged? Let's do it again.

Merging a PR creates a commit on the canonical repository. Even though the most recent changes were your additions, technically your fork and local repository do not have that "merge" commit and are now out-of-date with the canonical repo. So, we need to close the loop.

----
**Action:** Close the loop. 

1. Open Git Bash and make sure you are in your project's directory (reminder: use `cd`).
1. Pull down changes from the canonical repository (aka the "upstream" remote) by running `git pull upstream main`.
1. We now have changes locally that do not appear on our fork (aka the "origin" remote). So if we run `git status`, we get the message "Your branch is ahead of 'origin/main' by X commits".
1. Just like we did earlier, we can push our local changes to our fork by running `git push` (or `git push origin main` to be explicit).
1. Now when you run `git status`, you should see that everything is up-to-date and there is nothing to commit. 

You have once again closed the loop after your PR was merged! We are almost done - head to the next section to learn about our last new topic.

</details>

<hr>

<details>
<summary><h2>16. Using a gitignore file</h2></summary>

The last topic we are going to cover in this tutorial is the `.gitignore` file. These files are used when you have a local file that you don't want to track changes to in a commit or put on GitHub. You simply add the name of the file (including directory structure when applicable) to the `.gitignore` file to have Git *ignore* it (see what they did there?). This practice is often used for intermediate files created by processes within your repo, temporary files, or really large data that need to be stored elsewhere. Additional information about `.gitignore` files can be found in [this article](https://www.pluralsight.com/guides/how-to-use-gitignore-file).

----
**Action:** Add a file and then gitignore it.

1. First, open the `.gitignore` file that is in your local directory using a text editor (for example, Notepad++). It should be completely empty. If you don't see this file, try changing your settings so that you can see hidden files. On Mac, run `Command + Shift + .` to reveal them. On Windows, click `View > Show > Hidden items` in the File Explorer.
1. Next, download [this image](https://www.usgs.gov/media/images/icon-teaching) (right click and choose "Save image as") and save as `wss-icon-small-teacher.png` in your `learning-gitflows-[username]` folder on your computer. 
1. Now in Git Bash, run `ls` to "list" the items in your current working directory. You should see the following: `dryville_story.md`, `README.md` and `wss-icon-small-teacher.png`. Note that the `.gitignore` file doesn't show up with `ls` because it is technically a "hidden" file (starts with a `.`).
1. So, you've added a new file to your repository. Now, run `git status`. Git shows that `wss-icon-small-teacher.png` is an untracked file. We could leave it like that and just try to remember to not commit it, but that seems risky. The more foolproof way is to to add it to the `.gitignore` file.  
1. Copy the filename `wss-icon-small-teacher.png` and paste into the `.gitignore` file. Save the file.
1. Now run `git status`. It no longer shows `wss-icon-small-teacher.png` as an untracked file, but instead shows that we have modified `.gitignore`. That is because this file is version controlled - whenever we change it, we push those changes to the main repository so that everyone uses the same one. 
1. Now, commit your changes to `.gitignore` and push to your fork.  
```
git add .gitignore
git commit -m "add downloaded image to gitignore"
git push origin main
```
8. Finally, create a pull request. Make sure to add your course contact as a reviewer of your PR. Revisit the step "Request to add your changes to the canonical repo" if you need any reminders for how to do this.

Once you open your PR, wait for it to be reviewed and merged. Once your PR has been merged, you can read the final section.

</details>

<hr>

<details>
<summary><h2>17. In conclusion ...</h2></summary>

Welcome to the end of the hands on tutorial with Git and GitHub! You have now been exposed and practiced the basic workflow that is common for collaborating on codebases in open science. Below is a summary of all the concepts you learn. Feel free to screenshot/copy/bookmark that section to use as a reference in the future. At the very end of this section, we share resources that you may be interested in exploring later as you embark on your journey to become a Git and collaborative coding expert!

## The conceptual diagram of the workflow you just learned/used 

![image](https://user-images.githubusercontent.com/13220910/155410782-77ba4334-9253-4e1e-a5f0-ac779569fc6d.png)

## A summary list of commands that were used.

### Setting up a new project

1. Fork the canonical repo to your username.
1. Create a local copy of your fork - copy the SSH URL from **your fork's** GitHub page, then in Git Bash run `git clone [insert your fork's SSH URL]`.
1. Add the canonical repo as a remote to your local version - copy the SSH URL from **the canonical repo's** GitHub page, then in Git Bash run `git remote add upstream [insert canonical repo's SSH URL]`.
1. Verify that you are ready to go with remotes - run `git remote -v` and check that your fork's URL is next to `origin` and the canonical repo is listed next to `upstream`.

### Saving a change locally

1. Change the file(s).
1. Inspect what changes git detects - run `git status`
1. Stage the files that you want to include in your commit - `git add [insert file name]`. Pro tip: use `git add .` to stage all changed files listed with `git status`.
1. Commit your staged changes - `git commit -m "[commit message here]"`

### Moving your local commits to your fork

1. Run `git push origin main`
1. Look at the "commits" page on your fork on GitHub to see your new commits (click "X commits" below the green `<> Code` dropdown button).

### Adding your changes to the canonical repository

1. Once you have changes on your fork that make it different from the canonical repository, go to your fork's GitHub page and click "New pull request". 
1. In the next screen, verify that the `base` repository shows the canonical and the `head` repository shows your fork. 
1. Click "Create pull request".
1. Add a title and description. Include a reviewer. If the PR addresses specific [issues](https://docs.github.com/en/issues/tracking-your-work-with-issues/about-issues) in your GitHub repo, link to them by adding `#[issue number]` in your description.
1. The reviewer will approve/merge the changes.
1. Close the loop by pulling down the changes from upstream to your local repo - `git pull upstream main`

### Handling merge conflicts

1. If you have a merge conflict after pulling down changes, look in the file(s) that have been flagged as having conflicts.
1. Inspect the content between `<<<<<<< HEAD` and `=======`, which is the content that existed before the merge (likely your local content).
1. Now inspect the content between `=======` and `>>>>>>> [string of letters and numbers]`, which is the content that is trying to be merged with what currently exists locally (likely the remote content).
1. Decide what of that content to keep and what to delete.
1. Remove the merge conflict symbols, `<<<<<<< HEAD`, `=======`, and `>>>>>>> [string of letters and numbers]`.
1. Save the file and then commit your merge resolution (see above for making commits). The the message "resolve merge conflict" is often used.

## Feeling confident? Explore more!

There is a lot more Git that can be learned, but the above are the basics that will probably be enough for awhile. As you start to get more advanced, there may be some additional concepts/commands you should learn such as, 

* Temporarily hiding changes in order to pull upstream changes to avoid conflicts (`git stash`, `git stash apply`),
* branching (`git switch -c`, `git checkout`), and
* [much more](https://git-scm.com/doc)!

Congratulations - you completed the tutorial!

</details>

<hr>
