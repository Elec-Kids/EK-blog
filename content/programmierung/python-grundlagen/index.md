---
title: "Python Grundlagen"
subtitle: "Lernpfad, Übersicht und passende Artikel"
date: 2026-03-31
draft: false
author: "ElecKids"
description: "Eine Übersichtsseite für den Einstieg in Python mit Lernpfad, geplanter Tutorial-Reihe und passenden Artikeln."
summary: "Hier findest du den Einstieg in Python bei ElecKids: eine Übersicht kommender Tutorials, ein visueller Lernpfad und passende Artikel zum Thema Programmierung."
---

Python ist ein guter Einstieg ins Programmieren, weil man mit wenig Syntax schnell sichtbare Ergebnisse bekommt. Genau darum geht es in diesem Bereich: erst die Grundlagen verstehen, dann Schritt für Schritt kleine Programme schreiben und später den Übergang zu MicroPython und Mikrocontrollern schaffen.

## Was dich hier erwartet

Auf dieser Seite findest du den Einstieg in `Python Grundlagen` an einer Stelle. Dazu gehören:

* vorhandene Einsteigerartikel
* eine Übersicht der nächsten Tutorials
* ein klarer Lernpfad vom ersten Python-Code bis zu kleinen Anwendungen

## Übersicht geplanter Tutorials

| Tutorial | Ziel | Schwierigkeit | Status |
| --- | --- | --- | --- |
| <a href="{{< relref "posts/python-einfuehrung" >}}">Python kennenlernen</a> | Erste Befehle ausprobieren und verstehen, wie ein einfaches Programm aufgebaut ist | leicht | veröffentlicht |
| <a href="{{< relref "programmierung/variablen-zahlen-und-text" >}}">Variablen, Zahlen und Text</a> | Werte speichern, verändern und ausgeben | leicht | veröffentlicht |
| <a href="{{< relref "programmierung/if-und-else" >}}">if und else</a> | Entscheidungen im Code treffen | leicht bis mittel | veröffentlicht |
| <a href="{{< relref "programmierung/schleifen-mit-for-und-while" >}}">Schleifen mit for und while</a> | Wiederholungen sauber aufbauen | mittel | veröffentlicht |
| <a href="{{< relref "programmierung/listen-und-kleine-datenstrukturen" >}}">Listen und kleine Datenstrukturen</a> | Mehrere Werte gemeinsam verarbeiten | mittel | veröffentlicht |
| <a href="{{< relref "programmierung/funktionen" >}}">Funktionen</a> | Größere Programme in verständliche Teile aufteilen | mittel | veröffentlicht |
| <a href="{{< relref "programmierung/python-auf-dem-mikrocontroller" >}}">Python auf dem Mikrocontroller</a> | Den Übergang von Python zu MicroPython verstehen | mittel | veröffentlicht |

## Lernpfad als Blockdiagramm

Das Diagramm zeigt dir die Reihenfolge, in der du die Themen am besten angehen kannst.

{{< mermaid >}}
flowchart LR
    A[Python kennenlernen] --> B[Variablen und Text]
    B --> C[if und else]
    C --> D[Schleifen]
    D --> E[Listen]
    E --> F[Funktionen]
    F --> G[MicroPython auf dem Mikrocontroller]
{{< /mermaid >}}

## Artikel zum Thema Programmierung

Hier findest du passende Beiträge, wenn du tiefer in das Thema einsteigen oder einzelne Punkte noch einmal in Ruhe nachlesen willst.

{{< topic_articles refs="posts/python-einfuehrung, posts/was-bringt-dir-das, posts/thonny-installation-manual, posts/was-ist-ein-mikrokontroller" >}}
