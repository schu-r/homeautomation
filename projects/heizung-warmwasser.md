---
layout: project
title: "Warmwasser: Frischwassermodul & Zirkulation"
header_image: "https://schu-r.github.io/homeautomation/images/water-tap-1529179_1280.jpg"
summary: "Neue Zirkulationspumpe aktiviert sich automatisch, sobald das Frischwassermodul Warmwasser anfordert. HomeAssistant steuert das Ganze so, dass nach einer Minute die Leitungen heiß sind, ohne dauernd Energie zu verbraten. Warmwasser sofort, ohne Verschwendung."

---
# Warmwasser: Frischwassermodul & Zirkulation
Das Frischwassermodul liefert Warmwasser, sobald der Puffer genug Energie hat. In der Praxis reicht das aber nicht, wenn die Zirkulationsleitung schläft. Die war zwar schon beim Hausbau vorgesehen, aber ihre Pumpe war damals defekt und niemand kümmerte sich weiter darum.

## Problem
Wir haben extrem lange Leitungen und es dauert lange bis das Warme Wasser in alle Ecken kommt. Wir hatten schon eine Zirkulationspumpe aber di eist mit einer Zeitschltuhr gelaufen. Gewohnheiten verschieben sich. Braucht man warmes Wasser zum Kochen? Oder zum Abwaschen? Sonntag ist garantiert anders. Wann wird geduscht? Warum läuft die Pumpe obwohl keiner daheim ist. 

## Zirkulation
Jetzt arbeitet dort eine neue, kleine Zirkulationspumpe. Ein Shelly misst ihren Verbrauch, ein weiterer den des Frischwassermoduls. Sobald das Frischwassermodul Strom zieht (also jemand Warmwasser anfordert), schaltet HomeAssistant die Zirkulationspumpe für eine Minute ein, aber nur wenn sie in den letzten 30 Minuten nicht bereits lief.

## Ergebnis
Das Ergebnis: Man lässt den Wasserhahn kurz warm anlaufen, dreht ab, wartet eine Minute und hat dann sofort heißes Wasser. Perfekt zum Duschen, ohne Ressourcen zu verschwenden.

## Aber es geht noch besser
Ein Temperaturfühler zur Feinabstimmung wäre noch die nächste Ausbaustufe.
