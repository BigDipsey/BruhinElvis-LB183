# Cybersecurity

## Einleitung:
In diesem Portfolio werde ich über Cybersecurity aus den Perspektiven eines Angreifers und eines defensiven Programmierers reden. Ich werde auch bekannte Cybersecurity-Bedrohungen aufzeigen und wie man diese mit bekannten Methoden zum größten Teil unschädlich machen kann.

## Aktuelle Bedrohungen

### Phishing
**Was ist Phishing?**
Phishing ist, wenn Betrüger sich als vertrauliche Person oder Unternehmen ausgeben, um an private Daten zu kommen. Das machen sie meistens durch falsche E-Mails oder Nachrichten.

**Gegenmaßnahmen**
- Vorsichtiger Umgang mit E-Mails von unbekannten Absendern.
- Klicke nicht auf Links oder Anhänge in verdächtigen Nachrichten.
- Überprüfung von der E-Mail-Adresse auf komische Endungen.

### Malware
**Was ist Malware?**
Malware ist eine bösartige Software, die Schaden anrichten kann, wie Viren oder Trojaner.

**Gegenmaßnahmen**
- Ein Antivirenprogramm nutzen.
- Keine Dateien aus unsicheren Quellen herunterladen.
- Betriebssysteme und Software auf neuesten Stand halten.

### Ransomware
**Was ist Ransomware?**
Ransomware ist eine Art von Malware, die Dateien verschlüsselt und Lösegeld für das Entschlüsseln und Freigeben der Daten verlangt.

**Gegenmaßnahmen**
- Backups.
- Betriebssysteme und Software auf neuesten Stand halten.

### DDoS-Angriffe (Distributed Denial of Service)
**Was ist ein DDoS-Angriff?**
Bei einem DDoS-Angriff senden viele Computer gleichzeitig Anfragen an einen Server, um ihn lahmzulegen.

**Gegenmaßnahmen**
- Gute Netzwerksicherheit und Überwachung.
- Netzverkehr filtern.

## Sicherheitslücken
### JavaScript-Injections und SQL-Injections

Sicherheitslücken können in verschiedenen Interpretern auftreten, wenn bestimmte Zeichenfolgen als Befehle interpretiert werden. Dies geschieht besonders häufig an Stellen, an denen Benutzereingaben erforderlich sind. Angreifer können diese Schwachstellen ausnutzen, um schädliche Skripte einzufügen oder Befehle zur Manipulation der Authentifizierung durchzuführen.

#### Risiken:

- **JavaScript-Injections:** Angreifer könnten auf Benutzerdaten zugreifen und somit an persönliche Informationen gelangen oder ganze Scripts ausführen.
Das Cross-Site Scripting (XSS) ist, wenn der Angreifer ein solches Script ausgeführt hat und auf Informationen zugreifen kann und weiteren schädlichen Code auf dem Browser einer anderen Person installieren kann.
- **SQL-Injections:** Angreifer könnten auf Datenbanken zugreifen, Befehle durchführen, Daten abrufen und diese sogar ändern oder löschen, was die Integrität der Daten verletzt.

In diesem Fall habe ich eine SQL-Injection durchgeführt, wobei es nicht wichtig ist, was im Passwortfeld steht, solange ich 'administrator' als Nutzernamen eingebe. Das funktioniert, weil SQL-Befehle typischerweise mit einem Apostroph ' enden. Durch das Einfügen eines zusätzlichen Apostrophs am Ende des Nutzernamens und anschließendes Hinzufügen eines SQL-Kommentarzeichens (--), wird der restliche Teil der SQL-Abfrage auskommentiert. Somit wird der Authentifizierungsprozess manipuliert, da die Überprüfung des Passworts umgangen wird.

https://github.com/BigDipsey/BruhinElvis-LB183/assets/89131634/325ddb20-7adf-453d-8ad7-05dbca65b70f

## Authentifizierung und Autorisierung

### Hashing
Zuerst ist es wichtig, das Erlangen der Passwörter durch Angreifer zu erschweren. Dies erreicht man, indem man die Passwörter vor dem Speichern hasht. Durch das Hashing müssen Angreifer einen größeren Aufwand betreiben, um das Passwort zu entschlüsseln. Außerdem wird es für Mitarbeiter mit schlechten Absichten schwieriger, das Passwort zu missbrauchen und sich als ein anderer Nutzer auszugeben.

### Salting
Viele Systeme verwenden zusätzlich zum Hashing einen sogenannten Salt. Dies bedeutet, dass beim Eingeben eines Passworts automatisch ein Zusatz hinzugefügt wird, bevor das Passwort gehasht wird. Dieser Zusatz, der Salt, erhöht die Sicherheit, da Angreifer, die den Salt nicht kennen (selbst wenn sie den Hash-Mechanismus kennen), größere Schwierigkeiten haben, das Passwort zu ermitteln.

### Unsaubere API
Anschließend ist es wichtig, dass Abfragen, die ausschließlich im eingeloggten Zustand erfolgen sollten, auch nur dann möglich sind. Bei einer unsauberen API-Implementierung kann es vorkommen, dass zwar ein Login erforderlich ist, dieser aber nicht effektiv genutzt wird. Angreifer könnten in solchen Fällen auf bestimmte Abfragen zugreifen, ohne dass sie in einen Account eingeloggt sind. Dies stellt ein erhebliches Sicherheitsrisiko dar.
