Hands-on: Metadaten mit CatMDEdit erstellen (15 Min.)
========================================================

a) Tool-Vorstellung (2 Min.)
----------------------------

- **CatMDEdit:** Kostenlos, plattformunabhängig, unterstützt ISO 19115, ISO 19139 und INSPIRE.
- **Download:** `catmdedit.sourceforge.io <https://catmdedit.sourceforge.io>`_
- **Installation:** Java erforderlich, dann einfach starten.
- **Alternativen:** Geoportal.gov.pl Metadata Editor, ArcGIS Pro Metadateneditor (kurz erwähnen).

b) Neues Metadaten-Dokument anlegen (2 Min.)
--------------------------------------------

- Starte CatMDEdit.
- Wähle „Neues Metadatendokument“.
- Wähle das gewünschte Profil: ISO 19115, ISO 19139 oder INSPIRE.
- Kurzer Überblick über die Oberfläche und wichtigsten Menüs.

c) Schritt für Schritt: Felder ausfüllen (8 Min.)
-------------------------------------------------

1. **Identifikation**

   - Titel: „Beispiel-Datensatz Flurstücke NRW 2025“
   - Zusammenfassung: „Dieser Datensatz enthält die Flurstücke von NRW für das Jahr 2025...“
   - Schlagwörter: „Flurstücke, Kataster, NRW, 2025“
   - Themenkategorie: Auswahl aus Liste (z.B. Verwaltung, Geobasisdaten)

2. **Räumlicher Bezug**

   - Geografische Ausdehnung: Rechteck aufziehen oder Koordinaten eingeben (Bounding Box für NRW)
   - Optional: Visualisierung auf Karte zeigen

3. **Zeitlicher Bezug**

   - Erfassungsdatum: z.B. 2025-01-01 bis 2025-12-31
   - Aktualisierungsintervall: „Jährlich“ oder „unregelmäßig“

4. **Kontakt**

   - Organisation: „Landesvermessungsamt NRW“
   - E-Mail, Telefonnummer, Adresse

5. **Nutzungsbedingungen**

   - Lizenz: z.B. „Datenlizenz Deutschland – Namensnennung – Version 2.0“
   - Zugriffsrechte: „Öffentlich“

6. **Distribution**

   - Download-Link oder Dienst-URL eintragen
   - Format angeben (z.B. GML, Shape, GeoJSON)

7. **Weitere Felder**

   - Vorschaubild hochladen (optional)
   - Dokumentation/Link zu weiterführenden Infos

.. note::

   CatMDEdit zeigt an, ob Pflichtfelder fehlen – so bleibt alles INSPIRE- und ISO-konform.

d) Validierung und Export (3 Min.)
----------------------------------

**Validierung:**

- Prüfe, ob alle Pflichtfelder ausgefüllt sind (CatMDEdit gibt Hinweise).
- Fehler und Warnungen besprechen.

**Export:**

- Exportiere als ISO 19139 XML (Datei → Exportieren → ISO 19139).
- Zeige, wie die XML-Datei aussieht (kurzer Blick in den Code).

**Import in Portale:**

- Hinweis, wie die Datei in Portale wie GEOkatalog.NRW, INSPIRE-Kataloge oder eigene Systeme eingespielt werden kann.

6. Best Practices & Tipps (3 Min.)
==================================

**Qualität vor Quantität:**

- Lieber weniger, aber vollständige und korrekte Metadaten als viele unvollständige.

**Hilfetexte nutzen:**

- Viele Editoren bieten Tooltips und Hilfetexte – diese helfen, Fehler zu vermeiden.

**Aktualität sicherstellen:**

- Metadaten regelmäßig prüfen und aktualisieren.

**Redundanzen vermeiden:**

- INSPIRE-Daten nur an einer Stelle beschreiben (z.B. GEOkatalog.NRW).

**Synergien nutzen:**

- Metadaten können zwischen Open Data und Geodateninfrastruktur geteilt werden (siehe Leitfaden NRW).

7. Häufige Fehler & Troubleshooting (2 Min.)
============================================

- Fehlende Pflichtfelder (z.B. kein räumlicher Bezug)
- Unklare oder zu knappe Beschreibungen
- Falsche oder fehlende Lizenzangaben

**Tipp:** Validierungsfunktionen nutzen, Rückfragen an Metadaten-Teams oder Leitfäden.

8. Ausblick & weiterführende Ressourcen (1 Min.)
================================================

**Weiterbildung:**

- Schulungen der GDI-DE, Online-Kurse, Webinare

**Wichtige Links:**

- `CatMDEdit Download <https://catmdedit.sourceforge.io>`_
- `Leitfaden NRW <https://open.nrw/system/files/media/document/file/leitfaden_zur_metadatenerfassung.pdf>`_
- `INSPIRE-Metadatenprofil Deutschland <https://www.gdi.nrw/system/files/media/document/file/architektur_gdi_de_konventionen_metadaten_v2_3_0.pdf>`_
- `GEOkatalog NRW <https://www.geoportal.nrw/geoportal/metadaten>`_

**Community:**

- Arbeitskreis Metadaten der GDI-DE, Foren, Mailinglisten
