---
layout: default
title: Draw a Map base styles
modal-id: dam-styles
category: invisible
---
These styles can live in the custom CSS in the agency admin, or indeed in a LCSS file within the theme itself.

{% highlight css %}
/* draw a map */

div.leaflet-left {
    display: block;
}
.mappydelete {
	position: relative;
	top: -15px;
	left: 0%;
	width: 100%;
	height: 50px;
	display: none;
	background: rgba(84, 84, 84, 0.9);
	text-align: left;
	padding-left: 30px;
	padding-top: 15px;
	line-height: 50px;
	border-radius: 4px;
	box-shadow: 0 1px 7px rgba(0, 0, 0, 0.65);
	color: white;
	font-family:Arial, Helvetica, sans-serif;
}
.mappyedit {
	position: relative;
	top: -15px;
	left: 0%;
	width: 100%;
	height: 50px;
	display: none;
	background: rgba(84, 84, 84, 0.9);
	text-align: left;
	padding-left: 30px;
	padding-top: 15px;
	line-height: 50px;
	border-radius: 4px;
	box-shadow: 0 1px 7px rgba(0, 0, 0, 0.65);
	color: white;
	font-family:Arial, Helvetica, sans-serif;
}
.mappy {
	position: relative;
	top: -15px;
	left: 0%;
	width: 100%;
	height: 50px;
	display: none;
	background: rgba(84, 84, 84, 0.9);
	text-align: left;
	padding-left: 30px;
	padding-top: 15px;
	line-height: 50px;
	border-radius: 4px;
	box-shadow: 0 1px 7px rgba(0, 0, 0, 0.65);
	color: white;
	font-family:Arial, Helvetica, sans-serif;
}
.leaflet-top {
	top: 48px;
}
.leaflet-control-title {
    position: relative;
}
.leaflet-touch .leaflet-control-title-interior {
    background-color: #ffffff;
    background-position: -182px 0;
    background-repeat: no-repeat;
    border-bottom-left-radius: 0 !important;
    border-bottom-right-radius: 0 !important;
    border-top-left-radius: 4px;
    border-top-right-radius: 4px;
    cursor: auto;
    display: block;
    font-size: 12px;
    height: 20px;
    line-height: 20px;
    margin-top: 30px;
    padding: 3px;
    position: relative;
    text-align: center;
    vertical-align: middle;
    width: 99px;
}
.leaflet-control-title-interior {
    background-color: #ffffff;
    background-position: -182px 0;
    background-repeat: no-repeat;
    border-radius: 4px 4px 0 0;
    cursor: auto;
    display: block;
    font-size: 12px;
    height: 20px;
    line-height: 20px;
    padding: 3px;
    position: relative;
    text-align: center;
    vertical-align: middle;
    width: 99px;
}
.leaflet-help-banner {
    background: none repeat scroll 0 0 rgba(84, 84, 84, 0.9);
    border-radius: 4px;
    box-shadow: 0 1px 7px rgba(0, 0, 0, 0.65);
    color: white;
    display: none;
    font-family: Arial,Helvetica,sans-serif;
    height: 50px;
    left: 0;
    line-height: 50px;
    padding-left: 150px;
    position: fixed;
    text-align: left;
    top: 0;
    vertical-align: middle;
    width: 100%;
}
.leaflet-draw-draw-freehand-banner {
    background: none repeat scroll 0 0 rgba(84, 84, 84, 0.9);
    border-radius: 4px;
    box-shadow: 0 1px 7px rgba(0, 0, 0, 0.65);
    color: white;
    display: none;
    font-family: Arial,Helvetica,sans-serif;
    height: 50px;
    left: 0;
    line-height: 50px;
    padding-left: 150px;
    position: fixed;
    text-align: left;
    top: 0;
    vertical-align: middle;
    width: 100%;
}
.leaflet-draw-edit-edit-banner {
    background: none repeat scroll 0 0 rgba(84, 84, 84, 0.9);
    border-radius: 4px;
    box-shadow: 0 1px 7px rgba(0, 0, 0, 0.65);
    color: white;
    display: none;
    font-family: Arial,Helvetica,sans-serif;
    height: 50px;
    left: 0;
    line-height: 50px;
    padding-left: 150px;
    position: fixed;
    text-align: left;
    top: 0;
    vertical-align: middle;
    width: 100%;
}
.leaflet-control-remove-all-interior a {
    background-color: #ffffff;
    background-image: url("/assets/binsprite.png");
    background-position: -182px 0;
    background-repeat: no-repeat;
    border-radius: 0 0 4px 4px;
    cursor: auto;
    display: block;
    height: 20px;
    padding: 3px 3px 3px 30px;
    position: relative;
    text-align: left;
    top: -20px;
    width: 72px;
}
.leaflet-retina .leaflet-control-remove-all-interior a {
    background-image: url("binsprite-2x.png") !important;
    background-position: -182px 0;
    height: 20px;
    width: 72px;
}
.leaflet-control-remove-all-interior {
    background-color: #ffffff;
    background-image: url("/assets/binsprite.png");
    background-position: -182px 0;
    background-repeat: no-repeat;
    border-radius: 0 0 4px 4px;
    cursor: pointer;
    display: block;
    height: 20px;
    padding: 3px 3px 3px 30px;
    position: relative;
    text-align: left;
    top: -20px;
    width: 72px;
}
.leaflet-retina .leaflet-control-remove-all-interior {
    background-image: url("/assets/binsprite-2x.png") !important;
    background-size: 300px 30px !important;
    height: 20px;
    width: 72px;
}
.leaflet-disabled {
    color: #bbb;
}
.leaflet-disabled:hover {
    background-color: #ffffff !important;
    color: #f4f4f4;
    cursor: pointer;
}
.leaflet-control-remove-all-interior:hover {
    background-color: #f4f4f4;
}
.leaflet-draw-section {
    position: relative;
}
.leaflet-draw-toolbar {
    margin-top: 0;
}
.leaflet-draw-toolbar-top {
    margin-top: 0;
    position: relative;
}
.leaflet-draw-toolbar-notop a:first-child {
    border-top-right-radius: 0;
}
.leaflet-draw-toolbar-nobottom a:last-child {
    border-bottom-right-radius: 4px;
}
.leaflet-draw-toolbar a {
    background-image: url("/assets/spritesheet.png");
    background-repeat: no-repeat;
}
.leaflet-retina .leaflet-draw-draw-freehand {
    background-image: url("/assetsfreehand-2x.png");
    background-position: 8px center !important;
    background-repeat: no-repeat;
    background-size: 15px 15px !important;
}
.leaflet-retina .leaflet-draw-toolbar .leaflet-draw-edit-edit.leaflet-disabled {
    background-image: url("/assetsedit-2x.png");
    background-size: 300px 30px !important;
    width: 105px;
}
.leaflet-retina .leaflet-draw-toolbar .leaflet-draw-edit-edit {
    background-image: url("/assets/edit-2x.png");
    background-size: 300px 30px !important;
    width: 105px;
}
.leaflet-draw-toolbar .leaflet-draw-draw-freehand.leaflet-disabled {
    background-image: url("/assets/spritesheet-2x.png");
}
.leaflet-draw a {
    display: block;
    position: relative;
    text-align: center;
    text-decoration: none;
    top: -10px;
}
.leaflet-draw-actions {
    display: none;
    left: 26px;
    list-style: none outside none;
    margin-left: 75px;
    padding: 0;
    position: absolute;
    top: 0;
    white-space: nowrap;
}
.leaflet-right .leaflet-draw-actions {
    left: auto;
    right: 26px;
}
.leaflet-draw-actions li {
    display: inline-block;
}
.leaflet-draw-actions li:first-child a {
    border-left: medium none;
    color: #ffffff;
    top: 0;
}
.leaflet-draw-edit-edit .leaflet-draw-actions li:first-child a {
    display: inline-block;
}
.leaflet-draw-actions li:last-child a {
    border-radius: 0 4px 4px 0;
    color: #ffffff;
    display: inline-block;
    top: 0;
}
.leaflet-right .leaflet-draw-actions li:last-child a {
    border-radius: 0;
    color: #ffffff;
}
.leaflet-right .leaflet-draw-actions li:first-child a {
    border-radius: 4px 0 0 4px;
}
.leaflet-draw-actions a {
    background-color: #919187;
    border-left: 1px solid #aaa;
    color: #fff;
    font: 11px/28px "Helvetica Neue",Arial,Helvetica,sans-serif;
    height: 28px;
    left: 4px;
    padding-left: 10px;
    padding-right: 10px;
    position: relative;
    text-decoration: none;
    z-index: 50;
}
.leaflet-draw-actions-bottom {
    margin-top: 0;
}
.leaflet-draw-actions-top {
    margin-top: 1px;
}
.leaflet-draw-actions-top a, .leaflet-draw-actions-bottom a {
    height: 27px;
    line-height: 27px;
}
.leaflet-draw-actions a:hover {
    background-color: #a0a098;
}
.leaflet-draw-actions-top.leaflet-draw-actions-bottom a {
    height: 26px;
    line-height: 26px;
}
.leaflet-draw-toolbar .leaflet-draw-draw-polyline {
    background-position: -2px -2px;
}
.leaflet-draw-toolbar .leaflet-draw-draw-polygon {
    background-position: -31px -2px;
}
.leaflet-draw-toolbar .leaflet-draw-draw-rectangle {
    background-position: -62px -2px;
}
.leaflet-draw-toolbar .leaflet-draw-draw-circle {
    background-position: -92px -2px;
}
.leaflet-draw-toolbar .leaflet-draw-draw-marker {
    background-position: -122px -2px;
}
.leaflet-draw-toolbar .leaflet-draw-draw-freehand {
    background-position: -267px -2px;
    border-radius: 0 !important;
    padding-left: 30px;
    position: relative;
    text-align: left;
    width: 75px !important;
}
.leaflet-draw-toolbar .leaflet-draw-draw-freehand:hover {
    background-position: -267px -2px;
}
.leaflet-draw-toolbar .leaflet-draw-edit-edit {
    background-image: url("/assets/edit.png");
    background-position: -152px -2px;
    margin-top: 5px;
    padding-left: 30px;
    position: relative;
    text-align: left;
    width: 75px !important;
}
.leaflet-draw-edit-edit {
    border-radius: 0 !important;
    position: absolute;
    top: -10px !important;
}
.leaflet-draw-toolbar .leaflet-draw-edit-remove {
    background-image: url("/assets/binsprite.png");
    background-position: -184px 0;
    padding-left: 30px;
    position: relative;
    text-align: left;
}
.leaflet-retina .leaflet-draw-edit-remove {
    background-image: url("/assets/binsprite-2x.png") !important;
    background-position: -182px 0;
    background-size: 300px 30px !important;
    border: medium none;
    box-shadow: none;
    margin-top: -5px;
}
.leaflet-touch .leaflet-draw-edit-remove {
    margin-top: -5px;
}
.leaflet-delete-disabled:hover {
    background-color: #fff;
}
.leaflet-draw-toolbar .leaflet-draw-edit-edit.leaflet-disabled {
    background-image: url("/assets/edit.png");
    background-position: -152px -2px;
    color: #bbb;
    position: relative;
}
.leaflet-retina .leaflet-draw-toolbar .leaflet-draw-edit-edit.leaflet-disabled .leaflet-retina {
    background-image: url("/assets/edit- f f2x.png");
    background-position: -152px -2px;
    color: #f4f4f4;
    position: relative;
}
.leaflet-draw-toolbar .leaflet-draw-edit-edit.leaflet-disabled:hover {
    background-color: #fff;
}
.leaflet-draw-toolbar .leaflet-draw-edit-edit:hover {
    background-color: #f4f4f4;
}
.leaflet-draw-toolbar .leaflet-draw-edit-remove.leaflet-disabled {
    background-image: url("/assets/binsprite.png");
    background-position: -184px 0;
}
.leaflet-mouse-marker {
    background-color: #fff;
    cursor: crosshair;
}
.leaflet-draw-tooltip {
    background: none repeat scroll 0 0 rgba(0, 0, 0, 0.5);
    border: 1px solid transparent;
    border-radius: 4px;
    color: #fff;
    display: none;
    font: 12px/18px "Helvetica Neue",Arial,Helvetica,sans-serif;
    margin-left: 20px;
    margin-top: -21px;
    padding: 4px 8px;
    position: relative;
    visibility: hidden;
    white-space: nowrap;
    z-index: 5000;
}
.leaflet-draw-tooltip:before {
    border-bottom: 6px solid transparent;
    border-right: 6px solid rgba(0, 0, 0, 0.5);
    border-top: 6px solid transparent;
    content: "";
    left: -7px;
    position: absolute;
}
.leaflet-error-draw-tooltip {
    background-color: #f2dede;
    border: 1px solid #e6b6bd;
    color: #b94a48;
}
.leaflet-error-draw-tooltip:before {
    border-right-color: #e6b6bd;
}
.leaflet-draw-tooltip-single {
    margin-top: -12px;
}
.leaflet-draw-tooltip-subtext {
    color: #f8d5e4;
}
.leaflet-draw-guide-dash {
    font-size: 1%;
    height: 5px;
    opacity: 0.6;
    position: absolute;
    width: 5px;
}
.leaflet-edit-marker-selected {
    background: none repeat scroll 0 0 rgba(254, 87, 161, 0.1);
    border: 4px dashed rgba(254, 87, 161, 0.6);
    border-radius: 4px;
}
.leaflet-edit-move {
    cursor: move;
}
.leaflet-edit-resize {
    cursor: pointer;
}
.leaflet-oldie .leaflet-draw-toolbar {
    border: 3px solid #999;
}
.leaflet-oldie .leaflet-draw-toolbar a {
    background-color: #eee;
}
.leaflet-oldie .leaflet-draw-toolbar a:hover {
    background-color: #fff;
}
.leaflet-oldie .leaflet-draw-actions {
    left: 32px;
    margin-top: 3px;
}
.leaflet-oldie .leaflet-draw-actions li {
    display: inline;
}
.leaflet-oldie .leaflet-edit-marker-selected {
    border: 4px dashed #fe93c2;
}
.leaflet-oldie .leaflet-draw-actions a {
    background-color: #999;
}
.leaflet-oldie .leaflet-draw-actions a:hover {
    background-color: #a5a5a5;
}
.leaflet-oldie .leaflet-draw-actions-top a {
    margin-top: 1px;
}
.leaflet-oldie .leaflet-draw-actions-bottom a {
    height: 28px;
    line-height: 28px;
}
.leaflet-oldie .leaflet-draw-actions-top.leaflet-draw-actions-bottom a {
    height: 27px;
    line-height: 27px;
}

/* End draw a map */
{% endhighlight %}