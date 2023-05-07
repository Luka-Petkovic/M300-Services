Apache Server
===

Beim ausführen dieses Dockerfile wird ein Container erstellt, der einen Apache-Webserver und eine HTML-Seite bereitstellt. Der Benutzer kann auf diese Anwendung über einen Webbrowser zugreifen und die HTML-Seite mit der Nachricht "Das ist ein Test" anzeigen lassen.

### **Dockerfile**
In diesem Dockerfile wird das neueste Ubuntu-Basisimage als Grundlage verwendet, anschließend werden der Apache-Webserver und das curl-Programm installiert, die Konfigurationsdatei des Apache-Servers aktualisiert, die index.html-Datei in das Verzeichnis /var/www/html kopiert und der Container auf Port 8081 freigegeben. Abschließend wird der Befehl zum Starten des Apache-Servers definiert.

### **apache.conf**
Die apache.conf-Datei ist eine Konfigurationsdatei für den Apache-Webserver, die die grundlegenden Einstellungen für den Webserver definiert. Hier wird der Servername auf "localhost" und das Dokumentenverzeichnis auf "/var/www/html" gesetzt. Darüber hinaus werden die Berechtigungen für das Verzeichnis definiert, damit der Apache-Server auf die Dateien im Verzeichnis zugreifen und sie bereitstellen kann.

### **index.html**
Die index.html-Datei ist eine statische HTML-Seite, die im Apache-Webserver-Verzeichnis /var/www/html platziert wird. Sie enthält eine einfache HTML-Struktur mit einem Titel "M300-LB3" und einem Absatztext "Das ist ein Test". Wenn der Apache-Webserver gestartet ist, kann diese Seite im Webbrowser über die Adresse "localhost:8081" aufgerufen werden.

Apache HTTP to HTTPS
===

Dieser Dockerfile erstellt ein Docker-Image, das den Apache-Webserver mit aktiviertem SSL-Modul und Basis-Authentifizierung verwendet. Der Apache-Webserver wird im Vordergrund gestartet und die Ports 80 und 443 werden freigegeben.

### **Schritte**

1. Verwende das neueste offizielle Ubuntu-Image als Basis.
2. Setze den Maintainer des Images auf Apache.
3. Installiere den Apache-Webserver, SSL-Zertifikate und apache2-utils.
4. Aktiviere notwendige Apache-Module (ssl, rewrite, headers) und das SSL-Standard-Site.
5. Erstelle eine Umleitungsregel von Port 80 auf 443 in einer .conf-Datei.
6. Füge die Authentifizierungsanweisungen zur SSL-Konfigurationsdatei hinzu.
7. Setze die Umgebungsvariablen für Apache.
8. Erstelle notwendige Verzeichnisse für Apache.
9. Erstelle eine .htpasswd-Datei mit Basis-Authentifizierung.
10. Exponiere Ports 80 und 443.
11. Starte den Apache-Webserver im Vordergrund.

### **Verwendung**
Das erstellte Docker-Image kann verwendet werden, um einen Apache-Webserver mit SSL-Unterstützung und Basis-Authentifizierung in einem Docker-Container bereitzustellen. Die Ports 80 und 443 müssen freigegeben werden, damit der Container von außen erreichbar ist.

Dockerfile MySQL
===

Dieser Dockerfile erstellt ein Image für einen MySQL-Server mit vordefinierten Benutzer- und Datenbankinformationen.

### **Details**
Der Dockerfile basiert auf dem offiziellen MySQL-Image, das über Docker Hub bereitgestellt wird. Es wird eine Datenbank namens mydatabase erstellt und ein Benutzer mit den Zugangsdaten user:123456 angelegt. Der MySQL-Server wird auf Port 3306 freigegeben und automatisch gestartet, wenn der Docker-Container gestartet wird.

Image Bereitstellung
===

Dieses Dockerfile erstellt ein Image für einen Apache Webserver auf Basis des offiziellen Ubuntu 20.04 Images. Der Apache wird installiert, eine Beispiel-Webseite erstellt und der Port 80 wird für eingehende Verbindungen freigegeben. Die Zeitzone wird auf Europa/Berlin gesetzt.


Das erstellte Image des Apache-Webservers kann sowohl in einem privaten Unternehmen als auch auf Docker-Hub hochgeladen werden, um es später auf anderen Systemen oder in der Cloud zu verwenden. Durch das Hochladen in ein privates Unternehmen können Sie das Image innerhalb Ihres Netzwerks oder auf Ihren eigenen Servern speichern und verteilen, während das Hochladen auf Docker-Hub das Image der breiten Öffentlichkeit zugänglich macht.