WMS-Dienst erstellen
==========

.. hint::

   Ziel der Übung
      * OGC-Dienst erstellen 
      * Eigene OGC-Dienste mit QGIS-Server erstellen

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

2. Gehen wir zum Kartendienst. Öffne folgenden Link
   
   * /cgi-bin/qgis_mapserv.fcgi?MAP=/home/qgis/projects/world.qgs&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetMap&WIDTH=800&HEIGHT=400&LAYERS=airports,countries,countries_shapeburst,places&CRS=EPSG:4326&BBOX=-90,-180,90,180
   
   - Ändere die Parameter *&WIDTH=* und *&HEIGHT*. Was verändert sich?

.. codeblock::

   /cgi-bin/qgis_mapserv.fcgi?  <!-- unser QGIS-Server -->
   MAP=/home/qgis/projects/world.qgs <!-- navigation -->
   &SERVICE=WMS
   &VERSION=1.3.0
   &REQUEST=GetMap
   &WIDTH=800
   &HEIGHT=400
   &LAYERS=airports,countries,countries_shapeburst,places
   &CRS=EPSG:4326
   &BBOX=-90,-180,90,180


Layer selektion & Filter
~~~~~~~~~~~~~~~~~

3. Du kannst den existierenden Kartendienst nach deinen Wünschen anpassen, indem du nur einzelne Layer auswählst oder die Layer filterst.

.. codeblock::

   /cgi-bin/qgis_mapserv.fcgi?MAP=/home/qgis/projects/world.qgs

   &REQUEST=GetMap

   &SERVICE=WMS

   &VERSION=1.3.0

   &WIDTH=400

   &HEIGHT=300

   &CRS=EPSG:4326

   &BBOX=41,-6,52,10

   &LAYERS=countries_shapeburst,countries,places

   &FILTER=countries_shapeburst,countries:"name" = 'France';places: "name" = 'Paris'



.. hint::

   Weitere Möglichketien WMS-Dienste zu konfigurieren und abzufragen findest du in der `QGIS Dokumentation (englisch) <https://docs.qgis.org/3.40/en/docs/server_manual/services/wms.html#getmap>`__


GetFeatureInfo
~~~~~~~~~~~~~~~~~


kjh





Vorbereitung des eigenen WMS-Layers
~~~~~~~~~~~~~~~~~

Zu Beginn brauchen wir ein QGIS_Projekt, dass wir im Anschluss als WMS-Dienst veröffentlichen. Lade dir die Übungsdaten aus ILIAS herunter.
Suchen Sie zusätzlich einen WMS, den Sie schon kennen.

.. hint::

      Was läuft da im Hintergrund ab? 

      - QGIS verwaltet ein Projekt in der QGS/QGZ Datei, in der Vektor- und Rasterdaten sowie Dienste enthalten sein können. 
      - In den Properties / Eigenschaften ist eingestellt, dass das Projekt als OWS veröffentlicht werden soll. Änderungen im Projekt (*.qgz) müssen unter gleichem Namen gespeichert werden.

Die Veröffentlichung übernimmt der installierte QGIS Server zusammen mit dem QWC2 Client, sobald der Aufruf durch den Browser auf die URL stattfindet (request). Das machen Sie, indem Sie die vorher aufgerufene Seite im Browser aktualisieren.
Der Browser stellt daraufhin die geändert Karte dar.
Der Client ist auf dieses Projekt eingerichtet, deshalb können andere Projekte aus QGIS nicht im Browser als Karte dargestellt werden. Der QGIS Server würde dann als Antwort (response) eine XML Datei liefern.

Innerhalb dieser VM OSGEO live existiert ein komplettes System von Desktop-Programmen, Servern und Clients, die aufeinander abgestimmt sind. Es handelt sich um ein lokales System, in dem die Server-Client Beziehung simuliert wird.
In einer echten Remote Situation muss ein entfernter Server (oder mehrere) existieren, auf dem mindestens ein GIS Server läuft. Auf diesen Server wird von einer Benutzer:in eine Anfrage geschickt, von irgendwo (mit Internetverbindung natürlich). Der Server liefert dann eine Antwort zurück, die im Browser interpretiert wird.
Ohne einen zusätzlichen GIS Client (serverseitig) kann nur die XML Datei im Browser angezeigt werden.
Mit einem Client (Fat Client) wird die angefragte Kartenansicht im Browser angezeigt.



QGIS & QGIS-Server
~~~~~~~~~~~~~~~~~

1. GIS-Projekt zum Veröffentlichen vorbereiten

   - Öffnen Sie das vorbereitete GIS Projekt „Web_GIS_Praesenz_TN_2024.qgz oder Ihr eigenes QGZ Projekt.
   - Überprüfen Sie das CRS, im Projekt sollte das gleiche CRS definiert sein, wie in den Vektordaten.
   - Wenn der sf richtig funktioniert, können Sie die Vorbereitung entweder in Ihrem Windows mit QGIS oder auch im Gast- Linux mit QGIS machen!

