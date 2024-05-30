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

You have successfully closed the loop after your PR was merged! Close this issue and move to the next one.
