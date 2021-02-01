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
	<summary>Working Example with Code Example</summary>
	
```md
# A collapsible section with markdown
<details>
  <summary>Click to expand!</summary>
  
  ## Heading
  1. A numbered
  2. list
     * With some
     * Sub bullets

```

</details>

----

<br>

# Git Commands: 
<details> 
	<summary>A list of applicable git commands with explanations of common uses for them.</summary>
	
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
	
Usage: Git Reset

:warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: :warning: 

The `git reset` command is a complex and versatile tool for undoing changes. It has three primary forms of invocation. These forms correspond to command line arguments `--soft`, `--mixed`, `--hard`. The three arguments each correspond to Git's three internal state management mechanism's, The Commit Tree (HEAD), The Staging Index, and The Working Directory.

#### Git Reset & Three Trees of Git
To properly understand `git reset` usage, we must first understand Git's internal state management systems. Sometimes these mechanisms are called Git's "three trees". Trees may be a misnomer, as they are not strictly traditional tree data-structures. They are, however, node and pointer-based data structures that Git uses to track a timeline of edits. The best way to demonstrate these mechanisms is to create a changeset in a repository and follow it through the three trees. 

To get started we will create a new repository with the commands below:

```shell
$ mkdir git_reset_test $ cd git_reset_test/ $ git init . Initialized empty Git repository in /git_reset_test/.git/ $ touch reset_lifecycle_file $ git add reset_lifecycle_file $ git commit -m"initial commit" [master (root-commit) d386d86] initial commit 1 file changed, 0 insertions(+), 0 deletions(-) create mode 100644 reset_lifecycle_file
```
The above example code creates a new git repository with a single empty file, `reset_lifecycle_file`. At this point, the example repository has a single commit (`d386d86`) from adding `reset_lifecycle_file`.

#### The working directory
The first tree we will examine is "The Working Directory". This tree is in sync with the local filesystem and is representative of the immediate changes made to content in files and directories.


```shell
$ echo 'hello git reset' > reset_lifecycle_file
 $ git status 
 On branch master 
 Changes not staged for commit: 
 (use "git add ..." to update what will be committed) 
 (use "git checkout -- ..." to discard changes in working directory) 
 modified: reset_lifecycle_file
 ```


In our demo repository, we modify and add some content to the `reset_lifecycle_file`. Invoking `git status` shows that Git is aware of the changes to the file. These changes are currently a part of the first tree, "The Working Directory". `git status` can be used to show changes to the Working Directory. They will be displayed in the red with a '`modified`' prefix.

#### Staging index
Next up is the 'Staging Index' tree. This tree is tracking Working Directory changes, that have been promoted with `git add`, to be stored in the next commit. This tree is a complex internal caching mechanism. Git generally tries to hide the implementation details of the Staging Index from the user.

To accurately view the state of the Staging Index we must utilize a lesser known Git command `git ls-files`. The `git ls-files` command is essentially a debug utility for inspecting the state of the Staging Index tree.
 
```shell
git ls-files -s 100644 e69de29bb2d1d6434b8b29ae775ad8c2e48c5391 0 reset_lifecycle_file
```

Here we have executed `git ls-files` with the `-s` or `--stage` option. Without the `-s` option the `git ls-files` output is simply a list of file names and paths that are currently part of the index. The `-s` option displays additional metadata for the files in the Staging Index. This metadata is the staged contents' mode bits, object name, and stage number. Here we are interested in the object name, the second value (`d7d77c1b04b5edd5acfc85de0b592449e5303770`). This is a standard Git object SHA-1 hash. It is a hash of the content of the files. The Commit History stores its own object SHA's for identifying pointers to commits and refs and the Staging Index has its own object SHA's for tracking versions of files in the index.

Next, we will promote the modified reset_lifecycle_file into the Staging Index.

```shell
$ git add reset_lifecycle_file 

 
$ git status 

 
On branch master Changes to be committed: 

 
(use "git reset HEAD ..." to unstage) 

 
modified: reset_lifecycle_file
```

Here we have invoked `git add reset_lifecycle_file` which adds the file to the Staging Index. Invoking `git status` now shows `reset_lifecycle_file` in green under "Changes to be committed". It is important to note that `git status` is not a true representation of the Staging Index. The `git status` command output displays changes between the Commit History and the Staging Index. Let us examine the Staging Index content at this point.

 
```shell
$ git ls-files -s 100644 d7d77c1b04b5edd5acfc85de0b592449e5303770 0 reset_lifecycle_file
```
We can see that the object SHA for `reset_lifecycle_file` has been updated from `e69de29bb2d1d6434b8b29ae775ad8c2e48c5391` to `d7d77c1b04b5edd5acfc85de0b592449e5303770`.

#### Commit history
The final tree is the Commit History. The `git commit` command adds changes to a permanent snapshot that lives in the Commit History. This snapshot also includes the state of the Staging Index at the time of commit.

 
```shell
$ git commit -am"update content of reset_lifecycle_file" [master dc67808] update content of reset_lifecycle_file 1 file changed, 1 insertion(+) $ git status On branch master nothing to commit, working tree clean
```
Here we have created a new commit with a message of "update content of resetlifecyclefile". The changeset has been added to the Commit History. Invoking `git status` at this point shows that there are no pending changes to any of the trees. Executing `git log` will display the Commit History. Now that we have followed this changeset through the three trees we can begin to utilize `git reset`.

#### How it works
At a surface level, `git reset` is similar in behavior to `git checkout`. Where `git checkout` solely operates on the HEAD ref pointer, `git reset` will move the HEAD ref pointer and the current branch ref pointer. To better demonstrate this behavior consider the following example:


This example demonstrates a sequence of commits on the master branch. The HEAD ref and master branch ref currently point to commit d. Now let us execute and compare, both `git checkout b` and `git reset b`.

#### git checkout b

With `git checkout`, the master ref is still pointing to d. The HEAD ref has been moved, and now points at commit b. The repo is now in a 'detached HEAD' state.

#### git reset b

Comparatively, `git reset`, moves both the HEAD and branch refs to the specified commit.

In addition to updating the commit ref pointers, `git reset` will modify the state of the three trees. The ref pointer modification always happens and is an update to the third tree, the Commit tree. The command line arguments `--soft`, `--mixed`, and `--hard` direct how to modify the Staging Index, and Working Directory trees.

#### Main Options
The default invocation of `git reset` has implicit arguments of `--mixed` and `HEAD`. This means executing `git reset` is equivalent to executing `git reset --mixed HEAD`. In this form `HEAD` is the specified commit. Instead of `HEAD ` any Git SHA-1 commit hash can be used.


#### --hard
This is the most direct, :warning: DANGEROUS :warning: , and frequently used option. When passed `--hard` The Commit History ref pointers are updated to the specified commit. Then, the Staging Index and Working Directory are reset to match that of the specified commit. Any previously pending changes to the Staging Index and the Working Directory gets reset to match the state of the Commit Tree. This means any pending work that was hanging out in the Staging Index and Working Directory will be lost.

To demonstrate this, let's continue with the three tree example repo we established earlier. First let's make some modifications to the repo. Execute the following commands in the example repo:

```shell
$ echo 'new file content' > new_file $ git add new_file $ echo 'changed content' >> reset_lifecycle_file
```
These commands have created a new file named `new_file` and added it to the repo. Additionally, the content of `reset_lifecycle_file` will be modified. With these changes in place let us now examine the state of the repo using `git status`.

```shell
$ git status On branch master Changes to be committed: (use "git reset HEAD ..." to unstage) new file: new_file Changes not staged for commit: (use "git add ..." to update what will be committed) (use "git checkout -- ..." to discard changes in working directory) modified: reset_lifecycle_file
```
We can see that there are now pending changes to the repo. The Staging Index tree has a pending change for the addition of `new_file` and the Working Directory has a pending change for the modifications to `reset_lifecycle_file`.

Before moving forward let us also examine the state of the Staging Index:

```shell
$ git ls-files -s 100644 8e66654a5477b1bf4765946147c49509a431f963 0 new_file 100644 d7d77c1b04b5edd5acfc85de0b592449e5303770 0 reset_lifecycle_file
```
We can see that `new_file` has been added to the index. We have made updates to `reset_lifecycle_file` but the Staging Index SHA (`d7d77c1b04b5edd5acfc85de0b592449e5303770`) remains the same. This is expected behavior because have not used `git add` to promote these changes to the Staging Index. These changes exist in the Working Directory.

Let us now execute a `git reset --hard` and examine the new state of the repository.

```shell
$ git reset --hard HEAD is now at dc67808 update content of reset_lifecycle_file $ git status On branch master nothing to commit, working tree clean $ git ls-files -s 100644 d7d77c1b04b5edd5acfc85de0b592449e5303770 0 reset_lifecycle_file
```
Here we have executed a "hard reset" using the `--hard` option. Git displays output indicating that `HEAD` is pointing to the latest commit `dc67808`. Next, we check the state of the repo with `git status`. Git indicates there are no pending changes. We also examine the state of the Staging Index and see that it has been reset to a point before `new_file` was added. Our modifications to `reset_lifecycle_file` and the addition of `new_file` have been destroyed. This data loss cannot be undone, this is critical to take note of.

