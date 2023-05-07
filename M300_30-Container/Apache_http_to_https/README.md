### **Erstelle ein Image**
```
docker build -t <image-name> .
```

### **Erstelle ein Container**
```
docker run -p 80:80 -p 443:443 -d <image-name>
```