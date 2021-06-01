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

## Multimedia Netzwerke
Quality of Service: Netzwerk liefert die Dienstgüte, welche für die jeweilige Anwendung notwendig ist.
- Zuverlässiges/schnelles verbinden und trennen
- Probleme beim Verbindungsaufbau sollen schnellstmöglich mitgeteilt werden
- Stabile, vollständige, fehlerfreie und möglichst originalgetreue Übertragung
- Geringe Wartezeiten
- Abrechnung der Kommunikation sollte dem korrekten Zeit- und Datenumfang entsprechen.

- Latenzzeit: Verzögerung der Ende-zu-Ende Übertragung
- Jitter: Abweichung der Latenzzeit vom Mittelwert
- Paketverlustrate: Anteil der verlorenen/verspäteten Pakete
- Durchsatz: Übertragene Datenmenge pro Zeiteinheit

**Media Streaming**
- von gespeicherten Medien, Live-Medien oder Interaktiv
- Nur temporäre Kopie beim Endnutzer
- Verzügerung und Jitter (Verzögerungsschwankung) wichtige Kriterien
- Tolerant gegenüber Paketverlust
- Client spielt das Medium bereits ab, während der Server immer noch weitere Teile des Videos an den Client überträgt
- Puffer im Client, um Jitter auszugleichen
- Oft UDP statt TCP für geringeren Overhead
- Kompression und Error Concealment

**Ansatz 1:**
Datei in Teilen per HTTP runterladen und abspielen, während weitere Teile laden.

**Ansatz 2:**
Streamen von einem dedizierten Streamingserver. Dabei kann ein extra Protokoll auf Grundlage von UDP verwendet werden, in der Regel effizienter.

**UDP vs TCP**
- UDP sendet mit einer konstanten Rate ohne auf Überlast Rücksicht zu nehmen
- TCP sendet mit maximaler TCP-Rate, verzögert wegen Übertragungswiederholungen, braucht größeren Puffer. Aber weniger Probleme mit Firewalls als UDP

**Best-Effort-Dienste**

Multimedia-Anwendungen verwenden Techniken auf der Anwendungsschicht, um die Auswirkungen von Verzögerungen und Verlusten zu minimieren.

**Internettelefonie**
- Während dem Sprechen werden Daten erzeugt und Übertragen, zum Beispiel Stücke von 20ms mit 8kByte/s = 160Byte
- Header für die Anwendungsschicht, die zur Übertragung der  Audiodaten verwendet wird
- Paketverlust durch Netzwerküberlastung möglich
- Paket kann verzögert sein und dann nicht mehr gebraucht werden.
- Je nach Kodierung können Verlustraten von 1-10% toleriert werden
- Abspielverzögerung: Groß = weniger verworfene Pakete, Klein = Interaktiver
- Adaptive Bestimmung der Wiedergabeverzögerung
- Exponentielle Glättung mit kontante u: $d_i = (1-u)d_{i-1} + u*\text{Verzögerung}_i$
- durchschnittliche Abweichung von der geschätzten Verzögerung: $v_i = (1-u)v_{i-1} + u|r\text{Verzögerung} - d_i|$
- $p_i = t_i + d_i + K * v_i$

**Paketverluste**
1. Forwärtskorrektur: Für jede Gruppe von n Paketen wird ein Redundanzpaket erstellt (XOR).Maximal 1 Paket kann verloren gehen.Höhere Wiedergabeverzögerung weil alle Pakete eingegangen sein müssen bevor abgespielt wird.
2. zweiter Strom mit niedriger Qualität. Wenn nicht beide Pakete verloren werden kann der Verlust verborgen werden.
3. Interleaving: Samples werden in kleinere Einheiten zerlegt und ein Paket enthält Daten von mehreren Samples. Bei einem verlorenen Paket entstehen keine "Lücken". Keine Redundaz, höhere Abspielverzögerung

**CDN Content-Distribution-Netzwerk**
- viele CDN-Server im Internet in der Nähe der Nutzer
- Verzögerung minimalisieren, Redundanz
- Der CDN Provider erstellt eine Karte mit den Distanzen aller IP-Adressen zu den eigenen Servern. Beim Eintreffen einer DNS-Anfrage wird der nächste Server verwendet.

### Dienstklassen
Manche Anwendungen haben höhere Anforderungen. Zum Beispiel sollte ein VoIP Anruf nicht stocken, wenn eine Datei hochgeladen wird.
1. Pakete markieren, um Verkehrsklassen zu unterscheiden
2. Isolation der einzelnen Netzwerkströme und beschränken durch policy
3. Trotz Isolation müssen die Ressourcen so gut wie möglich ausgenutzt werden.

**Scheduling**

1. FIFO: Bearbeitung in der Reihenfolge der Ankunft. Discard-Policy: letztes, nach Priorität oder zufällig
2. Prioritätswarteschlange: Übertragen des Paketes mit der höchsten Prio. Prio kann aus den Headerinformationen bestimmt werden.
3. Round-Robin-Scheduling: Verschiedene Klassen an Paketen und je eine Warteschlange pro Klasse. Abwechselndes Bedienen des ersten Paketes jeder Warteschlange.
4. Weighted Fair Queuing: Wie Round Robin, aber jede Warteschlange hat ein Gewicht, nach dem sie bedient wird

**Überwachung (Policing)**
Beschränken nach:
- Durchschnittliche Rate
- Maximale Rate
- Burst-Größe

Methonde Leaky Bucket: Es wird mit konstanter Geschwindigkeit Tokens bis zu einem Limit generiert. Das Übertragen eines Pakets kostet einen Token. Eine Kombination von Weighted Fair Queueing + Leaky Bucket führt zu einer oberen Grenze für die Verzögerung.

### IETF Differentiated Services
- Dienstklassen mit unterschiedlicher Priorität
- Router am Rand des Netzwerks markieren die Priorität der Pakete
- Die Router im Inneren Puffern und Schedulen auf Basis der Markierung
- Markierung von Dienstklassen oder Profilen
- Eingangsverkehr kann entsprechend des Profils begrenzt und überwacht werden.
- Wird im TOS Feld (IPv4) oder im Traffic-Class-Feld (IPv6) markiert
- 6 Bits für Differentiated Service Code Point DSCP, 2 Bits ungenutzt.
- Es können verschiedene Mechanismen verwendet werden, zum Beispiel Bandbreite für eine Klasse festlegen oder Priorisierung beim Scheduling

**Rufzulassung**
Ein Netzwerkstrom  meldet seinen Bedarf an. Er muss abgewiesen werden,  wenn keine ausreichenden Ressourcen bereit stehen. Ressourcen werden dafür reserviert.