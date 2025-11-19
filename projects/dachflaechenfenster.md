---
layout: project
title: "Dachflächenfenster – Eigenbau-Steuerung mit ESPHome"
header_image: "https://benz24.at/media/catalog/product/cache/bfcae97d2193cbe275913001b48435f4/1/1/115328-01-xxl_2.jpg"
summary: "Meine Dachflächenfenster steuere ich jetzt selbst: Mit [ESPHome](https://esphome.io/) und ein paar Relais öffnen und schließen sie bei Wind und Regen zuverlässig – ohne lange Leitern oder kaputte Motoren. Alles lokal, alles Open Source. #SmartHome #ESPHome #DIY"
code_files:
  - name: "ESPHome Steuerung"
    path: "https://github.com/schu-r/homeautomation/blob/main/source/velux-esszimmer.yaml"
---
# Dachflächenfenster – Eigenbau-Steuerung mit ESPHome

Beim Bau meines Hauses hat mein Elektriker eine Steuerung für die Dachflächenfenster (Velux) und die Raffstores (Schlotterer) installiert. Ein eigener Regensensor und Windsensor sollten die Fenster bei Regen schließen und die Rollos bei starkem Wind hochfahren.  

Funktioniert hat das nur mittelprächtig:  
- Der Regensensor musste ständig getauscht werden – mit einer **laaaaangen Leiter**.  
- Bei jedem Windstoß starteten die Rollomotoren der Dachflächenfenster, die nur durch Überlast stoppen. Nach einigen Jahren waren die Motoren (und mein Elektriker) durch.  

Der Velux-Service tauschte die Motoren aus, aber die Steuerung wollte ich nicht mehr übernehmen.  

## Meine Lösung mit ESPHome

Mit ESPHome habe ich ein eigenes Projekt aufgebaut, das die Fenster und die Beschattung über einfache Relais steuert. Die Beschaltung der Fenster war dabei knifflig:  

- Es gibt **drei Drähte**: Fenstermotor, Beschattungsmotor und eine gemeinsame Wurzel.  
- Um das Fenster zu öffnen: `+` an Fenster, `–` an Wurzel.  
- Zum Schließen: umgekehrt.  
- Bei der Beschattung genauso.  

Das Problem: an der Wurzel liegen beim Öffnen des Fensters und Schließen der Beschattung **gleichzeitig + und – an**. Kurzschlussgefahr!  

## Die Technik dahinter

Die Lösung:  
- Die Wurzel wird zwischen `+` und `–` umgeschaltet.  
- Der Ausgang der **Direction (Richtung)** geht auf den Schalter für Fenster und Beschattung.  
- So lässt sich jede `+/-`-Kombination einstellen, ohne einen Kurzschluss zu verursachen.  

Der komplette Sourcecode ist links erhältlich!

