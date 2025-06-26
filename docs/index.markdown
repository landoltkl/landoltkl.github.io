---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

<html>
<head>
<meta charset="utf-8">
<style>
  .container {
  display: flex; /* Makes the container a flex container */
  flex-wrap: wrap;
  align-items: center; /* Vertically aligns items in the center (optional) */
  flex-direction: row;
  justify-content: space-around;
  margin: auto;
  }
  img {
    max-width: 50%; /* Image can take up to 50% of the container width */
    height: auto; /* Maintains aspect ratio during resize */
    margin-right: 15px; /* Adds space between image and text (optional) */
    margin-bottom: 30px;
    border: 3px solid
  }
  .text {
    flex: 1; /* Allows text to take up remaining space */
  }
  @media (max-width: 800px) {
    .container {
      flex-direction: column;
      text-align: center;
    }
  }
</style>
</head>
<body>

<div class="container">
  <img src="../assets/img/IMG_20250412_183143_jek.JPG" alt="Description of image">
  <div class="text">
  <p>I try to fit the nature of the world onto silicon chips. And that doesn’t just mean I’ve tried growing tomatoes on my computer’s graphics card (believe me, it doesn’t work that well).

Being able to answer complex geospatial questions using a variety of open-source software has been driving my passion and ultimately my career. I love to see spatial data make an impact in how we understand the world and how that benefits both the people and the natural environment that the world is composed of.<br><br>

I apply that mentality to my work at USGS with the Upper Midwest Environmental Sciences Center. I use machine learning, remote sensing, and other tools to detect, analyze, and understand wildlife in aerial imagery. This work gives me the opportunity to explore geospatial, statistical, and machine learning techniques to take advantage of ‘big data’ and provide explanations for large-scale phenomena.<br><br>

Outside of work I enjoy baking, fishing, kayaking, hiking, and spending time with my dog Russ.</p>
</div>
</div>