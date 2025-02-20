Koordinatenbezugssysteme (KBS)
==================

Schlagworte: Koordinatenbezugssystem (KBS), Projektion, On-the-fly Projektion, Latitude, Longitude, Northing, Easting

.. admonition:: Warum alle Weltkarten falsch sind | Terra X plus
    :class: admonition-youtube

    ..  youtube:: NAi3v33fVww

    `Terra X plus on Youtube <https://www.youtube.com/watch?v=NAi3v33fVww>`_.

Übersicht
========

**Map projections** try to portray the surface of the earth, or a portion of the earth, on a flat piece of paper or computer screen. In layman's term, map projections
try to transform the earth from its spherical shape (3D) to a planar shape (2D).

A **coordinate reference system** (CRS) then defines how the two-dimensional, projected map in your GIS relates to real places on the earth. 
The decision of which map projection and CRS to use depends on the regional extent of the area you want to work in, on the analysis you want to do, and often on the availability of data.

Kartenprojektion im Detail
========================

Eine traditionelle Methode zur Darstellung der Erdform ist die Nutzung von Globen. Dennoch gibt es ein Problem mit dieser Methode. 
Obwohl Globen den größten Teil der Erdform widerspiegeln und die räumliche Struktur der kontinent-großen Bestandteile darstellen, lassen sie sich nur sehr schwierig in der Tasche tragen. 
Außerdem sind sie nur für sehr kleine Maßstäbe (z.B. 1:100 Millionen) geeignet.

Die meisten thematischen Kartendaten, die in GIS-Anwendungen verwendet werden, haben bedeutend größere Maßstäbe. Typische GIS-Datensätze besitzen Maßstäbe von 1:250.000 oder größer, je nach Detailgrad. 
Ein Globus dieser Größe wäre sehr schwierig und teuer zu produzieren und noch schwieriger zu transportieren. Deshalb haben Kartografen eine Reihe von Techniken entwickelt namens Kartenprojektionen, 
die - mit angemesserer Genauigkeit - die kugelförmige Erde in zwei Dimensionen darstellen.

Von nahem betrachtet wirkt die Erde relativ flach. Aber vom Weltall aus sieht man, dass die Erde relativ kugelförmig ist. Wie wir im nächsten Thema Kartenherstellung sehen werden, 
sind Karten eine Widerspiegelung der Realität. Sie werden nicht nur entworfen, um Eigenschaften darzustellen, sondern auch Gestalt und räumliche Anordnung. Jede Kartenprojektion hat Vorteile und Nachteile. 
Die beste Kartenprojektion ist abhängig vom Maßstab der Karte und vom Verwendungszweck. Zum Beispiel könnte eine Karte inakzeptable Verzerrungen aufweisen, 
wenn sie für die Darstellung des gesamten afrikanischen Kontinents genutzt wird, könnte aber eine exzellente Wahl sein für eine großmaßstäbliche (detailiierte) Karte Ihres Landes. 
Die Eigenschaften einer Kartenprojektion können auch einige Konstruktionsmerkmale der Karte beeinflussen. Einige Projektionen sind geeignet für kleine Flächen, 
während andere ideal sind für Kartiergebiete mit großer Ost-West-Ausdehnung oder wieder andere für Kartiergebiete mit großer Nord-Süd-Erstreckung.

Die drei Familien der Kartenprojektionen
=====================================

The process of creating map projections is best illustrated by positioning a light source inside a transparent globe on which opaque earth features are placed. Then
project the feature outlines onto a two-dimensional flat piece of paper. Different ways of projecting can be produced by surrounding the globe in a
**cylindrical** fashion, as a **cone**, or even as a **flat surface**. Each of these methods produces what is called a **map projection family**. Therefore,
there is a family of **planar projections**, a family of **cylindrical projections**, and another called **conical projections**.

.. _figure_projection_families:

.. figure:: https://docs.qgis.org/3.34/de/_images/projection_families.png
   :align: center
   :width: 30em

   Die drei Kategorien von Kartenprojektionen. a) Zylinderprojektion, b) Kegelprojektion und c) Azimuthalprojektion.

