---
title: "Variablen, Zahlen und Text"
subtitle: "Werte speichern und mit ihnen arbeiten"
date: 2026-03-31
draft: false
author: "ElecKids"
description: "Eine einfache Einführung in Variablen, Zahlen und Text in Python."
summary: "Hier lernst du, wie Python sich Werte merkt, wie du mit Zahlen rechnest und wie du Text in Programmen verwendest."
---

Wenn du in Python nicht immer wieder dieselben Werte neu schreiben willst, benutzt du Variablen. Mit ihnen kann sich dein Programm Zahlen, Namen oder Texte merken und später wieder verwenden.

Wenn du den ersten Schritt noch nicht gemacht hast, starte am besten mit [Python kennenlernen]({{< relref "posts/python-einfuehrung" >}}).

## Was ist eine Variable?

Eine Variable ist ein Name, unter dem Python etwas speichert.

```python
name = "Mila"
punkte = 8
```

Hier merkt sich Python zwei Dinge:

* In `name` steht der Text `"Mila"`
* In `punkte` steht die Zahl `8`

Mit `print(...)` kannst du dir den Inhalt anzeigen lassen:

```python
name = "Mila"
punkte = 8

print(name)
print(punkte)
```

Die Ausgabe sieht dann so aus:

```text
Mila
8
```

{{< admonition tip "Merke dir" >}}
Eine Variable ist wie ein beschriftetes Fach. Unter dem Namen `name` liegt hier der Text `"Mila"`, unter `punkte` die Zahl `8`.
{{< /admonition >}}

## Zahlen in Python

Mit Zahlen kannst du in Python direkt rechnen.

```python
aepfel = 4
birnen = 3
gesamt = aepfel + birnen

print(gesamt)
```

Die Ausgabe ist:

```text
7
```

Du kannst auch andere Rechenarten benutzen:

```python
print(10 - 2)
print(3 * 4)
print(12 / 3)
```

{{< admonition note "Wichtig" >}}
Zahlen stehen in Python **ohne** Anführungszeichen. Dann kann Python mit ihnen rechnen.
{{< /admonition >}}

## Text in Python

Text steht in Anführungszeichen.

```python
farbe = "blau"
tier = "Katze"
```

Ohne Anführungszeichen würde Python denken, dass `blau` oder `Katze` Variablennamen sind.

Auch Text kannst du ausgeben:

```python
farbe = "blau"
print(farbe)
```

{{< admonition warning "Achte darauf" >}}
Text braucht Anführungszeichen. Ohne Anführungszeichen würde Python glauben, dass `blau` ein Variablenname ist.
{{< /admonition >}}

## Der Unterschied zwischen `7` und `"7"`

Das sieht ähnlich aus, ist aber nicht dasselbe:

```python
zahl = 7
text = "7"
```

`7` ist eine Zahl. Damit kannst du rechnen.

```python
zahl = 7
print(zahl + 3)
```

Ausgabe:

```text
10
```

`"7"` ist Text. Damit rechnet Python nicht, sondern behandelt es wie Zeichen.

```python
text = "7"
print(text + "3")
```

Ausgabe:

```text
73
```

Das ist wichtig: Zahlen und Text sind nicht automatisch dasselbe.

{{< admonition info "Erkenntnis" >}}
`7` und `"7"` sehen ähnlich aus, sind für Python aber verschiedene Dinge: einmal eine Zahl, einmal Text.
{{< /admonition >}}

## Zahlen und Text zusammen benutzen

Oft willst du beides in einer Ausgabe kombinieren. Das geht besonders gut mit einem `f`-String:

```python
name = "Mila"
punkte = 8

print(f"{name} hat {punkte} Punkte.")
```

Ausgabe:

```text
Mila hat 8 Punkte.
```

Das `f` vor dem Text bedeutet: Python darf die Werte aus den geschweiften Klammern einsetzen.

{{< admonition tip "Praktisch" >}}
Mit `f`-Strings kannst du Text und Werte sauber zusammen ausgeben, ohne alles mühsam zusammenzusetzen.
{{< /admonition >}}

## Werte verändern

Variablen können sich ändern. Das ist wichtig, weil Programme oft mit Werten arbeiten, die nicht immer gleich bleiben. Punkte können mehr werden, Leben können weniger werden oder ein Zähler läuft Schritt für Schritt hoch.

```python
punkte = 8
punkte = punkte + 1

print(punkte)
```

Ausgabe:

```text
9
```

Wenn du so etwas zum ersten Mal siehst, wirkt die Zeile

```python
punkte = punkte + 1
```

erst einmal seltsam. Links und rechts steht ja `punkte`. Python liest das aber in einer festen Reihenfolge:

1. Es schaut nach, welcher Wert gerade in `punkte` steckt.
2. Es rechnet auf der rechten Seite `punkte + 1`.
3. Das Ergebnis wird wieder in `punkte` gespeichert.

Vorher war also in `punkte` die `8`. Nach der Rechnung wird daraus die `9`.

So kannst du dir den Ablauf auch als kleines Diagramm vorstellen:

{{< mermaid >}}
flowchart LR
    A["`punkte` speichert 8"] --> B["Python liest den aktuellen Wert"]
    B --> C["Es rechnet: 8 + 1"]
    C --> D["Das Ergebnis ist 9"]
    D --> E["`punkte` speichert jetzt 9"]
{{< /mermaid >}}

Du kannst dir das wie eine Kiste mit einem Etikett vorstellen:

* Auf der Kiste steht `punkte`
* In der Kiste liegt zuerst `8`
* Dann nimmt Python die `8`, rechnet `+ 1` und legt `9` zurück in dieselbe Kiste

Das alte Ergebnis wird also ersetzt.

Hier noch ein längeres Beispiel:

```python
punkte = 8
print(punkte)

punkte = punkte + 1
print(punkte)

punkte = punkte + 1
print(punkte)
```

Ausgabe:

```text
8
9
10
```

So kannst du zum Beispiel Punkte zählen oder Werte Schritt für Schritt verändern.

{{< admonition success "Das solltest du hier mitnehmen" >}}
`punkte = punkte + 1` bedeutet nicht: "8 ist gleich 9". Es bedeutet: "Nimm den bisherigen Wert, erhöhe ihn um 1 und speichere das neue Ergebnis wieder unter demselben Namen."
{{< /admonition >}}

## Probier es selbst aus

Teste diese kleinen Aufgaben in Thonny:

1. Speichere deinen Namen in einer Variable und gib ihn aus.
2. Speichere dein Alter in einer Variable und rechne aus, wie alt du nächstes Jahr bist.
3. Speichere deine Lieblingsfarbe als Text und gib einen Satz dazu aus.
4. Schreibe eine Ausgabe wie: `Timo hat 12 Punkte.`

## Wichtige Merksätze

* Zahlen stehen ohne Anführungszeichen.
* Text steht mit Anführungszeichen.
* Variablen helfen dir, Werte zu speichern und später wieder zu benutzen.
* Mit `print(...)` kannst du prüfen, was gerade in einer Variable steckt.

Wenn das klappt, kannst du als Nächstes lernen, wie Programme Entscheidungen treffen, zum Beispiel mit `if` und `else`.
