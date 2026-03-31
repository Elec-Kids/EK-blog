---
title: "Listen und kleine Datenstrukturen"
subtitle: "Mehrere Werte zusammen speichern"
date: 2026-03-31
draft: false
author: "ElecKids"
description: "Eine einfache Einführung in Listen und kleine Datenstrukturen in Python."
summary: "Hier lernst du, wie du mit Listen mehrere Werte gemeinsam speicherst, einzelne Einträge ansprichst und mit Schleifen verarbeitest."
---

Manchmal reicht eine einzelne Variable nicht aus. Wenn du mehrere Farben, Namen oder Punktestände speichern willst, ist es unpraktisch, für jeden Wert eine eigene Variable anzulegen. Dafür gibt es Listen.

Wenn du vorher noch einmal wiederholen willst, wie Wiederholungen funktionieren, schau zuerst in [Schleifen mit for und while]({{< relref "programmierung/schleifen-mit-for-und-while" >}}).

## Was ist eine Liste?

Eine Liste ist eine geordnete Sammlung von mehreren Werten.

```python
farben = ["rot", "blau", "gruen"]
print(farben)
```

Ausgabe:

```text
['rot', 'blau', 'gruen']
```

In dieser Liste stehen drei Texte zusammen in einer einzigen Variable.

{{< admonition tip "Merke dir" >}}
Eine Liste ist wie eine Reihe von Fächern. In jedem Fach liegt ein Wert, und alle gehören zusammen.
{{< /admonition >}}

## Auf einzelne Werte zugreifen

Du kannst einzelne Einträge aus einer Liste ansprechen.

```python
farben = ["rot", "blau", "gruen"]

print(farben[0])
print(farben[1])
print(farben[2])
```

Ausgabe:

```text
rot
blau
gruen
```

Python zählt dabei nicht mit `1`, sondern mit `0`.

* `farben[0]` ist der erste Eintrag
* `farben[1]` ist der zweite Eintrag
* `farben[2]` ist der dritte Eintrag

{{< admonition note "Wichtig" >}}
Bei Listen beginnt das Zählen in Python immer bei `0`.
{{< /admonition >}}

## So kannst du dir eine Liste vorstellen

{{< mermaid >}}
flowchart LR
    A["`farben`"] --> B["[0] rot"]
    A --> C["[1] blau"]
    A --> D["[2] gruen"]
{{< /mermaid >}}

## Werte in einer Liste ändern

Du kannst einen Eintrag in einer Liste auch ersetzen.

```python
farben = ["rot", "blau", "gruen"]
farben[1] = "gelb"

print(farben)
```

Ausgabe:

```text
['rot', 'gelb', 'gruen']
```

Hier wurde der zweite Eintrag ausgetauscht.

{{< admonition info "Erkenntnis" >}}
Mit `farben[1] = "gelb"` änderst du nicht die ganze Liste, sondern nur genau diesen einen Platz.
{{< /admonition >}}

## Neue Werte anhängen

Oft soll eine Liste mit der Zeit größer werden. Dafür gibt es `append(...)`.

```python
tiere = ["Katze", "Hund"]
tiere.append("Maus")

print(tiere)
```

Ausgabe:

```text
['Katze', 'Hund', 'Maus']
```

Python hängt den neuen Wert hinten an die Liste an.

## Wie viele Einträge gibt es?

Mit `len(...)` kannst du nachschauen, wie lang eine Liste ist.

```python
tiere = ["Katze", "Hund", "Maus"]
print(len(tiere))
```

Ausgabe:

```text
3
```

Das ist nützlich, wenn du wissen willst, wie viele Werte gerade gespeichert sind.

## Mit einer Schleife durch eine Liste gehen

Listen und Schleifen passen gut zusammen.

```python
tiere = ["Katze", "Hund", "Maus"]

for tier in tiere:
    print(tier)
```

Ausgabe:

```text
Katze
Hund
Maus
```

Python nimmt hier nacheinander jeden Eintrag aus der Liste und speichert ihn kurz in `tier`.

{{< admonition info "Wichtig für das Verständnis" >}}
Die Variable `tier` ist **nicht** die ganze Liste. Sie enthält in jeder Runde immer nur **einen** einzelnen Eintrag aus der Liste.
{{< /admonition >}}

## So läuft die Schleife Runde für Runde

Bei diesem Beispiel passiert nicht alles gleichzeitig. Python nimmt immer nur einen Wert nach dem anderen:

{{< mermaid >}}
flowchart LR
    A["`tiere = [Katze, Hund, Maus]`"] --> B["1. Runde: `tier = Katze`"]
    B --> C["2. Runde: `tier = Hund`"]
    C --> D["3. Runde: `tier = Maus`"]
    D --> E["Keine Einträge mehr: Schleife endet"]
{{< /mermaid >}}

