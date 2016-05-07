# Git-Hooks

Git-Hooks is a tool to manage project, user, and global Git hooks for multiple git repositories.

git-hooks lets hooks be installed inside git repositories, users home directory, and globally.  
When a hook is called by `git`, git-hooks will check each of these locations for the hooks to run.


Install
=======

Run `./build/build` to add git-hooks to bin directory.

Run `./build/add-git-hooks` to add default hooks to user directory.

Run `git hooks --install` in a git project tell it to use git-hooks hooks.  You can run `git hooks --uninstall` at any time to revert to your previous hooks.  (These are usually the default hooks, which do nothing.)

Run `git hooks --installglobal` to force any new git repository or any git repository you clone to have a reminder to install git hooks. (It can't be on by default for security reasons.)

Overview
========

Hooks are powerful and useful. Default hooks included with `./build/add-git-hooks`:

- Run linter before commit messages (node only)
- Prevent pushing to master branch
- Run test before pushing (node only)

Included hooks that can be added by moding the `./build/add-git-hooks`:

- Spell check the commit message.
- Verify that the code builds.
- Verify that any new files contain a copyright with the current year in it.
- Verify that the project still builds
- Verify that autotests matching the modified files still pass with no errors.
- Pre-populate the commit message with a "standard" format.

Locations
=========

git-hooks provide a way to manage and share your hooks using three locations:

 - **User hooks**, installed in `~/.git_hooks/`
 - **Project hooks**, installed in `.git/git_hooks/` in a project.
 - **Global hooks**, specified with the `hooks.global` configuration option.

The `contrib/` directory includes a number of useful hooks, and can be set by doing the following:

	   git config --global hooks.global $PWD/contrib/

You can even specify _multiple_ directories for your global hooks! Simply separate each path with spaces.


Creating hooks
==============

To keep things organized, git-hooks looks for scripts in **sub-directories** named after the git hook name.  For example, this project has the following `pre-commit` script in the following location:

	   git_hooks/pre-commit/bsd

When `git hooks` is run without arguments, it lists all hooks installed on your system.  It will run the hooks with the `--about` argument to generate the description shown.  

Check out the hooks in `contrib/` for some examples.

