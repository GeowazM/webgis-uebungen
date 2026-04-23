Metadaten mit GeoNetwork erstellen
========

.. hint::

      Um den FARI Prinzipien u.a. des OGC gerecht zu werden, ISO-konforme Geodaten bereitzustellen
      und ggf. auch INSPIRE-Anforderungen zu erfüllen gibt es eine Reihe von Software, die uns dabei unterstützt diese Anforderungen zu erfüllen.

.. hint::

      Es gibt verschiedene Normen, die mit Hilfe von GeoNetwork und dessen Benutzeroberfläche verwaltet werden können:

      - Dublin Core
      - ISO 19115 (oder Vorgänger ISO 19139)
      - INSPIRE

      Diese Normen finden sich in der *Adminkonsole* unter *Metadaten & Vorlagen*


INSPIRE Ja oder Nein?
----------------

Hier ist ein guter **Leitfdaden der GDI-DE** zum Vorgehen mit Metadaten & deren Geodatendienste (WMS/WFS): `INSPIRE Umsetzung - GDI-DE <https://www.gdi-de.org/umsetzung/inspire-umsetzung/>`__




Metadaten mit GeoNetwork erstellen
---------

Eine Schritt für Schritt Anleitung (engl.): `INSPIRE-konforme Einträge in GeoNetwork <https://docs.geonetwork-opensource.org/4.4/user-guide/describing-information/inspire-editing/>`__


===========================================
🎯 Aufgabentypen für die Hands-on Phase
===========================================

Anstatt klassischer Arbeitsblätter kannst du die Aufgaben als "Quests" oder Level strukturieren. Das erhöht den Reiz, die oft pingelige Metadaten-Validierung erfolgreich abzuschließen.

Level 1: Metadaten importieren
-------------------------------------------

* **Lernziel:** Verständnis für den XML-Austausch von Metadaten.
* **Aufgabe:** Lade einen Beispiel-Datensatz über den bereitgestellten Link der GDI-BW herunter (als XML) und importiere ihn in deinem GeoNetwork-Konto.
  
  * Füge Ihn der Gruppe *webgis-2026* hinzu
  * Hinweis: Häkchen bei **"Neue UUID generieren"!** aktivieren.

* **Arbeitsauftrag:** Finde heraus, unter welcher INSPIRE-Kategorie (Thema) dieser Datensatz aktuell einsortiert ist. Ändere den Titel so ab, dass dein Vorname darin vorkommt, damit wir ihn im Katalog wiederfinden.

Level 2: Die Validierung
-----------------------------------------------------------

* **Lernziel:** Anwendung der `Verordnung (EG) Nr. 1205/2008 hinsichtlich Metadaten <https://eur-lex.europa.eu/legal-content/DE/ALL/?uri=CELEX:32008L0120>`__ in der Praxis.
* **Aufgabe:** Nutze die interne Validierungsfunktion im GeoNetwork.
* **Arbeitsauftrag:** Führe eine Validierung deines Metadatensatzes durch. Das System wird dir (wahrscheinlich) Fehler anzeigen. Deine Mission: Behebe die roten Warnungen (z. B. fehlende Zugänglichkeitseinschränkungen oder unvollständige Ansprechpartner), bis die Validierung erfolgreich durchläuft.

Level 3: Metadaten mit Geodiensten koppeln
-------------------------------------------------------

