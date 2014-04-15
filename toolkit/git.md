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

###Patch mode
Sometimes you'll find that when the time comes to add a file to the staging index, the file has two modifications that are unrelated to each other.
As a general principle, you should try to put unrelated changes in separate commits. You can do this by adding the file with `git add -p` or `git add --patch`.

Git then splits the file into logical hunks of code and presents you with an interactive prompt where you can decide whether you want to stage the current hunk, skip, or split it into even smaller pieces.

###Autocorrect
If you've ever made a typo when running a Git command, you may have noticed Git sometimes replies with a "did you mean...?" question. Currently there's no way to answer this with a "y" or "n", but you can utilise Git's autocorrect feature by typing

`git config --global help.autocorrect 5`

The number above represents a time in units of 100ms. From now on, git will automatically rerun what you typed, with the autocorrected command, after a delay of 0.5 seconds. If you don't want Git to execute the autocorrected command, press <kbd>ctrl</kbd>+<kbd>c</kbd>, before the time elapses.