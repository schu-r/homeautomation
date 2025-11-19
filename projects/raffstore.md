---
layout: project
title: "Raffstore – Schutz bei Wind und Blitz"
header_image: "https://cdn.pixabay.com/photo/2016/03/02/13/45/window-1232371_960_720.jpg"
summary: "Meine Raffstores reagieren jetzt selbst auf Gewitter: Mit [ESPHome](https://esphome.io/) und Blitzortung fahren sie hoch, bevor der Wind zuschlägt – lokal, Open Source und zuverlässig. #SmartHome #ESPHome #DIY #Blitzortung"
code_files:
  - name: "ESPHome Steuerung"
    path: "https://github.com/schu-r/homeautomation/blob/main/source/raffstore.yaml"
---
# Raffstore – Schutz bei Wind und Blitz

Wie schon bei den Dachflächenfenstern erwähnt, hatte die ursprüngliche Steuerung irgendwann ihren Geist aufgegeben – genauso wie der Elektriker. Zeit, das selbst in die Hand zu nehmen.  

Mit [ESPHome](https://esphome.io/) habe ich schnell eine neue Steuerung für die Raffstores gebaut – dreimal im Haus: Esszimmer, Schlafzimmer und Wohnzimmer.  

## Windschutz

Anfangs nutzte ich den Windsensor meiner Ecowitt-Wetterstation. Doch die Sommergewitter zeigen ein Problem: der Wind kommt oft **plötzlich und stark**, während die Raffstores ein paar Sekunden brauchen, um hochzufahren. Der Sensor schlägt nicht immer rechtzeitig an.  

## Blitzortung als Frühwarnsystem

Die Lösung: Blitzortung. Über eine HACS-Integration beziehe ich die Daten von [blitzortung.org](https://www.blitzortung.org/) – wenn in einem Umkreis von 10 km ein Blitz einschlägt, geht mein Haus automatisch in **Schutzzustand**:  

- Rollos fahren hoch  
- Dachflächenfenster schließen  

So reagieren die Raffstores nicht nur auf Wind, sondern auch auf herannahende Gewitter – bevor etwas passiert.  

Dieses Projekt verbindet einfache Hardware, intelligente Software und Open-Source-Ideen, um ein sicheres, selbstdenkendes Zuhause zu schaffen.

Der komplette Sourcecode ist links erhältlich!

