Container sichern & beschränken
===

Das Dockerfile nutzt ein schlankes Python-3.9 Basisimage, um den Container klein zu halten und die Angriffsfläche zu reduzieren. Die Einschränkung der Berechtigungen durch die Erstellung eines eigenen Benutzers und die Verwendung einer requirements.txt-Datei minimieren die Angriffsfläche zusätzlich und erhöhen die Sicherheit der Anwendung

Protokollieren & Überwachen
===

Dies ist ein Dockerfile, das auf dem google/cadvisor-Image basiert und cAdvisor in einem Container bereitstellt. Der Port 8080 wird freigegeben, um auf die cAdvisor-Web-Schnittstelle zugreifen zu können. Der Befehl CMD startet cAdvisor mit den Optionen --logtostderr und --port=8080.