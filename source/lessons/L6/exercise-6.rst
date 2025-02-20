Exercise 6
==========

.. note::

    Please complete this exercise by **the start of the next lesson**.


Exercise 6 hints
-----------------

Data format for problems 1-3
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The first 5 rows of the data file look like the following:

.. code:: python

    STATION           ELEVATION  LATITUDE   LONGITUDE  DATE     PRCP     TAVG     TMAX     TMIN     
    ----------------- ---------- ---------- ---------- -------- -------- -------- -------- -------- 
    GHCND:FIE00142080         51    60.3269    24.9603 19520101 0.31     37       39       34       
    GHCND:FIE00142080         51    60.3269    24.9603 19520102 -9999    35       37       34       
    GHCND:FIE00142080         51    60.3269    24.9603 19520103 0.14     33       36       -9999    

As you can see, we have rainfall data (``PRCP``) in inches, and temperature data (``TAVG``, ``TMAX``, and ``TMIN``) in degrees Fahrenheit.
Dates of the observations are given in the format YYYYMMDD.
No-data values are indicated with ``-9999``.

Reading in fixed-width text files
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Rather than having separation by commas, our data file this week has a variable number of spaces between values.
Previously, we read in comma-separated values using the option ``sep=','`` for the Pandas ``read_csv()`` function.
For a variable number of spaces we can either use the ``sep`` or ``delim_whitespace parameter``; ``sep='\s+'`` or ``delim_whitespace=True`` will work, but not both.
In this case, we suggest using ``delim_whitespace``.

Skipping the second row of a file
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The ``skiprows=n`` option of the Pandas ``read_csv()`` function is an easy way to skip the first *n* rows of a file when reading it.
If we wanted to skip the first two rows of our data file, we could thus use ``skiprows=2``.
The value for ``n``, however, need not be a single value, but can also be given in the form of a list.
In this way, one can skip reading the second row of a file using a list with an index value for the second row.
In other words, you can use ``skiprows=[1]``.

Joining data from one DataFrame to another
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

One quite useful functionality in Pandas is the ability to conduct a **table join**
where data from one DataFrame is merged with another DataFrame based on a common **key**.
Hence, making a table join requires that you have at least one common variable in both
of the DataFrames that can be used to combine the data together.

Consider a following example. Let's first create some test data to our DataFrames.

.. ipython:: python
    :suppress:

        import pandas as pd

.. ipython:: python

    data1 = pd.DataFrame(data=[['20170101', 'Pluto'], ['20170102', 'Panda'], ['20170103', 'Snoopy']], columns=['Time', 'Favourite_dog'])
    data2 = pd.DataFrame(data=[['20170101', 1], ['20170101', 2], ['20170102', 3], ['20170104', 3], ['20170104', 8]], columns=['Time', 'Value'])
    data1
    data2

Übung 6
=======

Ziel der Übung
--------------

-  Rasterdaten im GIS öffnen und kennenlernen
-  farbliche Darstellung der Rasterwerte anpassen
-  Rasterdaten in Vektordaten umwandeln
-  Globale Rasteroperationen anwenden (z.B. Projektion ändern)
-  Lokale Rasteroperationen anwenden (z.B. NDVI berechnen)

Wiki:
-----

-  `Rasterdaten im GIS öffnen und
   kennenlernen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Layer-Konzept>`__
-  `Darstellung von
   Rasterdaten <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Rasterdarstellung>`__
-  `Vektordaten in Rasterdaten
   umwandeln <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Konvertierung>`__
-  `Globale
   Rasteroperationen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Globale-Funktionen>`__
-  `Lokale
   Rasteroperationen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Lokale-Funktionen>`__

Daten
-----

Ladet euch vom USB-Stick und speichert sie auf eurem PC. Legt einen
lokalen Ordner an und speichert dort die Daten. (.zip Ordner müssen
vorher entpackt werden.)

-  Landsat 8 data (Source: Landsat-8 image courtesy of the U.S.
   Geological Survey; Downloaded via
   `EarthExplorer <https://earthexplorer.usgs.gov/>`__
-  ASTER Global Digital Elevation Map (GDEM) SRTM DEM (Source: `NASA
   JPL <https://asterweb.jpl.nasa.gov/GDEM.asp>`__

Aufgaben
--------

Aufgabe 1: Arbeiten mit Geländemodellen
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Verbindet die ASTER-Kacheln (ASTGMT2) miteinander (z.B. mit
   **merge**).
-  Bringt das ASTER-Höhenmodell in eine metrische Projektion (z.B.
   WGS84/UTM 37N).
-  Verschafft euch einen Überblick über die Höhenwerte. Was sind die
   maximalen und minimalen Höhen im Untersuchungsgebiet. Schaut dies in
   den Layer-Eigenschaften nach.
-  Berechnet aus dem ASTER-Höhenmodell Konturlinien 100 Meter Schritten.
-  Berechnet ein Hillshade (dt. Schummerung).

Aufgabe 2: Arbeiten mit Landsat 8 Daten
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  In dieser Aufgabe arbeiten wir mit Daten des Landsat 8 Satelliten
   (*LC08*). Wir nutzen für unsere Analyse die Bänder 2, 3, 4 & 5.
   Welchen Farben entsprechen diese Bänder?
-  Erstellt ein Raster Komposit (bzw. **Virtual Raster**) aus den
   gegebenen Bändern.
-  Visualisiert das Komposit in Falschfarben, sodass Vegetation rot
   erscheint (siehe *Symbology*).
-  Berechnet den Normalized Difference Vegetation Index (bspw. mit dem
   **Raster Calculator**).
-  Erstellt anschließend NDVI-Klassen (**Reclassify by table**).
   Orientiert euch dabei an folgender Einteilung.

================================= =========
Kategorie                         NDVI
================================= =========
Wasser und Schnee                 < 0
Felsen, Sand, Gebäude             0 - 0.2
Gras, Sträucher                   0.2 - 0.4
Wald und intensive Landwirtschaft > 0.4
================================= =========

-  Stellt die Klassen farblich sinnvoll dar.

Aufgabe 3: 3D Visualisierung erstellen
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Erstellt ein Polygon (Vektordatei), mit dem ihr die Landsat-8 Daten
   und das ASTER-Höhenmodell verkleinern (clippen) könnt. Ziel ist es
   ein Untersuchungsgebiet um den Vesuv zu definieren.
-  Installiert das Plugin *Qgis2threejs*.

   -  Startet den *Qgis2threejs Explorer*,
   -  aktiviert das ASTER Höhenmodell & das Landsat-8 Bild.
   -  Tipp: Ändere die Überhöhung (exaggeration) in den Scene Settings
      zu 2.5.

-  Schaut euch das Modell an, findet eine gute Perspektive und
   exportiert diese als .png

So (oder ähnlich) kann es am Ende aussehen
------------------------------------------

.. figure:: qgisthreejs.jpg
   :alt: 3D Landschaft

   3D Landschaft

Quelle: `Qthreejs
Plugin <https://qgis2threejs.readthedocs.io/en/docs/_images/top.jpg>`__