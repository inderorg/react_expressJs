project with express js
with es6 on both server and client side , so we will use babel
lets start with the empty and default settings using command that will create basic package.json file
$npm init -y 

after that add details and add your git repository url also if you want
then initialize the git repository ( empty now)
$git init
// then open the project in sublime, and lets add dependencies and code it, start by creating a folder name Server, and first file inside name index.js
so that (index.js) gonna be our main entry point , and here we wanna run our express server

$subl .  
index.js
	so here we import express from express and then initialize application using variable app by assigng it to express
let app = express()

app.get( ‘/*’,(req, res) =>{

 res.send(“Hello World”);

});

app.listen(3000, () =>console.log(“running on localhost:3000 	”));

———index.js ————
import express from 'express';

let app = express();

app.get('/*',(req, res) =>{
	res.send("hello world");

});

app.listen(3000, () => console.log( "server is listening port 3000"));
———————————— 

Now,  we need to check by running using below command
$node server/index.js
// note : as it will trow error because the import is unknown to the program , so we need to instal ldependencies for it 
// npm install --save-dev babel-cli 
// npm install --save express

now inside the package.json we will add “server” under script , 
“server” : “babel-node server/index.js”;
now we can run our server using below command
$npm run server
//note : but before proceeding to the above command we need to ensure that we have added one more devdependencies( for es2015) that is babel-preset-es2015
//also create new file named .babelrc and create object inside it as below
{
	“presets”:[ 
				“es2015”
			]
}

then, install devdevpendency for es2015
$npm install --save-dev babel-preset-es2015


Now after installing it , you can run command for your server
$npm run server

//so now we have the proper response 
//so lets set up a proper html file instead of the sting “hello world”


so change the response type of send to sendFile

and we use path package to join it with current directory with 
arguments ( _ _dirname, ‘’./index.html’)


res.sendFile(path.join( _ _dirname, ‘./index.html’));
and off course we need to import path from path

import path from ‘path’;


Now , create a new file inside server folder name index.html
and there just paste boiler plate html 

———index.html  —————— 
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Inder:My Web page</title>
	<meta content="width=device-width, initial-scale=1" name="viewport" />
</head>
<body>
	<h1>Hello , world </h1>

</body>
</html>

———————
 Now, we can not see the change until we rebuild ( restart the server ) 
thats not a good way to develop software
so, for that we need to install nodemon

npm install --save-dev nodemon
// so that we don’t need to restart server every time , 

and go back to package.json file 
“server”:” nodemon —watch server babel-node sever/index.js“,
so that we gonna watch only server folder , because we gonna have clients folder also that we don’t want to watch 
as we don’t want to restart server every time if we change to the client side , because client-side weill be handle by webpack so next we need to execute babel-node and we need to provider the file index.js to nodemon 


“server”: “nodemon —watch server —exec babel-node — server/index.js”,

that it so now if you change in html file and after reloading page you can see the changes
 next we need to push the worked code to git 
for that we need to create one more file 
.gitignore // that fill will consist of folders and files that we don’t want to push to git 

.DS_Store
node_modules






















 


































