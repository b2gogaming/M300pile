# M300 - LB1 Vagrant TeamSpeak- Server with centos7 + VLC server

![Bild1](/images/tsicon.JPG)

## Dokumentation zum Auftrag LB1

Als Auftrag wurde als Ziel gesetzt, mehrere Services mit vagrant aufzusetzen und zu sichern.

#### Auftragsvorraussetzungen

* Teamspeak- Server
* Wird über vagrant mit VirtualBox als Provider erstellt
* Firewall- Service und Sicherheitskonfiguration
* VLC Streaming Server
* mit vagrant aufgesetzt
* Sicherheitsserivice konfigurieren

## Inhaltsverzeichnis

* Modulbeschreibung
* Auftrag
* Planung
* Vorbereitung
* Teamspeak Server
* VLC Server
* Referenzen
* Analyse
 
 ------------------------------------------------------------

* Die Inhalte sind auf das Modul [300 Plattformübergreifende Dienste in ein Netzwerk integrieren](https://cf.ict-berufsbildung.ch/modules.php?name=Mbk&a=20101&cmodnr=300&noheader=1) zugeschnitten.
* Die Original Inhalte basieren auf dem Projekt [devops](https://github.com/mc-b/devops).
* Formatierungen und Icons von [Michael Blickenstorfer](https://github.com/TacoNaco47/M300), Besten Dank!

## Modulbeschreibung von ICT Berufsbildung
Link: https://cf.ict-berufsbildung.ch/modules.php?name=Mbk&a=20101&cmodnr=300&noheader=1

<b> Modul </b>     | Plattformübergreifende Dienste in ein Netzwerk integrieren
-------------------|---------------------------------------------------------------------------------------------------------------------------------------
<b> Kompetenz </b> | Plattformübergreifende Dienste nach Vorgabe für eine heterogene Systemumgebung konfigurieren, in Betrieb nehmen, testen und freigeben.
  
--------------------
  
- **Handlungsziele** 
  - **_Handlungsnotwendige Kenntnisse_** 
                      
1. Aus den Vorgaben die erforderlichen Dienste ermitteln, Schutz- und Sicherheitsanforderungen ableiten und ein Konzept für die Integration der Dienste ausarbeiten. 
   1. _Kennt die Einsatz- und Konfigurationsmöglichkeiten der vorgegebenen Betriebssysteme und Dienste._
 
2. Clients und Server gemäss Vorgaben konfigurieren, einrichten und geforderte Funktionalität überprüfen. 
   1. _Kennt die übliche (best practice) Vorgehensweise bei der Inbetriebnahme von Serverdiensten (zB. installieren, konfigurieren, starten, testen).
   2. _Kennt betriebssystemspezifische Konzepte zur Konfiguration von Software (zB. Konfigurationsdateien, Registry, systemweite / benutzerspezifische Konfiguration).
   3. _Kennt die Möglichkeiten von Betriebssystemen zur Gewährleistung und Absicherung des Zugriffs auf Netzwerk-Ressourcen (Authentifizierung, Autorisierung)._
   4. _Kennt die unterschiedlichen Konzepte, Systembefehle und Hilfsprogramme für die Benutzer- und Rechteverwaltung (zB. User-ID, Zugriffsrechte, Gruppenmitgliedschaft, Standardrechte, Vererbung, Homeverzeichnis)._
3. 	Netzwerkverbindungen einrichten, Dienste in Betrieb nehmen und testen. Definierte Schutz- und Sicherheitsmassnahmen überprüfen.
   1. _Kennt die Konfigurationsmöglichkeiten eines DHCP Servers (zB. Zuweisung einer IP Adresse, einer Subnet-Maske, Angaben zu DNS-Servern, Standard-Gateways)._
   2. _Kennt die Konfigurationsmöglichkeiten eines DNS-Servers._
   3. _Kennt die notwendigen Einstellungen bei einem Client in einer DHCP-/DNS-Serverumgebung._
   4. _Kennt die Elemente und Funktionen des TCP/IP-Protokolls (zB. MAC- und IP-Adressen, IP-Adressklassen, private Adressen, Netzmasken, Routing, Adress Resolution Protocol (ARP), wichtige Portnummern)._
4. Anwendungen und Tools installieren, einrichten und geforderte Funktionalität überprüfen und gemeinsame Ressourcen einbinden 	
   1. _Kennt technische Möglichkeiten um Ressourcen im Netzwerk durch Gruppen gemeinsam zu nutzen (zB. Groupware)._
5. Allfällige Fehler systematisch eingrenzen, protokollieren und Massnahmen zur Fehlerbehebung einleiten. 	
   1. _Kennt Methoden zur systematischen Fehlereingrenzung (zB. Ausschlussverfahren intakter Systeme)._
   2. _Kennt Werkzeuge zur Fehleranalyse und –behebung._
   3. _Kennt den Aufbau und die wesentlichen Merkmale eines Testprotokolls._
6. Dokumentation für die Administration des Netzes, der Rollen und Rechte und der eingerichteten Dienste und Anwendungen erstellen.
   1. _Kennt Aufbau und Inhalt einer Netzwerk- und Systemdokumentation._
    	 

<tab>    | <tab>
--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Kompetenzfeld**   | System Management
**Objekt**        | Clients, Server (File, Print, DNS, DHCP, Directory Services, Terminal, SSH, Web) und Peripherie mit unterschiedlichen Betriebssystemen in einem einfachen Netzwerk.
**Niveau**        | 3
**Voraussetzung** | Konfigurieren und betreiben von PCs. Servern und Peripherie (Multiusersysteme) Erfahrung im Aufbau von lokalen Netzwerken

## Auftrag

Der Auftrag setzt sich aus zwei Eckpunkten zusammen: Definieren eines oder mehreren Diensten durch IaC (Infrastructure as Code) und diese per Vagrant auf der Virtualbox- Umgebung zu virtualisieren.

Im Tandem mit Greuter Noah überlegten wir uns, welche Dienste wir für diesen Auftrag zusammenstellen wollen. Die ersten Ideen waren:

* Webserver (Apache2) mit weiteren Funktionen
* BackUp Service
* Monitoring Tool
* VLC Streaming Server
* Teamspeak Server (mit Client)

Unsere Entscheidung fiel auf die beiden Dienste Teamspeak und VLC. Der VLC Dienst wurde von Herrn Noah Greuter erarbeitet, während der Teamspeak Server von Herrn Nishan Kotuwattegedera ausgearbeitet wurde.

## Vorbereitung und Tools
#### Tools
Für die Aufgabe wurden folgendende Tools:
* GitHub
* GitClient
* Visual Studio Code
* GitBash
* Vagrant
* VirtualBox
* Markdown

Github: GitHub ist eine offene Development Plattform, die es weltweit Entwicklern erlaubt ihre Codes teilen, testen und auszutauschen. GitHub macht sich essentielle Service zum eigen, wie Branches, Repositories, Commits, PullRequests und Git (die Kontroll- Software, auf welcher GitHub basiert).

GitClient: Ein GitClient ist eine Software, welche mit Repositories arbeitet, remote und lokal.

Visual Code Studio: VCS ist ein Source- Code Editor, welches von Microsoft entwickelt wurde. Es erlaubt die Bearbeitung von Codes, Shells und config- Files.

GitBash: Eine Software, welche die beiden Kontroll- Softwares "git" und "bash" umfasst, und diese Bearbeiten und Ausführen kann.

Vagrant: Eine Open- Source Software, um virtuelle Maschinen zu bauen und zu verwalten. Es kreiert die VMs nach einem vorgegebenen Algorithmus, was es erlaubt mehrere Maschinen nach einem gleichem Schema zu erstellen.

VirtualBox: Eine Open- Source HyperV- Virtualisierungssoftware, welche hier in diesem Auftrag, das Skelett für Vagrant darstellt.

Markdown: Eine Git- basierte Sprache, welche für README- Dokumentationen auf GitHub verwendet werden.

#### Vorbereitung
Bevor wir mit dem Projekt loslegen konnten, mussten wir uns zu unseren Servicen informieren: 

Teamspeak: Eine Live- Chat Software, welche mit einer Serverbasierten Struktur arbeitet.

VLC: Eine Open- Source Media Cross- Plattform Player- und Streaming Software.

## Teamspeak Server auf Basis centos7 Box auf Vagrant
Bevor man mit der Erstellung der Maschine beginnt, erstellt man mit GitBash eine lokale Ablage (hier "teamspeakvm"). Danach GitBash starten, mit dem Kommand "cd teamspeakvm" in die Ablage wechseln.

Nun wird vagrant mit dem Kommand "vagrant init" gestartet und eine Erstumgebung initialisiert.

Nachdem man die Umgebung erstellt hat, muss das vagrant File angepasst werden, sodass es unseren Bedürfnissen entspricht. In diesem Fall einem Teamspeak- Server.

![Bild2](/images/vfile.PNG)

* Die VM wird provisioniert auf die TSS Instance.
* Eine Box CentOS7 wird erstellt
* Der Hostname wird gesetzt auf ts-server
* Der Provider wird definiert.
* Die Spezifikationen der VM werden vorgegeben.
* Die IP wird gesetzt. Hier durch DHCP.
* Schluss endlich werden noch die nötigen Zusatzsoftwares installiert über Shell Commands.

(Installation des TSS Services, der Firewall und des eigentlichen unterstützten Servers.)

(Notiz:Der VM Name in Virtualbox darf nicht gesetzt werden, da dies zu einem unerwarteten Error führt.)

#### Shells und Service
Auf dem Server müssen verschiedene Dienste zusätzlich installiert werden, damit nebst der Sicherheit, auch der eigentlich Dienst funktioniert.

Folgende drei Dienste müssen definiert und installiert werden:

* Firewall
* Serverinfrastruktur
* Server- Systemdienste

Diese werden über Shell Commands in das Vagrantfile eingespielt, sodass diese beim Start der VM automatisch verwirklichen.

![Bild3](/images/addFirewall.PNG)

![Bild4](/images/installApp.PNG)

![Bild5](/images/addSystem.PNG)

## Start des Servers/ IP

Der Server muss im NAT Modus gestartet werden. Sobald der Server komplett durchgestartet ist, kann man sich mit dem Kommand "vagrant ssh" auf das Server Interface verbinden. 

Um die IP des Servers zu ermitteln, gibt man den Kommand "ip address" ein. Die Server IP ist unter dem eth1 herauszufiltern.

## Client und Connect

Um sich auf den Server zu verbinden, muss ein ein Teamspeak Client heruntergeladen werden.

Unter der Option "Connections/ Verbinden" kann man die nun bekannte Server IP eingeben, sich einen Nicknamen setzen und Verbinden. Der Server wurde so definiert, dass kein Server- Passwort gesetzt erstellt wurde.

![Bild6](/images/tsclient.PNG)