ISO 19115-Format mit dem geocat.ch Export Plugin in QGIS
===============================================================================================================

Ziel
----

Exportiere die Metadaten eines Gebäude-Layers der Universität Tübingen in QGIS in ein geocat.ch-kompatibles XML-Format (ISO 19139_CHE-Profil), 
um sie für den Austausch oder die Veröffentlichung in einem Metadatenkatalog wie geocat.ch nutzen zu können.

Voraussetzungen
---------------

- QGIS (Version 3.x empfohlen)
- Gebäude-Layer der Universität Tübingen (z.B. als Shapefile, GeoPackage oder PostGIS-Layer)
- Internetzugang für Plugin-Installation

Schritt 1: Plugin-Installation
------------------------------

1. Starte QGIS.
2. Gehe zu **Erweiterungen > Erweiterungen verwalten und installieren**.
3. Suche nach **geocat export**.
4. Installiere das Plugin „geocat.ch Export“.
   - Das Plugin ist im offiziellen QGIS Plugin Repository verfügbar.

Schritt 2: Layer-Metadaten vorbereiten
--------------------------------------

1. Lade den Gebäude-Layer der Universität Tübingen in dein QGIS-Projekt.
2. Rechtsklicke auf den Layer und wähle **Eigenschaften**.
3. Wechsle zum Tab **Metadaten**.
4. Fülle mindestens die Pflichtfelder aus:

   - **Titel:** z.B. ``Gebäude der Universität Tübingen``
   - **Zusammenfassung (Abstract):** z.B. ``Dieser Datensatz enthält die Standorte und Grundrisse der Gebäude der Universität Tübingen. Er dient der Verwaltung, Planung und Information für Studierende, Mitarbeitende und Gäste.``
   - **Kontakt:** z.B. ``Universität Tübingen, Dezernat IV – Gebäudemanagement, gebaeude@uni-tuebingen.de``
   - **Räumliche Ausdehnung (Extent):** Automatisch übernehmen lassen oder Bounding Box manuell eingeben (z.B. den Bereich der Stadt Tübingen).

5. Optional: Ergänze weitere Felder wie Schlagwörter (z.B. ``Universität, Gebäude, Tübingen, Campus``), Zeitbezug, Lizenz, etc.

Schritt 3: Metadaten exportieren
--------------------------------

1. Rechtsklicke auf den Gebäude-Layer.
2. Wähle im Kontextmenü **Export layer metadata for geocat.ch**.
3. Das Plugin erstellt eine XML-Datei im geocat.ch-kompatiblen ISO 19139_CHE-Format und speichert sie im Home-Verzeichnis deines Benutzers.
   - Falls kein ``fileIdentifier`` angegeben ist, wird automatisch eine UUID generiert.

Schritt 4: XML-Datei prüfen und weiterverwenden
-----------------------------------------------

1. Öffne die erzeugte XML-Datei mit einem Texteditor oder XML-Viewer.
2. Prüfe, ob die wichtigsten Angaben korrekt übernommen wurden (Titel, Zusammenfassung, Kontakt, Ausdehnung).
3. Lade die XML-Datei im gewünschten Metadatenkatalog hoch, z.B. auf geocat.ch.

Hinweise & Einschränkungen
--------------------------

- Das Plugin exportiert aktuell nur den Typ ``dataset`` (Datensatz), keine Dienste (service).
- Felder wie Distributionsformate werden angelegt, aber nicht automatisch befüllt – ggf. manuell ergänzen.
- Die Validierung prüft keine katalogisierten Werte wie Kontakte oder Extents – eine abschließende Prüfung erfolgt im Zielkatalog.
- Die Datumsfelder werden wie folgt interpretiert: Das Beginndatum der zeitlichen Ausdehnung gilt als Erstellungsdatum; das Exportdatum ist der Zeitpunkt der Datei-Erstellung.

Weiterführende Links
--------------------

- `geocat.ch Export Plugin (QGIS Plugin Repository) <https://plugins.qgis.org/plugins/geocat_export/>`_
- `Anleitung und Hintergrund (GeoWerkstatt) <https://www.geowerkstatt.ch/blog/chtvrb2wavtr2rvwb6t1rqowtai617>`_
- `Handbuch geocat.ch (Metadatenfelder und Empfehlungen) <https://info.geocat.ch/de/handbuch-geocatch-geodaten>`_

Tipp
----

Das Plugin unterstützt mehrere Sprachen (de, en, fr, it), die Metadaten selbst werden jedoch nicht automatisch übersetzt. Ergänze wichtige Informationen 
ggf. in mehreren Sprachen, falls dies für den Zielkatalog erforderlich ist.


**Verbindung herstellen**

Passwörter und Nutzernamen erhälst du im Modul. Jetzt wollen wir eine Verbindun herstellen.


.. figure:: https://github.com/GeoWerkstatt/qgis-geocat-export/blob/master/geocat-export.gif
   :alt: QGIS-plugin für Geonode

   Quelle: `Geowerkstatt <https://www.geowerkstatt.ch/blog/chtvrb2wavtr2rvwb6t1rqowtai617>`__
