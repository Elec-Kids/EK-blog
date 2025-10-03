---
title: "Dein Start ins MicroPython-Abenteuer: Thonny IDE für Eltern erklärt!"
date: 2025-10-02
draft: false
author: "Lumi-Fuchs"
tags: ["Thonny", "IDE", "MicroPython", "Programmieren", "Eltern", "Anleitung", "Software"]
categories: ["Software", "Elterninfo","Tutorials"]
featuredImagePreview: "header_thonny.png"
featuredImage: "header_thonny.png"
summary: "Begleiten Sie Ihr Kind auf den ersten Schritten ins MicroPython-Programmieren! Diese Anleitung erklärt Eltern kinderleicht, wie sie die Thonny IDE installieren, einen Mikrocontroller verbinden und erste Programme hochladen."
---

# Dein Start ins MicroPython-Abenteuer: Thonny IDE für Eltern erklärt! 🚀💻

Hallo liebe Eltern und Unterstützer unserer jungen Technik-Entdecker! 🦊 Euer Lumi-Fuchs ist heute hier, um euch eine super-praktische Software vorzustellen, die den Einstieg ins Programmieren mit Mikrocontrollern kinderleicht macht: die **Thonny IDE**! ✨

Wenn eure Kinder mit dem ESP8266 oder Raspberry Pi Pico in die Welt des MicroPython eintauchen, ist Thonny (sprich: Ton-nie) das perfekte Werkzeug. Es ist wie ein freundlicher Übersetzer und eine Werkstatt in einem, die es euch und euren Kindern ermöglicht, schnell und unkompliziert eigene Ideen umzusetzen. Diese Anleitung hilft euch, Thonny einzurichten, damit ihr eure Kinder optimal unterstützen könnt.

## Was ist Thonny IDE? – Die freundliche Programmier-Werkstatt! 🛠️

**IDE** steht für "Integrated Development Environment", also eine "integrierte Entwicklungsumgebung". Das ist ein schickes Wort für ein Programm, das alles Wichtige enthält, um Code zu schreiben, zu testen und auf einen Mikrocontroller zu übertragen. Thonny ist speziell dafür gemacht, Python und MicroPython zu lernen und zu nutzen. Es ist sehr übersichtlich und einfach zu bedienen, was es ideal für Anfänger macht.

**Warum Thonny so toll ist:**

*   **Einfache Installation:** Schnell auf dem Computer eingerichtet.
*   **Übersichtliche Oberfläche:** Keine komplizierten Menüs, alles Wichtige ist sofort sichtbar.
*   **MicroPython-Unterstützung:** Erkennt Mikrocontroller automatisch und kann Code direkt hochladen.
*   **Fehler finden leicht gemacht:** Hilft dabei, Fehler im Code zu entdecken und zu verstehen.

## Schritt 1: Thonny auf dem Computer installieren 🖥️

Die Installation von Thonny ist kinderleicht und funktioniert auf Windows, macOS und Linux:

