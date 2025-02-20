OGC-Standards
=======================

**OGC (Open Geospatial Consortium) Web Services (OWS)** bezieht sich auf eine Reihe von Standards und Protokollen, die entwickelt wurden, um die Interoperabilität und 
den Austausch von Geodaten und Geodaten-Dienste über das Internet zu ermöglichen.

Ein wichtiger Bestandteil davon ist das OGC Web Services Context Document (OWS Context). Dieses Dokument wurde erstellt, um eine Sammlung von konfigurierten Informationsressourcen (Service-Set) 
zwischen Anwendungen als eine Sammlung von Diensten zu übermitteln12. Es unterstützt verschiedene Webdienste wie 
- Web Feature Service (WFS) 
- Web Map Service (WMS)
- Web Map Tile Service (WMTS)
- Web Coverage Service (WCS)

Enthält KI generierte Inhalte; Quelle: `OGC Web Services Context Document (OWS Context) <https://www.ogc.org/de/publications/standard/owc/>`__


Hintergrund
------------
Die OGC-Standards (Open Geospatial Consortium) entstanden aus dem Bedarf, Geodaten und Geodaten-Dienste eine einheitliche und interoperable Plattform zu bieten. 
Hier sind einige wichtige Schritte in der Entwicklung dieser Standards

1. Gründung des OGC: Das Open Geospatial Consortium wurde 1994 gegründet, um die Interoperabilität von Geodaten und Geodaten-Dienste zu fördern.
2. Entwicklung erster Standards: In den frühen Jahren konzentrierte sich das OGC auf die Entwicklung von Standards für Webdienste wie den Web Map Service (WMS) und 
den Web Feature Service (WFS), die es ermöglichten, Karten und geospatiale Daten über das Internet auszutauschen.
3. Erweiterung der Standards: Mit der Zeit wurden weitere Standards entwickelt, um verschiedene Aspekte der Geodatenverarbeitung abzudecken, darunter 
der Web Coverage Service (WCS) und der Web Processing Service (WPS).
4. Einführung moderner APIs: In den letzten Jahren hat das OGC begonnen, moderne Web-APIs zu entwickeln, die auf den bestehenden Webdienststandards aufbauen, aber 
ressourcenzentrierte Ansätze und moderne Webentwicklungstechniken nutzen.

Diese Standards haben die Zusammenarbeit und den Austausch von Geodaten weltweit erheblich erleichtert und Innovationen in verschiedenen Branchen gefördert.

Enthält KI generierte Inhalte; Quelle: `OGC Web Services Context Document (OWS Context) <https://www.ogc.org/de/publications/standard/owc/>`__





Under Construction
--------------

`overpass turbo <https://overpass-turbo.eu/>`__ ist eine Webseite mit
der man Anfragen (queries) an die Overpass API senden kann.

Mithilfe der Kartenansicht wählt man den Bereich aus für den Geodaten
abgerufen werden sollen. Man kann hier auch eine Bounding-Box manuell
selektieren (1) oder Koordinaten einer BBox in der Anfrage angeben (2).
Man kann die gesamte Anfrage selbst in QL schreiben, oder aber den
Wizard (3) nutzen, der den query dann erstellt.

.. figure:: https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/OSM/overpass-turbo.png
   :alt: overpass-turbo.png

   overpass-turbo.png

Anfragen stellen
~~~~~~~~~~~~~~~~

Ihr gebt in einer Anfrage bestimmte Tags an und Overpass gibt euch alle
Objekte in dem gewählten Ausschnitt, die mindestens einen dieser Tags
haben, zurück.

Anfragen an Overpass können aus einem einzigen Argument bestehen (z.B.
``"building"="clinic"``) oder mehreren Argumenten (z.B.
``"building"="clinic"`` ``"building"="hospital"`` und
``"amenity"="hospital"``). Mehrere Argumente anzugeben ist
empfehlenswert, da möglicherweise nicht alle Objekte die ihr sucht, auf
die gleiche Weise getagged sind.

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/OSM/videos/use-turbo.mp4">

.. raw:: html

   </video>

Die zurückgegebenen Objekte werden euch in der Kartenansicht interaktiv
dargestellt. Um mit den Daten weiterarbeiten zu können, z.B. in QGIS,
könnt ihr sie über die Export-Funktion in verschiedenen Formaten
herunterladen. In den meisten Fällen lässt es sich in QGIS am
einfachsten mit GeoJSON arbeiten.

Und wie lade ich jetzt **nur die von mir gemappten Objekte** herunter?

.. raw:: html

   <details>

.. raw:: html

   <summary>

Hier versteckt sich eine Anleitung

.. raw:: html

   </summary>

Daten eines bestimmten Nutzers anfragen
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Um nur die Daten eines bestimmten Nutzers herunterzuladen, kann man
entweder das Argument ``user:"<euer Nutzername>"`` oder das Argument
``uid:<eure Nutzer ID>`` zu einer Anfrage hinzufügen.

Wenn man einfach alle von diesem User gemappten Objekte innherhalb der
bbox haben will, fügt man sonst keine Argumente hinzu:

::

   [out:json][timeout:25];
   // gather results
   (
     node(uid:<die ID des Nutzer>)({{bbox}});
     way(uid:<die ID des Nutzer>)({{bbox}});
     relation(uid:<die ID des Nutzer>)({{bbox}});
   );
   // print results
   out body;
   >;
   out skel qt;

Wenn man aber nur z.B. alle von diesem User gemappten Straßen haben
möchte, hängt man das ``user`` oder ``uid`` Argument einfach hinten an
die Anfrage für highways dran:

::

   [out:json][timeout:25];
   // gather results
   (
     // query part for: “highway=*”
     node["highway"](user:"<Nutzername>")({{bbox}});
     way["highway"](user:"<Nutzername>")({{bbox}});
     relation["highway"](user:"<Nutzername>")({{bbox}});
   );
   // print results
   out body;
   >;
   out skel qt;

Mehr dazu könnt ihr auch unter
https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL#By_user_(user,_uid)
oder https://wiki.openstreetmap.org/wiki/Overpass_API#User lesen.

.. raw:: html

   </details>

QuickOSM
--------

QuickOSM ist ein Plugin für QGIS mit der man Anfragen (queries) an die
Overpass API senden kann.

Ihr installiert QuickOSM wie gewohnt über Erweiterungen > Erweiterungen
verwalten und installieren…

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/OSM/videos/install-quickosm.mp4">

.. raw:: html

   </video>

.. _anfragen-stellen-1:

Anfragen stellen
~~~~~~~~~~~~~~~~

Für QuickOSM gelten die gleichen Anfrage-Prinzipien wie für overpass
turbo.

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/OSM/videos/use-quickosm.mp4">

.. raw:: html

   </video>

Die zurückgegebenen Daten sind Vektorobjekte, die direkt in QGIS
angezeigt werden. Diese neuen Layer sind erst mal nur temporär und
müssen per Rechtsklick auf das Layer > Export > Objekte speichern als…
auf eurem Computer gespeichert werden, wenn ihr Sie über die offene
Sitzung hinaus behalten wollt.
