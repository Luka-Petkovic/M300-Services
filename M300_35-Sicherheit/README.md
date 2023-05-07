Container sichern & beschränken
===

Das Dockerfile nutzt ein schlankes Python-3.9 Basisimage, um den Container klein zu halten und die Angriffsfläche zu reduzieren. Die Einschränkung der Berechtigungen durch die Erstellung eines eigenen Benutzers und die Verwendung einer requirements.txt-Datei minimieren die Angriffsfläche zusätzlich und erhöhen die Sicherheit der Anwendung

Protokollieren & Überwachen
===

Dies ist ein Dockerfile, das auf dem google/cadvisor-Image basiert und cAdvisor in einem Container bereitstellt. Der Port 8080 wird freigegeben, um auf die cAdvisor-Web-Schnittstelle zugreifen zu können. Der Befehl CMD startet cAdvisor mit den Optionen --logtostderr und --port=8080.

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