WMS auslesen
==========

.. hint::

   Ziel der Übung
      * OGC-Dienste kennenlernen 
      * WMS-Layer lesen lernen

.. seealso::

      *  `OGC <https://www.ogc.org/de/>`__
      *  `QGIS Server <https://docs.qgis.org/3.34/en/docs/server_manual/index.html>`__
      *  `OGC-Dienste - Basics <https://docs.qgis.org/3.40/en/docs/server_manual/services/basics.html>`__


Hintergrund
--------

Du willst den Austausch von Geodaten mit internen & externen Partnern effizienter gestalten. Deine Geodaten sollen als Schaufenster für
andere Abteilungen zur Verfügung stehen, damit diese bessere Entscheidungen finden können. Externe Ingenieurbüros sollen eine Möglichkeit erhalten, eure Geodaten anzuzapfen, 
um beidseitig Arbeit zu sparen. In solchen Fällen ploppt oft das Stichwort Interoperabilität auf, dass seit Jahrzenten Thema der Geodaten-Community ist. Für eine bessere
Interoperabilität bzw. Austauschbarkeit von Geodaten wurden die OGC-Standards wie bspw. WMS-& WFS-Layer entwickelt. Mit solchen OGC-Diensten haben wir schon gearbeitet.
Wir haben zum Beispiel die OpenStreetMap Hintergrundkarte (als Konsumenten)  in ArcGIS Pro und QGIS eingebunden. Mit dem QGIS-Server können wir (zum Produzenten werden und) eigene WMS/WFS-Dienste erstellen. 
Diese eigenen Dienste können wir wiederrum internen & externen Partnern über einen Link zur Verfügung stellen. Neben QGIS-Server gibt es weitere räumlichen Server wie GeoServer und MapServer, die solche Dienste 
ebenfalls bereitstellen können. Da der QGIS-Server in QGIS Desktop nutzerfreundlich integierbar ist, nutzen wir ihn in dieser Übung. Aus früheren Kursen existiert eine Übung mit GeoServer, 
die zur Verfügung gestellt werden kann, falls Sie diesen Server kennenlernen möchten.


.. hint::

   Hier ist die Seite der `Firma Terrestris <https://www.terrestris.de/de/openstreetmap-wms/>`__, die mehrere eigene WMS-Dienste anbieten. So kann die Bereitstellung deiner OGC-Dienste irgendwann auch aussehen. 




**Starten wir mit dem WMS-Layer!**


WMS-Dienst die mit QGIS-Server erstellt wurden kennenlernen
--------

Den Link zum WMS-Layer, den wir für dich vorbereitet haben, bekommt ihr im Kurs. Wir werden in dieser Übung wie folgt vorgehen:

- WMS-Layer Link & deren funktionsweise näher kennenlernen
- WMS-Layer in QGIS vorbereiten
- Eigenen WMS-Layer veröffentlichen

.. important::

   Wir haben auf unserem Server `QGIS-Server <https://docs.qgis.org/3.40/en/docs/server_manual/getting_started.html>`__ installiert und ein QGIS-Projekt mit dem 
   Namen **world.qgs** in den Ordner **/home/qgis/projects** kopiert.
   Der QGIS-Server erkennt die Konfigurationen, die wir in QGIS vorher definiert haben und liefert (**served**) uns das Projekt als Web Mapping Service (WMS).
   Das werden wir am Ende der Übung ebenfalls mit unseren eigenem Projekt machen.

Der Link:

   * /cgi-bin/qgis_mapserv.fcgi?MAP=/home/qgis/projects/world.qgs&LAYERS=airports,countries,countries_shapeburst,places&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetMap&CRS=EPSG:4326&WIDTH=800&HEIGHT=400&BBOX=-90,-180,90,180

