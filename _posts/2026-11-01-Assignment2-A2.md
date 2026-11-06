---
layout: single
title: "Assignment 2: Manual Geocoding vs. Automated Geocoding"
date: 2026-11-01
---

## Manual Geocoding vs. Automated Geocoding

## Background and Expectations


## Interactive Map

<div style="width:100%; height:70vh;">
  <iframe
    src="{{ '/assets/Maps/1_The_Road_Map.html' | relative_url }}"
    style="width:100%; height:100%; border:0;"
    loading="lazy">
  </iframe>
</div>

map 1 obseractions

<div style="width:100%; height:70vh;">
  <iframe
    src="{{ '/assets/Maps/1_The_Road_Map.html' | relative_url }}"
    style="width:100%; height:100%; border:0;"
    loading="lazy"
    onload="
      setTimeout(() => {
        const widget = this.contentWindow.HTMLWidgets.find('.leaflet.html-widget');
        const map = widget.getMap();

        map.fitBounds([
          [29.5, -91.0],
          [38.5, -75.5]
        ], {animate: false});

        map.dragging.disable();
        map.scrollWheelZoom.disable();
        map.touchZoom.disable();
        map.doubleClickZoom.disable();
        map.boxZoom.disable();
        map.keyboard.disable();

        if (map.zoomControl) {
          map.removeControl(map.zoomControl);
        }
      }, 500);
    ">
  </iframe>
</div>

