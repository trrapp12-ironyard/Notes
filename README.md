# Coding Notes Table of Contents

[App.js](#app.js)|[An Accordion in Markdown](#an-accordion-in-markdown)|[Git Commands](#git-commands)|[Coding Project Ideas](#coding-project-ideas)|[Future Section 1](#future-section-1)|[Future Section 2](#future-section-2)|
|:---:|:---:|:---:|:---:|:---:|:---:|
|[Future Section 3](#future-section-3)|[Future Section 4](#future-section-4)|[Future Section 5](#future-section-5)|[Future Section 6](#future-section-6)|[Future Section 7](#future-section-7)|[Future Section 8](#future-section-8)|

----

<br>

# App.js

##### How to start web page on Node.js from command line

1) create "app.js" file <br>
2) include the following code in the app.js file 
(example found from <a href="https://stackabuse.com/how-to-start-a-node-server-examples-with-the-most-popular-frameworks/">How to Start a Node Server: Examples with the Most Popular Frameworks</a>)

```javascript
const http = require('http')
//require pulls in libraries from node, in this case it pulls in the http file which we will use to make a post request
//this next line will create an instance of the http server to handle HTTP requests
let app = http.createServer((req, res) function {
//set a response type of plain text for the reponse
	res.writeHead(200, {'Content-Type' : 'text/plain'});
	// Send back a response and end the connection
	res.end('Hellow World'); 
});
//STart the server on port 3000
app.listen(3000, '127.0.0.1');
console.log("Node server running on port 3000");
```

another example from <a href="https://www.youtube.com/watch?v=VShtPwEkDD0">youtube</a>

```javascript
const http = require('http');
const fs = require('fs');
const port = 8080;

const server = http.createServer(function (req, res) {
  res.writeHead(200, { 'Content-Type' : 'text/html'})
  fs.readFile('index.html', function (error, data) {
    if (error) {
      res.writeHead(404)
      res.write('Error: File Not Found')
    } else {
      res.write(data)
    }
    res.end()
  })
})

server.listen(port, function (error) {
  if (error) {
   console.log('there was an error: ' + error)
 } else {
   console.log("server is listneing on port: " + port)
 }
})

```
----

<br>

# An Accordion in Markdown: 

<details>
  <summary>Click to expand!</summary>
  
  ## Heading
  1. A numbered
  2. list
     * With some
     * Sub bullets
</details>

```md
# A collapsible section with markdown
<details>
  <summary>Click to expand!</summary>
  
  ## Heading
  1. A numbered
  2. list
     * With some
     * Sub bullets
</details>
```
----

<br>

# Git Commands: 

A list of applicable git commands with explanations of common uses for them.

<details>
	<summary>git config</summary>
	
Usage: git config is used primarily to set up configuration settings having to do with the git repository.  For example, setting up the email associated with the repository.

git config can take different arguments.  Each represents a different configuration level.  
* ` --local` By default, git config will write to a local level if no configuration option is passed. Local level configuration is applied to the context repository git config gets invoked in. Local configuration values are stored in a file that can be found in the repo's .git directory: .git/config
* ` --global` Global level configuration is user-specific, meaning it is applied to an operating system user. Global configuration values are stored in a file that is located in a user's home directory. ~ /.gitconfig on unix systems and C:\Users\\.gitconfig on windows.
* ` --system` System-level configuration is applied across an entire machine. This covers all users on an operating system and all repos. The system level configuration file lives in a gitconfig file off the system root path. $(prefix)/etc/gitconfig on unix systems. On windows this file can be found at C:\Documents and Settings\All Users\Application Data\Git\config on Windows XP, and in C:\ProgramData\Git\config on Windows Vista and newer.

Thus the order of priority for configuration levels is: local, global, system. This means when looking for a configuration value, Git will start at the local level and bubble up to the system level.


	
Example: 

setting up an email: 
```shell
git config --global user.email "your_email@example.com"
```
setting up a default IDE (integrated development environment: software for building applications that combines common developer tools into a single graphical user interface (GUI)). 
```shell
~ git config --global core.editor "atom --wait"~
```

```shell
~ git config --global core.editor "subl -n -w"~
```

```shell
~ git config --global core.editor "'c:/program files/sublime text 3/sublimetext.exe' -w"~
```

