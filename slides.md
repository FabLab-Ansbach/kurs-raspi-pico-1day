---
# try also 'default' to start simple
theme: neversink
color: green-light
title: Code Week 2025 - Programmieren mit dem Raspberry Pi Pico
info: FabLab Ansbach e.V. 2025
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
layout: cover
---
# Programmieren mit dem Raspbery Pi Pico
FabLab Ansbach e.V. in Kooperation mit dem Gründerzentrum ANsWERK, November 2025


---
layout: image-right
image: images/raspi.png
backgroundSize: 37em
---
# Der Raspberry Pi Pico
* Microcontroller Board
* RP2040 32-Bit Prozessor mit 133MHz
* 264 kByte RAM
* 2MByte Flash
* 26 GPIOs
---
layout: image-left
image: images/pico_nokia.webp
background-size: 40em
---
# Und wozu?
* (Heim-)Automatisierung / Smart-Home
  * Sensoren
  * Heizungssteuerung
* Robotik
  * Fahrzeuge
  * Roboterarm
* kleinere Elektronik-Projekte
* Prototyping
  
<small>Image credits: [Pavel's devlog](https://www.pavelp.cz/posts/eng-raspberry-pico-nokia-display/)</small>
---
---
# Programmierung

Sprachen:
* Micro-Python
* Circut-Python
* C/C++ (wie z.B. Arduino)

Wir nutzen eine grafische Oberfläche.

---
---
# Piper Make
Im Browser (Chromium): [make.playpiper.com](https://make.playpiper.com)

* Creative Mode auswählen
* "New Project" anklicken
* Auf das Projekt klicken
---
layout: section
---
# Grundlagen Elektronik

Wer hat in Physik gut aufgepasst?
---
layout: image-left
image: images/stromkreis_simple.webp
background-size: 30em
---
# Stromkreis

* Welche Bauteile gibt es in unserem Beispiel?
* Worauf müssen wir bei einem Stromkreis achten?
---
layout: two-cols-header
---
# Ohmsches Gesetz

::left::

$$
\begin{align*}
  U &= R \cdot{} I \\
  R &= \frac{U}{I} \\
  I &= \frac{U}{R} \\
  \\
  \text{U: Spannung} \\
  \text{I: Stromstärke} \\
  \text{R: Widerstand} \\
\end{align*}
$$

::right::

* Welche Spannung benötigt eine LED?
* Welche Stromstärke benötigt eine LED?

---
layout: image-right
image: images/led_aufbau.svg
background-size: 18em
---
# LED
* Plus / Minuspol darf nicht vertauscht werden
* niemals ohne Vorwiderstand betreiben
  * sonnst brennt die LED durch
---
layout: section
---
# Erstes Projekt

Eine LED blinken lassen
---
layout: image-right
image: images/pro1-raspi-led.png
background-size: contain
---
# Schaltung

## Bauteile
* Widerstand 330 Ohm
* Rote LED

* Pluspol der LED an GPIO1
* Minuspol über Widerstand auf GND

---
layout: image-left
image: images/pro1-programm-blink.png
background-size: 25em
---
# Programmierung
* **Start:** Beginn des Programms (wird immer benötigt)
* **Repeat forever:** Für immer wiederholen
* **turn pin _n_ _(ON|OFF)_:** Pin ein oder ausschalten
* **wait _n_ seconds:** n sekunden abwarten

### Tipps für Piper Make

* Die Blöcke sind links farblich sortiert
* Zum löschen Blöcke auf die Mülltonne ziehen
* Nicht verbundene Blöcke sind inaktiv

---
layout: statement
---

# Neue Aufgabe
## Eine zweite LED, die entgegengesetzt blinkt

---
layout: two-cols-header
---
# Wechselblinker

::left::
## Schaltung

* Wie muss die LED angeschlossen werden?
* Welchen Pin können wir verwenden?

::right::

## Programm

* Welche Blöcke müssen wir hinzufügen?
* Welche Werte müssen eingetragen werden?
  * Wovon hängen die Werte ab?

---
layout: section
---

# Eingabe

Die LED soll mittels Taster gesteuert werden

---
layout: image-right
image: images/pro3-raspi-led-taster.png
background-size: contain
---
# Schaltung

* LED mit Widerstand an GPIO-14 und GND
* Taster an GPIO-15 und +3.3V

**Fragen**
* Widerstand vor der LED, macht das etwas aus?
* Was passiert, wenn der Taster gedrückt wird?

---
layout: image-left
image: images/pro3-programm-siple.png
background-size: 20em
---
# Programm

* **If ... do ...  else ...** -> Wenn die Bedingung zutrifft, tue etwas. Sonst tue etwas anderes
  * Bedingung muss einen Wahrheitswert (boolschen Wert) zurückgeben
* **is pin _n_ HIGHT when pulled DOWN** 
  * **HIGH** 3.3V liegen an
  * **LOW**  keine Spannung liegt an
  * **pulled DOWN** Pin wird über einen hohen Widerstand auf GND gezogen

---
layout: statement
---

# Aufgabe
## Die LED soll nach dem Tastendruck noch 5 Sekunden leuchten

---
layout: default
---

# "Treppenhausschaltung"
* Welchen Block müssen wir hinzufügen?
* Welche(n) Wert(e) müssen wir eintragen

**Zusatzfrage** Was passiert, wenn wir den Taster gedrückt lassen (und warum)?

---
layout: statement
---
# Neues Problem

<br/>

## Kilian hat sein Fahrrad an den Lichtschalter gelehnt und das Licht geht nicht mehr aus. 

<br/>

## Wie können wir ihm helfen?

---
layout: statement
---
# Mittagspause

<br/>

## 30 Minuten

---
layout: statement
---
# Nicht mehr ganz so neues Problem

<br/>

## Kilian hat sein Fahrrad an den Lichtschalter gelehnt und das Licht geht nicht mehr aus. 

<br/>

## Wie können wir ihm helfen?
---
layout: section
---

# Einführung Variablen

--- 
layout: image-left
image: images/varia-drawers.png
background-size: 22em
---
# Variablen

* Kennt man aus der Mathematik
* Platzhalter für Werte
* Wie eine Schublade
  * Ich lege mir einen Wert in die Schublade und nutze ihn später
* Verschiedene Datentypen
  * Bool(ean)
  * String
  * Integer/Double
  * Float
  * u.v.m.

---
layout: image-right
image: images/varia-blocks.png
background-size: 28em
---
# Variablen in Piper Make

## Neue Variable erstellen:
* Variables -> Create Variable
* Namen eingeben und OK klicken

## Blöcke für jede Variable
* **Set _x_ to _y_** ?
* **change _x_ by _y_** ?
* **_x_** Wert einsetzen

---
layout: image-right
image: images/p4-varia-simple.png
background-size: 25em
---
# Einfaches Programm mit Variablen

* Tasterstatus wird in Variable abgelegt
* Anhand dieser Variable wird entschieden, ob die Lampe ein/aus geschalten wird

**Zusatzfrage:** Was passiert, wenn wir die Variable auf 2 setzen statt auf 0?

---
layout: statement
---
# Und wie lösen Variablen jetzt unser Problem?

---
layout: image-right
image: images/p5-treppenhaus-single.png
background-size: contain
---
# Verbesserte Treppenhausschaltung

* Wenn Taster HIGH ist **und** letzter Wert 0 war 
  * letzer Wert = 1
  * LED für fünf Sekunden einschalten
* ansonsten
  * Wenn Taster LOW ist
    * letzter Wert = 0

**Zusatzfragen:**
* Wo ist der Fehler?

---
layout: statement
---
# Zusatzaufgabe

<br/>

## Zwei Taster, einer für 5 Sekunden und einer für 10 Sekunden

<br/>

## Aber die LED wird nur an einer Stelle angesteuert

---
# Keep last slide
layout: default
---
# Credits

**Erstellt für den FabLab Ansbach e.V., 2025** \
**Letzte Aktualisierung:** 6. November 2025

Fragen, Anmerkungen, Beschwerden oder Kuchenrezepte an [info@fablab-ansbach.de](mailto:info@fablab-ansbach.de)

Slides created with [SliDev (Slides for Developers)](https://sli.dev)