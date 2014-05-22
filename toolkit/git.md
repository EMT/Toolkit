Git Bits ‘n’ Pieces
===================

Without version control, multiple developers working on the same code projects would soon find themselves
(accidentally) overwriting and clashing with the work of others. With version control, all developers can 
work independently and, when ready, safely merge their code into a shared repository.

By its very nature, version control records a comprehensive history of each project it's used on. This allows us to roll back to previous states
if anyone accidentally introduces bugs or mistakes.

Git is Fieldwork's version control system of choice.


#### New to Git?

If you're absolutely brand new to Git, rather than re-inventing the wheel and writing a complete manual here, we recommend you spend some time learning the basics.
You might find [this tutorial](https://www.atlassian.com/git/tutorial/git-basics) helpful in getting you up and running.

## Tips and Tricks

###Git Ignore
Every project should have a .gitignore file in its root directory to stop certain files from being needlessly tracked. Setting this up in the first
commit saves you the hassle of dealing with the problem later on. Here is what Fieldwork's default .gitignore looks like (lines beginning with `#` are comments):

	# All .DS_Store files (created by OSX to store custom attributes of a folder)
    .DS_Store

	# All files in all sass-cache folders (created by Sass to speed up compilation speed)
    *.sass-cache*

Various projects using various frameworks will probably need other folders and files to be put in .gitignore. For examples, [see here](https://github.com/github/gitignore).

If you're working on a project with stray .DS_Store files in it, you can remove them all with the following line

    find . -name .DS_Store -print0 | xargs -0 git rm --ignore-unmatch

Then commit the changes.

(It's worth noting that .gitignore will only ignore matching files that are *not* already in the repository)

###Patch mode
Sometimes you'll find that when the time comes to add a file to the staging index, the file has two modifications that are unrelated to each other.
As a general principle, you should try to put unrelated changes in separate commits. You can do this by adding the file with `git add -p` or `git add --patch`.

Git then splits the file into logical hunks of code and presents you with an interactive prompt where you can decide whether you want to stage the current hunk, skip, or split it into even smaller pieces.

###Autocorrect
If you've ever made a typo when running a Git command, you may have noticed Git sometimes replies with a "did you mean...?" question. Currently there's no way to answer this with a "y" or "n", but you can utilise Git's autocorrect feature by typing

	git config --global help.autocorrect 5

The number above represents a time in units of 100ms. From now on, git will automatically rerun what you typed, with the autocorrected command, after a delay of 0.5 seconds. If you don't want Git to execute the autocorrected command, press <kbd>ctrl</kbd>+<kbd>c</kbd>, before the time elapses.

###Creating, pushing to, and tracking new branches

If you're working on a new feature, it's a good idea to create a new branch. This is so if a bug arises in existing code before your new feature is ready, you can easily fix it in the original branch without it getting embroiled in your semi-completed new feature.

To create a new branch (such as "my-new-feature") type the following: 

	git branch my-new-feature
	git checkout my-new-feature

You can do the above two lines in one fell swoop with

	git checkout -b my-new-feature

To push the new branch to a remote, use the following:

	git push -u origin my-new-feature

The `-u` option sets up tracking meaning in the future when we do a `git pull` or `git push` we don't need to specify branch names.



###Submodules
If, for example, we're working on a lithium project, we want to easily keep the Lithium core up to date. To help with this, we can load it as a submodule.
When you first clone a project that contains submodules, you get the directories that contain the submodules, but none of the files yet. To get these files,
you need to run two commands: 

`git submodule init`

initializes your local configuration file (.gitmodules), and 

`git submodule update` 

fetches all the data from that project.

If you ever need to change any of the URLs in the file, you need to run 

`git submodule sync`

This means that next time you try to update the submodules, git will look for them at the new address.


###Quitting Vim

For various reasons (such as forgetting the `-m` option during a commit), Git will sometimes open up Vim for you to type a commit message. It's not obvious how to exit Vim, so, when you want to quit,
press <kbd>ESC</kbd> to get into command mode. Then type `:q` and press enter.