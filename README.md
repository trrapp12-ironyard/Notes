
## Coding Notes

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

## An Accordion in Markdown: 

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


## Git Commands: 

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
	
Usage: think of `git add` as saving your changes.  It is usually preceeded by a `git status` to see if there are any files that are not being tracked.  `git status` will show a list of files in green{: style="color: red; opacity: 0.80;" } and a list of <span style="color:red">files in red</span>.  The ones in red are ones that the git repository "can't see" or "is not currently tracking."  Adding them will change the untracked status to a tracked status, thereby enabling you to push them up to the git repository.  Without adding them there is not a way to push them from your local branch (the changes you make on your computer) to the master branch (the branch that lives in the GitHub cloud that everyone else is also adding information to.)   

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
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
</details>

<details>
	<summary>git diff</summary>
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
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
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
</details>

<details>
	<summary>git rm</summary>
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
</details>

<details>
	<summary>git log</summary>
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
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
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
</details>

<details>
	<summary>git branch</summary>
	
Usage: 
	
Example: 
	
```shell
git config --global user.email "your_email@example.com"
```

	
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

## Coding Project Ideas

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



