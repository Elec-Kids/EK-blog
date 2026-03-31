---
title: "Python auf dem Mikrocontroller"
subtitle: "Der Einstieg in MicroPython"
date: 2026-03-31
draft: false
author: "ElecKids"
description: "Eine einfache Einführung in MicroPython und Python auf Mikrocontrollern."
summary: "Hier lernst du, was sich ändert, wenn Python nicht mehr nur auf dem Computer läuft, sondern direkt auf einem Mikrocontroller."
---

Bis jetzt lief dein Python-Code nur am Computer. Der nächste Schritt ist besonders spannend: Dein Programm läuft direkt auf einem Mikrocontroller und kann echte Hardware steuern.

Wenn du vorher noch einmal wiederholen willst, wie du Code in Bausteine aufteilst, schau zuerst in [Funktionen]({{< relref "programmierung/funktionen" >}}).

## Was bedeutet das überhaupt?

Ein Mikrocontroller ist ein kleiner Computer auf einem Board. Er kann Signale lesen und Dinge steuern, zum Beispiel:

* LEDs
* Taster
* Sensoren
* kleine Displays

Wenn dort Python läuft, wird dein Code also nicht nur auf dem Bildschirm sichtbar. Er kann echte Bauteile ansteuern.

{{< admonition tip "Merke dir" >}}
Auf dem Computer schreibt dein Python-Programm Text in ein Fenster. Auf dem Mikrocontroller kann es zusätzlich mit echter Hardware arbeiten.
{{< /admonition >}}

## Was ist MicroPython?

MicroPython ist eine schlankere Version von Python für Mikrocontroller.

Die Sprache sieht an vielen Stellen vertraut aus, aber sie bringt zusätzliche Dinge mit, die für Hardware wichtig sind. Zum Beispiel kannst du mit `Pin` Ein- und Ausgänge steuern.

```python
from machine import Pin
```

So etwas brauchst du auf dem normalen Computer meistens nicht. Auf einem Mikrocontroller ist es aber zentral.

{{< admonition info "Erkenntnis" >}}
MicroPython ist kein völlig neues Thema, sondern Python in einer Form, die für kleine Boards und Hardware angepasst wurde.
{{< /admonition >}}

## Was du brauchst

Für den Einstieg brauchst du:

* einen Mikrocontroller, zum Beispiel einen Raspberry Pi Pico
* ein USB-Datenkabel
* einen Computer mit Thonny
* etwas Geduld beim ersten Verbinden

Wenn du noch unsicher bist, helfen dir diese beiden Seiten:

* [Was ist ein Mikrocontroller?]({{< relref "posts/was-ist-ein-mikrokontroller" >}})
* [Thonny für Eltern: Einstieg in Python und MicroPython]({{< relref "posts/thonny-installation-manual" >}})

## Was ist jetzt anders als am Computer?

Am Computer startet dein Python-Programm, zeigt etwas an und beendet sich oft wieder. Auf dem Mikrocontroller läuft dein Code häufig dauerhaft weiter oder reagiert direkt auf Taster, Sensoren und andere Signale.

Ein typischer Unterschied ist:

* am Computer: `print("Hallo")`
* auf dem Mikrocontroller: LED an, LED aus, Taster lesen, Sensorwert messen

## So läuft der Weg vom Code zur Hardware

{{< mermaid >}}
flowchart LR
    A["Du schreibst Code in Thonny"] --> B["Der Code wird auf das Board übertragen"]
    B --> C["MicroPython führt den Code auf dem Mikrocontroller aus"]
    C --> D["Das Board steuert LED, Taster oder Sensoren"]
{{< /mermaid >}}

## Ein erstes Beispiel: LED blinken lassen

Das folgende Beispiel ist für einen **Raspberry Pi Pico** gedacht:

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

Was passiert hier?

1. `Pin` wird importiert, damit du einen Ausgang am Board steuern kannst.
2. `time` wird importiert, damit du kurze Pausen machen kannst.
3. `led = Pin(25, Pin.OUT)` richtet den LED-Pin als Ausgang ein.
4. `while True:` bedeutet: Dieser Block wird immer wiederholt.
5. Die LED wird eingeschaltet, dann kurz gewartet.
6. Die LED wird ausgeschaltet, dann wieder kurz gewartet.

Das Ergebnis ist ein Blinklicht.

{{< admonition success "Das solltest du hier mitnehmen" >}}
Auf dem Mikrocontroller schreibt dein Code nicht nur Text, sondern kann direkt etwas in der echten Welt steuern.
{{< /admonition >}}

## Warum `while True` hier sinnvoll ist

Auf dem Computer war eine Endlosschleife eher etwas, worauf du aufpassen musstest. Auf einem Mikrocontroller ist sie oft ganz normal, weil das Board ständig weiterarbeiten soll.

Zum Beispiel:

* eine LED soll weiter blinken
* ein Taster soll immer wieder geprüft werden
* ein Sensor soll regelmäßig gemessen werden

Darum sieht man in MicroPython-Projekten oft `while True`.

## Wichtig: Nicht jedes Board ist gleich

Das LED-Beispiel oben passt zum Raspberry Pi Pico. Bei anderen Boards kann der LED-Pin anders heißen oder ganz anders angesprochen werden.

{{< admonition warning "Achte darauf" >}}
Code für Mikrocontroller ist oft **boardabhängig**. Ein Beispiel für den Pico läuft nicht automatisch genauso auf jedem anderen Board.
{{< /admonition >}}

## Was du aus dem Computer-Python schon mitnimmst

Vieles bleibt gleich:

* Variablen funktionieren weiter
* `if` und `else` funktionieren weiter
* Schleifen funktionieren weiter
* Funktionen funktionieren weiter

Neu ist vor allem, dass dein Code jetzt auf Hardware trifft.

## Probier es selbst aus

Wenn du einen Raspberry Pi Pico hast, probiere diese Schritte:

1. Übertrage das Blink-Beispiel auf das Board.
2. Ändere die Pausenzeit von `0.5` auf `1.0` und beobachte den Unterschied.
3. Ändere die Pausenzeit auf `0.2`, damit die LED schneller blinkt.
4. Lies den Code noch einmal und erkläre dir selbst, welche Zeile für welche Aufgabe zuständig ist.

## Wichtige Merksätze

* MicroPython ist Python für Mikrocontroller.
* Auf einem Mikrocontroller kann dein Code echte Hardware steuern.
* Vieles aus normalem Python bleibt gleich.
* Bei Hardware-Code kommt zusätzlich das jeweilige Board dazu.
* Ein kleines Blink-Beispiel ist ein guter erster Schritt.

Wenn das klappt, kannst du als Nächstes mit echten Tastern, LEDs oder Sensoren kleine Projekte bauen.
