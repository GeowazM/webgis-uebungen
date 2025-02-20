Exercise 7 - Optional
========

.. note::
   
   Ziel der Übung
      -  WMS Layer hinzufügen
      -  Reliefanalysen durchführen


.. seealso::

   Daten
      - siehe Exercise 7
      - `WMS-Layer des BGR <https://geoportal.bgr.de/mapapps/resources/apps/geoportal/index.html?lang=de#/datasets/portal/cf2c54d6-1412-462c-9271-6307bfc4ba48>`__

.. hint::

   OGC-Standards

   Die Open Geospatial Consortium (OGC) Standards sind international anerkannte Spezifikationen, die den Austausch von geospatialen Informationen zwischen 
   verschiedenen Systemen ermöglichen1. Diese Standards decken verschiedene Bereiche ab, wie z.B. Datenentdeckung, Organisation, Zugriff, Verarbeitung, Visualisierung und Entdeckung. 

   WMS (Web Map Service): Ein Web Map Service (WMS) ist ein Standardprotokoll, das von der OGC entwickelt wurde, um georeferenzierte Kartenbilder über das Internet 
   bereitzustellen. WMS-Dienste bieten verschiedene Anfragetypen:

   - GetCapabilities: Liefert Metadaten über den WMS-Dienst, wie z.B. verfügbare Layer, unterstützte Bildformate und Koordinatensysteme
   - GetMap: Liefert ein Kartenbild basierend auf den angegebenen Parametern wie Breite, Höhe, Koordinatensystem und Bildformat
   - GetFeatureInfo: (optional) Liefert Informationen über bestimmte Punkte auf der Karte, wenn der Layer als 'abfragbar' markiert ist

   Quelle: `OGC.org <https://www.ogc.org/de/publications/standard/wms/>`__

   Als Alternative zu einem WMS-Layer werden häufig WMTS-Layer bereitgestell: 
   Da WMTS vorgerenderte Kacheln verwendet, sind die Antwortzeiten sehr kurz. Die Kacheln können auf dem Server und Client zwischengespeichert werden, was die Ladezeiten erheblich reduziert.
   Quelle `Weichand, J. (2014): Moderne Geodatenbereitstellung im Kontext der europäischen Geodateninfrastruktur INSPIRE. FOSSGIS 2014. <https://www.weichand.de/download/fossgis_2014_Weichand_INSPIRE-Netzdienste.pdf>`__




🗺 Aufgabe 1 - WMS-Layer hinzufügen
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Füge einen WMS-Layer der `Bundesanstalt für Geowissenschaften und Rohstoffe (BGR) <https://www.bgr.bund.de/DE/Home/homepage_node.html>`__ hinzu

.. figure:: https://raw.githubusercontent.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/refs/heads/main/exercise_07/exercise_7_neu/WMS-Layer_hinzufuegen_clip.jpg
   :alt: WMS-Layer hinzufügen

   WMS-Layer hinzufügen

- Hole dir `beim BGR <https://geoportal.bgr.de/mapapps/resources/apps/geoportal/index.html?lang=de#/datasets/portal/cf2c54d6-1412-462c-9271-6307bfc4ba48>`__ den WMS GetCapabilities Link

   .. raw:: html

      <details>

   .. raw:: html

      <summary>

   Lösung

   .. raw:: html

      </summary>

   .. raw:: html

      <ul>

   .. raw:: html

      <li>

   `Der WMS-Layer liegt als XML Datei vor <https://services.bgr.de/wms/inspire_ge/guek250/?REQUEST=GetCapabilities&SERVICE=wms&VERSION=1.3.0>`__

   .. raw:: html

      <li>

   Link: https://services.bgr.de/wms/inspire_ge/guek250/?REQUEST=GetCapabilities&SERVICE=wms&VERSION=1.3.0

   .. raw:: html

      </ul>

   .. raw:: html

      </details>


.. raw:: html

   <details>
     <summary>Lösung</summary>

     <p><a href="https://services.bgr.de/wms/inspire_ge/guek250/?REQUEST=GetCapabilities&SERVICE=wms&VERSION=1.3.0">Der WMS-Layer liegt als XML Datei vor</a></p>
     <p>Link:https://services.bgr.de/wms/inspire_ge/guek250/?REQUEST=GetCapabilities&SERVICE=wms&VERSION=1.3.0</p>

   </details>

🧮 Aufgabe 2 - Das Relief analysieren und visualisieren
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Aufgabe 2 a - Visualisieren
^^^^^^^^^^^^^^^^^^^^^^^^^

-  Berechnet eine Schummerung (via **Hillshade**) für das Geländemodell. Tipp: Nutze die Processing - Toolbox, um Funktionen zu finden.
-  Füge den Wert 0 (schwarze Ränder am Dateirand) den No Data Values hinzu (via *Transparency - Additional…*)
-  Schiebe das Höhenmodell-Layer (DEM) über den Hillshade-Layer und setze die Transparenz des DEMs auf 70% (**Transparency - Global Opacity**).
-  Ermittelt die Hangneigung in ° (via **Slope**). Diese kann eine Visualisierung ebenfalls aufwerten.

Aufgabe 2 b - Analysieren
^^^^^^^^^^^^^^^^^^^^^^^

-  Selektiert besonders steile Regionen (>20°) (nutzt dazu das **Reclassify Tool**)
-  Erstellt Übersichtsstatistiken für die beiden Nationalparks (bspw. mit Hilfe von **Zonal Statistics**).

   -  Schaut euch die Werte an. Was zeigen uns die Zahlen?
   -  Was ist die maximale Hangneigung pro Nationalpark?
   -  Wie hoch ist die durchschnittliche Hangneigung pro Nationalpark?

-  Konvertiert die Auswahl ins Vektorformat (**Conversion - Raster to Vector**). Anschließend kannst du das **Basic statistic per field** nutzen.
