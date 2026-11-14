# Mein gesundes Leben – Android-PWA

Alle Dateien **gemeinsam im Hauptverzeichnis** des GitHub-Repositories hochladen:
- index.html
- manifest.webmanifest
- sw.js
- icon-192.png
- icon-512.png

## GitHub Pages
Settings → Pages → Deploy from a branch → main → /(root) → Save.

Nach der Veröffentlichung den HTTPS-Link in **Chrome auf Android** öffnen.
Chrome-Menü (⋮) → **App installieren** (manchmal „Zum Startbildschirm hinzufügen“).
Wenn „App installieren“ nicht angeboten wird: Seite neu laden, kurz warten und prüfen, ob alle fünf Dateien am selben Ort liegen.

## Daten
Die App speichert persönliche Daten im Browser des jeweiligen Ursprungs. Die über GitHub Pages geöffnete App hat einen anderen Speicherbereich als die bisherige lokale HTML-Datei.
Vor dem Umstieg JSON-Sicherung in der alten App exportieren und in der neuen App importieren.
Keine persönlichen JSON-Daten in GitHub hochladen.
Eine lokale Kopie im Browser ist kein Ersatz für eine externe Sicherung.

## Updates
Die PWA versucht beim Öffnen online die aktuelle Version zu laden. Offline wird die zwischengespeicherte App verwendet.


Version 5.9: Fotos liegen in IndexedDB und werden nicht von der normalen JSON-Sicherung erfasst. Für vollständige Backups unter Einstellungen die ZIP-Sicherung verwenden.
