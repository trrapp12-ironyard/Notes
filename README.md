
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
	
	Usage: 
	
```shell
git config --global user.email "your_email@example.com"
```
	
```sh
git config --global user.email "your_email@example.com"
```
	
```bash
git config --global user.email "your_email@example.com"
```
	
```zsh
git config --global user.email "your_email@example.com"
```
	
```console
git config --global user.email "your_email@example.com"
```
	
```shell-session
git config --global user.email "your_email@example.com"
```
	
```powershell
git config --global user.email "your_email@example.com"
```
	
```ps
git config --global user.email "your_email@example.com"
```
	
```dos
git config --global user.email "your_email@example.com"
```
	
```bat
git config --global user.email "your_email@example.com"
```
	
```cmd
git config --global user.email "your_email@example.com"
```
	
```Shell
git config --global user.email "your_email@example.com"
```
	
```dos
git config --global user.email "your_email@example.com"
```
	
</details>

<details>
	<summary>git init</summary>
	explanation: 
	
</details>

<details>
	<summary>git clone</summary>
	explanation: 
	
</details>

<details>
	<summary>git add</summary>
	explanation: 
	
</details>

<details>
	<summary>git commit</summary>
	explanation: 
	
</details>

<details>
	<summary>git diff</summary>
	explanation: 
	
</details>

<details>
	<summary>git reset</summary>
	explanation: 
	
</details>

<details>
	<summary>git status</summary>
	explanation: 
	
</details>

<details>
	<summary>git rm</summary>
	explanation: 
	
</details>

<details>
	<summary>git log</summary>
	explanation: 
	
</details>

<details>
	<summary>git show</summary>
	explanation: 
	
</details>

<details>
	<summary>git tag</summary>
	explanation: 
	
</details>

<details>
	<summary>git branch</summary>
	explanation: 
	
</details>

<details>
	<summary>git checkout</summary>
	explanation: 
	
</details>

<details>
	<summary>git merge</summary>
	explanation: 
	
</details>

<details>
	<summary>git remote</summary>
	explanation: 
	
</details>

<details>
	<summary>git push</summary>
	explanation: 
	
</details>

<details>
	<summary>git pull</summary>
	explanation: 
	
</details>

<details>
	<summary>git stash</summary>
	explanation: 
	
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



