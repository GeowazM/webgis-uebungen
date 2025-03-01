WMS erstellen
==========

.. hint::

   Ziel der Übung
      * OGC-Dienst erstellen 
      * Eigene OGC-Dienste mit QGIS-Server erstellen

.. seealso::

      *  `OGC <https://www.ogc.org/de/>`__
      *  `QGIS Server <https://docs.qgis.org/3.34/en/docs/server_manual/index.html>`__
      *  `OGC-Dienste - Basics <https://docs.qgis.org/3.40/en/docs/server_manual/services/basics.html>`__


.. hint::

   Hier ist die Seite der `Firma Terrestris <https://www.terrestris.de/de/openstreetmap-wms/>`__, die mehrere eigene WMS-Dienste anbieten. So kann die Bereitstellung deiner OGC-Dienste irgendwann auch aussehen. 




Eigenen OGC-Dienst konfigurieren
-----------

Um einen neuen QGIS Server WMS, WFS, OAPIF oder WCS bereitzustellen, müssen Sie eine QGIS-Projektdatei mit einigen Daten erstellen oder eines Ihrer aktuellen Projekte verwenden. 
Definieren Sie die Farben und Stile der Layer in QGIS und das Projekt-CRS, falls noch nicht definiert. Gehen Sie dann zum *QGIS-Server* Menü im Dialogfeld *Projekt ► Eigenschaften…* und geben 
Sie im Tab *Service Capabilities* einige Informationen über den OWS an.


.. figure:: https://docs.qgis.org/3.40/en/_images/ows_server_definition.png
   :alt: QGIS-Server Plugin

   *Service Capabilities* definieren, Quelle: `QGIS Dokumentation <https://docs.qgis.org/3.40/en/docs/server_manual/getting_started.html#serve-a-project>`__


Sie müssen zuerst die *Service Capabilities* aktivieren, falls sie deaktiviert sind. Dies wird in der GetCapabilities-Antwort des WMS, WFS oder WCS erscheinen. Wenn Sie das Kontrollkästchen 
Dienstfähigkeiten aktivieren nicht aktivieren, verwendet QGIS Server die Informationen aus der Datei wms_metadata.xml im cgi-bin-Ordner.


Eigenen WMS-Dienst definieren
-----------
Im WMS-Tab können Sie die Optionen für die WMS-Fähigkeiten definieren.


.. figure:: https://docs.qgis.org/3.40/en/_images/ows_server_wms.png
   :alt: QGIS-Server Plugin - WMS

   *WMS* definieren, Quelle: `QGIS Dokumentation <https://docs.qgis.org/3.40/en/docs/server_manual/getting_started.html#serve-a-project>`__


Extent (Bbox)
^^^^^^^^

Aktivieren Sie *Extent*, um die räumliche Ausdehnung (eng. bounding box oder bbox) zu definieren, der in der WMS GetCapabilities-Antwort angegeben wird. Das räumliche Auswahl-Widget hilft Ihnen, 
die Ausdehnung (*Extent*) als xmin, xmax, ymin, ymax Text einzugeben oder ihn aus der Kartenansicht, Layern, Lesezeichen usw. auszuwählen.

CRS
^^^^

Durch Aktivieren des Kontrollkästchens CRS-Einschränkungen können Sie einschränken, in welchen Koordinatenreferenzsystemen (CRS) QGIS-Server Karten rendern wird. 
Es wird empfohlen, die angebotenen CRS einzuschränken, da dies die Größe der WMS GetCapabilities-Antwort reduziert. Verwenden Sie die Schaltfläche Symbologie hinzufügen unten, 
um diese CRS aus dem Koordinatenreferenzsystem-Auswahlfenster auszuwählen, oder klicken Sie auf Verwendet, um die im QGIS-Projekt verwendeten CRS zur Liste hinzuzufügen.

Wenn Sie Drucklayouts in Ihrem Projekt definiert haben, werden diese in der GetProjectSettings-Antwort aufgelistet und können von der GetPrint-Anfrage verwendet werden, 
um Drucke zu erstellen, wobei eines der Drucklayouts als Vorlage verwendet wird. Dies ist eine QGIS-spezifische Erweiterung der WMS 1.3.0-Spezifikation. 
Wenn Sie ein Drucklayout von der Veröffentlichung durch den WMS ausschließen möchten, aktivieren Sie das Kontrollkästchen Layouts ausschließen und klicken Sie auf die Schaltfläche 
Symbologie hinzufügen unten. Wählen Sie dann ein Drucklayout aus dem Dialogfeld Drucklayout auswählen aus, um es zur Liste der ausgeschlossenen Layouts hinzuzufügen.

