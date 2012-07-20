Spam-Schutz #1: verstecktes Feld im Kontaktformular
==========

Wenn man ein Kontaktformular auf der eigenen Website hat, wird darüber gegebenenfalls Spam versendet.
Mit einem simplen Trick kann man das fast gänzlich verhindern.

Das Prinzip von Spam über Kontaktformulare
-------------

Bots, bzw. Scripte, die Websites nach Formularen durchforsten fügen meistens in jedes Feld Inhalt ein.
Wenn man ein Feld hat, das nicht auszufüllen ist, kann man diese Scripte daran hindern, Spam zu versenden.

Formularbeispiel
-------------

Ein Kontaktformular könnte wie folgt aussehen:

```html
<form method="post" action="kontakt.php">
    <fieldset>
        <legend><label for="name">Name:</label></legend>
        <input type="text" name="name" id="name" />
    </fieldset>
    <fieldset>
        <legend><label for="email">E-Mail:</label></legend>
        <input type="text" name="email" id="email" />
    </fieldset>
    <fieldset>
        <legend><label for="nachricht">Nachricht:</label></legend>
        <textarea rows="20" cols="14" name="nachricht" id="nachricht"></textarea>
    </fieldset>
    <fieldset class="dau">
        <legend><label for="dau_text">Bitte f&uuml;llen Sie das folgende Feld nicht aus:</label></legend>
        <input type="text" name="dau" id="dau_text" value="" />
    </fieldset>
    <input type="submit" value="Absenden" />
</form>
```

Der wichtige Teil des Formulars ist das fieldset mit der Klasse „dau“. Dieses wird mit CSS versteckt, damit es ein
„normaler“ Besucher nicht sieht. Für alle, die CSS nicht aktiviert haben (man denke an Screen-Reader) gibt es den
Infotext.

Das CSS muss dementsprechend folgendes enthalten:

```css
.dau { display: none; }
```

Schlusswort
-------------

Im PHP-Script zum Verarbeiten des Kontaktformulars prüft man zunächst, ob `$_POST['dau']` leer ist. Wenn dem nicht so ist,
handelt es sich mit hoher Wahrscheinlichkeit um einen Bot und keine reale Person. Als Folge kann man eine Fehlermeldung
ausgeben oder das Script beenden.

Ich bin schon bei mehreren Sites mit dieser Methode auf 0% Spam gekommen. Manchmal lohnt es natürlich, sich nicht nur
auf eine Anti-Spam-Methode zu verlassen.