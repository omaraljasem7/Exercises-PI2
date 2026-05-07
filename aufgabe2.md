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


## Lösung von Aufgab 2.1:
Die Inhalt von den 3 files: 
- starter.txt ist in Inode 8, in Inode 8 stehen diese direkten Clusteradressen 
42, 199, 73, 8 
D.h. die Inhalt der Datei starter.txt steht in den Adressen in der Reihenfolge 42 -> 199 -> 73 -> 8
- Inhalt ist : "Pikachu+Evoli"
- Die Datei starter.txt ist 12 Byte groß ,also 13/4 = 3.25 also ceil(3.25)=4 cluster aber letzter cluster liefert nur 1 Byte  weil: 
die ersten 3 clsuter sind 4 Byte groß also wir haben 12 Bytes und in dem cluster 8 : brauchen wir nur von  i^-^  das erste byte daher nur i

- legend.txt in Inode 17 (16 Bytes ):
- d.h. ich brauche 4 cluster weil 16 /4 =4 
- Die clusteradressen sind: 301, 15, 222, 89
- Inhalt : "Raikou_ist_stark"


- team.txt (in Inode 29 und ist 30 Bytes groß) : 
- 30 / 4 = 7.5 nach ceil =8 cluster d.h. die Inhalt von team.txt steht in genau 8 clsuters und diese sind in der Reihenfolge: 50, 178, 12, 234, 99, 9, 188, 241 (4*7 +2 Bytes= 30 Bytes d.h. vom 8. cluster brauche ich nur 2 Bytes)
- "Team_Rocket_Jessie+JamesMauzi!"


## Lösung von Aufabge 2.2:
**shiny.txt** mit Inode 25 soll zum Wurzelvereichnis hinzugefüt werden
Inhalt ist :Shiny-Suche läuft!
- Shiny -> 5 Byts 
- \- -> 1 Byte
- Suche -> 5 Bytes 
- leerzeichen -> 1 Byte 
- läuft -> 5 Bytes 
- ! -> 1 Byte 
- = 18 Bytes d.h. ich brauche 18/4 clusterss 4.5 also = 5 clusters 
- in den  clustern kommt nach einander : 
-  Shin
-  y-Su
-  che 
-  läuf
-  t!

**Die Belegeung der Cluster soll bei dem culuster 240 beginnen**
**240 -> 242 ->243->244 -> 246**

#### Hier ist die Modifikation der Tabelle 

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
| 240       | Shin      | 
| 242       | y-Su      |
| 243       | che       |
| 244       | läuf      |
| 246       | t!        |
| 241       | i!?@      |
| 245       | lum_      |
| 301       | Raik      |


## In der Inode Tabelle kommt ein neuer Eintrag 
### Inode Tabelle

| Inode | Typ         | Größe     | Direkte Clusteradressen             |
|-------|-------------|-----------|-------------------------------------|
|  1    | Verzeichnis | 64 Bytes  | 105, 203, 87, 156, ...              |
|  8    | Datei       | 13 Bytes  | 42, 199, 73, 8                      |
| 17    | Datei       | 16 Bytes  | 301, 15, 222, 89                    |
| 29    | Datei       | 30 Bytes  | 50, 178, 12, 234, 99, 9, 188, 241   |
| 35    | Datei       | 18 Bytes  | 240, 242,243,244,246                |

##  und in Inode1 : kommt ein neuer Eintrag in das Wurzelverzeichnis 

| Name          | Inode |
|---------------|-------|
| starter.txt   |  8    |
| legend.txt    | 17    |
| team.txt      | 29    |
| shiny.txt     | 35    |