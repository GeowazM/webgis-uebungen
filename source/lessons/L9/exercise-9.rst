Exercise 9
=======

.. note::
   
      -  Workflows automatisieren

.. hint::

      -  `Automatisierung <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Automatisierung>`__


.. seealso::

   Daten
      - Ladet euch die `die Daten herunter <https://github.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/blob/main/exercise_09/exercise_09.zip>`__ und speichert sie auf eurem PC (.zip Ordner nach dem Download entzippen).
      - Straßen-Layer (Quelle: `OpenStreetMap and Contributors <https://www.openstreetmap.org>`__)
      - Hotels-Layer (Quelle: `OpenStreetMap and Contributors <https://www.openstreetmap.org>`__)

Kontext
-------

Ihr möchtet in Zukunft wiederkehrend den vom Verkehr beeinträchtigten Bereich rund um Hotels berechnen. 
Dabei möchten ihr auch Parameter variieren. Erstellt hierfür ein geeignetes Werkzeug.

Aufgabe
=======

Aufgabe 1 
----------

Erstellt ein Modell, welches

1.  einen Punkt- und einen Linienlayer einlesen kann
2.  die Punkte mit einem frei wählbaren Pufferabstand puffert (der von Hotels oder anderen Einrichtungen direkt erreichbare Bereich)
3.  Die Linien mit einem zweiten frei wählbaren Pufferabstand puffert (welcher den vom Lärm beeinflussten Bereich rund um Straßen repräsentiert)
4.  die Schnittmenge dieser Puffer berechnet
5.  abschließend noch einen *Dissolve* ausführt

Aufgabe 2: Modell ausführen
---------------------------

Modell ausführen -  nutzt euer Modell um die folgende Parameterkombinationen zu testen

1. Hotel-Buffer: 50m, Straßen-Buffer: 50m
2. Hotel-Buffer: 100m, Straßen-Buffer: 100m
3. Hotel-Buffer: 150m, Straßen-Buffer: 150m

So oder ähnlich könnte euer finales Modell aussehen:

.. figure:: https://raw.githubusercontent.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/refs/heads/main/exercise_09/model.PNG
   :alt: Tool im ModelBuilder

   Quelle: QGIS - Tool im ModelBuilder
