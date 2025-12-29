---
title: Learning Astro
author: Matias Tupper  
description: A post about learning Astro to make my portfolio site
image:
    url: 'https://docs.astro.build/assets/rose.webp'
    alt: 'The Astro logo on a dark background with a pink glow.'
pubDate: 2025-12-29
tags: ["astro", "notebook", "learning in public"]
---
# Learning Astro

I will be using this post as an Astro learning notebook. As I continue working through [this](https://docs.astro.build/en/tutorial/0-introduction/) Astro tutorial, I will take some small notes here that shoul be eveything I've learned about what Astro is and how to use it.

## What is Astro?

Astro is a JavaScript web framework optimized for building fast, content driven websites. It allows you to use heavier JS frameworks to build fast, 100% static sites. My GOAT fireship has an [Astro in 100 Seconds](https://www.youtube.com/watch?v=dsTXcSeAZq8&pp=ygUOYXN0cm8gZmlyZXNoaXA%3D) video.

## Astro tutorial

Starting an Astro project is as simple as running `npm create astro@latest`. Then you'll be prompted for downloading dependecies, starting a new git repository, and also options for a starter template

Once you got your project started, to preview the site you can run `npm run dev` to open an Astro dev server you can prieview in your browser.

### Astro Pages

To start editing the content on your site, go to `src/pages/` in your directory. There you'll find `index.astro` along with any other pages that make up your site. `.astro` files are how you build pages for your site, and like always `index.astro` will be your default "home" page. the `index.astro` file of a fresh project will look something like this:

```
---
<!-- Frontmatter script, Here you write any JS for yout page -->
---
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width" />
    <meta name="generator" content={Astro.generator} >
    <title>Astro</title>
  </head>
  <body>
    <h1>Astro</h1>
  </body>
</html>
```

inside your astro file, you can edit your HTML content just as you would a regular HTML file. After saving any changes you'll see the updated content on your dev server in your browser.

Astro is great for making blogs and posts using Markdown. You can make content in `.md` files and Astro converts it to HTML. For example, this post is being written as an `.md` file, but you are seein git converted into HTML on my site!

To start utilizing JS when building Astro pages, you can write JavaScript or TypeScript expressions in the forntmatter at the very beggining of you `.astro` file, and then use what you defined in your astro template by using curly braces `{}` to tell astro you're using some JavaScript.

For example: 
After adding the following JavaScript to your frontmatter, between the code fences:
```
---
const pageTitle = "About Me";

const identity = {
  firstName: "Sarah",
  country: "Canada",
  occupation: "Technical Writer",
  hobbies: ["photography", "birdwatching", "baseball"],
};

const skills = ["HTML", "CSS", "JavaScript", "React", "Astro", "Writing Docs"];
---
```

You can add the following code into your HTML template:
```
<p>Here are a few facts about me:</p>
<ul>
  <li>My name is {identity.firstName}.</li>
  <li>I live in {identity.country} and I work as a {identity.occupation}.</li>
  {identity.hobbies.length >= 2 &&
    <li>Two of my hobbies are: {identity.hobbies[0]} and {identity.hobbies[1]}</li>
  }
</ul>
<p>My skills are:</p>
<ul>
  {skills.map((skill) => <li>{skill}</li>)}
</ul>
```

The key takeaways about using JavaScript in Astro are:
1. Writing an Astro template is very much like writing HTML, but you can include JavaScript Expressions within it.
2. The Astro frontmatter script contains only JavaScript.
3. You can use all modern JavaScript logical operator, expressions and function in either section of your `.astro` file. But, curly braces are necesarry (only) in the HTML template body.

You can use this to conditionally render HTML elements using JavaScript logical operators. For example:
```
---
const happy = true;
const finished = false;
const goal = 3;
---
```

Lets you do things like:
```
{happy && <p>I am happy to be learning Astro!</p>}

{finished && <p>I finished this tutorial!</p>}

{goal === 3 ? <p>My goal is to finish in 3 days.</p> : <p>My goal is not 3 days.</p>}
```