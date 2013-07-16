---
author: admin
comments: true
date: 2013-05-27 01:16:02+00:00
layout: post
slug: playing-with-google-map-api
title: Playing with Google Map API
wordpress_id: 1074
categories:
- Research
---

The main purpose of this post is only to write about Google Map API for future reference. Here are the code snippets :

Get the latitude and longitude based on address : [http://maps.googleapis.com/maps/api/geocode/json?address=435A%20Kent%20St&sensor=true](http://maps.googleapis.com/maps/api/geocode/json?address=435A%20Kent%20St&sensor=true)

The code below set up the Google Map, put the marker and also make it grayscale

``` javascript    
function initialize() {
    var map;
    var location = new google.maps.LatLng(-33.87190930, 151.20480740);
    var styles = [
        {
            featureType: "all",
            elementType: "all",
            stylers: [
                { saturation: -100 }
            ]
        }
    ];

    var mapOptions = {
        center: location,
        zoom: 17,
        mapTypeControlOptions: {
            mapTypeId: [google.maps.MapTypeId.ROADMAP, 'theGray']
        }
    };

    map = new google.maps.Map(document.getElementById("map-canvas"), mapOptions);
    var mapType = new google.maps.StyledMapType(styles, { name:"GrayScale" });    
    map.mapTypes.set('theGray', mapType);
    map.setMapTypeId('theGray');

    marker = new google.maps.Marker({
        position: location,
        map: map
    });
}
google.maps.event.addDomListener(window, 'load', initialize);
```
