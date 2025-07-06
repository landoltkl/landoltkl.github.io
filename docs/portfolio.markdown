---
layout: page
title: Portfolio
permalink: /portfolio/
---

<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Responsive Button Grid</title>
  <style>
    body {
      font-family: sans-serif;
      background-color: #f9f9f9;
      margin: 0;
      padding: 20px;
      box-sizing: border-box;
    }
    .grid-container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 15px;
      width: 100%;
      max-width: 1000px;
      margin: 0 auto;
    }
    .grid-button {
      background-color:rgb(104, 102, 142);
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      padding: 15px;
      cursor: pointer;
      transition: background-color 0.3s ease;
      width: 150px;
      height: 150px;
      box-sizing: border-box;
    }
    .grid-button:hover {
      background-color:rgb(71, 73, 71);
    }
  </style>
</head>
<body>

  <div class="grid-container" id="buttonGrid"></div>

  <script>
    const pages = [
      { label: "University of Michigan Poster", url: "/portfolio/umich" },
      { label: "Images and annotations to automate the classification of avian species", url: "https://www.sciencebase.gov/catalog/item/63bf21cdd34e92aad3cdac5a" },
      { label: "Aerial thermal imagery of the Central Platte River Valley and bounding box annotations of sandhill cranes", url: "https://www.sciencebase.gov/catalog/item/634eb641d34e47431c1543d4" },
      { label: "Code, imagery, and annotations for training a deep learning model to detect wildlife in aerial imagery", url: "https://www.sciencebase.gov/catalog/item/658da7c1d34e3265ab14bb00" },
      { label: "La Crosse, Wisconsin, Sanborn Maps", url: "/portfolio/sanborn" }
    ];

    const grid = document.getElementById("buttonGrid");

    pages.forEach(page => {
      const button = document.createElement("button");
      button.className = "grid-button";
      button.textContent = page.label;
      button.onclick = () => window.location.href = page.url;
      grid.appendChild(button);
    });
  </script>

</body>
</html>

<h2>Conferences and Presentations</h2>
<ul>
<li><a href="/portfolio/umich">University of Michigan Poster</a></li>
</ul>

<h2>ScienceBase Publications</h2>
<ul>
<li><a href="https://www.sciencebase.gov/catalog/item/63bf21cdd34e92aad3cdac5a">
Images and annotations to automate the classification of avian species</a><br></li>
<li><a href="https://www.sciencebase.gov/catalog/item/634eb641d34e47431c1543d4">
 Aerial thermal imagery of the Central Platte River Valley and bounding box annotations of sandhill cranes</a><br></li>
<li><a href="https://www.sciencebase.gov/catalog/item/658da7c1d34e3265ab14bb00">
Code, imagery, and annotations for training a deep learning model to detect wildlife in aerial imagery</a><br></li>
</ul>

<h2>For Fun</h2>
<ul>
<li><a href="/portfolio/sanborn">La Crosse, Wisconsin, Sanborn Maps</a></li>
</ul>