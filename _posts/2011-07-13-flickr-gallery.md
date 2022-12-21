---
layout: post
title: "Flickr Gallery"
date: "2011-07-13"
categories: software
---

Siempre se me olvidan los shortcodes de este plugin así que me los pongo cerquita para que no se me olviden.

Shortcode Examples

- `[.flickr-gallery]` Crea una galería genérica.

`[flickr-gallery]`

- `[.flickr]https://flickr.com/photos/dancoulter/2619594365/[/flickr]` Al utilizar directamente la url de la imagen cuando ampliamos nos transfiere a flickr

`[flickr]https://flickr.com/photos/dancoulter/2619594365/[/flickr]`

##### Additional Options

- `[.flickr-gallery mode="photoset" photoset="72157605870230826"]` Muestra las fotos del "álbum" asociada al id del parámetro photoset. Este se consigue accediendo al álbum y en la url  entre "sets" y "detail" lo tienes  `/sets/**72157627137371055**/detail/`

`[flickr-gallery mode="photoset" photoset="72157605870230826"]`

- `[.flickr-gallery mode="tag" tags="foo" tag_mode="all"]`  Shows photos from your photostream with the specified tags (comma separated). If you leave off the tag\_mode option, it defaults to “any”.

`[flickr-gallery mode="tag" tags="foo" tag_mode="all"]`

- `[.flickr-gallery mode="recent"]` Shows recent photos from your photostream

`[flickr-gallery mode="recent"]`

- `[.flickr-gallery mode="interesting"]` Shows interesting photos from your photostream

`[flickr-gallery mode="interesting"]`

- `[.flickr-gallery mode="search" tags="foo" group_id="46862018@N00"]` The search mode supports any arbitrary search using the options listed here: [https://www.flickr.com/services/api/flickr.photos.search.html](https://www.flickr.com/services/api/flickr.photos.search.html)

`[flickr-gallery mode="search" tags="foo" group_id="46862018@N00"]`

- `[.flickr size="small" float="left"]https://www.flickr.com/photos/dancoulter/2619594365/[/flickr]` Sets the size of the inserted image to “small” (defaults to “medium”) and makes the next paragraph of text wrap around to the right of the image (you can specify “right” for the float parameter as well, which defaults to “none”)

`[flickr size="small" float="left"]https://www.flickr.com/photos/dancoulter/2619594365/[/flickr]`

 

 

- `[.flickr height="300" width="400"]https://www.flickr.com/photos/dancoulter/2422361554/[/flickr]` This one is a video. It’ll automatically embed the flash movie for you. If you want to change its size, you can use the width and height options.

`[flickr height="300" width="400"]https://www.flickr.com/photos/dancoulter/2422361554/[/flickr]`

Fuentes:

[Wordpress Plugins](https://wordpress.org/extend/plugins/flickr-gallery/other_notes/ "Flickr Gallery")

[Proyecto original](https://co.deme.me/projects/flickr-gallery/ "Flickr Gallery")
