Passive Fernerkundung
===============

Was ist Fernerkundung?
===============

Fernerkundung ist die Wissenschaft und Technik, Informationen über Objekte oder Phänomene auf der Erdoberfläche zu sammeln, ohne direkten Kontakt 
mit ihnen zu haben. Dies geschieht hauptsächlich durch die Erfassung und Analyse von Daten, die von Satelliten, Flugzeugen oder Drohnen aufgenommen werden.
Informationen zur DIN Norm können Sie `hier <https://www.dgpf.de/src/tagung/jt2017/proceedings/proceedings/papers/27_DGPF2017_Baltrusch_Reulke.pdf>`_ finden. 

.. figure:: https://fe-lexikon.info/bild/active_passive_sensors.jpg
   :alt: Active und passive Sensoren

   Baldenhofer, K.G.: `Lexikon der Fernerkundung <https://fe-lexikon.info/Fernerkundung.htm>`_

Was ist passive Fernerkundung?
--------------

Passive Fernerkundung nutzt Sensoren, die die natürliche Strahlung der Erde erfassen. Diese Strahlung kann entweder von der Sonne reflektiert oder von der Erdoberfläche selbst emittiert werden. 
Beispiele für passive Sensoren sind Multispektralkameras und Wärmebildkameras. Passive Sensoren benötigen keine eigene Energiequelle zur Aussendung von Strahlung, da sie die vorhandene Strahlung nutzen.

Anwedungsbeispiele
--------------
Beispiele für den Einsatz der Fernerkundung findest du bei den `Sentinel Success Stories <https://sentinel.esa.int/web/success-stories/list>`_


Wichtige passive Erdbeobachtungsmissionen
===============

Landsat 8 & 9
--------------

Landsat 8, gestartet im Jahr 2013, ist mit zwei Hauptinstrumenten ausgestattet: dem Operational Land Imager (OLI) und dem Thermal Infrared Sensor (TIRS). 
OLI erfasst Daten in neun Spektralbändern, einschließlich eines panchromatischen Bands mit 15 m Auflösung, während TIRS die Landoberflächentemperatur in 
zwei thermischen Bändern misst. Landsat 8 bietet eine räumliche Auflösung von 30 m für multispektrale und 100 m für thermische Daten und hat eine 
Schwadbreite von 185 km. Die Daten werden alle 16 Tage wiederholt erfasst.

Das Landsat Programm läuft seit 1972 und über den USGS EarthExplorer können Fernerkundungsdaten bis in diese Zeit zurück bezogen werden. Der Landsat 9 ist der aktuelleste 
Satellite dieser Serie und führt die Landsat Legacy fort.

.. admonition:: Landsat 9: Continuing the Legacy
    :class: admonition-youtube

    ..  youtube:: k3biSynSBgo

    `NASA Goddard on Youtube <https://www.youtube.com/watch?v=k3biSynSBgo>`_

Sentinel-2
--------------

Die Sentinel-2 Mission besteht aus zwei identischen Satelliten, die in einer sonnensynchronen Umlaufbahn operieren. 
Sie liefern hochauflösende multispektrale Bilder mit einer Schwadbreite von 290 km und einer Wiederholrate von 5 Tagen am Äquator. 
Die Satelliten sind mit einem optischen Instrument ausgestattet, das 13 Spektralbänder abdeckt, darunter vier Bänder mit 10 m, sechs Bänder mit 20 m und drei Bänder mit 60 m räumlicher Auflösung. 
Diese Daten unterstützen Anwendungen in der Landüberwachung, Landwirtschaft, Notfallmanagement und mehr.

.. admonition:: 25 years of Copernicus
    :class: admonition-youtube

    ..  youtube:: vyoXKUuAf5E

    European Space Agency @ `ESA on Youtube <https://www.youtube.com/watch?v=vyoXKUuAf5E>`_

Wie funktioniert Fernerkundung?
===============

Elektromagnetische Strahlung
--------------

Elektromagnetische Strahlung umfasst ein breites Spektrum von Wellenlängen, von Gammastrahlen bis zu Radiowellen. In der Fernerkundung werden hauptsächlich 
sichtbares Licht, Infrarot und Mikrowellen genutzt. Diese Strahlung wird von der Erdoberfläche reflektiert oder emittiert und von Satellitensensoren erfasst.

