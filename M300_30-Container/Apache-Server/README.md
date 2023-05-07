### **Erstelle ein Image**
```
docker build -t mein-image .
```

### **Erstelle ein Container**
```
docker run -d --name mein-container -p 8080:80 mein-image
```