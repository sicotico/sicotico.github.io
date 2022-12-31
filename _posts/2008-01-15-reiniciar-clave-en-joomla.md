---
layout: single
title: "Reiniciar clave en Joomla"
date: "2008-01-15"
categories: dev
---

Para la gente que se le olvida la clave , como yo , o simplemente quiere un script para cambiarla.

Esta es la sql que necesita

``INSERT INTO `jos_users` VALUES (62, 'Administrator', 'admin', 'info@localhost.com', 'e10adc3949ba59abbe56e057f20f883e', 'Super Administrator', 0, 1, 25, '2006-01-16 20:28:43', '2006-01-16 20:30:48', '', '', 0, '');``

La password es "123456"