1.  **Herunterladen:** Besuchen Sie die offizielle Thonny-Webseite: [https://thonny.org/](https://thonny.org/)
2.  **Installationsdatei wählen:** Laden Sie die passende Version für Ihr Betriebssystem herunter (z.B. "Windows installer" oder "macOS").
3.  **Installation starten:** Öffnen Sie die heruntergeladene Datei und folgen Sie den Anweisungen auf dem Bildschirm. Meistens reicht es, einfach auf "Weiter" oder "Installieren" zu klicken.
4.  **Thonny starten:** Nach der Installation finden Sie Thonny im Startmenü oder in Ihren Anwendungen. Öffnen Sie es!

### 1.5 Thonny auch für lokale Python-Programmierung nutzen 🐍

Bevor wir mit dem Mikrocontroller arbeiten, können Kinder Thonny auch als normale **Python-Umgebung auf dem eigenen Computer** nutzen. Das hat gleich mehrere Vorteile:

*   **Kein Terminal nötig:** Kinder müssen keine komplizierten Befehle in der Eingabeaufforderung (CMD/Terminal) eintippen. Alles läuft direkt in Thonny.
*   **Direktes Ausprobieren:** Erste Programme lassen sich sofort starten und die Ergebnisse erscheinen unten in der sogenannten **Shell**.
*   **Grundlagen üben:** Kinder können spielerisch die wichtigsten Elemente von Python (wie Ausgaben, Schleifen, Variablen) lernen, bevor sie mit echter Hardware experimentieren.

#### So funktioniert es:

1.  **Neues Programm anlegen:**
    Öffnen Sie Thonny und klicken Sie auf **File → New** (Datei → Neu). Im großen oberen Fenster erscheint ein leeres Dokument.

2.  **Erste Zeilen Code schreiben:**
    Geben Sie z. B. den folgenden Code ein:
    ```python
    print("Hallo, ich bin dein erstes Python-Programm!")
    for i in range(5):
        print("Runde:", i+1)
    ```

3.  **Programm starten:**
    Klicken Sie auf den **grünen Play-Button** (Pfeil-Symbol oben).
    Im unteren Bereich von Thonny (der Shell) erscheint sofort die Ausgabe.

    Ergebnis könnte so aussehen:
    ```
    Hallo, ich bin dein erstes Python-Programm!
    Runde: 1
    Runde: 2
    Runde: 3
    Runde: 4
    Runde: 5
    ```

4.  **Speichern:**
    Speichern Sie das Programm wie gewohnt über **File → Save as...**. Wenn Sie es auf dem PC speichern, ist es ein normales Python-Programm und läuft immer wieder, wenn Sie es öffnen und starten.

#### Warum das sinnvoll ist:

- Kinder können in einer sicheren Umgebung erste Erfolgserlebnisse haben.
- Sie lernen, wie Programme Schritt für Schritt aufgebaut sind.
- Sie müssen sich noch nicht mit Verkabelung oder Treibern beschäftigen.

Erst wenn die Grundlagen sitzen, wechseln wir zum Mikrocontroller (ab Schritt 2). Dann wissen die Kinder schon, wie man Code schreibt und startet – und sehen ihre Programme direkt in der Hardware lebendig werden.


## Schritt 2: Den Mikrocontroller mit Thonny verbinden 🔌

Jetzt wird es spannend! Wir verbinden den Mikrocontroller (z.B. ESP8266 oder Raspberry Pi Pico) mit dem Computer und sagen Thonny, dass es mit ihm sprechen soll.

1.  **Mikrocontroller vorbereiten:** Stellen Sie sicher, dass auf dem Mikrocontroller bereits MicroPython installiert ist. Falls nicht, gibt es dafür separate Anleitungen (z.B. auf der MicroPython-Webseite oder in unseren ElecKids-Tutorials).
2.  **Verbinden per USB-Kabel:** Schließen Sie den Mikrocontroller mit einem USB-Kabel an Ihren Computer an. Achten Sie darauf, ein Datenkabel zu verwenden, nicht nur ein Ladekabel!
3.  **Treiber installieren (falls nötig):** Manchmal muss der Computer einen speziellen Treiber installieren, damit er den Mikrocontroller erkennt. Bei Raspberry Pi Pico ist das meistens nicht nötig. Bei ESP8266-Boards (wie NodeMCU oder Wemos D1 Mini) kann es sein, dass ein Treiber für den CH340- oder CP210x-Chip benötigt wird. Eine kurze Suche nach "CH340 Treiber Windows" oder "CP210x Treiber Mac" hilft hier schnell weiter.
4.  **Thonny einstellen:**
    *   Gehen Sie in Thonny auf **"Tools"** (Werkzeuge) und dann auf **"Options..."** (Optionen...).
    *   Wählen Sie den Reiter **"Interpreter"**.
    *   Wählen Sie im Dropdown-Menü **"MicroPython (ESP32/ESP8266)"** oder **"MicroPython (Raspberry Pi Pico)"** aus, je nachdem, welchen Mikrocontroller Ihr Kind verwendet.
    *   Bei **"Port"** wählen Sie den USB-Anschluss aus, an dem der Mikrocontroller angeschlossen ist. Das ist oft ein Eintrag wie `COMx` (Windows) oder `/dev/tty.usbserial-xxxx` (macOS/Linux). Wenn Sie unsicher sind, probieren Sie die verschiedenen Optionen aus oder ziehen Sie das Kabel ab und stecken es wieder ein – der richtige Port verschwindet dann kurz und taucht wieder auf.
    *   Klicken Sie auf **"OK"**.

Wenn alles geklappt hat, sollte im unteren Bereich von Thonny (der "Shell") eine Meldung erscheinen, die anzeigt, dass Thonny mit dem Mikrocontroller verbunden ist (z.B. `MicroPython v1.x.x on 20xx-xx-xx; ESP module with ESP8266` oder `MicroPython v1.x.x on 20xx-xx-xx; Raspberry Pi Pico`).

## Schritt 3: Das erste Programm hochladen und starten 🚀

Jetzt kann das Programmieren losgehen! Wir schreiben ein ganz einfaches Programm, das eine LED blinken lässt.

1.  **Code schreiben:** Im oberen, großen Bereich von Thonny (dem Editor) schreiben Sie den Code. Hier ein Beispiel für eine LED, die an Pin 2 angeschlossen ist (oft bei ESP8266-Boards, beim Pico wäre es z.B. Pin 25 für die eingebaute LED):

    ```python
    from machine import Pin
    import time

    # Definiere den Pin, an den die LED angeschlossen ist
    # (Beim ESP8266 ist D4 oft Pin 2, beim Pico ist Pin 25 die eingebaute LED)
    led = Pin(2, Pin.OUT) # Beispiel für ESP8266 mit LED an D4

    while True:
        led.value(1)  # LED einschalten (HIGH)
        time.sleep(0.5) # 0.5 Sekunden warten
        led.value(0)  # LED ausschalten (LOW)
        time.sleep(0.5) # 0.5 Sekunden warten
    ```

2.  **Speichern auf dem Mikrocontroller:**
    *   Klicken Sie auf das **Speichern-Symbol** (Diskette) oder gehen Sie auf "File" (Datei) -> "Save as..." (Speichern unter...).
    *   Wählen Sie **"MicroPython device"** (MicroPython-Gerät) aus.
    *   Geben Sie der Datei den Namen `main.py` und klicken Sie auf "OK". `main.py` ist ein besonderer Name, denn der Mikrocontroller startet dieses Programm automatisch, wenn er eingeschaltet wird.

3.  **Programm starten:**
    *   Nach dem Speichern startet das Programm oft automatisch. Falls nicht, klicken Sie auf den **grünen "Run"-Knopf** (Pfeil-Symbol) oder trennen Sie den Mikrocontroller kurz vom USB-Kabel und stecken ihn wieder ein.

Die LED auf dem Mikrocontroller (oder die extern angeschlossene LED) sollte nun im Sekundentakt blinken! Herzlichen Glückwunsch, Sie haben erfolgreich ein MicroPython-Programm auf den Mikrocontroller Ihres Kindes geladen!

## Tipps zur Unterstützung eurer Kinder 🤝

*   **Gemeinsam entdecken:** Setzen Sie sich zusammen hin und probieren Sie die Beispiele aus. Fragen Sie Ihr Kind, was es als Nächstes bauen möchte.
*   **Fehler sind Freunde:** Wenn ein Programm nicht sofort funktioniert, ist das kein Problem! Helfen Sie Ihrem Kind, die Fehlermeldungen in Thonny zu lesen und gemeinsam nach Lösungen zu suchen. Das ist ein wichtiger Teil des Lernprozesses.
*   **Ermutigen und Loben:** Jedes funktionierende Projekt, egal wie klein, ist ein Erfolg! Loben Sie die Kreativität und den Forschergeist Ihres Kindes.
*   **Sicherheit beachten:** Erinnern Sie Ihr Kind immer daran, vorsichtig mit Elektronik umzugehen und die Anleitungen genau zu befolgen.

Mit Thonny und eurer Unterstützung steht dem MicroPython-Abenteuer eurer Kinder nichts mehr im Wege! Es ist eine wunderbare Möglichkeit, logisches Denken, Problemlösung und Kreativität zu fördern.

**Euer Lumi-Fuchs – Euer Programmier-Begleiter!** 🦊💻✨
