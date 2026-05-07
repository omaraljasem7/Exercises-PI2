## Aufgabe 3: Prozessverwaltung &ndash; Scheduling

In dieser Aufgabe vertiefen wir das Wissen zu zwei Scheduling-Algorithmen:

1. **Round-Robin Scheduling** (präemptiv) mit Zeitscheiben von 5 ms. Initialisierung: Alle bei t=0 verfügbaren Prozesse werden alphabetisch sortiert (A, B, D, E). Einreihungsregel: Unterbrochene Prozesse werden immer am Ende der aktuellen Ready-Queue eingereiht.
2. **Shortest Job First (SJF) Scheduling** (nicht-präemptiv), bei dem jeweils der Prozess mit der kürzesten Restrechenzeit aus der Ready-Queue gewählt wird. Bei gleicher Rechenzeit entscheidet die alphabetische Reihenfolge. (<a href="https://de.wikipedia.org/wiki/Shortest-Job-Next#Beispiel">siehe Wikipedia</a>).

Helfen Sie Professor Eich dabei, die Rechenkapazität des PCs zu verwalten. Es sollen die folgenden fünf Prozesse gerechnet werden:

| Prozesse      | Verfügbar nach    | Rechenzeit    |
|---------------|-------------------|---------------|
| A             | 0 ms              |  7 ms         |
| B             | 0 ms              |  5 ms         |
| C             | 3 ms              |  3 ms         |
| D             | 0 ms              | 13 ms         |
| E             | 0 ms              |  9 ms         |

Geben Sie für **beiden** Scheduling-Verfahren folgende Informationen an:
1. In welcher *Reihenfolge* das Scheduling-Verfahren die Prozesse bearbeitet sowie die jeweilige Ausführungsdauer jedes Durchlaufs (bei präemptiven Verfahren können Prozesse mehrfach vorkommen). Beachten Sie dabei, dass nicht alle Prozesse sofort verfügbar sind.
2. Für jeden Prozess die *Laufzeit* (Turnaround Time). Dies ist die Zeitspanne von der Ankunft eines Prozesses bis zu seiner vollständigen Ausführung (Fertigstellung).
3. Für jeden Prozess die *Wartezeit* (Waiting Time). Die Wartezeit eines Prozesses ist die Gesamtzeit, die er in der Ready-Queue verbringt (Turnaround Time minus tatsächliche Rechenzeit).
4. Die Anzahl der *Kontextwechsel* (Context Switches) vom Start bis zur Fertigstellung aller Prozesse.

Vergleichen Sie die Ergebnisse beider Scheduling-Verfahren. Welche Eigenschaften (s. Vorlesung) priorisieren die Scheduling-Verfahren.