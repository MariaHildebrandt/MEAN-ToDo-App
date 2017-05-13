# MEAN-ToDo-App

Simple productivity one-site-application. Screenshots below

## Includes
- [Bootstrap](http://getbootstrap.com/) 
- [Font-Awesome](http://fontawesome.io/)
- [Google Fonts](https://fonts.google.com/)
- [License free Images from Pexels.com](https://nodejs.org/en/) 
- Database (NoSQL, [MongoDB](https://www.mongodb.com/) ) wie MongoJS
- adapted [Template ](...)

## Requirements
- [Node.js](https://nodejs.org/en/)
- [MongoDB](https://www.mongodb.com/) (installation manual below in "How to Recreate Environment")

## Manual Setup
1. Download mit Git:
```bash
git clone https://github.com/MariaHildebrandt/MEAN-ToDo-App projectname
```
2. navigate to projectname and install with node package manager
```bash
npm install
```
3. start your project and open http://localhost:3000 in your browser
```bash
npm start
```

## Screenshots

#### Full View:
<p>
  <a href=""></a>,
  <a href="https://postimg.org/image/fxabdd09r/">Login</a>
</p>

#### Preview:
<p align="left">
  <img src="https://s19.postimg.org/8g13y5aqr/nodelogreg.png"  width="400px">
</p>

## ToDo and Bugs
#### Bugs: 
- no known bugs
#### ToDo: 
- ...

## How to Recreate Environment
### Express Server Setup
#### 1.) Create Package.json file
- create a new folder. open folder in git bash or cmd
```bash
npm init
```
- follow the instructions.Entry Point will be server.js. 
#### 2.) Install Dependencies
```bash
npm install express mongojs ejs body-parser --save
```
#### 3.) Create server.js file
- enter all dependencies
- setup routes
- setup views folder for templates and views like ejs: regular html with extra variables to create syntax and more
```bash
var express = require('express');
var path = require('path');
var bodyParser = require('body-parser');

var index = require('./routes/index');
var todos = require('./routes/todos');

//instantiate express
var app = express();

//template Engine
app.set('views', path.join(__dirname, 'views'));
app.set('view engine', 'ejs');

//body-parser
app.use(bodyPaser.json());
app.use(bodyParser.urlencoded({extended: false}));

//routes, refers to var index, todos above
app.use('/', index);
app.use('/api/v1', todos);

//open port
app.listen(3000, function(){
  console.log('Server started on port 3000...');
});
```
#### 4.) create a view for index
- on the same level as the views folder, create a new folder named 'routes'
- routes will have two files: index.js and todos.js
- in index.js:
```bash
var express = require('express');
var router = express.Router();

//will print out message in browser if successful setup
router.get('/', function(req, res, next){
  res.send('INDEX');
});

module.exports = router;
```
- copy&paste into todos.js with 
```bash
//...
router.get('/todos', function(req, res, next){ res.send('TODOS API');});
//...
```
#### 5.) run in cmd 
```bash
node server
```
- http://localhost:3000 will show INDEX
- http://localhost:3000/api/v1/todos will show TODOS API