.. hint::
   
   Jeder einzelne Layer eines WebGIS Projektes "sollte" in den Eigenschaften Angaben zu den Metadaten aufweisen. Metadaten können alternativ über eine URL angeben werden (ISO-Meta oder Dublin Core).
   Um die Layer eindeutig zu identifizieren, befüllen Sie „QGIS-Server“ den Kurznamen, den Titel und die Zusammenfassung (Kurz und prägnant).

2. QGIS-Server vorbereiten

   - Um unseren WMS-Layer via QGIS-Server zu veröffentlichen, müssen wir in den QGIS-Projekteigenschaften Angaben zum Layer/den Layern machen.
   - Nehmen Sie bei „Eigenschaften“ im Reiter „GIS_Server“ bzw. „OWS Server“ die genannten Einstellungen vor und setzen Sie den Haken bei „WMS Capabilities“. Verwenden Sie Ihre eigenen Namen und Angaben.
   - Sie sollten den enthaltenen WMS, den Sie selbständig hinzugefügt haben, von der Veröffentlichung ausschließen. Diesen können wir im Nachgang hinzuziehen.

.. hint::

   Vom Kleinen zum Großen. Kleine WMS-Layer entwickeln, testen, weiterentwickeln, testen usw. So schonen wir unsere Nerven und erhöhen die Wahrscheinlichkeiten auf eine erfolgreiche Veröffentlichgung.


3. Testen Sie Ihre Einstellungen und korrigieren Sie gegebenenfalls.

      - Welche Angaben könnten noch wichtig sein?
      - Speichern Sie das Projekt als WebGIS_IhrNachname.qgz im gleichen Verzeichnis ab, damit der Pfad zu den SHP-Daten erkannt wird.


4. WMS-Layer veröffentlichen

Es muss der exakte Aufruf des WMS in den Browser getippt werden. Verwenden Sie dazu den Link aus der Quickstart Anleitung zu QGIS Server:

http://localhost/cgi-bin/qgis_mapserv.fcgi?map=/home/user/world.qgz&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetMap&BBOX=-91.901820,-180.000000,83.633800,180.000000&CRS=EPSG:4326&WIDTH=722&HEIGHT=352&LAYERS=ne_10m_admin_0_countries&STYLES=default&FORMAT=image/png&DPI=96&TRANSPARENT=true

Ändern Sie den Aufruf (angepasst auf Ihren Ordner):

http://localhost/cgi-bin/qgis_mapserv.fcgi?map=/home/user/GIS/WEB_GIS/Dateiname.qgz&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetCapabilitiesmap=/home/user/GIS/WEB_GIS/Dateiname.qgz


Dieser Teil des „Request“ muss mit Ihrem Pfad ersetzt werden.
Mit diesem Request liefert der Browser eine XML Datei zurück. Das bedeutet der QGIS Server läuft und das Projekt wird gefunden.
Da QGIS Desktop ein Fat Client ist kann er diesen Aufruf als Karte darstellen. Fügen Sie diesen Dienst in QGIS als WMS hinzu.
Sie bekommen dadurch eine „Kopie“ Ihrer Layer, aber als WMS Layer.


2.5 	Fazit
Wenn Sie Ihre Daten nur innerhalb eines Spezialisten Teams veröffentlichen möchten, bei der alle ein Desktop-GIS verwenden, dann wären Sie zunächst mal fertig. 
Natürlich kann noch Vieles verfeinert werden. Auch das werden wir an diesem Wochenende noch üben.
Vermutlich soll dieser Dienst aber auch im Browser aufgerufen werden. Deshalb muss noch ein Client installiert werden, der das erledigt.
Damit beschäftigen wir uns in der  Übung zu LizMap.

Sie haben erste Schritte in einem UBUNTU Linux System als Virtuelle Maschine kennengelernt und kurz den QGIS Server mit QWC2 Client getestet.
Starten Sie den QGIS Server über „Geospatial – Web Services – QGIS Server“.  Falls das Fenster des Browser noch offen ist, aktualisieren Sie es.
Er startet voreingestellt mit dem originalen Natural Earth Projekt und benutzt den installierten QGIS Client QWC2. Deshalb kann im Browser die Karte dargestellt werden.
Ändern Sie im Desktop QGIS die Farbzusammenstellung der Originaldatei und speichern Sie das Projekt (keinen neuen Projektnamen vergeben)
Jetzt aktualisieren Sie den Browser-Aufruf. Die neue Farbzusammenstellung müsste erscheinen.

