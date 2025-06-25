---
layout: page
title: La Crosse, Wisconsin, Sanborn Maps
permalink: /portfolio/sanborn
---

Pending Updates

<html>
<head>
<meta charset="utf-8">
<title>Guides</title>
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
<div id="map"></div>
<script>
	// TO MAKE THE MAP APPEAR YOU MUST
	// ADD YOUR ACCESS TOKEN FROM
	// https://account.mapbox.com
	mapboxgl.accessToken = 'pk.eyJ1IjoibGFuZG9sdGtsIiwiYSI6ImNtYzg3Y2tqNTB0ZzUybHBrdmNpNzVtNWUifQ.nkZuU2AjjAtWrJ_LLfXulA';
    const map = new mapboxgl.Map({
        container: 'map',
        style: 'mapbox://styles/mapbox/streets-v9',
        projection: 'globe', // Display the map as a globe, since satellite-v9 defaults to Mercator
        zoom: 1,
        center: [30, 15]
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
</script>