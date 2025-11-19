---
layout: project
title: "Heizung mit Gehirm"
header_image: "https://www.froeling.com/es-es/wp-content/uploads/sites/11/2023/04/Newsletter_PlusX_0423.png"
summary: "Ich habe mein komplettes Heizsystem modernisiert: neuer Pelletkessel, 1000-Liter-Puffer, optimierte Solarthermie, Frischwassermodul und zwei getrennte Heizkreise. Der Kessel regelt nur sich selbst, Puffer und Solar. Die Heizkreise steuere ich mit eigener Sensorik und HomeAssistant, weil ein einziger Raumfühler und starre Logik einfach zu grob sind. Seit Sommer 2025 läuft das System effizient, sonnensynchron und endlich so, wie es zu meinem Haus passt."
chapters:
  - id: heizung-warmwasser
    title: "1. Warmwasser"
  - id: heizkreissteuerung
    title: "2. Heizkreissteuerung"
---
# Heizung – Projektübersicht

Pellets, Solarthermie und eine PV-Anlage. Eigentlich ein solides Setup, aber mein Pelletverbrauch ist in den letzten Jahren deutlich gestiegen. Zeit also, das komplette Heizsystem auf einen modernen Stand zu bringen und gleichzeitig meine Automatisierungspläne umzusetzen.

## Was erneuert wurde
- Umstieg vom 500-Liter-Boiler auf einen 1000-Liter-Pufferspeicher  
- Optimierung und hydraulische Einbindung der Solarthermie  
- Spülen und Neuabgleich der beiden Heizkreise  
- Neuer, kleiner dimensionierter Pelletkessel  
- Warmwasserbereitung über ein Frischwassermodul  
- Zwei vollständig getrennte Heizkreise (oben Fußbodenheizung, unten Heizkörper)

![Firma Veigl](https://bad-veigl.at/wp-content/uploads/2019/07/veigl-logo.png)
[https://bad-veigl.at/](https://bad-veigl.at/)

Damit das alles sinnvoll zusammenspielt, brauchte ich einen Installateur, der sowohl meine technischen Anforderungen als auch meine Automatisierungsziele versteht. Mit der Firma Veigl habe ich genau diesen Partner gefunden. Ich wusste vorher nicht, wie viele Funktionen ein moderner Puffer tatsächlich mitbringt – und warum man sie gezielt einsetzen sollte. Nach einem intensiven Austausch einigten wir uns auf eine klare Aufteilung:

## Rollenverteilung im System
- **Der Kessel** regelt sich selbst, den Puffer und die Solaranlage  
- **Die Heizkreise** (Mischer und Pumpen) regle ich selbst  
- **Warmwasser** übernimmt das Frischwassermodul

## Warum der Kessel die Heizkreise nicht steuern soll
Die Standardlogik eines Pelletkessels ist für ein echtes Smart-Home eher hinderlich:

1. **Ein einziger Raumfühler entscheidet für das ganze Haus.**  
   Wird dieser Raum warm, bleibt der Rest kalt – egal, was wirklich gebraucht wird.

2. **Sonneneinstrahlung wird ignoriert.**  
   Das System heizt früh morgens den Puffer hoch, obwohl in einer Stunde die Solarthermie liefern würde und die Sonne die Wohnräume aufwärmt.

3. **Keine vorausschauende Logik.**  
   Alles reagiert nur auf die aktuelle Innentemperatur, nicht auf Wetterprognosen.

Genau deshalb übernehmen jetzt eigene Sensoren, mehrere Heizkreisregelungen und HomeAssistant die Feinsteuerung. Der Kessel liefert die Wärme, aber *wie* und *wohin* sie verteilt wird, entscheidet ein intelligentes, fein abgestimmtes System.

## Ergebnis
Ende Sommer 2025 wurden der neue Kessel und der Pufferspeicher montiert. Die Solarthermie lädt den Puffer endlich effizient und sauber hoch. Die Basis steht – und in den folgenden Kapiteln zeige ich, wie die Heizkreisregelung, Warmwasserlogik und vorausschauende Steuerung zusammenspielen.


