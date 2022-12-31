---
layout: single
title: "Modificar el CSS del Uploader Media WordPress +3.5"
date: "2013-05-22"
categories: dev
---

# Uploader Media Wordpress

    	.media-menu,.attachments-browser,.media-frame-menu,#wp\_editimgbtn,.media-router .active:after {
            display:none;
        }
		.media-modal{
			width:600px;
			max-height:400px;
			margin:auto;
		}
		.media-frame-title h1{
			font-family:"gill sans";
		}
		.media-frame-title,.media-frame-router,.media-frame-toolbar{
			left:0px;
			text-align:center;
		}
		.media-frame-content,.uploader-inline-content{
			margin-top:40px;
			position:static;
			text-align:center;
		}
		.media-toolbar,.media-toolbar-primary{
			position:static;
			width:128px;
			padding:0px;
			margin:auto;
			float:none;
			text-align:center;
		}
		media-button-insert{
			display:block;
		}
		.media-router{
			float:none;
			width:100px;
			margin:auto;
		}
		.media-router a{
			border-right:0px;
		}

Fuente: [Customize Media Manager](https://wordpress.org/support/topic/customize-media-manager?replies=5 "Customize Media Manager") https://wordpress.org/support/topic/customize-media-manager?replies=5
