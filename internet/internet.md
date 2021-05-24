# **Internet**
# Einführung
Vor Internet: Leitungsvermittlung zwischen Sender und Empfänger

Im Internet: Paketvermittlung zwischen Sender und Empfänger

Paketvermittlung hat eine höhere Kapazität, weil mehrere mögliche Pfade bestehen

**Arten von Netzen**
- Mobilnetze: 3G, 4G, 5G. Geräte verbinden sich über Funk mit Basis-Stationen
- Firmennetze/Lokale Netzwerke
- Internet Infrastrukturen von Internet Service Providers. Es gibt globale ISP (Telekom) und lokale ISP (Kabel BW)

**Bestandteile des Internet**
- Router
- Server
- WLAN-Access-Point
- Endsysteme
- Basisstationen für Mobilfunk
- Switch

**Protokolle zum Austausch**
- TCP-IP (SYN, SYN-ACK, ACK 3-Way Handshake)

**Zugangsnetze**
- WLAN
- ETHERNER
- DSL

**DSL**

DSL nutz größeren Frequenzbereich als der analoge Telefonanschluss, darum geringere Reichweite und höhere Datenrate. Bei ADSL  wird der für die Festnetztelefonie verwendete Frequenzbereich ausgespart, sodass DSL und Telefon gleichzeitig funktionieren. Von der Vermittlungsstelle wird dann per Glaßfaser an das Backbone übertragen.

**CMTS Cable Modem Termination System**

Das CMTS kann Daten vom Endkunden an das Internet weiter-routen. Weil upstream-ressourcen beschränkt sind, wird hier durch einen Scheduler gefiltert.

**Fiber to the Home/Building**

Bei Einfamilienhäusern ist die Anschlussdose immer hinter der Hauseinführung. Ein Anwedungsspezifisches Gerät (ASG) mit kombiniertem Integrated Access Device (IAD, hat Buchsen für verschiedene Geräte) speichert die Zugangsdaten des Kunden und wird von Provider bereitgestellt. Bei Heimvernetzungen muss das Kabel biegsam sein (Standard ITU-T-G.657B).

**Routing-Algorithmen**
- Bei Link State Routing Protokollen kennt jeder Router die gesamte Topologie
- Bei Distanzvektor/Pfadvektor Algorithmen teilen sich die Router nur mit, wie gut sie an verschiedene Zielknoten angebunden sind.

**Paketvermittlung**
- Bei Store-and-Forward werden die Pakete auf Fehler überprüft und nur intakte Pakete weitergeleitet. Warteschlange bei voller Leitung. Langsamer
- Bei Cut-Through werden Pakete weitergeleitet bevor das ganze Paket angekommen ist. Schneller

**Internet-Schichtenmodell**

Bitübertragungsschicht -> Sicherungsschicht -> Netzwerkschicht -> Transportschicht -> (Kommunikationssteuerungsschicht) -> (Darstellungsschicht) -> Anwendungsschicht

**TCP Transmission Control Protocol**
- Baut eine Verbindung zwischen 2 Endpunkten her
- Baut auf IP auf
- Datenverluste werden erkannt und automatisch behoben

## Kapitel 2
**Websocket**

Websockets sind kompatibel aber verschieden zu HTTP und sind voll-duplex. Sie erlauben Verbindungen mit weniger overhead als HTTP polling und erlaubt real time Datenübertragung. Server und Client können über eine offene Verbindung länger kommunizieren.

**Netzanforderungen**

Unterschiedliche Services haben unterschiedliche Anforderungen, vor allem in Sachen Datenverlust, Durchsatz und Echtzeit. Verbindungen sollten stabil sein und zuverlässig getrennt werden.

### HTTP Hypertext Transfer Protocol

Zustandsloses Protokoll zur Übertragung von Daten auf der Anwendungsschicht auf TCP, vor allem für Webseiten. HTTPS ist zusätzlich noch verschlüsselt. Sitzungsinformationen müssen jedes Mal mitgeführt werden, zum Beispiel als Cookie in den Header-Informationen. 

```
GET /infotext.html HTTP/1.1
Host: www.example.com
```

**HTTP-Anfragemethoden**
- GET: Gebräuchlichste Methode. Fragt eine Ressource beim Server ab. Kann extra Inhalte zum Server übertragen, allerdings sollen GET-Anfragen sonst keine Auswirkungen haben.
- POST: Schickt große Mengen an Daten zur weiteren Verarbeitung zum Server. POST-Daten werden nicht zwischengespeichert.
- HEAD: Server schickt den gleichen HTTP-Header wie bei GET, aber keinen Dateiinhalt. Überprüfen der Gültigkeit einer Datei.
- PUT: PUT dient zum Hochladen einer Datei zu einem Webserver. Bestehende Ressourcen werden überschrieben.
- PATCH: Ändert ein Dokument statt es wie bei PUT komplett zu ersetzen.
- DELETE: Löscht Ressource auf dem Server
- TRACE: Liefert Anfrage zurück wie sie gesendet wurde
- OPTIONS: Liste der vom Server unterstützten Methoden und Merkmale
- CONNECT: Erlaubt Proxyservern einen SSL-Tunnel aufzubauen.

**Aufbau HTTP-Nachricht**
- Startline: Enthält die verwendete Methode
- Header: Enthält Paare. Enthält Informationen zum Host-System, Cookies und welche Sprachen der Client als Antwort akzeptiert.
- Body: Enthält die übertragenen Daten
- Antwort-Start-Line: HTTP-Version und Status Code
- Antwort-Header: Informationen zum Server-System
- Antwort-Body: Enthält die gewünschten Daten

**Cookies**
- Werden vom Webserver geschickt oder von Javascript erzeugt. Kann bei wiederholtem Aufrufen der Seite ausgelesen werden (SessionID, Speichern eines Logins oder Warenkorb oder Tracking).

**Browser-Cache**
speichert bereits abgerufene Ressourcen und beschleunigt so das Laden einer Seite. Es kann zusätzlich noch in Firmennetzen oder anderen Orten im Internet gecacht werden.

### FTP File Transfer Protocol
Zustandsbehaftetes Netzwerkprotokoll zur Übertragung von Dateien. Separate Verbindungen für Steuerung und Datenübertragung. Eine FTP-Sitzung beginnt, indem vom Client zum Control Port des Servers (Standard-Port 21) eine TCP-Verbindung für Befehle aufgebaut wird. Der Server antwortet immer mit einem Statuscode. Die meisten Befehle sind erst nach Authentifizierung zulässig. Die meisten Browser haben einen eingebauten FTP Client

### E-Mail
Asynchrones Kommunikationsmedium: Der Sender versendet die Nachricht unabhängig davon, ob der Empfänger sie sofort entgegennehmen kann oder nicht.

**Ablauf des Versendens**
- Client schickt eine SMTP-Anfrage an den Quell-Mailserver (a.org)
- Mailserver erfragt "Mail eXchanger record" beim DNS-Server (ns.b.com)
- DNS-Server liefert MX-Record mit Prioritätsliste von Ziel-Mailservern (b.com)
- a.org sendet die E-Mail nacheinander an alle b.com, bis einer die E-Mail annimmt
- Der Ziel-Mailserver speichert die E-Mail, bis der Nutzer seine E-Mails per POP3 abholt

**Protokolle**
- SMTP: Protokoll zum Mailversand und Transport
- POP3: Abrufen von E-Mails am Mailserver
- IMAP: Zugreifen auf Postfächer und verwalten von E-Mails
- SMAP: Weiterentwicklung vom IMAP im experiementellen Stadium
