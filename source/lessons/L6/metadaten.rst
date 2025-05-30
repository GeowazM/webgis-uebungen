Metadatenformate für Geodaten
========

.. hint::

   Metadaten sind strukturierte Informationen, die Geodaten oder Geodatendienste beschreiben und auffindbar sowie nutzbar machen. 
   Im WebGIS-Kontext sind standardisierte Metadatenformate unerlässlich, um Interoperabilität, Austausch und effiziente Suche zu gewährleisten [9].

.. hint::

      Es gibt fünf Haupttypen von Ressourcen, die GeoNode verwalten kann:

      - Datensätze
      - Karten
      - Dokumente
      - GeoStories
      - Dashboards

      Jeder Ressourcentyp hat sein eigenes Menü und kann über die Schaltflächen Datensätze, Karten, Dokumente, GeoStories und Dashboards in der Navigationsleiste erreicht werden.



Dublin Core
-----------

Dublin Core ist ein international etablierter, einfach gehaltener Standard zur Beschreibung von digitalen Ressourcen, ursprünglich für Dokumente im Internet entwickelt, aber auch für Geodaten nutzbar [10]_, [11]_, [12]_. Er wurde 1994 von der Dublin Core Metadata Initiative (DCMI) ins Leben gerufen.

- *Simple Dublin Core* umfasst 15 Kernelemente wie Titel, Ersteller, Betreff, Beschreibung, Herausgeber, Sprache, Rechte usw. [8], [11].
- *Qualified Dublin Core* erweitert diese um zusätzliche Elemente und Verfeinerungen, z.B. für genauere Zeitangaben oder Beziehungen zwischen Ressourcen [8], [13]. Für Geodaten wurden im Laufe der Zeit Erweiterungen eingeführt, z.B. für die Beschreibung der räumlichen Ausdehnung [6]_.
- **Vorteile:** Einfachheit, breite Unterstützung (z.B. Pflichtformat für OGC-Katalogdienste wie CSW), gute Interoperabilität.
- **Einschränkung:** Für komplexe Geodatenprojekte oft nicht detailliert genug.

ISO 19115
---------

ISO 19115 ist der internationale Standard für die Beschreibung von Geoinformationen und Geodatendiensten [5]. Er ist deutlich umfangreicher und spezifischer als Dublin Core.

- Definiert über 400 Metadatenelemente, z.B. zu Inhalt, räumlich-zeitlichen Bezügen, Datenqualität, Zugangsmöglichkeiten und Nutzungsrechten.
- Ein verpflichtender Kerndatensatz mit etwa 20 Elementen deckt die Minimalanforderungen ab [5].
- Grundlage für viele nationale und internationale Geodateninfrastrukturen (GDI), z.B. GDI-DE, GDI-NI.
- ISO 19139 Standard ist dar ISE 19115 Standard als XML Datei

INSPIRE-Metadatenprofil
-----------------------

INSPIRE ist eine EU-Richtlinie zur Schaffung einer europäischen Geodateninfrastruktur. Sie definiert ein Metadatenprofil, das auf ISO 19115 basiert und für Geodatensätze und -dienste verpflichtende, bedingt verpflichtende und optionale Elemente vorgibt [7]_.

- Viele nationale Profile (z.B. GDI-DE, GDI-NI) basieren auf INSPIRE und ISO 19115.
- INSPIRE legt Wert auf Interoperabilität und harmonisierte Metadaten für den europäischen Austausch.

FGDC CSDGM
----------

FGDC Content Standard for Digital Geospatial Metadata (CSDGM) ist der US-amerikanische Standard für Geodatenmetadaten, entwickelt vom Federal Geographic Data Committee [8]_.

- Enthält 334 Metadatenelemente.
- Wird in den USA zunehmend durch das North American Profile (basierend auf ISO 19115) abgelöst.

Weitere Formate
---------------

- **ArcGIS-Metadaten:** Proprietäres Format von Esri, kompatibel mit internationalen Standards, aber für ArcGIS-Produkte optimiert [8]_.
- **DCMI Metadata Terms:** Erweiterung von Dublin Core für granularere Beschreibungen, insbesondere durch sogenannte "Refinements" und Properties [13]_.

Übersicht der wichtigsten Metadatenformate
------------------------------------------

+---------------------+----------------------------------------------+--------------------------+
| Format/Standard     | Fokus/Besonderheit                           | Typische Anwendung       |
+=====================+==============================================+==========================+
| Dublin Core         | Einfach, 15 Kernelemente, erweiterbar        | Web, OGC-Katalogdienste  |
+---------------------+----------------------------------------------+--------------------------+
| ISO 19115           | Sehr detailliert, internationaler Standard   | Geodateninfrastrukturen  |
+---------------------+----------------------------------------------+--------------------------+
| INSPIRE             | EU-weit, basiert auf ISO 19115               | Europäische GDI          |
+---------------------+----------------------------------------------+--------------------------+
| FGDC CSDGM          | US-Standard, sehr umfassend                  | US-Behörden, Altbestand  |
+---------------------+----------------------------------------------+--------------------------+
| ArcGIS-Metadaten    | Software-spezifisch, ISO-kompatibel          | ArcGIS-Umgebung          |
+---------------------+----------------------------------------------+--------------------------+
| DCMI Metadata Terms | Erweiterung von Dublin Core                  | Wissenschaft, Web        |
+---------------------+----------------------------------------------+--------------------------+

Zusammenfassung
-----

Für den WebGIS-Kontext ist Dublin Core wegen seiner Einfachheit und Interoperabilität beliebt, reicht aber für komplexe Geodatenprojekte oft nicht aus. ISO 19115 und darauf basierende Profile wie INSPIRE sind für professionelle Geodateninfrastrukturen Standard. In der Praxis werden oft mehrere Formate parallel unterstützt, um sowohl einfache als auch detaillierte Metadatenbedürfnisse abzudecken [6]_, [8]_, [9]_.

Mehr Informationen gibt’s beim Arbeitskreis Metadaten des GDI-DE:  
https://www.gdi.nrw/system/files/media/document/file/architektur_gdi_de_konventionen_metadaten_v2_3_0.pdf



Quellen
-------

.. [5] https://de.wikipedia.org/wiki/ISO_19115
.. [6] https://gispoint.de/fileadmin/user_upload/paper_gis_open/537508080.pdf
.. [7] https://www.geosn.sachsen.de/redmine/projects/metadaten/wiki/Metadatenelemente_nach_INSPIRE-Festlegungen_Dienst
.. [8] https://enterprise.arcgis.com/de/inspire/10.5/get-started/standards-support.htm
.. [9] https://gdi.bmel.de/metadaten
.. [10] https://de.ryte.com/wiki/Dublin_Core
.. [11] https://www.forschungsdaten.org/index.php/Dublin_Core
.. [12] https://wiki.selfhtml.org/wiki/Websemantics/Dublin_Core
.. [13] https://wiki.dnb.de/download/attachments/272237368/Einf%C3%BChrung_in_Metadaten_und_Metadatenformate_final.pdf?api=v2