#### --mixed
This is the default operating mode. The ref pointers are updated. The Staging Index is reset to the state of the specified commit. Any changes that have been undone from the Staging Index are moved to the Working Directory. Let us continue.

```shell
$ echo 'new file content' > new_file $ git add new_file $ echo 'append content' >> reset_lifecycle_file $ git add reset_lifecycle_file $ git status On branch master Changes to be committed: (use "git reset HEAD ..." to unstage) new file: new_file modified: reset_lifecycle_file $ git ls-files -s 100644 8e66654a5477b1bf4765946147c49509a431f963 0 new_file 100644 7ab362db063f9e9426901092c00a3394b4bec53d 0 reset_lifecycle_file
```
In the example above we have made some modifications to the repository. Again, we have added a `new_file` and modified the contents of `reset_lifecycle_file`. These changes are then applied to the Staging Index with `git add`. With the repo in this state, we will now execute the reset.

```shell
$ git reset --mixed $ git status On branch master Changes not staged for commit: (use "git add ..." to update what will be committed) (use "git checkout -- ..." to discard changes in working directory) modified: reset_lifecycle_file Untracked files: (use "git add ..." to include in what will be committed) new_file no changes added to commit (use "git add" and/or "git commit -a") $ git ls-files -s 100644 d7d77c1b04b5edd5acfc85de0b592449e5303770 0 reset_lifecycle_file
```
Here we have executed a "mixed reset". To reiterate, `--mixed` is the default mode and the same effect as executing `git reset`. Examining the output from `git status` and `git ls-files`, shows that the Staging Index has been reset to a state where `reset_lifecycle_file` is the only file in the index. The object SHA for `reset_lifecycle_file` has been reset to the previous version.

The important things to take note of here is that git status shows us that there are modifications to `reset_lifecycle_file` and there is an untracked file: `new_file`. This is the explicit `--mixed`  behavior. The Staging Index has been reset and the pending changes have been moved into the Working Directory. Compare this to the `--hard` reset case where the Staging Index was reset and the Working Directory was reset as well, losing these updates.

#### --soft
When the `--soft` argument is passed, the ref pointers are updated and the reset stops there. The Staging Index and the Working Directory are left untouched. This behavior can be hard to clearly demonstrate. Let's continue with our demo repo and prepare it for a soft reset.

```shell
$ git add reset_lifecycle_file 

 
$ git ls-files -s 

 
100644 67cc52710639e5da6b515416fd779d0741e3762e 0 reset_lifecycle_file 

 
$ git status 

 
On branch master 

 
Changes to be committed: 

 
(use "git reset HEAD ..." to unstage) 

 
modified: reset_lifecycle_file 

 
Untracked files: 

 
(use "git add ..." to include in what will be committed) 

 
new_file
```

Here we have again used `git add` to promote the modified `reset_lifecycle_file` into the Staging Index. We confirm that the index has been updated with the `git ls-files` output. The output from `git status` now displays the "Changes to be committed" in green. The `new_file` from our previous examples is floating around in the Working Directory as an untracked file. Lets quickly execute `rm new_file` to delete the file as we will not need it for the upcoming examples.

With the repository in this state we now execute a soft reset.

 
```shell
$ git reset --soft $ git status On branch master Changes to be committed: (use "git reset HEAD ..." to unstage) modified: reset_lifecycle_file $ git ls-files -s 100644 67cc52710639e5da6b515416fd779d0741e3762e 0 reset_lifecycle_file
```
We have executed a 'soft reset'. Examining the repo state with `git status` and `git ls-files` shows that nothing has changed. This is expected behavior. A soft reset will only reset the Commit History. By default, `git reset` is invoked with `HEAD` as the target commit. Since our Commit History was already sitting on HEAD and we implicitly reset to HEAD nothing really happened.

To better understand and utilize `--soft` we need a target commit that is not HEAD. We have `reset_lifecycle_file` waiting in the Staging Index. Let's create a new commit.

```shell
$ git commit -m"prepend content to reset_lifecycle_file"
```
At this point, our repo should have three commits. We will be going back in time to the first commit. To do this we will need the first commit's ID. This can be found by viewing output from git log.

```shell
$ git log commit 62e793f6941c7e0d4ad9a1345a175fe8f45cb9df Author: bitbucket  Date: Fri Dec 1 15:03:07 2017 -0800 prepend content to reset_lifecycle_file commit dc67808a6da9f0dec51ed16d3d8823f28e1a72a Author: bitbucket  Date: Fri Dec 1 10:21:57 2017 -0800 update content of reset_lifecycle_file commit 780411da3b47117270c0e3a8d5dcfd11d28d04a4 Author: bitbucket  Date: Thu Nov 30 16:50:39 2017 -0800 initial commit
```
Keep in mind that Commit History ID's will be unique to each system. This means the commit ID's in this example will be different from what you see on your personal machine. The commit ID we are interested in for this example is `780411da3b47117270c0e3a8d5dcfd11d28d04a4`. This is the ID that corresponds to the "initial commit". Once we have located this ID we will use it as the target for our soft reset.

Before we travel back in time lets first check the current state of the repo.

 
```shell
$ git status && git ls-files -s On branch master nothing to commit, working tree clean 100644 67cc52710639e5da6b515416fd779d0741e3762e 0 reset_lifecycle_file
```
Here we execute a combo command of `git status` and `git ls-files -s` this shows us there are pending changes to the repo and `reset_lifecycle_file` in the Staging Index is at a version of `67cc52710639e5da6b515416fd779d0741e3762e`. With this in mind lets execute a soft reset back to our first commit.

```shell
$git reset --soft 780411da3b47117270c0e3a8d5dcfd11d28d04a4 $ git status && git ls-files -s On branch master Changes to be committed: (use "git reset HEAD ..." to unstage) modified: reset_lifecycle_file 100644 67cc52710639e5da6b515416fd779d0741e3762e 0 reset_lifecycle_file
```
The code above executes a "soft reset" and also invokes the `git status` and `git ls-files` combo command, which outputs the state of the repository. We can examine the repo state output and note some interesting observations. First, `git status` indicates there are modifications to `reset_lifecycle_file` and highlights them indicating they are changes staged for the next commit. Second, the git ls-files input indicates that the Staging Index has not changed and retains the `SHA 67cc52710639e5da6b515416fd779d0741e3762e` we had earlier.

To further clarify what has happened in this reset let us examine the git log:

```shell
$ git log commit 780411da3b47117270c0e3a8d5dcfd11d28d04a4 Author: bitbucket  Date: Thu Nov 30 16:50:39 2017 -0800 initial commit
```
The log output now shows that there is a single commit in the Commit History. This helps to clearly illustrate what `--soft` has done. As with all `git reset` invocations, the first action reset takes is to reset the commit tree. Our previous examples with `--hard` and `--mixed` have both been against the `HEAD` and have not moved the Commit Tree back in time. During a soft reset, this is all that happens.

This may then be confusing as to why `git status` indicates there are modified files. `--soft` does not touch the Staging Index, so the updates to our Staging Index followed us back in time through the commit history. This can be confirmed by the output of `git ls-files -s` showing that the SHA for `reset_lifecycle_file` is unchanged. As a reminder, `git status` does not show the state of 'the three trees', it essentially shows a diff between them. In this case, it is displaying that the Staging Index is ahead of the changes in the Commit History as if we have already staged them.

#### Resetting vs Reverting
:warning: *If `git revert` is a “safe” way to undo changes, you can think of `git reset` as the dangerous method. There is a real risk of losing work with `git reset`. `git reset` will never delete a commit, however, commits can become 'orphaned' which means there is no direct path from a ref to access them. These orphaned commits can usually be found and restored using `git reflog`. Git will permanently delete any orphaned commits after it runs the internal garbage collector. By default, Git is configured to run the garbage collector every 30 days. Commit History is one of the 'three git trees' the other two, Staging Index and Working Directory are not as permanent as Commits. Care must be taken when using this tool, as it’s one of the only Git commands that have the potential to lose your work.* :warning:

Whereas reverting is designed to safely undo a public commit, `git reset` is designed to undo local changes to the Staging Index and Working Directory. Because of their distinct goals, the two commands are implemented differently: resetting completely removes a changeset, whereas reverting maintains the original changeset and uses a new commit to apply the undo.

#### Don't Reset Public History
You should never use `git reset` when any snapshots after have been pushed to a public repository. After publishing a commit, you have to assume that other developers are reliant upon it.

:warning: Removing a commit that other team members have continued developing poses serious problems for collaboration. When they try to sync up with your repository, it will look like a chunk of the project history abruptly disappeared. The sequence below demonstrates what happens when you try to reset a public commit. The `origin/master branch` is the central repository’s version of your local master branch. :warning: 

