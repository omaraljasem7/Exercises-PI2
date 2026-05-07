## Aufgabe 2: Dateisysteme &ndash; ext2

Gegeben sei ein **ext2-Dateisystem** mit folgenden Eigenschaften:

- Clustergröße: 4 Bytes
- 12 direkte Clusteradressen pro Inode
- Clusteradressen sind 4 Byte lang

### Inode Tabelle

| Inode | Typ         | Größe     | Direkte Clusteradressen             |
|-------|-------------|-----------|-------------------------------------|
|  1    | Verzeichnis | 64 Bytes  | 105, 203, 87, 156, ...              |
|  8    | Datei       | 13 Bytes  | 42, 199, 73, 8                      |
| 17    | Datei       | 16 Bytes  | 301, 15, 222, 89                    |
| 29    | Datei       | 30 Bytes  | 50, 178, 12, 234, 99, 9, 188, 241   |

### Inode 1: Cluster-Inhalte des Wurzelverzeichnisses

| Name          | Inode |
|---------------|-------|
| starter.txt   |  8    |
| legend.txt    | 17    |
| team.txt      | 29    |

### Datencluster

| Cluster   | Inhalt    |
|-----------|-----------|
| 8         | i^-^      |
| 9         | ames      |
| 12        | ket_      |
| 15        | ou_i      |
| 42        | Pika      |
| 50        | Team      |
| 73        | Evol      |
| 89        | tark      |
| 99        | ie+J      |
| 118       | igel      |
| 167       | Glur      |
| 178       | _Roc      |
| 188       | Mauz      |
| 199       | chu+      |
| 222       | st_s      |
| 234       | Jess      |
| 241       | i!?@      |
| 245       | lum_      |
| 301       | Raik      |

1. Wie lauten die Inhalte der drei Dateien im Wurzelverzeichnis?
2. Ein neuer Eintrag *shiny.txt* mit Inode 35 soll zum Wurzelverzeichnis hinzugefügt werden. Die Datei soll den Inhalt <code>Shiny-Suche läuft!</code> enthalten. Beginnen Sie die Belegung bei Clusteradresse 240. Gehen Sie davon aus, dass alle in der Tabelle aufgeführten Cluster bereits belegt sind und alle nicht aufgeführten Cluster noch frei sind. Tragen Sie die benötigten Einträge in die Markdown-Tabelle ein und passen Sie alle betroffenen Tabellen entsprechend an.
