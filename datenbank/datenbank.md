# **Datenbanksysteme (Martin Hulin)**


- [**Datenbanksysteme (Martin Hulin)**](#datenbanksysteme-martin-hulin)
- [Einführung](#einführung)
  - [Datenbankentypen](#datenbankentypen)
    - [Strukturierte Datenbanken](#strukturierte-datenbanken)
    - [Volltextdatenbanken](#volltextdatenbanken)
    - [Multimedia-Datenbanken](#multimedia-datenbanken)
  - [Externe Sichten](#externe-sichten)
  - [Benutzergruppen](#benutzergruppen)
# Einführung

Datenbanken sind ein zentraler Speicherort für Daten, die einfach abgerufen werden können. 

Beispiel: Katalog der Hochschulbib oder Suche nach Lehrveranstaltungen im LSF

Eigenschaften von Datenbanken:
- dauerhafte Speicherung (persistent)
- logische Beziehungen zwischen den Daten
- Die Daten haben einen bestimmten Zweck und stellen einen Ausschnitt/Abstraktion der realen Welt dar (Miniwelt)

Speichern und Verarbeiten der Daten mit Datenbankmanagementsystem (DBMS):
- Eingabe
- Ändern
- Löschen
- Suchen von Daten,
- Strukturdefinition

DBMS können auf mehrere Datenquellen zugreifen und Anfragen von mehreren Programmen ausführen.

## Datenbankentypen

### Strukturierte Datenbanken
Von jeden Objekt werden ganz bestimmte Daten gespeichert, wie in einer großen Tabelle. Nur Textdaten oder Zahlen.
- Hierarchische Datenbanken (alt)
- Netzwerkdatenbanken (alt)
- **Relationale Datenbanken** (z. B. SQL)
- Objektorientierte Datenbanken (Für Objektorientierte Programmierung, hat sich nicht durchgesetzt
- **NoSQL Datenbanken**
  - Dokumenten Datenbanken
  - Key-Value Stores
  - Graphen-Datenbanken
  - Spaltenorientierte Datenbanken

### Volltextdatenbanken
Jedes Text-Objekt besteht aus unstrukturiertem Prosatext und kann ganz unterschiedliche Daten beinhalten. Kein fester Platz für Daten. (Gerichtsurteile)

### Multimedia-Datenbanken
- Sowohl strukturierte als auch unstrukturierte Daten
- Unstrukturierte Daten können Text, Bild, Ton, ... sein

**Weitere Aufgaben eines DBMS**
- Verwaltung von Zugriffsrechten
- Aufbereitung von Daten
- Sicherheit vor Datenverlust
- Vermeiden von Inkonsistenzen
- Effiziente Suche von Daten

## Externe Sichten
Große Datenbanken werden unübersichtlich, deshalb dürfen verschiedene Benutzergruppen nur bestimmte Ausschnitte sehen. Gesamte Konzeptsicht bleibt verborgen.

## Benutzergruppen
**DB-Entwickler**
Entwerfen die Struktur der DB und setzen es im DBMS um

**DB-Administrator**
Verwaltet die DB, führt Strukturänderungen durch und installiert neue Versionen, Tools...

**DB-Programmierer**
Programmieren Programme und Tools, die auf die Datenbank zugreifen

**DB-Nutzer**
Trägt Daten ein, löscht/ändert Daten, stellt Abfragen.
- Naiver Zugriff: Immer ähnliche Zugriffe
- Seltener Zugriff, unterschiedlichste Abfragen (Manager)
- Komplexe Zugriffe, genaue Kenntnis der DB


