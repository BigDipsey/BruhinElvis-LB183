# Handlungsziel 2: Erkennen und Schliessen von Sicherheitslücken

https://github.com/BigDipsey/BruhinElvis-LB183/assets/89131634/325ddb20-7adf-453d-8ad7-05dbca65b70f

Mit diesem Code kann ich verhindern das der Nutzer (') nicht als befehl eingeben kann. So wird das Statement sozusagen wie Vobereitet.

Code von ChatGPT
```C#
string sql = "SELECT * FROM Users WHERE username = @username AND password = @password";
SqlCommand command = new SqlCommand(sql, yourConnection);
command.Parameters.AddWithValue("@username", request.Username);
command.Parameters.AddWithValue("@password", MD5Helper.ComputeMD5Hash(request.Password));

```


### Auswahl und Beschreibung des Artefakts
Im Rahmen dieses Handlungsziels habe ich ein Video zu einer SQL Injection gemacht. Mein Artefakt zeigt wie ein Angreifer eine SQL Injection ausführen könnte um sich zugriff auf die Website zu verschaffen. 

### Nachweis der Zielerreichung
Das Handlungsziel wurde erreicht, indem ich eine Sicherheitslücke erkannt habe und diese mit Escaping geschlossen habe.

### Erklärung des Artefakts
Das Artefakt zeigt wie ich eine SQL Injection ausführe und zu einem Admin gemacht werde so muss ich als Angreifer das Passwort nicht kennen.

### Kritische Beurteilung
Dieses Handlungsziel wurde gut erreicht da ich jeweils einen Weg gezeigt habe mich einzuschleussen und auf der kehr seite wie ich dieses Problem lösen kann. Es ist jedoch wichtig zu beachten das es noch weitere Sicherheitslücken gibt und auch diese beim Programmieren bedenken muss, zum Beispiel Cross-Site Scripting (XSS) muss in solchen Sitationen auch bedacht werden. Diese können ein genau so grosses Risiko für Nutzer darstellen wie SQL-Injections
