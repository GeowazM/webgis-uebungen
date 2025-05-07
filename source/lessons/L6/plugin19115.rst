ISO 19115-Format mit GeoCat Bridge for QGIS
===================================================================================

Ziel
----

Exportiere Metadaten eines Layers in QGIS im allgemeinen ISO 19115-Format – flexibel für nationale und internationale Kataloge (z.B. GeoNetwork, CSW) – mit dem Plugin GeoCat Bridge.

Voraussetzungen
---------------

- QGIS (Version 3.16 oder neuer empfohlen)
- Layer mit Geodaten (z.B. Gebäude der Universität Tübingen)
- Internetzugang für Plugin-Installation
- Optional: Zugang zu einem GeoNetwork-Katalog (z.B. für Publikation)

Schritt 1: Plugin-Installation
------------------------------

1. Öffne QGIS.
2. Gehe zu **Erweiterungen > Erweiterungen verwalten und installieren**.
3. Suche nach **GeoCat Bridge**.
4. Installiere das Plugin „GeoCat Bridge“.
   - Alternativ: Lade die neueste Version von der `GeoCat-Website <https://plugins.qgis.org/plugins/geocatbridge/>`_ oder dem `GeoCat-Kundenportal <https://www.geocat.net/docs/bridge/qgis/latest/installation.html>`_ herunter und installiere sie über **Installieren aus ZIP**.
5. Starte QGIS ggf. neu.
6. Aktiviere das Plugin, falls es nicht automatisch aktiviert ist.

Schritt 2: Metadaten für den Layer erfassen
-------------------------------------------

1. Lade deinen Layer (z.B. Gebäude der Universität Tübingen) in das QGIS-Projekt.
2. Rechtsklicke auf den Layer und wähle **Eigenschaften**.
3. Gehe zum Tab **Metadaten**.
4. Fülle die wichtigsten Felder aus:
   - **Titel:** z.B. ``Gebäude der Universität Tübingen``
   - **Zusammenfassung:** z.B. ``Dieser Datensatz enthält die Standorte und Grundrisse der Gebäude der Universität Tübingen.``
   - **Kontakt:** z.B. ``Universität Tübingen, Dezernat IV – Gebäudemanagement, gebaeude@uni-tuebingen.de``
   - **Räumliche Ausdehnung (Extent):** Automatisch übernehmen oder manuell eingeben.
   - Ergänze ggf. weitere Felder wie Schlagwörter, Lizenz, Zeitbezug etc.

Schritt 3: Metadaten mit GeoCat Bridge exportieren
--------------------------------------------------

1. Öffne das Menü **Internet > GeoCat Bridge > Export**.
2. Wähle den gewünschten Layer aus.
3. Wähle als Exportziel **Lokale Datei**.
4. Wähle das gewünschte Metadatenformat, z.B. **ISO 19115** oder **ISO 19139**.
5. Lege das Zielverzeichnis und den Dateinamen fest.
6. Klicke auf **Exportieren**.
7. Die Metadaten werden als XML-Datei im gewählten Format gespeichert.

Schritt 4: Metadaten weiterverwenden oder publizieren
-----------------------------------------------------

- Öffne die erzeugte XML-Datei mit einem Texteditor oder XML-Viewer.
- Prüfe, ob alle Angaben korrekt übernommen wurden.
- Die Datei kann jetzt in einen Metadatenkatalog wie GeoNetwork (CSW) importiert oder mit Partnern ausgetauscht werden.
- Optional: Mit GeoCat Bridge kannst du Metadaten und Daten auch direkt in einen GeoNetwork-Katalog publizieren (Serververbindung erforderlich).

Vorteile von GeoCat Bridge
--------------------------

- Flexibler Export in verschiedene Metadatenformate (ISO 19115, ISO 19139 u.a.).
- Unterstützung für nationale und internationale Profile.
- Möglichkeit, Metadaten, Daten und Styles gemeinsam zu exportieren oder zu publizieren.
- Einfache Integration mit GeoNetwork, GeoServer und MapServer.
- Open Source und aktiv weiterentwickelt.

Hinweise
--------

- Für Publikation in einen Katalog (z.B. GeoNetwork) muss eine Serververbindung im Plugin konfiguriert werden.
- Neuere QGIS-Versionen benötigen ggf. das Python-Paket ``lxml`` für Metadatenexport.
- Die Community-Edition ist frei verfügbar, für Enterprise-Support und zusätzliche Features gibt es eine lizenzierte Version.

Weiterführende Links
--------------------

- `GeoCat Bridge Plugin (QGIS Plugin Repository) <https://plugins.qgis.org/plugins/geocatbridge/>`_
- `Offizielle Dokumentation GeoCat Bridge <https://www.geocat.net/docs/bridge/qgis/latest/>`_
- `GitHub: GeoCat Bridge for QGIS <https://github.com/GeoCat/qgis-bridge-plugin>`_
- `GeoNetwork opensource <https://geonetwork-opensource.org/>`_

Fazit
-----

Das geocat.ch Export Plugin ist optimal für den Export ins Schweizer ISO 19139_CHE-Profil.  
Für allgemeine ISO 19115-Exporte oder internationale Kataloge empfiehlt sich GeoCat Bridge for QGIS als flexible und leistungsfähige Alternative.

**Verbindung herstellen**

Passwörter und Nutzernamen erhälst du im Modul. Jetzt wollen wir eine Verbindun herstellen.


.. figure:: https://geosolutionsgroup.com/wp-content/uploads/2025/01/qgisgeonode.jpg?x67834
   :alt: QGIS-plugin für Geonode

   Quelle: `QGIS-plugin für Geonode <https://www.geosolutionsgroup.com/blog/geonode-4-4/>`__
