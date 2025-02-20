Übung 2
==========

.. hint::

   Ziel der Übung
      * Die ersten Schritte zum Webmapping
      * Die Benutzeroberfläche von qgis2web kennenlernen

.. note::

   **Für diese Übung nutzen wir folgende Tools**
      *  `QGIS <https://qgis.org/>`__
      *  `Plugin *qgis2web* <https://plugins.qgis.org/plugins/qgis2web/>`__
      *  `QGIS Cloud <https://qgiscloud.com/de/pages/quickstart>`__
   

Aufgaben - HTML, CSS & JavaScript
===========

Die Basics
--------

Für den Erstkontakt von HTML, CSS & JavaScript nutzen wir die `w3school <https://www.w3schools.com/>`__
- Grundgerüst: Öffne den Link zu `HTML Intro <https://www.w3schools.com/html/tryit.asp?filename=tryhtml_intro>`__
   * **Verändere** den *Page Title* und den *My first paragraph* und 
   * klicke auf **Run**

- Sytling: Öffne den Link zu `HTML CSS <https://www.w3schools.com/html/tryit.asp?filename=tryhtml_css_fonts>`__
   * **Verändere** den *Page Title* und den *My first paragraph* und 
   * klicke auf **Run**

- Öffne den Link zu `HTML JavaScript <https://www.w3schools.com/html/tryit.asp?filename=tryhtml_script_html>`__
   * **Verändere** den *Click Me!* und klicke auf **Run**
   * Passe den Coode wie folgt an und lasse es erneut runnen

.. code-block:: javascript
  :linenos:

   <script>
   function myFunction() {
   document.getElementById("demo").innerHTML = "Hello JavaScript!";
   }
   </script>


- Neu

Für die Erstellung von Internetseiten brauchen Sie keine spezielle Software. Es reicht ein einfacher Editor, bei Windows ist einer dabei. Besser wäre ein weiter entwickelter Editor, 
wie NotePad++, der mit Code auch grafisch umgehen kann. Zunächst genügt der Editor von Windows.
Rechtsklick auf die Datei – Öffnen mit… - Editor
Die Seite wird nur aus HTML-Code bestehen. Lesen Sie dazu folgende Einstiegsseiten:
https://wiki.selfhtml.org/wiki/HTML/Tutorials/Einstieg


Fertig!
Das ist die Idee dahinter. Sie müssen natürlich entsprechende Regeln beachten, d.h Sie müssen richtigen HTML-Code schreiben.
Auf der Seite SelfHTML stehen die Zeilen so, wie Sie vom Browser interpretiert werden kön-nen:
https://wiki.selfhtml.org/
https://wiki.selfhtml.org/wiki/HTML/Tutorials/Grundger%C3%BCst#Kopiervorlage_f.C3.BCr_ganz_Ungeduldige
Erstellen Sie eine einfache Datei mit dem Code für eine Überschrift und mit etwas Text. Die¬se Datei speichern Sie aus dem Editor heraus unter einem Namen der die Endung .html hat.
Speichern Sie in einem neuen leeren Ordner.
Dann Doppelklicken Sie im Dateimanager auf diese HTML. Wenn alles richtig ist, öffnet sich eine Internetseite in Ihrem Browser. Falls im Browser nicht das erwartete Ergebnis erscheint, muss eine Fehleranalyse gemacht werden.
Sie können Ihre Arbeit auch online testen:
https://www.w3schools.com/html/tryit.asp?filename=tryhtml_intro
Unter dieser Internetadresse finden Sie einen Online Editor, der für kleine Aufgaben hilfreich ist.



.. note::

   Tip: Mit einem Style Sheet (.css) kannst du das Aussehen deiner ganzen Webseite bearbeiten. Alles in nur einer Datei!




.. raw:: html

   <iframe width="100%" src="https://www.w3schools.com/html/tryit.asp?filename=tryhtml_intro">

.. raw:: html

   </iframe>



old
---------

Mit dem Plugin *qgis2web* lassen sich schnell und einfach interaktive Webmaps erstellen. Dafür brauchen wir ein QGIS-Projekt mit einigen Layern:
-	Starte QGIS
-	Lade dir die Daten `„uebung_1_13.zip“ aus ILIAS <https://lms-ubinfo.uni-tuebingen.de/ilias3/ilias.php?baseClass=ilrepositorygui&ref_id=37653>`__ herunter
-	Öffne das QGIS-Projekt
      *	Füge mind. einen WMS oder WMTS-Layer hinzu
      *	OpenStreetMap 
      *	Digitales Orthophotos
      *	Installiere das Plugin *qgis2web* 

.. figure:: img/qgis2web.png
   :alt: QGIS-Plugin *qgis2web*
   :width: 800px

   QGIS-Plugin *qgis2web*


-	Öffne das Plugin *qgis2web*  

.. figure:: img/qgis2web_logo.png
   :alt: *qgis2web* Logo
   :width: 150px

   Logo *qgis2web*

- Passe zwei Popup Fields zu *inline Label - always visible* an

.. figure:: img/qgis2web_screenshot_ol_v2.PNG
   :alt: *qgis2web* Menü
   :width: 150px

   Menü *qgis2web*

-	Exportiere deine WebMap 

.. figure:: img/export.png
   :alt: *qgis2web* Export
   :width: 150px

   Export *qgis2web*

- Eine Browser-Tab sollte sich öffnen & die Karte anzeigen.

**So (oder ähnlich) kann deine erste Webmap aussehen**


.. figure:: img/qgis2web_screenshot_map.PNG
   :alt: *qgis2web* Webmap
   :width: 800px

   Webmap *qgis2web*


Gratulation! Deine erste Webmap ist fertig! 
