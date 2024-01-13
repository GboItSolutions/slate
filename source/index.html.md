---
title: OpenReza API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - csharp
  - javascript

toc_footers:
  - <a href='#'>S'inscrire pour avoir une clé d'Api</a>

includes:
  - booking
  - client
  - events
  - eventLog
  - form
  - media
  - place
  - product
  - question
  - room
  - waitinglist
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation de l'API OpenReza
---

# Introduction

Bienvenue sur l'api OpenReza !
<p>Gérer votre système de réservation, vos clients, vos élèves, vos entraînements, vos abonnements ...</p>

# Authentication

OpenReza utilise des clés pour accéder aux APIs. Connectez-vous ou créer un compte sur OpenReza.com afin d'obtenir une clé.

L'API OpenReza attend qu'un clé soit incluse dans chacune des requêtes dans l'en-tête comme ceci :
<p>`x-api-key: <YOUR_API_KEY>`</p>

<asIde class="notice">
Vous devez remplacer <code><YOUR_API_KEY></code> par votre clé personnelle.
</asIde>
