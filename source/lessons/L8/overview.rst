Interpolation
===============

Räumliche Interpolation
--------------

Räumliche Interpolation bezieht sich auf die Schätzung von Werten an unbekannten geografischen Positionen, basierend auf bekannten Werten in benachbarten Positionen. 
Dies ist besonders nützlich in der Geowissenschaft und Umweltforschung.

Nutzen der räumlichen Interpolation:

1. Datenlücken füllen: Hilft dabei, fehlende Daten in geografischen Datensätzen zu ergänzen.
2. Erstellung kontinuierlicher Flächen: Ermöglicht die Erstellung von Karten und Modellen, die kontinuierliche Flächen darstellen, wie z.B. Temperatur- oder Höhenkarten.
3. Verbesserte Analyse: Unterstützt bei der Analyse und Visualisierung räumlicher Muster und Trends.

Räumliche Interpolationsverfahren
--------------

Thiessen Polygone (Voronoi Diagramm)

* erstellt Voronoi Diagramme anhand eines Punk-Layers

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/videos/qgis_voronoi.mp4">

.. raw:: html

   </video>


Inverse Distanzgewichtung (IDW)

* Interpolation Attribut hinzufügen
* Distance Coefficient –> Power
* Extent angeben
* Output Raster Size: ACHTUNG: wird in den Einheiten des Layers angegeben, sprich bei einer metrischen Projektion in Meter, im Beispiel nutzen wir 1000 m

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/videos/qgis_idw.mp4">

.. raw:: html

   </video>