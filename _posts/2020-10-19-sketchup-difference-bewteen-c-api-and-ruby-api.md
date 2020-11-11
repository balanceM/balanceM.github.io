---
id: 88
title: Sketchup Difference bewteen c api and ruby api
date: 2020-10-19T09:51:06+00:00
author: banana
layout: post
guid: http://180.76.187.186/?p=88
permalink: /2020/10/19/sketchup-difference-bewteen-c-api-and-ruby-api/
categories:
  - Sketchup
---
The SketchUp Ruby API is embedded in the app itself for live action on the model. It is the main technique for implementing extensions (aka plugins).

The SketchUp C SDK is a separate library for creating standalone applications that can manipulate a SketchUp file outside of SketchUp itself and also for creating importers/exporters for other file formats