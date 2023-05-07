### **Erstelle ein Image**
```
docker build -t mein-image .
```

### **Erstelle ein Container**
```
docker run -d --name mein-container -p 8080:80 mein-image
```

### **Wichtig!**
Die drei Dateien müssen sich im selben Verzeichnis befinden und der Benutzer muss im selben Verzeichnis sein, um die Befehle erfolgreich auszuführen.