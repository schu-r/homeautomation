---
layout: project
title: "Kühlung im Sommer – Automatisch, clever, zuverlässig"
header_image: "https://cdn.pixabay.com/photo/2018/07/29/21/16/heat-3571032_1280.jpg"
summary: "Im Sommer kühlt mein Haus automatisch: Dachfenster, Raffstores, Lüftung und kleine Klimaanlage arbeiten zusammen – lokal, Open Source und zuverlässig. #SmartHome #HomeAutomation #ESPHome #DIY"
code_files:
  - name: "ESPHome Steuerung"
    path: "https://github.com/schu-r/homeautomation/blob/main/source/raffstore.yaml"
---
# Kühlung im Sommer – Automatisch, clever, zuverlässig

Nachdem die Dachflächenfenster und die Raffstores unter meiner Kontrolle sind, wollte ich auch im Sommer, dass mein Haus aktiv hilft, die Räume kühl zu halten – ohne dass ich selbst ständig Lüften oder Beschatten muss.  

## Morgendliche Kühlung

- Wenn der Wetterbericht hohe Temperaturen vorhersagt:  
  - Öffnen um **6:30 Uhr** die Dachfenster, um die kühle Morgenluft hereinzulassen.  
  - Gleichzeitig wird der **Raffstore im Esszimmer** geschlossen, um direkte Sonneneinstrahlung zu vermeiden.  

## Dynamische Anpassung

- Wenn es draußen wärmer wird als drinnen:  
  - Die Dachfenster schließen automatisch.  
  - Die Beschattung wird unten gehalten, um Hitze draußen zu halten.  
- Um **14:30 Uhr**: Esszimmerfenster öffnen (da ist schon Schatten), Schlafzimmer und Wohnzimmer schließen – passend zu Tageslicht, Sonne und Raumnutzung.  

## Intelligente Reaktion auf Bewohner

- Wird die Balkontür geöffnet, fahren die Raffstores hoch – jemand will raus, das Haus reagiert darauf.  
- Die **Wohnraumlüftung** kühlt die Räume, außer ein Fenster ist geöffnet.  
- Wenn es immer noch zu warm ist und die PV-Anlage viel Strom liefert, springt die **Klimaanlage** an.  
  - Es handelt sich nur um eine kleine Blockklimaanlage (ich bekomme maximal ~3 °C), aber der Unterschied zwischen 24 °C und 27 °C im Haus ist spürbar.  

## Alles im Blick

Alle Automationen berücksichtigen:  
- Wettervorhersage  
- Aktuelle Messwerte der Wetterstation  
- Raumtemperaturen  

Das Ergebnis: Selbst wenn ich in die Arbeit fahre, kümmert sich das Haus aktiv um Komfort und Schutz. Ich kann mich darauf verlassen, dass alles automatisch läuft – vom Lüften über Beschattung bis zur Kühlung.  

Dieses Projekt zeigt, wie kleine Automationen zusammenspielen, um ein intelligentes, selbstdenkendes Zuhause zu schaffen.

