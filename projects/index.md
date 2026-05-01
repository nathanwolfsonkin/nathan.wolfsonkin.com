---
title: Projects
nav:
  order: 2
  tooltip: Personal and Professional Projects
---

## Featured Projects

{% include list.html component="card" data="projects" filter="group == 'featured'" %}

## Academic Projects

{% include list.html component="card" data="projects" filter="group == 'personal'" %}

## Professional Work

During my undergraduate, I worked part-time for [CoreSWX](https://coreswx.com/), a Long Island–based company specializing in power solutions for the film industry. Below is a selection of products for which I designed the mechanical components and successfully brought to market.

{% include list.html component="card" data="projects" filter="group == 'coreswx'" %}

## More

{% include list.html component="card" data="projects" filter="!group" style="small" %}
