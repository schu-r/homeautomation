---
layout: project
title: "Heizkreissteuerung aber richtig"
header_image: "https://schu-r.github.io/homeautomation/images/1084px-Sindelfingen_Haus_&_Energie_2018_by-RaBoe_056.jpg"
summary: "Meine Heizkreise laufen nicht mehr nach dem Motto „ein Raumfühler für alle“, sondern über eine eigene ESPHome-Regelung mit PID, DS18B20, DHT22, Zigbee-Ventilen und HomeAssistant. Jeder Stock bekommt Wärme nach echtem Bedarf, Sonneneinstrahlung und Holzofen inklusive. Präzise, zonenbasiert, komplett lokal. #SmartHome #HomeAssistant #ESPhome #Heiztechnik #DIYTech #OpenSource #Automation"
code_files:
  - name: "ESPHome Heizkreise"
    path: "https://github.com/schu-r/homeautomation/blob/main/source/heizkreis-esphome.yaml"
  - name: "Stockwerktemperatur"
    path: "https://github.com/schu-r/homeautomation/blob/main/source/heizkreis-temperatur.jinja"
  - name: "Vorlauftemperatur"
    path: "https://github.com/schu-r/homeautomation/blob/main/source/heizkreis-vorlauf.yaml"
---
# Heizkreissteuerung  
Die neue Pelletheizung bekam einen Pufferspeicher, doch die Regelung für die beiden Heizkreise habe ich sofort an mich gerissen. 

Die eigentliche Heizung darf tun, was Heizungen eben tun. Aber die beiden Heizkreise wollte ich selbst kontrollieren, denn die Standardlösung mit einem einzigen Raumfühler pro Stockwerk ist bei unserem Haus schlicht unbrauchbar. Oben heizt die Sonne das halbe Stockwerk gratis auf, unten sorgt der Holzofen meiner Schwiegermutter für Verwirrung bei der Heizung. Eine zentrale Messung hätte völlig falsche Signale geliefert.

## Problem
Alles auf einen Raum bezogen ist komplett falsch. Aber die Heizung hat keine andere Möglichkeit. Zusätzlich weiiß ich nicht, wie viel Wärme gebraucht wird. Warum wird der Heizkörper nicht warm obwohl es überall kalt ist? Warum heizt die Heizung obwol die Sonne reinknallt? Die Heizung soll steuern wie viel Wärme wir brauchen und zwar nicht nach Zeitplan sondern nach anwesenheit. Ein schönes, warmes Haus, aber wenn keiner daheim ist, werfe ich die Pellets beim Fenster raus.

## ESPHome Übernimmt  
Also habe ich die komplette Regelung ausgelagert: Ein ESP32 mit ESPHome übernimmt jeden Mischer und die jeweilige Pumpe. Vor- und Rücklauf werden über DS18B20 überwacht. Die Regler laufen lokal am ESP über einen PI-Algorithmus, der feinfühlig auf Änderungen reagiert und den Mischer exakt dort hält, wo die Temperatur hinkommen soll. Die Vorgabewerte und die tatsächliche Heizanforderung liefert HomeAssistant, doch die schnelle, saubere Regelarbeit passiert direkt am Gerät.

## Pumpe mit PWM
Die Pumpen laufen nicht stumpf konstant. Sie orientieren sich an der Temperaturdifferenz zwischen Vor- und Rücklauf. Wird viel Wärme abgenommen, steigt die Pumpendrehzahl, sinkt der Bedarf, fährt sie wieder herunter. Dadurch reagiert der Heizkreis schneller, effizienter und schont obendrein Material und Strom.
*VORSICHT* Pumpen haben komosche PWM 0% = 100% Drehzal und umgekehert, Aber das ist je nach Pumpe unterschiedlich und kann sogar konfiguriert werden (nicht bei allen) PWM-Heizsteuereung und PWM-Solarsteuerung. Anfangs bekam ich nur Warmwasser wenn ich die Pumpen auf 1% runterregelte. Das War verwirrend. 

