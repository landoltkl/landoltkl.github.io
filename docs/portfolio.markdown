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
    .controls {
      max-width: 1000px;
      margin: 0 auto 20px;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      gap: 10px;
    }
    select {
      padding: 8px;
      font-size: 16px;
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
      display: flex;
      flex-direction: column;
      align-items: center;
      /* justify-content: space-between; */
      background-color: #ffffff;
      border: 2px solid #4CAF50;
      border-radius: 10px;
      padding: 10px;
      height: 180px;
      cursor: pointer;
      transition: transform 0.2s ease;
      text-align: center;
      box-sizing: border-box;
      max-width: 180px
    }
    .grid-button img {
      max-width: 100%;
      max-height: 90px;
      object-fit: contain;
      border-radius: 6px;
    }
    .grid-button span {
      margin-top: 8px;
      font-size: 16px;
      font-weight: bold;
      color: #333;
    }
    .grid-button:hover {
      background-color: #45a049;
    }
    .hidden {
      display: none;
    }
  </style>
</head>
<body>

  <div class="controls">
    <label for="categoryFilter">Filter by category:</label>
    <select id="categoryFilter">
      <option value="all">All</option>
      <option value="conf_pres">Conferences and Presentations</option>
      <option value="pub">ScienceBase Publications</option>
      <option value="personal">Personal Projects</option>
    </select>
  </div>

  <div class="grid-container" id="buttonGrid"></div>

  <script>
    const pages = [
      { 
        label: "University of Michigan Poster", 
        url: "/portfolio/umich", 
        category: "conf_pres" , 
        img_display: "../assets/img/UMICH_2023_Poster.png"
        },
      { 
        label: "Annotation dataset for of avian species", 
        url: "https://www.sciencebase.gov/catalog/item/63bf21cdd34e92aad3cdac5a" , 
        category: "pub" ,
        img_display: "../assets/img/USGS_logo_green.png"
        },
      { 
        label: "Aerial thermal imagery and annotations of sandhill cranes",
        url: "https://www.sciencebase.gov/catalog/item/634eb641d34e47431c1543d4",
        category: "pub",
        img_display: "../assets/img/USGS_logo_green.png"
        },
      {
        label: "Code, imagery, and annotations for training a DL model",
        url: "https://www.sciencebase.gov/catalog/item/658da7c1d34e3265ab14bb00",
        category: "pub",
        img_display: "../assets/img/USGS_logo_green.png"
        },
      {
        label: " La Crosse, Wisconsin, Sanborn Maps",
        url: "/portfolio/sanborn",
        category: "personal",
        img_display: "../assets/img/sanborn_lax_pearl.png"
        }
    ];

    const grid = document.getElementById("buttonGrid");

    // Create buttons
    pages.forEach(page => {
        const button = document.createElement("button");
        button.className = "grid-button";
        // button.textContent = page.label;
        button.dataset.category = page.category;
            //   button.style.backgroundImage = `url('${page.img_display}')`;
        button.onclick = () => window.location.href = page.url;

        const img = document.createElement("img");
        img.src = page.img_display;
        img.alt = page.label;
        
        const label = document.createElement("span");
        label.textContent = page.label;
        button.appendChild(img);
        button.appendChild(label);
        grid.appendChild(button);
    });
    // Filter logic
    const filter = document.getElementById("categoryFilter");
    filter.addEventListener("change", () => {
      const selected = filter.value;
      const buttons = document.querySelectorAll(".grid-button");

      buttons.forEach(btn => {
        const category = btn.dataset.category;
        btn.classList.toggle("hidden", selected !== "all" && category !== selected);
      });
    });
  </script>

</body>
</html>