Natürlich wird heutzutage der Prozess, die Erdkugel auf ein flaches Blatt Papier zu projizieren, unter Zuhilfenahme mathematischer Prinzipien aus der Geometrie und Trigonometrie durchgeführt. 
Dies stellt die physische Projektion von Lichtstrahlen durch den Globus nach.

.. admonition:: GIS Koordinatensysteme - Einführung
    :class: admonition-youtube

    ..  youtube:: kGt0tgkPZwE

    `Marshall Mappers on Youtube <https://youtu.be/kGt0tgkPZwE?si=VjSO40_wuNdVn7Ll>`_.





****************************
Mit Koordinatenbezugssystemen arbeiten
****************************

Jeder Layer sollte ein Koordinatensystem besitzen, d.h. jeder Geodatensatz befindet ich in einem definiertem Koordinatensystem. In
QGIS werden alle Layer eines Projektes in der Kartenansicht im selben Koordinatensystem dargestellt.

Dieses Projekt Koordinatensystem kann unabhängig vom Koordinatensystem der Layer gewählt werden. Falls das Projekt-Koordinatensystem und das
Koordinatensystem der Layer nicht übereinstimmen, werden die Layer on-the-fly umprojiziert. Diese on-the-fly Umprojektion verändert aber
nicht permanent das Koordinatensystem des Datensatzes, sondern nur kurzfristig seine **Darstellung** und ggfs. die Ergebnisse von Längen-,
Fläche- und Winkelberechnungen. Bei der Arbeit in QGIS ist es zu empfehlen die Layer und die darin enthaltenen Daten langfristig umzuprojizieren.

Zur Kommunikation von Koordinatensysteme existieren zwei Formate: PROJ (auch ein Softwareprogramm) & WKT (auch WKT-CRS genannt). Beide sind
durch das OGC anerkannt und alle gängigen Kartographie und GIS Softwares können damit umgehen. 

Beispiel **EPSG:4326**

.. raw:: html

   <details>

.. raw:: html

   <summary>

WKT

.. raw:: html

   </summary>

::

   GEOGCS["WGS 84",
       DATUM["WGS_1984",
           SPHEROID["WGS 84",6378137,298.257223563,
               AUTHORITY["EPSG","7030"]],
           AUTHORITY["EPSG","6326"]],
       PRIMEM["Greenwich",0,
           AUTHORITY["EPSG","8901"]],
       UNIT["degree",0.0174532925199433,
           AUTHORITY["EPSG","9122"]],
       AUTHORITY["EPSG","4326"]]

.. raw:: html

   </details>

.. raw:: html

   <details>

.. raw:: html

   <summary>

PROJ

.. raw:: html

   </summary>

::

   +proj=longlat +datum=WGS84 +no_defs +type=crs

.. raw:: html

   </details>

Beispiel **EPSG:32634**

.. raw:: html

   <details>

.. raw:: html

   <summary>

WKT

.. raw:: html

   </summary>

::

   PROJCS["WGS 84 / UTM zone 34N",
       GEOGCS["WGS 84",
           DATUM["WGS_1984",
               SPHEROID["WGS 84",6378137,298.257223563,
                   AUTHORITY["EPSG","7030"]],
               AUTHORITY["EPSG","6326"]],
           PRIMEM["Greenwich",0,
               AUTHORITY["EPSG","8901"]],
           UNIT["degree",0.0174532925199433,
               AUTHORITY["EPSG","9122"]],
           AUTHORITY["EPSG","4326"]],
       PROJECTION["Transverse_Mercator"],
       PARAMETER["latitude_of_origin",0],
       PARAMETER["central_meridian",21],
       PARAMETER["scale_factor",0.9996],
       PARAMETER["false_easting",500000],
       PARAMETER["false_northing",0],
       UNIT["metre",1,
           AUTHORITY["EPSG","9001"]],
       AXIS["Easting",EAST],
       AXIS["Northing",NORTH],
       AUTHORITY["EPSG","32634"]]

.. raw:: html

   </details>

.. raw:: html

   <details>

.. raw:: html

   <summary>

PROJ

