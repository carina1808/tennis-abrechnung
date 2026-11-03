# Projektbeschreibung – Tennis-Abrechnung

**Stand:** 03.11.2026  
**Aktuelle Version:** 3.2  
**Plattform:** Installierbare Progressive Web App (PWA) für Android  
**Repository:** `https://github.com/<BENUTZERNAME>/tennis-abrechnung`  
**App-Adresse:** `https://<BENUTZERNAME>.github.io/tennis-abrechnung/`

> `<BENUTZERNAME>` durch den eigenen GitHub-Benutzernamen ersetzen. Diese Projektbeschreibung enthält keine persönlichen Abrechnungsdaten.

## 1. Ziel und Nutzung

Private App zur Erfassung und Abrechnung von Tennistrainings. Die Nutzerin verwendet ausschließlich ein Android-Smartphone; ein PC ist nicht erforderlich. Die App wird über GitHub Pages per HTTPS bereitgestellt und über Chrome auf dem Startbildschirm installiert. Nach dem Laden ist die App dank Service Worker grundsätzlich offline nutzbar. Die Trainings- und Zahlungsdaten werden **lokal im Browser-Speicher des jeweiligen Geräts** gespeichert, nicht in GitHub oder in einer Cloud-Datenbank.

## 2. Navigation und Bedienung

Untere Navigationsleiste mit **Start**, **Termine**, **Personen**, **Material**, **Auswertung**. Der aktive Menüpunkt ist farblich markiert; beim Bearbeiten eines Termins bleibt „Termine“, beim Bearbeiten eines Materialpostens „Material“ aktiv.

Oberfläche für Smartphone-Bildschirme optimiert. Symbole: Plus zum Hinzufügen, Stift zum Bearbeiten, dezentes Kreuz zum Entfernen/Löschen. Vor Löschungen beziehungsweise Massen-Zahlungsbestätigungen erfolgt eine Rückfrage. Datumsangaben werden in Übersichten und Berichten als **TT.MM.JJJJ** dargestellt. Technisch werden Datumswerte für die Sortierung als ISO-Datum (`YYYY-MM-DD`) gespeichert.

## 3. Personen

- Beliebig viele Teilnehmerinnen anlegen, umbenennen und aus der aktiven Liste entfernen.
- Personen- und Teilnehmerauswahllisten alphabetisch nach Namen sortieren.
- Entfernen aus der aktiven Liste archiviert eine Person; historische Termine und Zahlungen bleiben erhalten.
- Pro Person in der Personenübersicht anzeigen: **Anzahl Teilnahmen** und **Summe tatsächlich als bezahlt markierter Beträge**.
- Höchstens **vier Teilnehmerinnen je Trainingstermin**; dies ist unabhängig von der Gesamtzahl der angelegten Personen.

## 4. Trainingstermine

Jeder Termin enthält:

- Datum und Uhrzeit (Stunden 00–23, Minuten 00–59; bei neuen Terminen ist Minute **00** vorausgewählt).
- Platzart **Halle** oder **Freiluftplätze**.
- Bei Halle: Hallenkosten und Lichtgeld als bearbeitbare Beträge.
- Bei Freiluftplätzen: Hallenkosten und Lichtgeld automatisch **0 €**.
- Ein bis vier ausgewählte Teilnehmerinnen.
- Individuellen Rechnungsbetrag **und** Zahlungsstatus („Bezahlt“/„Offen“) je Teilnehmerin.

Mehrere Termine am selben Datum mit unterschiedlicher Uhrzeit und unterschiedlichen Teilnehmerinnen sind möglich und werden getrennt abgerechnet. Termine können angelegt, bearbeitet und nach Bestätigung gelöscht werden. Beim Bearbeiten sind zunächst nur die ausgewählten Personen als Kacheln sichtbar; weitere können ergänzt werden. Teilnehmerkacheln sollen einheitlich und kompakt gestaltet sein: Name/Teilnahme, individueller Betrag, Zahlungsstatus. Der Speichern-Button ist auch ohne Scrollen bis zum Ende erreichbar. Ein gesetzter Zahlungsstatus kann beim Bearbeiten wieder zurückgenommen werden.

### Terminübersicht

- **Neueste Termine zuerst**, bei gleichem Datum spätere Uhrzeit zuerst.
- Gruppierung zuerst nach **Jahr**, darin nach **Monat**; beide Ebenen unabhängig auf- und zuklappbar.
- Neueste Jahre und Monate stehen oben.

## 5. Preisberechnung

Standardmäßiger **Preisvorschlag je Teilnehmerin**:

`Abrunden_auf_0,50_EUR((Hallenkosten + Lichtgeld + 30,00 EUR) / Anzahl_Teilnehmerinnen)`

