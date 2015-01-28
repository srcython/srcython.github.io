---
layout: post
title: Hello World!
---

**Hello World!**


```js
var express = require('express');  
var async = require('async');  
var fs = require('fs');  
var app = express();

app.post('/process-file', function(req, res) {  
  var inputFile = 'input.txt';
  var outputFile = 'output.txt';

  var done = function(err, result) {
    if (err) return res.status(500).send(err);
    res.status(200).send('processed successfully with async');
  };

  async.waterfall([
    fs.readFile.bind(fs, inputFile),
    process1,
    process2,
    process3,
    fs.writeFile.bind(fs, outputFile)
  ], done);
});
```
