### **Erstelle ein Image**
```
docker build -t my-mysql-image .
```

### **Erstelle des MySQL Container**
```
docker run --name my-mysql-container -p 3306:3306 -d my-mysql-image
```

### **Testen ob man sich mit dem Volume verbinden kann**
```
docker exec -it my-mysql-container mysql -u myuser -pmypassword mydatabase
```

### **Info**
Wenn du erfolgreich mit der Datenbank verbunden bist, bedeutet das, dass das Volume korrekt erstellt wurde und funktioniert.