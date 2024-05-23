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

The following actions need to happen **in each** participant's course repo.

Delete the following folders/files:

- `.github`
- `course_guide_learners_dynamic.md`
- `course_guide_instructors.md`

Rename `course_guide_learners_static.md` to `course_guide.md`.

#### Dynamic course repo setup

For **each** participant's course repo, star the repo (it might need to be a specific person) to kick-off the setup GitHub Actions workflow which will remove unneeded files, rename the correct course guide markdown file, and create all the issues.

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
> 1. Open the file `course_instructions.md` and follow along with what it says to do. Consider opening a new tab or window so that you can easily flip back-and-forth between the instructions and the activities.
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

For the static course, you will need to have the repo setup locally in order to perform two actions as someone progresses through the tutorial.

TODO: FILL IN INSTRUCTIONS [BELOW ARE THE OLD ONES]

1. For each participant, create a new blank project in the ["gitflows trainings" group](https://code.usgs.gov/wma/dsp/trainings/gitflows-trainings). Use the naming convention `ds-gitflows-[username]` for each participant. Choose "Internal" visibility. Do not allow the system to create a README. These will be considered the canonical repositories for each participant.
1. Set the project you just created to be accessible by the user. Manage -> Members -> Invite Members. **Use the "Developer" role.**
1. In the project you just created, go to Settings -> Repository, choose "Protected branches", and set `main` up to be protected with permissions like this: ![](archive/img/protected_branch_settings.PNG)
1. For each participant, clone the repo you are looking at now to a fresh directory on your local computer, and then push it to the project you just created in the step above. Use commands like the following:

```bash
git clone git@code.usgs.gov:wma/dsp/trainings/ds-gitflows-static-template.git scratch_directory
cd scratch_directory
git remote rename origin old-origin
git remote add origin git@code.usgs.gov:wma/dsp/trainings/gitflows-trainings/ds-gitflows-[username]
git push -u origin
cd ..
rm -rf scratch_directory
```

### Dynamic course

TODO: FILL IN INSTRUCTIONS

TODO: See [Issue #10](https://github.com/CUAHSI/learning-gitflows-template/issues/10) because the dynamic course may not yet be functioning. 