Suchen Sie einen WMS, den Sie schon kennen, beispielsweise einen der LUBW:
https://rips-gdi.lubw.baden-wuerttemberg.de/arcgis/services/wms/UIS_0100000001200001/MapServer/WMSServer?

Kopieren Sie die URL in die Zwischenablage und „importieren“ Sie den Dienst in die Karte im Browser.
Dazu öffnen Sie die Layers and Legend Anzeige und fügen Sie den Inhalt der Zwischenablage unten hinzu.
Dieser hinzugefügte Layer der NSG ist nur temporär für diese Sitzung sichtbar und nur für diejenigen, die ihn hinzugefügt haben.
Sollte der Layer dauerhaft und für alle Nutzer:innen sichtbar sein, muss er im Ursprungsprojekt hinzugefügt werden. Das erfordert Aufwand zur Administration innerhalb der 
VM und wird nicht vertieft.

Ende Februar 24 wurde ein PlugIn „QWC2 Tools“ veröffentlicht, der den komplizierten Prozess der Veröffentlichung wesentlich vereinfachen soll.
Leider reicht die Zeit bis zu den Präsenztagen nicht, um dieses Tool in die Übung zu intergrieren.
Versuchen Sie es selbst bei Gelegenheit.

2.2.1 	Anmerkung:  Was läuft da im Hintergrund ab?
QGIS verwaltet ein Projekt in der QGS/QGZ Datei, in der Vektor- und Rasterdaten sowie Dienste enthalten sein können. 
In den Properties / Eigenschaften ist eingestellt, dass das Projekt als OWS veröffentlicht werden soll. Änderungen im Projekt (*.qgz) müssen unter gleichem Namen gespeichert werden.
Die Veröffentlichung übernimmt der installierte QGIS Server zusammen mit dem QWC2 Client, sobald der Aufruf durch den Browser auf die URL stattfindet (request). Das machen Sie, indem Sie die vorher aufgerufene Seite im Browser aktualisieren.
Der Browser stellt daraufhin die geändert Karte dar.
Der Client ist auf dieses Projekt eingerichtet, deshalb können andere Projekte aus QGIS nicht im Browser als Karte dargestellt werden. Der QGIS Server würde dann als Antwort (response) eine XML Datei liefern.

Anmerkung
Innerhalb dieser VM OSGEO live existiert ein komplettes System von Desktop-Programmen, Servern und Clients, die aufeinander abgestimmt sind. Es handelt sich um ein lokales System, in dem die Server-Client Beziehung simuliert wird.
In einer echten Remote Situation muss ein entfernter Server (oder mehrere) existieren, auf dem mindestens ein GIS Server läuft. Auf diesen Server wird von einer Benutzer:in eine Anfrage geschickt, von irgendwo (mit Internetverbindung natürlich). Der Server liefert dann eine Antwort zurück, die im Browser interpretiert wird.
Ohne einen zusätzlichen GIS Client (serverseitig) kann nur die XML Datei im Browser angezeigt werden.
Mit einem Client (Fat Client) wird die angefragte Kartenansicht im Browser angezeigt.

2.2.2 	Arbeit mit QGIS und QGIS Server
Bei der Arbeit mit Virtuellen Maschinen arbeiten Sie mit „zwei Rechnern“, da die VM einen komplett virtualisierten Rechner enthält. Eine Verbindung kann über die Shared Folder / Gemeinsame Ordner hergestellt werden.
Wenn Shared Folder (sf) korrekt eingerichtet ist und dadurch auf Ihrem Windows Dateisystem ein oder mehrere Projekte verbunden wurden, kann es im Gast (Ubuntu Linux) mit QGIS geöffnet werden.
Sollte sf nicht richtig funktionieren, kopieren Sie das gesamte Projekt in die VM in den Ordner „User“.

2.3 	GIS-Karte zum Veröffentlichen vorbereiten
Öffnen Sie das vorbereitete GIS Projekt „Web_GIS_Praesenz_TN_2024.qgz oder Ihr eigenes QGZ Projekt.
Überprüfen Sie das CRS, im Projekt sollte das gleiche CRS definiert sein, wie in den Vektordaten.
Wenn der sf richtig funktioniert, können Sie die Vorbereitung entweder in Ihrem Windows mit QGIS oder auch im Gast- Linux mit QGIS machen!

Jeder einzelne Layer eines Web-GIS Projektes sollte in den Eigenschaften Angaben zu den Metadaten aufweisen. (Metadaten können aber auch extern über eine URL angeben werden.)
Um die Layer eindeutig zu identifizieren, schreiben Sie in den Eigenschaften bei „QGIS Server“ bei Kurzname, Titel und Zusammenfassung etwas hinzu.