.. raw:: html

   </summary>

::

   +proj=utm +zone=34 +datum=WGS84 +units=m +no_defs +type=crs

.. raw:: html

   </details>

Projektkoordinatensystem
------------------------

Ändern des Projektkoordinatensystem
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/kartographie_uebung/-/wikis/uploads/videos/changeProjectProjection.mp4">

.. raw:: html

   </video>

Benutzerdefinierte Projektion
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Man kann auch eigene Koordinatensysteme definieren. I.d.R. auf Basis existierender Koordinatensysteme, deren Parameter (z.B. Schnittpunkte
oder Schnittkreise so wählen, dass die darzustellende Region möglichst wenig verzerrt wird).

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/kartographie_uebung/-/wikis/uploads/videos/customProjection.mp4">

.. raw:: html

   </video>

Layerkoordinatensystem
----------------------

Welches Koordinatensystem ist im Layer definiert?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Über die Layer Metadaten können sie dessen Koordinatensystem überprüfen.

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/kartographie_uebung/-/wikis/uploads/videos/kbs-metadaten.mp4">

.. raw:: html

   </video>

Koordinatensystem eines Layers ändern
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Vektordaten
^^^^^^^^^^^

Liegen die Daten im Vektorformat vor (Punkte, Linien, Polygone), dann kann man ihr Koordinatensystem über ``Vektor`` > ``Datenmanagement-Werkzeuge`` > ``Layer umprojizieren`` verändern.

Die Daten werden mit diesem Werkzeug umprojiziert und es wird ein neues Layer mit den veränderten Daten ausgegeben.

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/kartographie_uebung/-/wikis/uploads/videos/kbs-vektor.mp4">

.. raw:: html

   </video>

Rasterdaten
^^^^^^^^^^^

Liegen die Daten im Rasterdatenformat vor, dann kann man ihr Koordinatensystem über ``Raster`` > ``Projektionen`` > ``Transformieren (Reprojizieren)`` verändern.

Projection Wizard
=================

Um ein passendes Koordinatensystem für einen bestimmten Anwendungszweck und Ausschnitt der Erde zu finden, gibt es den *Projection Wizard* unter `projectionwizard.org <https://projectionwizard.org/>`__.

Auf dieser Webseite könnt ihr den Ausschnitt in dem sich eure Karte befindet auswählen und unter *Distortion Property* festlegen ob die
Projektion flächentreu (equal-area), winkeltreu (conformal), längentreu (equidistant) oder ein Kompromiss aus allen drei (compromise) sein soll.

.. figure:: https://courses.gistools.geog.uni-heidelberg.de/giscience/kartographie_uebung/-/wikis/uploads/img/projwiz-distortion.png
   :alt: projwiz-distortion.png

   projwiz-distortion.png

Die Webseite gibt euch dann Vorschläge, welches Koordinatensystem euren Anforderungen am besten entspricht und bietet sie sowohl im PROJ und WKT Format an.

Der Projection Wizard liefert die besten Ergebnisse für große Maßstäbe und Karten über Ländergrenzen hinweg. Für kleinere Maßstäbe bietet es
sich an, das offizielle Koordinatensystem des jeweiligen Staats zu benutzen.

Literatur zu Koordinaten, Projektionen und Koordinatenbezugssysteme
=================

Quellen
   * De Lange, N. (2020): `Geoinformatik in Theorie und Praxis. 4. Auflage. DOI: https://doi.org/10.1007/978-3-662-60709-1 <https://doi.org/10.1007/978-3-662-60709-1>`__
   * `QGIS Documentation - Eine sanfte Einführung in GIS <https://docs.qgis.org/3.34/de/docs/gentle_gis_introduction/coordinate_reference_systems.html>`__
   * `Open Geo Edu  - Tutorial: Kartennetzentwürfe & Koordinatensysteme <https://learn.opengeoedu.de/tutorials/OGE-Tutorial_KNE_Koordinaten.pdf>`__
   *  `Geoneers - Marshall Mappers on Youtube <https://youtu.be/kGt0tgkPZwE?si=VjSO40_wuNdVn7Ll>`_.