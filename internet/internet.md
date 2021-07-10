# **Internet**
# Einführung
Vor Internet: Leitungsvermittlung zwischen Sender und Empfänger

Im Internet: Paketvermittlung zwischen Sender und Empfänger. Längere Nachrichten werden in einzelne Datenpakete aufgeteilt ung entweder verbindungslos oder verbindungsorientiert übertragen.

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

Bitübertragungsschicht _Kabel_ -> Sicherungsschicht _Bridge, Switch_ -> Netzwerkschicht/Vermittlungsschicht _IP, Router_ -> Transportschicht _TCP/UDP_ -> (Kommunikationssteuerungsschicht) -> (Darstellungsschicht) -> Anwendungsschicht

**TCP Transmission Control Protocol**
- Baut eine Verbindung zwischen 2 Endpunkten her
- Baut auf IP auf
- Datenverluste werden erkannt und automatisch behoben

**Client-Server vs Peer to Peer**
Bei Client-Server kann der Client einen Dienst beim Server anfordern, der üblicherweise für viele Clients arbeitet. Bei Peer to Peer kommunizieren mehrere gleichberechtigte Computer untereinander, keine Unterscheidung zwischen C/S, jede Node hat die Daten selbst.

## Kapitel 2
**Websocket**

Websockets sind kompatibel aber verschieden zu HTTP und sind voll-duplex. Sie erlauben Verbindungen mit weniger overhead als HTTP polling und erlaubt real time Datenübertragung. Server und Client können über eine offene Verbindung länger kommunizieren.

**Netzanforderungen**

Unterschiedliche Services haben unterschiedliche Anforderungen, vor allem in Sachen Datenverlust, Durchsatz und Echtzeit. Verbindungen sollten stabil sein und zuverlässig getrennt werden.

### HTTP Hypertext Transfer Protocol

Zustandsloses Protokoll zur Übertragung von Daten auf der Anwendungsschicht auf TCP, vor allem für Webseiten. HTTPS ist zusätzlich noch verschlüsselt. Sitzungsinformationen müssen jedes Mal mitgeführt werden, zum Beispiel als Cookie in den Header-Informationen. 
![](img/http.png)
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
Manche Anwendungen haben höhere Anforderungen. Zum Beispiel sollte ein VoIP Anruf nicht stocken, wenn eine Datei hochgeladen wird. Grundprinzipien von QoS:
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

## Kommunikation in verteilten Netzwerken
### Remote Procedure Call RPC
Ermöglicht den Aufruf von Funktionen in anderen Adressräumen. Verschiedene Implementierungen sind meist nicht kompatibel.

Für den Aufruf sind Name der Prozedur (oder ID) und zugehörige Parameter notwendig.

**Remote Method Invocation**
Aufruf einer Methode eines entfernten Java-Objekts. Andere JVM auf beliebigem anderem Computer. Aufruf sieht gleich aus wie normaler Aufruf, es müssen nur extra Exceptions gefangen werden. Die Verbindung wird mit dem Stub realisiert. Für die Verbindung braucht man die Serveradresse und einen Bezeichner von einem Namensdienst.

**Webservice**
Schnittstelle über HTTP(S) für Maschine-zu-Maschine Kommunikation, zum Beispiel REST-APIs. Kommunikation oft im XML oder JSON Format

**SOAP** besteht aus 3 Teilen, UDDI als Verzeichnisdienst zur Registrierung von Webservices, WSDL zur Beschreibung der Methoden und SOAP zur Kommunikation. SOAP ist auf HTTP(S) aufgebaut und benutzt XML in einem speziellen Namensraum. Eine Nachricht besteht aus einem `Envelope`, in dem ein `Header` und ein `Body` sind.
```
<?xml version="1.0"?>

<soap:Envelope
xmlns:soap="http://www.w3.org/2003/05/soap-envelope/"
soap:encodingStyle="http://www.w3.org/2003/05/soap-encoding">

<soap:Header>
...
</soap:Header>

<soap:Body>
...
  <soap:Fault>
  ...
  </soap:Fault>
</soap:Body>

</soap:Envelope>
```

