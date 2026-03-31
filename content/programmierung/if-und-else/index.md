---
title: "if und else"
subtitle: "Entscheidungen im Code treffen"
date: 2026-03-31
draft: false
author: "ElecKids"
description: "Eine einfache Einführung in if und else in Python."
summary: "Hier lernst du, wie Python Entscheidungen trifft und warum if und else für fast jedes Programm wichtig sind."
---

Viele Programme müssen entscheiden, was als Nächstes passiert. Soll eine Nachricht angezeigt werden? Ist ein Spiel gewonnen? Darf ein Level starten? Genau dafür gibt es in Python `if` und `else`.

Wenn du vorher noch einmal wiederholen willst, wie Python mit Werten arbeitet, schau zuerst in [Variablen, Zahlen und Text]({{< relref "programmierung/variablen-zahlen-und-text" >}}).

## Was macht `if`?

Mit `if` prüfst du eine Bedingung.

Wenn die Bedingung stimmt, führt Python den eingerückten Code darunter aus.

```python
punkte = 12

if punkte >= 10:
    print("Level geschafft!")
```

Hier prüft Python:

* Ist `punkte` größer oder gleich `10`?
* Wenn ja, wird `Level geschafft!` ausgegeben.

{{< admonition tip "Merke dir" >}}
`if` bedeutet: "Wenn das hier stimmt, dann führe diesen Teil aus."
{{< /admonition >}}

## Was ist eine Bedingung?

Eine Bedingung ist eine Frage, auf die Python nur mit `ja` oder `nein` antworten kann.

Zum Beispiel:

* Ist `punkte >= 10`?
* Ist `alter == 10`?
* Ist `leben > 0`?

Stimmt die Bedingung, läuft der `if`-Block. Stimmt sie nicht, überspringt Python ihn.

```python
alter = 9

if alter >= 10:
    print("Du bist in dieser Gruppe dabei.")
```

Hier wird nichts ausgegeben, weil `9` nicht größer oder gleich `10` ist.

{{< admonition info "Erkenntnis" >}}
Eine Bedingung ist für Python immer entweder **wahr** oder **falsch**. Dazwischen gibt es nichts.
{{< /admonition >}}

## Wichtige Vergleichszeichen

Mit diesen Zeichen prüfst du Bedingungen:

| Zeichen | Bedeutung | Beispiel |
| --- | --- | --- |
| `==` | ist gleich | `alter == 10` |
| `!=` | ist nicht gleich | `farbe != "rot"` |
| `>` | ist größer als | `punkte > 5` |
| `<` | ist kleiner als | `leben < 3` |
| `>=` | ist größer oder gleich | `punkte >= 10` |
| `<=` | ist kleiner oder gleich | `zeit <= 20` |

{{< admonition warning "Achte darauf" >}}
`=` und `==` sind nicht dasselbe. Mit `=` speicherst du einen Wert. Mit `==` vergleichst du zwei Werte.
{{< /admonition >}}

## Was macht `else`?

Mit `else` legst du fest, was passieren soll, wenn die Bedingung **nicht** stimmt.

```python
punkte = 7

if punkte >= 10:
    print("Level geschafft!")
else:
    print("Noch nicht geschafft.")
```

Python prüft zuerst die `if`-Bedingung:

1. Ist `punkte >= 10`?
2. Bei `7` lautet die Antwort: nein.
3. Deshalb wird der `else`-Teil ausgeführt.

Ausgabe:

```text
Noch nicht geschafft.
```

## So läuft eine Entscheidung ab

Das kannst du dir auch als Diagramm vorstellen:

{{< mermaid >}}
flowchart LR
    A["`punkte` speichert 7"] --> B{"Ist `punkte >= 10`?"}
    B -->|Ja| C["Gib aus: Level geschafft!"]
    B -->|Nein| D["Gib aus: Noch nicht geschafft."]
{{< /mermaid >}}

{{< admonition success "Das solltest du hier mitnehmen" >}}
Mit `if` prüfst du, ob etwas stimmt. Mit `else` legst du fest, was sonst passieren soll.
{{< /admonition >}}

## Die Einrückung ist wichtig

In Python erkennt man an der Einrückung, welche Zeilen zu `if` oder `else` gehören.

```python
punkte = 12

if punkte >= 10:
    print("Level geschafft!")
    print("Du darfst weiter.")
else:
    print("Versuch es noch einmal.")
```

Beide eingerückten Zeilen nach `if` gehören zusammen. Python weiß dadurch: Diese Anweisungen sollen nur laufen, wenn die Bedingung stimmt.

Wenn die Einrückung fehlt oder durcheinander ist, versteht Python den Code nicht richtig.

{{< admonition note "Wichtig" >}}
Nach `if ...:` und `else:` kommt ein Doppelpunkt. Die Zeilen darunter müssen eingerückt sein.
{{< /admonition >}}

## Ein Beispiel mit Text

`if` und `else` funktionieren nicht nur mit Zahlen, sondern auch mit Text.

```python
farbe = "blau"

if farbe == "blau":
    print("Richtig geraten!")
else:
    print("Das war eine andere Farbe.")
```

Auch hier prüft Python wieder nur: stimmt die Aussage oder stimmt sie nicht?

## Probier es selbst aus

Teste diese Aufgaben in Thonny:

1. Lege eine Variable `punkte` an und prüfe, ob sie größer oder gleich `10` ist.
2. Ändere den Wert von `punkte` und beobachte, wann `if` läuft und wann `else`.
3. Lege eine Variable `farbe` an und prüfe, ob sie `"gruen"` ist.
4. Schreibe ein kleines Programm, das je nach Alter zwei verschiedene Ausgaben macht.

## Wichtige Merksätze

* `if` prüft eine Bedingung.
* `else` läuft, wenn die Bedingung nicht stimmt.
* Bedingungen sind für Python entweder wahr oder falsch.
* `==` vergleicht zwei Werte, `=` speichert einen Wert.
* Einrückung und Doppelpunkt gehören in Python zu dieser Struktur dazu.

Wenn das klappt, kannst du als Nächstes lernen, wie du mit `for` und `while` Wiederholungen im Code aufbaust.
