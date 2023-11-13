# Mitgliedsdaten aus ZMI

Um den Aufwand der Dateneingabe während des Preisschießens zu reduzieren, können Mitgliedsdaten aus ZMI in das jeweilige
System importiert werden.

## Export aus ZMI

- Tab Import / Export
- TXT055
- Ggf. "Adresse und Telefonnummer exportieren" deaktivieren (Datensparsamkeit gem. DSGVO)
- Filter auf von Gau 105-Fürth bis Gau 105-Fürth setzen (ggf. nur in Bezirks-Version, auf Gau-Ebene sollte keine Einschränkung notwendig sein)
- "Export TXT055"-Button

Der Export enthält **alle** Mitglieder des Schützengaues Fürth.
Die exportierte Datei ist Windows-1250 (cp1250) codiert. Beim Öffnen kann es passieren, dass Sonderzeichen nicht korrekt
dargestellt werden. Im Normalfall sollte dies jedoch automatisch beim Import vom jeweiligen System berücksichtigt und
dort wieder korrekt dargestellt werden. 

## Filterung für Damengauschießen (optional)
Für bestimmte Preisschießen genügt ein Teil der exportierten Mitgliedsdaten aus ZMI (Datensparsamkeit gem. DSGVO).
Mit awk wird Spalte 8, die das Geschlecht enthält, auf den Wert 'W' für weiblich gefiltert. Es werden nur
die entsprechenden Zeilen ausgegeben. Hier am Beispiel auf einem Linux-System (z.B. Meyton-Anlage)
```shell
cat TXT055.dat | awk -F ';' '$8 ~ /W/' > DGS.dat
```
Das Resultat ist die Datei DGS.dat, die nur noch alle weiblichen Mitglieder des Gaues
enthält.

## Import in eine Meyton-Schießanlage
1. Anwendung Starterlisten starten
2. Stammdaten
3. Schützenstammdaten bearbeiten
4. Schützenstammdaten aus BSSBWin importieren.
5. TXT055.dat-Datei auswählen