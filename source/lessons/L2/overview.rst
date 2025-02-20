QGIS Print Composer
===============

Hier wird der QGIS Print Composer erläutert. Er ist das Zentrale Tool in QGIS, um Karten zu erstellen.

.. figure:: https://docs.qgis.org/3.34/de/_images/print_composer_complete.png
   :alt: Der QGIS Print Composer

   Quelle: QGIS Dokumentation

Kartengestaltung
================

Bei der Erstellung von Karten empfiehlt es sich grundsätzlich häufig zu speichern.

Druckzusammenstellung
---------------------

Print Layout erstellen
~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/videos/qgis_new_print_layout.mp4">

.. raw:: html

   </video>

Seitenformat einstellen
~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/videos/qgis_map_page_size.mp4">

.. raw:: html

   </video>

Karte
-----

Die Karte ist das zentrale Element der Druckzusammenstellung.

Karten-Feld hinzufügen
~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/videos/qgis_map_add_map.mp4">

.. raw:: html

   </video>

Für den Fall, dass mehrere Kartenblätter in einem Drucklayout zu sehen sein sollen, empfiehlt sich folgendes Vorgehen:

1. In QGIS die Ansicht so modifizieren, wie es für Kartenblatt 1 gewünscht ist (Layer ein-/ausblenden, etc.).
2. In der Druckansicht über die Liste der Elemente (oben rechts) Kartenblatt 1 auswählen.
3. In den Elementeigenschaften oben rechts auf *Vorschau aktualisieren* klicken.
4. In den Elementeigenschaften unter der Kategorie *Layer* die Haken bei *Layer sperren* und *Layerstile sperren* setzen, damit sich beim
   weiteren Modifizieren keine Änderungen in Kartenblatt 1 mehr ergeben.

Analog die Schritte für jedes Kartenblatt wiederholen.

Maßstab einstellen
~~~~~~~~~~~~~~~~~~

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/videos/qgis_map_change_scale.mp4">

.. raw:: html

   </video>

Kartenrahmen gestalten / Grid hinzufügen
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Achtet hier darauf das richtige Koordinatensystem zu wählen
-  Auch die Einheiten sind hier wichtig, in der Regel möchtet ihr ein Grid in den Einheiten der Projektion (*Map Units*) erstellen,
   *Centimeters* bezieht sich auf die Größe eures Kartenblattes und sagt nicht über die Lage der Daten aus

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/videos/qgis_map_add_grid.mp4">

.. raw:: html

   </video>

Schaut hier auch nochmal in `diese Issue <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/issues/6>`__
falls euer Grid nicht korrekt angezeigt wird.

Fehler beim Einfügen des Grids können außerdem auftreten, wenn vorher falsch umprojeziert wurde, siehe
`Projektionen </content/gis/01_karto-basics/qgis-Projektionen.md>`__.

Übersichtskarte / 2. Kartenfeld
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/videos/qgis_map_add_overview_map.mp4">

.. raw:: html

   </video>

-  setzt den Haken bei “Lock Layers” wenn ihr unterschiedliche Layer für eure Karten anzeigen möchtet
-  setzt den Haken bei “Lock Styles for Layers”, wenn ihr z.B. das gleiche Layer aber mit unterschiedlicher Signatur darstellen wollt.

Weitere Kartenelemente
----------------------

Titel und Textfelder
~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/videos/qgis_map_add_textlabel.mp4">

.. raw:: html

   </video>

Legende
~~~~~~~

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/videos/qgis_map_add_legend.mp4">

.. raw:: html

   </video>

Maßstabsbalken
~~~~~~~~~~~~~~

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/videos/qgis_map_add_scalebar.mp4">

.. raw:: html

   </video>

Nordpfeil / Bilder hinzufügen
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/videos/qgis_map_add_image.mp4">

.. raw:: html

   </video>

Die fertige Karte exportieren
-----------------------------

.. raw:: html

   <video width="100%" controls src="https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/videos/qgis_export_map.mp4">

.. raw:: html

   </video>

.. figure:: https://courses.gistools.geog.uni-heidelberg.de/giscience/qgis-book/-/raw/main/uploads/QGIS/my_world_map.png
   :alt: qgis_exported_map

   qgis_exported_map

**Hinweis:** Es lohnt sich immer die exportierte Karte nach dem Exportieren und vor der Abgabe noch einmal anzusehen. Dabei können zum
Beispiel **Fehler** in der Rechtschreibung, oder etwa auch eine falsche Maßeinheit im Maßstabsbalken auffallen. Es kann jedoch auch in seltenen
Fällen vorkommen, dass **Kartenelemente** beim Exportiervorgang **verrutschen**, oder ungewollte Artefakte, wie zum Beispiel kleinere
Striche, auftauchen. In der letzteren Situation liegt oft kein Fehler beim Bearbeiter, sondern im System vor. Um die falsche Darstellung zu
beheben, hilft oft nur erneutes Exportieren oder das Erstellen eines neuen Drucklayouts (am besten durch ein Transferieren der ursprünglichen
Zusammenstellung durch sukzessives STRG + V).

--------------

Weitere Ressourcen
==================

-  `QGIS Doku: Using Print
   Layout <https://docs.qgis.org/testing/en/docs/training_manual/map_composer/map_composer.html>`__

Erinnerung zu den Richtlinien der Kartengestaltung
==================================================

https://courses.gistools.geog.uni-heidelberg.de/giscience/kartographie_uebung

.. admonition:: Ein Videotutorial zur Nutzung des QGIS Print Composer
    :class: admonition-youtube

    ..  youtube:: rpkeBZHrXVQ&t=320s

    `Marshall Mappers channel on Youtube - Ganze Playlist: <https://www.youtube.com/watch?v=rpkeBZHrXVQ&list=PL5sBg4szdujUY-w6wvivTfxnCFzDQvrIi>`_.
