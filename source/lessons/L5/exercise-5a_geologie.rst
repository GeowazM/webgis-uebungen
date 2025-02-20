Exercise 5 a
========

.. admonition:: Start your assignment

    **Du kannst zwischen verschiedenen Karten, die du georeferenzieren sollst, auswählen**.

.. hint::
   
   Ziel der Übung
      -  web-basierte Hintergrundkarten nutzen
      -  Ein Bild (Raster) Georeferenzieren


.. seealso::

   Daten
      - Ladet euch `die Daten herunter <https://github.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/blob/main/exercise_05b/exercise_05b_data.zip>`__ und
      - Speichert sie auf eurem PC
      - Legt einen lokalen Ordner an und
      - Speichert dort die obigen Daten. (.zip Ordner müssen vorher entpackt werden.)


Ein Bild georeferenzieren
~~~~~~~~~~~~~~~~~~~~~~~~~

Kontext
^^^^^^^

Du brauchst für dein Projekt eine geologische Karte von Heidelberg. Die einzig verfügbaren Informationen, die du finden kannst ist eine PDF
Karte der Universität Heidelberg. Um diese geologische Karte mit deinen weiteren Geodaten zu verknüpfen, müssen wir diese georeferenzieren.

.. figure:: https://raw.githubusercontent.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/refs/heads/main/exercise_05b/geologische_karte_heidelberg.PNG
   :alt: Geologische Karte von Heidelberg

   Geologische Karte von Heidelberg

.. raw:: html

   <p align="center">Quelle: Universitätbibliothek Heidelberg</p>


Aufgabe
-----

1. Versehe das zur Verfügung gestellte Raster mit WGS 84 / UTM Zone 32N Koordinaten (EPSG: 32632).
2. Verwende als Referenz-Layer eine Webkarte deiner Wahl (bspw. OSM Standard oder Bing Satellite), welche du in Form einer Hintergrundkarte einbinden kannst.
3. Wähle eine geeignete Transformationsvorschrift (bspw. Ploynominal 1, 2 oder 3) und setzt genügend und ausreichend verteilte Passpunkte.
4. Kontrolliere abschließend deinen Erfolg, indem du die Passgenauigkeit des georeferenzierten Bildes mit überlagerten Hintergrundkarte vergleichst.

