# Netflix Clone Skin für Jellyfin

Ein detailgetreuer Netflix-Skin für Jellyfin, der das Aussehen und Verhalten von Netflix nachbildet.

![Netflix Clone Preview](images/preview.png)

## Features

✨ **Authentisches Netflix-Design**
- Originalgetreue Farbpalette (Netflix-Rot #E50914, Schwarz, Grautöne)
- Netflix-typische Schriftarten und Abstände
- Charakteristische Netflix-UI-Elemente

🎬 **Hero/Billboard-Banner**
- Großer Featured-Content-Bereich mit Hintergrundbild
- Verlaufs-Overlay für bessere Lesbarkeit
- Play- und Info-Buttons im Netflix-Stil

📺 **Horizontale Content-Reihen**
- Smooth-Scrolling Medien-Kacheln
- Hover-Zoom-Effekte mit Delay (Netflix-typisch)
- Automatische Thumbnail-Anpassung

🎯 **Interaktive Kacheln**
- Hover-Effekt mit Vergrößerung (Scale 1.08)
- Play-Button-Overlay beim Hover
- Responsive Größenanpassung

🔍 **Detail-Ansicht**
- Modal-Dialog im Netflix-Design
- Umfassende Metadaten-Anzeige
- Episoden-Liste mit Thumbnails
- "More Like This" Sektion

🎮 **Video Player**
- Minimalistisches Player-Interface
- Netflix-ähnliche Steuerungselemente
- Fortschrittsbalken in Netflix-Rot

📱 **Vollständig Responsive**
- Desktop, Tablet und Mobile optimiert
- Adaptive Schriftgrößen und Abstände
- Touch-optimierte Bedienelemente

## Installation

### Methode 1: GitHub Raw-URL (Empfohlen)

1. Öffne Jellyfin Dashboard → Allgemein → Benutzerdefiniertes CSS
2. Füge folgende Zeile ein:

```css
@import url('https://raw.githubusercontent.com/B3Crazy/Jellyfin-Skins/main/Netflix-Clone/custom.css');
```

3. Speichern und Seite neu laden (Strg+F5)

### Methode 2: CSS direkt einbinden

1. Kopiere den gesamten Inhalt der `custom.css` Datei
2. Öffne Jellyfin Dashboard → Allgemein → Benutzerdefiniertes CSS
3. Füge den kopierten Code direkt in das Feld ein
4. Speichern

### Methode 3: Lokale Installation

1. Navigiere zum Jellyfin-Konfigurationsverzeichnis:
   - Windows: `%AppData%\Jellyfin\` oder `C:\ProgramData\Jellyfin\Server\`
   - Linux: `/var/lib/jellyfin/` oder `~/.config/jellyfin/`
   - Docker: Dein konfiguierter Config-Mount

2. Erstelle (falls nicht vorhanden) einen Ordner namens `web-custom`

3. Kopiere `custom.css` in den `web-custom` Ordner

4. Starte Jellyfin neu

5. Öffne Jellyfin Dashboard → Allgemein → Benutzerdefiniertes CSS
6. Aktiviere die Option "Benutzerdefiniertes CSS verwenden"

## Anpassungen

**Hinweis:** Wenn du die GitHub-Import-Methode nutzt, erstelle eine eigene CSS-Datei für deine Anpassungen und importiere zuerst den Netflix-Skin, dann deine Overrides.

### Farben ändern

Die Hauptfarben können in den CSS-Variablen am Anfang der Datei angepasst werden:

```css
:root {
    --netflix-red: #E50914;        /* Netflix Rot */
    --netflix-black: #141414;      /* Haupt-Hintergrund */
    --netflix-dark-gray: #181818;  /* Sekundärer Hintergrund */
    --netflix-medium-gray: #2F2F2F; /* UI-Elemente */
    --netflix-light-gray: #B3B3B3; /* Sekundärtext */
}
```

### Abstände anpassen

```css
:root {
    --content-padding: 60px;  /* Seitenabstand */
    --row-gap: 3vw;          /* Abstand zwischen Reihen */
}
```

### Hover-Effekt Intensität

```css
:root {
    --hover-scale: 1.5;      /* Vergrößerungsfaktor beim Hover */
    --transition-speed: 0.3s; /* Animationsgeschwindigkeit */
}
```

## Kompatibilität

- ✅ Jellyfin 10.8.x
- ✅ Jellyfin 10.9.x
- ✅ Browser: Chrome, Firefox, Safari, Edge
- ✅ Jellyfin Web App
- ⚠️ Mobile Apps: Begrenzte Unterstützung (nur Web-Interface)

## Screenshots

### Home-Ansicht
Der Hero-Banner und horizontale Content-Reihen im Netflix-Stil.

### Detail-Ansicht
Modal-Dialog mit Metadaten, Episoden-Liste und ähnlichen Inhalten.

### Mobile Ansicht
Responsive Design für Smartphones und Tablets.

## Bekannte Einschränkungen

1. **Native Mobile Apps**: Dieser Skin funktioniert nur im Web-Interface, nicht in nativen iOS/Android-Apps
2. **Schriftart**: Netflix Sans ist proprietär - der Skin nutzt Fallback-Fonts (Helvetica Neue, Arial)
3. **Animationen**: Einige komplexe Netflix-Animationen sind mit CSS-only nicht möglich
4. **Auto-Play Trailer**: Jellyfin unterstützt keine Auto-Play-Trailer wie Netflix

## Fehlerbehebung

### Skin wird nicht angewendet

1. Überprüfe, ob "Benutzerdefiniertes CSS verwenden" aktiviert ist
2. Leere den Browser-Cache (Strg + F5)
3. Überprüfe die Browser-Konsole auf CSS-Fehler (F12)

### Elemente überlappen sich

Dies kann bei benutzerdefinierten Jellyfin-Plugins auftreten. Versuche:
- Deaktiviere andere Themes/CSS-Anpassungen
- Aktualisiere Jellyfin auf die neueste Version

### Performance-Probleme

Bei älteren Geräten:
- Reduziere `--hover-scale` auf 1.2
- Erhöhe `--transition-speed` auf 0.5s
- Deaktiviere `backdrop-filter` in `.backdropContainer`

## Mitwirken

Verbesserungsvorschläge und Pull Requests sind willkommen!

1. Fork das Repository
2. Erstelle einen Feature-Branch (`git checkout -b feature/AmazingFeature`)
3. Committe deine Änderungen (`git commit -m 'Add some AmazingFeature'`)
4. Push zum Branch (`git push origin feature/AmazingFeature`)
5. Öffne einen Pull Request

## Credits

- Design inspiriert von [Netflix](https://www.netflix.com)
- Erstellt für [Jellyfin](https://jellyfin.org)
- Community-Feedback und Verbesserungen

## Lizenz

Dieses Projekt steht unter der MIT-Lizenz - siehe [LICENSE](../LICENSE) Datei für Details.

**Hinweis**: Dieses Projekt ist nicht mit Netflix verbunden oder von Netflix unterstützt. Es ist ein Community-erstellter Skin für Jellyfin.

## Changelog

### Version 1.0.1 (November 2025)
- 🔧 Alle Styles in einer einzigen CSS-Datei konsolidiert
- 🔗 Optimiert für GitHub Raw-URL Import
- 📚 Erweiterte Jellyfin-spezifische Selektoren integriert

### Version 1.0.0 (November 2025)
- 🎉 Initiale Veröffentlichung
- ✨ Vollständiges Netflix-Design
- 📱 Responsive Design
- 🎬 Hero-Banner mit Gradient-Overlay
- 🔍 Detail-Modal
- 🎮 Video-Player-Anpassungen
- 📺 Horizontale Scroll-Reihen mit Hover-Effekten

---

**Viel Spaß mit deinem Netflix-Style Jellyfin! 🎬🍿**
