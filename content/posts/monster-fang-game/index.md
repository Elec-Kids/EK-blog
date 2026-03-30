---
title: "LED-Monster-Fang mit dem Raspberry Pi Pico"
date: 2025-10-12
draft: true
author: "ElecKids"
tags: ["Raspberry Pi Pico", "MicroPython", "LED", "Taster", "Spiel"]
categories: ["Projekte"]
summary: "Baue ein einfaches Fangspiel mit dem Raspberry Pi Pico, drei LEDs und zwei Tastern. Dabei lernst du, wie Eingaben, LEDs, Zufall und Programmabläufe zusammenarbeiten."
---

# LED-Monster-Fang mit dem Raspberry Pi Pico

In diesem Projekt baust du ein kleines Spiel mit drei LEDs und zwei Tastern. Du kannst den Schwierigkeitsgrad wechseln, den Fang starten und dir das Ergebnis über die LEDs anzeigen lassen. Das Projekt ist gut geeignet, um zu verstehen, wie ein Mikrocontroller Taster einliest, LEDs steuert und mit Zufallswerten arbeitet.

## Was du brauchst

Für das Projekt brauchst du:

* einen **Raspberry Pi Pico**
* **3 LEDs** in Rot, Gelb und Grün
* **2 Taster**
* **3 Widerstände mit 220 Ohm**
* ein **Steckbrett**
* **Jumper-Kabel**
* einen Computer mit **Thonny**

## Aufbau der Schaltung

Die LEDs werden jeweils über einen Vorwiderstand an einen GPIO-Pin angeschlossen. Die andere Seite der LED kommt an **GND**.

* rote LED an **GP16**
* gelbe LED an **GP17**
* grüne LED an **GP18**

Die Taster werden gegen **GND** geschaltet. Im Code nutzen wir dafür die internen Pull-Up-Widerstände des Pico.

* Start-Taster an **GP14**
* Modus-Taster an **GP15**

Wichtig:

* LEDs immer mit Widerstand verwenden
* auf die richtige Richtung der LED achten
* vor dem Umbauen den Pico vom USB trennen

## Der komplette Code

Speichere den folgenden Code als `main.py` auf deinem Pico:

