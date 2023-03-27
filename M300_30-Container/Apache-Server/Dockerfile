# Basisimage auswählen
FROM ubuntu:latest

# Arbeitsverzeichnis erstellen
WORKDIR /app

# Apache Webserver und curl installieren
RUN apt-get update && \
    apt-get install -y apache2 curl && \
    rm -rf /var/lib/apt/lists/*

# Konfigurationsdatei des Apache-Servers aktualisieren
COPY ./apache.conf /etc/apache2/sites-available/000-default.conf

# Index.html File hinzufügen
COPY ./index.html /var/www/html/

# Exponiere Port 8081
EXPOSE 8081

# Startbefehl definieren
CMD ["apachectl", "-D", "FOREGROUND"]