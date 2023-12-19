# Handlungsziel 5: Auditing und Logging

## Auswahl und Beschreibung des Artefakts
Im Rahmen dieses Handlungsziels habe ich einen Screenshot des Codes erstellt, welcher Einschränkungen für Personen vorsieht, die ein Passwort erstellen möchten. Dadurch werden die am häufigsten verwendeten Passwörter nach bestimmten Kriterien aussortiert.

## Nachweis der Zielerreichung
Das Handlungsziel wurde erreicht, indem ich demonstrierte, dass das Passwort bestimmte Anforderungen erfüllen muss, bevor es akzeptiert und gespeichert werden kann.

## Erklärung des Artefakts
Das Artefakt zeigt einen Codeabschnitt, der die Erstellung allzu einfacher Passwörter verhindert, wie beispielsweise "1234". Es sind nur Passwörter zulässig, die mindestens acht Zeichen lang sind und mindestens einen Grossbuchstaben, eine Ziffer und ein Sonderzeichen enthalten.

## Kritische Beurteilung
Dieses Handlungsziel wurde erfolgreich umgesetzt, da ich einen wichtigen Faktor hervorgehoben habe: den menschlichen Faktor. Man sollte jedoch weitere Schritte in der Implementierung hinzufügen und auf gewisse Methoden zurückgreifen, um es Angreifern schwerer zu machen wie Hashing, Salting und Zwei-Faktor-Authentifikation. Somit kann man zum einen sicherstellen das der Angreiffer bei Zugriff auf die Datenbank keine Passwörter einfach in Textform erhalten kann und zum anderen kann der Angreifer ohne Zugriff auf das Handy der Betroffenen Person sich nicht einloggen.
