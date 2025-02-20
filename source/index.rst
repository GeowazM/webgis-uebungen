.. Geo-Python documentation master file, created by
   sphinx-quickstart on Thu Aug 23 14:00:02 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. image:: img/banner/world-map.png
    :class: dark-light

Willkommen zum Modul WebGIS 🗺🌐
===========================

Informationen finden Sie `hier <https://wissenschaftliche-weiterbildung.info/Veranstaltung/cmx64c779c751049.html>`__  !

Das Modul behandelt die theoretischen Grundlagen zum Aufbau internetgestützter GIS-Plattformen. Dabei werden neben den grundlegenden Systemanforderungen an die Technik auch mögliche Umsetzungen mit 
Open Source- wie auch proprietären Softwarepakete vermittelt. Die Teilnehmenden erarbeiten sich in praktischen Übungen erste Kenntnisse zu Aufbau und Verwaltung eines Web-GIS unter Einbeziehung eigener und fremder Datensätzen.
Das Modul wird im Rahmen der berufsbegleitenden Weiterbildung Geodatenmanager/-in der Universität Tübingen genutzt & weiterentwickelt. 


Lernziele
---------

- Übersicht über verschiedene Web-GIS-Systeme.
- Kenntnisse der möglichen Einsatzbereiche und ihrer Grenzen.
- Kenntnisse spezifischer Systemanforderungen.
- Basiswissen zum Aufbau eines Web-GIS mit entsprechenden OGC (Open Geospatial Consortium) Standards.
- Implementierung eines Web-GIS mit Basisfunktionalität.
- Integration eigener Daten in ein Web-GIS.
- Einbindung von Hintergrundkarten in ein Web-GIS.
- Einführung in die Erstellung einer GDI.

Ablauf und Inhalte der Übungen
-----------------------------------------------------

Ablauf
~~~~~~

-  Die Übungen werden hier bereitgestellt.
-  Die Inhalte der Übungen sollt ihr euch großteils selbständig erarbeiten. In ILIAS findet ihr weitere Informationen, um die Übungsaufgaben zu meistern.
-  Die Vorlesungsfolien und alles weiteren Materialien werden euch über ILIAS bereitgestellt.
-  Bei Fragen wendet euch direkt an mich oder schreibt per Mail (siehe Folien).

Inhalte
~~~~~~~

Anhand der Übungen lernt ihr, **wie** ihr praktisch vorgeht, um ans Ziel zu kommen. Ihr versteht **warum** eure Lösungen funkionieren und erhaltet eine
Übersicht wie **WebMaps & WebGIS-Systeme** funktionieren. Die Übungen sind als praxisorientierte **Hands-On** Sessions gestaltet.

+-------+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Übung | Thema                     | Anwendungen, Tools u.ä.                                                                                                                                         |
+=======+===========================+=================================================================================================================================================================+
| 0     | WebGIS & Geoportale       | `Geoportal Stuttgart <https://maps.stuttgart.de/stadtplan/>`__                                                                                                  |
+-------+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 1     | Erste interaktive Webmaps | `QGIS und qgis2web <https://plugins.qgis.org/plugins/qgis2web/>`__                                                                                              | 
+-------+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2     | HTML,CSS und JavaScript   | `Eine Karte erstellen <https://einfuhrung-gis-fur-geowissenschaften.readthedocs.io/de/latest/lessons/L2/exercise-2.html>`__                                     |
+-------+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 3     | Vulkanismus weltweit      | `Mit Attributtabellen arbeiten <https://einfuhrung-gis-fur-geowissenschaften.readthedocs.io/de/latest/lessons/L3/exercise-3.html>`__                            |
+-------+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

--------------

.. admonition:: Hilfe

    Im Laude der Übungen werden euch typische Probleme von Geodaten und GIS-Software begegnen. Das Auftreten dieser Probleme ist i.d.R. beabsichtig. 
    Lösungen, Herangehensweisen zu diesen Problemen besprechen wir in der Vorlesung und während der gesamten Kurswoche.
    Online Hilfe findet ihr im `ILIAS <https://lms-ubinfo.uni-tuebingen.de/ilias3/ilias.php?baseClass=ilrepositorygui&cmd=render&ref_id=37481>`__ des Geographischen Instituts der Uni Heidelberg und ganz allgemein im Internet.

.. admonition:: Hilfe

    Starte mit dem Kurs indem du im Navigationsfesnter (links) die "Kursinhalte" & den Bereich "Wissenswertes" anschaust.

.. toctree::
    :maxdepth: 2
    :caption: Kursinhalte

    modul-info/info

.. toctree::
    :maxdepth: 2
    :caption: Wissenswertes

    gis-info/was-ist-gis
    gis-info/koordinatensysteme
    gis-info/datenorganisation
    gis-info/hinweise
    gis-info/einstellungen
    gis-info/nutzeroberflaeche
    gis-info/glossar


.. toctree::
    :maxdepth: 2
    :caption: Erste Schritte in QGIS

    lessons/L0/installation
    lessons/L0/exercise-0


.. toctree::
    :maxdepth: 2
    :caption: Das Layerprinzip

    lessons/L1/overview
    lessons/L1/exercise-1-germany
    lessons/L1/exercise-1-tectonicplates
    lessons/L1/exercise-1-tectonicplates_additional

.. toctree::
    :maxdepth: 2
    :caption: Eine Karte erstellen

    lessons/L2/overview
    lessons/L2/exercise-2
    lessons/L2/exercise-2_additional

.. toctree::
    :maxdepth: 2
    :caption: Mit Attributen arbeiten

    lessons/L3/overview
    lessons/L3/exercise-3-vulcanoes
    lessons/L3/exercise-3-vulcanoes_additional

.. toctree::
    :maxdepth: 2
    :caption: Vektorgeometrien verarbeiten

    lessons/L4/exercise-4
    lessons/L4/exercise-4_ahrweiler

.. toctree::
    :maxdepth: 2
    :caption: Geodaten erfassen

    lessons/L5/georeferenzieren
    lessons/L5/exercise-5a_geologie
    lessons/L5/digitalisieren
    lessons/L5/exercise-5b-iceland

.. toctree::
    :maxdepth: 2
    :caption: Rasterdaten verarbeiten

    lessons/L6/overview
    lessons/L6/exercise-6a

.. toctree::
    :maxdepth: 2
    :caption: Digitale Geländemodelle nutzen
    
    lessons/L7/overview
    lessons/L7/exercise-7b
    lessons/L7/exercise-7b_additional

.. toctree::
    :maxdepth: 2
    :caption: Vom Punkt zur Fläche

    lessons/L8/overview
    lessons/L8/exercise-8

.. toctree::
    :maxdepth: 2
    :caption: Prozesse automatisieren

    lessons/L9/overview
    lessons/L9/exercise-9

.. toctree::
    :maxdepth: 2
    :caption: Geodaten

    gis-data/geobasisdaten-bw
    gis-data/basemap-de
    gis-data/download-osm-data
    gis-data/onegeology
