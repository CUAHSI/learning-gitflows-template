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

You have now successfully created a PR! Wait for your PR to be reviewed and merged. Once your PR has been merged, close this issue and move on to the next one.
