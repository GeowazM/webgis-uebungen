Exercise 5 b
==========

.. note::
   
   Ziel der Übung
      -  web-basierte Hintergrundkarten nutzen
      -  Vektordaten händisch erstellen (Digitalisieren)

.. note::

   Wiki
      -  `Basemaps <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Basemaps>`__
      -  `Digitalisieren <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Digitalisierung>`__


.. seealso::

   Daten
      * Ladet euch `die Daten herunter <https://github.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/blob/main/exercise_05a/exercise_5a_iceland/exercise_5a_data_iceland.zip>`__ und
      * Speichert sie auf eurem PC
      * Legt einen lokalen Ordner an und
      * Speichert dort die obigen Daten. (.zip Ordner müssen vorher entpackt werden.)
      * Quelle: Landsat-9 image vom 17.07.2023 heruntergeladen via `USGS EarthExplorer <https://earthexplorer.usgs.gov/>`__

Daten digitalisieren
^^^^^^^

Du brauchst für deinen Nebenjob Daten über das Eruptionsgeschehen auf Island. Die isländischen Behörden stellen jedoch keine Geodaten zur Verfügung.
Allerdings kannst du die betroffenen Gebiete auf Satellitenbildern ausfindig machen. Um aus den Bilddaten (bspw. Satelliten oder georeferenzierten Karten)
Geodaten zu gewinnen, die du mit weiteren Informationen anreichern kannst, musst du diese digitalisieren.

Aufgaben
--------

In den Daten findet ihr eine Landsat 9 Satellitenbildaufnahme, die am 17.07.2023 aufgenommen wurde. Wir wollen herausfinden, wie groß die von Lava überflossene Fläche ist.

1. Erstellt zwei neue Layer: Einen für (a) die Lavafläche und einen zweiten (b) für Straßen. Fügt zu jedem Layer ein Attribute "Name" hinzu.
2. Nutze als Kartierungsgrundlage die Landsat 9 Aufnahme in den Daten und eine Hintergrundkarte auf Basis von Satellitendaten (z.B. Bing, OSM). Diese könnt ihr mit Hilfe des Plugins QuickMapServices in QGIS einbinden. Was ist der UNterschied zwischen Bing Satellite und der Landsat-9 Aufnahme?
3. Digitalisiere die Fläche des Eruptionsereignissen ab. Digitalisiere ebenfalls die Straße von Reykjavik nach Grindavik inkl. deren Kennzeichnung ab.
4. Füge zu jedem Feature den passenden Namen hinzu.
5. Berechne die Fläche der von dir digitalisierten Lavafläche. Wie viel km² sind es?
5. Optional: Füge zur von dir bestimmten Lavafläche einen Hyperlink zu weiteren Informationen (bspw. siehe unten) hinzu.

- Für weitere Informationen könnt ihr hier reinschauen: `NASA Earth Observation <https://earthobservatory.nasa.gov/images/151653/lava-and-smoke-blanket-fagradalsfjall>`__
- Einige vor Ort Aufnahmen könnt ihr euch hier anschauen: `Volcano at Litlihrutur Iceland <https://youtu.be/tvxbKWxmfXk?si=XYrX663QaoqlOEPo>`__

.. figure:: https://raw.githubusercontent.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/refs/heads/main/exercise_05a/exercise_5a_iceland/exercise_5a_iceland.png
   :alt: Landsat-9 image of iceland

   Quelle: Own research, Landsat-9 image from 17.07.2023 of the U.S. Geological Survey