As soon as you add new commits after the reset, Git will think that your local history has diverged from `origin/master`, and the merge commit required to synchronize your repositories is likely to confuse and frustrate your team.

:warning: *The point is, make sure that you’re using `git reset` on a local experiment that went wrong—not on published changes. If you need to fix a public commit, the `git revert` command was designed specifically for this purpose*. :warning: 

Examples
 
```shell
git reset 
```
Remove the specified file from the staging area, but leave the working directory unchanged. This unstages a file without overwriting any changes.

 
```shell
git reset
```
Reset the staging area to match the most recent commit, but leave the working directory unchanged. This unstages all files without overwriting any changes, giving you the opportunity to re-build the staged snapshot from scratch.

```shell
git reset --hard
```
Reset the staging area and the working directory to match the most recent commit. In addition to unstaging changes, the `--hard` flag tells Git to overwrite all changes in the working directory, too. Put another way: this obliterates all uncommitted changes, so make sure you really want to throw away your local developments before using it.

```shell
git reset  
```
Move the current branch tip backward to commit, reset the staging area to match, but leave the working directory alone. All changes made since  will reside in the working directory, which lets you re-commit the project history using cleaner, more atomic snapshots.

 
```shell
git reset --hard
```

Move the current branch tip backward to `commit` and reset both the staging area and the working directory to match. This obliterates not only the uncommitted changes, but all commits after, as well.

#### Unstaging a file
The `git reset` command is frequently encountered while preparing the staged snapshot. The next example assumes you have two files called `hello.py` and `main.py` that you’ve already added to the repository.

```shell
# Edit both hello.py and main.py # Stage everything in the current directory git add . # Realize that the changes in hello.py and main.py # should be committed in different snapshots # Unstage main.py git reset main.py # Commit only hello.py git commit -m "Make some changes to hello.py" # Commit main.py in a separate snapshot git add main.py git commit -m "Edit main.py"
```
As you can see, `git reset` helps you keep your commits highly-focused by letting you unstage changes that aren’t related to the next commit.

#### Removing Local Commits
The next example shows a more advanced use case. It demonstrates what happens when you’ve been working on a new experiment for a while, but decide to completely throw it away after committing a few snapshots.

```shell
Create a new file called `foo.py` and add some code to it # Commit it to the project history git add foo.py git commit -m "Start developing a crazy feature" # Edit `foo.py` again and change some other tracked files, too # Commit another snapshot git commit -a -m "Continue my crazy feature" # Decide to scrap the feature and remove the associated commits git reset --hard HEAD~2
```

The `git reset` HEAD~2 command moves the current branch backward by two commits, effectively removing the two snapshots we just created from the project history. Remember that this kind of reset should only be used on unpublished commits. Never perform the above operation if you’ve already pushed your commits to a shared repository.

