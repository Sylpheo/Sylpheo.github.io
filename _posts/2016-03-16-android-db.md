---
layout: post
title: Accéder à la base de données sqlite sur un périphérique Android via adb
modified:
categories: blog
excerpt:
author: marion_aubard
tags: [adb, android, sqlite]
image:
  feature:
date: 2016-03-16T16:46:01+01:00
---

- Localiser **adb**. Soit il est installé et peut-être accédé directement dans le terminal via **adb** ou utilisé de la manière suivante :
    `cd  /Users/marion/Library/Android/sdk/platform-tools`
- Utiliser la commande `shell` : 
	`./adb shell` 
		ou
	`adb shell`
- Ouvrir `sqlite3` sur la base de données souhaitée. Pour savoir laquelle utiliser, ouvrir le **ADM (Android Device Monitor)** et rechercher le chemin de la base de données. Cela donne un résultat de la forme : 
	`sqlite3 /data/data/com.marion.whiteladder/databases/Area.db`
- Utiliser ensuite des requêtes SQL pour alimenter la base ou récupérer ses informations.