## Raumtemperatur messen
Im Obergeschoss habe ich das System schon länger vorbereitet: In vielen Räumen messen DHT22-Module die Temperatur, ein eigener ESP steuert die Ventile der Fußbodenheizung. Dadurch bekommt der Heizkreis eine echte, zonenbasierte Rückmeldung über den tatsächlichen Bedarf.  
Im Untergeschoss war das nachrüstmäßig komplizierter, deshalb kamen Zigbee-Heizkörperventile von Sonoff dazu. Sie regeln jeden Raum einzeln, und ergänzende Shelly H&T sorgen dafür, dass die Regelung sich nicht auf die Ventiltemperatur verlässt, sondern wirklich den Raum erfasst.

Beide Heizkreise berechnen eine Durchschnittstemperatur, aber dynamisch: Räume, die durch externe Wärmequellen (wie den berühmten Holzofen) viel zu heiß werden, werden bei der Berechnung ignoriert. So beeinflusst ein überheizter Raum nicht den Rest des Stockwerks.

## Solltemperatur für Vorlauf
Belibt nur noch die Temperatur für den Vorlauf zu bestimmen. Der wird einerseits über die Außentemperatur bestimmt aber auch mit der Differrenz wischen ist und Soll. Je mehr abweichung desto wärmer das System, damit es richtig einheizt.

## Anwesenheits und Zeibasierte Steuereung
Wenn in der Früh alle in die Arbeit und Schule fahren, den ganzen Tag keiner daheim ist, dann braucht die Heizung nicht zu arbeiten. Also eine Absenktemperatur einstellen. In der Früh wird entschieden ob jemand daheim ist und dann die richtige Temperatur eingestellt. Sollte jemand heimkommen wird natürlich sofort hochgefahren. Dabei geht es um eine Temperaturdifferenz von 1.5°C - Also nichts Weltbewegendes. Im Unteren Stock passiert es immer wieder das alle für ein halben Tag wegfahren. Das aber nicht zu fixen Zeiten. Ist länger keiner daheim, dann runter mit der Temperatur. Natürlich gibt es noch die normale Nachtabsenkung. 

Am Ende entsteht ein System, das nicht schaltet wie ein dummer Zentralthermostat, sondern wie ein fein abgestimmtes Netz aus Sensoren, Regelungstechnik und Logik. Die Heizung liefert Wärme, aber die Verteilung und Dosierung übernimmt eine selbst entwickelte Steuerung, die genau weiß, wer gerade wie viel braucht.

## Update #1
Neuer Modus: *PAUSE*: Die Pumpe wird sonst zwischen 50% und 100% gesteuert. Im Pause Modus regelt er auf 1% runter. Warum? Weil mir der Heizkreis sonst den Puffer ausleert und der Kessel in einen kalter Puffer reintransportiert. Das mag er nicht. Also wird auf Pause geschaltet wenn der Puffer 3° nidriger als die gewünschte Vorlauftemperatur ist.  

## Update #2
Bis jetzt lief alles prima, aber auf einmal versagte eine Pumpe. Egal was ich in der PWM einstellte, die Pumpe willte nicht. DAzu muss man sagen habe ich das PWM Signal des ESP mit einer Brücke (L298N) auf 5V raufgeboostet. Wenn der aber keine Spannug hatte liefe es wieder. Also mal die Pumpe direkt am ESP angeschlossen und siehe da das Datenblatt hatte gelogen mit 3.3V geht es auch. 
Tja bis ich merkte, dass auch die zweite Pumpe komische sachen machte und die Brücke recht heiß lief. 
Die Untersuchung ergab, dass sich eine Ader gelöst hatte und die beiden Ausgänge kurz geschlossen hatte. Darum mwollte die erste Pumpe nicht mehr. Die 2. Pumpe ging dann, aber wenn am freien eingang der 2. pumpe ein Signal empfangen wurde kam der Kurzschkuss wieder zu tragen.
*Lösung*: Brucke wurde ausgetauscht (mit Pins und Stecker versehen) und den Kabeln habe ich noch einen 1.5K Widerstand gegeben so dass das ganze kurzschlussfest wird. - Tja man lernt ....


Der Sourcecode (soweit ich es expoertieren konnte) ist links erhältlich!

