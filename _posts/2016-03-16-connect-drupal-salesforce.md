---
layout: post
title: Connecter Drupal et Salesforce
modified:
categories: blog
excerpt:
tags: [connector, drupal, salesforce]
author: marion_aubard
image:
  feature:
date: 2016-03-16T16:50:42+01:00
---

# Configuration préalable de Drupal

Il est possible de synchroniser les objets entre Salesforce et Drupal.
Activer `Update manager` dans les modules.
Pour cela sur Drupal, dans Importer un module, ajouter les modules suivants :

- [Salesforce Suite](https://ftp.drupal.org/files/projects/salesforce-7.x-3.1.tar.gz)
- [Ctools](https://ftp.drupal.org/files/projects/ctools-7.x-1.9.tar.gz)
- [Entity](https://ftp.drupal.org/files/projects/entity-7.x-1.6.tar.gz)
- [Libraries](https://ftp.drupal.org/files/projects/libraries-7.x-2.2.tar.gz)
- [Views](https://ftp.drupal.org/files/projects/views-7.x-3.13.tar.gz)

Il suffit ensuite de connecter les deux services entre eux.

# Création d'une application connectée sur Salesforce

Sur Salesforce, créer une application connectée :

- `Setup > Create > App > New Connected App`
- `Enable OAuth settings`
- `Callback URL` : l’URL de Drupal (exemple : http://localhost/drupal/salesforce/oauth_callback)
- `Selected OAuth scopes`

    - `Perform requests on your behalf at any time`
    - `Access and manage your data`
    - `Access your basic information`

# Configurer Salesforce sur Drupal

Sur Drupal, après avoir installé les modules, configurer Salesforce

- `Modules > Salesforce API > Configurer > Authorize`
- Ajouter les consumer et client keys de l’application connectée précédemment créée.
- Dans `Advanced`, mettre l’URL de connexion (https://login.salesforce.com ou portail de la communauté)
- Cliquer sur `Authorize`

# Interfacer le modèle de données Drupal avec celui de Salesforce

Sur Drupal, créer ensuite un mapping entre objet Salesforce et Drupal :

- `Modules > Salesforce Mapping > Configurer > add salesforce mapping`
- Choisir une entité Drupal et un objet Salesforce
- Ajouter un mapping entre un champ de l’objet Drupal, et un de Salesforce. Attention, côté Salesforce, il faut que ce soit un external id.
- Choisir la méthode de synchronisation