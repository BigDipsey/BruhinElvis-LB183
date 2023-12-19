# Handlungsziel 5: Auditing und Loggin
```C#
public ActionResult<User> Login(LoginDto request)
        {
            if (request == null || request.Username.IsNullOrEmpty() || request.Password.IsNullOrEmpty())
            {
                return BadRequest();
            }
            string username = request.Username;
            string passwordHash = MD5Helper.ComputeMD5Hash(request.Password);

            User? user = _context.Users
                .Where(u => u.Username == username)
                .Where(u => u.Password == passwordHash)
                .FirstOrDefault();

            if (user == null)
            {
                _logger.LogWarning($"login failed for user '{request.Username}'");
                return Unauthorized("login failed");
            }

            _logger.LogInformation($"login successful for user '{request.Username}'");
            return Ok(CreateToken(user));
        }
```
Login fehlgeschlagen
![image](https://github.com/BigDipsey/BruhinElvis-LB183/assets/89131634/e06cc59c-b203-444f-8252-7b966d60ea22)

Login Erfolgreich
![image](https://github.com/BigDipsey/BruhinElvis-LB183/assets/89131634/019b6419-5e77-4b4c-9ea4-8d178e1f4082)




## Auswahl und Beschreibung des Artefakts
Im Rahmen dieses Handlungsziels habe ich einen Screenshot des Codes erstellt, welcher die Funktionalität des Auditing unn Logging zeigt.

## Nachweis der Zielerreichung
Das Handlungsziel wurde erreicht, indem ich demonstrierte, dass die Konsole beim Login die Informationen generiert.

## Erklärung des Artefakts
Das Artefakt zeigt einen Codeabschnitt, der für die Generierung verantwortlich ist.

## Kritische Beurteilung
Dieses Handlungsziel wurde erfolgreich umgesetzt, man muss jedoch beachten welche Informationen man zurück gibt Angreifer könnten genau diese Inforamtion für sich Nutzen zum Beispiel, wenn steht, dass das Passwort falsch ist weiss der Angreifer das es diesen Nutzer gibt und wenn er erfährt das der Nutzer nicht existiert kann er einfach andere Nutzer ausprobieren.
