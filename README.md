# M300-Services | Toolumgebungeng

GitHub Account
=======

### **SSH-Key erstellen**
Folgende Befehle im Bash ausführen:
1. Account E-Mail von Github eingeben
    ```
    ssh-keygen -t rsa -b 4096 -C "beispiel@beispiel.com"
    ```
2. SSH-Key wird erstellt
    ```
    Generating public/private rsa key pair.
    ```
3. Namensabfrage für den Schlüssel
   ```
   Enter a file in which to save the key (~/.ssh/id_rsa): 
   ```
4. Passwort setzten (Im ideal Fall hinterlegt man das gerade beim SSH-Agent)
    ```
    Enter passphrase (empty for no passphrase): [Passwort]
    Enter same passphrase again: [Passwort wiederholen]
    ``` 

### **SSH-Key dem SSH-Agent hinzufügen**

1. Man muss den Key bei seinem Account unter den Einstellungen hinterlegen:

![GitHub Konto SSH Keys](Screenshot/Github_SSH_Screenshot.png)

Git Client
======
### **Client installieren**

Den Git Client braucht man um Dateien auf Github Hoch und runter zuladen. [Git Download](https://git-scm.com/downloads)

### **Client konfigurieren**
1. Zunächst muss man zwei Befehle im Bash eingeben.

```
  git config --global user.name "<username>"
  
  git config --global user.email "<e-mail>"
```
### **Repository klonen**
1. Als nächstes wollen wir ein Repository klonen, dies machen wir im Bash.

```
git clone https://gitlab.com/ch-tbz-it/Stud/m300/
```
2. Damit das funktioniert, muss man ins richtige Verzeichnis wechseln.
```
cd M300
```
3. Damit das Repository aktualisiert wird, muss man zunächst den Folgenden Befehl eingeben.

```
git pull
```

4. Um den Status anzuzeigen, kann man den folgenden Befehl eingeben.

```
git status
```
### **Repository herunterladen & aktualisieren**

1. Zunächst wollen wir ein Ordner im gewünschten Verzeichnis wählen.

```
cd Wohin/auch/immer

mkdir MeinLokalesRepository
```
2. Repository mit SSH klonen

```
git clone git@github.com:<Ihr Name>/my_M300.git
```

3.Jetzt machen wir wieder das gleiche wie bei der letzten Aufgabe. Somit aktualisiert und prüft man den Status.

```
git pull
```

### **Repository hochladen**

1. Zum Verzeichnis wechseln

```
cd Pfad/zu/meinem/Repository
```
2. Die Daten hinzufügen, damit es beim Upload funktioniert

```
git add -A .
```
3. Die Bestätigung geben.

```
git commit -m "Mein Kommentar"
```
4. Upload pushen

```
git push
```


Virtualbox
======

### **Software herunterladen & installieren**

Damit wir fortfahren können, müssen wir VirtualBox herunterladen. 
[VirtualBox download](https://www.virtualbox.org/)

### **ISO-Datei herunterladen**


Damit unsere VM später funktioniert, brauchen wir logischerweise eine ISO, am besten verwendet man gerade diese: [Ubuntu-ISO](https://ubuntu.com/#download)

Damit die ISO-Datei Reproduzierbar ist, muss man es im gewünschten Verzeichnis ablegen. Hierzu muss man achten, dass es auf dem lokalen PC abgespeichert ist.

### **VM erstellen**

Die Schwirigkeit beim erstellen der VM lag bei der Dateigrösse... Ich hatte 10GB laut Anleitung genommen, das hat aber leider nicht funktioniert, da die VM immer wieder abstürzte... Also habe ich mich dazu entschieden 25GB zu nehmen, dannch hat es funktioniert. Wichtig ist ebenfalls dass man das richtige Medium ausgewählt hat. Die ISO Datei muss logischer Weise vorhanden sein.

### **VM einrichten**

Wichtig ist, dass die VM läuft, dannch muss man sich beim Bash anmelden. Paketliste muss nei eingelesen werden und die Pakete Aktualisiert. Dafür braucht man die Befehle:

```
sudo apt-get update   

#Paketlisten des Paketmanagement-Systems "APT" neu einlesen

sudo apt-get upgrade   

#Installierte Pakete wenn möglich auf verbesserte Versionen aktualisieren

sudo reboot           #System-Neustart durchführen
```

### **Synaptic installieren**

1. Synaptic ist zur Verwaltung von Debian-Paketen gemacht, kann aber auch mit RPM-Paketen umgehen. Darum müssen wir das herunterladen.
```
 sudo apt-get install synaptic
```
2. Synaptic öffnen und apache installieren

```
sudo reboot
```

Damit wir testen können, ob das ganze funktoniert hat, muss man prüfen, ob der Standard-Content des Webservers localhost erreichbar ist.

Vagrant
======

Was ist Vagrant eigentlich?

Ein Vagrant-file ist für die Automatisierung oder für die Reproduzierbarkeit. Somit kann man mit einer einfachen ausführung Virtuelle Maschienen erstellen lassen. Man kann nicht nur Virtuelle Maschienen erstellen sondern auch verwalten.


## **Software herunterladen & installieren**

1. Vagrant kann man unter dieser Internetseite herunterladen [Vagrant-Download](https://www.vagrantup.com/)
2. Für die Installation muss man nichts beachten. Wenn man den Download abgeschlossen hat, kann man mit dem Erstellen der Virtuellen Maschienen anfangen.

## **Virtuelle Maschine erstellen**

1. Damit wir ein sogennantes Vagrant-file erstellen können, müssen wir in ein gewünschtes Verzeichnis wechseln und dort einen Ordner erstellen. Nach dem erstellen des Ordners muss man auch gerade dort hin Navigieren.

```
cd Wohin/auch/immer
mkdir MeineVagrantVM
cd MeineVagrantVM
```

2. Vagrantfile erzeugen, VM erstellen und entsprechend starten:

```
vagrant init ubuntu/xenial64        
vagrant up --provider virtualbox    
```

3. Da die VM nun läuft, kann man über ssh zugreifen.

```
vagrant ssh
```

4. VM über GUI ausschalten.

Visual Studio Code
======

### **Software herunterladen & installieren**

1. Damit man eine effiziente Entwicklungsumgebung aufbauen kann, brachut man eine Applikation, welche dafür sorgt, dass man alle lokalen Repositories an einem Ort verwalten kann. Eine Gute Lösung dafür ist Visual Studio code.

2. Mit dem Folgenden Link kann man Visual Studio code herunterladen: [Visual Studio Code Download](https://code.visualstudio.com/)

### **Erweiterungen hinzufügen**
1. Damit das arbeiten leichter fällt, verwenden wir noch vier wichtige Erweiterungen:

* Markdown All in One
* Vagrant Extension
* vscode-pdf Extension
* Auto Markdown TOC
  
Diese erweiterungen kann man bei Visual Studio code an der Linken Seite finden... 

![Erweiterungen bei Visual Studio Code](/Screenshot/Erweiterungen.png)

### **Einstellungen anpassen**

1. Damit nicht alle Daten beim Cloud Repository hinzugefügt werden kann man eine sogennante .gitignor datei erstellen.
2. Hierzu ein Screenshot wie die Aussieht:

![Ausnahmen für Cloud-Repository](/Screenshot/Gitignore.png)

1. Ich würde euch meine gezeigten Einstellungen empfehlen.

### **Repository hinzufügen & pushen**

1. Damit man die Ganzen Änderungen hochladen kann, muss man an der Linken Seite unter Source Control gehen. Eine Nachricht hinzufügen und dann commit sagen. Nach dem man die Bestätigung gegeben hat und die Daten hochgeladen wurden, muss man noch Synchronisieren.

![Upload der Veränderungen](/Screenshot/Push_Changes.png)

Automatischer Web-Server | MyVagrant Folder
======
Navigieren sie im Folder "M300_10-Toolumgebung/MyVagrant" dort sollten sie ein Vagrantfile finden.
 
Mit diesem Vagranfile kann automatisch ein Web-Server erstellen ohne etwas gross zu machen. Mann muss nur diesen einen Befehl ausführen:
```
vagrant up
```
Wenn man diesen Befehl eingegeben hat, erstellt er eine Vm "Xenial64" und führt folgende Befehle aus:
```
config.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true #Leitet den Port 80 der VM (Gastsystem) an den Port 8080 des Hostsystems weiter
apt-get update
sudo apt-get install -y apache2
```
Sobald die VM erstellt wurde kann man unter der URL http://localhost:8080 die apache Website öffnen
```
http://localhost:8080
```
Testfälle
======
| Testfall                                           | geschätztes Ergebniss                       | effektives Ergebnis |
| -------------------------------------------------- | ------------------------------------------- | ------------------- |
| 1. Zugang via SSH                                  | Zugriff auf VM möglich                      | korrekt             |
| 2. Zugriff auf die Website                         | Zeigt apache-default-page                   | korrekt             |
| 3. Reproduzierbarkeit                              | VM kann genau gleich wieder erstellt werden | korrekt             |
| 4. VM kann von jemand anderes auch erstellt werden | bei Silvan genau gleich erstellt            | korrekt             |

Reflexion
======
Am Anfang hatten wir eine schwierige Zeit, um in das Thema reinzukommen. Das war aber nicht lange so. Nachdem wir uns ein wenig schlau gemacht haben und ein paar Test durchgeführt haben, wurde uns immer mehr und mehr klar. Wir waren stehts bei der Sache und hatten alle Aufgaben versucht zu meistern. Wir waren so verbissen das wir mehrere Stunden an einem Problem sassen, bis es schlussendlich funktionierte. Ich finde wir haben sehr gut und schnell gearbeitet und ich bin zufrieden mit unserer Leistung.

Wichtige Befehle
======

| Befehl        | Beschreibung                                                    |
|---------------|-----------------------------------------------------------------|
| `git init`    | Erstellt ein neues, leeres Git-Repository im aktuellen Verzeichnis |
| `git add`     | Fügt Änderungen der Arbeitskopie zum Staging-Bereich hinzu        |
| `git commit`  | Speichert die Änderungen im Repository und erstellt eine Version |
| `git clone`   | Erstellt eine lokale Kopie eines Remote-Repositories             |
| `git pull`    | Lädt die neuesten Änderungen aus einem Remote-Repository herunter |
| `git push`    | Überträgt lokale Änderungen an ein Remote-Repository             |
| `git branch`  | Erstellt, löscht oder zeigt Branches im Repository an            |
| `git merge`   | Führt zwei oder mehr Branches zusammen                           |
| `git status`  | Zeigt den Status der Arbeitskopie und des Repositories an        |
| `git log`     | Zeigt die Versionsgeschichte mit allen Commits an                |

Container
===

Ein Container ist ein Konzept der Informatik, das hilfreich ist, um Anwendungen in einer Umgebung auszuführen, die isoliert und unabhängig von anderen Anwendungen und dem Betriebssystem des Computers ist.

Ein Vorteil von Containern ist, dass sie portabel sind und auf verschiedenen Betriebssystemen und Servern ausgeführt werden können, solange sie die Container-Software unterstützen. Durch die Verwendung von Containern können Anwendungen schneller bereitgestellt und skaliert werden, da sie unabhängig von der zugrunde liegenden Infrastruktur sind und somit schneller und einfacher bereitgestellt werden können.

Docker
===

## Wichtige Befehle für Docker ##

| Befehl | Beschreibung |
| --- | --- |
| `docker build` | Baut ein Docker-Image aus einem Dockerfile |
| `docker run` | Startet einen Docker-Container aus einem Docker-Image |
| `docker stop` | Stoppt einen laufenden Docker-Container |
| `docker rm` | Löscht einen Docker-Container |
| `docker rmi` | Löscht ein Docker-Image |
| `docker ps` | Zeigt eine Liste der laufenden Docker-Container an |
| `docker images` | Zeigt eine Liste der verfügbaren Docker-Images an |
| `docker exec` | Führt einen Befehl in einem laufenden Docker-Container aus |
| `docker-compose up` | Startet Docker-Container mit Docker Compose |
| `docker-compose down` | Stoppt Docker-Container mit Docker Compose und löscht sie |
| `docker save` | Speichert ein Docker-Image als Tar-Datei |
| `docker load` | Lädt ein Docker-Image aus einer Tar-Datei |
| `docker login` | Meldet sich bei Docker Hub oder einer anderen Docker-Registry an |
| `docker push` | Lädt ein Docker-Image auf Docker Hub oder eine andere Docker-Registry hoch |
| `docker pull` | Lädt ein Docker-Image von Docker Hub oder einer anderen Docker-Registry herunter |

# Installation Docker Desktop und Aktivierung von WSL2 #

1. Laden Sie Docker Desktop für Windows herunter. 

Dazu kann man direk auf diese Webseite gehen. [Docker-Desktop](https://www.docker.com/products/docker-desktop/)

2. Führen Sie den Installationsassistenten aus. 

Öffnen Sie die heruntergeladene Datei "DockerDesktopInstaller.exe" und folgen Sie den Anweisungen des Installationsassistenten.

3. Konfigurieren Sie Docker Desktop. 

Nach Abschluss der Installation startet Docker Desktop automatisch. Möglicherweise müssen Sie jedoch den Computer neu starten, um Docker Desktop ordnungsgemäß zu starten. In den Einstellungen sollten man die Option "Use the WSL 2 based engine" auswählen. Wenn Sie dies tun, wird Docker Desktop WSL2 als Engine verwenden.

4. Aktivieren Sie WSL2.

Öffne Docker Desktop und gehene auf das Zahnrad. Unter "General" kann man nun WSL2 Aktivieren:

![WSL2 aktivieren](/Screenshot/WS2".png)

1. Installieren Sie eine Linux-Distribution.

Da Docker Desktop WSL2 als Engine verwendet, benötigen Sie eine Linux-Distribution, die auf Ihrem Computer ausgeführt werden kann. Ich empfehle Ubuntu 22.04.2 LTS:

![Ubuntu 22.04.2 LTS](/Screenshot/Ubuntu_W.png)


6. Überprüfen Sie die Installation.

Öffnen Sie ein PowerShell-Fenster und führen Sie den folgenden Befehl aus, um zu überprüfen, ob Docker Desktop ordnungsgemäß installiert und konfiguriert ist:
```
docker run hello-world
```
Wenn alles funktioniert hat, sollte es folgendermassen aussehen:
![Test Docker](/Screenshot/Docker_hello_World.png)



Somit hat man Docker Desktop erfolgreich auf Windows installiert und WSL2 aktiviert.

Docker Architecktur
===

![Architecktur Docker](/Screenshot/Grafik.png)

## Docker Deamon ## 

* Erstellen, Ausführen und Überwachen der Container

* Bauen und Speichern von Images

## Docker Client ##

* Docker wird über die Kommandozeile (CLI) mittels des Docker Clients bedient

* Kommuniziert per HTTP REST mit dem Docker Daemon

## Images ##

* Images sind gebuildete Umgebungen welche als Container gestartet werden können

* Images sind nicht veränderbar, sondern können nur neu gebuildet werden.

## Container ## 

* Container sind die ausgeführten Images.

* Ein Image kann beliebig oft als Container ausgeführt werden.
  

## Docker Registry ## 

* In Docker Registries werden Images abgelegt und verteilt.

Dockerfile
===

Ein Dockerfile ist ein Textdokument, das eine Abfolge von Anweisungen enthält, mit denen ein Docker-Image erstellt werden kann. Um ein Dockerfile zu erstellen, kann man zuerst ein neues Verzeichnis anlegen und darin eine Datei mit dem Namen "Dockerfile" erstellen.

Anschliessend kann das Image wie folgt gebuildet werden:
```
    $ docker build -t mysql .
```
Starten:
```
    $ docker run --rm -d --name mysql mysql
```
Funktionsfähigkeit überprüfen:
```
    $ docker exec -it mysql bash
```
Überprüfung im Container:
```
    $ ps -ef
    $ netstat -tulpen
```

Netzwerk-Anbindung
===

Das wichtigste bei den Netzwerk Anbindungen ist, dass man weiss wie man Aussenstehenden Personen zugriff gebenkann. Das ganze funktioniert mit Ports. Dafür braucht man folgenden Behfel: -p oder -P.

Um eine Verbindung zu einem Docker-Container herzustellen, der eine Anwendung ausführt, die auf einen bestimmten Port hört, muss der Port an den Host oder das Netzwerk weitergeleitet werden. Dazu kann man im Dockerfile die Ports, die die Anwendung nutzt, über die Anweisung "EXPOSE" eintragen. Dies ermöglicht es, dass andere Container oder Anwendungen über das Netzwerk auf den Container zugreifen und mit der Anwendung kommunizieren können.

Volumes
===

Bisher gingen alle Änderungen im Dateisystem verloren, wenn der Docker-Container gelöscht wurde. Um Daten auch über das Löschen des Containers hinaus zu erhalten, bietet Docker verschiedene Optionen:

* Daten auf dem Host ablegen: Man kann die Daten auf dem Hostsystem speichern, auf dem Docker läuft. Dadurch bleiben die Daten auch erhalten, wenn der Container gelöscht wird.

* Daten zwischen Containern teilen: Man kann Daten zwischen verschiedenen Containern teilen. Dadurch können mehrere Container auf dieselben Daten zugreifen und die Daten bleiben erhalten, auch wenn einer der Container gelöscht wird.

* Eigene Volumes erstellen: Man kann eigene Volumes erstellen, um Daten zu speichern. Diese Volumes sind unabhängig vom Container und können auch von anderen Containern genutzt werden. Dadurch bleiben die Daten erhalten, auch wenn der Container gelöscht wird.

Diese Optionen erlauben es, Daten auch über das Löschen eines Containers hinaus zu behalten und erleichtern die Verwaltung von Daten in Docker-Containern.

## Volume - Verzeichnis ##

Ein Volume ist ein spezielles Verzeichnis auf dem Hostsystem, in dem ein oder mehrere Docker-Container ihre Daten speichern können. Volumes bieten verschiedene nützliche Funktionen für die Verwaltung von persistenter oder gemeinsam genutzter Daten.

## Wie erstellt man ein neues Volume /data Verzeichnis? ##

Man muss den Folgenden Befehl einggeben, dass ein neues Docker Volume angelegt wird.

```
docker volume create data
```

Mit dem Folgenden Befehl kann man Überprüfen, ob der Befehl funktioniert hat. Somit werden alle verfügbaren Docker-Volumes aufgelistet.
```
docker volume ls
```

Damit man das Volume verwenden kann, muss man die folgenden Zeilen im Docker-Compose hinzufügen. Smoit wird "my-data" durch den gewünschten Namen des Volumes ersetzt.
```
volumes:
  my-data:
```

## Datencontainer ##

Wie starten man einen Container? Und wie kommen andere Personen darauf?

Um den Container zu starten, muss man den folgenden Befehl eingeben:
```
docker run
```
Um auf ein Container zugreifen zukönnen, muss man folgenden Behfel eingeben:
```
--volumes-from
```

## Named Volumes ##

Docker Volume ist seit Version 1.9 ein wichtiger Befehl, zur Verwaltung von Volumes auf einem Docker Host. Mit dem Befehl kann man ganz viele Sachen verwalten. Alle diese hier aufzuzählen macht aber keinen Sinn.


Image-Bereitstellung
===

Es existieren zahlreiche Optionen, um Images bereitzustellen. Man kann sie durch das Erstellen von Dockerfiles erstellen, von einer Registry mit "docker pull" herunterladen oder mithilfe von "docker load" aus einer Archivdatei installieren.

## Namensgebung für Images ##

Images bestehen aus einem Namen und einer Version, wobei bei fehlender Angabe automatisch ":latest" hinzugefügt wird. Um Images bereitzustellen, sind präzise und beschreibende Namen und Tags von entscheidender Bedeutung. Die Namen und Tags werden entweder beim Bauen der Images oder durch den Befehl "docker tag" festgelegt.

Bei den Tag-Namen muss man auf ein Paar Sachen achten:

* Gross- und Kleinbuchstaben
* Zahlen
* Symbolen . und -
* nicht länger als 128 Zeichen
* erstes Zeichen kein . oder -

Bei der Entwicklung eines Workflows ist es äußerst wichtig, sinnvolle Namen für Repositories und Tags zu verwenden. Docker hat nur wenige Einschränkungen bezüglich der Namensgebung und erlaubt jederzeit die Erstellung oder Löschung von Namen. Es obliegt also dem Entwicklungsteam, ein angemessenes Namensschema zu entwerfen und anzuwenden

## Warnung vor dem latest-Tag ##

Wenn bei einem "docker run" oder "docker pull" Befehl kein spezifischer Tag angegeben wird, verwendet Docker standardmäßig das Image, das mit "latest" gekennzeichnet ist. Wenn kein solches Image vorhanden ist, wird eine Fehlermeldung ausgegeben.

# Docker Hub #

Ein eigenes Images bereitzustellen ist am einfachsten, wenn man Dockers Hub verwendet.

Das Hub ist soweit kostenlos, man kann aber auch für Repositories von privaten Personen zahlen.

## Docker Hub einrichten ##

1. Zuerst muss man achten, dass man einen Docker Hub Account hat.
2. Image erstellen

```
docker tag mysql username/mysql
```

3. Um das Image hochzuladen, muss man den Befehl push mit verwenden.

```
docker push username/mysql
```

Dannach muss das Image noch beschrieben werden.

## Weitere Befehle ##

Nach einem Image kann man suchen mit folgendem Befehl:

```
docker search mysql
```
Um ein Image herunterzuladen, muss man den befehl pull verwenden:

```
docker pull ubuntu
```

# Export/Import von Container und Images #

Damit man Images zwischen zwei Hots hin und her verschieben kann, braucht man die Befehle docker export und docker import. Damit man Verzeichnisse hin und her kopieren kann, verwenden wir docker save und docker load.
```
docker export
```

```
docker import
```


Um seine eigenen Images sehen zu können, muss man folgenden Befehl ausführen:

```
/vagrant/mysql$ docker images
```
Wie kann ich mein Images wiederherstellen?

```
docker load
```


## TAR-Format ##

Das TAR-Format dient der Archivierung und Komprimierung von Dateien und Verzeichnissen und hat seinen Ursprung in der Sicherung von Daten auf Magnetbändern. Heutzutage wird es oft verwendet, um Dateien in einer einzelnen, komprimierten Datei für die Übertragung oder Speicherung zu archivieren. Um die Dateigröße weiter zu reduzieren, können TAR-Dateien mit verschiedenen Komprimierungsverfahren wie Gzip, bzip2 oder XZ komprimiert werden. Im Bereich von Docker-Images werden TAR-Dateien häufig als Archivdateien verwendet.

# Private Registry #

Es gibt verschiedene Möglichkeiten, Images neben dem Docker Hub bereitzustellen, aber die manuelle Erstellung oder der Export/Import von Images sind suboptimale Optionen. Das Erstellen von Images aus Dockerfiles auf jedem Host ist langsam und kann zu unterschiedlichen Images führen, während das Exportieren und Importieren von Images knifflig und fehleranfällig sein kann. Stattdessen wird empfohlen, eine andere Registry zu verwenden, die selbst gehostet oder von einem anderen Unternehmen betrieben wird.

[&uarr; nach oben](https://github.com/Luka-Petkovic/M300-Services)