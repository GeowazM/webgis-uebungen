Exercise 6
==========

.. note::
   
   Ziel der Übung
      - Rasterdaten im GIS öffnen und kennenlernen
      - farbliche Darstellung der Rasterwerte anpassen
      - Rasterdaten in Vektordaten umwandeln
      - Globale Rasteroperationen anwenden (z.B. Projektion ändern)
      - Lokale Rasteroperationen anwenden (z.B. NDVI berechnen)

.. hint::

      -  `Rasterdaten im GIS öffnen und kennenlernen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/-/wikis/qgis-Layer-Konzept>`__
      -  `Darstellung von Rasterdaten <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/-/wikis/qgis-Rasterdarstellung>`__
      -  `Vektordaten in Rasterdaten umwandeln <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/-/wikis/qgis-Konvertierung>`__
      -  `Globale Rasteroperationen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/-/wikis/qgis-Globale-Funktionen>`__
      -  `Lokale Rasteroperationen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/-/wikis/qgis-Lokale-Funktionen>`__


.. seealso::

   Daten
      - Ladet euch die `Daten herunter <https://drive.google.com/file/d/1-HAi07UMHeHFqQSgDtZRzKLDA8SULBk6/view?usp=drive_link>`__ und speichert sie auf eurem PC (.zip Ordner nach dem Download entzippen).
      - Landsat 8 data (Source: Landsat-8 image courtesy of the U.S. Geological Survey; Downloaded via `EarthExplorer <https://earthexplorer.usgs.gov/>`__)
      - Shuttle Radar Topography Mission (SRTM) (Source: `NASA <https://www.usgs.gov/index.php/centers/eros/science/usgs-eros-archive-digital-elevation-srtm-mission-summary#:~:text=The%20objective%20of%20this%20project%20is%20to%20produce,1-arc-second%20%28approximately%2030%20meters%29%20on%20a%20latitude%2Flongitude%20grid.>`__)


Aufgaben
==========

⛰ Aufgabe 1 
--------

Arbeiten mit Geländemodellen

1. Verbinde die SRTM-Kacheln miteinander (z.B. mit merge).
2. Bringe das SRTM-Höhenmodell in eine metrische Projektion (z.B. 25832).
3. Verschaffe dir einen Überblick über die Höhenwerte. Was sind die maximalen und minimalen Höhen im Untersuchungsgebiet. Schaue dies in den Layer-Eigenschaften nach (bspw. mit einem Histogramm).
4. Berechnet aus dem SRTM-Höhenmodell Konturlinien 100 Meter Schritten.
5. Berechnet ein Hillshade (dt. Schummerung).

🛰 Aufgabe 2
--------

Arbeiten mit Landsat 8 Daten

1. In dieser Aufgabe arbeiten wir mit Daten des Landsat 8 Satelliten (LC08). Wir nutzen für unsere Analyse die Bänder 2, 3, 4 & 5. Welchen Farben entsprechen diese Bänder?
2. Erstellt ein Raster Komposit (bzw. Virtual Raster) aus den gegebenen Bändern.
3. Visualisiert das Komposit in Falschfarben, sodass Vegetation rot erscheint (siehe Symbology).
4. Berechnet den Normalized Difference Vegetation Index (bspw. mit dem Raster Calculator).
5. Erstellt anschließend NDVI-Klassen (Reclassify by table). Orientiert euch dabei an folgender Einteilung.

+-----------------------------------+-----------+
| Kategorie                         | NDVI      |
+===================================+===========+
| Wasser und Schnee                 |       < 0 | 
+-----------------------------------+-----------+
| Felsen, Sand, Gebäude	            |   0 - 0.2 |
+-----------------------------------+-----------+
| Gras, Sträucher	                  | 0.2 - 0.4 | 
+-----------------------------------+-----------+
| Wald und intensive Landwirtschaft	|     > 0.4 | 
+-----------------------------------+-----------+

* Stellt die Klassen farblich sinnvoll dar.

🗻 Aufgabe 3 - Optional
--------

3D Visualisierung erstellen

1. Erstellt ein Polygon (Vektordatei), mit dem ihr die Landsat-8 Daten und das SRTM-Höhenmodell auf euer Untersuchungsgebiet zuschneiden (clippen) könnt. Ziel ist es ein Untersuchungsgebiet um den Vesuv zu definieren.
2. Installiert das Plugin Qgis2threejs.
   - Startet den Qgis2threejs Explorer
   - aktiviert das ASTER Höhenmodell & das Landsat-8 Bild
   - Tipp: Ändere die Überhöhung (exaggeration) in den Scene Settings zu 3.0
3. Schaut euch das Modell an, findet eine gute Perspektive und exportiert diese als .png

.. figure:: https://raw.githubusercontent.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/refs/heads/main/exercise_06/vesuvio.jpg
   :alt: 3D Model of Vesuvio and Napoli

   3D Model vom Vesuch, Neapel und Umgebung; Erstellt mit qgisthreejs; Daten: SRTM, Landsat-9 via USGS EarthExplorer
