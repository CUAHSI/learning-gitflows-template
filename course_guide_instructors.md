# Course Facilitation Guide

This template repository contains the starting content to teach the common open-source, fork-and-pull style workflow. For the full experience, it requires a course contact to review and merge pull requests. It is currently available as either static instructions (participants read through a single document and a course contact must take actions beyond the PR reviews) or a dynamic course (participants complete separate GitHub issues and closing issues triggers certain actions automatically). Both of these course types require participants to actually use Git commands locally and interact with GitHub repositories.

## Actions you take before the course

### 1. Send an email or message with initial setup instructions

Course participants will need to do some preparation prior to starting the course, including some software setup. Make sure they send you their GitHub usernames as quickly as possible!

Below is a suggested email/message:

> Hello [ LEARNER'S NAME ], 
> 
> Thanks for your interest in learning Git and GitHub for collaborative coding! My name is [ YOUR NAME ] and I will be your point-of-contact throughout this course.
> 
> Before you can start the tutorial itself, there are few required technical steps to get setup. Please complete the steps below and reach out if you have any issues.
> 
> 1. [Create a GitHub account](https://docs.github.com/en/get-started/start-your-journey/creating-an-account-on-github#signing-up-for-a-new-personal-account) if you do not already have one. 
> 1. Reply to me with your GitHub username.
> 1. [Download and install Git.](https://git-scm.com/downloads)
> 1. Prepare your GitHub account to communicate with your local computer by [setting up SSH keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account). This is an important step in the Git/GitHub setup process! It can also be somewhat confusing. Make sure you read and execute any of the "Prerequisite" steps listed in the link. These setup steps give you instructions that will require interaction with the [command line](https://www.g2.com/articles/command-line-interface) by having your copy/paste and execute short commands. To access the command line interface, open the application "Command Prompt" if you are on a Windows machine and "Terminal" if you are on a Mac.
> 
> If you are completely new to the ideas of collaborative coding through Git and GitHub, we recommend watching a couple of videos to become familiar with the terminology and general concepts before diving into the interactive course.
> 
> - [Introduction to Open Source Vocabulary - Part 1](https://www.youtube.com/watch?v=ViC0j7jjKnU) (~10 minutes). A good primer for folks that are new to these concepts and terminology before they start this course.
> - [Introduction to Open Source Vocabulary - Part 2](https://www.youtube.com/watch?v=kIMNgGfwvMA) (~11 minutes). This video dives deeper into how collaborative and open source coding projects evolve and common files that you will see. 
> 
> We are so excited for you to learn more about collaborative coding through Git and GitHub. Again, reach out with any issues or questions and send your GitHub username as soon as possible so that I can get the rest of the course prepared for you!
> 
> Thank you,
> [YOUR NAME]

### 2. Setup the learning repos

Every participant taking this course will need their own repo based on this template. A course facilitator will need to take action here. Before you do this, you will need to collect the GitHub usernames of each participant as requested in the initial message/email that went out to participants (see previous step). Once you have that information, you can run through the repo setup steps below.

1. Create the new repository using the "Use this template" button near the top and name the repo `learning-gitflows-[username]`. DO NOT check the box that says "Include all branches". You can optionally fill in the repo description with "Git training repo for [ Learner's Name ]". Then choose "Create repository".
1. Customize/cleanup the repo. Follow the additional instructions below this list depending on whether you are offering this course as the static or dynamic version. Then return here to do step 3.
1. Change the settings so that PRs cannot be merged without a review. Go to Settings > Branches > Click "Edit" next to `main`. Then, check the boxes next to `Require a pull request before merging` and `Require approvals`. Make sure the required number of approvals is set to 1. See image below this list for an example of what this should look like.
1. Invite the participant as a collaborator to this new repository.

![image](https://github.com/CUAHSI/learning-gitflows-template/assets/13220910/7d8516d9-6249-4ba4-9f6d-59b5ecb7c074)

#### Static course repo setup

After following the instructions for creating the new repo (they are the same for both static and dynamic courses), complete the following actions **in each** participant's course repo.

Delete the following folders/files:

- `.github`
- `course_guide_learners_dynamic.md`
- `course_guide_instructors.md`

Rename `course_guide_learners_static.md` to `course_guide.md`.

#### Dynamic course repo setup

After following the instructions for creating the new repo described above (they are the same for both static and dynamic courses), **each** participant's course repo will need to be starred (it might need to be a specific person) to kick-off the setup GitHub Actions workflow which will remove unneeded files, rename the correct course guide markdown file, and create all the issues.

TODO: See [Issue #10](https://github.com/CUAHSI/learning-gitflows-template/issues/10) because the dynamic course may not yet be functioning. 

### 3. Send particpants a follow-up with their individual course links

To actually start the course, you will need to send each participant their individual repo link and suggest navigating directly to the `course_guide.md` file. Below is an example message you could use. 

> Hello [ LEARNER'S NAME ],
> 
> Now that you have completed all of the required technical steps, you can get started with our interactive course! Follow the steps below to get started.
> 
> 1. Login to your GitHub account.
> 1. Accept the invitation to be a collaborator on your new repo if you haven't already.
> 1. Navigate to the main repository for your course: [INSERT LINK]. We will often refer to this link as `www.github.com/[org]/learning-gitflows-[username]` throughout the course.
> 1. Open the file `course_guide.md` and follow along with what it says to do. Consider opening a new tab or window so that you can easily flip back-and-forth between the instructions and the activities.
> 
> There will be specific times throughout the course that you need to tag me, your course contact. When you do this, you will need to use my GitHub user account: `[ YOUR GITHUB USER ]`.
> 
> If you are having any issues along the way, you can also send me a message here to reach me outside of GitHub.
> 
> Good luck and have fun!
> 
> Best,
> [ YOUR NAME ]

If you are sending this out to a lot of people, consider making a table with their name in one column and their course link in another. Then, change the instructions in step 3 below to point people to the table.

## Actions for the course contact while someone takes the course

If you are named as a course contact for someone who is taking the course, the following outlines and describes what is expected as they progress through the tutorial. The expectations are slightly different depending on whether someone is taking the static course or the dynamic course.

### Static course

For the static course, you will need to have the repo setup locally in order to perform some of the actions as someone progresses through the tutorial. If you expect to be the course contact for more than one person, consider making a folder in which to store all of these repos.

```bash
git clone git@github.com:[org]/learning-gitflows-[username].git
cd learning-gitflows-[username]
```

There are five places where you *must* take action and be ready to help move someone along. There may be other times that a learner reaches out with a question but these are the necessary actions that you must take to move the course forward:

1. **Between steps 8 and 9: approve and merge their very first PR.** Step 8 (called `Request to add your changes to the canonical repo`) instructs a learner to open a new PR that should contain two commits both with changes to the `dryville_story.md` file. The first commit adds three paragraphs under a header called `## Getting Water to Your Homes`. You should expect to see three hyperlinks, one in each paragraph, for the phrases/words `over 8 pounds a gallon`, `Water does flow downhill`, and `creek`. The second commit adds two paragraphs under the header `## Dryville's First Water Works`. There is only one hyperlink here for the words `aqueduct system`. They need those elements + a title + a brief description. If all of those things exist, you can [approve the PR](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/approving-a-pull-request-with-required-reviews) and then merge it. They should get confirmation that they can move on but you can also add a comment that explicitly says "You're all set to move on to the next step!" 

2. **Between steps 9 and 10: commit new content as a collaborator.** After they close the loop from their merged PR to their local repo in Step 9, they will reach out to you to say that they have done so. At this time you should commit new content to mimic a real world scenario where a collaborator adds content. First, make sure you pull down their changes with a `git pull origin main`. Then, copy and paste the contents of [this file](https://github.com/CUAHSI/learning-gitflows-template/blob/main/.github/commit_content/be_gone_dirty_water.md) to the bottom of the `dryville_story.md` (make sure the hyperlink is included). Then, run the commands below to commit and push the change up to the repo. Once you see your commit up there, let them know they can continue to Step 10 `Get a collaborator's content locally` in the course.

```bash
git add dryville_story.md
git commit -m "add be-gone-dirty-water section"
git push origin main
```

3. **During Step 11: commit a change to initiate a merge conflict.** After they successfully pull down your content in Step 10, they will reach out letting you know they are starting Step 11 `Add two new sections of the story`. In this step, they will add two new sections to the story during Step 11. At the same time, you will also make a commit to this file and create a merge conflict. Your commit will include *almost* the same content as their second commit which adds a section with the header `## Storing Water for a Rainy Day`. The main difference is that your commit will not have a hyperlink on the word `reservoir`. To make the commit, first make sure you are up-to-date by running `git pull origin main`. Then, copy and paste the content from [this file](https://github.com/CUAHSI/learning-gitflows-template/blob/main/.github/commit_content/storing_water.md) to the bottom of the `dryville_story.md` file (there *should not* be any hyperlinks in this new section). Now run these commands to commit and push this change.

```bash
git add dryville_story.md
git commit -m "add storing-water section"
git push origin main
```

4. **Between steps 14 and 15: approve and merge the second pull request.** After they successfully conquer a merge request, they should have added two new sections to the Dryville story document and will send you a pull request to review with these additions. This PR should have 3 commits: one that adds the section `## Your First Flood`, one that adds the section `## Storing Water for a Rainy Day`, and one that resolves the merge conflict. In the end they should only have the three paragraphs of text between these two new header sections, no remaining merge conflict symbols, and the word `reservoir` in the first sentence of the second section should be a hyperlink (this was the result of the merge conflict resolution). There should also be a reasonable title and description. If they have all of these elements, you can [approve the PR](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/approving-a-pull-request-with-required-reviews) and then merge it. They should get confirmation that they can move on but you can also add a comment that explicitly says "You're all set to move on to the next step!"

5. **Between steps 16 and 17: approve and merge the third and final pull request.** Step 16 introduces the idea of a `.gitignore` file. This file already exists in the repository but their open PR should contain a new line with the name `wss-icon-small-teacher.png` to gitignore this image. Check that their PR has a title, description, and only the one change in the `.gitignore` file. Make a comment requesting changes or describing why something is different than you expected if their PR does not match those expectations. If it does, you can [approve the PR](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/approving-a-pull-request-with-required-reviews) and then merge it. They should get confirmation that they can move on but you can also add a comment that explicitly says "You're all set to move on to the next step!". This last step is just closing out their course with some final thoughts and information. No further action is needed from you to move them along.

### Dynamic course

For the dynamic course option, there are three places where you *must* take action and be ready to help move someone along. However, you do not need to setup the repo locally. Your actions can be completed on GitHub. Besides those three actions, the course will progress by the individual closing issues and the GitHub Actions Bot reacting to certain events, though there may be other times that a learner reaches out with a question.

Rather than duplicating instructions, we will point you to the actions described in the static course contact section above. Numbers 1, 4, and 5 from the static course contact instructions represent the actions you must take in the dynamic course. One exception is that in addition to the elements listed, you should confirm or point out that learners can start their PR description with the phrase `Fixes #X` in order to autoclose an issue. At a minimum, learners should link to the issue they are resolving in their description before you approve and merge.

Numbers 2 and 3 from the static course contact instructions represent the manual work that a course contact must do to replace GitHub Actions in the static version of the course. You do not need to do either of those here since a GitHub Action will do it for you. Instead, just know what is supposed to happen. In number 2 above, a GitHub Action to add collaborator content is triggered when Issue 9 closes. In number 3 above, a GitHub Action to add content that creates a merge conflict is triggered when Issue 10 closes.

TODO: See [Issue #10](https://github.com/CUAHSI/learning-gitflows-template/issues/10) because the dynamic course may not yet be functioning. 