Das bedeutet: Immer **abrunden**, nicht kaufmännisch runden. Beispiel bei Hallenkosten 20 €, Licht 2 € und drei Personen: `(20 + 2 + 30) / 3 = 17,333… €`, Vorschlag **17,00 € pro Person**.

- Standardmäßig erhalten alle ausgewählten Teilnehmerinnen denselben Vorschlagsbetrag.
- Ein gemeinsamer Betrag kann manuell gesetzt werden.
- Alternativ kann für jede Teilnehmerin **ein eigener Betrag** eingegeben werden.
- Die tatsächlich eingetragenen individuellen Beträge sind maßgeblich für Einnahmen, offene Zahlungen, Personenstatistiken und Berichte.
- Bei Freiluftplätzen entfallen Hallen- und Lichtkosten in der Formel; das Gewinnziel von 30 € bleibt Bestandteil des Vorschlags.
- Das Gewinnziel ist eine **Berechnungsgrundlage**, keine garantierte Einnahme.

## 6. Startseite

Sechs Kennzahlen in kompakter zweispaltiger Anordnung, in genau dieser Reihenfolge:

| Links | Rechts |
| --- | --- |
| Termine | Trainingstage |
| Einnahmen | Verdienst |
| Material | Halle und Licht |

- **Termine** = Anzahl gespeicherter Trainingseinheiten.
- **Trainingstage** = Anzahl unterschiedlicher Kalendertage mit mindestens einem Termin; z. B. 25 Termine an 18 Tagen = **25 Termine, 18 Trainingstage**. Das dient auch als Grundlage einer späteren Kilometerberechnung.
- **Einnahmen** = Summe aller für Termine berechneten Teilnehmerbeträge, unabhängig vom Zahlungseingang.
- **Verdienst** = Einnahmen minus Hallen-/Lichtkosten minus Materialkosten.
- **Material** = Summe erfasster Materialausgaben.
- **Halle und Licht** = Summe der Platz-/Lichtkosten.

Darunter folgt der Abschnitt **Offene Zahlungen**: Gesamtbetrag unmittelbar **oberhalb** der nach Teilnehmerin zusammengefassten offenen Beträge. Jede Person wird nur einmal mit ihrer offenen Gesamtsumme angezeigt. Pro Person sind folgende Aktionen verfügbar:

1. **Einzeln bezahlen:** Offene Termine mit Datum, Uhrzeit und Betrag einblenden und einzeln als bezahlt markieren.
2. **Alles bezahlt:** Sämtliche offenen Terminbeträge dieser Person nach Sicherheitsabfrage als bezahlt markieren.

Eine versehentlich erfasste Zahlung kann weiterhin im jeweiligen Termin zurückgenommen werden.

## 7. Material

Eigenständiger Menüpunkt **Material** für Tennisbälle und sonstige Ausgaben. Pro Materialposten werden **Bezeichnung**, **Kaufdatum** und **Preis** erfasst. Posten können hinzugefügt, bearbeitet und über ein dezentes Kreuz in der Materialliste gelöscht werden. Materialkosten fließen in Startseiten-Verdienst und Zeitraum-Auswertung ein; für die Zuordnung zum Zeitraum zählt das **Kaufdatum**.

## 8. Auswertung und PDF

- Beliebiger Datumsbereich (z. B. Wintersaison).
- Auswertung der Termine, Einnahmen, Hallen-/Lichtkosten, Materialausgaben, Gesamtkosten, Verdienst, erhaltenen Zahlungen und offenen Forderungen.
- Bei Terminen zählt das **Trainingsdatum**, bei Material das **Kaufdatum**.
- PDF-Ausgabe über die Browser-Druckfunktion („Als PDF speichern“); kein eigener serverseitiger PDF-Dienst.
- Bericht enthält Termine mit Datum/Uhrzeit, Platzart, Kosten, individuellen Teilnehmerbeträgen und Zahlungsstatus sowie Materialposten.

## 9. Datenspeicherung und Sicherung

**Technik:** HTML, CSS und JavaScript in `index.html`; `manifest.webmanifest` für die Installation, `sw.js` für Offline-Cache, `icon.svg` als Symbol und `README.txt` als Kurzanleitung.

**Speicher:** `localStorage` unter dem Schlüssel `tennisabrechnung_v1`. Der Datenbestand enthält Arrays für `people`, `sessions` und `materials`. Beträge werden intern in **Cent** gespeichert, um Rundungsprobleme zu vermeiden. Termine enthalten Einträge je Person mit individuellem Betrag und `paid`-Status. Bei bestehenden Daten darf das Format nicht ohne Migration geändert werden.

