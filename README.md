# DigiDot_2


🔄 DigiDot QR-Code Replacer

![alt text](https://img.shields.io/badge/Lizenz-MIT-blue.svg)


![alt text](https://img.shields.io/badge/Technologie-Vanilla%20JS-yellow.svg)

Ein leistungsstarkes, rein clientseitiges Web-Tool zum Einfügen und präzisen Positionieren von QR-Codes auf Bildern. Diese Anwendung wurde mit dem Fokus auf Einfachheit, Leistung und Datenschutz entwickelt. Da die gesamte Verarbeitung lokal im Browser des Benutzers stattfindet, werden zu keinem Zeitpunkt Bilder oder Daten an einen externen Server gesendet.
____
code:
https://github.com/Digid0t/DigiDot_2/blob/main/index.html

web:
https://raw.githack.com/Digid0t/DigiDot_2/main/index.html

bildlink:
https://github.com/Digid0t/DigiDot_2/blob/main/QR-Code%20Replacer.png

_____

(Empfehlung: Ersetze diesen Link durch einen echten Screenshot oder ein GIF deiner Anwendung, um die Funktionalität zu demonstrieren.)
✨ Features im Überblick

    100% Client-Side: Maximale Privatsphäre und Geschwindigkeit, da keine Server-Kommunikation stattfindet.

    Intuitiver Bild-Upload: Unterstützt sowohl die Dateiauswahl als auch Drag & Drop.

    Dynamische QR-Code-Generierung: Erstellt QR-Codes in Echtzeit aus jeder beliebigen URL.

    Interaktive Live-Vorschau: Alle Änderungen werden sofort auf einer hochauflösenden Canvas-Vorschau visualisiert.

    Multimodale Positionierung:

        Drag & Drop: Greife und verschiebe den QR-Code direkt mit der Maus.

        Präzisions-Slider: Justiere die X/Y-Position und die Größe auf den Pixel genau.

        Click-to-Position: Zentriere den QR-Code durch einen Klick an einer beliebigen Stelle im Bild.

    Interaktive Größenanpassung: Verändere die Größe des QR-Codes über einen Slider oder durch Ziehen eines Resize-Handles.

    Visuelles Feedback: Klare visuelle Hinweise für interaktive Elemente, Hover-Zustände und deaktivierte Aktionen.

    Finaler Export: Lade das fertige Bild als verlustfreie PNG-Datei herunter.

    Responsive Design: Die Benutzeroberfläche passt sich nahtlos an verschiedene Bildschirmgrößen an.

🚀 Anwendung

Die Nutzung der Anwendung ist unkompliziert und erfordert keine technischen Kenntnisse.

    🖼️ Bild hochladen: Klicke auf 📤 Bild auswählen oder ziehe deine Bilddatei per Drag & Drop in den markierten Bereich.

    🔗 Link eingeben: Sobald das Bild geladen ist, wird das URL-Eingabefeld aktiv. Gib hier den Link ein, für den der QR-Code erstellt werden soll (z.B. https://github.com).

    🎉 Generieren: Klicke auf QR-Code generieren. Der QR-Code erscheint sofort auf dem Vorschau-Bild.

    🛠️ Anpassen: Positioniere und skaliere den QR-Code nach deinen Wünschen:

        Ziehen: Klicke auf den QR-Code und halte die Maustaste gedrückt, um ihn zu verschieben.

        Größe ändern: Ziehe den kleinen blauen quadratischen Anfasser in der unteren rechten Ecke des QR-Codes.

        Feinjustierung: Benutze die Schieberegler im Bedienfeld für pixelgenaue Kontrolle.

    ✅ Finalisieren: Wenn alles perfekt positioniert ist, klicke auf ✅ Position bestätigen & Bild erstellen. Dieser Schritt rendert das endgültige Bild im Hintergrund.

    💾 Herunterladen: Klicke auf den nun sichtbaren Button 💾 Fertiges Bild herunterladen, um das Ergebnis auf deinem Computer zu speichern.

🛠️ Technische Umsetzung im Detail

Dieses Projekt ist bewusst als eine in sich geschlossene index.html-Datei konzipiert, um maximale Portabilität und Einfachheit zu gewährleisten. Es hat keine Build-Schritte und kann direkt in jedem modernen Browser geöffnet werden.
Projektstruktur

Die gesamte Anwendung ist in einer einzigen Datei enthalten:

    HTML: Definiert die semantische Struktur und die DOM-Elemente.

    CSS: Verantwortlich für das gesamte Styling, das responsive Layout und die visuellen Zustände der UI-Elemente.

    JavaScript: Beinhaltet die gesamte Anwendungslogik, von der Event-Verwaltung bis zur Canvas-Manipulation.

Kerntechnologien

    HTML5: Insbesondere das <canvas>-Element für das Rendering der Bilder.

    CSS3: Flexbox und CSS Grid für das Layout, position: absolute für das Overlay und :hover, :disabled für die Interaktivität.

    Vanilla JavaScript (ES6+): Keine Frameworks, keine Abhängigkeiten (außer QRCode.js), nur reines JavaScript für maximale Performance.

    QRCode.js: Eine bewährte externe Bibliothek, die über ein CDN geladen wird, um die QR-Codes zu generieren.

Analyse der Funktionsweise
1. HTML-Struktur

Die HTML-Struktur ist klar gegliedert, um eine Trennung von Anliegen (Separation of Concerns) zu erreichen, selbst innerhalb einer einzigen Datei.

    Steuerungs-Panel (.controls-panel): Enthält alle UI-Elemente, mit denen der Benutzer interagiert (Buttons, Slider, Inputs). Es ist "sticky", um bei langen Bildern sichtbar zu bleiben.

    Canvas-Container (.canvas-container): Dieser Container ist entscheidend für die Interaktivität.

        <canvas id="previewCanvas">: Hier wird die Live-Vorschau gerendert. Alle Zeichenoperationen (Originalbild, QR-Code) finden auf diesem Canvas statt.

        <div id="qrOverlay">: Ein entscheidendes Element! Dies ist ein unsichtbares div, das per JavaScript exakt über den auf dem Canvas gezeichneten QR-Code gelegt wird. Der Grund: DOM-Elemente können Maus-Events (wie mousedown, drag) viel einfacher und performanter handhaben als Canvas-Pixel. Das div agiert als "Hitbox" für den QR-Code.

    Versteckte Helfer-Elemente:

        <div id="qrcode">: Dieses div ist display: none. Die qrcode.js-Bibliothek benötigt ein DOM-Element, in das sie ihr generiertes QR-Code-Canvas zeichnen kann. Wir nutzen dieses versteckte div als temporären Speicherort.

        <canvas id="finalCanvas">: Ebenfalls display: none. Auf dieses Canvas wird das endgültige, hochauflösende Bild gezeichnet, wenn der Benutzer auf "Position bestätigen" klickt. Dies trennt die Live-Vorschau vom finalen Rendering.

2. CSS-Styling

Das CSS ist nicht nur für die Optik zuständig, sondern unterstützt auch die Funktionalität:

    Layout mit CSS Grid: .main-layout verwendet display: grid, um eine robuste zweispaltige Struktur zu schaffen, die sich bei kleineren Viewports (@media-Query) automatisch in ein einspaltiges Layout umwandelt.

    Die Overlay-Technik: #qrOverlay ist position: absolute innerhalb des position: relative Containers #canvasContainer. Seine left, top, width und height Eigenschaften werden dynamisch per JavaScript gesetzt, um es perfekt mit dem QR-Code auf dem Canvas zu synchronisieren.

    Visuelles Feedback: Hover-Effekte auf Buttons und der gestrichelte Rand des Overlays geben dem Benutzer klares Feedback. Der :disabled-Selektor wird intensiv genutzt, um Buttons, die in einem bestimmten Zustand nicht verwendet werden können (z.B. "Generieren" ohne Bild), visuell zu deaktivieren und per cursor: not-allowed als nicht klickbar zu kennzeichnen.

3. JavaScript-Logik: Der Kern der Anwendung

Die Logik lässt sich in mehrere Arbeitsabläufe unterteilen:

A. Initialisierung & State Management

    Globale Variablen (originalImage, qrCodeImage, isDragging, isResizing, qrX, qrY, qrSize) halten den aktuellen Zustand der Anwendung.

    Alle benötigten DOM-Elemente werden zu Beginn einmal selektiert und in Konstanten gespeichert, um wiederholte DOM-Abfragen zu vermeiden.

    Alle Event-Listener werden initialisiert und an die entsprechenden Elemente gebunden.

B. Workflow: Bild-Upload

    Der change-Event auf <input type="file"> oder der drop-Event auf dem .upload-section lösen die Funktion handleImageUpload aus.

    Ein FileReader-Objekt wird instanziiert. Die readAsDataURL()-Methode liest die Bilddatei ein.

    Im onload-Callback des Readers wird ein neues Image-Objekt erstellt und seine src auf das Ergebnis des Readers (eine Base64-Data-URL) gesetzt.

    Im onload-Callback des Image-Objekts (das feuert, wenn das Bild dekodiert ist), wird das Bild in originalImage gespeichert.

    Die Abmessungen beider Canvases (previewCanvas, finalCanvas) und die max-Werte der Slider werden an die Dimensionen des hochgeladenen Bildes angepasst.

    Die showPreview()-Funktion wird aufgerufen, um das Bild erstmals anzuzeigen.

Generated javascript

      
// Ausschnitt aus der Bild-Upload-Logik
function handleImageUpload(file) {
    const reader = new FileReader();
    reader.onload = (e) => {
        const img = new Image();
        img.onload = () => {
            originalImage = img;
            // ... Canvases und Slider anpassen ...
            previewCanvas.width = img.width;
            previewCanvas.height = img.height;
            // ...
            showPreview();
        };
        img.src = e.target.result;
    };
    reader.readAsDataURL(file);
}

    

IGNORE_WHEN_COPYING_START
Use code with caution. JavaScript
IGNORE_WHEN_COPYING_END

C. Workflow: QR-Code-Generierung

    Der click-Event auf #generateBtn startet die generateQRCode-Funktion.

    Die qrcode.js-Bibliothek wird aufgerufen und angewiesen, den QR-Code in das versteckte <div id="qrcode"> zu rendern. Die Bibliothek erzeugt darin ein eigenes <canvas>-Element.

    Der entscheidende Trick: Wir warten mit setTimeout einen kurzen Moment, um sicherzustellen, dass das Canvas gezeichnet wurde. Dann selektieren wir dieses temporäre Canvas und konvertieren seinen Inhalt mit qrCanvas.toDataURL() in ein Image-Objekt (qrCodeImage). Dieser Schritt ist notwendig, um den QR-Code einfach auf unser Haupt-Canvas zeichnen zu können.

    Sobald qrCodeImage geladen ist, werden die Anpassungs-Steuerelemente sichtbar gemacht und showPreview() wird erneut aufgerufen.

Generated javascript

      
// Ausschnitt aus der QR-Code-Generierung
function generateQRCode(url) {
    document.getElementById('qrcode').innerHTML = ''; // Vorherigen QR-Code löschen
    new QRCode(document.getElementById('qrcode'), { /* ... options ... */ });

    setTimeout(() => {
        const qrCanvas = document.querySelector('#qrcode canvas');
        if (qrCanvas) {
            qrCodeImage = new Image();
            qrCodeImage.onload = function() {
                // UI aktivieren und Vorschau aktualisieren
                adjustmentControls.style.display = 'block';
                showPreview();
            };
            qrCodeImage.src = qrCanvas.toDataURL();
        }
    }, 100);
}

    

IGNORE_WHEN_COPYING_START
Use code with caution. JavaScript
IGNORE_WHEN_COPYING_END

D. Workflow: Interaktive Manipulation & Rendering

    Rendering (showPreview): Diese Funktion ist das Herzstück der UI. Sie wird bei jeder Änderung aufgerufen. Sie führt eine klare Reihenfolge von Zeichenoperationen auf dem previewCtx (dem 2D-Kontext des Vorschau-Canvas) aus:

        clearRect(): Löscht das gesamte Canvas.

        drawImage(originalImage, ...): Zeichnet das Hintergrundbild.

        Wenn qrCodeImage existiert:

            fillRect(): Zeichnet ein leicht gefärbtes Rechteck als "Matte" hinter dem QR-Code.

            drawImage(qrCodeImage, ...): Zeichnet den QR-Code an der aktuellen qrX, qrY Position mit der Größe qrSize.

        updateOverlay(): Aktualisiert die Position und Größe des qrOverlay-Divs, um mit dem gezeichneten QR-Code übereinzustimmen.

    Interaktion (Drag, Resize, Click): Die mousedown, mousemove, und mouseup Events arbeiten zusammen:

        mousedown auf dem #qrOverlay setzt isDragging = true (oder isResizing = true, wenn der Anfasser geklickt wurde) und speichert einen Offset, um Sprünge zu vermeiden.

        Der mousemove-Event auf dem document prüft, ob einer dieser Zustände true ist. Wenn ja, berechnet er die neue Position oder Größe basierend auf der Mausposition (e.clientX, e.clientY) und der Skalierung des Canvas.

        Nach jeder Berechnung werden die globalen State-Variablen (qrX, qrY, qrSize) aktualisiert und showPreview() aufgerufen, was die flüssige Live-Vorschau erzeugt.

        mouseup setzt die is...-Flags zurück auf false und beendet die Interaktion.

E. Workflow: Finalisierung & Download

    Der Klick auf #finalizeBtn zeichnet die exakt gleiche Szene wie showPreview auf das versteckte, aber hochauflösende finalCanvas.

    Der Klick auf #downloadBtn erzeugt dynamisch ein <a>-Element.

    finalCanvas.toDataURL('image/png') serialisiert den Inhalt des Canvas in eine Base64-codierte PNG-Grafik.

    Diese Data-URL wird als href des Links gesetzt und das download-Attribut wird mit einem dynamischen Dateinamen versehen.

    link.click() wird programmatisch aufgerufen, um den Download-Dialog des Browsers auszulösen.

Mögliche zukünftige Verbesserungen

    Farbwähler: Dem Benutzer erlauben, die Farbe des QR-Codes und des Hintergrunds anzupassen.

    State-Saving: Den aktuellen Zustand (Bild, URL, Position) im localStorage speichern, damit der Benutzer seine Arbeit später fortsetzen kann.

    Weitere Export-Formate: Unterstützung für JPEG mit Qualitätseinstellung.

    Rotation: Einen weiteren Slider hinzufügen, um den QR-Code zu drehen.

    Integration von Logos: Dem QR-Code ein kleines Logo in der Mitte hinzufügen.


_____

![QR-Code Replacer](https://raw.githubusercontent.com/Digid0t/DigiDot_2/main/QR-Code%20Replacer.png)


_____

<img src="https://raw.githubusercontent.com/Digid0t/DigiDot_2/main/DigiDot_2_QR.png" alt="DigiDot 2 QR Code" width="300">

____
