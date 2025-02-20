Exercise 4
==========

.. hint::

   Ziel der Übung
      *  `Geometriefunktionen vertiefen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Geometrieoperationen>`__
      *  `Vektordaten räumlich verschneiden <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Räumliche-Verschneidungen>`__
      *  `Räumliche Joins durchführen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Räumliche-Joins>`__
      *  `Tabellenfunktionen nutzen und einfache Statistiken erstellen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Tabellenfunktionen>`__

.. seealso::

   Daten
   Ladet euch `die Daten herunter <exercise_04_data.zip>`__ und speichert
   sie auf eurem PC. Legt einen lokalen Ordner an und speichert dort die
   obigen Daten (.zip Ordner müssen vorher entpackt werden.).
      * Osnabrück Fluss Hase (Line) (Quelle: `OpenStreetMap <https://www.openstreetmap.org>`__)
      * Osnabrück Straßennetzwerk (Line) (Quelle: `OpenStreetMap <https://www.openstreetmap.org>`__)
      * Osnabrück Stadtgrenze (Polygon) (Quelle: `OpenStreetMap <https://www.openstreetmap.org>`__)
      * Osnabrück Gebäude (Polygon) (Quelle: `OpenStreetMap <https://www.openstreetmap.org>`__)

Aufgaben
--------

In deiner Heimatstadt wird das Thema Hochwasser diskutiert. Du möchtest sich einen ersten Eindruck verschaffen, welche Flächen 
von einem Hochwasser betroffen wären und wie groß der Schaden an Gebäuden und Straßen sein würde. Da dir keine offiziellen Geodaten 
zur Verfügung stehen beziehst du Volunteered Geographic Information (VGI) wie OpenStreetMap-Daten.

Datenvorbereitung
~~~~~~~~~~~~~~~~~

1. Schneidet den Gebäude-Datensatz und den Straßen-Layer auf das Stadtgebiet Osnabrücks zu (**Clip** Funktion).
2. Projiziert anschließend alle Daten in ein metrisches Koordinatensystem (z.B. WGS 84 / UTM 32N).

Hochwasserbereich ermitteln
~~~~~~~~~~~~~~~~~~~~~~~~~~~

3. Verbindet alle Teilstücke der Hase zu einer einzelnen Geometrie. Nutzt dazu die **Dissolve** Funktion.
4. Zur Berechnung der Hochwassergefahr nutzen wir einen vereinfachten Ansatz. Berechnet 3 Stufen der Hochwassergefahr mithilfe der **(Multiple)Buffer**-Funktion:

(a) alle Bereiche in Abstand von maximal 100 m zur Hase,
(b) alle Bereiche zwischen 100 m und 200 m Abstand,
(c) alle Bereiche mit einem Abstand von mehr als 200 m bis zu 300 m.

-  optional: Färbt die Bereiche ensprechend der Hochwassergefahr ein.

Gebäude nach Hochwassergefahr einteilen
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

5. Fügt zu jedem Gebäude die maximale Hochwassergefahrenklasse (a, b, c) hinzu. Nutzt dafür die **Join Attribute by Location** Funktion.
6. Zählt wie viele Gebäude in jede der drei Klassen vorhanden sind. Erstellt dazu eine kategorisierte Statistik der Attributwerte
   (**Statistic by categories** Funktion) in Form einer Tabelle und speichert diese.

   *  optional: Färbt die Gebäude ensprechend der Hochwassergefahr ein.
   *  optional: Visualisiert die Statistik mit einem Balkendiagramm. Nutzt
   dafür ein Programm eurer Wahl (z.B. Excel).

Hochwassergefährdete Bereiche im Straßennetzwerk ausweisen
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

7. Verschneidet das Straßennetzwerk mit dem Hochwassergefahr-Layer (**Clip**).
8. Berechnet anschließend die Länge der neu enstandenen Straßensegmente (**$length**).
9. Auf welcher Gesamtlänge sind die unterschiedlichen Straßentypen möglicherweise von Hochwasser pro Klasse (a, b, c) betroffen?
   Erstellt dafür eine gruppierte Statistik.

   *  optional: Visualisiert die Statistik in einem Balkendiagramm. Nutzt dafür ein Programm eurer Wahl (z.B. Excel).

So (oder ähnlich) sieht’s am Ende aus
-------------------------------------

.. figure:: https://raw.githubusercontent.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/refs/heads/main/exercise_04/osnabrueck_karte.png
   :alt: Karte von Osnabrück

   Karte von Osnabrück

.. figure:: https://raw.githubusercontent.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/refs/heads/main/exercise_04/building_count_stats.png
   :alt: Statistik zu Gebäuden

   Statistik zu Gebäuden

.. figure:: https://raw.githubusercontent.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/refs/heads/main/exercise_04/road_length_stats.png
   :alt: Statistik zu Straßen

   Statistik zu Straßen