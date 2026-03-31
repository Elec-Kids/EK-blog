---
title: "Funktionen"
subtitle: "Code in übersichtliche Teile aufteilen"
date: 2026-03-31
draft: false
author: "ElecKids"
description: "Eine einfache Einführung in Funktionen in Python."
summary: "Hier lernst du, was Funktionen sind, wie du sie aufrufst, wie du Werte übergibst und wie sie dir helfen, Programme übersichtlich aufzubauen."
---

Wenn Programme größer werden, willst du nicht jeden Schritt immer wieder neu hinschreiben. Genau dafür gibt es Funktionen. Mit ihnen kannst du Code in kleine, verständliche Bausteine aufteilen.

Wenn du vorher noch einmal wiederholen willst, wie Listen und Schleifen zusammenarbeiten, schau zuerst in [Listen und kleine Datenstrukturen]({{< relref "programmierung/listen-und-kleine-datenstrukturen" >}}).

## Was ist eine Funktion?

Eine Funktion ist ein benannter Codeblock, den du später aufrufen kannst.

Du kannst dir eine Funktion wie ein Werkzeug vorstellen:

* sie hat einen Namen
* sie erledigt eine bestimmte Aufgabe
* du kannst sie immer wieder benutzen

```python
def hallo():
    print("Hallo!")
```

Mit `def` beginnt die Definition einer Funktion. In diesem Beispiel heißt sie `hallo`.

{{< admonition tip "Merke dir" >}}
Eine Funktion ist ein eigener kleiner Arbeitsblock mit einem Namen.
{{< /admonition >}}

## Definieren ist noch nicht ausführen

Wenn du eine Funktion nur schreibst, passiert noch nichts. Sie wird erst ausgeführt, wenn du sie aufrufst.

```python
def hallo():
    print("Hallo!")

hallo()
hallo()
```

Ausgabe:

```text
Hallo!
Hallo!
```

Die Funktion wird hier zweimal aufgerufen. Deshalb erscheint die Ausgabe auch zweimal.

{{< admonition note "Wichtig" >}}
`def hallo():` bedeutet nicht: "Führe das jetzt aus." Es bedeutet: "Merke dir diesen Code unter dem Namen `hallo`."
{{< /admonition >}}

## So läuft ein Funktionsaufruf ab

{{< mermaid >}}
flowchart LR
    A["Programm läuft"] --> B["`hallo()` wird aufgerufen"]
    B --> C["Python springt in die Funktion"]
    C --> D["Der Code in `hallo` wird ausgeführt"]
    D --> E["Python kehrt zum Hauptprogramm zurück"]
{{< /mermaid >}}

## Warum Funktionen nützlich sind

Funktionen helfen dir, weil du damit:

* Wiederholungen vermeidest
* längere Programme ordnen kannst
* Aufgaben in kleine Schritte aufteilst
* Code leichter lesen und ändern kannst

Statt denselben Block immer wieder zu kopieren, schreibst du ihn einmal als Funktion.

## Funktionen mit Eingaben

Oft soll eine Funktion nicht immer genau dasselbe tun, sondern mit unterschiedlichen Werten arbeiten. Dafür kannst du ihr eine Eingabe mitgeben.

```python
def begruesse(name):
    print(f"Hallo, {name}!")

begruesse("Mila")
begruesse("Noah")
```

Ausgabe:

```text
Hallo, Mila!
Hallo, Noah!
```

Hier ist `name` ein Platzhalter. Beim Aufruf bekommt die Funktion dann einen echten Wert.

{{< admonition info "Erkenntnis" >}}
Der Name in den Klammern der Funktion ist wie ein leeres Fach. Beim Aufruf legst du einen passenden Wert hinein.
{{< /admonition >}}

## Funktionen und Listen kombinieren

Funktionen passen gut zu Listen und Schleifen.

```python
def begruesse(name):
    print(f"Hallo, {name}!")

namen = ["Mila", "Noah", "Tariq"]

for name in namen:
    begruesse(name)
```

Ausgabe:

```text
Hallo, Mila!
Hallo, Noah!
Hallo, Tariq!
```

Python geht hier erst durch die Liste und ruft dann für jeden Namen die Funktion auf.

## Funktionen können auch etwas zurückgeben

Manche Funktionen sollen nicht nur etwas ausgeben, sondern ein Ergebnis zurückgeben. Dafür gibt es `return`.

```python
def doppelt(zahl):
    return zahl * 2

ergebnis = doppelt(4)
print(ergebnis)
```

Ausgabe:

```text
8
```

Hier passiert Folgendes:

1. Die Funktion bekommt die `4`
2. Sie rechnet `4 * 2`
3. Mit `return` gibt sie das Ergebnis zurück
4. Das Ergebnis wird in `ergebnis` gespeichert

{{< admonition success "Das solltest du hier mitnehmen" >}}
`print(...)` zeigt etwas an. `return` gibt einen Wert zurück, damit du später weiter damit arbeiten kannst.
{{< /admonition >}}

## Einrückung und Doppelpunkt sind wieder wichtig

Wie bei `if`, `else`, `for` und `while` erkennt Python auch bei Funktionen an der Einrückung, welche Zeilen dazugehören.

```python
def zaehle_bis_drei():
    print(1)
    print(2)
    print(3)
```

Alle eingerückten Zeilen gehören hier zur Funktion.

{{< admonition warning "Achte darauf" >}}
Nach `def name(...):` kommt ein Doppelpunkt. Die Zeilen der Funktion müssen eingerückt sein.
{{< /admonition >}}

## Gute Funktionsnamen helfen

Ein guter Funktionsname sagt möglichst klar, was die Funktion macht.

```python
def starte_spiel():
    print("Das Spiel startet.")
```

Das ist verständlicher als ein Name wie `mach1()`.

## Probier es selbst aus

Teste diese Aufgaben in Thonny:

1. Schreibe eine Funktion, die `Hallo!` ausgibt, und rufe sie zweimal auf.
2. Schreibe eine Funktion `begruesse(name)`, die einen Namen begrüßt.
3. Schreibe eine Funktion `quadriere(zahl)`, die die Zahl mit sich selbst multipliziert und zurückgibt.
4. Erstelle eine Liste mit Namen und rufe in einer Schleife für jeden Namen deine Begrüßungsfunktion auf.

## Wichtige Merksätze

* Eine Funktion ist ein benannter Codeblock.
* Mit `def` definierst du eine Funktion.
* Erst beim Aufruf wird die Funktion ausgeführt.
* Über Klammern kannst du Werte an die Funktion übergeben.
* Mit `return` kann eine Funktion ein Ergebnis zurückgeben.

Wenn das klappt, kannst du als Nächstes lernen, wie Python auf einem Mikrocontroller läuft und was bei MicroPython anders ist als auf dem Computer.
