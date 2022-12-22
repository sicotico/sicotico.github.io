---
layout: post
title: "GPG y apt-get"
date: "2005-08-21"
categories: software
---

Solucionar errore de GPG en apt:

El error es el siguiente: GPG error: ftp://ftp.nerim.net stable Release: The following signatures could n't be verified because the public key is not available: NO\_PUBKEY 07DC563D1F41B 907 W: GPG error: ftp://ftp.nerim.net unstable Release: The following signatures cou ldn't be verified because the public key is not available: NO\_PUBKEY 07DC563D1F4 1B907 W: GPG error: ftp://ftp.nerim.net testing Release: The following signatures coul dn't be verified because the public key is not available: NO\_PUBKEY 07DC563D1F41 B907

solucion :

Paso 1. gpg --keyserver wwwkeys.eu.pgp.net --recv-keys "vuestra KEY"

Paso 2. gpg --armor --export "vuestra KEY" > marillat.sig

Paso 3. sudo apt-key add marillat.sig
