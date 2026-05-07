## Aufgabe 1: Dateisysteme &ndash; FAT

Helfen Sie dem Pokémon-Forschungsteam, die Daten eines antiken FAT-Speichers zu rekonstruieren. Der Speicher verwendet 4 Bytes pro Cluster statt der heute üblichen 4 kB.

### Daten

| Index | FAT       | Cluster [je 4 Byte]   |
|-------|-----------|-----------------------|
|  0    | 0x0000    | Bisa                  |
|  1    | 5         | Wir                   |
|  2    | 31        | E8gm                  |
|  3    | 0x0000    | Pika                  |
|  4    | 8         | http                  |
|  5    | 14        | <3 E                  |
|  6    | 0x0000    | Merr                  |
|  7    | 29        | -Aer                  |
|  8    | 9         | s://                  |
|  9    | 10        | www.                  |
| 10    | 11        | yout                  |
| 11    | 15        | ube.                  |
| 12    | 0x0000    | y ch                  |
| 13    | 0x0000    | rist                  |
| 14    | EOF       | voli                  |
| 15    | 16        | com/                  |
| 16    | 22        | watc                  |
| 17    | 0x0000    | mas_                  |
| 18    | 7         | Mega                  |
| 19    | 0x0000    | rand                  |
| 20    | EOF       | tyl_                  |
| 21    | 0x0000    | omst                  |
| 22    | 2         | h?v=                  |
| 23    | 0x0000    | uff_                  |
| 24    | 0x0000    | FooB                  |
| 25    | EOF       | PlI_                  |
| 26    | 0x0000    | sam_                  |
| 27    | 0x0000    | Knof                  |
| 28    | 0x0000    | ensa                  |
| 29    | 20        | odac                  |
| 30    | 0x0000    | Blab                  |
| 31    | 25        | ARGv                  |
### Stammverzeichnis

| Dateiname     | Datum      | Größe    | Startindex    |
|---------------|------------|----------|---------------|
| eevee.txt     | 04.02.2024 | 12 Bytes |  1            |
| song.txt      | 13.03.2007 | 43 Bytes |  4            |
| lost.txt      | 01.01.1970 | 15 Bytes | 18            |

1. Rekonstruieren Sie alle drei Dateien aus dem Stammverzeichnis. Geben Sie die Clusterkette und den Text in Ihrer Lösung an.
2. Speichern Sie anschließend folgende Nachricht im FAT-Speicher: `Relaxo ist mein Spirit-Pokémon`. Überschreiben Sie dabei nur freie Cluster. Das erste Cluster soll an Position 3 stehen. Nutzen Sie jeweils das nächstfolgende freie Cluster für Ihre Clusterkette und ergänzen Sie das Stammverzeichnis entsprechend (`Relaxo.txt`).

# Lösung von Rekonstruktion der 3 Dateien.
wir wissen dass in jedem Cluster 4 Bytes gespeichert werden 
wir sehen dass die Datei eevee.txt hat eine Groeße von 12 Bytes hat -> 12 / 4 = 3 clusters 

- clusterkette: 1 -> 5 -> 14 -> EOF ("Das sind genau 3 clusters")
- Inhalt: Wir <3 Evoli
  
file song.txt:
43 bytes / 4 bytes =  10.75 = 11 clusters nach ceil(10.75)
- clusterkette: 4 -> 8 -> 9 -> 10 -> 11 -> 15 -> 16 -> 22 -> 2 -> 31 -> 25 -> EOF
- Inhalt: https://www.youtube.com/watch?v=E8gmARGvPlI_
Inahlt ist ein youtube link 


file lost.txt (15 Bytes startindex ist 18)
15 / 5 = 3.75 nach ceil = 4 clusters 
- clusterkette: 18 -> 7 -> 29 -> 20 -> EOF
- inhalt: Mega-Aerodactyl_


Aufgabe 1.2: 
- sperichern von `Relaxo ist mein Spirit-Pokémon`
- startindex soll index 3 sein 
  - Relaxo -> 6 Bytes 
  - leerzeichen  -> 1 byte 
  - ist -> 3 bytes 
  - leerzeichen -> 1 byte 
  - mein -> 4 bytes 
  - leerzeichen -> 1  byte
  - Spirit -> 6 bytes 
  - \- -> 1 btyte
  - Pokémon -> 7 bytes 
  - Das sind genau  30 btyte
30 / 4  =   7.5 cluster nach ceil (7.5) = 8 clusters und in jedem cluster kommt genau 4 bytes bis auf den letzten cluster 

clusterkette : 
3 -> 6 -> 12 -> 13 -> 17 -> 19 -> 21 -> 23 
3 : Rela
6  : xo i 
12 : st m 
13 : ein 
17 : Spir
19 :it-P
21 :okém  
23 :on
#### hier ist die Modifikation der obigen Tabelle 
### Daten

| Index | FAT       | Cluster [je 4 Byte]   |
|-------|-----------|-----------------------|
|  0    | 0x0000    | Bisa                  |
|  1    | 5         | Wir                   |
|  2    | 31        | E8gm                  |
|  3    | **6**    | **Rela**                  |
|  4    | 8         | http                  |
|  5    | 14        | <3 E                  |
|  6    | **12**    | **xo i**                  |
|  7    | 29        | -Aer                  |
|  8    | 9         | s://                  |
|  9    | 10        | www.                  |
| 10    | 11        | yout                  |
| 11    | 15        | ube.                  |
| 12    | **13**    | **st m**                  |
| 13    | **17**    | **ein**    **hier gibt es leerzeichen nach ein**              |
| 14    | EOF       | voli                  |
| 15    | 16        | com/                  |
| 16    | 22        | watc                  |
| 17    | 0x0000    | **Spir**                  |
| 18    | 7         | Mega                  |
| 19    | **19**    | **it-P**                  |
| 20    | EOF       | tyl_                  |
| 21    | **23**    | **okém**                  |
| 22    | 2         | h?v=                  |
| 23    | **EOF**    | **on**                  |
| 24    | 0x0000    | FooB                  |
| 25    | EOF       | PlI_                  |
| 26    | 0x0000    | sam_                  |
| 27    | 0x0000    | Knof                  |
| 28    | 0x0000    | ensa                  |
| 29    | 20        | odac                  |
| 30    | 0x0000    | Blab                  |
| 31    | 25        | ARGv                  |


### hier kommt die Ergängung von dem Stammverzeichnis 
### Stammverzeichnis

| Dateiname     | Datum      | Größe    | Startindex    |
|---------------|------------|----------|---------------|
| eevee.txt     | 04.02.2024 | 12 Bytes |  1            |
| song.txt      | 13.03.2007 | 43 Bytes |  4            |
| lost.txt      | 01.01.1970 | 15 Bytes | 18            |
| Relaxo.txt    | 07.05.2026 | 30 Bytes | 3             |