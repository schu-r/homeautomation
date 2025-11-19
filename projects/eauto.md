---
layout: project
title: "E-Auto Laden mit PV-Überschuss"
header_image: "https://cdn.motor1.com/images/mgl/YA3nbq/s3/hyundai-inster-2024-das-exterieur.jpg"
summary: "Mein Hyundai Inster lädt nur mit Sonnenstrom: HomeAssistant steuert den go-eCharger, berechnet den echten PV-Überschuss und hält alles stabil. Kein Netzbezug, klare Limits, volle Kontrolle. #verbrauchsoptimierung #pv #emobilität"
code_files:
  - name: "GO-E Automation"
    path: "https://github.com/schu-r/homeautomation/blob/main/source/eauto-setmaxload.yaml"
  - name: "Max A 1 Phasig"
    path: "https://github.com/schu-r/homeautomation/blob/main/source/eauto-maxA-1P-laden.yaml"
  - name: "Max A 3 Phasig"
    path: "https://github.com/schu-r/homeautomation/blob/main/source/eauto-maxA-3P-laden.yaml"
---
# E-Auto Laden mit PV-Überschuss

Im Juni ist ein Hyundai Inster bei uns eingezogen. Und wenn schon ein E-Auto, dann soll er sich bitte aus meiner PV-Anlage bedienen statt aus dem Netz. Der billigste Strom ist schließlich der, den ich selbst erzeuge.

Über den Makerspace habe ich einen E-Auto-Freak kennengelernt, der einen nagelneuen **go-eCharger** übrig hatte. Perfekt, denn HomeAssistant kann diese Wallbox direkt steuern: Ladestrom in Ampere, einphasig oder dreiphasig, alles programmierbar.

## Wie viel Strom darf er ziehen?

Das Laden sollte natürlich nur den **tatsächlichen PV-Überschuss** verwenden. Dafür messe ich am Stromzähler, wie viel Leistung gerade aus dem Haus rausgeht.  
HomeAssistant berechnet dann:

- Wie viele Ampere könnte der Charger ziehen, ohne dass ich Netzstrom einkaufe?  
- Reicht es für einphasig?  
- Reicht es vielleicht für dreiphasig?  
- Oder lieber doch nichts, weil gerade der Backofen glaubt, er wäre ein Fusionreaktor?

Sobald der Charger aber zu laden beginnt, geht plötzlich kein Strom mehr ins Netz. Bedeutet: Die *Überschussmessung* wäre falsch.  
Also rechne ich die **Leistung des Chargers wieder drauf**, damit der Algorithmus weiß, wie viel echte Sonnenenergie übrig bleibt.

Die Wolken am Himmel oder auch Backöfen und Herdplatten lassen den Verbrauch sehr schwanken. Darum wird der **PV-Überschuss als 1-Minuten-Minimalwert** geglättet. Der Lader bleibt dadurch stabil unter der Kurve und schaltet nicht dauernd ein und aus.

## Funktionen, die den Alltag leichter machen

Ein paar Komfortfeatures mussten natürlich auch sein:

- „Wenn’s sein muss, kauf halt 1, 2, 3,... kW zu.“  
  Dank meiner Energiegemeinschaft ist das sogar halbwegs sinnvoll.

- „Lade nur bis 80%.“  
  Klingt einfach, ist aber tricky: Die Verbindung zu meinem Auto ist so langsam, dass ich den Batteriestand vorher speichern musste.  
  Den Rest rechne ich über die Ladung des Chargers selbst hoch.

- „Ladefreigabe nur für mich.“  
  Falls jemand glaubt, er könne mal schnell sein Auto anstecken, während ich schlafe: nein. Und wenn, dann bekommt er nur PV Strom. 

## Ergebnis

Mein Auto lädt jetzt exakt so, wie ich es möchte:  
PV-optimiert, elegant geglättet und ohne Netzstrom, solange es irgendwie möglich ist. Auch wenn die Auto-API manchmal im Schneckentempo antwortet.


Der Sourcecode (soweit ich es expoertieren konnte) ist links erhältlich!

