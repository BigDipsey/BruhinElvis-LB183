# Cybersecurity

# Einleitung:
In diesem Portfolio werde ich über Cypersecurity aus den Perspektiven eines Angreifers und eines Defensiven Programmierers reden. Ich werde auch bekannte Cybersecurity Bedrohungen aufzeigen und wie man diese mit bekannten Methoden zum grössten Teil unschädlich machen kann.

## Aktuelle Bedrohungen

### Phishing
**Was ist Phishing?**
Phishing ist, wenn Betrüger sich als vertrauliche Person oder Unternehemn ausgeben, um an private Daten zu kommen. Das machen sie meistens durch falsche E-Mails oder Nachrichten.

**Gegenmassnahmen**
- Vorsichtigiger Umgang mit E-Mails von unbekannten Absendern.
- Klicke nicht auf Links oder Anhänge in verdächtigen Nachrichten.
- Überprüfung von der E-Mail-Adresse auf komische Endungen.

### Malware
**Was ist Malware?**
Malware ist eine bösartige Software, die Schaden anrichten kann, wie Viren oder Trojaner.

**Gegenmassnahmen**
- ein Antivirenprogramm nutzen.
- keine Dateien aus unsicheren Quellen herunterladen.
- Betriebssyteme und Software auf neusten Stand halten.

### Ransomware
**Was ist Ransomware?**
Ransomware ist eine Art von Malware, die Dateien verschlüsselt und Lösegeld, für das entschlüsseln und Freigeben der Daten verlangt.

**Gegenmassnahmen**
- Backups
- Betriebssyteme und Software auf neusten Stand halten.

### DDoS-Angriffe (Distributed Denial of Service)
**Was ist ein DDoS-Angriff?**
Bei einem DDoS-Angriff senden viele Computer gleichzeitig Anfragen an einen Server, um ihn lahmzulegen.

**Gegenmassnahmen**
- gute Netzwerksicherheit und Überwachung.
- Netzverkehr filtern



## Sicherheitslücken
### JavaScript-Injections und SQL-Injections

Sicherheitslücken können in verschiedenen Interpretern auftreten, wenn bestimmte Zeichenfolgen als Befehle interpretiert werden. Dies geschieht besonders häufig an Stellen, an denen Benutzereingaben erforderlich sind. Angreifer können diese Schwachstellen ausnutzen, um schädliche Skripte einzufügen oder Befehle zur Manipulation der Authentifizierung durchzuführen.

#### Risiken:

- **JavaScript-Injections:** Angreifer könnten auf Benutzerdaten zugreifen und somit an persönliche Informationen gelangen oder ganze Scripts ausführen.
Das Cross-Site Scripting (XSS) ist wenn der Angreifer ein solches Script ausgeführt hat und auf informationen zugreiffen kann und weiteren schädlichen Code auf dem Browser einer anderen Person Installieren kann.
- **SQL-Injections:** Angreifer könnten auf Datenbanken zugreifen, befehle durchführen, Daten abrufen und diese sogar ändern oder löschen, was die Integrität der Daten verletzt.
