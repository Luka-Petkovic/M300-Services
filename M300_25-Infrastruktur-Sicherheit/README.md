M300 - 25 Infrastruktur-Sicherheit
===

VM Vagrantfile - Firewall
===
In diesem Beispiel werden zwei virtuelle Maschinen definiert: "firewall" und "web". Beide virtuellen Maschinen basieren auf Ubuntu "Xenial64".

Die "firewall"-VM hat die IP-Adresse "10.0.0.10" und wird über den Hostnamen "Firewall" identifiziert. Diese VM wird über eine Shell-Provisionierung konfiguriert, um das ufw-Paket zu installieren. Danach wird die ufw-Firewall so konfiguriert, dass sie den eingehenden Datenverkehr auf Port 80, eingehenden Datenverkehr von der IP-Adresse "10.0.2.2" auf Port 22 und eingehenden Datenverkehr von der IP-Adresse "10.0.0.20" auf Port 3306 erlaubt.

![Firewall_Code](/Screenshot/Vagrantfile_Firewall_Firewall.png)

Die "web"-VM hat die IP-Adresse "10.0.0.20" und wird über den Hostnamen "web" identifiziert. Diese VM wird über eine Shell-Provisionierung mit dem Apache-Webserver installiert. Zusätzlich wird ein synchronisierter Ordner zwischen dem Host-Verzeichnis "html/" und dem Gast-Verzeichnis "/var/www/html" eingerichtet. Der Gast-Port 80 wird auf den Host-Port 8090 weitergeleitet.

![WEB_Code](/Screenshot/Vagrantfile_Firewall_Web.png)