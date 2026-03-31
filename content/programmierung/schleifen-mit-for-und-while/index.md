---
title: "Schleifen mit for und while"
subtitle: "Wiederholungen im Code aufbauen"
date: 2026-03-31
draft: false
author: "ElecKids"
description: "Eine einfache Einführung in for- und while-Schleifen in Python."
summary: "Hier lernst du, wie du mit for und while Anweisungen mehrfach ausführen kannst und wann welche Schleife sinnvoll ist."
---

Manchmal soll ein Programm etwas nicht nur einmal tun, sondern mehrmals. Vielleicht willst du von `1` bis `5` zählen, denselben Text wiederholen oder einen Countdown bauen. Genau dafür gibt es Schleifen.

Wenn du vorher noch einmal wiederholen willst, wie Python Entscheidungen trifft, schau zuerst in [if und else]({{< relref "programmierung/if-und-else" >}}).

## Was ist eine Schleife?

Eine Schleife bedeutet: Python führt einen Teil des Codes mehrfach aus.

Statt denselben Befehl fünfmal hinzuschreiben, kannst du Python sagen: Wiederhole das bitte.

```python
print("Start")
print("Start")
print("Start")
```

Das geht zwar, ist aber schnell unpraktisch. Mit einer Schleife geht es besser.

{{< admonition tip "Merke dir" >}}
Eine Schleife ist ein wiederholter Ablauf. Python führt denselben Block so oft aus, wie du es vorgibst.
{{< /admonition >}}

## Die `for`-Schleife

Eine `for`-Schleife ist gut, wenn du schon weißt, wie oft etwas wiederholt werden soll.

```python
for zahl in range(5):
    print(zahl)
```

Ausgabe:

```text
0
1
2
3
4
```

Python läuft hier Schritt für Schritt durch die Zahlen aus `range(5)`.

`range(5)` bedeutet in diesem Fall:

* beginne bei `0`
* zähle weiter
* höre vor `5` auf

Darum erscheint die `5` selbst noch nicht in der Ausgabe.

{{< admonition note "Wichtig" >}}
`range(5)` liefert die Zahlen `0, 1, 2, 3, 4`. Die letzte Zahl ist also nicht automatisch dabei.
{{< /admonition >}}

## Wenn du bei 1 starten willst

Oft willst du nicht bei `0`, sondern bei `1` anfangen.

```python
for zahl in range(1, 6):
    print(zahl)
```

Ausgabe:

```text
1
2
3
4
5
```

Hier bedeutet `range(1, 6)`:

* starte bei `1`
* höre vor `6` auf

## Was passiert in jeder Runde?

Die Variable in der Schleife bekommt in jeder Runde einen neuen Wert.

```python
for zahl in range(1, 4):
    print(f"Jetzt ist die Zahl {zahl}")
```

Ausgabe:

```text
Jetzt ist die Zahl 1
Jetzt ist die Zahl 2
Jetzt ist die Zahl 3
```

Python macht also nicht alles auf einmal, sondern Runde für Runde.

{{< admonition info "Erkenntnis" >}}
In jeder Schleifenrunde bekommt die Schleifenvariable einen neuen Wert. Danach wird der eingerückte Block ausgeführt.
{{< /admonition >}}

## Die `while`-Schleife

Eine `while`-Schleife ist gut, wenn du nicht vorher festlegst, wie viele Runden es gibt, sondern nur eine Bedingung vorgibst.

```python
zaehler = 1

while zaehler <= 3:
    print(zaehler)
    zaehler = zaehler + 1
```

Ausgabe:

```text
1
2
3
```

Python prüft hier vor jeder neuen Runde:

1. Ist `zaehler <= 3`?
2. Wenn ja, wird der Block ausgeführt.
3. Danach wird `zaehler` erhöht.
4. Dann wird die Bedingung erneut geprüft.

## So kannst du dir `while` vorstellen

{{< mermaid >}}
flowchart LR
    A["`zaehler` startet bei 1"] --> B{"Ist `zaehler <= 3`?"}
    B -->|Ja| C["Gib `zaehler` aus"]
    C --> D["Erhöhe `zaehler` um 1"]
    D --> B
    B -->|Nein| E["Schleife endet"]
{{< /mermaid >}}

{{< admonition success "Das solltest du hier mitnehmen" >}}
`for` benutzt du oft, wenn die Anzahl der Wiederholungen schon feststeht. `while` benutzt du oft, wenn eine Bedingung entscheidet, ob es weitergeht.
{{< /admonition >}}

## Vorsicht bei `while`

Bei einer `while`-Schleife musst du aufpassen, dass sich etwas verändert. Sonst kann sie endlos weiterlaufen.

Schau dir dieses Beispiel an:

```python
zaehler = 1

while zaehler <= 3:
    print(zaehler)
```

Hier fehlt die Zeile, die `zaehler` verändert. Darum bleibt der Wert immer `1`, die Bedingung bleibt immer wahr, und die Schleife hört nicht auf.

{{< admonition warning "Achte darauf" >}}
In einer `while`-Schleife muss meistens eine Variable verändert werden. Sonst kann eine Endlosschleife entstehen.
{{< /admonition >}}

## Die Einrückung ist wieder wichtig

Wie bei `if` und `else` erkennt Python auch bei Schleifen an der Einrückung, welche Zeilen zur Schleife gehören.

```python
for zahl in range(3):
    print("Runde")
    print(zahl)
```

Beide eingerückten Zeilen werden in jeder Runde ausgeführt.

{{< admonition note "Wichtig" >}}
Nach `for ...:` und `while ...:` kommt ein Doppelpunkt. Die Zeilen darunter müssen eingerückt sein.
{{< /admonition >}}

## `for` und `while` im Vergleich

| Schleife | Gut geeignet für | Beispiel |
| --- | --- | --- |
| `for` | feste Anzahl von Wiederholungen | fünfmal zählen |
| `while` | Wiederholung solange etwas stimmt | solange Leben übrig sind |

## Probier es selbst aus

Teste diese Aufgaben in Thonny:

1. Schreibe eine `for`-Schleife, die die Zahlen von `1` bis `10` ausgibt.
2. Schreibe eine `for`-Schleife, die dreimal `Hallo!` ausgibt.
3. Schreibe eine `while`-Schleife, die von `5` rückwärts bis `1` zählt.
4. Ändere den Wert in einer `while`-Schleife und beobachte, wann sie endet.

## Wichtige Merksätze

* Schleifen wiederholen Code.
* `for` ist gut für eine bekannte Anzahl von Wiederholungen.
* `while` ist gut für Wiederholungen mit Bedingung.
* Bei `while` muss sich meistens etwas ändern, damit die Schleife endet.
* Doppelpunkt und Einrückung gehören auch hier zur Struktur dazu.

Wenn das klappt, kannst du als Nächstes lernen, wie du mehrere Werte zusammen in Listen speicherst und verarbeitest.
