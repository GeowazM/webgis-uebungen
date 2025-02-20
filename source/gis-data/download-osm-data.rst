OSM Daten herunterladen
=======================

OpenStreetMap ist streng genommen eine Geodatenbank, keine Karte. D.h.
die Karte die ihr unter https://www.openstreetmap.org seht, ist nur eine
Darstellung der Punkt-, Linien- und Flächenobjekte die in der Datenbank
gespeichert sind.

Es gibt verschiedene Wege Daten aus OSM herunterzuladen. Hier werden
euch Overpass und seine Anwendungsmodule wie z.B. QuickOSM (das QGIS
Plugin für Overpass Turbo) vorgestellt.

Overpass ist eine API, die Anfragen für Daten aus OSM annimmt und diese
Daten ausgibt.

overpass turbo
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
