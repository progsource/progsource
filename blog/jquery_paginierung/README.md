Paginierung mit JavaScript (jQuery)
==========

Hat man mehrere Elemente von einem Typ, so zum Beispiel mehrere Artikel-Teaser, kann man diese einfach mit jQuery auf
mehrere Seiten teilen.

Mit jQuery Plugins schnell ans Ziel kommen
-------------

Als ich mit jQuery zu arbeiten anfing, gefiel mir, wie schnell man zum Ergebnis kommt.
Plugins können den Entwicklungsprozess noch stärker beschleunigen,

Viele kostenlose Erweiterungen gibt es auf der <a href="http://plugins.jquery.com/" target="_blank">jQuery</a>
Seite selbst zum Download. Davon abgesehen gibt es zum Beispiel noch
<a href="http://jqueryui.com/" target="_blank">jQuery UI</a> oder
<a href="http://flowplayer.org/tools/" target="_blank">jQuery Tools</a>.

Paginierung
-------------

Zutaten:
------------

- <a href="http://docs.jquery.com/Downloading_jQuery" target="_blank">jQuery</a>
- <a href="http://plugins.jquery.com/project/pagination" target="_blank">jQuery Pagination Plugin</a>

Zubereitung:
------------

Man nehme ein HTML Dokument mit folgendem Aufbau:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
   "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Paginierung</title>
        <link rel="stylesheet" type="text/css" href="css/pagination.css"/>
    </head>

    <body>
        <div class="element">
            <p>Dies ist ein Element.</p>
        </div>
        <div class="element">
            <p>Dies ist ein Element.</p>
        </div>
        <div class="element">
            <p>Dies ist ein Element.</p>
        </div>
        <div class="element">
            <p>Dies ist ein Element.</p>
        </div>
        <div class="element">
            <p>Dies ist ein Element.</p>
        </div>
        <div class="element">
            <p>Dies ist ein Element.</p>
        </div>
        <div class="element">
            <p>Dies ist ein Element.</p>
        </div>
        <div class="element">
            <p>Dies ist ein Element.</p>
        </div>
        <div class="element">
            <p>Dies ist ein Element.</p>
        </div>
        <div class="element">
            <p>Dies ist ein Element.</p>
        </div>
        <div class="element">
            <p>Dies ist ein Element.</p>
        </div>
        <div class="element">
            <p>Dies ist ein Element.</p>
        </div>
        <div id="paginierung"></div>
        <script type="text/javascript" src="js/jquery.js"></script>
        <script type="text/javascript" src="js/jquery.pagination.js"></script>
        <script type="text/javascript" src="js/mypagination.js"></script>
    </body>
</html>
```

In der JavaScript Datei muss man nun zunächst eine Funktion schreiben, in der man sagt, was bei Klick auf
eine Zahl in der Paginierung passieren soll:

```javascript
// Anzahl der Elemente pro Seite
var elPerPage = 7;

// Callback Funktion bei Klick auf einen Link der Paginierung
function handlePaginationClick(new_page_index, pagination_container) {
	// Alle vorhandenen Elemente verstecken
	$('.element').hide();
	// new_page_index ist die Seitenzahl -1
	// Nummer des letzten Elements berechnen
	var lastItem = new_page_index + 1;
	lastItem *= elPerPage;
	// Nummer des ersten Elements berechnen
	var firstItem = new_page_index * elPerPage;
	// Alle auf der Seite befindlichen Elemente anzeigen
	for (var i=firstItem; i<lastItem; i++) {
	    $($('.element')[i]).show();
	}
	return false;
}
```

Danach müssen wir noch bestimmen, wie der Container für die Paginierung heißt und stellen die gewünschten
Optionen ein:

```javascript
// sobald der Inhalt der Seite geladen ist
$(document).ready(function() {
	// Wenn mindestens ein Element vorhanden ist
	if ($('.element').size() > 0) {
		// Alle Elemente verstecken
		$('.element').hide();

		// Erster Parameter: Anzahl von Elementen
		// Zweiter Parameter: Optionen
		$("#paginierung").pagination(
			$('.element').size(), {
				// Anzahl der Elemente pro Seite
				items_per_page: elPerPage,
				// Callback Funktion
				callback: handlePaginationClick,
				// Text für den letzten Link
				next_text: 'N&auml;chste',
				// Text für den ersten Link
				prev_text: 'Vorherige'
		});
	}
});
```

Und schon hat man eine Paginierung.