.. figure:: https://www.geospektiv.de/assets/unit/M8mXK9lm/modul_biodiversitaet_startseite_1.png
   :alt: Sentinel-2 Aufnahme (Echtfarbe, Falschfarbe & NDVI) von Heidelberg

   Sentinel-2 Aufnahme (Echtfarbe, Falschfarbe & NDVI) von Heidelberg. Quelle: Eigene Erhebung, ESA Sentinel-2 Daten, rgeo.

Räumliche Auflösung
--------------

Ein Satellitenbild besteht aus einzelnen Pixeln. Jedes Pixel beinhaltet die Reflektionswerte für die vom Sensor definierten Bereiche der elektromagnetischen Strahlung (Bänder oder Kanäle genannt). 
Jedes Pixel kann in einer Farbe (Rot, Grün oder Blau) eingefärbt & dargestellt werden, so entstehen aus Millionen einzelner Pixel Bilder der Erdoberfläche. 
Ein Pixel eines Sentinel-2 Satellitenbildes repräsentiert in Wirklichkeit eine Fläche von 10 x 10 Metern. Zoomst du zu nah heran, wird das Bild deshalb unscharf.

.. figure:: https://www.geospektiv.de/assets/unit/PAow6aAv/schwetzi_resolution_v4.png
   :alt: Sentinel-2 Aufnahme (Echtfarbe, Falschfarbe & NDVI) von Heidelberg

   Unterschiedliche Zoomstufen - Räumliche Auflösung eines Sentinel-2 Satellitenbildes – 1 Pixel repräsentiert eine Fläche von 10 x 10 Metern. Quelle: rgeo - PH Heidelberg.

Spektrale Auflösung
--------------

Die spektrale Auflösung bezieht sich auf die Fähigkeit eines Sensors, verschiedene Wellenlängen des elektromagnetischen Spektrums zu unterscheiden. 
Ein Sensor mit hoher spektraler Auflösung kann schmalere Wellenlängenbereiche erfassen und somit detailliertere Informationen über die Erdoberfläche liefern. 
Dies ist besonders nützlich für die Identifizierung und Analyse spezifischer Materialien oder Vegetationstypen.
Beim Falschfarbenbild 8-4-3 werden dem roten Kanal die Reflexionswerte des nahen Infrarot (NIR) zugewiesen, dem grünen Kanal die des roten Lichts und dem blauen Kanal die des grünen Lichts. 
Deshalb sehen Landbedeckungen / Landnutzungen im Falschfarbenbild 8-4-3 etwas anders aus. Wald, der im Echtfarbenbild grün erscheint, wird im Falschfarbenbild rötlich dargestellt und tritt, wie Vegetation insgesamt, 
besser hervor. Beton reflektiert Strahlung anders als Erde, anders als Wasser und anders als Pflanzen. Durch diese Rückstrahlungsunterschiede haben diese Flächen für uns alle eine andere Farbe. 
Folglich sehen sie auch im Echtfarbensatellitenbild unterschiedlich aus. Im infraroten Bereich gilt das gleiche, weshalb manche Objekte plötzlich eine ähnliche und manche unterschiedliche Farben erhalten.


Zeitliche Auflösung
--------------
Die zeitliche Auflösung in der passiven Fernerkundung beschreibt, wie oft ein Sensor Daten von derselben Stelle auf der Erdoberfläche erfassen kann. Diese Auflösung hängt von der Umlaufbahn des Satelliten und dem Sensordesign ab. 
Zum Beispiel hat der MODIS-Sensor eine zeitliche Auflösung von 1-2 Tagen. Das bedeutet, dass er die Erde alle 1-2 Tage vollständig abbilden kann, was uns ermöglicht, Veränderungen auf der Erdoberfläche nahezu in Echtzeit zu beobachten.


.. admonition:: Introducing the Copernicus Data Space Ecosystem
    :class: admonition-youtube

    ..  youtube:: _1r7Ki4IaVA

    European Space Agency @ `ESA on Youtube <https://www.youtube.com/watch?v=vyoXKUuAf5E>`_.

.. admonition:: HOW TO DOWNLOAD LANDSAT 8 IMAGE FROM USGS EARTH EXPLORER WEBSITE
    :class: admonition-youtube

    ..  youtube:: kk4z6f30NFg&t=2s

    European Space Agency @ `ESA on Youtube <https://www.youtube.com/watch?v=kk4z6f30NFg&t=2s>`_.