```python
# ==== EINSTELLUNGEN ====
"""
LED-Monster-Fang – Raspberry Pi Pico (RP2040), MicroPython

Drei LEDs (rot/gelb/grün) und zwei Taster:
- Taster START: startet den Fangprozess (gelbe LED atmet/blinkt).
- Taster MODUS: wechselt zwischen leicht/mittel/schwer (Anzeige über LEDs).

Ergebnis:
- Erfolg -> grünes Schnellblinken
- Misserfolg -> rotes Blinken
"""

from machine import Pin, PWM
import utime as time
import urandom


# ==============================
#       KONSTANTEN / PARAMETER
# ==============================

USE_PWM = True                  # False: gelbe LED nur Blinken (ohne Dimmung)
DAUER_WURF_MS = 2500            # Dauer des "Wurfs" in Millisekunden

# Fangwahrscheinlichkeiten in Prozent (leicht / mittel / schwer)
TREFFER_LEICHT = 70
TREFFER_MITTEL = 40
TREFFER_SCHWER = 20

# Pinbelegung (kannst du anpassen)
PIN_ROT = 16        # GP16
PIN_GELB = 17       # GP17
PIN_GRUEN = 18      # GP18
PIN_START = 14      # Start-Taster (gegen GND, Pull-Up an)
PIN_MODUS = 15      # Modus-Taster (gegen GND, Pull-Up an)


# ==============================
#         HARDWARE-SETUP
# ==============================

led_rot = Pin(PIN_ROT, Pin.OUT, value=0)
led_gelb = Pin(PIN_GELB, Pin.OUT, value=0)
led_gruen = Pin(PIN_GRUEN, Pin.OUT, value=0)

taster_start = Pin(PIN_START, Pin.IN, Pin.PULL_UP)
taster_modus = Pin(PIN_MODUS, Pin.IN, Pin.PULL_UP)

# PWM nur für gelbe LED erforderlich
pwm_gelb = PWM(Pin(PIN_GELB))
pwm_gelb.freq(500)  # angenehme PWM-Frequenz (Flimmern vermeiden)

# Modi: 0=leicht (grün), 1=mittel (gelb), 2=schwer (rot)
modus = 0


# ==============================
#         HILFSFUNKTIONEN
# ==============================

def setze_modus_led():
    """
    Zeigt den aktuellen Modus über die farbige LED an.
    0 = grün (leicht), 1 = gelb (mittel), 2 = rot (schwer)
    """
    led_rot.value(0)
    led_gelb.value(0)
    led_gruen.value(0)

    if modus == 0:
        led_gruen.value(1)
    elif modus == 1:
        led_gelb.value(1)
    else:
        led_rot.value(1)


def taste_gedrueckt(pin):
    """
    Gibt True zurück, wenn die Taste (aktiv LOW) gedrückt ist.
    Beinhaltet eine einfache Entprellung.
    """
    if pin.value() == 0:
        time.sleep_ms(20)  # Entprellen
        return pin.value() == 0
    return False


def blinken(pin, anzahl, an_ms=100, aus_ms=100):
    """
    Lässt eine LED mehrfach blinken.
    :param pin: Pin-Objekt der LED
    :param anzahl: Anzahl der Blinkzyklen
    :param an_ms: Einschaltzeit pro Zyklus (ms)
    :param aus_ms: Ausschaltzeit pro Zyklus (ms)
    """
    for _ in range(anzahl):
        pin.value(1)
        time.sleep_ms(an_ms)
        pin.value(0)
        time.sleep_ms(aus_ms)


def wurf_animation():
    """
    Simuliert den Wurf:
    - bei USE_PWM=True: gelbe LED "atmet" (sanfte Helligkeitsänderung)
    - sonst: gelbe LED blinkt einfach
    """
    if USE_PWM:
        start = time.ticks_ms()
        periode_ms = 800  # Dauer eines hell->dunkel-Zyklus
        halb = periode_ms // 2

        while time.ticks_diff(time.ticks_ms(), start) < DAUER_WURF_MS:
            phase = time.ticks_diff(time.ticks_ms(), start) % periode_ms
            if phase <= halb:
                # hoch dimmen
                duty = int((phase / halb) * 65535)
            else:
                # runter dimmen
                duty = int(((periode_ms - phase) / halb) * 65535)
            pwm_gelb.duty_u16(duty)
            time.sleep_ms(5)

        pwm_gelb.duty_u16(0)
    else:
        ende = time.ticks_ms() + DAUER_WURF_MS
        while time.ticks_ms() < ende:
            led_gelb.value(1)
            time.sleep_ms(150)
            led_gelb.value(0)
            time.sleep_ms(150)


def fang_erfolg(treffer_wahrscheinlichkeit):
    """
    Entscheidet per Zufall, ob der Fang gelingt.
    :param treffer_wahrscheinlichkeit: 0..100 (Prozent)
    :return: True bei Erfolg, sonst False
    """
    # Zufallswert 0..99
    zufall = urandom.getrandbits(7) % 100
    return zufall < treffer_wahrscheinlichkeit


def zeige_ergebnis(erfolg):
    """
    Zeigt das Ergebnis an:
    - Erfolg: schnelles grünes Blinken
    - Misserfolg: rotes Blinken
    """
    if erfolg:
        blinken(led_gruen, anzahl=8, an_ms=60, aus_ms=60)
    else:
        blinken(led_rot, anzahl=8, an_ms=120, aus_ms=120)


# ==============================
#            START
# ==============================

setze_modus_led()
print(
    "Bereit! START drücken zum Fangen. "
    "MODUS zum Wechseln von leicht/mittel/schwer."
)


# ==============================
#         HAUPTSCHLEIFE
# ==============================

try:
    while True:
        # Modus wechseln?
        if taste_gedrueckt(taster_modus):
            modus = (modus + 1) % 3
            setze_modus_led()
            # warten bis losgelassen
            while taster_modus.value() == 0:
                time.sleep_ms(10)

        # Fang starten?
        if taste_gedrueckt(taster_start):
            # kurze Start-Animation (alle kurz an)
            led_rot.value(1)
            led_gelb.value(1)
            led_gruen.value(1)
            time.sleep_ms(200)
            led_rot.value(0)
            led_gelb.value(0)
            led_gruen.value(0)

            # Wurf abspielen
            wurf_animation()

            # Erfolg je nach Modus ermitteln
            if modus == 0:
                p = TREFFER_LEICHT
            elif modus == 1:
                p = TREFFER_MITTEL
            else:
                p = TREFFER_SCHWER

            erfolg = fang_erfolg(p)
            zeige_ergebnis(erfolg)

            # Modus-LED wieder anzeigen
            setze_modus_led()

            # warten bis Start losgelassen
            while taster_start.value() == 0:
                time.sleep_ms(10)

        time.sleep_ms(10)

except KeyboardInterrupt:
    # Aufräumen bei Abbruch (z. B. Strg+C über die REPL)
    pwm_gelb.deinit()
    led_rot.value(0)
    led_gelb.value(0)
    led_gruen.value(0)
```

