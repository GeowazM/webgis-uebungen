Exercise 3
==========

Ziel der Übung
--------------

-  Nicht-räumliche Abfragen durchführen.
-  Räumliche Abfragen durchführen.
-  Geometrieoperationen nutzen (z.B. die Fläche eines Polygons
   berechnen).

Wiki:
-----

-  `Nicht-Räumliche Abfragen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Nicht-Räumliche-Abfragen>`__
-  `Räumliche
   Abfragen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Räumliche-Abfragen>`__
-  `Geometrieoperationen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Geometrieoperationen>`__

Daten
-----

Ladet euch `die Daten herunter <exercise_03_data.zip>`__ und speichert
sie auf eurem PC. \* World Administrative Boundaries Level 0 (Countries)
(Polygon) (Quelle: `World Food Programme
WFPGeonode <https://geonode.wfp.org/layers/geonode%3Awld_bnd_adm0_wfp>`__)
\* Urban Agglomerations Datensatz (Point) (Quelle: `UN World
Urbanization Prospects 2018 <https://population.un.org/wup/>`__)

Aufgaben
--------

1. Öffne die oben angegebenen Dateien in QGIS.
2. Wähle 3 Städte deiner Wahl (manuell) in der Benutzeroberfläche aus.
   Öffne nun die Attributtabelle und lass dir die Informationen für die
   ausgewählten Features anzeigen. Speichere die ausgewählten Features
   anschließend in einer neuen Datei (Layer).
3. In welcher Einheit liegen die Einwohnerzahlen vor? Dies ist für die
   folgenden Aufgaben wichtig.
4. Wähle nun anhand einer Abfrage (automatisch) alle Städte, welche im
   Jahr 2015 mehr als 15 Millionen Einwohner hatten. Wie viele Städte
   gibt es, die diese Bedingung erfüllen? Welche Stadt hat die meisten
   Einwohner?
5. Führe nun eine kombinierte Selektion durch. Selektiere zunächst alle
   Städte in China. Entferne anschließend alle Städten mit einer
   Einwohnerzahl kleiner als 1 Million aus dieser Auswahl. Wie viele
   Millionenstädte gibt es in China?
6. Berechne die Fläche jedes einzelnen Features in Quadratmeter. (Bei
   Fragestellungen dieses Typs ist es besonders wichtig die Projektion
   der Daten zu beachten. Wir nutzen hier hier Mollweide (EPSG: 54009),
   eine flächentreue Projektion.) Welches ist das kleinste Land der Welt
   und wie groß (klein) ist es? Unter Land verstehen wir hier alle
   Features mit dem Status *Member State*.



.. note::

    Please complete this exercise by **the start of the next lesson**.

.. admonition:: Pair programming

    Students attending the course in Helsinki, **note that we continue working in pairs**.
    We will only grade the repository of the member of your pair that is responsible for this week's exercise.
    See more information in Slack, and in week 2: `Why are we working in pairs? <https://geo-python-site.readthedocs.io/en/latest/lessons/L2/why-pairs.html>`_

Cloud computing environments
----------------------------

.. image:: https://img.shields.io/badge/launch-binder-red.svg
   :target: https://mybinder.org/v2/gh/Geo-Python-2024/Binder/main?urlpath=lab
   
.. image:: https://img.shields.io/badge/launch-CSC%20Noppe-blue.svg
   :target: https://noppe.csc.fi

Exercise 3 hints
----------------

Here are a few things that may be helpful in completing Exercise 3.

Tests
~~~~~

The exercise notebook contains some tests help you see if your code is working correctly. Some code cells contain
a line that says: `raise NotImplementedError()`. Always remove this piece of code from your submission and replace
it with your own code. The error tells us if you have not started the exercise.

Combining strings
~~~~~~~~~~~~~~~~~

In case you have forgotten, string variables can be added together. For example,

.. code-block:: python

    a = "Taco "
    b = "time"
    c = a + b
    print(c)

Nested if statements
~~~~~~~~~~~~~~~~~~~~

In some cases it might be useful to have nested if statements, meaning that you have another layer of
conditions after the first condition resolves to True.

Take a look of following example:

.. code-block:: python

    season = "Winter"
    temperature = 10

    if season == "Winter":

        if temperature > 7:
            print("No need for winter jacket!")

        else:
            print("It might be cold! Wear a proper jacket!")

   elif season == "Summer":

        if temperature > 20:
            print("It's warm! Time to wear shorts!")

        else:
            print("Well this is Finland, better wear long trousers!")
   else:
        print("Check the weather forecast!")