* **Lernziel:** Metadaten als Brücke zu echten Geodiensten (WMS/WFS) verstehen.
* **Aufgabe:** Verknüpfe den "toten" Metadatensatz mit lebendigen Daten. Dies ist im Sinne der `Verordnung (EG) Nr. 1089/2010 über die Bereitstellung von Geodaten und Geodatendiensten <https://eur-lex.europa.eu/legal-content/DE/TXT/PDF/?uri=CELEX:32010R1089>`__ ein wichtiger Schritt, um die Auffindbarkeit und Nutzbarkeit deiner Daten zu erhöhen.
* **Arbeitsauftrag:** Wechsle zu deinem Metadatensatz, bearbeite Ihn und füge unter "Online-Ressourcen" die GetCapabilities-URL des GeoServers hinzu (z. B. ``https://[DEIN-SERVER]/geoserver/wms``). Wähle als Protokoll **OGC:WMS Web Map Service** aus und trage den Layer-Namen ein (Format: ``Workspace:Layer``). Speichere die Änderungen und teste die Verknüpfung, indem du den WMS in QGIS über die CSW-Schnittstelle suchst und lädst.


===========================================
Cheat-Sheet: GeoNetwork & INSPIRE Metadaten
===========================================

**Tipp für die Praxisphase:** Speichere regelmäßig zwischen! Die Vorgaben der INSPIRE-Richtlinien sind streng und die Validierung verzeiht wenig, aber mit diesen Grundlagen umschiffst du die häufigsten Fehlerquellen.

1. GeoNetwork Navigation & Editor-Tricks
----------------------------------------

* **Ansichten wechseln:** Nutze im Editor oben rechts das Dropdown-Menü, um zwischen "Standardansicht", "INSPIRE-Ansicht" und "Vollständiger Ansicht" zu wechseln. Die INSPIRE-Ansicht blendet unnötigen Ballast aus und fokussiert sich auf das Wesentliche.
* **Schnelles Speichern (Diskette):** Speichert den aktuellen Stand, ohne den Editor zu verlassen. Nutze das regelmäßig nach größeren Anpassungen.
* **Speichern & Schließen:** Speichert die Daten und bringt dich zurück zur Katalogübersicht.
* **Fehler-Check (Validierungs-Button):** Führe die Validierung direkt im Editor aus. Rote Kreuze zeigen dir genau an, in welchen Reitern noch Pflichtfelder leer oder fehlerhaft sind.
* **Verzeichnis-Suche (Lupe):** Klicke auf das Lupen-Symbol neben Kontaktfeldern, um Personen oder Organisationen aus dem internen Verzeichnis zu laden, statt alle Daten (Adresse, Mail) mühsam von Hand einzutippen.

2. Die "Big 5" INSPIRE-Pflichtfelder (Deine Validierungs-Retter)
---------------------------------------------------------------

Wenn die Validierung fehlschlägt, liegt es zu 90 % an diesen fünf Bereichen:

+----------------------------+----------------------------------------------------------+-------------------------------------------------------------------------------------------------+
| Feld                       | Was wird verlangt?                                       | Typischer Fehler                                                                                |
+============================+==========================================================+=================================================================================================+
| **Identifikation** | Eindeutiger Titel und eine verständliche Beschreibung    | Abstract ist zu kurz, komplett leer oder unverständlich.                                        |
|                            | (Abstract).                                              |                                                                                                 |
+----------------------------+----------------------------------------------------------+-------------------------------------------------------------------------------------------------+
| **Schlüsselwörter** | Mindestens ein Schlagwort aus dem offiziellen            | Es wurden nur Freitext-Wörter verwendet statt der Thesaurus-Anbindung.                          |
|                            | GEMET-Thesaurus.                                         |                                                                                                 |
+----------------------------+----------------------------------------------------------+-------------------------------------------------------------------------------------------------+
| **Verantwortliche Stelle** | Wer ist zuständig? (Name, Organisation, E-Mail).         | Es wurde keine "Rolle" (z. B. Eigentümer, Verwalter) aus dem Dropdown zugewiesen.               |
+----------------------------+----------------------------------------------------------+-------------------------------------------------------------------------------------------------+
| **Zugang & Nutzung** | Klare Angaben zu Lizenzen und Nutzungseinschränkungen.   | Feld vergessen. Oft muss explizit "Keine Bedingungen" ausgewählt werden, wenn es frei ist.      |
+----------------------------+----------------------------------------------------------+-------------------------------------------------------------------------------------------------+
| **Datenqualität (Lineage)**| Kurzer Text zur Herkunft: Wie wurden die Daten erhoben?  | Feld bleibt leer. Ein prägnanter Satz reicht oft schon (z. B. "Digitalisiert aus Luftbildern"). |
+----------------------------+----------------------------------------------------------+-------------------------------------------------------------------------------------------------+

3. Online-Ressourcen verknüpfen (Die GeoServer-Anbindung)
--------------------------------------------------------

Metadaten ohne Geodaten sind nur halbe Kataloge. Um deinen Datensatz mit einer echten Karte zu verbinden, navigierst du zum Bereich "Online-Ressourcen".

* **URL:** Trage hier die GetCapabilities-URL deines GeoServers ein (z. B. ``https://[DEIN-SERVER]/geoserver/wms``).
* **Protokoll:** Wähle zwingend **OGC:WMS Web Map Service** (für Karten zum Ansehen) oder **OGC:WFS Web Feature Service** (für Vektordaten zum Download) aus der Liste.
* **Name der Ressource:** Trage hier exakt den Layer-Namen (Format: ``Workspace:Layer``) aus dem GeoServer ein, damit GeoNetwork den richtigen Dienst aufruft.

4. CSW-Endpunkt (Für QGIS & externe Kataloge)
---------------------------------------------

Mit diesem Standard machst du deinen Metadatenkatalog für die Außenwelt (und andere Suchmaschinen) über die Schnittstelle sichtbar.

**Deine CSW-Basis-URL lautet:**
  ``https://[DEINE-DOMAIN]/geonetwork/srv/ger/csw``

**So testest du deine eigene Arbeit in QGIS:**

1. Öffne ein leeres QGIS-Projekt.
2. Klicke im Menü auf **Web** und öffne das Plugin **MetaSearch**.
3. Lege unter dem Reiter "Dienste" eine **Neue Verbindung** an und füge deine CSW-URL ein.
4. Wechsle in den Reiter "Suche", tippe deinen Vornamen (oder deinen Datensatz-Titel) ein.
5. Klicke auf **Suchen**, wähle deinen Datensatz aus und lade den verknüpften WMS direkt in die Karte!