==========
Übung 3 - Konfiguration
==========

.. hint::

   Ziel der Übung
      * Erste Einblicke in *Visual Studio Code* 
      * Die Extension *Live Server* kennenlernen

.. seealso::

      *  `Visual Studio Code <https://code.visualstudio.com/>`__
      *  `Live Server <https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer>`__
      *  `Masterportal Docs <https://www.masterportal.org/mkdocs/doc/v3.7.0/User/About/>`__


Masterportal konfigurieren
===========
Jetzt haben wir alle notwendigen Vorbereitungen getroffen und können mit der Entwicklung bzw. Konfiguration unseres Masterportal-Geoviewer starten.
Ein zentrales Dokument, dass wir für die Konfiguration brauchen ist `die offizielle Dokumentation (Masterportal Docs) <https://www.masterportal.org/mkdocs/doc/v3.7.0/User/About/>`__.
Das *Masterportal example* befindet sich in Hamburg. Die dort eingesetzten Parameter ändern wir jetzt Schritt für Schritt, um aus dem Example unseren eigenen Geoviewer zu konfigurieren.

Titel & Logo ändern
-----------

.. caution::

   Die *index.html* betrifft ausschließlich den Browsertab. Der Masterportal code ist so aufgebaut, dass alles, was innerhalb des Browserfensters passiert, in den *Global-* und *Portal-Settings* definiert ist.

Da wir ohnehin die *index.html* Seite offen haben, können wir direkt den Titel und das Logo des Geoviewers im Browsertab ändern.

1. In der *index.html* kannst du den Titel der Seite ändern 
2. Füge eine Logo (fiktiv oder dein Eigenes) in den Ordner *resources/img/UT-logo.svg* (siehe Bild)
3. Füge die Zeile *<link rel="icon" href="./resources/img/UT-logo.svg">* ein und speichere dein Projekt (Strg+S)

.. figure:: img/masterportal_index_html_title.PNG
   :alt: Angepasster Titel und Logo
   :width: 800px

   Angepasster Titel und Logo

4. Öffne nun die Datei *config.json* (bspw. *uni-tuebingen/config.json*)
5. Navigiere zum Abschnitt **"portalFooter"**. Ändere den URL zu einer Website deiner Wahl. Passe den Alias & den mobilen Alias an. Das kann dann bspw. wie folgt aussehen.

