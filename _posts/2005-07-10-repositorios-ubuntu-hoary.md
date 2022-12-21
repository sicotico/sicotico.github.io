---
layout: post
title: "Repositorios Ubuntu Hoary"
date: "2005-07-10"
categories: 
  - "sin-categoria"
---

Sicotico WeBlog v2.0

editar como root el fichero /etc/apt/sources.list y comentar todas las lines y pegar lso siguientes repositorios. Ademas hay un par de repositorios especiales , como son los de "marillat" y "NdissWrapper" este ultimo solo valido para x86 junto con el de KDE , mientras que el de marilals se explica como usarlo en otro post:

( # --> linea comentada )

##Main deb https://es.archive.ubuntu.com/ubuntu hoary main restricted deb-src https://es.archive.ubuntu.com/ubuntu hoary main restricted

##UPDATES deb https://es.archive.ubuntu.com/ubuntu hoary-updates main restricted deb-src https://es.archive.ubuntu.com/ubuntu hoary-updates main restricted

##Universe Multiverse España deb https://es.archive.ubuntu.com/ubuntu hoary universe multiverse deb-src https://es.archive.ubuntu.com/ubuntu hoary universe multiverse

##Security-Main deb https://security.ubuntu.com/ubuntu hoary-security main restricted deb-src https://security.ubuntu.com/ubuntu hoary-security main restricted

##Security-Universe deb https://security.ubuntu.com/ubuntu hoary-security universe deb-src https://security.ubuntu.com/ubuntu hoary-security universe

##Repositorios Bakports España FAST deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted deb ftp://ftp2.caliu.info/backports/ hoary-extras-staging main universe multiverse restricted deb ftp://ftp2.caliu.info/backports/ hoary-backports-staging main universe multiverse restricted

##Marillat deb ftp://ftp.nerim.net/debian-marillat stable main deb ftp://ftp.nerim.net/debian-marillat unstable main deb ftp://ftp.nerim.net/debian-marillat testing main

#Mirror aditel (se caen mucho estos repositorios) deb ftp://ftp.ubuntu-es.org/ubuntu hoary main restricted universe multiverse deb ftp://ftp.ubuntu-es.org/ubuntu hoary-security main restricted

\# KDE Ultima Version para x86

#deb ftp://ftp.rediris.es/mirror/kde/stable/3.4.1/kubuntu hoary-updates main

#NdissWrapper #deb https://ndiswrapper.sourceforge.net/debian ./

Espero que os sirva de algo ...............

Vínculo: [sources](https://www.blogger.com/sources)
