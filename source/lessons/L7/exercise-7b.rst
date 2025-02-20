Exercise 7
========

Kontext
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- `UNESCO Geopark <https://www.geopark-ries.de/geologie/>`_
- `Geologie Nördlinger Ries <https://www.geopark-ries.de/geologie/>`_

Das **Nördlinger Ries** ist geologisch bemerkenswert, weil es sich um einen der **am besten erhaltenen großen Impaktkrater der Erde** handelt. 

Das Nördlinger Ries entstand vor etwa 14,6 Millionen Jahren durch den Einschlag eines Asteroiden. Dieser Einschlag wird als Ries-Ereignis bezeichnet und 
führte zur Bildung eines nahezu kreisförmigen Kraters mit einem Durchmesser von etwa ? bis ? Kilometern. mIm Ries findet man Suevit, das durch den Einschlag entstanden ist. 
Suevit besteht aus einer Mischung von geschmolzenem und zertrümmertem Material und ist ein typisches Merkmal von Impaktkratern. 
Rund 150 dieser geologischen Besonderheiten sind im UNESCO Global Geopark Ries zu finden. Im Inneren des Kraters befindet sich eine ringförmige Hügelkette, 
die als Kristalliner Ring bezeichnet wird. Diese Struktur unterscheidet das Nördlinger Ries von einfacheren, schüsselförmigen Kratern und ist ein weiteres Indiz für die komplexen Prozesse, die beim Einschlag abliefen.
Der Einschlag führte zur Bildung von Moldaviten, glasartigen Tektiten, die durch die Hitze des Einschlags entstanden und über weite Teile Mitteleuropas verstreut wurden.

In dieser Aufgabe schauen wir uns das Nördlinger Ries an. Verschaffe dir einen ersten Eindruck über den UNESCO Global Geopark Ries `hier <https://www.geopark-ries.de/geologie/>`__. Ein kleines Video zu
den Besonderheiten des Nördlinger Ries findet ihr `hier <https://www.youtube.com/watch?v=YPRzwbnE6kI>`__. 

.. admonition:: Wie verheerend ist ein Asteroideneinschlag?

    :class: admonition-youtube

    ..  youtube:: 68qyJR8P5TI

   `Terra X History on Youtube <https://www.youtube.com/watch?v=68qyJR8P5TI>`_.

.. note::
   
   Ziel der Übung
      -  Rasterdaten zuschneiden
      -  Reliefanalysen durchführen
      -  zonale Statistiken berechnen
      -  Rasterdaten in Vektordaten umwandeln
      -  ein Höhenprofil erstellen

.. hint::

      -  `Rasterdaten im GIS öffnen und kennenlernen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/-/wikis/qgis-Layer-Konzept>`__
      -  `Darstellung von Rasterdaten <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/-/wikis/qgis-Rasterdarstellung>`__
      -  `Vektordaten in Rasterdaten umwandeln <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/-/wikis/qgis-Konvertierung>`__
      -  `Globale Rasteroperationen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/-/wikis/qgis-Globale-Funktionen>`__
      -  `Lokale Rasteroperationen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/-/wikis/qgis-Lokale-Funktionen>`__


.. seealso::

   Daten
      - Ladet euch die `Daten herunter <https://drive.google.com/file/d/11oB7zJvFFbwGA0gy2a9i4-cSSWlNzCMp/view?usp=drive_link>`__ und speichert sie auf eurem PC (.zip Ordner nach dem Download entzippen).
      - Linien-Layer: Transect_1 und Transect_2 - Quelle: Own research
      - Raster-Layer: SRTM Höhendaten (Quelle: NASA JPL (2013). NASA Shuttle Radar Topography Mission Global 1 arc second. Accessed 2024-03-14 from https://doi.org/10.5067/MEaSUREs/SRTM/SRTMGL1.003)

Aufgaben
--------

⛰ Aufgabe 1 - Digital Elevation Model (DEM)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Vorbereitung des DEM's 

* Verschmelzt die SRTM-Kacheln (SRTMGL1) miteinander (z.B. via **Merge**). 
* Bringt das Höhenmodell in eine passende **metrische Projektion** (z.B. ETRS 89 / UTM 32N). 
* Verschafft euch einen Überblick über die Werte. Bei digitalen Geländemodellen sind dies immer Höhenwerte. Was sind die maximalen und minimalen Höhen im Untersuchungsgebiet? 
* Ladet euch mit Hilfe von *QuickMapServices* eine *OSM Standard* Hintergrundkarte (**Basemap**) in euer Projekt. Wo befindet sich unser Untersuchungsgebiet?
* Nutze das Mess-Tool, um die Nord-Süd-Distanz des Kraters auszumessen. Wie Breit ist der Kraterrand (circa)?

〰 Aufgabe 2 - Ein Höhenprofil erstellen
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Vorsicht: Plugins können etwas undurchsichtig sein. Achtet auf die einzelnen Schritte des Erklärvideos. Kleinigkeiten können hier entscheidend sein.
-  Erstellt für den Transect_1-Layer ein Höhenprofil (bspw. Profil_1a).
-  Das Höhenprofil soll auf der x-Achse die Distanz in Meter zeigen & auf der y-Achse die Höhe ü.N.
-  Speichert euer Höhenprofil als PNG ab.
-  Glättet jetzt euer Ergebnis in dem ihr pro Pixel den Durchschnitt der 21x21 Nachbarschaft berechnet (via **r.neighbors**).
-  Erstellt mit Hilfe des Transect_1-Layer nochmals ein Höhenprofil (bspw. Profil_1b). Speichert es erneut und vergleicht es mit dem ersten Profil. Was für ein Unterschied ist erkennbar?
-  Jetzt erstelle ein Höhenprofil mit dem Transect_2 Layer und exportiere dies ebenfalls (bspw. Profil_3).
-  Kreiere eine eigene Linie (**Layer - Create layer**), visualisiere damit ein Höhenprofil und speichere dies (Profil 3).

.. figure:: https://raw.githubusercontent.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/refs/heads/main/exercise_07/exercise_7_neu/noerdlinger-ries_profile.png
   :alt: SRTM-Höhenmodell des inkl. Transect

   SRTM-Höhenmodell des Nördlinger Ries inkl. Transect

.. figure:: https://raw.githubusercontent.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/refs/heads/main/exercise_07/exercise_7_neu/noerdlinger-ries_profile_profile-tool.png
   :alt: Profil des Transects

   Profil des Transects; Erstellt mit QGIS Plugin *Profile Tool*; Daten: SRTM