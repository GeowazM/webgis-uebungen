Rahmen vorbereiten
==========

.. hint::

   Ziel der Übung
      * Erste Einblicke in *Visual Studio Code* 
      * Die Extension *Live Server* kennenlernen

.. seealso::

      *  `Visual Studio Code <https://code.visualstudio.com/>`__
      *  `Live Server <https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer>`__


Masterportal
~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   <video width="100%" controls src="https://www.masterportal.org/fileadmin/content/videos/Video_1_Masterportal_Vorstellung.mp4">

.. raw:: html

   </video>

Quelle: `Masterportal <https://www.masterportal.org/media/videos>`__


Schritt für Schritt Richtung eigenes WebGIS
===========
Um ein eigenes WebGIS mit Masterportal zu erstellen, gehen wir in drei Schritten vor. Zuerst bereiten wir alle Informationen vor, die wir für unser Untersuchungsgebiet benötigen. 
Im Anschluss bereiten wir unsere Entwicklungsumgebung vor. Dann werden wir die Karte, die Werkzeuge, den Footer und das Logo anpassen. 


Vorbereitung
~~~~~~~~~~~~~~~~~~~~~~

Installiere dier die Extension *Live Server* (falls noch nicht geschehen)


.. figure:: img/vs_code_live_server.PNG
   :alt: Visual Studio Code
   :width: 450px

   `Visual Studio Extension Live Server <https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer>`__


1. Nutze die Geodaten bzw. das QGIS-Projekt von Aufgabe 2 und speichere es erneut ab.
2. Extrahiere aus der Gemarkung Tübingens die *Layerausdehnung* deiner Region
3. Lass dir den *Zentroid* der Gemarkung Tübingen ausgeben.
4. Notiere dir die Koordinaten der *Layerausdehnung* & des *Zentroids*
5. Reprojiziere die Koordinaten der *Layerausdehnung* in WGS 84 - WGC. Notiere dir die Koordinaten ebenfalls
6. Lade dir drei WMS-Layer für deine Region (bspw.: 1x Schummerung, 1x Orthophoto, 1x basemap.de)
7. Speichere dein Projekt & lasse dein QGIS-Projekt geöffnet

.. figure:: img/qgis-projekt.PNG
   :alt: QGIS-Projekt mit *Layerausdehnung* oder & *Zentroid*
   :width: 800px

   QGIS-Projekt mit *Layerausdehnung* oder *Zentroid*



Masterportal herunterladen & einbinden
~~~~~~~~~~~~~~~~~~~~~~


1. Lade dir das `Masterportal example (examples-3.3.4-lts.zip) <https://bitbucket.org/geowerkstatt-hamburg/masterportal/downloads/>`__ herunter & enzippe den Ordner an einer für dich geeigneten Stelle.
2. Innerhalb des Masterportal_example Ordners findest du einen Ordner *Basic*. Kopiere diesen und bennene ihn passend zu deinem Untersuchungsgebiet um (bspw. uni-tuebingen).

3. Öffne dein Masterportal example (bspw. uni-tuebingen) Ordner in Visual Studio Code

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

   Der Ordner Basic dient als Backup

.. figure:: img/masterportal_folder_order.PNG
   :alt: Masterportal in Visual Studio Code
   :width: 400px

   Masterportal Ordnerstruktur in Visual Studio

4. Öffne die *index.html* Datei

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

   Durch einfaches anklicken der *index.html*


5. So (oder so ähnlich) sollte dein Visual Studio Code jetzt aussehen
 
.. figure:: img/masterportal_index_html.PNG
   :alt: Masterportal in Visual Studio Code
   :width: 800px

   Masterportal *index.html* in Visual Studio

6. Starte mit dem *Live Server* die *index.html* Datei

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

   Rechtsklick in die *index.html* und dann **Open with Live Server** wählen

.. figure:: img/masterportal_vs_live_server_v2.PNG
   :alt: Masterportal in Visual Studio Code
   :width: 800px

   Masterportal *index.html* in Visual Studio


Gratulation! Du hast das Masterportal erfolgreich heruntergeladen, in Visual Studio Code geöffnet & die notwendigen Parameter in QGIS berechnet.
Jetzt kannst du mit der Entwicklung deines eigenen Masterportals beginnen (siehe Geoviewer konfigurieren)!