*Information taken from*  [Atlassian BitBucket](https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-config#:~:text=The%20git%20config%20command%20is,modify%20a%20configuration%20text%20file.)
</details>

<details>
	<summary>git init</summary>
	
Usage: `git init` initializes a new Git repository.  The intialization process essentially means that it will write a .git file in the directory that you are in.  One of the gotchas with this is to make sure that you have navigated to the correct directory first.  For example, if I were to create a file on my home computer that separated my professional work from my personal work.  I intend to put my personal work in it, so I will name it "Personal Portfolio."  Inside the "Personal Profile" directory, I eventually will have multiple projects.  One of those projects is going to be named "First Personal Project." So now the question.  Which directory level should I do my `git init` in?  

Answer: I will need to make a new folder to hold my individual project in, then initialize the git file in there.  Otherwise, if the ".git" file was initialized in the parent directory (Personal Portfolio), any time I made a commit to any of my projects, it would track it and send them up, creating an extremely bloated GitHub repository. 
	
Example(s):

setting up brand new directory from the command line and initializing the git repository in it.
1. navigate to the root directory (usually the user account, which will show you your desktop, also "~" stands for the root directory)
```shell
cd ~
```
2. navigate into to the desktop (cd stands for change directory)
```shell
cd Desktop
```
3. navigate to the directory (folder) you want to put the project in 
```shell
cd Desktop
```
4. make the parent directory for all the projects (mkdir stands for "make directory")
```shell
mkdir "Personal Portfolio Projects"
```
5. navigate into the directory you just made, so you can make another directory (folder) to hold the individual project (if you created a new directory with spaces in it, you will need to refer to your directory using quote thereafter.  If there is no space, no quotes are needed.)
```shell
cd "Personal Portfolio Projects"
```
6. now we can actually initialize a .git file.  Before we do this, we will need to step away from the command line and do one additional step.  Get off the command line and go to a browser.  Navigate to github.com.  Sign into your account.  Click on the "repositories" tab.  Click on the "new" button.  Type in the name of the repository. MAKE SURE THE NAME IN THIS REPOSITORY MATCHES THE NAME YOU NAME IT ON THE COMMAND LINE.  GitHub will take you to a screen that says, "Quick setup — if you’ve done this kind of thing before."  There will be three options to initialize a new repository along with buttons to copy the code.  Either click the buttons or copy the code manually with a <kbd>CTRL</kbd> + <kbd>C</kbd>.  Paste the code in the command line with a <kbd>CTRL</kbd> + <kbd>V</kbd>.  It should look something like this. 
```shell
echo "# delete-me" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/trrapp12/First-Personal-Project.git
git push -u origin main
```
7. you now have the repository initialized in TWO places (the local on your computer and the master in the cloud).  This is how it should be.  You can proceed by making whatever files you need in the directory and continuing with `git-push` and `git-pull` as needed.


Other important notes for more advanced development: 

##### git init vs. git clone
A quick note: git init and git clone can be easily confused. At a high level, they can both be used to "initialize a new git repository." However, git clone is dependent on git init. git clone is used to create a copy of an existing repository. Internally, git clone first calls git init to create a new repository. It then copies the data from the existing repository, and checks out a new set of working files. Learn more on the git clone page.

##### Bare repositories --- git init --bare
```shell
git init --bare <directory>
```
Initialize an empty Git repository, but omit the working directory. Shared repositories should always be created with the --bare flag (see discussion below). Conventionally, repositories initialized with the --bare flag end in .git. For example, the bare version of a repository called my-project should be stored in a directory called my-project.git.

The --bare flag creates a repository that doesn’t have a working directory, making it impossible to edit files and commit changes in that repository. You would create a bare repository to git push and git pull from, but never directly commit to it. Central repositories should always be created as bare repositories because pushing branches to a non-bare repository has the potential to overwrite changes. Think of --bare as a way to mark a repository as a storage facility, as opposed to a development environment. This means that for virtually all Git workflows, the central repository is bare, and developers local repositories are non-bare.

##### Git Tutorial: Bare Repositories
The most common use case for  git init --bare is to create a remote central repository:

```shell
ssh <user>@<host> cd path/above/repo git init --bare my-project.git
```
First, you SSH into the server that will contain your central repository. Then, you navigate to wherever you’d like to store the project. Finally, you use the --bare flag to create a central storage repository. Developers would then clone my-project.git to create a local copy on their development machine.

*information taken from* [Atlassian BitBucket: git init](https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-init)


</details>

<details>
	<summary>git clone</summary>
	
Usage: git init and git clone can be easily confused. At a high level, they can both be used to "initialize a new git repository." However, git clone is dependent on git init. git clone is used to create a copy of an existing repository. Internally, git clone first calls git init to create a new repository. It then copies the data from the existing repository, and checks out a new set of working files. Learn more on the git clone page.

Clones a repository into a newly created directory, creates remote-tracking branches for each branch in the cloned repository (visible using git branch --remotes), and creates and checks out an initial branch that is forked from the cloned repository’s currently active branch.

After the clone, a plain git fetch without arguments will update all the remote-tracking branches, and a git pull without arguments will in addition merge the remote master branch into the current master branch, if any (this is untrue when "--single-branch" is given; see below).

This default configuration is achieved by creating references to the remote branch heads under refs/remotes/origin and by initializing remote.origin.url and remote.origin.fetch configuration variables.
	
Example: 
	
```shell
git clone git@github.com:whatever folder-name
```

*information taken from* [Atlassian BitBucket: git init](https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-init) *and from* [git --fast-version-control: git-clone](https://git-scm.com/docs/git-clone)

</details>

<details>
	<summary>git add</summary>
	
Usage: think of `git add` as saving your changes.  It is usually preceeded by a `git status` to see if there are any files that are not being tracked.  `git status` will show a list of files in green and a list of files in red. The ones in red are ones that the git repository "can't see" or "is not currently tracking."  Adding them will change the untracked status to a tracked status, thereby enabling you to push them up to the git repository.  Without adding them there is not a way to push them from your local branch (the changes you make on your computer) to the master branch (the branch that lives in the GitHub cloud that everyone else is also adding information to.)   

Gotchas:  if you are used to working with a MAC or PC, the idea that "adding" is analogous to "saving" is very loosely accurate.  It's a good way to start thinking about it, but there are a lot of things that happen in saving on your computer that are actually separated into multiple commands in Git.  So a simple `git add` doesn't finish the process.  `git add` will tell the computer which file you are looking at.  You will then need to use a `git commit` to tell it that you "intend" to save it, or perhaps a better way to explain it is that it puts the added file into a batch will other files that are staged to be saved, but haven't been saved yet.  Finally, a `git push` will finish what we would think of as the "saving" process.

Explained another way: 

The `git add` and `git commit` commands compose the fundamental Git workflow. These are the two commands that every Git user needs to understand, regardless of their team’s collaboration model. They are the means to record versions of a project into the repository’s history.

Developing a project revolves around the basic edit/stage/commit pattern. First, you edit your files in the working directory. When you’re ready to save a copy of the current state of the project, you stage changes with `git add`. After you’re happy with the staged snapshot, you commit it to the project history with `git commit`. The `git reset` command is used to undo a commit or staged snapshot.

In addition to `git add` and `git commit`, a third command `git push` is essential for a complete collaborative Git workflow. `git push` is utilized to send the committed changes to remote repositories for collaboration. This enables other team members to access a set of saved changes.


Example: 

Simple git add command: 
```shell
git add
```
Stage all changes in the directory for the next commit
```shell
git add -p
```

*information found from* [Atlassian BitBucket: Saving Changes](https://www.atlassian.com/git/tutorials/saving-changes#:~:text=The%20git%20add%20command%20adds,until%20you%20run%20git%20commit%20.)

</details>

<details>
	<summary>git commit</summary>

Usage: The `git commit` command captures a snapshot of the project's currently staged changes. Committed snapshots can be thought of as “safe” versions of a project—Git will never change them unless you explicitly ask it to. Prior to the execution of `git commit`, The `git add` command is used to promote or 'stage' changes to the project that will be stored in a commit. These two commands `git commit` and `git add` are two of the most frequently used.

`Git commit` vs `SVN commit`
While they share the same name, `git commit` is nothing like `svn commit`. This shared term can be a point of confusion for Git newcomers who have a svn background, and it is important to emphasize the difference. To compare `git commit` vs `svn commit` is to compare a centralized application model (svn) vs a distributed application model (Git). In SVN, a commit pushes changes from the local SVN client, to a remote centralized shared SVN repository. In Git, repositories are distributed, Snapshots are committed to the local repository, and this requires absolutely no interaction with other Git repositories. Git commits can later be pushed to arbitrary remote repositories.

#### How it works
At a high-level, Git can be thought of as a timeline management utility. Commits are the core building block units of a Git project timeline. Commits can be thought of as snapshots or milestones along the timeline of a Git project. Commits are created with the git commit command to capture the state of a project at that point in time. Git Snapshots are always committed to the local repository. This is fundamentally different from SVN, wherein the working copy is committed to the central repository. In contrast, Git doesn’t force you to interact with the central repository until you’re ready. Just as the staging area is a buffer between the working directory and the project history, each developer’s local repository is a buffer between their contributions and the central repository.

This changes the basic development model for Git users. Instead of making a change and committing it directly to the central repo, Git developers have the opportunity to accumulate commits in their local repo. This has many advantages over SVN-style collaboration: it makes it easier to split up a feature into atomic commits, keep related commits grouped together, and clean up local history before publishing it to the central repository. It also lets developers work in an isolated environment, deferring integration until they’re at a convenient point to merge with other users. While isolation and deferred integration are individually beneficial, it is in a team's best interest to integrate frequently and in small units. For more information regarding best practices for Git team collaboration read how teams structure their Git workflow.

#### Snapshots, not differences
Aside from the practical distinctions between SVN and Git, their underlying implementation also follows entirely divergent design philosophies. Whereas SVN tracks differences of a file, Git’s version control model is based on snapshots. For example, a SVN commit consists of a diff compared to the original file added to the repository. Git, on the other hand, records the entire contents of each file in every commit.

#### Git Tutorial: Snapshots, Not Differences
This makes many Git operations much faster than SVN, since a particular version of a file doesn’t have to be “assembled” from its diffs—the complete revision of each file is immediately available from Git's internal database.

Git's snapshot model has a far-reaching impact on virtually every aspect of its version control model, affecting everything from its branching and merging tools to its collaboration work-flows.

#### Common options

```shell
git commit
```

Commit the staged snapshot. This will launch a text editor prompting you for a commit message. After you’ve entered a message, save the file and close the editor to create the actual commit.

```shell 
git commit -a
```

Commit a snapshot of all changes in the working directory. This only includes modifications to tracked files (those that have been added with git add at some point in their history).

```shell 
git commit -m "commit message"
```

A shortcut command that immediately creates a commit with a passed commit message. By default, git commit will open up the locally configured text editor, and prompt for a commit message to be entered. Passing the -m option will forgo the text editor prompt in-favor of an inline message.

```shell 
git commit -am "commit message"
```

A power user shortcut command that combines the -a and -m options. This combination immediately creates a commit of all the staged changes and takes an inline commit message.

```shell 
git commit --amend
```

This option adds another level of functionality to the commit command. Passing this option will modify the last commit. Instead of creating a new commit, staged changes will be added to the previous commit. This command will open up the system's configured text editor and prompt to change the previously specified commit message.

#### Examples
Saving changes with a commit
The following example assumes you’ve edited some content in a file called hello.py on the current branch, and are ready to commit it to the project history. First, you need to stage the file with git add, then you can commit the staged snapshot.

```shell 
git add hello.py
```

This command will add hello.py to the Git staging area. We can examine the result of this action by using the git status command.

```shell 
git status On branch master Changes to be committed:   (use "git reset HEAD ..." to unstage)   new file: hello.py 
```

The green output new file: hello.py indicates that hello.py will be saved with the next commit. From the commit is created by executing:

```shell
git commit
```

This will open a text editor (customizable via git config) asking for a commit log message, along with a list of what’s being committed:

```shell 
# Please enter the commit message for your changes. Lines starting # with '#' will be ignored, and an empty message aborts the commit. # On branch master # Changes to be committed: # (use "git reset HEAD ..." to unstage) # #modified: hello.py
```

Git doesn't require commit messages to follow any specific formatting constraints, but the canonical format is to summarize the entire commit on the first line in less than 50 characters, leave a blank line, then a detailed explanation of what’s been changed. For example:

```shell 
Change the message displayed by hello.py
 - Update the sayHello() function to output the user's name - Change the sayGoodbye() function to a friendlier message
 ```
 
It is a common practice to use the first line of the commit message as a subject line, similar to an email. The rest of the log message is considered the body and used to communicate details of the commit change set. Note that many developers also like to use the present tense in their commit messages. This makes them read more like actions on the repository, which makes many of the history-rewriting operations more intuitive.
 

#### How to update (amend) a commit
To continue with the hello.py example above. Let's make further updates to hello.py and execute the following:

```shell 
git add hello.py git commit --amend
```

This will once again, open up the configured text editor. This time, however, it will be pre-filled with the commit message we previously entered. This indicates that we are not creating a new commit, but editing the last.

#### Summary
The git commit command is one of the core primary functions of Git. Prior use of the git add command is required to select the changes that will be staged for the next commit. Then git commit is used to create a snapshot of the staged changes along a timeline of a Git projects history. Learn more about git add usage on the accompanying page. The git status command can be used to explore the state of the staging area and pending commit.

The commit model of SVN and Git are significantly different but often confused, because of the shared terminology. If you are coming to Git from a personal history of SVN usage, it is good to learn that in Git, commits are cheap and should be used frequently. Whereas SVN commits are an expensive operation that makes a remote request, Git commits are done locally and with a more efficient algorithm.
	
*information taken from* [Atlassian BitBucket: Git Commit](https://www.atlassian.com/git/tutorials/saving-changes/git-commit)

</details>

<details>
	<summary>git diff</summary>
	
Usage: Comparing changes between two repositories (usually comparing what you have on your local to see if there are changes with it and what is on the master.)

Diffing is a function that takes two input data sets and outputs the changes between them. `git diff` is a multi-use Git command that when executed runs a diff function on Git data sources. These data sources can be commits, branches, files and more. This document will discuss common invocations of `git diff` and diffing work flow patterns. The `git diff` command is often used along with `git status` and `git log` to analyze the current state of a Git repo.

Here are some things to know.  

`git status` will list all the files that haven't yet been committed.  This shows us the difference between what files are being tracked and what aren't.  It answers the "which" quetion.

`git diff` answers the "what" question.  Now that we know which files are different, "what" are the actual changes that were made.  

`git diff` will show the file differences which are not yet staged.  `git diff –staged` will show the differences between the files in the staging area and the latest version present. `git diff [first branch] [second branch]` shows the differences between the two branches. You can use this 

`git log` shows us differences, but in a historical context.  What was the history of changes over time.  This command is used to list the version history for the current branch.

Example output of a `git diff` command. 
```shell
diff --git a/diff_test.txt b/diff_test.txt
index 6b0c6cf..b37e70a 100644
--- a/diff_test.txt +++ b/diff_test.txt
@@ -1 +1 @@ -this is a git diff test example +this is a diff example
```
Breakdown of what the output means: 
1. Comparison input
 
```shell
diff --git a/diff_test.txt b/diff_test.txt
```
This line displays the input sources of the diff. We can see that `a/diff_test.txt` and `b/diff_test.txt` have been passed to the diff.

2. Meta data
 
```shell
index 6b0c6cf..b37e70a 100644
```
This line displays some internal Git metadata. You will most likely not need this information. The numbers in this output correspond to Git object version hash identifiers.

3. Markers for changes
 
```shell
--- a/diff_test.txt +++ b/diff_test.txt
```
These lines are a legend that assigns symbols to each diff input source. In this case, changes from `a/diff_test.txt` are marked with a `---` and the changes from `b/diff_test.txt` are marked with the `+++` symbol.

4. Diff chunks
The remaining diff output is a list of diff 'chunks'. A diff only displays the sections of the file that have changes. In our current example, we only have one chunk as we are working with a simple scenario. Chunks have their own granular output semantics.

 
```shell
@@ -1 +1 @@ -this is a git diff test example +this is a diff example
```
The first line is the chunk header. Each chunk is prepended by a header inclosed within `@@` symbols. The content of the header is a summary of changes made to the file. In our simplified example, we have -1 +1 meaning line one had changes. In a more realistic diff, you would see a header like:

```shell 
@@ -34,6 +34,8 @@
```
In this header example, 6 lines have been extracted starting from line number 34. Additionally, 8 lines have been added starting at line number 34.
</details>

<details>
	<summary>git reset</summary>
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
</details>

<details>
	<summary>git status</summary>
	
Usage: this will show files that have not yet been committed.  Meaning they exist in the computer file structure, but for some reason they have not been put on Git's list to track yet.  There may be good reasons to do this.  Ignored files are usually build artifacts and machine generated files that can be derived from your repository source or should otherwise not be committed. Some common examples are:

* dependency caches, such as the contents of /node_modules or /packages
* compiled code, such as .o, .pyc, and .class files
* build output directories, such as /bin, /out, or /target
* files generated at runtime, such as .log, .lock, or .tmp
* hidden system files, such as .DS_Store or Thumbs.db
* personal IDE config files, such as .idea/workspace.xml

Ignored files are tracked in a special file named .gitignore that is checked in at the root of your repository. There is no explicit git ignore command: instead the .gitignore file must be edited and committed by hand when you have new files that you wish to ignore. .gitignore files contain patterns that are matched against file names in your repository to determine whether or not they should be ignored.

For more information on ignoring a file that has already been tracked, see `git-rm` or `.gitignore` files.
	
Example: 
	
```shell
git status
```

	
</details>

<details>
	<summary>git revert</summary>
	
Usage: The `git revert` command can be considered an 'undo' type command, however, it is not a traditional undo operation. Instead of removing the commit from the project history, it figures out how to invert the changes introduced by the commit and appends a new commit with the resulting inverse content. This prevents Git from losing history, which is important for the integrity of your revision history and for reliable collaboration.

Reverting should be used when you want to apply the inverse of a commit from your project history. This can be useful, for example, if you’re tracking down a bug and find that it was introduced by a single commit. Instead of manually going in, fixing it, and committing a new snapshot, you can use git revert to automatically do all of this for you.

#### How it works
The `git revert` command is used for undoing changes to a repository's commit history. Other 'undo' commands like, git checkout and git reset, move the HEAD and branch ref pointers to a specified commit. `git revert` also takes a specified commit, however, `git revert` does not move ref pointers to this commit. A revert operation will take the specified commit, inverse the changes from that commit, and create a new "revert commit". The ref pointers are then updated to point at the new revert commit making it the tip of the branch.

To demonstrate let’s create an example repo using the command line examples below:

```shell
$ mkdir git_revert_test $ cd git_revert_test/ $ git init . Initialized empty Git repository in /git_revert_test/.git/ $ touch demo_file $ git add demo_file $ git commit -am"initial commit" [master (root-commit) 299b15f] initial commit 1 file changed, 0 insertions(+), 0 deletions(-) create mode 100644 demo_file $ echo "initial content" >> demo_file $ git commit -am"add new content to demo file" [master 3602d88] add new content to demo file n 1 file changed, 1 insertion(+) $ echo "prepended line content" >> demo_file $ git commit -am"prepend content to demo file" [master 86bb32e] prepend content to demo file 1 file changed, 1 insertion(+) $ git log --oneline 86bb32e prepend content to demo file 3602d88 add new content to demo file 299b15f initial commit
```

Here we have initialized a repo in a newly created directory named `git_revert_test`. We have made 3 commits to the repo in which we have added a file `demo_file` and modified its content twice. At the end of the repo setup procedure, we invoke `git log` to display the commit history, showing a total of 3 commits. With the repo in this state, we are ready to initiate a `git revert`.

 
```shell
$ git revert HEAD [master b9cd081] Revert "prepend content to demo file" 1 file changed, 1 deletion(-)
```
`git revert` expects a commit ref was passed in and will not execute without one. Here we have passed in the HEAD ref. This will revert the latest commit. This is the same behavior as if we reverted to `commit 3602d8815dbfa78cd37cd4d189552764b5e96c58`. Similar to a merge, a revert will create a new commit which will open up the configured system editor prompting for a new commit message. Once a commit message has been entered and saved Git will resume operation. We can now examine the state of the repo using git log and see that there is a new commit added to the previous log:

 
```shell
$ git log --oneline 1061e79 Revert "prepend content to demo file" 86bb32e prepend content to demo file 3602d88 add new content to demo file 299b15f initial commit
```
Note that the 3rd commit is still in the project history after the revert. Instead of deleting it, `git revert` added a new commit to undo its changes. As a result, the 2nd and 4th commits represent the exact same code base and the 3rd commit is still in our history just in case we want to go back to it down the road.

#### Common options
 
```shell
-e --edit
```
This is a default option and doesn't need to be specified. This option will open the configured system editor and prompts you to edit the commit message prior to committing the revert.

 
```shell
--no-edit
```
This is the inverse of the -e option. The revert will not open the editor.

 
```shell
-n --no-commit
```
Passing this option will prevent `git revert` from creating a new commit that inverses the target commit. Instead of creating the new commit this option will add the inverse changes to the Staging Index and Working Directory. These are the other trees Git uses to manage state the state of the repository. For more info visit the git reset page.

#### Resetting vs. reverting
It's important to understand that git revert undoes a single commit—it does not "revert" back to the previous state of a project by removing all subsequent commits. In Git, this is actually called a reset, not a revert.

Reverting has two important advantages over resetting. First, it doesn’t change the project history, which makes it a “safe” operation for commits that have already been published to a shared repository. For details about why altering shared history is dangerous, please see the `git reset` page.

Second, `git revert` is able to target an individual commit at an arbitrary point in the history, whereas `git reset` can only work backward from the current commit. For example, if you wanted to undo an old commit with git reset, you would have to remove all of the commits that occurred after the target commit, remove it, then re-commit all of the subsequent commits. Needless to say, this is not an elegant undo solution. For a more detailed discussion on the differences between `git revert` and other 'undo' commands see Resetting, Checking Out and Reverting.  

#### Summary
The `git revert` command is a forward-moving undo operation that offers a safe method of undoing changes. Instead of deleting or orphaning commits in the commit history, a revert will create a new commit that inverses the changes specified. `git revert` is a safer alternative to `git reset` in regards to losing work. To demonstrate the effects of `git revert` we leveraged other commands that have more in-depth documentation on their individual pages: `git log`, `git commit`, and `git reset`.

*information obtained from* [Atlassian BitBucket: Git Revert](https://www.atlassian.com/git/tutorials/undoing-changes/git-revert)
	
</details>

<details>
	<summary>git rm</summary>
	
Usage: Git sees every file in your working copy as one of three things:

* tracked - a file which has been previously staged or committed;
* untracked - a file which has not been staged or committed; or
* ignored - a file which Git has been explicitly told to ignore.

Ignored files are usually build artifacts and machine generated files that can be derived from your repository source or should otherwise not be committed. Some common examples are:

* dependency caches, such as the contents of /node_modules or /packages
* compiled code, such as .o, .pyc, and .class files
* build output directories, such as /bin, /out, or /target
* files generated at runtime, such as .log, .lock, or .tmp
* hidden system files, such as .DS_Store or Thumbs.db
* personal IDE config files, such as .idea/workspace.xml

Ignored files are tracked in a special file named `.gitignore` that is checked in at the root of your repository. There is no explicit git ignore command: instead the `.gitignore` file must be edited and committed by hand when you have new files that you wish to ignore. `.gitignore` files contain patterns that are matched against file names in your repository to determine whether or not they should be ignored.

`.gitignore` uses globbing patterns to match against file names. You can construct your patterns using various symbols:

|Pattern|Example matches|Explanation*|
|:---:|:---:|:---:|
| &ast;&ast;/logs | logs/debug.log <br> logs/monday/foo.bar  <br> build/logs/debug.log | You can prepend a pattern with a double asterisk to match directories anywhere in the repository.|
| &ast;&ast;/logs/debug.log | logs/debug.log <br> build/logs/debug.log <br> *but not* <br> logs/build/debug.log | You can also use a double asterisk to match files based on their name and the name of their parent directory.|
| &ast;.log | debug.log <br> foo.log <br> .log <br> logs/debug.log| An asterisk is a wildcard that matches zero or more characters.|
| &ast;.log <br> !important.log| debug.log <br> trace.log <br> *but not* <br> important.log <br> logs/important.log | Prepending an exclamation mark to a pattern negates it. If a file matches a pattern, but also matches a negating pattern defined later in the file, it will not be ignored. |
| &ast;.log <br> !important/ &ast;.log <br> trace. &ast; | debug.log <br> important/trace.log <br> *but not*
important/debug.log| Patterns defined after a negating pattern will re-ignore any previously negated files.|
| /debug.log| debug.log <br> *but not* <br> logs/debug.log| Prepending a slash matches files only in the repository root.|
| debug.log | debug.log <br> logs/debug.log| By default, patterns match files in any directory| 
| debug?.log | debug0.log <br> debugg.log <br> *but not* debug10.log| A question mark matches exactly one character.| 
| debug[0-9].log | debug0.log <br> debug1.log <br> *but not* <br> debug10.log| Square brackets can also be used to match a single character from a specified range.| 
| debug[01].log| debug0.log <br> debug1.log <br> *but not* debug2.log <br> debug01.log | Square brackets match a single character form the specified set.| 
| debug[!01].log | debug2.log <br> *but not* debug0.log <br> debug1.log <br> debug01.log | An exclamation mark can be used to match any character except one from the specified set. |
| debug[a-z].log | debuga.log <br> debugb.log <br> *but not* debug1.log | Ranges can be numeric or alphabetic.|
| logs | logs <br> logs/debug.log <br> logs/latest/foo.bar <br> build/logs <br> build/logs/debug.log | If you don't append a slash, the pattern will match both files and the contents of directories with that name. In the example matches on the left, both directories and files named logs are ignored |
| logs/	| logs/debug.log <br> logs/latest/foo.bar <br> build/logs/foo.bar <br> build/logs/latest/debug.log | Appending a slash indicates the pattern is a directory. The entire contents of any directory in the repository matching that name – including all of its files and subdirectories – will be ignored |
| logs/ <br> !logs/important.log | logs/debug.log <br> logs/important.log | Wait a minute! Shouldn't logs/important.log be negated in the example on the left Nope! Due to a performance-related quirk in Git, you can not negate a file that is ignored due to a pattern matching a directory |
| logs/&ast;&ast;/debug.log | logs/debug.log <br> logs/monday/debug.log <br> logs/monday/pm/debug.log |	A double asterisk matches zero or more directories.|
| logs/&ast;day/debug.log | logs/monday/debug.log <br> logs/tuesday/debug.log <br> *but not* logs/latest/debug.log | Wildcards can be used in directory names as well.|
| logs/debug.log| logs/debug.log <br> *but not* debug.log <br> build/logs/debug.log |Patterns specifying a file in a particular directory are relative to the repository root. (You can prepend a slash if you like, but it doesn't do anything special.)|

&ast;&ast; these explanations assume your `.gitignore file` is in the top level directory of your repository, as is the convention. If your repository has multiple `.gitignore` files, simply mentally replace "repository root" with "directory containing the `.gitignore` file" (and consider unifying them, for the sanity of your team).&ast;

In addition to these characters, you can use # to include comments in your `.gitignore` file:

```shell
# ignore all logs *.log 
```

You can use `\` to escape `.gitignore` pattern characters if you have files or directories containing them:

```shell
# ignore the file literally named foo[01].txt foo\[01\].txt 
```

#### Shared `.gitignore` files in your repository
Git ignore rules are usually defined in a `.gitignore` file at the root of your repository. However, you can choose to define multiple `.gitignore` files in different directories in your repository. Each pattern in a particular `.gitignore` file is tested relative to the directory containing that file. However the convention, and simplest approach, is to define a single `.gitignore` file in the root. As your `.gitignore` file is checked in, it is versioned like any other file in your repository and shared with your teammates when you push. Typically you should only include patterns in `.gitignore` that will benefit other users of the repository.

#### Personal Git ignore rules
You can also define personal ignore patterns for a particular repository in a special file at `.git/info/exclude`. These are not versioned, and not distributed with your repository, so it's an appropriate place to include patterns that will likely only benefit you. For example if you have a custom logging setup, or special development tools that produce files in your repository's working directory, you could consider adding them to `.git/info/exclude` to prevent them from being accidentally committed to your repository.

#### Global Git ignore rules
In addition, you can define global Git ignore patterns for all repositories on your local system by setting the Git `core.excludesFile` property. You'll have to create this file yourself. If you're unsure where to put your global `.gitignore` file, your home directory isn't a bad choice (and makes it easy to find later). Once you've created the file, you'll need to configure its location with git config:

```shell
$ touch ~/.gitignore $ git config --global core.excludesFile ~/.gitignore 
```
You should be careful what patterns you choose to globally ignore, as different file types are relevant for different projects. Special operating system files (e.g. `.DS_Store` and `thumbs.db`) or temporary files created by some developer tools are typical candidates for ignoring globally.

#### Ignoring a previously committed file
If you want to ignore a file that you've committed in the past, you'll need to delete the file from your repository and then add a .gitignore rule for it. Using the --cached option with git rm means that the file will be deleted from your repository, but will remain in your working directory as an ignored file.

```shell
$ echo debug.log >> .gitignore $ git rm --cached debug.log rm 'debug.log' $ git commit -m "Start ignoring debug.log" 
```
You can omit the `--cached option` if you want to delete the file from both the repository and your local file system.

#### Committing an ignored file
It is possible to force an ignored file to be committed to the repository using the `-f` (or --force) option with `git add`:

```shell
$ cat .gitignore *.log $ git add -f debug.log $ git commit -m "Force adding debug.log" 
```

You might consider doing this if you have a general pattern (like *.log) defined, but you want to commit a specific file. However a better solution is to define an exception to the general rule:

```shell
$ echo !debug.log >> .gitignore $ cat .gitignore *.log !debug.log $ git add debug.log $ git commit -m "Adding debug.log" 
```

This approach is more obvious, and less confusing, for your teammates.

#### Stashing an ignored file
`git stash` is a powerful Git feature for temporarily shelving and reverting local changes, allowing you to re-apply them later on. As you'd expect, by default git stash ignores ignored files and only stashes changes to files that are tracked by Git. However, you can invoke `git stash` with the `--all` option to stash changes to ignored and untracked files as well.

#### Debugging .gitignore files
If you have complicated `.gitignore` patterns, or patterns spread over multiple `.gitignore` files, it can be difficult to track down why a particular file is being ignored. You can use the `git check-ignore` command with the `-v` (or --verbose) option to determine which pattern is causing a particular file to be ignored:

```shell
$ git check-ignore -v debug.log .gitignore:3:*.log debug.log 
```

The output shows:
```shell
 :  :   
```
You can pass multiple file names to git check-ignore if you like, and the names themselves don't even have to correspond to files that exist in your repository.

*Information found at* [Atlassian BitBucket: .gitignore](https://www.atlassian.com/git/tutorials/saving-changes/gitignore#:~:text=Ignored%20files%20are%20usually%20build,contents%20of%20%2Fnode_modules%20or%20%2Fpackages)
</details>

<details>
	<summary>git log</summary>
	
Usage: This command is used to list the version history for the current branch.

Example: 
	
```shell
git log
```
This command is used to list the version history for the current branch.

```shell
git log –follow[file]  
```
This command lists version history for a file, including the renaming of files also.
	
</details>

<details>
	<summary>git show</summary>
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
</details>

<details>
	<summary>git tag</summary>
	
Usage:  

This command is used to give tags to the specified commit.
	
Example: 
	
```shell
git tag [commitID] 
```

	
</details>

<details>
	<summary>git branch</summary>
	
Usage: lists all the branches in the current repository

Example:

```shell
git branch
```

This command lists all the local branches in the current repository.

```shell
git branch [branch name]
```

This command creates a new branch.

```shell
git branch -d [branch name]
```

This command deletes the feature branch.

*information obtained from* [Top 20 Git Commands With Examples](https://dzone.com/articles/top-20-git-commands-with-examples)
</details>

<details>
	<summary>git checkout</summary>
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
</details>

<details>
	<summary>git merge</summary>
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
</details>

<details>
	<summary>git remote</summary>
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
</details>

<details>
	<summary>git push</summary>
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
</details>

<details>
	<summary>git pull</summary>
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
</details>

<details>
	<summary>git stash</summary>
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
</details>


----

<br>

# Coding Project Ideas

1. Chrome Extension: Encoder/Decoder
	<br>
	<br>
	*Current user experience based off of using [URL Decoder/Encoder](https://meyerweb.com/eric/tools/dencoder/)*
	- user has to click in the current field, do <kbd>CTRL</kbd>+ <kbd>A</kbd>, <kbd>CTRL</kbd>+<kbd>C</kbd>, click into webpage, <kbd>CTRL</kbd>+<kbd>A</kbd>, <kbd>CTRL</kbd>+<kbd>V</kbd>, hit the encode url button, hit <kbd>CTRL</kbd>+ <kbd>A</kbd>, <kbd>CTRL</kbd>+<kbd>C</kbd>, then go back to the field they are working in and hit <kbd>CTRL</kbd>+ <kbd>A</kbd>, <kbd>CTRL</kbd>+<kbd>V</kbd>.  Way too many times hitting <kbd>CTRL</kbd> + <kbd>something</kbd>
    
2. Chrome Extension: Underliner

	*create an extension that helps you to read across tabular data by drawing and displaying an underline across the entire screen*
    
3. Tribute Web Page

	*create web page for Diana's Grandpa that can serve up different cards with videos*
	  - cards would have a window to show the video, a link to click to view it, a description of the video, and would show up along an animated timeline
	  - certain moderators with priveleges would be able to move the movies up and down, or it would be decided programmatically
	  - have a place to raise issues with a form so people can give feedback.

----

<br>

# Future Section 1

----

<br>

# Future Section 2

----

<br>

# Future Section 3

----

<br>

# Future Section 4

----

<br>

# Future Section 5

----

<br>

# Future Section 6

----

<br>

# Future Section 7

----

<br>

# Future Section 8
