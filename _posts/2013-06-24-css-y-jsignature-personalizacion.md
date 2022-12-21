---
layout: post
title: "CSS y jSignature, personalización"
date: "2013-06-24"
categories: dev
---

## CSS y jSignature

CSS y jSignature , con estas notas quiero recoger los códigos que he utilizados para personalizar este Script JS , CSS y jSignature Proyecto original: [https://willowsystems.github.io/jSignature/#/about/](https://willowsystems.github.io/jSignature/#/about/ "jSignature") GitHub: [https://github.com/brinley/jSignature](https://github.com/brinley/jSignature "Github - jSignature") Ejemplos de de JSignature [https://www.unbolt.net/jSignature/](https://www.unbolt.net/jSignature/ "jSignature Ejemplos") Integración:

Mostrar firma

CSS:

div {
	margin-top:1em;
	margin-bottom:1em;
}
input {
	padding: .5em;
	margin: .5em;
}
select {
	padding: .5em;
	margin: .5em;
}

#signatureparent {
	color:darkblue;
	max-width:350px;
	padding:20px;
	/\*margin-left: 15em;
	position: relative;
	float:right;\*/
	padding-right:30px;

}
#content{
	display: inline-block;
}

#undo {
	position: relative  !important;
}
/\*This is the div within which the signature canvas is fitted\*/
#signature {
	border: 2px dotted black;
	background-color:lightgrey;
}

/\* Drawing the 'gripper' for touch-enabled devices \*/ 
html.touch #content {
	float:left;
	width:92%;
}
html.touch #scrollgrabber {
	float:right;
	width:4%;
	margin-right:2%;
	background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAAFCAAAAACh79lDAAAAAXNSR0IArs4c6QAAABJJREFUCB1jmMmQxjCT4T/DfwAPLgOXlrt3IwAAAABJRU5ErkJggg==)
}
html.borderradius #scrollgrabber {
	border-radius: 1em;
}
