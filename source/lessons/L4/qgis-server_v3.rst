WMS publizieren
==========

.. hint::

   Ziel der Übung
      * OGC-Dienst veröffentlichen 
      * Eigene OGC-Dienste mit QGIS-Server publizieren
      * Mit FileZilla Daten kopieren

.. seealso::

      *  `OGC <https://www.ogc.org/de/>`__
      *  `QGIS Server <https://docs.qgis.org/3.40/en/docs/server_manual/index.html>`__
      *  `OGC-Dienste - Basics <https://docs.qgis.org/3.40/en/docs/server_manual/services/basics.html>`__
      *  `FileZilla <https://filezilla-project.org/>`__



More Information
--------



2.4.5. Fine tuning your OWS
For vector layers, the Fields tab of the Layer ► Layer Properties dialog allows you to define for each attribute if it will be published or not. By default, all the attributes are published by your WMS and WFS. If you don’t want a specific attribute to be published, uncheck the appropriate checkbox in the Configuration column:

Do not expose in WFS

Do not expose in WMS

You can overlay watermarks over the maps produced by your WMS by adding text annotations or SVG annotations to the project file. See the Annotation Tools section for instructions on creating annotations. For annotations to be displayed as watermarks on the WMS output, the Fixed map position checkbox in the Annotation text dialog must be unchecked. This can be accessed by double clicking the annotation while one of the annotation tools is active. For SVG annotations, you will need either to set the project to save absolute paths (in the General menu of the Project ► Properties… dialog) or to manually modify the path to the SVG image so that it represents a valid relative path.

2.5. Integration with third parties
QGIS Server provides standard OGC web services like WMS, WFS, etc. thus it can be used by a wide variety of end user tools.

2.5.1. Integration with QGIS Desktop
QGIS Desktop is the map designer where QGIS Server is the map server. The maps or QGIS projects will be served by the QGIS Server to provide OGC standards. These QGIS projects can either be files or entries in a database (by using Project ► Save to ► PostgreSQL in QGIS Desktop).

Furthermore, dedicated update workflow must be established to refresh a project used by a QGIS Server (ie. copy project files into server location and restart QGIS Server). For now, automated processes (as server reloading over message queue service) are not implemented yet.

2.5.2. Integration with MapProxy
MapProxy is a tile cache server and as it can read and serve any WMS/WMTS map server, it can be directly connected to QGIS server web services and improve end user experience.

2.5.3. Integration with QWC2
QWC2 is a responsive web application dedicated to QGIS Server. It helps you to build a highly customized map viewer with layer selection, feature info, etc.. Also many plugins are available like authentication or print service, the full list is available in this repository.