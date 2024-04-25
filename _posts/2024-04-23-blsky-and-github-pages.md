---
title: Bluesky-handle mit gh-pages
subtitle: Eigene domain als handle nutzen
cover-img: /assets/img/bluesky-handle-example.jpeg
share-img: /assets/img/it-ferret-icon.jpg
tags: [blsky, bluesky, gh-pages]
---

# Kleines HowTo  

Falls euch eine eigene Domain gehört,könnt ihr diese als bluesky-handle verwenden, z.B. **@it-frettchen.de**. Hier wird beschrieben wie ihr ein Github-Pages-Repo umbaut, falls eure Webseite bereits dort liegt.

## Voraussetzungen  
- Besitz einer Domain
- konfiguriertes Github-Pages-Repo
- Bluesky-Account
- CMS-Kenntnisse oder
- Static-Site-Generator wie `Beautiful Jekyll`

## Vorbereitungen in Bluesky  
Unter „Einstellungen“, „Handle ändern“
könnt ihr eine Unterseite öffnen.
Dort klickt ihr auf „Ich habe meine eigene Domain“.
Dann seht ihr die Konfig-Seite, hierbei ist **No DNS Panel** aktiviert, da ich nur das Github-Repo anpassen möchte:

![Handle ändern](/assets/img/handle-config.jpeg){: .mx-auto.d-block :}

Hier im Beispiel wird die Domain
`verkehrswen.de` verwendet, diese wäre später der Bluesky-Handle *@verkehrswen.de*.  

## Im Git-Repo
Den Identifier ,`did:plc:blablubb123`, braucht ihr, also kopiert euch den String und legt gleich eine Datei an unter:

Dateiname: `atproto-did`  
Dateiendung: *keine*

Mit diesem Inhalt:

```
—
layout: none
permalink: .well-known/atproto-did
—
did:plc:blablubb123blablubb
```

Falls ihr Direkt-Zugriff auf euren Webspace habt, könnt ihr einfach eine Datei dort ablegen _(unter .well-known/atproto-did)_. Aber das geht hier nicht, da es eine Github-Pages-Seite ist (alles liegt im Repo).


### Wozu ist diese Datei?

Wir sollen im Webspace folgende Datei hinterlegen, die von Bluesky abgefragt wird, wenn ihr auf *Verify Text File* klickt:

```
https://verkehrswen.de/.well-known/atproto-did
```

Diese Seite wird als versteckte Unterseite angelegt, da wir `layout: none` angegeben haben.
Der `permalink` verweist auf den Ort,
an dem Bluesky die Datei erwartet, um sicher zu stellen, dass es eure Domain ist.

Zum Schluss committed ihr eure Github-Repo-Änderungen und wartet, bis der Build von Jekyll fertig ist.

## Worauf wird nicht eingegangen
- Was ist Markdown?
- Was ist Beautiful Jekyll?
- Wie lege ich einen Bluesky-Account an?
- Was ist ein DNS-Panel?
- Was sind Github-Pages?