.. code-block:: json

   {
    "portalFooter": {
      "urls": [
        {
          "bezeichnung": "common:modules.portalFooter.designation",
          "url": "https://www.geodatenmanagerin-tuebingen.de/termine-anmeldung/",   // Füge deine eigene URL ein
          "alias": "Geodatenmanager/-in - Universität Tübingen",                    // Füge einen Text ein, der für die URL angezeigt werden soll
          "alias_mobil": "GDM"                                                      // Füge einen Text ein, der in der mobilen Version angezeigt werden soll
        }
      ]
    },

Kartenviewer (Map canvas) anpassen
-----------

Jetzt widmen wir uns dem Kern unseres Geoviewers - dem Kartenview. Dafür müssen wir die geographische Ausdehnung (*Extent*) & 
den zentralen Startpunkt definieren (*Centroid* oder *Geoinstitut*) bzw. den  festlegen. Dafür nutzen wir die Daten aus der Vorbereitung.

1. Öffne die Datei *config.json* (bspw. *uni-tuebingen/config.json*)

**"portalConfig"**
^^^^^^^^^^^

2. Navigiere zum unten aufgeführten Code Bereich `portalConfig <https://www.masterportal.org/mkdocs/doc/v3.7.0/User/Portal-Config/config.json/>`__.

-> Ausgangssituation

.. code-block:: json

   {
  "portalConfig": {
    "map": {
      "controls": {
        "zoom": true,
        "orientation": {
          "zoomMode": "once"
        }
      },
      "mapView": {
        "backgroundImage": "./resources/img/backgroundCanvas.jpeg",
        "startCenter": [
          561210,
          5932600
        ],
        "extent": [
          510000.0,
          5850000.0,
          625000.4,
          6000000.0
        ],
        "startZoomLevel": 1
      }
    },

Startpunkt - **"startCenter"**
"""""""""""

Jetzt passen wir die einzelnen Bereiche auf unser Untersuchungsgebiet an. Wir starten mit dem `zentralen Startpunkt <https://www.masterportal.org/mkdocs/doc/v3.7.0/User/Portal-Config/config.json.de/#datatypescoordinate>`__.

3. Füge die Koordinaten deines Centroids oder deines zentralen Interessenpunkts (bspw. Geoinstitut) in den Code ein.

   .. raw:: html

      <details>

   .. raw:: html

      <summary>

   Hinweis

   .. raw:: html

      </summary>

   .. raw:: html

      <ul>

   .. raw:: html

      <li>

   Siehe **"startCenter"**. Die erste Koordinate repräsentiert den Rechtswert, die zweite den Hochwert.

-> Dein Ordner (bspw. uni-tuebingen)

.. code-block:: json

   {
  "portalConfig": {
    "map": {
      "controls": {
        "zoom": true,
        "orientation": {
          "zoomMode": "once"
        }
      },
      "mapView": {
        "backgroundImage": "./resources/img/backgroundCanvas.jpeg",
        "startCenter": [
          504116.11181222,
          5374563.32233909
        ],
        "extent": [
          510000.0,
          5850000.0,
          625000.4,
          6000000.0
        ],        
        "StartResolution": 9028,
        "StartZoomLevel": 1,
        "epsg": "EPSG:25832"
      }
    },

Ausdehnung - **"extent"**
"""""""""""

4. Als nächstes definieren wir den geographischen Rahmen (*Extent* oder *Bbox*) unseres Geoviewers


   .. raw:: html

      <details>

   .. raw:: html

      <summary>

   Hinweis

   .. raw:: html

      </summary>

   .. raw:: html

      <ul>

   .. raw:: html

      <li>

   Ein Extent besteht aus einem Array bestehend aus vier Zahlen. Ein Extent beschreibt einen rechteckigen Gültigkeitsbereich. Dabei wird ein Rechteck aufgespannt, 
   das durch die "linke untere" und die "rechte obere" Ecke definiert wird. Das Schema lautet [Hochwert-Links-Unten, Rechtswert-Links-Unten, Hochwert-Rechts-Oben, 
   Rechtswert-Rechts-Oben] oder [minx, miny, maxx, maxy]. Quelle: `Masterportal Docs <https://www.masterportal.org/mkdocs/doc/v3.7.0/User/Portal-Config/config.json.de/#datatypesextent>`__.

-> extent 

.. code-block:: json

{
  "portalConfig": {
    "map": {
      "controls": {
        "zoom": true,
        "orientation": {
          "zoomMode": "once"
        }
      },
      "mapView": {
        "backgroundImage": "./resources/img/backgroundCanvas.jpeg",
        "startCenter": [
          504127.9130919434828684,
          5374562.7627044897526503
        ],
        "extent": [466282.1500000000232831, 5340065.0599999995902181, 546528.7500000000000000, 5400973.9000000003725290],
        "StartZoomLevel": 1,
        "epsg": "EPSG:25832"
      }
    },


.. important::

   Achte auf die Projektion (EPSG), die du benutzt. Welche Projektion ist für dich die Richtige?

**Speichere dein Projekt und schaue dir die Änderungen in deinem Browserfenster an.** 

**Gratulation! Die Karte sollte jetzt angepasst sein**

Quelle - **"portalFooter"**
"""""""""""

Im unteren Bereich deines Geoviewers ist eine Quelle zur Kartographie und Gestaltung angegeben. Im Abschnitt **"portalFooter"** kannst du den URL Link und dessen Benennung ändern. 

.. code-block:: json
   {
    "portalFooter": {
      "urls": [
        {
          "bezeichnung": "common:modules.portalFooter.designation",
          "url": "https://www.geodatenmanagerin-tuebingen.de/termine-anmeldung/",
          "alias": "Geodatenmanager/-in - Universität Tübingen",
          "alias_mobil": "GDM"
        }
      ]
   },

.. figure:: img/qgis-projekt_bbox_extent.PNG
   :alt: QGIS-Projekt mit *Bounding box* oder *Extent* & *Centroid*
   :width: 800px

   QGIS-Projekt mit *Bounding box* oder *Extent* & *Centroid*


Werkzeuge - **"secondaryMenu"**
"""""""""""
 
 sdas


Navigationsfenster - **"mainMenu"**
"""""""""""
 
 sdas


Überblick *config.json*
-----------

.. figure:: img/masterportal_code_geoviewer_connect.jpg
   :alt: Masterportal code und Geoviewer Überblick
   :width: 800px

   Masterportal code und Geoviewer Überblick