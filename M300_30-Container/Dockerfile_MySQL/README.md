### **Erstelle ein Image**
```
docker build -t my-mysql-server .
```

Nachdem ausführen des Befehls sollte das so aussehen:
![Architecktur Docker](Screenshots/Image.png)

### **Erstelle ein Container**
```
docker run --name my-mysql-container -p 3306:3306 -d my-mysql-server
```

Nachdem ausführen des Befehls sollte das so aussehen:
![Architecktur Docker](Screenshots/Container.png)

Schlussendlich sollte man unter Docker das hier sehen:
![Architecktur Docker](Screenshots/Ende.png)