#### Summary
To review, `git reset` is a powerful command that is used to undo local changes to the state of a Git repo. `git reset` operates on "The Three Trees of Git". These trees are the Commit History (HEAD), the Staging Index, and the Working Directory. There are three command line options that correspond to the three trees. The options `--soft`, `--mixed`, and `--hard` can be passed to `git reset`.
 
	
*information taken from* [Atlassian BitBucket: Git Reset](https://www.atlassian.com/git/tutorials/undoing-changes/git-reset)
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
	
Usage: This command shows the metadata and content changes of the specified commit.
	
Example: 

```shell
git show [commit]
```
*information taken from* [Top 20 Git Commands with Examples](https://dzone.com/articles/top-20-git-commands-with-examples)
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
	
# Undoing Commits & Changes

In this section, we will discuss the available 'undo' Git strategies and commands. It is first important to note that Git does not have a traditional 'undo' system like those found in a word processing application. It will be beneficial to refrain from mapping Git operations to any traditional 'undo' mental model. Additionally, Git has its own nomenclature for 'undo' operations that it is best to leverage in a discussion. This nomenclature includes terms like reset, revert, checkout, clean, and more.

A fun metaphor is to think of Git as a timeline management utility. Commits are snapshots of a point in time or points of interest along the timeline of a project's history. Additionally, multiple timelines can be managed through the use of branches. When 'undoing' in Git, you are usually moving back in time, or to another timeline where mistakes didn't happen.

This tutorial provides all of the necessary skills to work with previous revisions of a software project. First, it shows you how to explore old commits, then it explains the difference between reverting public commits in the project history vs. resetting unpublished changes on your local machine.

# Finding what is lost: Reviewing old commits
The whole idea behind any version control system is to store “safe” copies of a project so that you never have to worry about irreparably breaking your code base. Once you’ve built up a project history of commits, you can review and revisit any commit in the history. One of the best utilities for reviewing the history of a Git repository is the `git log` command. In the example below, we use `git log` to get a list of the latest commits to a popular open-source graphics library.

 
```shell
git log --oneline e2f9a78fe Replaced FlyControls with OrbitControls d35ce0178 Editor: Shortcuts panel Safari support. 9dbe8d0cf Editor: Sidebar.Controls to Sidebar.Settings.Shortcuts. Clean up. 05c5288fc Merge pull request #12612 from TyLindberg/editor-controls-panel 0d8b6e74b Merge pull request #12805 from harto/patch-1 23b20c22e Merge pull request #12801 from gam0022/improve-raymarching-example-v2 fe78029f1 Fix typo in documentation 7ce43c448 Merge pull request #12794 from WestLangley/dev-x 17452bb93 Merge pull request #12778 from OndrejSpanel/unitTestFixes b5c1b5c70 Merge pull request #12799 from dhritzkiv/patch-21 1b48ff4d2 Updated builds. 88adbcdf6 WebVRManager: Clean up. 2720fbb08 Merge pull request #12803 from dmarcos/parentPoseObject 9ed629301 Check parent of poseObject instead of camera 219f3eb13 Update GLTFLoader.js 15f13bb3c Update GLTFLoader.js 6d9c22a3b Update uniforms only when onWindowResize 881b25b58 Update ProjectionMatrix on change aspect
```

Each commit has a unique SHA-1 identifying hash. These IDs are used to travel through the committed timeline and revisit commits. By default, `git log` will only show commits for the currently selected branch. It is entirely possible that the commit you're looking for is on another branch. You can view all commits across all branches by executing `git log --branches=*`. The command `git branch` is used to view and visit other branches. Invoking the command, `git branch -a` will return a list of all known branch names. One of these branch names can then be logged using `git log`.

When you have found a commit reference to the point in history you want to visit, you can utilize the `git checkout` command to visit that commit. `git checkout` is an easy way to “load” any of these saved snapshots onto your development machine. During the normal course of development, the HEAD usually points to master or some other local branch, but when you check out a previous commit, HEAD no longer points to a branch—it points directly to a commit. This is called a “detached HEAD” state, and it can be visualized as the following:


Checking out an old file does not move the HEAD pointer. It remains on the same branch and same commit, avoiding a 'detached head' state. You can then commit the old version of the file in a new snapshot as you would any other changes. So, in effect, this usage of git checkout on a file, serves as a way to revert back to an old version of an individual file. For more information on these two modes visit the git checkout page

# Viewing an old revision

This example assumes that you’ve started developing a crazy experiment, but you’re not sure if you want to keep it or not. To help you decide, you want to take a look at the state of the project before you started your experiment. First, you’ll need to find the ID of the revision you want to see.

```shell
git log --oneline
````
Let’s say your project history looks something like the following:

```shell
b7119f2 Continue doing crazy things 872fa7e Try something crazy a1e8fb5 Make some important changes to hello.txt 435b61d Create hello.txt 9773e52 Initial import
```
You can use git checkout to view the “Make some import changes to hello.txt” commit as follows:

 
```shell
git checkout a1e8fb5
```
This makes your working directory match the exact state of the `a1e8fb5` commit. You can look at files, compile the project, run tests, and even edit files without worrying about losing the current state of the project. Nothing you do in here will be saved in your repository. To continue developing, you need to get back to the “current” state of your project:

 
```shell
git checkout master
```
This assumes that you're developing on the default master branch. Once you’re back in the master branch, you can use either `git revert` or `git reset` to undo any undesired changes.

# Undoing a committed snapshot
There are technically several different strategies to 'undo' a commit. The following examples will assume we have a commit history that looks like:

```shell
git log --oneline 872fa7e Try something crazy a1e8fb5 Make some important changes to hello.txt 435b61d Create hello.txt 9773e52 Initial import
```
We will focus on undoing the `872fa7e Try something crazy` commit. Maybe things got a little too crazy.

# How to undo a commit with `git checkout`

Using the` git checkout` command we can checkout the previous commit, `a1e8fb5`, putting the repository in a state before the crazy commit happened. Checking out a specific commit will put the repo in a "detached HEAD" state. This means you are no longer working on any branch. In a detached state, any new commits you make will be orphaned when you change branches back to an established branch. Orphaned commits are up for deletion by Git's garbage collector. The garbage collector runs on a configured interval and permanently destroys orphaned commits. To prevent orphaned commits from being garbage collected, we need to ensure we are on a branch.

From the detached HEAD state, we can execute `git checkout -b new_branch_without_crazy_commit`. This will create a new branch named `new_branch_without_crazy_commit` and switch to that state. The repo is now on a new history timeline in which the `872fa7e` commit no longer exists. At this point, we can continue work on this new branch in which the `872fa7e` commit no longer exists and consider it 'undone'. Unfortunately, if you need the previous branch, maybe it was your master branch, this undo strategy is not appropriate. Let's look at some other 'undo' strategies. For more information and examples review our in-depth `git checkout` discussion.

# How to undo a public commit with `git revert`
Let's assume we are back to our original commit history example. The history that includes the `872fa7e` commit. This time let's try a revert 'undo'. If we execute `git revert HEAD`, Git will create a new commit with the inverse of the last commit. This adds a new commit to the current branch history and now makes it look like:

 
```shell
git log --oneline e2f9a78 Revert "Try something crazy" 872fa7e Try something crazy a1e8fb5 Make some important changes to hello.txt 435b61d Create hello.txt 9773e52 Initial import
```
At this point, we have again technically 'undone' the `872fa7e` commit. Although `872fa7e` still exists in the history, the new `e2f9a78` commit is an inverse of the changes in `872fa7e`. Unlike our previous checkout strategy, we can continue using the same branch. This solution is a satisfactory undo. This is the ideal 'undo' method for working with public shared repositories. If you have requirements of keeping a curated and minimal Git history this strategy may not be satisfactory.

# How to undo a commit with `git reset`
For this undo strategy we will continue with our working example. `git reset` is an extensive command with multiple uses and functions. If we invoke `git reset --hard a1e8fb5 `the commit history is reset to that specified commit. Examining the commit history with git log will now look like:

 
```shell
git log --oneline a1e8fb5 Make some important changes to hello.txt 435b61d Create hello.txt 9773e52 Initial import
```
The log output shows the `e2f9a78` and `872fa7e` commits no longer exist in the commit history. At this point, we can continue working and creating new commits as if the 'crazy' commits never happened. This method of undoing changes has the cleanest effect on history. Doing a reset is great for local changes however it adds complications when working with a shared remote repository. If we have a shared remote repository that has the `872fa7e` commit pushed to it, and we try to `git push` a branch where we have reset the history, Git will catch this and throw an error. Git will assume that the branch being pushed is not up to date because of it's missing commits. In these scenarios, `git revert` should be the preferred undo method.

# Undoing the last commit
In the previous section, we discussed different strategies for undoing commits. These strategies are all applicable to the most recent commit as well. In some cases though, you might not need to remove or reset the last commit. Maybe it was just made prematurely. In this case you can amend the most recent commit. Once you have made more changes in the working directory and staged them for commit by using `git add`, you can execute `git commit --amend`. This will have Git open the configured system editor and let you modify the last commit message. The new changes will be added to the amended commit.

# Undoing uncommitted changes
Before changes are committed to the repository history, they live in the staging index and the working directory. You may need to undo changes within these two areas. The staging index and working directory are internal Git state management mechanisms. For more detailed information on how these two mechanisms operate, visit the `git reset` page which explores them in depth.

# The working directory
The working directory is generally in sync with the local file system. To undo changes in the working directory you can edit files like you normally would using your favorite editor. Git has a couple utilities that help manage the working directory. There is the git clean command which is a convenience utility for undoing changes to the working directory. Additionally, `git reset` can be invoked with the `--mixed` or `--hard` options and will apply a reset to the working directory.

# The staging index
The `git add` command is used to add changes to the staging index. `git reset` is primarily used to undo the staging index changes. A `--mixed` reset will move any pending changes from the staging index back into the working directory.

# Undoing public changes
When working on a team with remote repositories, extra consideration needs to be made when undoing changes. `git reset` should generally be considered a 'local' undo method. A reset should be used when undoing changes to a private branch. This safely isolates the removal of commits from other branches that may be in use by other developers. Problems arise when a reset is executed on a shared branch and that branch is then pushed remotely with `git push`. Git will block the push in this scenario complaining that the branch being pushed is out of date from the remote branch as it is missing commits.

The preferred method of undoing shared history is `git revert`. A revert is safer than a reset because it will not remove any commits from a shared history. A revert will retain the commits you want to undo and create a new commit that inverts the undesired commit. This method is safer for shared remote collaboration because a remote developer can then pull the branch and receive the new revert commit which undoes the undesired commit.

# Summary
We covered many high-level strategies for undoing things in Git. It's important to remember that there is more than one way to 'undo' in a Git project. Most of the discussion on this page touched on deeper topics that are more thoroughly explained on pages specific to the relevant Git commands. The most commonly used 'undo' tools are `git checkout`, `git revert`, and `git reset`. Some key points to remember are:

* Once changes have been committed they are generally permanent
* Use git checkout to move around and review the commit history
* git revert is the best tool for undoing shared public changes
* git reset is best used for undoing local private changes

In addition to the primary undo commands, we took a look at other Git utilities: `git log` for finding lost commits `git clean` for undoing uncommitted changes `git add` for modifying the staging index.

*information for this section was found at* [Atlassian BitBucket: Undoing Commits and Changes](https://www.atlassian.com/git/tutorials/undoing-changes)
</details>

<details>
	<summary>git merge</summary>
	
# Git Merge
 

Merging is Git's way of putting a forked history back together again. The `git merge` command lets you take the independent lines of development created by git branch and integrate them into a single branch.

Note that all of the commands presented below merge into the current branch. The current branch will be updated to reflect the merge, but the target branch will be completely unaffected. Again, this means that `git merge` is often used in conjunction with `git checkout` for selecting the current branch and `git branch -d` for deleting the obsolete target branch.

# How it works

`git merge` will combine multiple sequences of commits into one unified history. In the most frequent use cases, `git merge` is used to combine two branches. The following examples in this document will focus on this branch merging pattern. In these scenarios, `git merge` takes two commit pointers, usually the branch tips, and will find a common base commit between them. Once Git finds a common base commit it will create a new "merge commit" that combines the changes of each queued merge commit sequence.

Say we have a new branch feature that is based off the master branch. We now want to merge this feature branch into master.

Invoking this command will merge the specified branch feature into the current branch, we'll assume master. Git will determine the merge algorithm automatically (discussed below).

Merge commits are unique against other commits in the fact that they have two parent commits. When creating a merge commit Git will attempt to auto-magically merge the separate histories for you. If Git encounters a piece of data that is changed in both histories it will be unable to automatically combine them. This scenario is a version control conflict and Git will need user intervention to continue. 

# Preparing to merge
Before performing a merge there are a couple of preparation steps to take to ensure the merge goes smoothly.

# Confirm the receiving branch
Execute `git status` to ensure that HEAD is pointing to the correct merge-receiving branch. If needed, execute `git checkout` to switch to the receiving branch. In our case we will execute `git checkout master`.

# Fetch latest remote commits
Make sure the receiving branch and the merging branch are up-to-date with the latest remote changes. Execute `git fetch` to pull the latest remote commits. Once the fetch is completed ensure the master branch has the latest updates by executing git pull.

# Merging
Once the previously discussed "preparing to merge" steps have been taken a merge can be initiated by executing `git merge` where  is the name of the branch that will be merged into the receiving branch.

# Fast Forward Merge
A fast-forward merge can occur when there is a linear path from the current branch tip to the target branch. Instead of “actually” merging the branches, all Git has to do to integrate the histories is move (i.e., “fast forward”) the current branch tip up to the target branch tip. This effectively combines the histories, since all of the commits reachable from the target branch are now available through the current one. For example, a fast forward merge of some-feature into master would look something like the following:

However, a fast-forward merge is not possible if the branches have diverged. When there is not a linear path to the target branch, Git has no choice but to combine them via a 3-way merge. 3-way merges use a dedicated commit to tie together the two histories. The nomenclature comes from the fact that Git uses three commits to generate the merge commit: the two branch tips and their common ancestor.

While you can use either of these merge strategies, many developers like to use fast-forward merges (facilitated through rebasing) for small features or bug fixes, while reserving 3-way merges for the integration of longer-running features. In the latter case, the resulting merge commit serves as a symbolic joining of the two branches.

Our first example demonstrates a fast-forward merge. The code below creates a new branch, adds two commits to it, then integrates it into the main line with a fast-forward merge.

```shell
# Start a new feature
git checkout -b new-feature master
# Edit some files
git add <file>
git commit -m "Start a feature"
# Edit some files
git add <file>
git commit -m "Finish a feature"
# Merge in the new-feature branch
git checkout master
git merge new-feature
git branch -d new-feature
```
This is a common workflow for short-lived topic branches that are used more as an isolated development than an organizational tool for longer-running features.

Also note that Git should not complain about the `git branch -d`, since new-feature is now accessible from the master branch.

In the event that you require a merge commit during a fast forward merge for record keeping purposes you can execute `git merge` with the `--no-ffoption`.

```shell
git merge --no-ff <branch>
```

This command merges the specified branch into the current branch, but always generates a merge commit (even if it was a fast-forward merge). This is useful for documenting all merges that occur in your repository.

# 3-way merge
The next example is very similar, but requires a 3-way merge because master progresses while the feature is in-progress. This is a common scenario for large features or when several developers are working on a project simultaneously.

```shell
Start a new feature
git checkout -b new-feature master
# Edit some files
git add <file>
git commit -m "Start a feature"
# Edit some files
git add <file>
git commit -m "Finish a feature"
# Develop the master branch
git checkout master
# Edit some files
git add <file>
git commit -m "Make some super-stable changes to master"
# Merge in the new-feature branch
git merge new-feature
git branch -d new-feature
```

Note that it’s impossible for Git to perform a fast-forward merge, as there is no way to move master up to new-feature without backtracking.

For most workflows, new-feature would be a much larger feature that took a long time to develop, which would be why new commits would appear on master in the meantime. If your feature branch was actually as small as the one in the above example, you would probably be better off rebasing it onto master and doing a fast-forward merge. This prevents superfluous merge commits from cluttering up the project history.

# Resolving conflict
If the two branches you're trying to merge both changed the same part of the same file, Git won't be able to figure out which version to use. When such a situation occurs, it stops right before the merge commit so that you can resolve the conflicts manually.

The great part of Git's merging process is that it uses the familiar edit/stage/commit workflow to resolve merge conflicts. When you encounter a merge conflict, running the `git status` command shows you which files need to be resolved. For example, if both branches modified the same section of `hello.py`, you would see something like the following:

```shell
On branch master
Unmerged paths:
(use "git add/rm ..." as appropriate to mark resolution)
both modified: hello.py
```

# How conflicts are presented
When Git encounters a conflict during a merge, It will edit the content of the affected files with visual indicators that mark both sides of the conflicted content. These visual markers are: `<<<<<<<`, `=======`, and `>>>>>>>`. Its helpful to search a project for these indicators during a merge to find where conflicts need to be resolved.

```shell
here is some content not affected by the conflict
<<<<<<< master
this is conflicted text from master
=======
this is conflicted text from feature branch
>>>>>>> feature branch;
```
Generally the content before the `=======` marker is the receiving branch and the part after is the merging branch.

Once you've identified conflicting sections, you can go in and fix up the merge to your liking. When you're ready to finish the merge, all you have to do is run `git add` on the conflicted file(s) to tell Git they're resolved. Then, you run a normal `git commit` to generate the merge commit. It’s the exact same process as committing an ordinary snapshot, which means it’s easy for normal developers to manage their own merges.

Note that merge conflicts will only occur in the event of a 3-way merge. It’s not possible to have conflicting changes in a fast-forward merge. 

# Summary
This document is an overview of the `git merge` command. Merging is an essential process when working with Git. We discussed the internal mechanics behind a merge and the differences between a fast forward merge and a three way, true merge. Some key take-aways are:
 

1. Git merging combines sequences of commits into one unified history of commits.
2. There are two main ways Git will merge: Fast Forward and Three way
3. Git can automatically merge commits unless there are changes that conflict in both commit sequences.
This document integrated and referenced other Git commands like: `git branch`, `git pull`, and `git fetch`. Visit their corresponding stand-alone pages for more information. 

*information for this article was taken from* [Atlassian BitBucket: Git Merge](https://www.atlassian.com/git/tutorials/using-branches/git-merge)
</details>

<details>
	<summary>git remote</summary>

# git syncing

SVN uses a single centralized repository to serve as the communication hub for developers, and collaboration takes place by passing changesets between the developers’ working copies and the central repository. This is different from Git's distributed collaboration model, which gives every developer their own copy of the repository, complete with its own local history and branch structure. Users typically need to share a series of commits rather than a single changeset. Instead of committing a changeset from a working copy to the central repository, Git lets you share entire branches between repositories.

The `git remote` command is one piece of the broader system which is responsible for syncing changes. Records registered through the `git remote` command are used in conjunction with the git fetch, git push, and git pull commands. These commands all have their own syncing responsibilities which can be explored on the corresponding links.

# Git remote
The `git remote` command lets you create, view, and delete connections to other repositories. Remote connections are more like bookmarks rather than direct links into other repositories. Instead of providing real-time access to another repository, they serve as convenient names that can be used to reference a not-so-convenient URL.

For example, the following diagram shows two remote connections from your repo into the central repo and another developer’s repo. Instead of referencing them by their full URLs, you can pass the origin and john shortcuts to other Git commands.

# Git remote usage overview
The `git remote` command is essentially an interface for managing a list of remote entries that are stored in the repository's ./.git/config file. The following commands are used to view the current state of the remote list.

Viewing `git remote` configurations
```shell
git remote
```
List the remote connections you have to other repositories.

```shell
git remote -v
```
Same as the above command, but include the URL of each connection.

Creating and modifying `git remote` configurations
The `git remote` command is also a convenience or 'helper' method for modifying a repo's ./.git/config file. The commands presented below let you manage connections with other repositories. The following commands will modify the repo's /.git/config file. The result of the following commands can also be achieved by directly editing the ./.git/config file with a text editor.

```shell
git remote add <name> <url>
```
Create a new connection to a remote repository. After adding a remote, you’ll be able to use as a convenient shortcut for in other Git commands.

```shell
git remote rm <name>
```
Remove the connection to the remote repository called .

```shell
git remote rename <old-name> <new-name>
```
Rename a remote connection from to .

# `Git remote` discussion
Git is designed to give each developer an entirely isolated development environment. This means that information is not automatically passed back and forth between repositories. Instead, developers need to manually pull upstream commits into their local repository or manually push their local commits back up to the central repository. The `git remote` command is really just an easier way to pass URLs to these "sharing" commands.

# The origin Remote
When you clone a repository with git clone, it automatically creates a remote connection called origin pointing back to the cloned repository. This is useful for developers creating a local copy of a central repository, since it provides an easy way to pull upstream changes or publish local commits. This behavior is also why most Git-based projects call their central repository origin.

# Repository URLs
Git supports many ways to reference a remote repository. Two of the easiest ways to access a remote repo are via the HTTP and the SSH protocols. HTTP is an easy way to allow anonymous, read-only access to a repository. For example:

```shell
http://host/path/to/repo.git
```
But, it’s generally not possible to push commits to an HTTP address (you wouldn’t want to allow anonymous pushes anyways). For read-write access, you should use SSH instead:

```shell
ssh://user@host/path/to/repo.git
```
You’ll need a valid SSH account on the host machine, but other than that, Git supports authenticated access via SSH out of the box. Modern secure 3rd party hosting solutions like Bitbucket.com will provide these URLs for you.

# `Git remote` commands
The `git remote` command is one of many Git commands that takes additional appended 'subcommands'. Below is an examination of the commonly used `git remote` subcommands.

```shell
ADD <NAME> <URL>
```
Adds a record to `./.git/config` for remote named at the repository url .

Accepts a `-f` option, that will git fetch immediately after the remote record is created.

Accepts a `--tags` option, that will git fetch immediately and import every tag from the remote repository.

```shell 
RENAME <OLD> <NEW>
```
Updates `./.git/config` to rename the record to . All remote-tracking branches and configuration settings for the remote are updated.

```shell
REMOVE or RM <NAME>
```
Modifies `./.git/config` and removes the remote named . All remote-tracking branches and configuration settings for the remote are removed.

```shell
GET-URL <NAME>
```
Outputs the URLs for a remote record.

Accepts `--push`, push URLs are queried rather than fetch URLs.

With `--all`, all URLs for the remote will be listed.

```shell
SHOW <NAME>
```
Outputs high-level information about the remote .

```shell
PRUNE <NAME>
```
Deletes any local branches for that are not present on the remote repository.

Accepts a `--dry-run` option which will list what branches are set to be pruned, but will not actually prune them.

# `Git remote` examples
In addition to origin, it’s often convenient to have a connection to your teammates’ repositories. For example, if your co-worker, John, maintained a publicly accessible repository on dev.example.com/john.git, you could add a connection as follows:

```shell 
git remote add john http://dev.example.com/john.git
```
Having this kind of access to individual developers’ repositories makes it possible to collaborate outside of the central repository. This can be very useful for small teams working on a large project.

# Showing your remotes
By default, the `git remote` command will list previously stored remote connections to other repositories. This will produce single line output that lists the names of "bookmark" name of remote repos.

```shell 
$ git remote
origin
upstream
other_users_repo
```
Invoking `git remote` with the `-v` option will print the list of bookmarked repository names and additionally, the corresponding repository URL. The -v option stands for "verbose". Below is example output of verbose `git remote` output.

```shell 
git remote -v
origin  git@bitbucket.com:origin_user/reponame.git (fetch)
origin  git@bitbucket.com:origin_user/reponame.git (push)
upstream    https://bitbucket.com/upstream_user/reponame.git (fetch)
upstream    https://bitbucket.com/upstream_user/reponame.git (push)
other_users_repo    https://bitbucket.com/other_users_repo/reponame (fetch)
other_users_repo    https://bitbucket.com/other_users_repo/reponame (push)
```
# Adding Remote Repositories
The `git remote` add command will create a new connection record to a remote repository. After adding a remote, you’ll be able to use as a convenient shortcut for in other Git commands. For more information on the accepted URL syntax, view the "Repository URLs" section below. This command will create a new record within the repository's ./.git/config. An example of this config file update follows:

```shell 
$ git remote add fake_test https://bitbucket.com/upstream_user/reponame.git; [remote "remote_test"] 
   url = https://bitbucket.com/upstream_user/reponame.git 
   fetch = +refs/heads/*:refs/remotes/remote_test/*
   ```
# Inspecting a Remote
The show subcommand can be appended to `git remote to give detailed output on the configuration of a remote. This output will contain a list of branches associated with the remote and also the endpoints attached for fetching and pushing.

```shell
git remote show upstream
* remote upstream
   Fetch URL: https://bitbucket.com/upstream_user/reponame.git
   Push URL: https://bitbucket.com/upstream_user/reponame.git
   HEAD branch: master
   Remote branches:
      master tracked
      simd-deprecated tracked
      tutorial tracked
   Local ref configured for 'git push':
      master pushes to master (fast-forwardable)
```

# Fetching and pulling from Git remotes
Once a remote record has been configured through the use of the `git remote` command, the remote name can be passed as an argument to other Git commands to communicate with the remote repo. Both git fetch, and git pull can be used to read from a remote repository. Both commands have different operations that are explained in further depth on their respective links.

# Pushing to Git remotes
The `git push` command is used to write to a remote repository.

```shell 
git push <remote-name> <branch-name>
```
This example will upload the local state of to the remote repository specified by .

# Renaming and Removing Remotes
```shell
git remote rename <old-name> <new-name>
```
The command `git remote` rename is self-explanatory. When executed, this command will rename a remote connection from to . Additionally, this will modify the contents of ./.git/config to rename the record for the remote there as well.

```shell
git remote rm <name>
```
The command `git remote rm` will remove the connection to the remote repository specified by the parameter. To demonstrate let us 'undo' the remote addition from our last example. If we execute `git remote rm remote_test`, and then examine the contents of `./.git/config` we can see that the `[remote "remote_test"]` record is no longer there.

*information for this article found at* [Atlassian BitBucket: git syncing](https://www.atlassian.com/git/tutorials/syncing)
</details>

<details>
	<summary>git fetch</summary>

# git fetch


The `git fetch` command downloads commits, files, and refs from a remote repository into your local repo. Fetching is what you do when you want to see what everybody else has been working on. It’s similar to svn update in that it lets you see how the central history has progressed, but it doesn’t force you to actually merge the changes into your repository. Git isolates fetched content from existing local content; it has absolutely no effect on your local development work. Fetched content has to be explicitly checked out using the `git checkout` command. This makes fetching a safe way to review commits before integrating them with your local repository.

When downloading content from a remote repo, `git pull` and `git fetch` commands are available to accomplish the task. You can consider `git fetch` the 'safe' version of the two commands. It will download the remote content but not update your local repo's working state, leaving your current work intact. `git pull` is the more aggressive alternative; it will download the remote content for the active local branch and immediately execute `git merge` to create a merge commit for the new remote content. If you have pending changes in progress this will cause conflicts and kick-off the merge conflict resolution flow.

# How `git fetch` works with remote branches

To better understand how `git fetch` works let us discuss how Git organizes and stores commits. Behind the scenes, in the repository's `./.git/objects directory`, Git stores all commits, local and remote. Git keeps remote and local branch commits distinctly separate through the use of branch refs. The refs for local branches are stored in the `./.git/refs/heads/`. Executing the git branch command will output a list of the local branch refs. The following is an example of `git branch` output with some demo branch names.

```shell 
git branch
master
feature1
debug2
```
Examining the contents of the /.git/refs/heads/ directory would reveal similar output.

```shell 
ls ./.git/refs/heads/
master
feature1
debug2
```
Remote branches are just like local branches, except they map to commits from somebody else’s repository. Remote branches are prefixed by the remote they belong to so that you don’t mix them up with local branches. Like local branches, Git also has refs for remote branches. Remote branch refs live in the `./.git/refs/remotes/` directory. The next example code snippet shows the branches you might see after fetching a remote repo conveniently named remote-repo:

```shell 
git branch -r
# origin/master
# origin/feature1
# origin/debug2
# remote-repo/master
# remote-repo/other-feature
```

This output displays the local branches we had previously examined but now displays them prefixed with `origin/`. Additionally, we now see the remote branches prefixed with `remote-repo`. You can check out a remote branch just like a local one, but this puts you in a detached HEAD state (just like checking out an old commit). You can think of them as read-only branches. To view your remote branches, simply pass the `-r `flag to the `git branch` command.

You can inspect remote branches with the usual `git checkout` and `git log` commands. If you approve the changes a remote branch contains, you can merge it into a local branch with a normal `git merge`. So, unlike SVN, synchronizing your local repository with a remote repository is actually a two-step process: `fetch`, then `merge`. The `git pull` command is a convenient shortcut for this process.

# `git fetch` commands and options

```shell 
git fetch <remote>
```
Fetch all of the branches from the repository. This also downloads all of the required commits and files from the other repository.

```shell 
git fetch <remote> <branch>
```
Same as the above command, but only fetch the specified branch.

```shell 
git fetch --all
```
A power move which fetches all registered remotes and their branches:

```shell 
git fetch --dry-run
```
The `--dry-run` option will perform a demo run of the command. It will output examples of actions it will take during the fetch but not apply them.

# `git fetch` examples

##### `git fetch` a remote branch

The following example will demonstrate how to fetch a remote branch and update your local working state to the remote contents. In this example, let us assume there is a central repo origin from which the local repository has been cloned from using the `git clone` command. Let us also assume an additional remote repository named `coworkers_repo` that contains a `feature_branch` which we will configure and fetch. With these assumptions set let us continue the example.

Firstly we will need to configure the remote repo using the git remote command.

```shell 
git remote add coworkers_repo git@bitbucket.org:coworker/coworkers_repo.git
```
Here we have created a reference to the coworker's repo using the repo URL. We will now pass that remote name to `git fetch` to download the contents.

```shell 
git fetch coworkers_repo coworkers/feature_branch
fetching coworkers/feature_branch
```
We now locally have the contents of `coworkers/feature_branch` we will need the integrate this into our local working copy. We begin this process by using the `git checkout` command to checkout the newly downloaded remote branch.

```shell 
git checkout coworkers/feature_branch
Note: checking out coworkers/feature_branch'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

git checkout -b <new-branch-name>
```

The output from this checkout operation indicates that we are in a detached HEAD state. This is expected and means that our HEAD ref is pointing to a ref that is not in sequence with our local history. Being that HEAD is pointed at the` coworkers/feature_branch` ref, we can create a new local branch from that ref. The 'detached HEAD' output shows us how to do this using the git checkout command:

```shell 
git checkout -b local_feature_branch
```
Here we have created a new local branch named `local_feature_branch`. This puts updates HEAD to point at the latest remote content and we can continue development on it from this point.

Synchronize origin with git fetch
The following example walks through the typical workflow for synchronizing your local repository with the central repository's master branch.

```shell 
git fetch origin
```
This will display the branches that were downloaded:

```shell 
a1e8fb5..45e66a4 master -> origin/master
a1e8fb5..9e8ab1c develop -> origin/develop
* [new branch] some-feature -> origin/some-feature
```
The commits from these new remote branches are shown as squares instead of circles in the diagram below. As you can see, `git fetch` gives you access to the entire branch structure of another repository.


To see what commits have been added to the upstream master, you can run a `git log` using `origin/master` as a filter:  

```shell 
git log --oneline master..origin/master
```
To approve the changes and merge them into your local master branch use the following commands:

```shell 
git checkout master
git log origin/master
```
Then we can use `git merge origin/master`:

```shell 
git merge origin/master
```
The `origin/master` and `master` branches now point to the same commit, and you are synchronized with the upstream developments.

# `git fetch` summary

In review, `git fetch` is a primary command used to download contents from a remote repository. `git fetch` is used in conjunction with git remote, git branch, git checkout, and git reset to update a local repository to the state of a remote. The `git fetch` command is a critical piece of collaborative git work flows. `git fetch` has similar behavior to git pull, however, `git fetch` can be considered a safer, nondestructive version.


</details>

<details>
	<summary>git push</summary>
	
Usage: Syncing
git push
git remote git fetch git push git pull
The git push command is used to upload local repository content to a remote repository. Pushing is how you transfer commits from your local repository to a remote repo. It's the counterpart to git fetch, but whereas fetching imports commits to local branches, pushing exports commits to remote branches. Remote branches are configured using the git remote command. Pushing has the potential to overwrite changes, caution should be taken when pushing. These issues are discussed below.

Git push usage
git push <remote> <branch>
Push the specified branch to , along with all of the necessary commits and internal objects. This creates a local branch in the destination repository. To prevent you from overwriting commits, Git won’t let you push when it results in a non-fast-forward merge in the destination repository.

git push <remote> --force
Same as the above command, but force the push even if it results in a non-fast-forward merge. Do not use the --force flag unless you’re absolutely sure you know what you’re doing.

git push <remote> --all
Push all of your local branches to the specified remote.

git push <remote> --tags
Tags are not automatically pushed when you push a branch or use the --all option. The --tags flag sends all of your local tags to the remote repository.

Git push discussion
git push is most commonly used to publish an upload local changes to a central repository. After a local repository has been modified a push is executed to share the modifications with remote team members.

Using git push to publish changes
The above diagram shows what happens when your local master has progressed past the central repository’s master and you publish changes by running git push origin master. Notice how git push is essentially the same as running git merge master from inside the remote repository.

Git push and syncing
git push is one component of many used in the overall Git "syncing" process. The syncing commands operate on remote branches which are configured using the git remote command. git push can be considered and 'upload' command whereas, git fetch and git pull can be thought of as 'download' commands. Once changesets have been moved via a download or upload a git merge may be performed at the destination to integrate the changes.

Pushing to bare repositories
A frequently used, modern Git practice is to have a remotely hosted --bare repository act as a central origin repository. This origin repository is often hosted off-site with a trusted 3rd party like Bitbucket. Since pushing messes with the remote branch structure, It is safest and most common to push to repositories that have been created with the --bare flag. Bare repos don’t have a working directory so a push will not alter any in progress working directory content. For more information on bare repository creation, read about git init.

Force Pushing
Git prevents you from overwriting the central repository’s history by refusing push requests when they result in a non-fast-forward merge. So, if the remote history has diverged from your history, you need to pull the remote branch and merge it into your local one, then try pushing again. This is similar to how SVN makes you synchronize with the central repository via svn update before committing a changeset.

The --force flag overrides this behavior and makes the remote repository’s branch match your local one, deleting any upstream changes that may have occurred since you last pulled. The only time you should ever need to force push is when you realize that the commits you just shared were not quite right and you fixed them with a git commit --amend or an interactive rebase. However, you must be absolutely certain that none of your teammates have pulled those commits before using the --force option.

Examples
Default git push
The following example describes one of the standard methods for publishing local contributions to the central repository. First, it makes sure your local master is up-to-date by fetching the central repository’s copy and rebasing your changes on top of them. The interactive rebase is also a good opportunity to clean up your commits before sharing them. Then, the git push command sends all of the commits on your local master to the central repository.

git checkout master
git fetch origin master
git rebase -i origin/master
# Squash commits, fix up commit messages etc.
git push origin master
Since we already made sure the local master was up-to-date, this should result in a fast-forward merge, and git push should not complain about any of the non-fast-forward issues discussed above.

Amended force push
The git commit command accepts a --amend option which will update the previous commit. A commit is often amended to update the commit message or add new changes. Once a commit is amended a git push will fail because Git will see the amended commit and the remote commit as diverged content. The --force option must be used to push an amended commit.

# make changes to a repo and git add
git commit --amend
# update the existing commit message
git push --force origin master
The above example assumes it is being executed on an existing repository with a commit history. git commit --amend is used to update the previous commit. The amended commit is then force pushed using the --force option.

Deleting a remote branch or tag
Sometimes branches need to be cleaned up for book keeping or organizational purposes. The fully delete a branch, it must be deleted locally and also remotely.

git branch -D branch_name
git push origin :branch_name
The above will delete the remote branch named branch_name passing a branch name prefixed with a colon to git push will delete the remote branch.


	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
</details>

<details>
	<summary>git pull</summary>

# `git pull`

The `git pull` command is used to fetch and download content from a remote repository and immediately update the local repository to match that content. Merging remote upstream changes into your local repository is a common task in Git-based collaboration work flows. The `git pull` command is actually a combination of two other commands, `git fetch` followed by `git merge`. In the first stage of operation `git pull` will execute a `git fetch` scoped to the local branch that HEAD is pointed at. Once the content is downloaded, `git pull` will enter a merge workflow. A new merge commit will be-created and HEAD updated to point at the new commit.

# `git pull` usage

#### How it works
The `git pull` command first runs `git fetch` which downloads content from the specified remote repository. Then a `git merge` is executed to merge the remote content refs and heads into a new local merge commit. To better demonstrate the pull and merging process let us consider the following example. Assume we have a repository with a master branch and a remote origin.


In this scenario, `git pull` will download all the changes from the point where the local and master diverged. In this example, that point is E. `git pull` will fetch the diverged remote commits which are A-B-C. The pull process will then create a new local merge commit containing the content of the new diverged remote commits.


In the above diagram, we can see the new commit H. This commit is a new merge commit that contains the contents of remote A-B-C commits and has a combined log message. This example is one of a few `git pull` merging strategies. A `--rebase` option can be passed to `git pull` to use a rebase merging strategy instead of a merge commit. The next example will demonstrate how a rebase pull works. Assume that we are at a starting point of our first diagram, and we have executed `git pull --rebase`.


In this diagram, we can now see that a rebase pull does not create the new H commit. Instead, the rebase has copied the remote commits A--B--C and rewritten the local commits E--F--G to appear after them them in the local origin/master commit history.

# Common Options
```shell 
git pull <remote>
```
Fetch the specified remote’s copy of the current branch and immediately merge it into the local copy. This is the same as `git fetch` followed by `git merge origin/`.

```shell
git pull --no-commit <remote>
```
Similar to the default invocation, fetches the remote content but does not create a new merge commit.

```shell
git pull --rebase <remote>
```
Same as the previous `pull` Instead of using `git merge` to integrate the remote branch with the local one, use `git rebase`.

```shell
git pull --verbose
```
Gives verbose output during a pull which displays the content being downloaded and the merge details.

#J Git pull discussion
You can think of `git pull` as Git's version of svn update. It’s an easy way to synchronize your local repository with upstream changes. The following diagram explains each step of the pulling process.


You start out thinking your repository is synchronized, but then `git fetch` reveals that origin's version of master has progressed since you last checked it. Then `git merge` immediately integrates the remote master into the local one.

# Git pull and syncing
`git pull` is one of many commands that claim the responsibility of 'syncing' remote content. The `git remote` command is used to specify what remote endpoints the syncing commands will operate on. The `git push` command is used to upload content to a remote repository.

The `git fetch` command can be confused with `git pull`. They are both used to download remote content. An important safety distinction can be made between `git pull` and `get fetch`. `git fetch` can be considered the "safe" option whereas, `git pull` can be considered unsafe. `git fetch` will download the remote content and not alter the state of the local repository. Alternatively, `git pull` will download remote content and immediately attempt to change the local state to match that content. This may unintentionally cause the local repository to get in a conflicted state.

# Pulling via Rebase
The `--rebase` option can be used to ensure a linear history by preventing unnecessary merge commits. Many developers prefer rebasing over merging, since it’s like saying, "I want to put my changes on top of what everybody else has done." In this sense, using `git pull` with the `--rebase` flag is even more like svn update than a plain `git pull`.

In fact, pulling with `--rebase` is such a common workflow that there is a dedicated configuration option for it:

```shell 
git config --global branch.autosetuprebase always
```
After running that command, all `git pull` commands will integrate via `git rebase` instead of `git merge`.

# `git pull` Examples
The following examples demonstrate how to use `git pull` in common scenarios:

# Default Behavior
```shell 
git pull
```
Executing the default invocation of `git pull` will is equivalent to `git fetch origin HEAD` and `git merge HEAD` where HEAD is ref pointing to the current branch.

# `git pull` on remotes

```shell 
git checkout new_feature
git pull <remote repo>
```
This example first performs a checkout and switches to the branch. Following that, the `git pull` is executed with being passed. This will implicitly pull down the newfeature branch from . Once the download is complete it will initiate a `git merge`.

`git pull rebase` instead of merge
The following example demonstrates how to synchronize with the central repository's master branch using a rebase:

```shell 
git checkout master
git pull --rebase origin
```
This simply moves your local changes onto the top of what everybody else has already contributed.
	
*information for this section came from* [Atlassian BitBucket: git pull](https://www.atlassian.com/git/tutorials/syncing/git-pull)
</details>

<details>
	<summary>git stash</summary>
	
Usage: Git stash

`git stash` temporarily shelves (or stashes) changes you've made to your working copy so you can work on something else, and then come back and re-apply them later on. Stashing is handy if you need to quickly switch context and work on something else, but you're mid-way through a code change and aren't quite ready to commit.

[Git Stash](#git-stash)

[Stashing your work](#stashing-your-work)

[Re-applying your stashed changes](#re-applying-your-stashed-changes)

[Stashing untracked or ignored files](#stashing-untracked-or-ignored-files)

[Managing multiple stashes](#managing-multiple-stashes)

[Viewing stash diffs](#viewing-stash-diffs)

[Partial stashes](#partial-stashes)

[Creating a branch from your stash](creating-a-branch-from-your-stash)

[Cleaning up your stash](#cleaning-up-your-stash)

[How git stash works](#how-git-stash-works)

# Stashing your work

The `git stash` command takes your uncommitted changes (both staged and unstaged), saves them away for later use, and then reverts them from your working copy. For example:

```shell
$ git status On branch master Changes to be committed: new file: style.css Changes not staged for commit: modified: index.html $ git stash Saved working directory and index state WIP on master: 5002d47 our new homepage HEAD is now at 5002d47 our new homepage $ git status On branch master nothing to commit, working tree clean
```

At this point you're free to make changes, create new commits, switch branches, and perform any other Git operations; then come back and re-apply your stash when you're ready.

Note that the stash is local to your Git repository; stashes are not transferred to the server when you push.

# Re-applying your stashed changes
You can reapply previously stashed changes with `git stash pop`:

```shell
$ git status On branch master nothing to commit, working tree clean $ git stash pop On branch master Changes to be committed: new file: style.css Changes not staged for commit: modified: index.html Dropped refs/stash@{0} (32b3aa1d185dfe6d57b3c3cc3b32cbf3e380cc6a)
```
Popping your stash removes the changes from your stash and reapplies them to your working copy.

Alternatively, you can reapply the changes to your working copy and keep them in your stash with `git stash apply`:

```shell
$ git stash apply On branch master Changes to be committed: new file: style.css Changes not staged for commit: modified: index.html
```
This is useful if you want to apply the same stashed changes to multiple branches.

Now that you know the basics of stashing, there is one caveat with `git stash` you need to be aware of: by default Git won't stash changes made to untracked or ignored files.

# Stashing untracked or ignored files
By default, running `git stash` will stash:

* changes that have been added to your index (staged changes)
* changes made to files that are currently tracked by Git (unstaged changes)
But it will not stash:

* new files in your working copy that have not yet been staged
* files that have been ignored
So if we add a third file to our example above, but don't stage it (i.e. we don't run git add), `git stash` won't stash it.

```shell
$ script.js $ git status On branch master Changes to be committed: new file: style.css Changes not staged for commit: modified: index.html Untracked files: script.js $ git stash Saved working directory and index state WIP on master: 5002d47 our new homepage HEAD is now at 5002d47 our new homepage $ git status On branch master Untracked files: script.js
```
Adding the `-u` option (or `--include-untracked`) tells `git stash` to also stash your untracked files:

```shell
$ git status On branch master Changes to be committed: new file: style.css Changes not staged for commit: modified: index.html Untracked files: script.js $ git stash -u Saved working directory and index state WIP on master: 5002d47 our new homepage HEAD is now at 5002d47 our new homepage $ git status On branch master nothing to commit, working tree clean
```
You can include changes to ignored files as well by passing the `-a` option (or `--all`) when running `git stash`.

# Managing multiple stashes
You aren't limited to a single stash. You can run `git stash` several times to create multiple stashes, and then use `git stash` list to view them. By default, stashes are identified simply as a "WIP" – work in progress – on top of the branch and commit that you created the stash from. After a while it can be difficult to remember what each stash contains:

```shell
$ git stash list stash@{0}: WIP on master: 5002d47 our new homepage stash@{1}: WIP on master: 5002d47 our new homepage stash@{2}: WIP on master: 5002d47 our new homepage
```
To provide a bit more context, it's good practice to annotate your stashes with a description, using `git stash` save "message":

```shell
$ git stash save "add style to our site" Saved working directory and index state On master: add style to our site HEAD is now at 5002d47 our new homepage $ git stash list stash@{0}: On master: add style to our site stash@{1}: WIP on master: 5002d47 our new homepage stash@{2}: WIP on master: 5002d47 our new homepage
```
By default, `git stash pop` will re-apply the most recently created `stash: stash@{0}`

You can choose which stash to re-apply by passing its identifier as the last argument, for example:

```shell
$ git stash pop stash@{2}
```

# Viewing stash diffs
You can view a summary of a stash with `git stash show`:

```shell
$ git stash show index.html | 1 + style.css | 3 +++ 2 files changed, 4 insertions(+)
```
Or pass the `-p` option (or `--patch`) to view the full diff of a stash:

```shell
$ git stash show -p diff --git a/style.css b/style.css new file mode 100644 index 0000000..d92368b --- /dev/null +++ b/style.css @@ -0,0 +1,3 @@ +* { + text-decoration: blink; +} diff --git a/index.html b/index.html index 9daeafb..ebdcbd2 100644 --- a/index.html +++ b/index.html @@ -1 +1,2 @@ +
```

# Partial stashes
You can also choose to stash just a single file, a collection of files, or individual changes from within files. If you pass the `-p` option (or `--patch`) to `git stash`, it will iterate through each changed "hunk" in your working copy and ask whether you wish to stash it:

```shell
$ git stash -p diff --git a/style.css b/style.css new file mode 100644 index 0000000..d92368b --- /dev/null +++ b/style.css @@ -0,0 +1,3 @@ +* { + text-decoration: blink; +} Stash this hunk [y,n,q,a,d,/,e,?]? y diff --git a/index.html b/index.html index 9daeafb..ebdcbd2 100644 --- a/index.html +++ b/index.html @@ -1 +1,2 @@ + Stash this hunk [y,n,q,a,d,/,e,?]? n
```

You can hit `?` for a full list of hunk commands. Commonly useful ones are:

|Command|Description|
|:---:|:---:|
|/ | search for a hunk by regex |
|?| help |
|n| don't stash this hunk |
|q| quit (any hunks that have already been selected will be stashed) |
|s| split this hunk into smaller hunks |
|y| stash this hunk |

There is no explicit "abort" command, but hitting `CTRL`-`C`(SIGINT) will abort the stash process.

# Creating a branch from your stash
If the changes on your branch diverge from the changes in your stash, you may run into conflicts when popping or applying your stash. Instead, you can use `git stash branch` to create a new branch to apply your stashed changes to:

 
```shell
$ git stash branch add-stylesheet stash@{1} Switched to a new branch 'add-stylesheet' On branch add-stylesheet Changes to be committed: new file: style.css Changes not staged for commit: modified: index.html Dropped refs/stash@{1} (32b3aa1d185dfe6d57b3c3cc3b32cbf3e380cc6a)
```
This checks out a new branch based on the commit that you created your stash from, and then pops your stashed changes onto it.

# Cleaning up your stash
If you decide you no longer need a particular stash, you can delete it with `git stash drop`:

```shell
$ git stash drop stash@{1} Dropped stash@{1} (17e2697fd8251df6163117cb3d58c1f62a5e7cdb)
```
Or you can delete all of your stashes with:

```shell
$ git stash clear
```

# How git stash works
If you just wanted to know how to use `git stash`, you can stop reading here. But if you're curious about how Git (and `git stash`) works under the hood, read on!

Stashes are actually encoded in your repository as commit objects. The special ref at .git/refs/stash points to your most recently created stash, and previously created stashes are referenced by the stash ref's reflog. This is why you refer to stashes by stash@{n}: you're actually referring to the nth reflog entry for the stash ref. Since a stash is just a commit, you can inspect it with git log:

```shell
$ git log --oneline --graph stash@{0} *-. 953ddde WIP on master: 5002d47 our new homepage |\ \ | | * 24b35a1 untracked files on master: 5002d47 our new homepage | * 7023dd4 index on master: 5002d47 our new homepage |/ * 5002d47 our new homepage
```
Depending on what you stashed, a single `git stash` operation creates either two or three new commits. The commits in the diagram above are:

* stash@{0}, a new commit to store the tracked files that were in your working copy when you ran git stash
* stash@{0}'s first parent, the pre-existing commit that was at HEAD when you ran git stash
* stash@{0}'s second parent, a new commit representing the index when you ran git stash
* stash@{0}'s third parent, a new commit representing untracked files that were in your working copy when you ran git stash. This third parent only created if:
	* your working copy actually contained untracked files; and
	* you specified the --include-untracked or --all option when invoked git stash.
	
How git stash encodes your worktree and index as commits:

Before stashing, your worktree may contain changes to tracked files, untracked files, and ignored files. Some of these changes may also be staged in the index.

Invoking `git stash` encodes any changes to tracked files as two new commits in your DAG: one for unstaged changes, and one for changes staged in the index. The special refs/stash ref is updated to point to them.

Using the `--include-untracked` option also encodes any changes to untracked files as an additional commit.

Using the `--all` option includes changes to any ignored files alongside changes to untracked files in the same commit.

When you run `git stash pop`, the changes from the commits above are used to update your working copy and index, and the stash reflog is shuffled to remove the popped commit. Note that the popped commits aren't immediately deleted, but do become candidates for future garbage collection.
	
*information found at* [Atlassian BitBucket: git stash](https://www.atlassian.com/git/tutorials/saving-changes/git-stash#managing-multiple-stashes)
</details>


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
