Übung Webmapping
==========

.. hint::

   Ziel der Übung
      * Die ersten Schritte zum Webmapping
      * Geoportale & Stadtpläne entdecken
      * Webmapping & WebGIS Software kennenlernen

.. note::

   **Geoportale**

      *  `COVID-19 Dashboard - John Hopkins University <https://coronavirus.jhu.edu/map.html>`__
      *  `Thünen Atlas <https://atlas.thuenen.de/#/>`__
      *  `Geoportal.de <https://www.geoportal.de/map.html?map=tk_03-mobile-breitbandverfuegbarkeit>`__
      *  `Geoportal Hamburg <https://geoportal-hamburg.de/?lng=de>`__
      *  `Stadtplan Stuttgart <https://maps.stuttgart.de/stadtplan/>`__
      *  `Stadtplan Esslingen <https://stadtplan.esslingen.de/stadtplan/>`__
      *  `Kreiskarte - Landratsamt Sigmaringen <https://experience.arcgis.com/experience/3cde06fa39b14fefb46746a8b551fbc1/>`__
      *  `Obstannahmestellen - Landratsamt Esslingen <https://webgis.regionalverband-braunschweig.de/portal/apps/experiencebuilder/experience/?id=ebf8a96383654dfa956cfd2a0c071272>`__
      *  `Flächennutzungsplan - Regionalverband Braunschweig <https://webgis.regionalverband-braunschweig.de/portal/apps/experiencebuilder/experience/?id=a369e782aad547269d264515c31f1c43>`__
      *  `Geoportal Landkreis Spree-Neiße <https://experience.arcgis.com/experience/6fe0897c55c14b1ba5eeea13645f50bc/?draft=true#widget_146=active_datasource_id:dataSource_3,center:1594769.2604481902%2C6754298.315757339%2C102100,scale:364165.49342622247,layer_visibility:%7B%22widget_146-dataSource_3%22%3A%7B%22widget_146-dataSource_3-1928fd75cad-layer-20%22%3Afalse%2C%22widget_146-dataSource_3-1928fc5f01b-layer-15%22%3Afalse%2C%22widget_146-dataSource_3-1928b5b1652-layer-50%22%3Atrue%2C%22widget_146-dataSource_3-1928b5b1652-layer-50-1928b59c7a5-layer-48%22%3Afalse%7D%7D>`__
      *  `Geoportal Kreis Lippe <https://geoportal.kreislippe.de/geoportal/application/bauleitplanung>`__
      *  `Geoportal Stadt Braunschweig <https://geoportal.braunschweig.de/WebOfficeNet/synserver?project=FRISBI&client=core&view=START_Themen%C3%BCbersicht>`__

   
Aufgabe 1
--------

Öffnen Sie die oben aufgelisteten Geoportale und untersuchen Sie diese auf folgende Kriterien.

1. Achte auf die Werkzeuge (Tools), die die Webanwendungen bereit stellen. Notieren Sie welche für Ihre Webanwendungen am relevantesten ist!
2. Gibt es Ihrer Einschätzung nach Unterschiede in der Nutzeroberfläche und der Bedienbarkeit?
3. Schätzen Sie welche Geoportale auf Open Source und welche auf proprietäre Software basiert
3. Bilden Sie drei bis vier Kategorien, denen Sie die einzelnen Geoportale zuordnen können.
   .. raw:: html

      <details>

   .. raw:: html

      <summary>

   Hinweis

   .. raw:: html

      </summary>

   .. raw:: html

      <ul>

   .. raw:: html

      <li>

   Bspw.: ESRI, Open Source, Rest

3. Interagiere mit der Karte und erkunde die Datensätze. Verwende hierfür das Zoom-Werkzeug und verschiebe die Karte. Beachte dabei die
   Statusleiste am unteren Bildschirmrand und wie diese sich verändert. Wie lauten die ungefähren Koordinaten für das Erdbeben in Alaska?
4. Mache dich mit dem Layer-Fenster (*Layer List*) vertraut. Blende abwechselnd verschiedene Layer ein und aus und verschiebe die Layer
   in der Hierarchie. Benennt den PB2002_plates sinnvoll um. Beachte, dass letzteres keine Auswirkung auf die Datenquellen (Dateinamen, Speicherort) hat.
5. Schau dir die **Attributdaten der Layer** an. Schaue dir zu diesem Zweck die Attributtabelle an und mache dich mit der zugehörigen
   Nutzeroberfläche vertraut. a) Wie viele Features gibt es im PB2002_plates? b) Welche Magnitude hatte das Erdbeben vor der Küste Neuseelands?
6. Ändere die **Projektion in der Kartenansicht** zu WGS84 UTM32N (EPSG-Code: 32632). **Beachte, dass dies nichts an der Projektion
   (den Koordinaten) der Dateien ändert, sondern lediglich die Projektion der Kartenansicht beeinflusst.** Überprüfe dies in den Eigenschaften des Punkt-Layers. Welche Projektion ist dort angegeben?
7. Speichere nun den Plattengrenzen-Layer in der Projektion WGS84 UTM 32N. **Dies ändert die Projektion der Datei.** Überprüft dies in den Eigenschaften des neu erstellten Layers.
8. Speichere dein Projekt ab.

**So (oder ähnlich) sieht’s am Ende aus**

.. figure:: img/stadt_vs_lra_esslingen_masterportal-arcgis-online_eb.PNG
   :alt: Stadtportal Esslingen (links) & WebMap Anwendung (rechts)
   :width: auto

   Stadtportal Esslingen (links) & WebMap Anwendung (rechts)


Optionale Aufgabe
--------

.. tip::

    Wir werden einige der oben aufgeführten Geoportale während des Moduls kennenlernen und damit arbeiten.


.. note::

   **Demos der Tools**

      *  `Mapbender <https://demo.mapbender.org/application/mapbender_user_yml>`__
      *  `Masterportal <https://www.masterportal.org/features/features>`__
      *  `Geonode <https://atlas.thuenen.de/#/>`__
      *  `ArcGIS Online <https://learn.arcgis.com/de/projects/get-started-with-arcgis-online/>`__
      *  `ArcGIS Experience Builder <https://developers.arcgis.com/experience-builder/>`__



- `Masterportal Video <https://www.masterportal.org/fileadmin/content/videos/Video_1_Masterportal_Vorstellung.mp4>`__

