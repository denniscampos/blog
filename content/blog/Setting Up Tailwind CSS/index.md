---
title: Setting up Tailwind CSS with NodeJS & Express [BEGINNER]
date: "2021-05-04T22:12:03.284Z"
description: "I am writing this tutorial because I feel setting up tailwindcss is not the easiest thing to do for a beginner."
---

## Introduction
I was inspired to write this tutorial because setting up TailWind CSS is not the easiest thing for a beginner. The documentation is excellent, but they use many disrespectful words 😂 for a beginner.

This tutorial is meant for anyone who wants to set up TailWindCSS with NodeJS & Express.

You don't need NodeJS and Express to get this going - you can always right-click your HTML file to run it locally on your machine.

I am going to assume you have a bit of experience with the command line and NodeJS.

Let's GET TO IT!!! 💯💯
![lets go](https://media.giphy.com/media/LoCDk7fecj2dwCtSB3/giphy.gif)

## The Setup
Open up your favorite texteditor and create a new folder. Name it whatever you'd like. 

Open up the terminal (if you use VSCode, you can press CTRL + J or CMD + J for MAC) and type the following: 

`$ npm init` 

Follow the prompt until a file name `package.json` is created in your folder.

## Installing Our Dependencies. 
Let's get this out the way now. Use the following commands in your terminal:

`$ npm install express`

`$ npm install -D tailwindcss@latest postcss@latest autoprefixer@latest`

And yes…you can install multiple packages without doing it one by one, but I want to make this as readable as possible. 😊

If everything went through, then you should see the following in your `package.json` file:

`express` under dependencies 

and three dependencies name under devDependencies called 
```
autoprefixer
postcss 
tailwindcss
```

I excluded the version number for this tutorial.

## Creating Our Files

Great - if you happened to be stuck, please reach out to me on [Twitter](https://twitter.com/dnbull) 😃

Let's create our folders and files and get it up and running! 

Create a folder called `public` & `src`. 
NOTE: public folder can be called anything you'd like but be sure it makes sense! 

Inside both folders, create a file called `styles.css` 

Inside the public folder, create a file called  `index.html`

Let's open up `styles.css` file inside the `src` folder and copy and paste the folllowing: 

``` 
@tailwind base;
@tailwind components;
@tailwind utilities;
```
You're halfway there! 
![Almost there](https://media.giphy.com/media/xUOxfh6ZM75efM3Bqo/giphy.gif)

Before we officially get tailwind going, let's quickly set up our server.

Create a file called `server.js` 
Note: You can also called this something else.

Copy and paste the following: 

```
const express = require('express')
const app = express();
const PORT = 3000; 

// Server Setup
app.use(express.static('public'))
app.use(express.urlencoded({ extended: true }))
app.use(express.json())

app.get('/', (req, res) => {
    res.send('hello world')
})

app.listen(PORT, () => {
    console.log(`Server running on port ${PORT}`)
})
```

Please, please, please contact me if the code above does not make sense to you. 

In your terminal, type the following: 

`$ node server` 

Note: if you called your server.js something else, use the name you decided to use. Example `$ node app`

You should see a message in the terminal that says, "Server running on port 3000" 

In your browser, open up the following URL: https://localhost:3000/

If you see "hello world" your server is officially up and running.

But... let's kill our server for now. In the terminal press and hold CTRL + C or CMD + C for MAC users.

## Let's Get Tailwind Officially Going

Open up `package.json` file and add the following under scripts: 

`"build-css": "tailwindcss build src/styles.css -o public/styles.css" `

This will allow us to build tailwind with our terminal. So lets open up our terminal again. 

Type the following: 

`$ npm run build-css`

You can check if this went through by going inside the public/styles.css file. You are going to see a bunch of scary stuff.

CONGRATULATIONS you have tailwind set up along with NodeJs & Express.

But... let's add a few more details to make sure you can enjoy tailwind. 

Inside the `index.html` make sure you created your HTML boiler plate. I will leave an example below.

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="styles.css">
    <title>Tailwind Fun</title>
</head>
<body>
    <div>
        <h1 class="bg-blue-400">Hello World!</h1>
    </div>
</body>
</html>
```

A few things to note - For our CSS, it will be styles.css without having to say "public/styles.css"

I left a class in the H1 element so that you can see if tailwind is officially working. 

## The Last Step 😲: 

Let's run our server again. 

In the terminal type the following: 

`$ node server`

Open up http://localhost:3000 in your browser and VOILA!!

Congratulations! You did it!!
![you did it](https://media.giphy.com/media/H1NIKdfygAAMruqArl/giphy.gif)

Visit tailwind's documentation and play around with the class for html elements. 

Here's an [example](https://tailwindcss.com/docs/background-color)

Pick a color to add to our HTML element. Example: 

```
<p class="bg-gray-400">some random text</p>
``` 
When you save and refresh your server, you should see a background color on your paragraph element. You can add as many classes as you like to one element.

If you do not like the tedious process of killing your server every time then I highly recommend [nodemon](https://www.npmjs.com/package/nodemon) 😄

If you get stuck anywhere throughout the tutorial please do not hesitate to contact me! Thank you so much for reading 💯

