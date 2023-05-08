Container sichern & beschränken
===

Das Dockerfile nutzt ein schlankes Python-3.9 Basisimage, um den Container klein zu halten und die Angriffsfläche zu reduzieren. Die Einschränkung der Berechtigungen durch die Erstellung eines eigenen Benutzers und die Verwendung einer requirements.txt-Datei minimieren die Angriffsfläche zusätzlich und erhöhen die Sicherheit der Anwendung

Wichtigste Befehle im Dockerfile:
```
RUN groupadd -r appuser && useradd -r -g appuser appuser

RUN pip install --no-cache-dir -r requirements.txt

RUN chown -R appuser:appuser /app
USER appuser

CMD ["python", "app.py"]
```

app.py File um eine Test Website darzustellen:
```
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return "Hello, World!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=8080)
```

[&uarr; nach oben](https://github.com/Luka-Petkovic/M300-Services/tree/main/M300_35-Sicherheit)

Protokollieren & Überwachen
===

Dies ist ein Dockerfile, das auf dem google/cadvisor-Image basiert und cAdvisor in einem Container bereitstellt. Der Port 8080 wird freigegeben, um auf die cAdvisor-Web-Schnittstelle zugreifen zu können. Der Befehl CMD startet cAdvisor mit den Optionen --logtostderr und --port=8080.

Code im Dockerfile um cadvisor zu starten:
```
CMD ["/usr/bin/cadvisor", "--logtostderr", "--port=8080"]
```

[&uarr; nach oben](https://github.com/Luka-Petkovic/M300-Services/tree/main/M300_35-Sicherheit)

Testfälle
======
| Testfall                                                  | geschätztes Ergebniss                       | effektives Ergebnis |
| --------------------------------------------------------- | ------------------------------------------- | ------------------- |
| 1. Image erstellen                                        | Image wird erfolgreich erstellt             | korrekt             |
| 2. Container erstellt                                     | Container wird erfolgreich erstellt         | korrekt             |
| 3. Container ist abrufbar                                 | Container konnte abgerufen werden           | korrekt             |
| 4. Reproduzierbarkeit                                     | Container wird genau gleich erstellt        | korrekt             |
| 5. Container kann von jemand anderes auch erstellt werden | bei Emir genau gleich erstellt              | korrekt             |

[&uarr; nach oben](https://github.com/Luka-Petkovic/M300-Services/tree/main/M300_35-Sicherheit)