Wenn Sie eine Ebene oder eine Layergruppe von der Veröffentlichung durch den WMS ausschließen möchten, aktivieren Sie das Kontrollkästchen Ebenen ausschließen und klicken Sie auf die Schaltfläche Symbologie hinzufügen unten. Dies öffnet das Dialogfeld Eingeschränkte Ebenen und Gruppen auswählen, in dem Sie die Ebenen und Gruppen auswählen können, die Sie nicht veröffentlichen möchten. Verwenden Sie die Umschalt- oder Strg-Taste, wenn Sie mehrere Einträge auswählen möchten. Es wird empfohlen, die Ebenen, die Sie nicht benötigen, von der Veröffentlichung auszuschließen, da dies die Größe der WMS GetCapabilities-Antwort reduziert, was zu schnelleren Ladezeiten auf der Clientseite führt.

Layer- und Feature-Optionen
^^^^^^

Sie können die angeforderten GetFeatureInfo-Daten als Klartext, XML und GML erhalten. Der Standard ist XML.

Wenn Sie das Kontrollkästchen Layer-IDs als Namen verwenden aktivieren, werden Layer-IDs verwendet, um Layer in der GetCapabilities-Antwort oder im GetMap LAYERS-Parameter zu referenzieren. 
Andernfalls wird der Layername oder der Kurzname, falls definiert (siehe QGIS Server-Eigenschaften), verwendet.

Wenn Sie möchten, können Sie das Kontrollkästchen Geometrie zur Feature-Antwort hinzufügen aktivieren. Dies wird den Extent für jedes Feature in der GetFeatureInfo-Antwort enthalten. 
Siehe auch den WITH_GEOMETRY-Parameter.

Da viele Webclients keine Kreisbögen in Geometrien anzeigen können, haben Sie die Möglichkeit, die Geometrie vor dem Senden an den Client in einer GetFeatureInfo-Antwort zu segmentieren. 
Dies ermöglicht es solchen Clients, die Geometrie eines Features dennoch anzuzeigen (z.B. zum Hervorheben des Features). Sie müssen das Kontrollkästchen Geometrie der Feature-Info segmentieren aktivieren, 
um die Option zu aktivieren.

Sie können auch die Option GetFeatureInfo-Geometriepräzision verwenden, um die Präzision der GetFeatureInfo-Geometrie festzulegen. Dies ermöglicht es Ihnen, Bandbreite zu sparen, wenn Sie nicht die volle Präzision benötigen.

Wenn eine Ihrer Ebenen die Map Tip-Anzeige verwendet (d.h. um Text mit Ausdrücken anzuzeigen), wird dies im GetFeatureInfo-Ausgang aufgelistet. Wenn die Ebene eine Wertkarte für eines ihrer Attribute verwendet, wird diese Information ebenfalls im GetFeatureInfo-Ausgang angezeigt.

Wenn Sie möchten, dass QGIS-Server spezifische Anforderungs-URLs in der WMS GetCapabilities-Antwort bewirbt, geben Sie die entsprechende URL im Feld Beworbene URL ein.


Legende
^^^^^^

Wenn eine Layergruppe an die GetLegendGraphic-Anfrage übergeben wird, werden alle ihre Blattebenen dem Legendenbild hinzugefügt. Aktivieren Sie das Kontrollkästchen Layergruppen in 
GetLegendGraphic hinzufügen, wenn Sie auch die Namen der Layergruppen (und Untergruppen) in den Layerbaum einfügen möchten, genau wie in der QGIS Desktop-Legende.

Darüber hinaus können Sie die maximale Größe der Karten, die von den Anfragen zurückgegeben werden, einschränken, indem Sie die maximale Breite und Höhe in die entsprechenden 
Felder unter Maximale Bildgröße für GetMap- und GetLegendGraphic-Anfragen eingeben.

Sie können den Qualitätsfaktor für JPEG- und WebP-Bilder ändern. Der Qualitätsfaktor muss im Bereich von 0 bis 100 liegen. 
Geben Sie 0 für maximale Kompression und 100 für keine Kompression an.

.. hint::

   Je nachdem, ob die Karte ein projiziertes CRS oder ein geografisches CRS verwendet und ob keine Informationen zur Bewertung der Karteneinheitengröße vorliegen, 
   können Sie eine Referenz für die Größe entweder durch eine Standardskala für die Legende oder durch Standardkarteneinheiten pro mm in der Legende angeben.




Standardparameter

+---------+---------------------------+-----------------------------+
| Konzept | Beschreibung              | Beispiel                    |
+=========+===========================+=============================+
| SERVICE | Name des Dienstes         | SERVICE=WMS                 |
+---------+---------------------------+-----------------------------+
| REQUEST | Name der Anfrage          | REQUEST=GetCapabilities     | 
+---------+---------------------------+-----------------------------+