## Beispiel 1: Jeden Namen begrüßen

Mit einer Liste und einer `for`-Schleife kannst du leicht mehrere ähnliche Ausgaben erzeugen.

```python
namen = ["Mila", "Noah", "Tariq"]

for name in namen:
    print(f"Hallo, {name}!")
```

Ausgabe:

```text
Hallo, Mila!
Hallo, Noah!
Hallo, Tariq!
```

In jeder Runde steht in `name` ein anderer Eintrag aus der Liste.

## Beispiel 2: Jeden Eintrag prüfen

Du kannst eine Liste auch mit einer `for`-Schleife **und** einer Bedingung kombinieren.

```python
farben = ["rot", "blau", "gruen"]

for farbe in farben:
    if farbe == "rot":
        print("Rot gefunden!")
    else:
        print(f"{farbe} ist nicht rot.")
```

Ausgabe:

```text
Rot gefunden!
blau ist nicht rot.
gruen ist nicht rot.
```

Python geht also Eintrag für Eintrag durch die Liste und prüft jeden Wert einzeln.

{{< mermaid >}}
flowchart LR
    A["Nimm den nächsten Eintrag aus `farben`"] --> B["Speichere ihn kurz in `farbe`"]
    B --> C["Führe den Code im Block aus"]
    C --> D{"Noch Werte übrig?"}
    D -->|Ja| A
    D -->|Nein| E["Schleife endet"]
{{< /mermaid >}}

## Beispiel 3: Mit Zahlen aus einer Liste rechnen

Eine Schleife kann auch mit Zahlen aus einer Liste arbeiten.

```python
punkte = [2, 4, 6]

for punktzahl in punkte:
    print(punktzahl + 1)
```

Ausgabe:

```text
3
5
7
```

Python nimmt hier wieder jeden Wert einzeln. Erst `2`, dann `4`, dann `6`.

{{< admonition note "Wichtig" >}}
In diesem Beispiel wird **nicht** automatisch die ganze Liste verändert. Python benutzt nur jeden Wert nacheinander für die Rechnung.
{{< /admonition >}}

{{< admonition success "Das solltest du hier mitnehmen" >}}
Mit einer `for`-Schleife kannst du sehr einfach durch alle Werte in einer Liste gehen, ohne jeden Eintrag einzeln anzusprechen. Die Schleifenvariable steht dabei immer nur für den aktuellen Wert der gerade dran ist.
{{< /admonition >}}

## Was bedeutet hier "kleine Datenstrukturen"?

Eine Liste ist schon eine einfache Datenstruktur. Das bedeutet: Sie ist eine feste Art, Daten geordnet zu speichern.

In dieser Einführung reicht es, wenn du verstehst:

* mehrere Werte können zusammen in einer Liste liegen
* jeder Platz hat eine Nummer
* du kannst Werte lesen, ändern und ergänzen

Später gibt es noch andere Datenstrukturen. Für den Einstieg ist die Liste aber die wichtigste.

## Vorsicht bei ungültigen Positionen

Wenn du auf einen Platz zugreifen willst, den es nicht gibt, bekommt Python ein Problem.

```python
farben = ["rot", "blau", "gruen"]
print(farben[3])
```

Hier gibt es keinen Eintrag mit der Nummer `3`, weil die Liste nur die Plätze `0`, `1` und `2` hat.

{{< admonition warning "Achte darauf" >}}
Wenn eine Liste drei Einträge hat, sind die gültigen Positionen oft `0`, `1` und `2` und nicht `1`, `2`, `3`.
{{< /admonition >}}

## Probier es selbst aus

Teste diese Aufgaben in Thonny:

1. Erstelle eine Liste mit drei Lieblingstieren und gib sie komplett aus.
2. Gib nur den ersten und den dritten Eintrag aus.
3. Ändere einen Eintrag in deiner Liste.
4. Hänge mit `append(...)` einen weiteren Wert an.
5. Gib die Liste mit einer `for`-Schleife Zeile für Zeile aus.

## Wichtige Merksätze

* Eine Liste speichert mehrere Werte zusammen.
* Die Plätze in einer Liste werden ab `0` gezählt.
* Mit `liste[index]` greifst du auf einen einzelnen Wert zu.
* Mit `append(...)` hängst du einen neuen Wert hinten an.
* Mit einer `for`-Schleife kannst du durch alle Werte einer Liste gehen.

Wenn das klappt, kannst du als Nächstes lernen, wie du mit Funktionen größere Programme in übersichtliche Teile aufteilst.
