Web-Performance #2: CSS und JavaScript optimieren
==========

Zur Optimierung der Performance einer Website helfen bereits kleinste Änderungen bezüglich CSS und JavaScript.
In diesem Artikel zeige ich euch einfache Möglichkeiten zur Verbesserung auf.

Auslagern von Styles und Scripts
-------------

Browser cachen, soweit in den Einstellungen des Browsers nicht anders angegeben, eine Seite. Das wiederrum bedeutet,
dass bereits geladene Inhalte nicht immer wieder erneut angefragt werden müssen.

Hat man innerhalb einer Website nun CSS und JavaScript Blöcke, die man auf jeder einzelnen Seite verwendet,
muss der entsprechende Code auch immer wieder mit geladen werden. Daher sollte man CSS und JavaScript auslagern.

Position von CSS und JavaScript Tags
-------------

Es ist erwiesen, dass man JavaScript-Dateien erst am Ende vom BODY in einer Seite angeben sollte.
Allein die Umstrukturierung vom Kopfbereich hin zu dem Ende vom BODY-Tag bringt bereits mehrere Sekunden.

CSS-Dateien hingegen gehören in den HEAD-Bereich einer Website.

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
	<head>
		<title>Mein Titel</title>
		<link rel="stylesheet" type="text/css" href="pfad/css/screen.css" media="screen" />
	</head>
	<body>
		<h1>Meine &Uuml;berschrift</h1>
		<p>Mein Inhalt</p>
		<script type="text/javascript" src="pfad/js/meinscript.js"> </script>
	</body>
</html>
```

mehrere Dateien mit nur einem HTTP-Request
-------------

Beim Laden von mehreren Dateien werden auch mehrere HTTP-Requests benötigt. Dies kann der Performance
einer Website ungünstig gegenüberstehen. Legt man diese Dateien in einer einzigen zusammen, kann man dadurch bereits
Sekunden gewinnen.

Unter dem nächsten Punkt findest du unter anderem einen Lösungsansatz mit PHP für dieses Problem.

Komprimieren von Dateien
-------------

Zum Komprimieren von JavaScript und CSS eignet sich die PHP-Klasse Minify, die auf Google-Code zu finden ist.

Minify entfernt nicht nur Kommentare und Leerzeichen, sondern kann die Dateien auch GZIP komprimiert ausgeben.
Entstandene komprimierte Dateien werden zudem gecacht.

Konfiguration
-------------

Bei Minify kann man einige Einstellungen in der config.php vornehmen. So kann man zum Beispiel einen Debug-Mode
aktivieren, bei dem mehrere Dateien zwar zusammengeführt, aber nicht komprimiert werden.

Ein Fehlerprotokoll für FirePHP (Firefox AddOn für die Firebug Konsole) kann mittels $min_errorLogger aktiviert werden.
Als Beispiel nun eine Konfigurationsdatei. Diese könnte entsprechend in einer XAMPP-Umgebung liegen.
Weitere Informationen zur Konfiguration befinden sich in der mit heruntergeladenen Konfigurationsdatei.

```php
<?php
$min_allowDebugFlag = false; // Debug-Mode
$min_errorLogger = false; // Fehlerprotokoll für FirePHP
$min_enableBuilder = false; // Manuell Dateien komprimieren
$min_cachePath = 'C:\\xampp\\htdocs\\cache'; // Pfad, in dem die Cache-Dateien abgelegt werden
$min_documentRoot = 'C:\\xampp\\htdocs'; // Hauptpfad, in dem auch der min Ordner liegt
$min_cacheFileLocking = true; // auf false stellen, wenn das Dateisystem NFS ist
$min_serveOptions['bubbleCssImports'] = false; // @import in CSS Dateien: Fehlermeldung werfen oder alle @import Befehle an den Anfang stellen
$min_serveOptions['maxAge'] = 1800; // maximales Alter des Browser-Caches in Sekunden
$min_serveOptions['minApp']['groupsOnly'] = false; // Minify akzeptiert bei true nur noch Gruppen in den Parametern
$min_serveOptions['minApp']['maxFiles'] = 10; // maximale Anzahl an Dateien, die bei Angabe von einzelnen Dateien komprimiert werden können
$min_symlinks = array(); // Bei Pfad-Problemen können hier mehrere mögliche Pfade angegeben werden
$min_uploaderHoursBehind = 0; // Fehlerbehebung von hochgeladenen Dateien von einem Windows zu einem Nicht-Windows-System
$min_libPath = dirname(__FILE__) . '/lib'; // Pfad zum Minify lib Ordner
ini_set('zlib.output_compression', '0'); // Versuche Ausgabe-Kompression zu deaktivieren
```

einzelne Dateien komprimieren
-------------

Zum Komprimieren von einer JavaScript- oder CSS-Datei muss man lediglich das HTML anpassen:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Mein Titel</title>
        <link rel="stylesheet" type="text/css" href="pfad/min/?f=pfad/screen.css" media="screen" />
    </head>
    <body>
        <h1>Meine &Uuml;berschrift</h1>
        <p>Mein Inhalt</p>
        <script type="text/javascript" src="pfad/min/?f=pfad/jquery.js,pfad/meinscript.js"> </script>
    </body>
</html>
```

In diesem Beispiel werden eine CSS- und zwei JavaScript-Dateien angegeben. Wie man beim JavaScript sehen kann,
werden mehrere Dateien einfach per Komma getrennt.

Gruppieren
-------------

Möchte man auf einer Website eine mit JavaScript unterstützte Bildergalerie nutzen oder hat mehrere CSS-Dateien,
um den Überblick zu wahren, sollte man diese Dateien nach Möglichkeit als eine Datei an den Browser senden.

Mit Minify geht das einfach und schnell. Hierzu muss man lediglich die Dateien mit einem Komma getrennt angeben
(s. oben) oder die groupsConfig.php anpassen.

Beispielsweise könnte die Gruppen-Datei so aussehen:

```php
<?php
return array(
    'mygallery' => array(
        '//js/jquery.js',
        '//js/jquery.gallery.js'
    )
);
```

Gruppen läd man im HTML mit dem g-Parameter. So wird dann aus dem längeren Aufruf der einzelnen JavaScript-Dateien
nur noch:

```html
<script type="text/javascript" src="pfad/min/?g=mygallery"> </script>
```

Fazit
-------------

Die Optimierung von CSS und JavaScript ist damit natürlich noch nicht vollständig. Man denke da an verschiedenste
Möglichkeiten, den Code an sich zu optimieren.

Auf jeden Fall haben mir die oben genannten Methoden schon einige Sekunden eingebracht.