**WSDL** erlaubt einem Client die Funktionen eines Webservice bei einem Webserver abzufragen. Alle verwendeten speziellen Datentypen sind in der WSDL-Datei in XML-Form eingebunden. Der Quellcode, der zum Zusammensetzen der gesendeten Objekte auf der Client-Seite notwendig ist, kann automatisiert aus der WSDL-Datei generiert werden. Der Client kann nun SOAP verwenden, um eine in WSDL gelistete Funktion letztlich aufzurufen.

| Element    | Description                                                               |
| ---------- | ------------------------------------------------------------------------- |
| `<types>`    | Defines the (XML Schema) data types used by the web service               |
| `<message>`  | Defines the data elements for each operation                              |
| `<portType>` | Describes the operations that can be performed and the messages involved. |
| `<binding>`  | Defines the protocol and data format for each port type                   |

```
<message name="getTermRequest">
  <part name="term" type="xs:string"/>
</message>

<message name="getTermResponse">
  <part name="value" type="xs:string"/>
</message>

<portType name="glossaryTerms">
  <operation name="getTerm">
    <input message="getTermRequest"/>
    <output message="getTermResponse"/>
  </operation>
</portType>

<binding type="glossaryTerms" name="b1">
   <soap:binding style="document"
   transport="http://schemas.xmlsoap.org/soap/http" />
   <operation>
     <soap:operation soapAction="http://example.com/getTerm"/>
     <input><soap:body use="literal"/></input>
     <output><soap:body use="literal"/></output>
  </operation>
</binding>
```
## Cloud Computing
- Direkten und schnellen Zugriff auf einen Pool von geteilten Ressourcen (Netzwerke, Speicherplatz, Rechenleistung, Anwendungen) über ein Netzwerk ohne menschliche Interaktion. Wichtig ist ständige Verfügbarkeit.

![](img/x-as-a-service.jpg)

Cloud wird auch oft als Hybrid-Cloud verwendet, zum Beispiel zur Integration von alten und neuen Systemen oder zur besseren Skalierung (bei peaks) und Backups. Eine hybrid Cloud hat aber auch Nachteile durch den komplexeren Aufbau und die damit verbundene Administration.

Beim Cloud Computing werden Applikationen virtualisiert, zum Beispiel mit Docker. Sie teilen dann das Betriebssystem (und je nach dem libraries). Ein beliebtes Konzept sind Microservices, mit denen ein großes Programm in viele kleine Unterteilt wird, die untereinander kommunizieren und besser skalieren. Die Runtime Optionen sind VPS, Containers oder Serverless

### Container vs VM
Container verwenden den Kernel des Host OS und verwenden nur eigene Bins/Libs für ihre Programme. So können Container von allen Linux-Distributionen auf einem Linux-Server laufen, da sie den Kernel teilen können.

VMs haben jeweils ein komplettes Gast OS mit eigenem Kernel, was zu mehr overhead führt und die Performance reduziert.

Container sind normalerweise schneller und lassen sich leichter deployen und restarten.

### Microservices
Microservices sind eine Alternative zu einem großen zentralen Programm. Der Webservice besteht aus vielen unabhängigen Programmen, die untereinander mit APIs kommunizieren. So können die einzelnen Bestandteile besser skaliert werden und es kann leichter auf bestehende Code-Bestandteile zugegriffen werden. EIn Nachteil ist, dass schon beim Ausfall eines einzelnen Webservice alles andere nicht mehr funktioniert.

## IPv6
Adressraum von IPv4 ist erschöpft und das normale Internetwachstum nicht mehr adressierbar. NAT als temporärer Fix. Unterstützung neuer Services mühsam.
- 128 Bit lange Adressen mit Adresshirarchie für einfacheres Backbone-Routing
- Mehrere Adressen pro IP-Interface üblich
- Autokonfiguration auch ohne DHCPv6 vorgesehen
- Fließende Netzmasken, Renumbering durch Präfixänderung
- Security Header Extension für Authentisierung, Integrität und Verschlüsselung
- Schlankerer Header zur schnelleren Verarbeitung und optional zusätzlich eingeschobene Header
- Verzicht auf Header Checksum und Fragmentierung
- Multicast beginnt mit FF00, kein Broadcast mehr
- Adresse besteht aus Global Routing Prefix, Subnet ID und Interface ID. Alle globalen Unicast-Adressen, die nicht mit 000 (binär) beginnen, besitzen eine 64 bit Interface ID

