### **Erstelle ein Image**
```
docker build -t mein-image .
```

### **Erstelle ein Container**
```
docker run -d --name mein-container -p 8080:80 mein-image
```

### **Wichtig!**
Alle 3 Dateien müssen im gleichen Verzeichnis sein. Beim ausführen dieser Befehele muss man ebenfalls im gleichen Verzeichnis sein wie diese 3 Dateien.