.. hint::

   Du kannst dir OGC-Dienste von Geoportalen anzeigen lassen, indem du mit der *rechten Maustaste* (irgendwo) klickst und *Untersuchen* auswählst. Hier kannst du unter dem WLAN-Logo, 
   dass für Netzwerk steht, die OWS-Dienste der Website anschauen. Durch das Auswählen eines bspw. Service=WMS&... unter *Name* erscheint dann im *Header* Bereich die Anforderungs-URL,
   die dem GetCapabilities Link des OGC-Dienstes entspricht. Diesen kannst du kopieren und in QGIS virtualisieren. Hier befinden sich i.d.R. auch Informationen, welches WebMapping/WebGIS Tool genutzt wird.
   Versuche es aus!


Gehen wir den Link bzw. den WMS-Dienst Schritt für Schritt durch und lernen seine funktionsweise näher kennen. Der WMS-Dienst kann über den Link gesteuert werden.
Einige der hier aufgelisteten Parameter sind standardisiert und in den OGC-Spezifikationen definiert, während andere sehr spezifisch für QGIS Server sind.

Standardparameter

+---------+---------------------------+-----------------------------+
| Konzept | Beschreibung              | Beispiel                    |
+=========+===========================+=============================+
| SERVICE | Name des Dienstes         | SERVICE=WMS                 |
+---------+---------------------------+-----------------------------+
| REQUEST | Name der Anfrage          | REQUEST=GetCapabilities     | 
+---------+---------------------------+-----------------------------+

GetCapabilities
~~~~~~~~~~~~~~~~~

1. Öffne den folgenden Link. Was für ein Format öffnet sich?
   
   * /cgi-bin/qgis_mapserv.fcgi?&REQUEST=GetCapabilities&SERVICE=WMS&VERSION=1.3.0
   
   - Welches CRS und welche EPSG ist hier hinterlegt?
   - Finde den Layer *countries* (Suchen via Strg + F)


Anwenderparameter

+-----------+----------------------------------------+-------------------------------------+
| Konzept   | Beschreibung                           | Beispiel                            |
+===========+========================================+=====================================+
| MAP       | QGIS-Projektdatei                      | MAP=/home/qgis/projects/world.qgs   |
+-----------+----------------------------------------+-------------------------------------+
| Short name| Definition des Kurznamens              | LAYERS=countries                    | 
+-----------+----------------------------------------+-------------------------------------+

Die Anbieterparameter ermöglichen es, die zu verwendende QGIS-Projektdatei zu definieren. Es kann sich um einen absoluten Pfad oder einen Pfad relativ 
zum Speicherort der Serverausführungsdatei qgis_mapserv.fcgi handeln. MAP ist standardmäßig obligatorisch, da eine Anfrage ein QGIS-Projekt benötigt, um tatsächlich zu funktionieren. 


Der Kurzname verwendet werden, um diese Elemente bei der Interaktion mit dem QGIS Server zu identifizieren. Zum Beispiel mit dem Standardparameter LAYERS

.. figure:: https://docs.qgis.org/3.40/en/_images/set_group_wms_data.png
   :alt: Set group WMS data

   Der "Short name" kann in QGIS - QGIS-Server Plugin definiert werden. Quelle: `QGIS Dokumentation <https://docs.qgis.org/3.40/en/docs/server_manual/services/basics.html>`__



GetMap
~~~~~~~~~~~~~~~~~

Gehen wir zum Kartendienst. Öffne folgenden Link
   
   * /cgi-bin/qgis_mapserv.fcgi?MAP=/home/qgis/projects/world.qgs&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetMap&WIDTH=800&HEIGHT=400&LAYERS=airports,countries,countries_shapeburst,places&CRS=EPSG:4326&BBOX=-90,-180,90,180

Ändere die Parameter *&WIDTH* auf "1200" und *&HEIGHT* auf "780". Was verändert sich?

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

/cgi-bin/qgis_mapserv.fcgi?MAP=/home/qgis/projects/world.qgs&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetMap&WIDTH=1200&HEIGHT=780&LAYERS=airports,countries,countries_shapeburst,places&CRS=EPSG:4326&BBOX=-90,-180,90,180




