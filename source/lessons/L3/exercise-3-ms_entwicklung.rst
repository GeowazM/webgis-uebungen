==========
Geoviewer konfigurieren
==========

.. hint::

   Ziel der Übung
      * Die Codestruktur des Masterportals kennenlernen 
      * Einen schlanken Geoviewer individuell zu konfigureren

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

.. hint::

   Die *index.html* betrifft ausschließlich den Browsertab. Der Masterportal code ist so aufgebaut, dass das meiste, was innerhalb des Browserfensters passiert, in den *Global-* und *Portal-Settings* definiert ist.

Da wir ohnehin die *index.html* Seite offen haben, können wir direkt den Titel und das Logo des Geoviewers im Browsertab ändern.

1. In der *index.html* kannst du den Titel der Seite ändern 
2. Füge eine Logo (fiktiv oder dein Eigenes) in den Ordner *resources/img/logo.svg* (siehe Bild)
3. Füge die Zeile *<link rel="icon" href="./resources/img/logo.svg">* ein und speichere dein Projekt (Strg+S)
4. Das Logo der Universit Tübingen darf aussschließlich von Mitarbeitern verwendet werden. Nutzt einen Dummy: suche bei Pixabay oder Google Material Icon. 

.. code-block:: html

   <!DOCTYPE html>
   <html lang="de">
      <head>
         <meta charset="utf-8">
         <meta http-equiv="X-UA-Compatible" content="IE=edge">
         <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=0">
         <meta name="apple-mobile-web-app-capable" content="yes">
         <meta name="mobile-web-app-capable" content="yes">

         <title>GDM-Portal</title>                                           <!-- enter your own Portal Title for the website at this -->
         <link rel="stylesheet" href="../mastercode/3_7_0/css/masterportal.css">
         <link rel="stylesheet" href="">                                     <!-- Here you can configure your own fonts as url -->
         <link rel="icon" href="./resources/img/UT-logo.svg">                 <!-- Hier kannst du ein Logo im Browsertab einfügen -->

      </head>
      <body>
         <div id="masterportal-root"></div>
         <script type="text/javascript" src="../mastercode/3_7_0/js/masterportal.js"></script>
      </body>
   </html>

.. figure:: img/masterportal_index_html_title.PNG
   :alt: Angepasster Titel und Logo
   :width: 800px

   Angepasster Titel und Logo

4. Öffne nun die Datei **config.json** (bspw. *uni-tuebingen/config.json*)
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

Geoviewer anpassen
-----------

Jetzt widmen wir uns dem Kern unseres Geoviewers - der Kartenansicht (engl. Map canvas). Dafür müssen wir die geographische Ausdehnung (*Extent*) & 
den zentralen Startpunkt definieren (*Centroid* oder bspw. das *Geoinstitut*). Dafür nutzen wir die Daten aus der Vorbereitung.

1. Öffne die Datei *config.json* (bspw. *uni-tuebingen/config.json*)
2. Navigiere zum unten aufgeführten Code Bereich `portalConfig <https://www.masterportal.org/mkdocs/doc/v3.7.0/User/Portal-Config/config.json/>`__.

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

Jetzt passen wir in der **config.json** Datei die einzelnen Parameter auf unser Untersuchungsgebiet an.

Startpunkt - **"startCenter"**
"""""""""""

Wir starten mit dem `zentralen Startpunkt <https://www.masterportal.org/mkdocs/doc/v3.7.0/User/Portal-Config/config.json.de/#datatypescoordinate>`__.
Dafür nutzen wir die Koordinaten, die wir in QGIS vorbereitet haben.

.. figure:: img/qgis-projekt_bbox_extent.PNG
   :alt: QGIS Layer Eigenschaften
   :width: 800px

   QGIS Layer Eigenschaften mit Extent & EPSG

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


.. code-block:: json

   {
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
        "startZoomLevel": 1
      }
    },


Ausdehnung - **"extent"**
"""""""""""

4. Als nächstes definieren wir den geographischen Rahmen (**Extent** bzw. **Bbox**) unseres Geoviewers


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


