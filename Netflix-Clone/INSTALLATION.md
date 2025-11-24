# Installationsanleitung - Netflix Clone Skin

## Schnellstart

### Option 1: GitHub Raw-URL (Empfohlen - Automatische Updates)

1. **URL importieren**
   - Öffne dein Jellyfin-Dashboard
   - Navigiere zu: **Dashboard** → **Allgemein** → **Benutzerdefiniertes CSS**
   - Füge folgende Zeile ein:
   ```css
   @import url('https://raw.githubusercontent.com/B3Crazy/Jellyfin-Skins/main/Netflix-Clone/custom.css');
   ```
   - Klicke auf **Speichern**

2. **Seite aktualisieren**
   - Drücke Strg+F5 (Hard Reload) um den Browser-Cache zu leeren
   - Der Netflix-Skin sollte nun aktiv sein

**Vorteil:** Updates werden automatisch übernommen, wenn du die Seite neu lädst!

### Option 2: Direkte CSS-Integration

1. **CSS-Inhalt kopieren**
   - Öffne die Datei `custom.css` auf GitHub oder lokal
   - Kopiere den gesamten Inhalt (Strg+A, Strg+C)

2. **In Jellyfin einfügen**
   - Öffne dein Jellyfin-Dashboard
   - Navigiere zu: **Dashboard** → **Allgemein** → **Benutzerdefiniertes CSS**
   - Füge den kopierten CSS-Code in das Textfeld ein
   - Klicke auf **Speichern**

3. **Seite aktualisieren**
   - Drücke Strg+F5 (Hard Reload) um den Browser-Cache zu leeren

### Option 3: Lokale Installation (Erweitert)

#### Für Windows:

1. **Jellyfin-Ordner finden**
   ```
   %AppData%\Jellyfin\
   ```
   oder
   ```
   C:\ProgramData\Jellyfin\Server\
   ```

2. **Web-Custom Ordner erstellen**
   - Navigiere zum Jellyfin-Installationsverzeichnis
   - Erstelle einen Ordner namens `web-custom` (falls nicht vorhanden)

3. **CSS-Dateien kopieren**
   - Kopiere `custom.css` in den `web-custom` Ordner
   - Optional: Kopiere auch `css/extended.css` für erweiterte Styles

4. **Jellyfin neustarten**
   - Starte den Jellyfin-Dienst neu
   - Windows: Dienste-App → Jellyfin → Neustart

5. **Im Dashboard aktivieren**
   - Dashboard → Allgemein → "Benutzerdefiniertes CSS verwenden" aktivieren

#### Für Linux:

1. **Jellyfin-Verzeichnis**
   ```bash
   /var/lib/jellyfin/
   ```
   oder
   ```bash
   ~/.config/jellyfin/
   ```

2. **Web-Custom Ordner**
   ```bash
   sudo mkdir -p /var/lib/jellyfin/web-custom
   ```

3. **CSS kopieren**
   ```bash
   sudo cp custom.css /var/lib/jellyfin/web-custom/
   sudo chown jellyfin:jellyfin /var/lib/jellyfin/web-custom/custom.css
   ```

4. **Jellyfin neustarten**
   ```bash
   sudo systemctl restart jellyfin
   ```

#### Für Docker:

1. **docker-compose.yml anpassen**
   ```yaml
   services:
     jellyfin:
       image: jellyfin/jellyfin
       volumes:
         - /pfad/zu/Netflix-Clone:/web-custom:ro
   ```

2. **Container neustarten**
   ```bash
   docker-compose down
   docker-compose up -d
   ```

## Erweiterte Konfiguration

### Eigene Anpassungen hinzufügen

Wenn du die GitHub-URL-Methode nutzt und eigene Änderungen vornehmen möchtest:

```css
/* Importiere zuerst den Netflix-Skin */
@import url('https://raw.githubusercontent.com/B3Crazy/Jellyfin-Skins/main/Netflix-Clone/custom.css');

/* Dann deine eigenen Overrides */
:root {
    --netflix-red: #FF0000; /* Deine eigene Farbe */
}
```

### Farben anpassen

Bearbeite die CSS-Variablen am Anfang der `custom.css`:

```css
:root {
    --netflix-red: #E50914;        /* Haupt-Akzentfarbe */
    --netflix-black: #141414;      /* Dunkler Hintergrund */
    --netflix-dark-gray: #181818;  /* UI-Elemente */
}
```

### Performance-Optimierung

Für ältere Geräte, reduziere Animationen:

```css
:root {
    --transition-speed: 0.1s;  /* Schneller */
    --hover-scale: 1.05;       /* Weniger Zoom */
}
```

Oder deaktiviere Animationen komplett:

```css
* {
    transition: none !important;
    animation: none !important;
}
```

## Fehlerbehebung

### Problem: Skin wird nicht angewendet

**Lösung 1: Cache leeren**
- Drücke Strg+Shift+Delete
- Wähle "Cached Images and Files"
- Klicke "Clear Data"
- Lade Jellyfin neu (Strg+F5)

**Lösung 2: CSS-Syntax prüfen**
- Öffne Browser-Entwicklertools (F12)
- Gehe zum "Console" Tab
- Suche nach CSS-Fehlern

**Lösung 3: Browser-Kompatibilität**
- Aktualisiere deinen Browser auf die neueste Version
- Teste mit einem anderen Browser (Chrome, Firefox, Edge)

### Problem: Elemente überlappen

**Lösung:**
- Deaktiviere andere Themes/Skins
- Deinstalliere CSS-modifizierende Plugins
- Teste mit Standard-Jellyfin-Installation

### Problem: Schriftart sieht anders aus

**Info:** Netflix Sans ist proprietär. Der Skin verwendet Fallback-Fonts:
- Helvetica Neue
- Arial
- System-Standard

**Optional:** Lade eine ähnliche Font herunter und füge hinzu:

```css
@font-face {
    font-family: 'CustomNetflixFont';
    src: url('PFAD/ZU/FONT.woff2') format('woff2');
}

:root {
    --netflix-font: 'CustomNetflixFont', sans-serif;
}
```

### Problem: Langsame Performance

**Lösungen:**
1. Reduziere `--hover-scale` auf 1.05
2. Erhöhe `--transition-speed` auf 0.5s
3. Deaktiviere `backdrop-filter`
4. Nutze Hardware-Beschleunigung im Browser

## Aktualisierung

### Automatische Updates (GitHub-Methode)

Wenn du die URL-Import-Methode nutzt, werden Updates automatisch übernommen:

```css
@import url('https://raw.githubusercontent.com/B3Crazy/Jellyfin-Skins/main/Netflix-Clone/custom.css');
```

Leere einfach den Browser-Cache (Strg+F5) um die neueste Version zu laden.

### Manuelle Updates

1. Lade die neue `custom.css` herunter
2. Ersetze die alte Datei
3. Leere Browser-Cache
4. Lade Jellyfin neu

## Deinstallation

1. **Dashboard-Methode:**
   - Dashboard → Benutzerdefiniertes CSS
   - Lösche den CSS-Code
   - Speichern

2. **Datei-Methode:**
   - Lösche `custom.css` aus `web-custom`
   - Starte Jellyfin neu

3. **Browser-Cache leeren:**
   - Strg+Shift+Delete
   - Cache leeren
   - Seite neu laden

## Unterstützung

Bei Problemen oder Fragen:

1. Prüfe die [FAQ](README.md#bekannte-einschränkungen)
2. Öffne ein Issue auf GitHub
3. Stelle sicher, dass du die neueste Jellyfin-Version nutzt

## Tipps & Tricks

### Nur bestimmte Bereiche stylen

Kommentiere ungewollte Abschnitte aus:

```css
/* ==================== HERO / BANNER SECTION ====================
.heroContent {
    ...
}
*/
```

### Kombinieren mit anderen Skins

Importiere mehrere CSS-Dateien:

```css
@import url('other-skin.css');
@import url('netflix-clone/custom.css');
```

Die letzte Regel gewinnt bei Konflikten.

### Mobile-only Anpassungen

```css
@media screen and (max-width: 768px) {
    /* Deine mobilen Anpassungen hier */
}
```

---

**Viel Erfolg bei der Installation! 🎬**
