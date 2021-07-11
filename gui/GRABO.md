## Software-Ergonomie

**Ergonomie**
- Lehre von der menschlichen Arbeit, ihrer Beschreibung, Modellierung, Verbesserung und die Bedürfnisse
- Ergonomie entwickelt Methoden zur Erfüllung der Schutzbedürfnisse
- Zentrale Ziele: Effektivität, Effizienz, Zufriedenheit
- Software-Ergonomie ist Teil der Mensch-Computer-Interaktion
- Entwicklung von Oberflächen im Rahmen des Usability-Engineerings

**Benutzerfreundlichkeit**
- Nutzungsqualität
- User Experience wird berücksichtigt

**Gebrauchstauglichkeit**: Ausmaß, in dem ein Produkt, System oder ein Dienst durch bestimmte Benutzer in einem bestimmten Anwendungskontext genutzt werden kann, um bestimmte Ziele effektiv, effizient und zufriedenstellend zu erreichen.

**Grudsätze der Dialoggestaltung**
- Leicht zu bedienen
- Aufgabenangemessenheit
- Selbstbeschreibungsfähigkeit
- Lernförderlichkeit (Metaphern)
- Steuerbarkeit
- Erwartungskonformität
- Individualisierbarkeit
- Fehlertoleranz

**Acht goldene Regeln von Shneiderman**
- Konsistenz
- Berücksichtige unterschiedliche Erfahrungen
- Rückmeldungen und Aktionen des Benutzers
- Abgeschlossene Operationen
- Fehler verhindern
- Einfache Rücksetzmöglichkeiten
- Benutzerbestimmte Eingaben
- Geringe Belastung des Kurzzeitgedächtnisses

**Zehn Usability Heuristiken von Nielsen**
- Einfache und natürliche Dialoge
- Ausdrucksweisen des Anwenders
- Minimale mentale Belastung des Benutzers
- Konsistenz
- Rückmeldungen
- Klare Auswege
- Abkürzungen
- Gute Fehlermeldungen
- Fehlervermeidung
- Hilfe und Dokumentation

**Ergänzungen von Markus Dahm**
- Freude bei der Arbeit
- Ansprechende Gestaltung
- Minimale Gestaltung
- Orientierung an Abläufen

## GUIs
**Abstract Window Toolkit (AWT)** basiert auf Primitivoperationen zum Zeichnen und besteht auf nativen Komponenten des Betriebssystems.

**Swing** wurde 1998 zur Erneuerung von AWT entwickelt. AWT und Swing bilden Java Foundation Classes als Teil der Java SE.

**JavaFX** ist eine komplette Neuentwicklung und seit Java 10 nicht mehr im JRE/JDK enthalten. Es erlaubt Direktzugriff auf Grafikkalte mit 2D/3D

**SWT Standard Widget Toolkit** Entwickelt von IBM um native Möglichkeiten eines grafischen Systems nutzen zu können. DLL muss mit ausgeliefert werden.

AWT und Swing erlauben keine deklarativen Oberflächen.

## Java Swing
**Ereignisorientierte Programmierung** ist ein Paradigma zur Steuerung des Programmflusses. Es gibt Listener und Ereignis-Objekte, die den Listenern übergeben werden. Außerdem Observer und Event Handler.

Komponenten werden in Containern platziert, zum Beispiel FlowLayout, BoxLayout oder GridLayout.

## JavaFX
**Lebenszyklus**: launch(String) -> init() -> start(Stage) -> stop()

**Aufbau**: Stage, Scene, Nodes

**Layoutcontainer**
- GridPane: Nodes werden Zellen in einem Raster zugeordnet
- StackPane: Nodes werden wie auf einem Stapel platziert
- FlowPane: Nodes werden horizontal oder vertikal nebeneinander platziert und umgebrochen
- BorderPane: Nodes werden im 5 verschiedenen Bereichen platziert
- HBox/VBox: Nodes werden horizontal/vertikal in einer Zelle ausgerichtet

Properties repräsentieren Eigenschaften eines Datenobjekts. Bindings deklarieren Abhängigkeiten dieser Properties. 

Bindings können auch bidirektional sein. Es wird lediglich eine Veränderung registriert und die Verbindung zwischen den Properties temporär als invalid markiert. Die Berechnung erfolgt dann erst wenn ein Zugriff mit getValue() erfolgt (lazy Evaluation). So müssen keine unnützen Änderungen propagiert werden.

Observables sind Collections, die das Observable Interface implementieren. Sie können in mehreren UI-Controls wie ListView, TableView oder Combobox verwendet werden. (ObservableList, ObservableMap, ObservableSet).

Listener kann man auf Property oder Binding registrieren (Interface ObservableValue). Es gibt InvalidationListener und ChangeListener.

## FXML
Deklarative Programmierung von Oberflächen. Einparung von Java Code und getrennte Arbeitsbereiche von Entwickler und Designer. Trennung von Design und Businesslogik erhöht Testbarkeit der Anwendung. Beinhaltet Prozessinstruktionen für Programm, das XML verarbeitet (z. B. imports)

Namensräume: Tags können gleiche Namen aber unterschiedliche Bedeutungen haben. Namensräume stellen die Eindeutigkeit von Elementen in gewissen Bereichen sicher.

Die Architektur besteht aus einer FXML-Datei, einer Controller Klasse, einer Daten-Klasse und einer Hauptklasse zum Starten der Anwendung und Laden der FXML Datei.

## Diagramme
LineChart, AreaChart, StackedAreaChart, PieChart, BarChart, ScatterChart, BubbleChart

## Entwurfsmuster
- Erzeugungsmuster: Entkopplung von Objektkonstruktion und Repräsentation. Kapselung und Auslagerung der Objekterzeugung
- Strukturmuster: Erleichterter Softwareentwurt durch vorgefertigte Schablonen für Beziehungen zwischen Klassen.
- Verhaltensmuster: Modellierung komplexen Verhaltens von Software
- Beobachtermuster: Push, Pull (Polling), Publish/Subscribe, Message Bus
- Model-View-Controller: Model ist unabhängig verwendbar. Views greifen Daten von Model ab. Controller nimmt Benutzereingaben entgegen.
- Varianten: Model-View-Presenter (Model und View komplett getrent), Model-View-Viewmodel (ViewModel enthält UI-Logik, komplexere Operationen und Zustand der View)

## Nebenläufigkeit
- Parallelisierung auf mehrere CPUs
- Anwendung muss jederzeit bedienbar sein, EventQueue darf nicht blockiert werden.
- Worker: Objekt, dass im Hintergrund Arbeit erledigt und dessen Zustand observierbar ist.
- Task: Implementierung des Worker-Interface
- Service: Taskverwaltung für mehrmalige Ausführung.
- ScheduledService: Task wird in vorbestimmten Intervallen ausgeführt