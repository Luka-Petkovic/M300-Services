M300 - 25 Infrastruktur-Sicherheit
===

VM Vagrantfile - Firewall
===
In diesem Beispiel werden zwei virtuelle Maschinen definiert: "firewall" und "web". Beide virtuellen Maschinen basieren auf Ubuntu "Xenial64".

Die "firewall"-VM hat die IP-Adresse "10.0.0.10" und wird über den Hostnamen "Firewall" identifiziert. Diese VM wird über eine Shell-Provisionierung konfiguriert, um das ufw-Paket zu installieren. Danach wird die ufw-Firewall so konfiguriert, dass sie den eingehenden Datenverkehr auf Port 80, eingehenden Datenverkehr von der IP-Adresse "10.0.2.2" auf Port 22 und eingehenden Datenverkehr von der IP-Adresse "10.0.0.20" auf Port 3306 erlaubt.
```
Vagrant.configure("2") do |config|
  config.vm.define :firewall do |firewall|
      firewall.vm.box = "ubuntu/xenial64"
      firewall.vm.network :private_network, ip: "10.0.0.10"
      firewall.vm.hostname = "Firewall"
      firewall.vm.provision "shell", inline: <<-SHELL
      apt-get update
      sudo apt-get install ufw
      sudo ufw allow 80/tcp
      sudo ufw allow from 10.0.2.2 to any port 22
      sudo ufw allow from 10.0.0.20 to any port 3306
      sudo ufw --force enable
      SHELL
  end
```

Die "web"-VM hat die IP-Adresse "10.0.0.20" und wird über den Hostnamen "web" identifiziert. Diese VM wird über eine Shell-Provisionierung mit dem Apache-Webserver installiert. Zusätzlich wird ein synchronisierter Ordner zwischen dem Host-Verzeichnis "html/" und dem Gast-Verzeichnis "/var/www/html" eingerichtet. Der Gast-Port 80 wird auf den Host-Port 8090 weitergeleitet.
```
config.vm.define :web do |web|
      web.vm.box = "ubuntu/xenial64"
      web.vm.network :private_network, ip: "10.0.0.20"
      web.vm.hostname = "web"
      web.vm.network "forwarded_port", guest:80, host:8090, auto_correct: true
      web.vm.synced_folder "html/", "/var/www/html"
      web.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get -y install apache2 
      SHELL
  end
```

VM Vagrantfile - ReverseProxy
===
In diesem Vagrantfile werden ebenfalls zwei Virtuelle Maschinen hergestellt und definiert: eine für einen Reverse Proxy und eine für einen Webserver.

Für den Reverse Proxy wird die "ubuntu/xenial64" Box verwendet und er erhält eine private IP-Adresse von 10.0.0.10 im privaten Netzwerk. Der Reverse Proxy wird so konfiguriert, dass er auf Port 8080 auf dem Hostsystem lauscht und eingehenden Datenverkehr an Port 80 auf der virtuellen Maschine weiterleitet. Der Ordner "Config_File/" auf dem Hostsystem wird mit dem Ordner "/etc/ap0ache2/sites-enabled/" auf der VM synchronisiert, um Konfigurationsdateien auszutauschen. Die virtuelle Maschine wird auch als "reverseproxy" mit dem Hostnamen "reverseproxy" konfiguriert.
```
Vagrant.configure("2") do |config|
  config.vm.define :reverseproxy do |reverseproxy|
      reverseproxy.vm.box = "ubuntu/xenial64"
      reverseproxy.vm.network :private_network, ip: "10.0.0.10"
      reverseproxy.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true
      reverseproxy.vm.synced_folder "Config_File/", "/etc/apache2/sites-enabled/"
      reverseproxy.vm.hostname = "reverseproxy"

      reverseproxy.vm.provision "shell", inline: <<-SHELL
      apt-get update
      sudo apt-get install -y apache2
      sudo apt-get install libapache2-mod-proxy-html
      sudo apt-get install libxml2-dev
      sudo a2enmod proxy
      sudo a2enmod proxy_html
      sudo a2enmod proxy_http
      SHELL
      reverseproxy.vm.provision "shell", path: "scripts/init.sh"
      reverseproxy.vm.provision "shell", inline: <<-SHELL
      sudo service apache2 restart
      SHELL
  end
```

