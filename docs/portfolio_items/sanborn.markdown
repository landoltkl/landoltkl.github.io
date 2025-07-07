---
layout: page
title: La Crosse, Wisconsin, Sanborn Maps
permalink: /portfolio/sanborn
---

<html>
<head>
<meta charset="utf-8">
<title>Sanborn Map</title>
<meta name="viewport" content="initial-scale=1,maximum-scale=1,user-scalable=no">
<link href="https://api.mapbox.com/mapbox-gl-js/v3.12.0/mapbox-gl.css" rel="stylesheet">
<script src="https://api.mapbox.com/mapbox-gl-js/v3.12.0/mapbox-gl.js"></script>
<style>
body { margin: 0; padding: 0; }
/* #map { position: relative;  } */
/* #map { position: absolute; top: 20%; right:20%; bottom: 20%; left:20%; } */
#map {  width: 100%; height:400px }
</style>
</head>
<body>
Digitizing historical 1884 Sanborn Maps for La Crosse, Wisconsin, to 3D polygons for visualization.
<style>
    #menu {
        background: #fff;
        position: absolute;
        z-index: 1;
        top: 10px;
        right: 10px;
        border-radius: 3px;
        width: 120px;
        border: 1px solid rgba(0, 0, 0, 0.4);
        font-family: 'Open Sans', sans-serif;
    }
    #menu a {
        font-size: 13px;
        color: #404040;
        display: block;
        margin: 0;
        padding: 0;
        padding: 10px;
        text-decoration: none;
        border-bottom: 1px solid rgba(0, 0, 0, 0.25);
        text-align: center;
    }
    #menu a:last-child {
        border: none;
    }
    #menu a:hover {
        background-color: #f8f8f8;
        color: #404040;
    }
    #menu a.active {
        background-color: #3887be;
        color: #ffffff;
    }
    #menu a.active:hover {
        background: #3074a4;
    }
</style>
<div id="map"></div>
<nav id="menu"></nav>
<div id="map"></div>
<script>
	mapboxgl.accessToken = 'pk.eyJ1IjoibGFuZG9sdGtsIiwiYSI6ImNtYzg3Y2tqNTB0ZzUybHBrdmNpNzVtNWUifQ.nkZuU2AjjAtWrJ_LLfXulA';
    const map = new mapboxgl.Map({
        container: 'map',
        style: 'mapbox://styles/landoltkl/cmcqkoydf00mc01s1clc65muj',
        projection: 'globe', // Display the map as a globe, since satellite-v9 defaults to Mercator
        zoom: 15,
        center: [-91.252, 43.814]
    });
    map.addControl(new mapboxgl.NavigationControl());
    map.scrollZoom.disable();
    map.on('style.load', () => {
        map.setFog({}); // Set the default atmosphere style
    });
    // The following values can be changed to control rotation speed:
    // At low zooms, complete a revolution every two minutes.
    const secondsPerRevolution = 240;
    // Above zoom level 5, do not rotate.
    const maxSpinZoom = 5;
    // Rotate at intermediate speeds between zoom levels 3 and 5.
    const slowSpinZoom = 3;
    let userInteracting = false;
    const spinEnabled = true;
    function spinGlobe() {
        const zoom = map.getZoom();
        if (spinEnabled && !userInteracting && zoom < maxSpinZoom) {
            let distancePerSecond = 360 / secondsPerRevolution;
            if (zoom > slowSpinZoom) {
                // Slow spinning at higher zooms
                const zoomDif =
                    (maxSpinZoom - zoom) / (maxSpinZoom - slowSpinZoom);
                distancePerSecond *= zoomDif;
            }
            const center = map.getCenter();
            center.lng -= distancePerSecond;
            // Smoothly animate the map over one second.
            // When this animation is complete, it calls a 'moveend' event.
            map.easeTo({ center, duration: 1000, easing: (n) => n });
        }
    }
    // Pause spinning on interaction
    map.on('mousedown', () => {
        userInteracting = true;
    });
    map.on('dragstart', () => {
        userInteracting = true;
    });
    // When animation is complete, start spinning if there is no ongoing interaction
    map.on('moveend', () => {
        spinGlobe();
    });
    spinGlobe();
    map.on('load', () => {
  // Replace 'your-layer-id' with the actual ID of the layer in your style
        const layerId = 'lax-draft1-4326-8-a6w8qq';
        document.getElementById('toggle-layer').addEventListener('click', () => {
            const visibility = map.getLayoutProperty(layerId, 'visibility');
            if (visibility === 'visible') {
            map.setLayoutProperty(layerId, 'visibility', 'none');
            } else {
            map.setLayoutProperty(layerId, 'visibility', 'visible');
            }
        });
        });

</script>

</body>
</html>