2.3.1 	Als OWS vorbereiten
Für die Veröffentlichung müssen in den Projekteigenschaften ganz bestimmte Angaben gemacht werden, um dem GIS Server das Projekt bekannt zu machen.
Nehmen Sie bei „Eigenschaften“ im Reiter „GIS_Server“ bzw. „OWS Server“ die genannten Einstellungen vor und setzen Sie den Haken bei „WMS Capabilities“. Verwenden Sie Ihre eigenen Namen und Angaben.
Sie sollten den enthaltenen WMS FFH_Gebiet von der Veröffentlichung ausschließen. Nachträglich kann getestet werden, ob dieser auch funktioniert.

Testen Sie Ihre Einstellungen und korrigieren Sie gegebenenfalls.
Welche Angaben könnten noch wichtig sein?
Speichern Sie das Projekt als WebGIS_IhrNachname.qgz im gleichen Verzeichnis ab, damit der Pfad zu den SHP-Daten erkannt wird.

2.4 	Karte veröffentlichen in QGIS Server
Leider funktioniert auf dieser VM dieses Beispiel nicht, dasselbe hat in der OSGEOlive 14.
QGIS Server liest die Projektdatei QGZ und erstellt daraus einen Web-Dienst, ohne dass die dazugehörenden Daten angegeben werden müssen. Mit einem Browser als Thin Client kann dieser Dienst aufgerufen, aber nicht dargestellt werden. Als Antwort erhält der Browser eine XML Datei.
Zum Aufruf muss der Pfad zur QGZ-Datei im GetCapabilities Aufruf angegeben werden. Die QGZ Datei liegt in home/user/Pfad-_zu_Ihrem_Projekt.
Da mit derzeitigem Wissen der QWC2 Client nicht auf die neue Datei eingerichtet werden kann, können wir nur testen, ob QGIS Server korrekt arbeitet. Als Fat Client verwenden wir unser Desktop QGIS.

Es muss der exakte Aufruf des WMS in den Browser getippt werden. Verwenden Sie dazu den Link aus der Quickstart Anleitung zu QGIS Server:
http://localhost/cgi-bin/qgis_mapserv.fcgi?map=/home/user/world.qgz&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetMap&BBOX=-91.901820,-180.000000,83.633800,180.000000&CRS=EPSG:4326&WIDTH=722&HEIGHT=352&LAYERS=ne_10m_admin_0_countries&STYLES=default&FORMAT=image/png&DPI=96&TRANSPARENT=true

Ändern Sie den Aufruf (angepasst auf Ihren Ordner):
http://localhost/cgi-bin/qgis_mapserv.fcgi?map=/home/user/GIS/WEB_GIS/Dateiname.qgz&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetCapabilitiesmap=/home/user/GIS/WEB_GIS/Dateiname.qgz

Dieser Teil des „Request“ muss mit Ihrem Pfad ersetzt werden.
Mit diesem Request liefert der Browser eine XML Datei zurück. Das bedeutet der QGIS Server läuft und das Projekt wird gefunden.
Da QGIS Desktop ein Fat Client ist kann er diesen Aufruf als Karte darstellen. Fügen Sie diesen Dienst in QGIS als WMS hinzu.
Sie bekommen dadurch eine „Kopie“ Ihrer Layer, aber als WMS Layer.

Anmerkung:
Aktuell findet der QGIS Server das Projekt nicht, in der OSGEO Live 14 jedoch geht es. Vermutlich wurde bei der Entwicklung etwas vergessen!?
Da wir derzeit den QWC2 Client nicht verwenden, sondern später LizMap kennenlernen, wird dieser Prozess des Servertest dort durchgeführt.
Hier sollte nun soweit vorbereitet werden, dass jedes Projekt veröffentlicht werden kann. Dazu müssen vermutlich irgendwelche Config Dateien editiert werden:
https://gis.stackexchange.com/questions/438114/configuring-qwc2-web-client-in-production-environment-and-displaying-custom-map

2.5 	Fazit
Wenn Sie Ihre Daten nur innerhalb eines Spezialisten Teams veröffentlichen möchten, bei der alle ein Desktop-GIS verwenden, dann wären Sie zunächst mal fertig. Natürlich kann noch Vieles verfeinert werden. Auch das werden wir an diesem Wochenende noch üben.
Vermutlich soll dieser Dienst aber auch im Browser aufgerufen werden. Deshalb muss noch ein Client installiert werden, der das erledigt.
Damit beschäftigen wir uns in der  Übung zu LizMap.
Sie haben erste Schritte in einem UBUNTU Linux System als Virtuelle Maschine kennengelernt und kurz den QGIS Server mit QWC2 Client getestet.

OGC-Dienste lesen lernen
----------------
URL decodieren
Gibts eine Anleitung?
WMS Dienste

dann WMTS Dienste -> Unterschiede Vorteile?

WFS-Dienste inkl. Filterung

