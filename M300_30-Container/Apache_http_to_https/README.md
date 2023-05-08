### **Erstelle ein Image**
```
docker build -t <image-name> .
```

![Architecktur Docker](Screenshots/Image.png)

### **Erstelle ein Container**
```
docker run -p 80:80 -p 443:443 -d <image-name>
```

Nachdem ausführen des Befehls sollte das so aussehen:
![Architecktur Docker](Screenshots/Container.png)

Beim aufrufen der Seite http://localhost sollte man direkt auf https:// geleitet werden und nach User gefragt werden:
![Architecktur Docker](Screenshots/User.png)
![Architecktur Docker](Screenshots/Ende.png)