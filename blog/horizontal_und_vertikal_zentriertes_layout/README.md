Horizontal und vertikal zentriertes Layout
==========

Es wird oft gewünscht ein Layout horizontal zentriert darzustellen. Manchmal soll es auch vertikal in der Mitte liegen.
In diesem Artikel stelle ich für beides eine Lösung vor.

Horizontal zentrieren
-------------

Möchte man ein Layout horizontal zentrieren, reicht ein wenig CSS, um dies zu realisieren. Gehen wir von folgendem
HTML aus:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html>
    <head>
        <title>Horizontal zentriertes Layout</title>
        <link rel="stylesheet" type="text/css" href="style.css"/>
    </head>
    <body>
        <div id="wrapper">
            <p>Der Wrapper ist zentriert.</p>
        </div>
    </body>
</html>
```

Im CSS wird der Inhalt des body zentriert, während im Wrapper dies für die Texte wieder zurückgesetzt wird. Dem Wrapper wird nach links und rechts ein automatisches margin gegeben. Hinzu kommen ein paar Angaben, damit man auch das Resultat vernünfitg erkennen kann.

```css
* { margin: 0; padding: 0; }

body { text-align: center; }

div#wrapper {
    background: #000;
    color: #fff;
    margin: 0 auto;
    text-align: left;
    width: 400px;
}
```

Damit ist der Wrapper zentriert und wir sind fertig.

Vertikal zentrieren
-------------

Die hier aufgeführte Lösung benutzt ein DIV, das die Hälfte des Anzeigebereichs an Höhe hat. Es steht über dem
eigentlichen Inhalt und verschiebt diesen nach unten. Dementsprechend gehen wir jetzt von dem unten stehenden HTML aus.

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html>
    <head>
        <title>Vertikal zentriertes Layout</title>
        <link rel="stylesheet" type="text/css" href="style.css"/>
    </head>
    <body>
        <div id="empty-wrapper"></div>
        <div id="wrapper">
            <p>Der Wrapper ist zentriert.</p>
        </div>
    </body>
</html>
```

Im CSS blenden wir das hinzu gekommene DIV nun aus und geben ihm die Hälfte der Höhe vom Inhaltsbereich mal -1 als
margin-top.

```css
* { margin: 0; padding: 0; }

body { height: 100%; width: 100%; }

div#empty-wrapper {
    display: block;
    float: left;
    height: 50%;
    margin-top: -300px; /* - Haelfte der Hoehe von #wrapper */
    visibility: hidden;
    width: 100%;
}

div#wrapper {
    background: #f00;
    clear: both;
    color: #fff;
    height: 600px;
    width: 500px;
}
```

Jetzt ist das Layout vertikal zentriert. Es funktioniert zwar nur, wenn man die Höhe des Inhaltsbereiches kennt, sollte
aber für die meisten Fälle nutzbar sein.
