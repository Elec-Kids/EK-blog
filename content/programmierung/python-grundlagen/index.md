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
| Python kennenlernen | Erste Befehle ausprobieren und verstehen, wie ein einfaches Programm aufgebaut ist | leicht | veröffentlicht |
| Variablen, Zahlen und Text | Werte speichern, verändern und ausgeben | leicht | geplant |
| if und else | Entscheidungen im Code treffen | leicht bis mittel | geplant |
| Schleifen mit for und while | Wiederholungen sauber aufbauen | mittel | geplant |
| Listen und kleine Datenstrukturen | Mehrere Werte gemeinsam verarbeiten | mittel | geplant |
| Funktionen | Größere Programme in verständliche Teile aufteilen | mittel | geplant |
| Python auf dem Mikrocontroller | Den Übergang von Python zu MicroPython verstehen | mittel | geplant |

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