**Wichtig:** App-Daten sind an Browserprofil und Webadresse gebunden. Löschen von Website-Daten, Wechsel der Domain oder ein Gerätewechsel kann den Zugriff auf die lokal gespeicherten Daten beenden. Deshalb regelmäßig unter **Auswertung → Datensicherung herunterladen (JSON)** sichern. Die Funktion **Datensicherung wiederherstellen** ersetzt nach Bestätigung den aktuellen lokalen Datenbestand durch die ausgewählte JSON-Datei.

**Datenschutz:** GitHub Pages veröffentlicht den App-Quellcode. Persönliche Teilnehmer-, Termin- und Zahlungsdaten gehören **nicht** in das öffentliche Repository. Die JSON-Datensicherung enthält solche Daten und sollte privat aufbewahrt werden.

## 10. Veröffentlichung und Updates (ohne PC)

1. In der App eine aktuelle **JSON-Datensicherung** erstellen.
2. Neue App-Version als ZIP herunterladen und auf Android entpacken.
3. Die fünf App-Dateien **einzeln im Stammverzeichnis** des GitHub-Repositories hochladen; nicht die ZIP-Datei selbst.
4. GitHub Pages ist auf Branch `main` und Verzeichnis `/ (root)` eingerichtet.
5. Veröffentlichung abwarten und installierte PWA erneut öffnen. Bei veralteter Anzeige gegebenenfalls die HTTPS-Webadresse in Chrome prüfen.
6. **Nicht** vorschnell Browser- oder Website-Daten löschen; sonst können lokale Abrechnungsdaten verloren gehen.

Die bestehende Installation muss für normale Updates nicht gelöscht werden. Für Offline-Updates sollte der Cache-Name in `sw.js` bei neuen Versionen erhöht werden.

## 11. Technische Datenstruktur (vereinfachtes Schema)

```json
{
  "people": [{"id": 1, "name": "Beispielperson", "archived": false}],
  "sessions": [{
    "id": 123,
    "date": "2026-11-03",
    "time": "15:00",
    "venue": "hall",
    "hall": 2000,
    "light": 200,
    "entries": [{"person": 1, "amount": 1700, "paid": false}]
  }],
  "materials": [{"id": 456, "name": "Tennisbälle", "date": "2026-11-03", "price": 2490}]
}
```

Dies ist **nur ein Beispielschema**, keine Sicherungsdatei und kein vollständiger Ersatz für den aktuellen Programmcode.

## 12. Regeln für zukünftige Weiterentwicklung

- **Vor jeder Änderung den aktuellen Quellcode prüfen**; nicht auf Basis einer veralteten Version neu aufbauen.
- Bestehende Termine, Personen, individuellen Beträge, Zahlungen, Materialposten und JSON-Sicherungen müssen kompatibel bleiben.
- Neue Funktionen dürfen die Erfassung und das Zurücknehmen von Zahlungen nicht unbeabsichtigt entfernen.
- Für Android auf schmale Displays und große Touch-Ziele achten. Native Android-Datums-/Uhrzeitdialoge können Darstellungsprobleme verursachen; Uhrzeit wird deshalb mit getrennten Auswahlfeldern erfasst.
- Alphabetische Personensortierung, absteigende Terminreihenfolge, Jahres-/Monatsgruppen, aktive Menümarkierung und die gewünschte Startseiten-Reihenfolge erhalten.
- Vor Veröffentlichung die wesentlichen Abläufe testen: Termin erstellen/bearbeiten/löschen, Einzel- und Sammelzahlung, Zahlungsrücknahme, Personenarchivierung, Material, Auswertung, Backup/Restore und Offline-Verhalten.
- Jede neue Version als vollständige ZIP mit den fünf App-Dateien ausliefern.

## 13. Vorlage für einen neuen Chat

> Ich möchte meine private Android-Tennis-Abrechnungs-App weiterentwickeln. Die beigefügte Markdown-Datei beschreibt Anforderungen und Funktionen. Die aktuelle Version ist eine PWA auf GitHub Pages. Ich lade außerdem die aktuelle ZIP-Datei mit dem Quellcode hoch. Bitte erhalte sämtliche vorhandenen Funktionen und die Kompatibilität zu den gespeicherten Daten. Meine gewünschte Änderung ist: **[Änderung eintragen]**. Gib mir anschließend eine vollständige neue ZIP-Version zum Hochladen auf GitHub.

---

**Wichtige Einschränkung:** Die Projektbeschreibung ist eine Dokumentation des Stands 3.2, keine automatische Synchronisierung mit künftigen Änderungen. Nach größeren Updates sollte sie entsprechend aktualisiert werden.
