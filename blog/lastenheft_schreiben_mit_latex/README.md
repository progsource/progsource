Lastenheft schreiben mit LaTeX
==========

LaTeX ist das HTML des Print-Bereichs - wenn man so will. Hier ein kleiner Einstieg mit Fokus auf ein Lastenheft.

Inhalt eines Lastenhefts
-------------

Helmut Balzert schreibt im Lehrbuch der Software-Technik:

<blockquote>
'''Aufgabe''': Das Lastenheft enthält eine Zusammenfassung aller fachlichen Basisanforderungen, die das zu
entwickelnde Software-Produkt aus der Sicht des Auftraggebers erfüllen muß. »Basisanforderungen« bedeutet eine
bewußte Konzentration auf die fundamentalen Eigenschaften des Produktes und ihre Beschreibung auf einem
hinreichenden Abstraktionsniveau.

'''Inhalt''': Bewußte Konzentration auf die fundamentalen Eigenschaften des Produktes. Beschreibung des »Was«,
nicht des »Wie«.
</blockquote>

Die Gliederung eines Lastenhefts teilt sich in die folgenden 7 Punkte:

# Zielbestimmung
# Produkteinsatz (Anwendungsbereiche und Zielgruppen)
# Produktfunktionen (Kernfunktion nummeriert mit /LF10/, /LF20/, ...)
# Produktdaten (Hauptdaten nummeriert mit /LD10/, /LD20/, ...)
# Produktleistungen (Leistungsanforderungen nummeriert mit /LL10/, /LL20/, ...)
# Qualitätsanforderungen
# Ergänzungen

Aufbau eines LaTeX-Dokuments
-------------

Mit LaTeX werden manche Doktorarbeiten, Berichtshefte, Briefe und so weiter verfasst. Der Grundaufbau ist auch nicht
weiter kompliziert.
Es gibt inzwischen mehrere Programme, mit denen man PDF-Dokumente aus dem LaTeX-Code erstellen kann.
Da wären zum Beispiel:

- <a href="http://www.texniccenter.org/" target="_blank">TeXnicCenter</a>
- <a href="http://www.xm1math.net/texmaker/" target="_blank">Texmaker</a>

Beide oben genannte Programme benötigen <a href="http://miktex.org/" target="_blank">MiKTeX</a>, mit dem man später
auch noch benötigte Pakete hinzuinstallieren kann.

LaTeX Grundgerüst
-------------

Folgend ein Grundgerüst für ein LaTeX-Dokument:

```latex
\documentclass[10pt]{scrreprt} % Schriftgroesse: 10pt; Dokumententyp: Report

% Deutsche Sprachdateien
\usepackage{ngerman}
\usepackage[latin1]{inputenc}

\usepackage{hyperref} % Verlinkungen im Dokument

\author{mona} % Autor
\title{Lastenheft} % Titel

\begin{document} % Hier beginnt der Inhalt des Dokuments

\maketitle % Titelseite generieren
\tableofcontents % Inhaltsverzeichnis generieren

\end{document} % Hier endet das Dokument
```

Grundgerüst für ein einfaches Lastenheft
-------------

Für das Lastenheft werden wir uns ein paar Hilfsfunktionen zurecht legen, die es vereinfachen sollen Funktionen,
Daten und Leistungen zu nummerieren.