Für den Webserver wird ebenfalls die "ubuntu/xenial64" Box verwendet und er erhält eine private IP-Adresse von 10.0.0.20 im privaten Netzwerk. Der Webserver wird so konfiguriert, dass er auf Port 8090 auf dem Hostsystem lauscht und auf Port 80 auf der virtuellen Maschine antwortet. Der Ordner "html/" auf dem Hostsystem wird mit dem Ordner "/var/www/html" auf der VM synchronisiert, um Webinhalte auszutauschen. Die virtuelle Maschine wird auch als "web" mit dem Hostnamen "web" konfiguriert.
```
  config.vm.define :web do |web|
      web.vm.box = "ubuntu/xenial64"
      web.vm.network :private_network, ip: "10.0.0.20"
      web.vm.hostname = "web"
      web.vm.network "forwarded_port", guest:80, host:8090, auto_correct: true
      web.vm.synced_folder "html/", "/var/www/html"
      web.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get -y install apache2 
      SHELL
  end
```

VM Vagrantfile - ReverseProxy with Firewall
===
Bei diesem Vagranfile werden die Vagrantfiles Firewall und ReverseProxy zusammen gefügt:
```
Vagrant.configure("2") do |config|
    config.vm.define :reverseproxy do |reverseproxy|
        reverseproxy.vm.box = "ubuntu/xenial64"
        reverseproxy.vm.network :private_network, ip: "10.0.0.10"
        reverseproxy.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true
        reverseproxy.vm.synced_folder "configs/", "/etc/apache2/sites-enabled/"
        reverseproxy.vm.hostname = "reverseproxy"

        reverseproxy.vm.provision "shell", inline: <<-SHELL
        apt-get update
        sudo apt-get install apache2 -y
        sudo apt-get install ufw -y
        sudo apt-get install libapache2-mod-proxy-html -y
        sudo apt-get install libxml2-dev -y
        sudo a2enmod proxy
        sudo a2enmod proxy_html
        sudo a2enmod proxy_http
        sudo ufw allow from 10.0.2.2 to any port 22
        sudo ufw allow 80/tcp
        sudo ufw --force enable
        SHELL
        reverseproxy.vm.provision "shell", path: "scripts/init.sh"
        reverseproxy.vm.provision "shell", inline: <<-SHELL
        sudo service apache2 restart
        SHELL
    end



    config.vm.define :web do |web|
        web.vm.box = "ubuntu/xenial64"
        web.vm.network :private_network, ip: "10.0.0.20"
        web.vm.hostname = "web"
        web.vm.synced_folder "html/", "/var/www/html"
        web.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get -y install apache2 ufw -y
        sudo ufw allow from 10.0.2.2 to any port 22
        sudo ufw allow from 10.0.0.10 to any port 80
        sudo ufw --force enable
        SHELL
    end
end
```

VM Vagrantfile - Authentifizierung und Autorisierung
===

In diesem Vagranfile wird wieder die "ubuntu/xenial64" Box verwendet. Die Maschine hat eine statische IP-Adresse und hört auf Port 80 und 443. Der Ordner "config/" auf dem Host-System wird mit dem Ordner "/etc/apache2/sites-available/" auf der VM synchronisiert (In diesem Ordner sind die Konfigurationen drin, die benötigt werden, für das SSL Zertifikat), um Konfigurationsdateien auszutauschen. Dann wird Apache installiert und konfiguriert, um SSL zu unterstützen und ein selbst signiertes SSL-Zertifikat zu generieren. Die Standardkonfiguration von Apache wird deaktiviert und durch die neue Konfiguration ersetzt. In diesem Vagrantfile kann man einen User angeben, sowie den dazu gehöriges Passwort (Mit demm muss man sich dan auf der Website anmelden um reinzukommen). Schliesslich wird der Apache-Dienst neu gestartet
```
Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.network "forwarded_port", guest:443, host:443, auto_correct: true
    config.vm.network "forwarded_port", guest:80, host:80, auto_correct: true
    config.vm.hostname = "WebServer"
    config.vm.synced_folder "config/", "/etc/apache2/sites-available/"
    config.vm.provision "shell", inline: <<-SHELL
      apt-get update
      sudo apt-get install -y apache2
      sudo a2ensite 001-ssl.conf
      sudo a2enmod ssl
      sudo a2dissite 000-default.conf
      sudo a2dissite default-ssl.conf
      sudo htpasswd -b -c /etc/apache2/.htpasswd vagrant Passwort
      sudo service apache2 restart
    SHELL
  end
```