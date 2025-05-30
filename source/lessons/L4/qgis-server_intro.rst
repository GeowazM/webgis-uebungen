Open Web Servers
==========

.. hint::

   Ziel der Übung
      * OGC-Dienste kennenlernen 
      * Eigene OGC-Dienste mit QGIS-Server erstellen

.. seealso::

      *  `OGC <https://www.ogc.org/de/>`__
      *  `QGIS Server <https://docs.qgis.org/3.40/en/docs/server_manual/index.html>`__
      *  `OGC-Dienste - Basics <https://docs.qgis.org/3.40/en/docs/server_manual/services/basics.html>`__


Demolink official:

http://qgis.demo/cgi-bin/qgis_mapserv.fcgi?MAP=/home/qgis/projects/world.qgs&LAYERS=countries&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetMap&CRS=EPSG:4326&WIDTH=400&HEIGHT=200&BBOX=-90,-180,90,180



Hintergrund
--------

QGIS Server ist eine Open-Source-Implementierung von WMS, WFS, OGC API for Features 1.0 (WFS3) und WCS, die zusätzlich erweiterte kartografische Funktionen für 
thematische Karten bietet. QGIS Server ist eine FastCGI/CGI (Common Gateway Interface) Anwendung, die in C++ geschrieben ist und zusammen mit einem Webserver 
(z.B. Apache, Nginx) arbeitet. Es unterstützt Python-Plugins, die eine schnelle und effiziente Entwicklung und Bereitstellung neuer Funktionen ermöglichen.
QGIS Server verwendet QGIS als Backend für die GIS-Logik und die Kartendarstellung. Darüber hinaus wird die Qt-Bibliothek für Grafiken und plattformunabhängige 
C++-Programmierung verwendet. Im Gegensatz zu anderer WMS-Software verwendet der QGIS Server kartografische Regeln als Konfigurationssprache, sowohl für die 
Serverkonfiguration als auch für die benutzerdefinierten kartografischen Regeln. Da QGIS Desktop und QGIS Server dieselben Visualisierungsbibliotheken verwenden, 
sehen die im Web veröffentlichten Karten genauso aus wie im Desktop-GIS. In den folgenden Abschnitten stellen wir eine Beispielkonfiguration zur Einrichtung eines
QGIS Servers unter Linux (Debian, Ubuntu und Derivate) und unter Windows bereit. Für weitere Informationen zur Entwicklung von Server-Plugins lesen Sie bitte 
QGIS Server und Python.

.. hint::

   Die bekanntesten **räumlichen Open Web Services (OWS)** sind **GeoServer, MapServer & QGIS Server**.

.. hint::

   `MapProxy <https://www.mapproxy.org/>`__ - coming soon

Der grundlegende Funktion eines räumlichen Webservers (unabhängig von der Software) funktioniert ähnlich. Hier eine Übersicht am Beispiel von GeoServer:

.. figure:: https://techtalk.intersec.com/2021/10/open-source-map-server-with-geoserver-and-qgis/schema-gis.png
   :alt: Open-source map server with Geoserver and QGIS

   Quelle: `intersec TeckTalk <https://techtalk.intersec.com/2021/10/open-source-map-server-with-geoserver-and-qgis/>`__

.. admonition:: 2019 - Vergleich QGIS-Server, Geoserver und MapServer
    :class: admonition-youtube

    ..  youtube:: IWloWZJ87lA&t=102s

    WhereGroup - `FOSSGIS on Youtube <https://www.youtube.com/watch?v=IWloWZJ87lA&t=102s>`_.
   

.. admonition:: FOSSGIS 2024 QGIS Server - Einsatz im Unternehmen
    :class: admonition-youtube

    ..  youtube:: Bl5-ubTBOZY

    `FOSSGIS on Youtube <https://www.youtube.com/watch?v=Bl5-ubTBOZY>`_.