```latex
\documentclass[10pt]{scrreprt} % Schriftgroesse: 10pt; Dokumententyp: Report

% Deutsche Sprachdateien
\usepackage{ngerman}
\usepackage[latin1]{inputenc}

\usepackage{hyperref} % Verlinkungen im Dokument

\author{mona} % Autor
\title{Lastenheft} % Titel

% Kommandos fuer das Lastenheft
\newcommand{\lastenheftf}[2]{\subsection{/LF#1/ #2}} % \lastenheftf{10}{Produktfunktion}
\newcommand{\lastenheftd}[2]{\subsection{/LD#1/ #2}} % \lastenheftd{10}{Produktdaten}
\newcommand{\lastenheftl}[2]{\subsection{/LL#1/ #2}} % \lastenheftl{10}{Produktleistung}

\begin{document} % Hier beginnt der Inhalt des Dokuments

\maketitle % Titelseite generieren
\tableofcontents % Inhaltsverzeichnis generieren

\chapter{Zielbestimmungen}

\small{Welche Ziele sollen durch den Einsatz des Produktes erreicht werden?}

\chapter{Produkteinsatz}

\small{Anwendungsbereiche und Zielgruppen}

\chapter{Produktfunktionen}

\small{Hauptfunktionen}

\section{Bereich 1}

\lastenheftf{10}{Funktion 1}
\lastenheftf{20}{Funktion 2}
\lastenheftf{30}{Funktion 3}

\chapter{Produktdaten}

\small{Hauptdaten}

\section{Bereich 1}

\lastenheftd{10}{Information 1}
\lastenheftd{20}{Information 2}
\lastenheftd{30}{Information 3}

\chapter{Produktleistungen}

\small{Leistungsanforderungen bzgl. Zeit, Datenumfang oder Genauigkeit}

\section{Bereich 1}

\lastenheftl{10}{Leistung 1}
\lastenheftl{20}{Leistung 2}

\section{Bereich 2}

\lastenheftl{30}{Leistung 3}

\chapter{Qualitätsanforderungen}

\small{z. B. Zuverlässigkeit, Benutzbarkeit, Effizienz, ...}

\chapter{Ergänzungen}

\small{spezielle Anforderungen vorhanden?}

\end{document} % Hier endet das Dokument
```

Das daraus resultierende PDF-Dokument zum Herunterladen: Lastenheft Grundgerüst (PDF, 49KB).

LaTeX Einführung?
-------------

Das bisher gezeigte reicht selbstverständlich nicht als Einführung in LaTeX. Ein Artikel würde dafür auch längst nicht
ausreichen. Im Internet gibt es aber bereits diverse Tutorials und Dokumentationen - oder man besorgt sich
entsprechende Fachliteratur (s. unten).

Ich hoffe ich konnte zumindest heute mal grob darstellen, was in ein Lastenheft gehört.
Es sollte möglichst so geschrieben werden, dass jeder Leser es direkt versteht. Im Allgemeinen werden Lastenhefte von
Auftraggebern verfasst. Man muss sich nicht peinlichst genau an die hier beschriebene Gliederung halten - es kann aber
nützlich sein, um ein gewünschtes Softwareprodukt möglichst ausführlich zu beschreiben.

Literaturempfehlung zu diesem Artikel
-------------

Lehrbuch der Softwaretechnik: Basiskonzepte und Requirements Engineering von Helmut Balzert,
bei <a href="http://www.progsource.de/b5/61n9n" target="_blank">Bol.de</a>,
<a href="http://www.progsource.de/b5/Ya9qq" target="_blank">Buch.de</a>,
<a href="http://www.progsource.de/b5/b8NjU" target="_blank">Libri.de</a>,
<a href="http://www.progsource.de/b5/Wvt8i" target="_blank">Thalia.de</a>,
<a href="http://www.progsource.de/b5/812xx" target="_blank">Weltbild.de</a>

LATEX, Bd. 1: Einführung von Helmut Kopka,
bei <a href="http://www.progsource.de/b5/okcfy" target="_blank">Bol.de</a>,
<a href="http://www.progsource.de/b5/8SYNK" target="_blank">Buch.de</a>,
<a href="http://www.progsource.de/b5/kW6UT" target="_blank">Libri.de</a>,
<a href="http://www.progsource.de/b5/d3nG8" target="_blank">Thalia.de</a>,
<a href="http://www.progsource.de/b5/W9F9C" target="_blank">Weltbild.de</a>