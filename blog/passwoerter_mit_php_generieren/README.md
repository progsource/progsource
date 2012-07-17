Passwörter mit PHP generieren
==========

Mit der PEAR Klasse Text_Password kann man auf einfache Weise Passwörter generieren. Wie das geht, erfährst du in
diesem Artikel.

Wie sehen „sichere“ Passwörter aus?
-------------

Allgemein kann man sagen, dass ein sicheres Passwort aus mindestens 8 Buchstaben und unterschiedlichen Zeichen
bestehen muss. So ist ein Passwort wie „12345“, „abcdef“, „ab12“ oder „test“ nicht als sicheres Passwort anzusehen.

Ein Beispiel für ein sicheres Passwort wäre da eher „l1_Pq9+-3F“ oder auch „m./E8#s0“.

Generieren mit PHP
-------------

Als Hilfe kann man sich die PEAR-Klasse Text_Password vornehmen, mit der man einfach und schnell neue
Passwörter generiert.
Möchte man ein Passwort mit mindestens 8 Zeichen erstellen, das unterschiedliche Zeichen enthält, muss man lediglich
folgenden Code einbauen:

    <?php
    require_once('Text/Password.php');
    $pw = Text_Password::create(8, 'unpronounceable');

Damit generierte Passwörter wären zum Beispiel: „h%4lAB3z“, „Ga#LHZiK“ und „WkPJ_4to“.

Sollte die Sicherheit niedriger eingestuft sein, kann mit Text_Password auch ein „aussprechbares“ Passwort,
das nur Buchstaben enthält, erzeugt werden:

    $pw = Text_Password::create(8, 'pronounceable');

„claechae“, „ueastiac“ oder „haleuedr“ wären mögliche Ergebnisse.

Mehrere Passwörter kann man zur gleichen Zeit generieren, indem der folgende Code benutzt wird:

    $pw_array  = array();
    $pw_array  = Text_Password::createMultiple(3);

    $pw_array2 = array();
    $pw_array2 = Text_Password::createMultiple(3, 10, 'unpronounceable');

Dabei erhält man ein Array mit entsprechender Menge an Passwörtern. In dem ersten Beispiel könnten zum Beispiel
folgende Passwörter heraus kommen: „drebaibiph“, „crifriacra“ und „dabiniamou“.

Das zweite Beispiel erzeugt dann wiederum „nicht aussprechbare“ Passwörter wie: „C%9bRflGcb“,
„MpVP@YXaFM“ oder „o%7N1R1q1Y“.

Weitere Möglichkeiten, wie man Text_Password verwenden kann, finden sich in der
<a href="http://pear.php.net/manual/de/package.text.text-password.types.php" target="_blank">PEAR Dokumentation</a>.

Speichern von Passwörtern in einer Datenbank
-------------

Speichert man ein Passwort in einer Datenbank ab, sollte dies nie unverschlüsselt abgelegt werden.
Es muss mindestens ein Hash mit MD5 erzeugt werden, obwohl selbst das in der heutigen Zeit nicht unbedingt
ausreichend ist. Die Verschlüsselung per SHA-1 ist, wie auf
<a href="http://www.heise.de/newsticker/meldung/Attacken-auf-SHA-1-weiter-vereinfacht-180587.html" target="_blank">heise online</a>
berichtet, auch nicht mehr ganz so sicher.

Bis bei dem Wettbewerb
<a href="http://csrc.nist.gov/groups/ST/hash/sha-3/index.html" target="_blank">„cryptographic hash Algorithm Competition“</a>
ein Gewinner gekürt wird, würde ich notfalls trotz dessen auf SHA-1 zurückgreifen, da MD5 unsicherer sein dürfte.