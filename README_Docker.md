# M300 - Plattformübergreifende Dienste in ein Netzwerk integrieren
Noah Greuter

Version 1.0, 12.04.2019

#### Voraussetzungen für Servicenutzung

* PC mit min. 8 GB freiem RAM und ca. 20 GB freiem Harddisk.
* Ein schneller Netzwerk- (Kabel!) und Internet-Anschluss

### Inhaltsverzeichnis

* [Service Beschreibung]()
* [Technische Angaben]()
* [Testing]()
* [Trouble Shooting]()

## Service Beschreibung

Der Service den wir zur Verfügung stellen besteht aus 2 Service die mit Docker compose zusammengeführt werden.
Diese Service bestehen aus MariaDB als Datenbank für die Wordpress Webapplikation.

Zuerst wird mit einem Dockerfile ein Grundimage erstellt welches als Baustein für die 2 Container gilt.

Die Service werden mit dem Compose Deamon zusammengeführt zu einem Image zusammengeführt und als Container gestartet.

## Technische Angaben


Benötigte Tools:
* Docker Deamon
* Docker Compose Deamon
* Docker Windows Toolbox
* vagrant
* GitBash

Benötigte Images:
* Wordpress Image
* Maria DB

## Testing

Sofern die Dockercompose Datei gestartet wird über den Deamon und die Port auf dem Host geöffnet sind (8080 muss offen sein)

Dann kann man per 127.0.0.1:8080 auf den Wordpress Service zugreifen.

## Trouble Shooting

Als Alternative wurde der Daemon direkt per vagrant installiert auf einer Ubuntu 14.04- Umgebung. Die primäre Installation verlief ohne Probleme, jedoch liessen sich keine Images fehlerfrei erstellen. Bei Erstellung der Datenbank- Optionen kam es konstant zu einem «pileline Error», was die Erstellung der Datenbank unterbrach und den Prozess totlaufen liess. Es wurden acht Alternative, bezogen von verschiedenen Git- Repositories und Online- Guides, jedoch alle mit dem gleichen Fehler. Der Fehler lag dementsprechend in der Host- Umgebung des Containers, was wir aber nicht erschliessen konnten, weswegen nach mehren Fehlschlägen und investierten Stunden diese Option ausgeschlossen wurde.

![Bild7](/images/docker1.PNG)

![Bild8](/images/docker2.PNG)

![Bild9](/images/docker3.PNG)



--------------------
