The next step in our workflow is to clone your fork. This creates a local copy of the repository that is specific to your user on GitHub. The local copy is where you will make changes to the codebase. 

----
**Action:** Clone this repo!

1. Open the GitHub page for your fork, e.g. `https://github.com/[username]/learning-gitflows-[username]`. *A navigation note*: from your fork, you can easily navigate back to the canonical repository by clicking the link next to "forked from" at the top, just below your forked repository name. From the canonical repo page, you can get back to your fork by clicking the fork button on the canonical repo and choosing your existing fork from the list.
2. Click the green `Code` button that has a drop down arrow. Again, make sure you are ***on your fork***. This means that you see `[username]/learning-gitflows-[username]` at the top of the page with `forked from [org]/learning-gitflows-[username]` underneath.
3. Copy the SSH address, not the HTTPS one (see image below). We should have already set up your SSH keys, but if not, follow [these instructions to generate an SSH key](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) and [these instructions to add the SSH key to your GitHub account](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account). When you come back to the page, you should have the SSH option.

![image](https://github.com/CUAHSI/learning-gitflows-template/assets/13220910/03273273-ebc7-4d7f-955c-dfaedf68edaa)

4. Open Git Bash on your computer.
5. Change the working directory ([use `cd`](https://stackoverflow.com/questions/17753986/how-to-change-directory-using-windows-command-line)) to the location where you would like to create the cloned directory. I would recommend creating a folder somewhere in your D drive to put GitHub projects.
6. Type `git clone [insert URL]` and hit enter, e.g. `git clone git@github.com:[username]/learning-gitflows-[username].git`. Note that you cannot CTRL+V to paste into Git Bash. Right click and choose paste instead.
7. A new folder with the same name as the repository is now available in your working directory. In the folder, you will find the same files and file structure that you can see on GitHub.
8. While in the folder, run the command 'git config pull.rebase false'. This will keep a confusing error message from arising later on.

You have now successfully cloned your fork! Close this issue and move on to the next one.