Ändere den Parameter *&CRS* zu "3857". Was verändert sich?

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

/cgi-bin/qgis_mapserv.fcgi?MAP=/home/qgis/projects/world.qgs&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetMap&WIDTH=1200&HEIGHT=780&LAYERS=airports,countries,countries_shapeburst,places&CRS=EPSG:3857&BBOX=-90,-180,90,180
   
Wir sehen, dass wir nichts sehen. Unser Beispiel WMS-Dienst bietet den Dienst nur im EPSG:4326 an.






Ändere den Parameter *&BBOX* von "-90" auf "0". Was verändert sich?

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

/cgi-bin/qgis_mapserv.fcgi?MAP=/home/qgis/projects/world.qgs&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetMap&WIDTH=1200&HEIGHT=780&LAYERS=airports,countries,countries_shapeburst,places&CRS=EPSG:4326&BBOX=0,-180,90,180
   

Die Bbox (eng. bounding box) ist der Extent, also die räumliche Ausdehnung unseres REQUEST. So können wir einen WMS-Dienst auf den von uns interessierte Gebiet zuschneiden.



Ändere den Parameter *&LAYERS* von "airports,countries,countries_shapeburst,places" zu "countries_shapeburst,places". Was verändert sich?

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

/cgi-bin/qgis_mapserv.fcgi?MAP=/home/qgis/projects/world.qgs&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetMap&WIDTH=1200&HEIGHT=780&LAYERS=countries_shapeburst,places&CRS=EPSG:4326&BBOX=-90,-180,90,180
   
Mit LAYERS können wir einzelne Layer eines WMS-Dienst individuell anpassen.



.. hint::

   /cgi-bin/qgis_mapserv.fcgi?  <!-- unser QGIS-Server -->

   MAP=/home/qgis/projects/world.qgs <!-- navigation -->

   &SERVICE=WMS     <!-- OGC-Dienst -->

   &VERSION=1.3.0   <!-- Version des Dienstes -->

   &REQUEST=GetMap  <!-- Karte -->

   &WIDTH=800       <!-- Darstellung im Browser -->

   &HEIGHT=400      <!-- Darstellung im Browser -->

   &LAYERS=airports,countries,countries_shapeburst,places   <!-- Layerauswahl -->

   &CRS=EPSG:4326         <!-- Koordinatenbezugssystem -->

   &BBOX=-90,-180,90,180  <!-- Räumliche Ausdehnung -->


Layer selektion & Filter
~~~~~~~~~~~~~~~~~

Du kannst den existierenden Kartendienst nach deinen Wünschen anpassen, indem du nur einzelne Layer auswählst oder die Layer filterst.

&LAYERS=countries_shapeburst,countries,places

&FILTER=countries_shapeburst,countries:"name" = 'France';places: "name" = 'Paris'



.. hint::

   Weitere Möglichketien WMS-Dienste zu konfigurieren und abzufragen findest du in der `QGIS Dokumentation (englisch) <https://docs.qgis.org/3.40/en/docs/server_manual/services/wms.html#getmap>`__


GetFeatureInfo
~~~~~~~~~~~~~~~~~

Du kannst den Kartendienst mit Informationen anreichern, die interaktiv vom Konsumenten abfragbar sind. 


&INFO_FORMAT=text/xml

&TRANSPARENT=TRUE

&QUERY_LAYERS=mylayer1

&FEATURE_COUNT=3

&I=250

&J=250


GetLegendGraphic
~~~~~~~~~~~~~~~~~

Als letztes WMS-Dienst Element schauen wir uns die Legende an.

SERVICE=WMS

&REQUEST=GetLegendGraphic

&LAYERS=countries,airports

&BBOX=43.20,-2.93,49.35,8.32

&CRS=EPSG:4326
