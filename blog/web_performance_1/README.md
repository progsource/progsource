Web-Performance #1: Ladezeiten mit Firebug messen
==========

Websites mit langen Ladezeiten werden nicht gerne besucht. Um die Performance zu verbessern, sollte man den
Ist-Zustand kennen. Dabei hilft das Firefox-AddOn Firebug.

Installation
-------------

Die Installation ist mit wenigen Klicks erledigt:
- auf die Firefox AddOn Seite gehen
- auf „Zu Firefox hinzufügen“ klicken
- bei der oben erscheinenden Leiste „Erlauben“ wählen
- ein paar Sekunden warten und auf „Installieren“ klicken

Nach einem Neustart von Firefox sieht man unten rechts das Firebug-Icon.

Stoppuhr oder Radarfalle?
-------------

Mit Klick auf das Firebug-Icon öffnet sich die Konsole.
Unter dem Punkt Netzwerk (muss ggf. zuvor aktiviert werden), stehen verschieden farbige Balken mit Angaben in
Millisekunden.

![Screenshot](https://github.com/progsource/progsource/raw/master/blog/web_performance_1/web_performance_001_screen.jpg)

Im Screenshot sieht man z. B., dass die aufgerufene Website insgesamt 215 ms geladen hat. Die Dateien werden
einzeln aufgeführt und so erkennt man, wo Verbesserungen notwendig sind.