# Graphen und Algorithmen auf Graphen

| Name         | Ziel                                                                              | Laufzeit | Erklärung                                                                      | Greedy |
| ------------ | --------------------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------ | ------ |
| Euler Weg    | Kann der Graph traversiert werden, ohne eine Kante doppelt zu gehen?              | O(n)     | Jeder Knoten braucht einen geraden Grad                                        | nein   |
| Euler Zyklus | Kann ein Graph traversiert werden, ohne doppelt zu gehen mit gleichem Ende/Start? | O(n)     | Jeder Knoten braucht gleich viele Kanten, die an ihm starten wie an ihm enden. | nein   |
| Breitensuche | Finden eines Weges von einem Ort zu einem anderen im Graph                        | O(n)     | Darstellung des Graphen als Baum, dann Level Order Durchlauf                   | nein   |
| Tiefensuche  | Finden eines Weges von einem Orz zu einem anderen im Graph                        | O(n)     | Rekursives Durchlaufen (Backtracking), Pre-Order Durchlauf                     | nein   |
|              |                                                                                   |          |                                                                                |        |


## Graphen

Ein Graph besteht auf Knoten und Kanten. Der Grad eines Knoten ist die Zahl der Kanten, die an ihm Enden/Beginnen.
Bei einem gerichteten Graph können Kanten nur in einer Richtung begangen werden. Ein gewichteter Graph hat Kosten
für jede Kante. Kanten mit negativem Gewicht können zu Schleifen mit den Kosten $-\infty$ führen.

## Euler Weg und Euler Zyklus

Für einen Eulerzyklus muss jeder Knoten einen geraden Grad haben. Falls der Graph
gerichtet ist, muss außerdem der ausgehende Grad gleich dem eingehenden Grad sein. 
Es wird bei einem zufälligen Knoten angefangen und ein Pfad gebildet. Bildet man dabei
einen Zyklus, der nicht alle Knoten enthält, wird der Zyklus zum ersten Knoten rotiert, 
der noch freie Kanten hat (breakout).

Für einen Eulerweg können auch zwei Knoten einen ungeraden Grad haben, diese werden 
dann mit einer Hilfskante verbunden, der Eulerzyklus erstellt, der Zyklus rotiert und 
die Hilfskante danach wieder entfernt.

## Traversieren von Graphen

Breitensuche geht rekursiv in jedem Schritt zu allen benachbarten Knoten. Ist mit dem 
Level Oder Durchlauf in Bäumen vergleichbar.

Tiefensuche geht über Backtracking rekursiv alle Knoten ab. Pre-Order in Bäumen

