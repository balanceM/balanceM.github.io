---
id: 90
title: Sketchup Difference bewteen c api and ruby api
date: 2020-10-19T09:51:17+00:00
author: banana
layout: revision
guid: http://180.76.187.186/2020/10/19/88-revision-v1/
permalink: /2020/10/19/88-revision-v1/
---
The SketchUp Ruby API is embedded in the app itself for live action on the model. It is the main technique for implementing extensions (aka plugins).

The SketchUp C SDK is a separate library for creating standalone applications that can manipulate a SketchUp file outside of SketchUp itself and also for creating importers/exporters for other file formats