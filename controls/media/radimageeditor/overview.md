---
title: Overview
page_title: Overview
description: Overview
slug: radimageeditor-overview
tags: overview
published: True
position: 0
---

# Overview



## 

{% if site.site_name == 'Silverlight' %}![](images/RadImageEditor_Overview_sl.png){% endif %}{% if site.site_name == 'WPF' %}![](images/RadImageEditor_Overview_wpf.png){% endif %}

__RadImageEditor__ is a control that can be used to preview and edit images in different file formats. It is meant to be used as a stand-alone control, but has also been integrated in __RadRichTextBox__.
         

The operations it can perform on an image are: 

* Crop 

* Canvas Resize

* Round Corners (including border)

* Hue Shift

* Saturation

* Contrast (and brightness) 

* Sharpen and Blur

* Rotating and Flipping

* Typing

* Drawing

* Panning

The image formats it supports are: 

For import: 

* JPEG; 

* PNG; 

* BMP{% if site.site_name == 'Silverlight' %}.{%endif%}{% if site.site_name == 'WPF' %};

* TIFF;

* GIF;

* ICO.
{%endif%}

For export: 

{% if site.site_name == 'WPF' %}
* JPEG;
{%endif%}

* PNG; 

* BMP{% if site.site_name == 'Silverlight' %}.{%endif%}{% if site.site_name == 'WPF' %};

* TIFF;

* GIF.
{%endif%}

__RadImageEditor__ is highly extensible, so you can implement and utilize additional image editing tools, as well as import and export in other formats. 
