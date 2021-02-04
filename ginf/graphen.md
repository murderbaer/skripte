# Graphen und Algorithmen auf Graphen

| Name                    | Ziel                                                                              | Laufzeit                         | Erklärung                                                                                                         | Greedy | Exakt |
| ----------------------- | --------------------------------------------------------------------------------- | -------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ------ | ----- |
| Euler Weg               | Kann der Graph traversiert werden, ohne eine Kante doppelt zu gehen?              | O(n)                             | Jeder Knoten braucht einen geraden Grad                                                                           | nein   | ja    |
| Euler Zyklus            | Kann ein Graph traversiert werden, ohne doppelt zu gehen mit gleichem Ende/Start? | O(n)                             | Jeder Knoten braucht gleich viele Kanten, die an ihm starten wie an ihm enden.                                    | nein   | ja    |
| Breitensuche            | Finden eines Weges von einem Ort zu einem anderen im Graph                        | O(n)                             | Darstellung des Graphen als Baum, dann Level Order Durchlauf                                                      | nein   | ja    |
| Tiefensuche             | Finden eines Weges von einem Orz zu einem anderen im Graph                        | O(n)                             | Rekursives Durchlaufen (Backtracking), Pre-Order Durchlauf                                                        | nein   | ja    |
| Kruskal Algorithmus     | Minimal aufspannender Baum                                                        | $O(n\cdot\log(n))$  bis $O(n^2)$ | Gruppen werden zusammengefasst.                                                                                   | ja     | ja    |
| Prim Algorithmus        | Minimal aufspannender Baum                                                        | $O(n\cdot\log(n))$  bis $O(n^2)$ | Immer die kürzeste anliegende Kante verwenden                                                                     | ja     | ja    |
| Dijkstra Algorithmus    | Kürzeste Wege                                                                     | $O(n^2)$                         | Brute Force in intelligenter Reihenfolge                                                                          | ja     | ja    |
| Bellman-Ford            | Kürzeste Wege                                                                     | $O(n^2)$                         | Verallgemeinerung von Dijkstra für negative Kanten                                                                | ja     | ja    |
| Floyd-Warshall          | All Pair shortest Path                                                            | $O(n^3)$                         | Verwendet Matrix-Operationen                                                                                      | nein   | ja    |
| Ungarischer Algorithmus | Matching                                                                          | $O(n^3)$                         | Findet Matching mit erweiterten Pfaden                                                                            | nein   | ja    |
| Nearest Neighbor        | TSP                                                                               | $O(n^2)$                         | Man fängt beim Startknoten an und geht von dort immer den kürzesten Pfad zum noch nicht besuchten Nachbar         | ja     | nein  |
| Greedy Algorithm        | TSP                                                                               | $O(n^2)$                         |                                                                                                                   | ja     | nein  |
| MST Heuristik           | TSP                                                                               | $O(n^2)$                         | Der Minimum spanning tree wird verdoppelt und Knoten, die doppelt angefahren werden, durch direkte Kanten ersetzt | nein   | nein  |
| Christofide Heuristik   | TSP                                                                               | $O(n^4)$                         | Minimum spanning tree, dann matching zwischen den Knoten mit ungeradem Grad.                                      | nein   | nein  |

## Graphen

Ein Graph besteht auf Knoten und Kanten. Der Grad eines Knoten ist die Zahl der 
Kanten, die an ihm Enden/Beginnen. Bei einem gerichteten Graph können Kanten 
nur in einer Richtung begangen werden. Ein gewichteter Graph hat Kosten
für jede Kante. Kanten mit negativem Gewicht können zu Schleifen mit 
den Kosten $-\infty$ führen.

## Euler Weg und Euler Zyklus

Für einen Eulerzyklus muss jeder Knoten einen geraden Grad haben. Falls der Graph
gerichtet ist, muss außerdem der ausgehende Grad gleich dem eingehenden Grad sein. 
Es wird bei einem zufälligen Knoten angefangen und ein Pfad gebildet. Bildet man
dabei einen Zyklus, der nicht alle Knoten enthält, wird der Zyklus zum ersten
Knoten rotiert, der noch freie Kanten hat (breakout).

Für einen Eulerweg können auch zwei Knoten einen ungeraden Grad haben, diese
werden dann mit einer Hilfskante verbunden, der Eulerzyklus erstellt, der 
Zyklus rotiert und die Hilfskante danach wieder entfernt.

## Traversieren von Graphen

Breitensuche geht rekursiv in jedem Schritt zu allen benachbarten Knoten. Ist
mit dem Level Oder Durchlauf in Bäumen vergleichbar.

