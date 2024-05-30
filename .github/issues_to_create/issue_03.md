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

You have now successfully cloned your fork! Close this issue and move on to the next one.
