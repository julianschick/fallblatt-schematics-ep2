# Fallblattanzeiger der S-Bahn-Berlin

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