.. code-block:: json

   {
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


.. hint::

   Achte auf die Projektion (EPSG), die du benutzt. Welche Projektion ist für dich die Richtige?

**Speichere dein Projekt und schaue dir die Änderungen in deinem Browserfenster an.** 

**Gratulation! Die Karte sollte jetzt angepasst sein**

Werkzeuge - **"secondaryMenu"**
"""""""""""
 
Das **"secondaryMenu"** ist die Toolbox bzw. Werkzeugkiste des Masterportals. Es bezieht sich auf das Navigationsfenster, dass man im rechten Bereich finden kann.

Als erstes wollen wir Werkzeuge löschen, die wir nicht benötigen. Lösche folgenden Codeabschnitt & speichere dein Projekt.

 .. code-block:: json

          {
            "type": "bufferAnalysis"
          },

Durch das Anpassen dieses bereiches kannst du definieren, welche Werkzeuge in deinem Geoviewer zur Verfügung stehen sollen.

Navigationsfenster - **"mainMenu"**
"""""""""""

Lösche im Abschnitt **"sections"** folgendes

 .. code-block:: json

          {
            "type": "openConfig"
          },
         {
            "type": "language"
          }

Speichere deine Datei und sieh dir die Veränderungen im Geoviewer an. Was hat sich geändert?


Überblick *config.json*
-----------

In der folgenden Abbildung kannst du dir einen Überblick verschaffen, welche Code-Abschnitt der *config.json* für welche Bereiche des Geoviewers zuständig sind.

.. figure:: img/masterportal_code_geoviewer_connect.jpg
   :alt: Masterportal code und Geoviewer Überblick
   :width: 800px

   Geoviewer und Masterportal *config.json* kombiniert


Weitere nützliche Werkzeuge (Tools)  *config.json*
-----------


.. caution::

   Einige Werkzeuge funktionieren nur, wenn die Anwendung Online ist. 


Die Kommune und deine Firma tauschen sich über ein Bauprojekt aus. Um eine schnelle, digitale und direkte Übersicht einer Straße & eines Gebäudes zu erhalten wurdest du beauftragt,
den Geoviewer zu erweitern, um einen solchen Austausch zu erleichtern. 


Wir haben im ersten Webinar den Straßenlayer (WFS-Dienst) aus unserem Geonode eingebunden & gestylt. Falls du diesen Straßenlayer noch nicht implementiert hast,
dann füge folgenden Code in deine *services.json* Datei.

.. code-block:: json

  {
    "id": "lgvline",
    "name": "strassen_test",
    "url": "https://prxmx-gdmtesting.rue23.uni-tuebingen.de/geoserver/geonode/strassen_tuebingen/ows",
    "typ": "WFS",
    "featureType": "geonode:strassen_tuebingen",
    "featurePrefix": "",
    "outputFormat" : "image/png",
    "version": "1.1.0",
    "featureNS": "",
    "gfiAttributes": {
      "name": "Name"
    },
    "gfiTheme": "default",
    "layerAttribution":"nicht vorhanden",
	"legendURL":"",
	"hitTolerance":"",
	"datasets":[],
	"urlIsVisible":true
  }


Im Anschluss an das einbinden unseres Straßen-Layers (WFS-Dienstes) haben wir diesen in *style_v3.json* individualisiert.

.. code-block:: json

  {
    "styleId": "1",
    "rules": [
      {
        "style": {
          "lineStrokeColor": [
            255, 0, 0, 0.5
          ],
          "lineStrokeWidth": 10
              }
      }
    ]
  }

Um unseren eingebunden & gestylten Layer im Geoviewer sichtbar zu machen, müssen wir diesen in die *config.json* unter "subjectLayer" > "elements:" einen Verweis einfügen.
Dafür können wir folgenden Code-Snippet nutzen.

.. code-block:: json

        {
          "id": "lgvline",
          "name": "Straßen",
          "styleId": "1",
          "visibility": true,
          "typ": "WFS"
        },


Geoobjekte auswählen & anzoomen
"""""""""""

Als erstes Werkzeug wollen wir eine Auswahlfunktion für Geoobjekte in unseren Geoviewer einbinden. 
Nutze folgenden Code-Schnipsel und teste das Auswahltool am Beispiel der Straßen ("secondaryMenu" > "section").
Wähle die Straßensegmente der Tübinger Neckarbrücke aus! Teste den Button *Auf dieses Feature zoomen*. Was passiert in der Layer-Übersicht?

.. code-block:: json

         {
            "type": "selectFeatures",
            "highlightVectorRulesPolygon": {
                "fill": {
                    "color": [255, 0, 255, 0.9]
                },
                "stroke": {
                    "width": 4,
                    "color": [0, 0, 204, 0.9]
                },
                "zoomLevel": 5
            },
            "highlightVectorRulesPointLine": {
                "fill": {
                    "color": [255, 0, 255, 0.9]
                },
                "stroke": {
                    "width": 8,
                    "color": [255, 0, 255, 0.9]
                },
                "image": {
                    "scale": 2
                },
                "zoomLevel": 5
            }
        }


Ansicht teilen (Share view)
"""""""""""

Wir konnten mit dem Auwahlwerkzeug einzelne Segmente aus unserem WFS-Dienst selektieren. Können wir diese Auwahl auch mit Kolleginnen & Kollegen teilen?
Versuchen wir es. Folgender Code kann in unsere *config.json* in die Werkzeugleiste ("secondaryMenu" > "section") eingebunden werden.

 .. code-block:: json

         {
            "icon": "bi-share",
            "name": "common:modules.shareView.name",
            "type": "shareView",
            "facebookShare": false,
            "qrShare": true
         }


.. caution::

   Funktioniert nur, wenn die Webseite online ist. Im Entwicklungsmodus (VS Code & Live Server) einbindbar, aber nicht testbar. 



Externe WFS-Dienste einbinden
"""""""""""

Jetzt haben wir unseren Straßenlayer eingebunden. Für unseren Auftrag ist es ebenfalls relevant die Gebäude mit zu berücksichtigen. Dafür binden wir in unserem Tübinger
Beispiel den Gebäudelayer des WFS-Dienstes (LGL BW Open Data) ALKIS mit ein. Verwende für ein anderes Untersuchungsgebiet einen passenden WFS-Dienst. Bei der Suche kann das QGIS-Plugin *GeoBasis_Loader* helfen.
Binde folgenden Code ein, verknüpfe diesen in der *config.json* & teste ob er im Geoviewer erscheint.

.. code-block:: json

  {
    "id": "lgvpolygon",
    "name": "gebaeude_test",
    "url": "https://owsproxy.lgl-bw.de/owsproxy/wfs/WFS_LGL-BW_ALKIS",
    "typ": "WFS",
    "featureType": "nora:v_al_gebaeude",
    "featurePrefix": "",
    "outputFormat" : "image/png",
    "version": "1.1.0",
    "featureNS": "",
    "gfiAttributes": "showAll",
    "gfiTheme": "default",
    "layerAttribution":"nicht vorhanden",
	"legendURL":"",
	"hitTolerance":"",
	"datasets":[],
	"urlIsVisible":true
  }

Geoobjekte (Features) erstellen, bearbeiten und/oder löschen
"""""""""""

.. code-block:: json

          {
            "type": "wfst",
            "name": "WFS-T Tool",
            "layerIds": [
              "lgvline",
              "lgvpoint",
              "lgvpolygon"
            ],
            "toggleLayer": false,
            "lineButton": [
              {
                "layerId": "lgvline",
                "available": true
              }
            ],
            "pointButton": [
              {
                "layerId": "lgvpoint",
                "available": true
              }
            ],
            "polygonButton": [
              {
                "layerId": "lgvpolygon",
                "available": true
              }
            ],
            "update": "Bearbeiten!",
            "delete": true
          }


WFS-Dienst filtern
"""""""""""

.. code-block:: json

            {   "type": "WFSSuche",
                "instances": [
                    {
                        "requestConfig": {
                            "layerId": "lgvline"
                        },
                        "selectSource": "https://geoportal-hamburg.de/lgv-config/gemarkungen_hh.json",
                        "literals": [
                            {
                                "clause": {
                                    "type": "and",
                                    "literals": [
                                        {
                                            "field": {
                                                "queryType": "equal",
                                                "fieldName": "gemarkung",
                                                "inputLabel": "Gemarkung",
                                                "options": ""
                                            }
                                        },
                                        {
                                            "field": {
                                                "queryType": "equal",
                                                "fieldName": "flur",
                                                "inputLabel": "Flur",
                                                "options": "flur"
                                            }
                                        }
                                    ]
                                }
                            }
                        ]
                    }
                ]
          },
