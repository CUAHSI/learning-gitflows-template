<details>
<summary><h2>How to start working on a new project</h2></summary>

Scenario: You are pointed to a code repository on GitLab (this one) for a project that you just joined. You need to start contributing to this codebase. Where do you start? 

You may know that you can use git version control and/or GitLab to make and save changes (commit), and merge those changes into the main code (merge request, aka pull request). Within the realm of these technologies, there are several different workflows that can be followed. The one we are focusing on here is known as the "fork-and-pull workflow". This will give you a broad base that will enable you to adapt to other workflows as necessary.

![fork-and-pull-concepts](https://user-images.githubusercontent.com/13220910/81212295-4bf05a80-8f9a-11ea-8302-99a231f61480.png)

There is a main version of the code that people are collaboratively developing. Each contributor has their own version of this code online and locally. Changes are made locally, sent to their online version, and then combined with the collaborative version of the code. Contributors are able to get the changes from other users by syncing their local version with the collaborative version of the code. Now let's look at that workflow using Git + GitLab terminology.

![fork-and-pull-terms](https://user-images.githubusercontent.com/13220910/81212707-dfc22680-8f9a-11ea-8fc8-ad0d960d8207.png)

There is a main version of the code that people are collaboratively developing (`upstream repository`). Each contributor has their own version of this code online (`forked repository`) and locally (`cloned repository`). Changes are saved locally (`commit`), sent to their online version (`pushed to their fork`), and then combined with the collaborative version of the code (`merged with a pull request`). Contributors are able to get the changes from other users by syncing their local version with the collaborative version of the code (`pull the upstream repository`).

We are going to walk through each of these steps within the workflow in this lesson. We will also learn about merge conflicts and what a `.gitignore` file is all about. 

</details>

<hr>

<details>
<summary><h2>Create a copy of the main repository (fork)</h2></summary>

The first step in our workflow when working on a new project is to fork the canonical repository. This creates a copy of the repository that is specific to your user on GitLab. Everyone that is working on the project has their own fork of the repository where they can safely make changes without impacting the main code or other contributor's code.

----
**Action:** Fork this repo!

1. Open the main repository page, `https://code.usgs.gov/wma/dsp/trainings/gitflows-trainings/ds-gitflows-[username]
2. Click the "Fork" button at the top right (see image below).

![create-new-fork](https://code.usgs.gov/wma/dsp/trainings/ds-gitflows-static-template/uploads/8ce4fee2301b48f960622bfc98bfcba3/create-new-fork.png)

3. If prompted with `Where should we fork ...`, choose your user account.
4. When it is complete, you should be on a new webpage. Instead of `/wma/dsp/trainings/gitflows-trainings/ds-gitflows-[username]`, you will now see `[username]/ds-gitflows-[username]` at the top.

Congratulations! You've made your own copy of the main repository.

</details>

<hr>

<details>
<summary><h2>Create a local copy (clone)</h2></summary>

The next step in our workflow is to clone your fork. This creates a local copy of the repository that is specific to your user on GitLab. The local copy is where you will make changes to the codebase. 

----
**Action:** Clone this repo!

1. Open the GitLab page for your fork, e.g. `https://code.usgs.gov/[username]/ds-gitflows-[username]`. *A navigation note*: from your fork, you can easily navigate back to the canonical repository by clicking the link next to "forked from" at the top, just below your forked repository name. From the canonical repo page, you can get back to your fork by clicking the fork button on the canonical repo and choosing your existing fork from the list.
2. Click the `Clone` button. Again, make sure you are ***on your fork***. This means that you see `[username]/ds-gitflows-[username]` at the top of the page with `forked from wma/dsp/trainings/gitflows-trainings/ds-gitflows-[username]` underneath.
3. Copy the SSH address, not the HTTPS one (see image below). We should have already set up your SSH keys, but if not, follow [these instructions to generate an SSH key](https://docs.gitlab.com/ee/user/ssh.html#generate-an-ssh-key-pair) and [these instructions to add the SSH key to your GitLab account](https://docs.gitlab.com/ee/user/ssh.html#add-an-ssh-key-to-your-gitlab-account). When you come back to the page, you should have the SSH option.

![clone-with-ssh](https://code.usgs.gov/wma/dsp/trainings/ds-gitflows-static-template/uploads/efaa9ac584b6ac4d9e1d36582a403d5d/clone-with-ssh.png)

4. Open Git Bash on your computer.
5. Change the working directory ([use `cd`](https://stackoverflow.com/questions/17753986/how-to-change-directory-using-windows-command-line)) to the location where you would like to create the cloned directory. GitLab provides a way to share and back up these projects. OneDrive doesn't work well with git repositories, so I would recommend creating a folder somewhere outside of OneDrive to put your GitLab projects in (e.g., in your D drive if you have one).
6. Type `git clone [insert URL]` and hit enter, e.g. `git clone git@code.usgs.gov:[username]/ds-gitflows-[username]`. Note that you cannot CTRL+V to paste into Git Bash. Right click and choose paste instead.
7. A new folder with the same name as the repository is now available in your working directory. In the folder, you will find the same files and file structure that you can see on GitLab.
8. While in the folder, run the command 'git config pull.rebase false'. This will keep a confusing error message from arising later on.

You have now successfully cloned your fork!

</details>

<hr>

<details>
<summary><h2>Link your clone to the canonical repo</h2></summary>

We refer to online versions of GitLab repositories as "remotes". If you open Git Bash to your project directory (you may need to `cd ds-gitflows-[username]` from the end of the last section) and run `git remote -v`, you will see a list of remotes and their URLs that are currently associated with your local copy. Currently, you have one remote - your fork of the repository - though you will see both a fetch and push option for it. It is referred to as the `origin` because your local copy *originated* from it. 

What we need to do now is link the canonical repository to your local copy. This closes the loop and enables you to pull down changes that collaborators have merged to the main repo into your local version. We refer to the online canonical version as the `upstream` repo and it is a `remote` because it is online.

----
**Action:** Link your cloned repository to the upstream remote.

1. Open the GitLab page for the main (or canonical) repository, `https://code.usgs.gov/wma/dsp/trainings/gitflows-trainings/ds-gitflows-[username]`
2. Just like in the previous step, click `Clone`
3. Copy the SSH URL (not the HTTPS URL)
4. Open Git Bash and `cd` to your project's working directory.  
5. Type `git remote add upstream [insert URL]`, e.g. `git remote add upstream https://code.usgs.gov/wma/dsp/trainings/gitflows-trainings/ds-gitflows-[username]`. *Reminder:* you cannot CTRL+V to paste into Git Bash. Right click and choose paste instead.
6. Hit enter.
7. Now, when you run `git remote -v` you should see a list with both an `upstream` remote and an `origin` remote.

You have now set up your new project for collaborative development! We are ready to start making changes. Please move onto the next section.

</details>

<hr>

<details>
<summary><h2>Your first commit</h2></summary>

You are now ready to start contributing your own content to the project! Normally, you would be adding new files, editing lines of code, etc; however, to keep this tutorial programming language-agnostic, we will be editing text in a Markdown document. I think you have already learned about Markdown but if not, visit [this quick article](https://guides.github.com/features/mastering-markdown/) to learn about it.

We will be using the `dryville_story.md` file to illustrate changes to a repository. First, you will make a change and then save it with Git.

----
**Action:** Add text to the story and commit your change.

1. Before we make any changes, let's check that we are starting from a clean slate. Run `git status` in Git Bash in your project directory. You should see a message that says "nothing to commit". This means that there are no changes on your local copy and it exactly matches the content on your remote fork (the `origin` repo). This is good!
1. Now, open the `dryville_story.md` file on your computer. Any text editor will do, such as [Notepad++](https://notepad-plus-plus.org/downloads/). Currently, there is a title (denoted by `#`) and two sub-headers (denoted by `##`) with text. You can also see the syntax for hyperlinks, `[text that appears](link/to/the/website)`. To see how this syntax is rendered on GitLab, open the `dryville_story.md` file on GitLab by going to the upstream repo (`https://code.usgs.gov/wma/dsp/trainings/gitflows-trainings/ds-gitflows-[username]`) and clicking the file name.
1. Now, we will add the next section of the story (we are recreating the story available [here on the USGS Water Science School](https://www.usgs.gov/special-topic/water-science-school/science/story-water-dryville)). Open that link. The next section in the story that we don't have in our file yet is called "Getting Water to Your Homes". Add the title (use `##`), the body text, and the appropriate link for the words "over 8 pounds a gallon" to the `dryville_story.md` file locally. Save the file.
1. Now, we have made a change in our local repo. If you run `git status` in Git Bash, you should see the words "modified: dryville_story.md". This means that Git detects a new change. At this point, you could run `git diff` to visually see the changes you made: red = original, green = changed (if you do this and see a `:` at the bottom of your bash window, type `q` to get out of the diff view before proceeding). You will also see the words "no changes added to commit". This is because we have not told Git to record these changes; we have not "staged" them. 
1. We now need to stage these changes so that they can be included in our commit. To stage our changes, run `git add dryville_story.md`. Now when you run `git status`, you see that the "modified: dryville_story.md" change is listed under "Changes to be committed". We are now ready to make a commit.
1. To make a commit, run `git commit -m "[insert your message here]"`. For this change, we will run `git commit -m "add getting-water-to-your-homes section"`. Any change that was listed under the "Changes to be committed" section when we ran `git status` will be included in this commit.
1. Run `git status` again. We should be back to where we started. There is "nothing to commit" because we don't have any additional changes to the repository content - we already committed our only changes. However, you will also see that it says "Your branch is ahead of 'origin/main' by 1 commit". We'll talk about that later.

You have now made a commit and recorded your changes with Git! Please move on to the next section.

</details>

<hr>

<details>
<summary><h2>Make a second commit for practice</h2></summary>

Practice makes perfect - let's make a second commit to our local repo.

----
**Action:** Add the next section's text and commit this change.

1. If you run `git status` in Git Bash  right now, you should see a message that says "nothing to commit" and also "Your branch is ahead of 'origin/main' by 1 commit". 
1. Open the `dryville_story.md` file on your computer and add the next section of [the story](https://www.usgs.gov/special-topic/water-science-school/science/story-water-dryville), which is called "Dryville's First Water Works". Keep the same formatting as before (`##` for the title, `[inline text](url)` for hyperlinks). Save the file.
1. We have now made a second change in our local repo. If you run `git status` in Git Bash, you should see the words "modified: dryville_story.md". This means that Git detects your change. You will also see the words "no changes added to commit". This is because we still need to stage our changes. Note that you will still see "Your branch is ahead of 'origin/main' by 1 commit" - more on that later.
1. Run `git add dryville_story.md` to stage these changes so that they can be included in our next commit. Now when you run `git status`, you see that the "modified: dryville_story.md" change is listed under "Changes to be committed". We are now ready to make a commit.
1. Run `git commit -m "add dryvilles-first-water-works section"` to make a second commit.
1. Run `git status` again. We should be back to where we started. There is "nothing to commit" because we don't have any additional changes to the repository content - we already committed our changes. However, you will now see that it says "Your branch is ahead of 'origin/main' by 2 commits". We'll talk about that next.

You have now made two commits and recorded your changes with Git! Please move on to the next section.


</details>

<hr>

<details>
<summary><h2>Move your local changes to your online repo</h2></summary>

At this point, we have made our file changes and are satisfied with the state of our local repository. It is time to join these changes with the main repository so that our collaborators can use them. Before we can merge our changes with the main repository, we need to get our local changes onto our fork on GitLab.

----
**Action:** Push your changes to your GitLab fork. 

1. If you run `git status` in Git Bash  right now, you should see a message that says "nothing to commit" and also "Your branch is ahead of 'origin/main' by 2 commits". This means that our local version has 2 new changes that do not appear in our remote fork (called the `origin` because our local version *originated* from it). 
1. To get our local changes to appear on our remote fork, we need to "push" them there. To do so, run `git push`. By default, it will push changes up to the `origin` remote `main` branch (we aren't using branching just yet, so everything is the `main` branch). If you want to be more explicit, you can run `git push [remote name] [branch name]`. For example, `git push origin main` will do the same as `git push`.
1. After you run this successfully, you will see "To code.usgs.gov:[username]/ds-gitflows-[username].git" near the bottom. It is telling you where those changes went, which is to your remote fork. Yay!
1. Go to **your fork's** webpage (`https://code.usgs.gov/[username]/ds-gitflows-[username]`) and click on the `commits` button (see image below). You should see your two commit messages appear there.

![two-commits-ahead](https://code.usgs.gov/wma/dsp/trainings/ds-gitflows-static-template/uploads/4ccdc91ee25a2d8dc5e9c5b575401d66/move-your-local-changes.png)

You have pushed your changes up to GitLab! Please move on to the next section.


</details>

<hr>

<details>
<summary><h2>Request to add your changes to the canonical repo</h2></summary>

With the new changes on your fork, you are now ready to create a merge request (MR; these are known as pull requests, PRs, on Github). An MR bundles all of your commits together and *requests* that they be *merg*ed into the canonical repository. When an MR is opened, you typically request that a collaborator review your changes. They can look at your MR and examine how the sum of all of your commits differ from the existing canonical repo. They can make suggestions for revisions to specific lines and ask for changes before they merge your contributions into the main repo. 

For now, we will discuss how to open a merge request.

----
**Action:** Open a merge request. 

1. Go to **your fork's** webpage (`https://code.usgs.gov/[username]/ds-gitflows-[username]`). At the top, you will see a "Create merge request" button (see image below). Click that button.

![create-merge-request](https://code.usgs.gov/wma/dsp/trainings/ds-gitflows-static-template/uploads/7702c06dfe0273b2c6186b7b8c1ba679/create-merge-request.png)

2. Before your merge request is actually created, you should verify that you are requesting the correct changes be merged with the correct repository. For now, we are not working with branches, so don't worry about the fields that say "main". However, you should verify that the `into` location is set to the project canonical repo (`/wma/wp/trainings/gitflows-trainings/ds-gitflows-[username]:main` in this case) and that the `From` location is set to your fork (`[username]/ds-gitflows-[username]:main`). If you needed to edit these locations, you could click "Change branches".

![new-merge-request](https://code.usgs.gov/wma/dsp/trainings/ds-gitflows-static-template/uploads/46500c359e1dedaa30e65d7016936d21/new-merge-request.png)

3. You also need to verify the commits lists. It should list the two that you just created.

![verify-two-commits](https://code.usgs.gov/wma/dsp/trainings/ds-gitflows-static-template/uploads/945b9a35363554a30a964a036597dd3c/verify-two-commits.png)

4. You now need to title your merge request and add a description about your changes. If you need a refresher, [here is an article about some common best practices when it comes to MRs/PRs](https://www.atlassian.com/blog/git/written-unwritten-guide-pull-requests).

![edit-title-description](https://code.usgs.gov/wma/dsp/trainings/ds-gitflows-static-template/uploads/04629e7af0d50614cff1b9be58b81288/edit-title-description.png)

5. Click the down symbol in the `Reviewer` box and select your course contact as the reviewer from the drop-down menu.

![select-reviewer](https://code.usgs.gov/wma/dsp/trainings/ds-gitflows-static-template/uploads/c325dd5e956555085f760409a0324536/select-reviewer-wide.png)

6. Now you are ready - click the blue "Create merge request" button.

![confirm-create-MR](https://code.usgs.gov/wma/dsp/trainings/ds-gitflows-static-template/uploads/31694212a55021200de16553244e5bd3/confirm-create-MR.png)

You have now successfully created a MR! Wait for your MR to be reviewed and merged (and feel free to ping your instructor on Teams and let them know the MR is waiting!)


</details>

<hr>

<details>
<summary><h2>Closing the loop</h2></summary>

Congratulations - your MR was merged and you have successfully changed the canonical repository. You are almost a Git Pro! 

Merging an MR creates a commit on the canonical repository. Even though the most recent changes were your additions, technically your fork and local repository do not have that "merge" commit and are now out-of-date with the canonical repo. So, what we will do now is learn how to close the loop after your MR is merged.

----
**Action:** Close the loop. 

1. Open Git Bash and make sure you are in your project's directory (reminder: use `cd`).
1. Pull down changes from the canonical repository (aka the "upstream" remote) by running `git pull upstream main`.
1. We now have changes locally that do not appear on our fork (aka the "origin" remote). So if we run `git status`, we get the message "Your branch is ahead of 'origin/main' by X commits".
1. Just like we did earlier, we can push our local changes to our fork by running `git push` (or `git push origin main` to be explicit).
1. Now when you run `git status`, you should see that everything is up-to-date and there is nothing to commit. 

You have successfully closed the loop after your MR was merged! Before you go on to the next section, your instructor will need to take an action. **Ping them to get them to do it, and wait until after they have confirmed things are ready before you move on to the next section.**


</details>

<hr>

<details>
<summary><h2>Get a collaborator's content locally</h2></summary>

Scenario: After your content was merged, a collaborator tells you that they added additional content. You want to keep working, but you don't want to duplicate anything they did. You now need to pull in their content to your local repository before you continue working. Don't worry, we have done this before. We just need to pull down any new changes from the canonical repository!

----
**Action:** Pull down a collaborator's contributions to the canonical repository. 

1. First, verify that you did indeed close the loop after merging your MR (see previous section).
1. Now, visit that canonical repository on GitLab and look at the commits (go to `https://code.usgs.gov/wma/dsp/trainings/gitflows-trainings/ds-gitflows-static-[username]` and click on "Code" | "Commits"). You should see a new commit that was not created by you. 
1. Click on the commit name to see what changes were made. Looks like your collaborator added the next section of the story! 
1. Our goal is to continue this work and add another section but first, we need to get our collaborator's changes locally. Before pulling down changes, verify that you don't have any uncommitted changes locally. Run `git status` and look for the phrase, "nothing to commit".
1. Next, pull their changes down using `git pull upstream main`. Remember, the "canonical repository" is referred to as the "upstream" remote in git commands.
1. Now when you open your `dryville_story.md` file locally, you should see the "Be Gone, Dirty Water" section is the last in the file. 

Great! You successfully pulled down contributions that someone else on your team made to the repository. Next, we will add another section. Please move onto the next section.


</details>

<hr>

<details>
<summary><h2>Add two new sections of the story</h2></summary>

Time to add on to this story. We've done this a couple times now, so the edit-save-add-commit pattern should be getting familiar.

----
**Action:** Add text for the next two sections and commit those changes.

1. **Ping your instructor and let them know that you have arrived at this step**. There is something that they need to do.
1. If you run `git status` in Git Bash  right now, you should see a message that says "nothing to commit" and also "Your branch is ahead of 'origin/main' by 1 commit" (that one commit is the one from your collaborator that has not yet been pushed to your fork). 
1. Open the `dryville_story.md` file on your computer and add the next section of [the story](https://www.usgs.gov/special-topic/water-science-school/science/story-water-dryville), which is called "Your First Flood". Keep the same formatting as before (`##` for the title, `[inline text](url)` for hyperlinks). Save the file.
1. If you run `git status` in Git Bash, you should see the words "modified: dryville_story.md". This means that Git detects your change. You will also see the words "no changes added to commit". This is because we still need to stage our changes. Note that you will still see "Your branch is ahead of 'origin/main' by 1 commit" - we still haven't pushed since we pulled down our collaborator's changes.
1. Run `git add dryville_story.md` to stage these changes so that they can be included in our next commit. Now when you run `git status`, you see that the "modified: dryville_story.md" change is listed under "Changes to be committed". We are now ready to make a commit.
1. Run `git commit -m "add your-first-flood section"` to make a commit.
1. Run `git status` again. We should be back to where we started. There is "nothing to commit" because we don't have any additional changes to the repository content - we already committed our changes. However, you will now see that it says "Your branch is ahead of 'origin/main' by 2 commits".
1. Now repeat for "Storing Water for a Rainy Day". Copy and paste text from [the complete story](https://www.usgs.gov/special-topic/water-science-school/science/story-water-dryville). Keep the same formatting as before (`##` for the title, `[inline text](url)` for hyperlinks). Save the file.
1. Run `git add dryville_story.md` to stage these changes.
1. Run `git commit -m "add storing-water-for-a-rainy-day section"` to make a commit.
1. Now `git status` shows that we are ahead of `origin/main` by 3 commits.

You have now made two new commits. Please move on to the next section.


</details>

<hr>

<details>
<summary><h2>Pull down more new changes from your collaborator</h2></summary>

In the last section, we made two commits that added two new sections of the story to our `dryville_story.md` file. Huzzah! Everything is peachy. However, while you were doing that, your collaborator also decided to add to the story and they committed before you. Now, we need to once again pull down their changes before moving on.

----
**Action:** Pull down your collaborator's most recent additions. 

1. **Do not proceed with this step until your instructor has verified that it's OK to go on!** (You pinged them in the last step, remember?)
1. First, verify that you did indeed complete the previous section.
1. Before pulling down changes, verify that you don't have any uncommitted changes locally. Run `git status` and look for the phrase, "nothing to commit".
1. Next, pull their changes down using `git pull upstream main`. 
1. Uh oh, there seems to be an issue. When we pulled down those changes, the message "CONFLICT (content): Merge conflict in dryville_story.md" appeared. We must have been editing the same line of the file as our collaborator.

Your first merge conflict! Everything will be OK, promise :) Please move on to the next section.


</details>

<hr>

<details>
<summary><h2>Conquer a merge conflict!</h2></summary>

In the last section, we pulled down changes from our collaborator and realized that there was a merge conflict. This occurs when you edit the same line of code. In this case, you both added on to the last line of the file. Don't worry - merge conflicts are not as intimidating as they may seem. Let's do this!

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

You start thinking... a [reservoir](https://www.usgs.gov/special-topic/water-science-school/science/lakes-and-reservoirs) (you can call it a lake) above town could really serve a lot of purposes. A lake will provide a place for you to have fun — go swimming, boating, catch catfish, and relax. You can run your water-supply intake pipes from the lake instead of from your creek, especially since the flood destroyed your water-intake pumping station. With a dam you can release only the amount of water you want into the creek below the dam, thus making sure you have just the right amount of water running in Dryville Creek at all times. A dam would even help prevent flooding downstream because you can hold extra rainfall and [runoff](https://www.usgs.gov/special-topic/water-science-school/science/runoff-surface-and-overland-water-runoff) during a storm and slowly release it afterward. You can build a bigger paddle wheel, or, better yet, construct a real [hydroelectric power plant](https://www.usgs.gov/special-topic/water-science-school/science/hydroelectric-power-water-use) in your dam to start generating electricity! More problems solved.
=======
## Storing Water for a Rainy Day

You start thinking... a reservoir (you can call it a lake) above town could really serve a lot of purposes. A lake will provide a place for you to have fun — go swimming, boating, catch catfish, and relax. You can run your water-supply intake pipes from the lake instead of from your creek, especially since the flood destroyed your water-intake pumping station. With a dam you can release only the amount of water you want into the creek below the dam, thus making sure you have just the right amount of water running in Dryville Creek at all times. A dam would even help prevent flooding downstream because you can hold extra rainfall and runoff during a storm and slowly release it afterward. You can build a bigger paddle wheel, or, better yet, construct a real hydroelectric power plant in your dam to start generating electricity! More problems solved.
>>>>>>> afd002e4b66f31f815e4236ffa6ea3e17f127e1d
```

5. Now, continuing on. Examine the differences between the "Storing Water for a Rainy Day" sections. Can you find any?
6. The only difference should be that your version (the top one) has markdown hyperlinks, while the version that is being merged does not. So, we actually want to keep only the version that you created. 
7. Delete the content between `=======` and `>>>>>>>`.
8. Now you are left with the merge conflict symbols and the correct version of the "Storing Water for a Rainy Day" section. Delete all of the symbols related to the merge conflict (`<<<<<<< HEAD`, `=======`, and `>>>>>>> [random letters/numbers]`). Now, you should be back to where you started (which happens in merge conflict resolution sometimes).
9. Save the file.
10. The last step for resolving a merge confict is to commit your changes. Follow the same pattern as before. Running `git status` will show you that you have an unresolved merge conflict. Just as before, run `git add dryville_story.md` to stage your changed file. Then commit by running `git commit -m "resolve merge conflict"`. 
11. Now, when you run `git status` you will see that you don't have any changes to commit (but your branch still ahead of origin/main - see next section).

You successfully resolved a conflict! Please move on to the next section.


</details>

<hr>

<details>
<summary><h2>Request newest set of changes be merged to the canonical repo</h2></summary>

We are now ready to push our local changes (including the resolved merge conflict) up to our fork (aka remote "origin"). Then, we can open a merge request (MR). 

----
**Action:** Push your changes to your GitLab fork and open an MR. 

1. If you run `git status` in Git Bash  right now, you should see a message that says "nothing to commit" and also "Your branch is ahead of 'origin/main' by X commits". Our local version has new changes that do not appear in our fork (aka the remote `origin` because our local version *originated* from it). 
1. Just as before, we need to "push" our local changes to our remote fork. Run `git push origin main` to do so. 
1. Go to **your fork's** webpage (`https://code.usgs.gov/[username]/ds-gitflows-[username]`) and click to the "Code" | "Commits" tab. You should see your new commit messages there, something like this:
![commits-after-conflict](https://code.usgs.gov/wma/dsp/trainings/ds-gitflows-static-template/uploads/157a9d82304e10ef9358448954a88e49/commits-after-conflict.png)

1. Now, click the "Code" | "Repository" tab to go back to your fork's home page. Look near the top to confirm that you're "Forked from Water Mission Area / Data Science Practitioners / Trainings / gitflows trainings / ds-gitflows-[username]" and "X commmits ahead of the upstream repository." To the right of that text, click the "Create merge request" button.
![create-MR-after-conflict](https://code.usgs.gov/wma/dsp/trainings/ds-gitflows-static-template/uploads/fd9c6e179ddcffb14735048f676860b5/create-MR-after-conflict.png)

1. Before your merge request is actually created, you need to verify that you are requesting the correct changes be merged with the correct repository. Remember, we are not working with branches, so don't worry about the fields that say "main". However, you should verify that the merge request will merge from your fork into the project canonical repo. In other words, the text at the top of the "New merge request" page should say "From [username]/ds-gitflows-[username]:main into wma/dsp/trainings/gitflows-trainings/ds-gitflows-[username]:main".
1. Add a title to your merge request and a description about your changes. 
1. Click the down symbol in the `Reviewer` box and select the username of your course instructor as the reviewer from the drop-down menu. If you do not have the option to add a reviewer, create the merge quest and add the reviewer afterward.
1. Now, click the "Create merge request" button.

You have successfully made a second merge request! Wait for your MR to be reviewed and merged. Once your MR has been merged, you can move on to the next section.


</details>

<hr>

<details>
<summary><h2>Close another loop after a merged MR</h2></summary>

Your MR was merged! Yay! Now, remember that "closing the loop" thing we did after our last MR was merged? Let's do it again.

Merging an MR creates a commit on the canonical repository. Even though the most recent changes were your additions, technically your fork and local repository do not have that "merge" commit and are now out-of-date with the canonical repo. So, we need to close the loop.

----
**Action:** Close the loop. 

1. Open Git Bash and make sure you are in your project's directory (reminder: use `cd`).
1. Pull down changes from the canonical repository (aka the "upstream" remote) by running `git pull upstream main`.
1. We now have changes locally that do not appear on our fork (aka the "origin" remote). So if we run `git status`, we get the message "Your branch is ahead of 'origin/main' by X commits".
1. Just like we did earlier, we can push our local changes to our fork by running `git push` (or `git push origin main` to be explicit).
1. Now when you run `git status`, you should see that everything is up-to-date and there is nothing to commit. 

You have once again closed the loop after your MR was merged! Please move on to the next section.

</details>

<hr>

<details>
<summary><h2>Using a gitignore file</h2></summary>

The last topic we are going to cover in this tutorial is the `.gitignore` file. These files are used when you have a local file that you don't want to track changes to in a commit or put on GitLab. You simply add the name of the file (including directory structure when applicable) to the `.gitignore` file to have Git *ignore* it (see what they did there?). This practice is often used for intermediate files created by processes within your repo, temporary files, or really large data that need to be stored elsewhere. Additional information about `.gitignore` files can be found in [this article](https://www.pluralsight.com/guides/how-to-use-gitignore-file).

----
**Action:** Add a file and then gitignore it.

1. First, open the `.gitignore` file that is in your local directory using a text editor (for example, Notepad++). It should be completely empty.
1. Next, download [this image](https://d9-wret.s3.us-west-2.amazonaws.com/assets/palladium/production/s3fs-public/styles/side_image/public/thumbnails/image/wss-icon-small-teacher.png?itok=PZHHzOTP) (right click and choose "Save image as") and save as `wss-icon-small-teacher.png` in your `ds-gitflows-[username]` folder. 
1. Now in Git Bash, run `ls` to "list" the items in your current working directory. You should see about 10 files, three of which are `course-instructions.md`, `dryville_story.md`, and `wss-icon-small-teacher.png`. Note that the `.gitignore` file doesn't show up with `ls` because it is technically a "hidden" file (starts with a `.`).
1. So, you've added a new file to your repository. Now, run `git status`. Git shows that `wss-icon-small-teacher.png` is an untracked file. We could leave it like that and just try to remember to not commit it, but that seems risky. The more foolproof way is to to add it to the `.gitignore` file.  
1. Add `wss-icon-small-teacher.png` to the `.gitignore` file. Save the file.
1. Now run `git status`. It no longer shows `wss-icon-small-teacher.png` as an untracked file, but instead shows that we have modified `.gitignore`. That is because this file is version controlled - whenever we change it, we push those changes to the upstream repository so that everyone uses the same one. 
1. Now, commit your changes to `.gitignore` and push to your fork.  
```
git add .gitignore
git commit -m "add downloaded image to gitignore"
git push origin main
```
8. Finally, create a merge request. Make sure to add your course contact as the reviewer of your MR. Revisit the "Request to add your changes to the canonical repo" section of this course-instructions.md doc if you need any reminders for how to do this.

Once you open your MR, wait for it to be reviewed and merged. Once your MR has been merged, close this issue and go to the next one.

</details>

<hr>

<details>
<summary><h2>In conclusion ...</h2></summary>

Welcome to the end of the hands on tutorial with Git and GitLab! You have now been exposed and practiced the basic workflow that USGS Data Science uses for collaborating on codebases. See the bottom of this issue for instructions about next steps.

## The conceptual diagram of the workflow you just learned/used 

![image](https://user-images.githubusercontent.com/13220910/81212707-dfc22680-8f9a-11ea-8fc8-ad0d960d8207.png)

## A summary list of commands that were used.

### Setting up a new project

1. Fork the canonical repo to your username.
1. Create a local copy of your fork - copy the SSH URL from **your fork's** GitLab page, then in Git Bash run `git clone [insert your fork's SSH URL]`.
1. Add the canonical repo as a remote to your local version - copy the SSH URL from **the canonical repo's** GitLab page, then in Git Bash run `git remote add upstream [insert canonical repo's SSH URL]`.
1. Verify that you are ready to go with remotes - run `git remote -v` and check that your fork's URL is next to `origin` and the canonical repo is listed next to `upstream`.

### Saving a change locally

1. Change the file(s).
1. Inspect what changes git detects - run `git status`
1. Stage the files that you want to include in your commit - `git add [insert file name]`. Pro tip: use `git add .` to stage all changed files listed with `git status`.
1. Commit your staged changes - `git commit -m "[commit message here]"`

### Moving your local commits to your fork

1. Run `git push origin main`
1. Look at the "Code" | "Commits" tab on your fork on GitLab to see your new commits.

### Adding your changes to the canonical repository

1. Once you have changes on your fork that make it different from the canonical repository, go to your fork's GitLab page and click "New merge request". 
1. In the next screen, verify that the `From` repository is your personal fork and the `into` repository is the canonical fork. 
1. Click "Create merge request".
1. Add a title and description. Include your course contact as a reviewer.
1. The reviewer will merge the changes.
1. Close the loop by pulling down the changes from upstream to your local repo - `git pull upstream main`

### Handling merge conflicts

1. If you have a merge conflict after pulling down changes, look in the file(s) that have been flagged as having conflicts.
1. Inspect the content between `<<<<<<< HEAD` and `=======`, which is the content that existed before the merge (likely your local content).
1. Now inspect the content between `=======` and `>>>>>>> [string of letters and numbers]`, which is the content that is trying to be merged with what currently exists locally (likely the remote content).
1. Decide what of that content to keep and what to delete.
1. Remove the merge conflict symbols, `<<<<<<< HEAD`, `=======`, and `>>>>>>> [string of letters and numbers]`.
1. Save the file and then commit your merge resolution (see above for making commits). The commit message "resolve merge conflict" is often used.

## Feeling confident? Explore more!

There is a lot more Git that can be learned, but the above are the basics that will probably be enough for awhile. As you start to get more advanced, there may be some additional concepts/commands you should learn such as, 

* Temporarily hiding changes in order to pull upstream changes to avoid conflicts (`git stash`, `git stash apply`),
* branching (`git switch -c`), and
* [much more!](https://git-scm.com/doc)
</details>

<details>
<summary><h2>One last thing...</h2></summary>

![Minions Bob, Stuart, and Kevin expressing jubilation](archive/img/81443707-86452d80-913b-11ea-9ad4-7be24ff64c39.gif)

Congratulations - you completed the tutorial!

</details>

<hr>
