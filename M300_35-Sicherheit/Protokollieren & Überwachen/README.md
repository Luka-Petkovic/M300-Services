### **Erstelle ein Image**
```
docker build -t mein-image .
```

Nachdem ausführen des Befehls sollte das so aussehen:
![Architecktur Docker](Screenshots/Image.png)

### **Erstelle ein Container**
```
docker run -p 8080:8080 mein-image
```

Nachdem ausführen des Befehls sollte das so aussehen:
![Architecktur Docker](Screenshots/Container.png)

Schlussendlich sollte man unter http://localhost:8080 das hier sehen:
![Architecktur Docker](Screenshots/Ende.png)