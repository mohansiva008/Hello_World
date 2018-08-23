# Hello_World
console.log('Hello World');
var express = require('express');
var http = require('http');
var url = require('url');
var bodyparse = require ('body-parser');
var fs = require('fs');
var app = express();
var names;
//Assign the port to listen
var server = app.listen(8880, function() {
    console.log('Ready on port %d', server.address().port);
});
//use the engine to provide the template (Note: all the html files are in the engine format(.ejs) is only acceptable)
app.set('view engine', 'ejs');
app.get('/home', (req, res) => res.send('Hello World, Welcome home dude!!')); 
app.get('', (req, res) => res.send('Sorry, Please Check your url...Here No one exist'));
app.get('/html', function (req, res) { 
    res.render('sign_in');
});
app.use(bodyparse.urlencoded({extended:false}));
app.use(bodyparse.json());
var myauthmap = new Map();
app.post('/login', function(req, res) { 
    
    var champ = req.body.username;
    res.render('User_Sign_Up');
    res.send(req.body);
});


///Install the .ejs and express.js and parseurl (For URL module to get the information from your URL);
