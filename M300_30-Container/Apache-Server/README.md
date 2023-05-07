### **Erstelle ein Image**
```
docker build -t mein-image .
```

### **Erstelle ein Container**
```
docker run -d --name mein-container -p 8080:80 mein-image
```

### **Wichtig!**
Beim Ausführen dieser Befehle muss man im gleichen Verzeichnis sein wie der Dockerfile. Ebenfalls müssen alle 3 Datei im gleich Verzeichnis sein!