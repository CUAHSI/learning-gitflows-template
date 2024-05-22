Scenario: You are pointed to a code repository on GitHub (this one) for a project that you just joined. You need to start contributing to this codebase. Where do you start? 

You may know that you can use git version control and/or GitHub to make and save changes (commit), and merge those changes into the main code (pull request). Within the realm of these technologies, there are several different workflows that can be followed. The one we are focusing on here is known as the "fork-and-pull workflow". This will give you a broad base that will enable you to adapt to other workflows as necessary.

![image](https://user-images.githubusercontent.com/13220910/81212295-4bf05a80-8f9a-11ea-8302-99a231f61480.png)

There is a main version of the code that people are collaboratively developing. Each contributor has their own version of this code online and locally. Changes are made locally, sent to their online version, and then combined with the collaborative version of the code. Contributors are able to get the changes from other users by syncing their local version with the collaborative version of the code. Now let's look at that workflow using Git + GitHub terminology.

![image](https://user-images.githubusercontent.com/13220910/155410782-77ba4334-9253-4e1e-a5f0-ac779569fc6d.png)

There is a main version of the code that people are collaboratively developing (`upstream repository`). Each contributor has their own version of this code online (`forked repository`) and locally (`cloned repository`). Changes are saved locally (`commit`), sent to their online version (`pushed to their fork`), and then combined with the collaborative version of the code (`merged with a pull request`). Contributors are able to get the changes from other users by syncing their local version with the collaborative version of the code (`pull the upstream repository`).

We are going to walk through each of these steps within the workflow in this lesson. We will also learn about merge conflicts and what a `.gitignore` file is all about. 

----
**Action:** Close this issue after you read about the workflow and proceed to the next issue in sequential order.
