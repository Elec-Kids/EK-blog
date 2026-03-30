---
title: "Thonny für Eltern: Einstieg in Python und MicroPython"
date: 2025-10-02
draft: false
author: "ElecKids"
tags: ["Thonny", "Python", "MicroPython", "Eltern", "Software"]
categories: ["Software", "Elterninfo", "Tutorials"]
featuredImagePreview: "header_thonny.png"
featuredImage: "header_thonny.png"
summary: "Thonny ist eine einfache Entwicklungsumgebung für Python und MicroPython. Diese Anleitung zeigt Eltern, wie sie Thonny installieren, erste Programme starten und einen Mikrocontroller verbinden."
---

# Thonny für Eltern: Einstieg in Python und MicroPython

Wenn Kinder mit Python oder MicroPython anfangen, ist eine übersichtliche Arbeitsumgebung sehr hilfreich. **Thonny** ist dafür gut geeignet: Das Programm ist einfach aufgebaut, läuft auf den gängigen Betriebssystemen und reicht für die ersten Schritte am Computer und mit Mikrocontrollern völlig aus.

Diese Anleitung richtet sich an Eltern und zeigt den typischen Einstieg.

## Was ist Thonny?

Thonny ist eine Entwicklungsumgebung für Python. Damit kann man:

* Python-Code schreiben
* Programme direkt starten
* Ausgaben und Fehlermeldungen sehen
* bei MicroPython den Code auf einen Mikrocontroller übertragen

Für Kinder ist vor allem hilfreich, dass alles in einem Fenster passiert und kein Terminal nötig ist.

## Schritt 1: Thonny installieren

1. Öffnen Sie die offizielle Webseite: [https://thonny.org/](https://thonny.org/)
2. Laden Sie die passende Version für Windows, macOS oder Linux herunter.
3. Starten Sie die Installation und folgen Sie den normalen Schritten.
4. Öffnen Sie Thonny nach der Installation.

## Schritt 2: Python zuerst lokal ausprobieren

Bevor ein Mikrocontroller angeschlossen wird, lohnt sich ein erster Test direkt am Computer. So kann Ihr Kind sehen, wie Code geschrieben und gestartet wird, ohne sich gleichzeitig mit Kabeln oder Hardware zu beschäftigen.

Öffnen Sie in Thonny ein neues Dokument und tragen Sie zum Beispiel diesen Code ein:

```python
print("Hallo, ich bin dein erstes Python-Programm!")
for i in range(5):
    print("Runde:", i + 1)
```

Starten Sie das Programm mit dem grünen Play-Button. Die Ausgabe erscheint unten in der Shell.

Das reicht für einen ersten Test schon aus. Danach kann die Datei ganz normal über **File -> Save as...** gespeichert werden.

## Warum dieser Zwischenschritt sinnvoll ist

Der lokale Einstieg hat ein paar klare Vorteile:

* Kinder lernen zuerst die Grundidee von Programmcode.
* Die Umgebung bleibt übersichtlich.
* Fehler lassen sich leichter einordnen.
* Es gibt noch keine zusätzliche Komplexität durch Board, Treiber oder Verkabelung.

## Schritt 3: Einen Mikrocontroller verbinden

Wenn die ersten Python-Beispiele am Computer funktionieren, kann Thonny auch mit einem MicroPython-Board verwendet werden.

Vor dem Verbinden sollten Sie prüfen:

* Ist auf dem Board bereits **MicroPython** installiert?
* Wird ein **Datenkabel** verwendet und nicht nur ein Ladekabel?
* Braucht das Board unter Windows oder macOS eventuell einen Treiber?

Beim Raspberry Pi Pico ist meist kein zusätzlicher Treiber nötig. Bei manchen ESP8266-Boards wird ein Treiber für Chips wie **CH340** oder **CP210x** benötigt.

## Schritt 4: Thonny auf das Board einstellen

1. Öffnen Sie in Thonny **Tools -> Options...**
2. Wechseln Sie zum Reiter **Interpreter**
3. Wählen Sie den passenden Interpreter aus:
   * **MicroPython (Raspberry Pi Pico)**
   * oder **MicroPython (ESP32/ESP8266)**
4. Wählen Sie darunter den richtigen Port aus.
5. Bestätigen Sie mit **OK**.

Wenn alles passt, erscheint unten in der Shell eine Meldung des angeschlossenen Boards.

## Schritt 5: Ein erstes MicroPython-Programm testen

Für einen einfachen Funktionstest reicht ein Blinkprogramm. Das folgende Beispiel nutzt die eingebaute LED des Raspberry Pi Pico:

```python
from machine import Pin
import time

led = Pin(25, Pin.OUT)

while True:
    led.value(1)
    time.sleep(0.5)
    led.value(0)
    time.sleep(0.5)
```

Wichtig: Dieses Beispiel ist für den **Raspberry Pi Pico** gedacht. Bei anderen Boards kann der LED-Pin anders sein.

Speichern Sie die Datei über **File -> Save as...** auf dem **MicroPython device**, zum Beispiel als `main.py`. Danach startet das Programm meist direkt oder nach einem Neustart des Boards.

## Typische Probleme am Anfang

Wenn nichts funktioniert, liegt es oft an einem dieser Punkte:

* das USB-Kabel ist nur ein Ladekabel
* der falsche Interpreter ist ausgewählt
* der falsche Port ist eingestellt
* auf dem Board ist noch kein MicroPython installiert
* ein Treiber fehlt

In diesen Fällen lohnt es sich, Schritt für Schritt zu prüfen statt alles gleichzeitig zu ändern.

## Wie Eltern sinnvoll unterstützen können

Hilfreich ist vor allem:

* gemeinsam die ersten Programme starten
* Fehlermeldungen in Ruhe lesen
* den Aufbau ordentlich halten
* kleine Fortschritte ernst nehmen

Kinder müssen am Anfang nicht alles verstehen. Wichtiger ist, dass sie ausprobieren, Rückmeldungen sehen und lernen, Probleme systematisch zu prüfen.