## Wie der Code aufgebaut ist

Der Code besteht aus ein paar klaren Abschnitten:

* **Einstellungen:** Hier legst du Dauer, Trefferwahrscheinlichkeiten und Pins fest.
* **Hardware-Setup:** LEDs und Taster werden als Ein- oder Ausgänge eingerichtet.
* **Hilfsfunktionen:** Kleine Funktionen übernehmen einzelne Aufgaben wie Modus-Anzeige, Entprellen, Blinkmuster und Zufallsentscheidung.
* **Hauptschleife:** Der Pico prüft ständig, ob ein Taster gedrückt wurde, startet dann die Animation und zeigt das Ergebnis an.

Besonders wichtig sind diese Funktionen:

* `taste_gedrueckt(pin)` verhindert durch eine kurze Pause, dass ein Tastendruck mehrfach gezählt wird.
* `wurf_animation()` steuert die gelbe LED während des Fangversuchs.
* `fang_erfolg(...)` entscheidet per Zufall, ob der Versuch gelingt.
* `zeige_ergebnis(...)` gibt die Rückmeldung über die rote oder grüne LED.

## So startest du das Spiel

1. Baue die Schaltung auf.
2. Öffne Thonny.
3. Speichere den Code als `main.py` auf dem Pico.
4. Starte das Board.

Danach gilt:

* Mit dem **Modus-Taster** wechselst du zwischen leicht, mittel und schwer.
* Mit dem **Start-Taster** startest du einen Fangversuch.
* Die LEDs zeigen dir Modus und Ergebnis an.

## Was du verändern kannst

Wenn das Grundspiel läuft, kannst du einiges anpassen:

* `TREFFER_LEICHT`, `TREFFER_MITTEL`, `TREFFER_SCHWER` verändern
* `DAUER_WURF_MS` kürzer oder länger machen
* `USE_PWM = False` setzen, wenn die gelbe LED nur blinken soll
* andere Pins eintragen, wenn du die Schaltung anders aufgebaut hast

## Was du dabei lernst

Mit diesem Projekt übst du mehrere Grundlagen gleichzeitig:

* LEDs ansteuern
* Taster einlesen
* Pull-Up-Widerstände verstehen
* Zufallswerte verwenden
* Funktionen im Code sinnvoll aufteilen

## Sicherheit

Arbeite bei diesem Projekt nur mit dem Pico und einer passenden, kleinen Stromversorgung, zum Beispiel über **USB**.

Wichtig:

* keine Experimente mit Steckdosen oder Netzspannung
* keine unbekannten Spannungen direkt an GPIO-Pins anschließen
* den Pico vor dem Umbauen vom USB trennen
* LEDs immer mit Widerstand betreiben

Wenn das Spiel einmal läuft, hast du ein gutes Beispiel dafür, wie Programmcode und echte Hardware zusammenarbeiten.