**Autokonfiguration**
- Interface bildet lokale Adresse aus Hardwareadresse
- Interface sendet router solicitation um nicht warten zu müssen
- Router sendet router advertisement (Präfix, Default Gateway)
- Interface bildet aus Präfix und link-lokaler Adresse eine globale Adresse
- Zur Verifikation der Eindeutigkeit wird noch eine ICMP neighbor solicitation versandt (Duplicate Adress Detection).

![](img/ipv6.png)

Optionsheader für:
- Routing: Erweiterte Routinginformationen
- Fragmentation: Fragmentierungsinformationen
- Authentication: Sicherheitsinformationen Authentizität und Integrität
- Encapsulation: Tunneling für vertrauliche Daten
- Hop-by-Hop Option: Spezielle Optionen, die an jedem Router verarbeitet werden
- Destination Option: Informationen für den Empfänger-Host

**Migration**
- Dual-Stack Techniken, welche die Koexistenz von IPv4 und IPv6 für dieselben Geräte und Netze erlauben
- Tunnel, welche IPv6 Regionen über IPv4 Regionen hinweg verbinden
- Protokollübersetzer, welche IPv6 Geräte mit IPv4 Geräten sprechen lassen

## Kryptografie
**Confidentiality**. Only the sender and intended receiver should be able to understand the contents of the transmitted message.

**Message integrity**. Alice and Bob want to ensure that the content of their communication is not altered, either maliciously or by accident, in transit

**End-point authentication**. Both the sender and receiver should be able to confirm their respective identity

**Operational security**. Almost all organizations (companies, universities, and so on) today have networks that are attached to the public Internet. These networks therefore can potentially be compromised by the other party involved in the communication

**Kernprinzipien von Kryptografie**
- Maskieren von Daten (Verschlüsselung)
- Potentieller Eindringling kann keine Informationen von abgefangenen Daten interpretieren
- Empfänger kann aus den maskierten Daten die Original-Daten wiederherstellen
- Um den Ciphertext  KA(M) zu erzeugen , werden Schlüssel benötigt. (KA Verschlüsselungs-Schlüssel, KB Entschlüsselungs-Schlüssel). Entschlüsselung erfolgt demnach beim Empfänger mit KB(KA(m)) Symmetrische Schlüssel sind gegeben wenn K(A) = K(B)

**Symmetrische Schlüssel**: Sender und Empfänger müssen den Schüssel vorher kennen.

**Asymmetrische Verschlüsselung**: Öffentlicher Schlüssel für die Verschlüsselung, privater Schlüssel für die Entschlüsselung.

Integrität kann über Hash Funktionen sichergestellt werden. Ein Message Authentication Code dient dazu, Gewissheit über den Ursprung von Daten oder Nachrichten zu erhalten und ihre Integrität zu überprüfen. MAC-Algorithmen erfordern zwei Eingabeparameter, erstens die zu schützenden Daten und zweitens einen geheimen Schlüssel, und berechnen aus beidem eine Prüfsumme, den Message Authentication Code.

Eine digitale Unterschrift attestiert, dass man mit dem Inhalt des digitalen Dokuments einverstanden ist. Es muss durch die digitale Signatur nachvollziehbar sein, dass der Unterzeichner unterschrieben hat. Certification Authorities sollen Keys zu Entities zuordnen und verifizieren. Sie sind eine Trusted Party.

PGP (Pretty Good Privacy) ist Standard für die Verschlüsselung von E-Mails.

SSL (Secure Socket Layer) ist technisch gesehen Teil der Anwendungsschicht, aus Sicht des Entwicklers ein Transportschichtprotokoll. Nachfolger ist TLS (Transport Layer Security). Es gelten die Prinzipien Vertraulichkeit (Verschlüsselung), Integrität der Daten und Authentizität der Daten.