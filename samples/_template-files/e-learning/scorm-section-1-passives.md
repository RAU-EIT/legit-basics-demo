---
title: SCORM Passive Objects Demo
subtitle: A pandoc parsing, vscode preview and weasyprint pdf'ing test
css: ../../../style-rau-base/rau-scorm.css
docType: scorm
chunk:
  classification: Public
  revisionDate: "Apr 2026"
  id: SCT001
---

## SCORM / E-Learning Passive Objects Test

This document demonstrates the syntax and functionality of the interactive objects that can be built into SCORM content.

These objects can be easily inserted into markdown using the vscode 'code snippets' functionality: **Ctrl+Space** brings up the snippet selector, and from there you can type 'rau' to see a list of the objects available.  

## The Accordion Object

The accordion object allows for blocks of content to be presented in collapsed (but expandable) containers. In print, this object shows all containers expanded, and tries to not page break in the middle of a block if possible.

Accordion objects are wrapped up in a fenced div with the class **rau-accordion**. Each collapsible section is in a **tab** div.

The first element of each tab should be an object (paragraph or header) that can be used as the title. If the first thing in the **tab** is soamething else, like an image or link, then the **tab**'s title will be set to 'Tab with no Title'.

Here's the markdown for the object.

::: rau-accordion

::: tab

### Section 1

Section 1 Content

![logo](media/ra-logo.png)

:::

::: tab

### Section 2, going farther

#### Sub Header

* Do a thing with this code, then do another thing.
* We can do all the things.
* More things more of the time.

#### Another Header

Can this actually work?!?

:::

::: tab

### Section 3, wall of text

This is the thing that we have to do. We have to do a thing.
There are a lot of things that we *could* do, but this is
the thing that we **HAVE** to do. Blah blah blah, green eggs
and ham, la li lu le lo.

:::

:::

::: rau-contentdivider
:::

## Tabbed Sections

Tabbed sections are like the accordion object type, but they break up the content horizontally instead of vertically. 

::: rau-tabbed-sections

::: tab

### Section 1 Summary

Section 1 Details

:::

::: tab

### Section 2 Summary

Section 2 Details

:::

::: tab

### Section 3 Summary

Section 3 Details

:::

:::

::: rau-contentdivider
:::



## Process Steps Object

The process steps object shows a set of information or steps. Note that this view looks different based on the docType. Change the docType option in this document's front matter to 'lab' and re-run the preview to see the output change to the 'Practice' section of a lab document!

::: rau-steps

::: tab

### Introduction

Write an intro for what these steps are going to do.

This introduction tab is optional and can be deleted.

![two people walking](media/twb-two-walkers.jpg)

:::

::: tab

### Step 1 Title

Step Details go here. This can contain many paragraphs, images or tables. Go wild!

:::

::: tab

### Step 2 Title

Step Details go here. This can contain many paragraphs, images or tables. Go wild!

:::

::: tab

### Step 3 Title

Step Details go here. This can contain many paragraphs, images or tables. Go wild!

:::

::: tab

### Summary

This is a recap of the things that were covered in this Steps object. This summary tab is optional and can be deleted.

:::

:::

::: rau-contentdivider
:::

## Alert objects

There are various alert objects that can be used to call out certain information or summarize key points. 

::: {.rau-alert .attention}

For further information

* [link text](url)

* [link text](url)

:::

::: rau-contentdivider
:::

## Hero banners can be used as well to draw attention to a major concept

::: {.hero}

![this is the bg image, if provided](media/straight-vs-crossover.png)

## Title

::: hero-subtitle

[Subtitle or List Text]

:::

:::

::: rau-contentdivider
:::

## Audio Files

Audio content can be used as well! If you have a transcript file, that will show up as subtitles with the audio player. 

~[Arthur the Rat, from https://iandevlin.com/html5/webvtt/audio/](media/arth_ire8.mp3){transcript='media/arth_ire8.vtt'}

::: rau-contentdivider
:::

## Video Files

Video content uses a similar format / player as audio files. Video files can have a transcript as well.

%[alt text](media/SampleVideo_1280x720_1mb.mp4){transcript='media/video-sample.vtt'}

::: rau-contentdivider
:::

