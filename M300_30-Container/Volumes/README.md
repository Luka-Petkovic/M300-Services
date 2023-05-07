### **Erstelle ein Image**
```
docker build -t my-mysql-image .
docker build -t my-test-image .
```

### **Erstelle des MySQL Container**
```
docker run --name my-mysql-container -v mysql-data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=mysecretpassword -e MYSQL_DATABASE=mydatabase -e MYSQL_USER=myuser -e MYSQL_PASSWORD=mypassword -d my-mysql-image
```

### **Erstelle des Test Container**
```
docker run --name my-test-container -v mysql-data:/test-volume -it my-test-image
```

### **Erstelle eine Datei vom Test Container aus**
```
docker exec -it my-test-container sh -c 'echo "Hallo, das ist eine Testdatei" > /test-volume/testfile2.txt'
```

### **Teste ob die Datei bei MySQL Container existiert**
```
docker exec -it my-mysql-container ls /var/lib/mysql
```

### **Info**
Jetzt sollte der Test-Container Zugriff auf das Volume des MySQL-Containers unter /test-volume haben. Beachte, dass diese Methode es beiden Containern ermöglicht, auf die Daten im gemeinsamen Volume zuzugreifen, aber sie können nicht direkt miteinander kommunizieren. Du kannst jedoch ein Netzwerk erstellen, wie in der vorherigen Antwort erwähnt, wenn sie miteinander kommunizieren müssen.