# Git Guide CS 125
(**Trigger Warning**: I'm only slightly less of a noob than y'all so be nice and pls tell me if something here is incorrect.)

### Other Guides
There is already an intro to git / version control [on the 125 website](https://cs125.cs.illinois.edu/MP/setup/git/). Read this first for a refresher on the importance of version control. This guide will be about using git to collaborate on [MP7](https://cs125.cs.illinois.edu/MP/7/). There are also much more complete guides such as the [Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials/what-is-version-control) or [Git's own tutorial](https://git-scm.com/docs/gittutorial). These tutorials cover about everything you need to know about git but may be a bit cumbersome for newcomers. This guide will be about quickly setting up a repository for you and your partner to easily collaborate on MP7.

### Creating a new repo on GitHub
You wont be able to collaborate without a shared git repository.
First, have one partner [create a new repository](https://github.com/new) on GitHub. Give it an apropriate name and description. Make sure it is <b>public</b> and <b>don't</b> add any initial files.

<img src="/img/new_repo.png" alt="new_repo.png"/>

### Creating a new repo on your computer
A new repo on GitHub is useless if you and you partner can't access it on your own machines. Have one partner navigate to directory of your project. (Probably something like `/path/to/AndroidStudioProjects/my_cool_mp7_project/`) If you haven't yet created you project do so now.

Next open the terminal in this directory. On linux you probably have an option to `right click` -> `open terminal here`. On windows, `right click` -> `git bash here`. On mac you will have to open the terminal the usual way then `cd` into your projects directory. (Unless you have [enabled the option](https://lifehacker.com/launch-an-os-x-terminal-window-from-a-specific-folder-1466745514))

Now you can initialize the repository with `git init`. If you run `git status` you will see a bunch of red "untracked files". These files need to be staged so you can commit them. (More on that [here](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)) You can add all files with `git add .` or add files individually with `git add /path/to/my_file.ext`. If you run `git status` again you will see that your files have been staged and are now colored green.

Now that your files are staged you can commit them with `git commit` this will pull up your default editor, which is probably [vim](https://www.vim.org/) or [nano](https://www.nano-editor.org/). If it's vim you might have some issues. The editor is opened so you can write a commit message. If you want to avoid the struggles of [closing vim](https://itsfoss.com/how-to-exit-vim/), you can also specify a commit message in the command itself `git commit -m "my commit message"`.

Lastly you have to add the remote repository you made on GitHub and push your changes. This can be done with `git remote add origin https://github.com/myusername/my_repo_name.git` and `git push -u origin master`.

Congratulations! You have created your first git repository on GitHub!

Here are the steps more succinctly:
```
cd /path/to/AndroidStudioProjects/my_cool_mp7_project/
git init
git add .
git commit -m "my commit message"
git remote add origin https://github.com/myusername/my_repo_name.git
git push -u origin master
```

### Adding your partner

In order for you guys to collaborate you first need to add your partner as a collaborator. This will give them commit access in your repo (only you have commit access by default). You can find collaborators in the settings tab of your repository's GitHub page.

<img src="/img/find_collaborators.png" alt="find_collaborators.png"/>

Seach for your partner's GitHub username. <b>Make sure you chose the correct one.</b>

<img src="/img/collaborate.png" alt="collaborate.png"/>

When you add them as a collaborator they will be sent an email. Once they accept, they will have to clone your repo.

From the point of view of the partner who did not create the repo the command is:

```
git clone https://github.com/mypartnersusername/their_repo_name.git
```

### General Git Workflow
(For both partners)

Every time you make a significant change you cant stage the changes with `git add my_changed_file.ext` (to add my_changed_file.ext) or `git add .` to add all files. Changes are committed with `git commit` (to write the commit message in the editor) or `git commit -m "my commit message"` (you probably want to use this one). Push to GitHub with `git push origin master` (<b>Always after you commit though</b>).

Again, after you make changes:

```
git add .
git commit -m "my commit message"
git push origin master
```

To retrieve changes that your partner has made:
```
git pull --no-edit
```

### Review

To be done once after creating your repository:

```
cd /path/to/AndroidStudioProjects/my_cool_mp7_project/
git init
git add .
git commit -m "my commit message"
git remote add origin https://github.com/myusername/my_repo_name.git
git push -u origin master
```

To be done once by the partner who did not create the repository:

```
git clone https://github.com/mypartnersusername/their_repo_name.git
```

To be done every time you want to commit and push changes:

```
git add .
git commit -m "my commit message"
git push origin master
```

To be done every time you want to pull your partners changes:

```
git pull --no-edit
```
