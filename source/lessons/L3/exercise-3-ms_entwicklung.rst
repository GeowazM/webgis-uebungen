Übung 3 - Konfiguration
==========

.. hint::

   Ziel der Übung
      * Erste Einblicke in *Visual Studio Code* 
      * Die Extension *Live Server* kennenlernen

.. figure:: img/vs_code.PNG
   :alt: Visual Studio Code
   :width: 800px

   `Visual Studio Code <https://code.visualstudio.com/>`__
 

.. seealso::

      *  `Visual Studio Code <https://code.visualstudio.com/>`__
      *  `Live Server <https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer>`__
      *  `Masterportal Docs) <https://www.masterportal.org/mkdocs/doc/v3.7.0/User/About/>`__


Masterportal konfigurieren
===========
Jetzt haben wir alle Vorbereitungen getroffen und können mit der Entwicklung bzw. Konfiguration unseres Masterportal-WebGIS starten.
Ein zentrales Dokument, dass wir für die Konfiguration brauchen ist `die offizielle Dokumentation (Masterportal Docs) <https://www.masterportal.org/mkdocs/doc/v3.7.0/User/About/>`__
Das Masterportal example befindet sich in Hamburg. Die dort eingesetzten Parameter ändern wir jetzt Schritt für Schritt, um aus dem Beispiel unser eigenes WebGIS zu konfigurieren.

Titel & Logo ändern
-----------

Da wir ohnehin die *index.html* Seite offen haben, können wir direkt den Titel und das Logo des WebGIS im Browsertab ändern.

.. seealso:: attention

   Die *index.html* betrifft ausschließlich den Browsertab. Der Masterportal code ist so aufgebaut, dass alles, was innerhalb des Browserfensters passiert, in den *Global-* und *Portal-Settings* definiert ist.

1. In der *index.html* kannst du den Titel der Seite ändern 
2. Füge eine Logo (fiktiv oder dein Eigenes) in den Ordner *resources/img/UT-logo.svg* (siehe Bild)
3. Füge die Zeile *<link rel="icon" href="./resources/img/UT-logo.svg">* ein und speichere dein Projekt (Strg + S)
4. Öffne die Datei *config.json* (bspw. *uni-tuebingen/config.json*)
5. Navigiere zum Abschnitt *portalFooter*
   - Ändere den URL zu einer Website deiner Wahl
   - Passe den Alias & den mobilen Alias an

    "portalFooter": {
      "urls": [
        {
          "bezeichnung": "common:modules.portalFooter.designation",
          "url": "https://www.geodatenmanagerin-tuebingen.de/termine-anmeldung/",
          "alias": "Geodatenmanager/-in - Uni Tübingen",
          "alias_mobil": "GDM"
        }
      ]
    },

.. figure:: img/masterportal_index_html_title.PNG
   :alt: Visual Studio Code
   :width: 800px

   Angepasster WebGIS Titel und Logo

Kartenviewer (Map canvas) anpassen
-----------

Jetzt widmen wir uns dem Kern unseres WebGIS-Portals - dem Kartenview. Dafür müssen wir die geographische Ausdehnung (*Extent*) & 
den zentralen Startpunkt definieren (*Centroid* oder *Geoinstitut*) bzw. den  festlegen. Dafür nutzen wir die Daten aus der Vorbereitung.

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
        "extent": [507866.7398613950936124, 500835.9344349517486989, 5370755.4711730508133769, 5376982.2454833826050162],
        "StartResolution": 9028,
        "StartZoomLevel": 1,
        "epsg": "EPSG:25832"
      }
    },


1. Öffne die Datei *config.json* (bspw. *uni-tuebingen/config.json*)
1. Den zentralen Startpunkt festlegen
    - Navigiere zum Abschnitt *startCenter*

.. code-block:: json

   {
      "key": "value",
      "key2": "value2",
      ...
   }

2. Die maximale geographische Ausdehnung unseres WebGIS



2. Öffne QGIS
3. Selektiere eine Gemeinde, Landkreis oder Region deiner Wahl & exportiere dir das Feature (bspw. Tübingen)
4. Berechne die *Bounding box* deiner Region
5. Lass dir den *Centroid* der berechneten *Bounding box* ausgeben.
6. Notiere dir die Koordinaten der Bounding box & des Centroid
7. Lade dir drei WMS-Layer für deine Region -> bspw.: 1x Schummerung, 1x Orthophoto, 1x basemap.de
8. Speichere dein Projekt & lasse dein QGIS-Projekt geöffnet

.. figure:: img/masterportal_folder_order.PNG
   :alt: QGIS-Projekt mit *Bounding box* oder *Extent* & *Centroid*
   :width: 800px

   QGIS-Projekt mit *Bounding box* oder *Extent* & *Centroid*


Navigation (side bar) individualisieren
-----------
 1. sdas


