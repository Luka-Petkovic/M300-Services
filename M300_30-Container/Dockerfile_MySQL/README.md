### **Erstelle ein Image**
```
docker build -t my-mysql-server .
```

### **Erstelle ein Container**
```
docker run --name my-mysql-container -p 3306:3306 -d my-mysql-server
```