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

//////////////////////////////////////////////////////////////today change ////////////////////////////////////////////
app.post('/login', function(req, res) { 
    
    var champ = req.body.username;
    console.log(req.body.username); 
    console.log(req.body.flag);
    var str = req.body.flag;
    
    if (str == 'true') {
        console.log('enter the true log');
        //if the password and username are success let the stop the page here
        res.send(req.body);
    }
    else{
        //if the auth details are not correct please redirect to the sign up page
        res.sendFile(__dirname+"/views/User_Sign_Up.html");
    }
});
app.post('/signup', function(req, res) {
    //Show the received data
    req.send(res);
});

///Install the .ejs and express.js and parseurl (For URL module to get the information from your URL);
