Title:	How To Write Collaboratively with Git and GitHub   
Author:	Jason Miller   
Date:    July 29, 2012   
Latex footer: testing   
Quotes Language:  english   
Copyright:  2012 all rights reserved   
keywords: git, github, writing    

## Workflow ##

In this document, we describe the workflow we will use in a collaborative writing context that involves the versioning system, git.

### Obtaining Project Files ###

To obtain the project materials, you must use git and create a clone of the master repository on your work machine.  This means you’ll need git installed and you’ll need an active internet connection.

There are many ways to obtain and install git. [^otheroptions]   The easiest way to install git on OS X is to use the graphical Git installer available for download at http://code.google.com/p/git-osx-installer.

If you have MacPorts installed, you can install git and its dependancies with a single command in the Terminal.

Once you have git installed, running, and configured,  (link to section on configuration) you can make a clone of the project repository on your working machine.  Open Terminal.app and authenticate if necessary.  Change to the directory in which you want the repository clone to reside.  Then, at the command line, type and then execute the following:

	git clone git@github.com:TrumanSTEP/NAME.git

This will clone the private repository named NAME hosted in the TrumanSTEP organizational account to the working directory/folder (as identified by the Terminal) on your local machine.  You can now open the files in that folder with a text editor and make contributions (new content, revisions, *etc.*) to the project.

[^otheroptions]:  See http://git-scm.com/book/en/Getting-Started-Installing-Git for a pretty comprehensive list of options, including instructions.



With the exception of special files, such as digital images that are included in a document for illustrative purposes, a project's files consist of flat text files.  Such files are text-only files with no formatting.  This 'flat' nature allows git to track the changes in the files, merge the revisions of the collaborators, and do the other magical things that it does.

### Making Revisions ###

To keep the 'flat' nature of the files, we must revise project files using text editors (as opposed to word processors).  Example text editors include (moving from free to paid) Emacs, TextEdit, Vim, Nano, TextWrangler, TextMate, BBEdit, and MarsEdit.

While some (most?) word processors allow you to save a file as text only, it's best to avoid using them.  Any changes in a file will be noticed and tracked by git, so who knows what can happen when a flat text files changes to rick text while being edited and then back to text only before being saved.

### Staging your Revisions ###

Once you've made changes to a file in the project, you are going to need to share those changes with the rest of the project collaborators.  This means the team needs your changes to propagate back into the master repository.

The first thing you are going to do is stage your revised file for propagation.  In Terminal.app, at the command line (with the project folder as the working directory [^pwd]), execute the following command

	git add FILENAME

This will stage your revised file for merging back into the project.  If you have made changes to multiple files, repeat this for each file, or execute

	git add FILENAME1 FILENAME2 ... FILENAMEn

The command ‘git status’ will show you which files have been staged for the merge.

[^pwd]:  You can use the ‘pwd’ command to see the path to your current location.  Alternatively, you can use the ls command to see the other files in the working directory; if you don't have other clones of the project files on your machine, you should be able to infer from the file list where you are.


### Sharing your Revisions ###


With revised files staged, you are ready to fold them into the project.  First, you commit those project revisions to your local copy using the command 'git commit'.   See the section [NAME] on a couple ways to use this command.  The basic invocation would look like

	git commit -m "comment" FILENAME

where "comment" is a sentence or phrase that describes the revisions you made to FILENAME.  As with the ‘git add' command, you can commit a list of files at a time by listing their filenames in series.  The comment is associated with the commit action, not with the files.

To prepare for merging your revisions with the master project files on GitHub, you will next fetch files in the current version on GitHub and merge your changes with them.  This happens with the command

	git fetch

Having just fetched the most recent version of the project from GitHub, you now merge your changes in with the command

 	git merge

If all goes well, you can then proceed to the last step.  If all does not go well, it means that the merge discovered a conflict between a revision you made and a revision someone else made since you obtained the files you revised.

#### Resolving Conflicts ####

Git will tell you where in each file those conflicts occur by placing a series of '<' symbols at the start of the conflict, a series of '>' at the end of the conflict, and a series of ''=' symbols between the two versions of the conflicting text.  You must resolve this conflict by replacing this block of text with the correct revision.  This might require a conversation with other collaborators.  If it does, it's probably better to delete your revision and go with the revision of your collaborator until you can have a conversation.  At this moment, it's important to resolve the conflict and get your other contributions into the master repository.

Once you resolve any conflicts, execute 'git merge' at the command line again to make sure all is well.  The proceed to push your changes into the master repository so they are available to your collaborators.

### Pushing your Revisions to the Team ###

To push your revisions to the master repository, execute

	git push

That's it.  Once you've done that, you will have on your local machine a clone of the master repository.