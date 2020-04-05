# Fallblattanzeiger der S-Bahn-Berlin

<img src="images/steuerplatine.jpg" width="200" align="right" />

Platine zur Ansteuerung von 3 Fallblattmodulen (typischerweise Linie, Fahrtziel und Laufweg) mit einem ESP32-Development-Board. Gedacht für Module der *Epoche 2* (siehe [Wikipedia](https://de.wikipedia.org/wiki/Fallblattanzeige)) und ein Eingriff in die Platine der Module ist erforderlich. Der Synchronmotor wird nicht über die Transistorschaltung auf der Platine des Fallblattmoduls gesteuert. Vielmehr wird die Platine so überbrückt, dass der Microcontroller direkten Zugriff auf die Hall-Sensoren hat und über einen eigenen Triac den Synchronmotor direkt steuert.

Zur Stromversorgung wird die Platine an 230 V Netzspannung angeschlossen. Ein großer Trafo, der nicht auf der Platine verbaut wird, sondern über Schraubklemmen angeschlossen werden kann, spannt auf 48 V AC herunter. Damit werden die Synchronmotoren der Module betrieben. Ein weiterer Trafo, der auf der Platine montiert wird, spannt auf 9 V AC herunter, die gleichgerichtet und mit einem Linearregler auf Logik-Betriebsspannung 3,3 V gebracht werden.

## Modifikationen an der Platine des Fallblattmoduls

Der unveränderte Schaltplan der Platine ist als [KiCad-Schaltplan](images/schaltplan-modul/schaltplan-modul.sch) und [PDF](images/schaltplan-modul.pdf) im Repo abgelegt. Soweit möglich, sind Typenbezeichnung der Bauteile mit angegeben, diese sind allerdings mit Google heute nur schwer zu deuten.

Die folgenden Pläne und Bilder zeigen die notwendigen Modifikationen. Einmal wird Pin 5 des Anschlusssteckers von Pin 10 des Anschlusssteckers getrennt, indem ein Widerstand und eine Diode entfernt werden. Außerdem wird Pin 10 direkt mit dem Flap-Hall-Sensor verbunden, durch setzen einer Brücke auf der Platine, wo schon zwei vorbereitete Pads nebeneinander liegen (violette Brücke). Zuletzt wird der Triac entfernt und überbrückt (blaue Brücke).

<img src="images/schaltplan-modul-modifikationen.jpg" alt="Schaltplan mit Modifikationen" />

## Teileliste (unvollständig)

* ESP32-Development-Board (es gibt 2 Varianten bei eBay, für diese Platine wird die üblichere mit 15 Pins je Reihe und GND/VCC  nebeneinander, nicht auf gegenüberliegenden Pins benötigt; diese wird oft unter dem Namen _DEVKITV1_ oder _NodeMCU_ verkauft). Das folgende Pinout ist das korrekte:

<img src="images/esp32-pinout.jpg" alt="ESP32-Pinout" width="300" />

* Netztrafo 48 V (eigentlich 42 V) mit Wumms, mind. 200 mA pro Modul, der Synchronmotor zieht so viel. Zum Beispiel [der hier](https://www.voelkner.de/products/1011896/TRU-Components-TC-RKT30-2X24-Ringkerntransformator-1-x-230V-2-x-24V-30-VA-625mA.html)
* [Transformator 9V _Block VB 2,0/1/9_](https://www.reichelt.de/printtrafo-2-va-9-v-222-ma-rm-20-mm-ei-30-15-5-109-p27328.html)
* Varistor (mind. 300 V)
* [Brückengleichrichter Rund, Wechselstrompins gegenüber, RM 5mm](https://www.reichelt.de/brueckengleichrichter-100-v-1-5-a-b70c1500rund-p181713.html)
* 4 x Schraubklemme 2-polig RM 7,5mm
* [Spannungsregler 3,3V Formfaktor TO-220 _STM LD1117 V33C_](https://www.reichelt.de/ldo-regler-fest-3-3-v-to-220-ld1117-v33c-p200891.html?)
* Elektrolytkondensator 470u, RM 5mm
* Elektrolytkondensator 10u, RM 2mm
* Kondensator 100n, RM 2,5mm
