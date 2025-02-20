Exercise 6 - Optional
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
      - Ladet euch die `Daten herunter <https://drive.google.com/file/d/1dlhFX5jOUJlZ0bNdei4iQWQ6xCXnkDTh/view?usp=drive_link>`__ und speichert sie auf eurem PC (.zip Ordner nach dem Download entzippen).
      - Landsat 8 data (Source: Landsat-8 image courtesy of the U.S. Geological Survey; Downloaded via `EarthExplorer <https://earthexplorer.usgs.gov/>`__)
      - ASTER Global Digital Elevation Map (GDEM) SRTM DEM (Source: `NASA JPL <https://asterweb.jpl.nasa.gov/GDEM.asp>`__)


Aufgaben
==========

Aufgabe 4 - Optional
--------

In den Daten findet ihr eine Landsat 9 Satellitenbildaufnahme, die am 17.07.2023 aufgenommen wurde. Wir wollen herausfinden, wie groß die von Lava überflossene Fläche ist.

1. Erstellt zwei neue Layer: Einen für (a) die Lavafläche und einen zweiten (b) für Straßen. Fügt zu jedem Layer ein Attribute "Name" hinzu.
2. Nutze als Kartierungsgrundlage die Landsat 9 Aufnahme in den Daten und eine Hintergrundkarte auf Basis von Satellitendaten (z.B. Bing, OSM). Diese könnt ihr mit Hilfe des Plugins QuickMapServices in QGIS einbinden. Was ist der UNterschied zwischen Bing Satellite und der Landsat-9 Aufnahme?
3. Digitalisiere die Fläche des Eruptionsereignissen ab. Digitalisiere ebenfalls die Straße von Reykjavik nach Grindavik inkl. deren Kennzeichnung ab.
4. Füge zu jedem Feature den passenden Namen hinzu.
5. Berechne die Fläche der von dir digitalisierten Lavafläche. Wie viel km² sind es?
6. Optional: Füge zur von dir bestimmten Lavafläche einen Hyperlink zu weiteren Informationen (bspw. siehe unten) hinzu.

.. figure:: https://raw.githubusercontent.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/refs/heads/main/exercise_06/qgisthreejs.jpg
   :alt: 3D Model

   Quelle: 3D Model erstellt mit qgisthreejs