Tiefensuche geht über Backtracking rekursiv alle Knoten ab. Pre-Order in Bäumen

## Aufspannende Bäume
Ein aufspannender Baum eines Graphen verbindet alle Knoten, ohne dass es Schleifen
gibt (nicht eindeutig). Der minimal aufspannende Baum ist der aufspannende Baum 
eines gewichteten Graphen, bei dem die Summe der Kantengewichte minimal ist.

Der Kruskal Algorithmus ist ein greedy Algorithmus. Alle Kanten werden nach dem 
Gewicht sortiert. Die Knoten werden durch die Kanten in Gruppen zusammengefasst, 
wobei die Kanten, die zur selben Gruppe zeigen, weggelassen werden.

Der Prim Algorithmus wählt einen Startknoten und sortiert alle anliegenden Kanten
nach dem Gewicht. Es wird immer die Kante mit dem geringsten Gewicht verwendet, 
es sei denn, die Kante zeigt zu einem Knoten, der schon im Baum ist.

## Kürzeste Pfade
Es gibt 3 Arten von kürzesten Pfaden:
- Single Pair shortest path
- Single Source shortest path
- All Pair shortest path

Bei negativem Kantengewicht kann es zu Schleifen mit negativer Summe kommen, was 
zu Abständen von $-\infty$ führen kann.

Der Dijkstra Algorithmus brute-forced alle Wege in der Reihenfolge der kürzesten
Wege zum Startpunkt. Dabei muss für jeden Knoten auch der Vorgänger auf dem Weg
zum Startpunkt gespeichert werden. Funktioniert nur mit nicht-negativen Kanten.

Der Bellman-Ford Algorithmus ist eine Verallgemeinerung vom Dijkstra Algorithmus
für negative Kanten. Der Abstand zu S wird nie als final betrachtet. Erkennt
negative Zyklen, aber funktioniert nur korrekt ohne sie.

Der Floyd-Warshall Algorithmus führt in jedem Durchlauf k
$$m_{i,j} = \min(m_{i, j}, m_{i, k} + m_{1, k})$$
auf jedes Element der Matrix durch.

## Schwierige Verfahren
Der Hamilton Weg ist ein Weg, der alle Knoten einmal durchläuft.
Der Hamilton Zyklus ist wie der Hamilton Weg, nur dass er am
gleichen Ort beginnt und endet. Es gibt keinen effizienten Algorithmus
um zu erkennen, ob ein Graph einen Hamilton Weg/Zyklus enthält.

Das Travelling Salesman Problem (TSP) sucht den Zyklus mit den geringsten
kosten durch alle Knoten des Graphen. Dabei ist jeder Knoten mit jedem
anderen Knoten verbunden. Es gibt also n! mögliche Pfade. Deshalb gibt
es Algorithmen, die Näherungslösungen in Polynomialer Zeit finden sollen.
(Problemklasse P und NP)

Ein Problem, bei dem Lösungsalgorithmen alle mindestens ein exponentielles
Wachstum haben, bezeichnet man als algorithmisch unlösbar.

Lösungen zu NP Problemen lassen sich aber in polynomialer Zeit überprüfen,
ob sie eine Lösung sind.

- Approximationsverfahren liefern eine Lösung in polynomialer Zeit mit
  Gütegarantie.
- Heuristische Verfahren liefern wahrscheinlich eine Lösung in 
  polynomialer Zeit ohne Gütegarantie.

## Paarungsproblem/Matchingproblem
2 Mengen sollen zugeordnet werden. Eine Kante geht immer von der ersten Menge 
zur zweiten Menge. In einer perfekten Paarung hat man viele Teilgrafen und
jeder Knoten hat den Grad 1.

TODO: Ungarischer Algorithmus

## TSP
Der nearest neighbor Algorithmus fängt bei einer zufälligen Kante an und
geht immer den kürzesten Pfad zum nächsten Nachbar. Findet nicht immer eine
Lösung und oft nicht die Beste.

Der Greedy Algorithm sortiert die Kanten nach Kosten und verbindet immer
die 2 Knoten mit den geringsten Kosten. Dieser Schritt wird übersprungen,
wenn ein Zyklus entsteht oder die Knoten schon Grad 2 erreicht haben.
Funktioniert nicht in jedem Fall.

Beim k-Opt-Verfahren werden k Kanten aus der aktuellen Tour entfernt und
durch geeignete andere k Kanten, die nicht (außerhalb) in
der Tour enthalten sind, ersetzt. Je größer das k, desto besser das Ergebnis
und desto höher der Rechenaufwand

