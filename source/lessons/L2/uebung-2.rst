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
   

HTML, CSS & JavaScript
===========

**Für den Erstkontakt zu HTML, CSS & JavaScript nutzen wir die Seite der** `w3school <https://www.w3schools.com/>`__. Für die Erstellung von Internetseiten brauchen Sie keine spezielle Software.
Später werdem wir `Visual Studio Code <https://code.visualstudio.com/>`__ als Integrierte Entwicklungsumgebung (IDE) nutzen.

- Das HTML Grundgerüst 
   * Öffne den Link zu `HTML Intro <https://www.w3schools.com/html/tryit.asp?filename=tryhtml_intro>`__
   * **Verändere** den *Page Title* und den *My first paragraph* und 
   * klicke auf **Run**

- Das Sytling einer HTML Seite 
   * `HTML CSS <https://www.w3schools.com/html/tryit.asp?filename=tryhtml_css_fonts>`__
   * **Verändere** die Farbe von ``color: blue;`` zu ``color: green`` und 
   * die Schriftart von ``font-family: verdana;`` zu ``font-family: arial``
   * klicke auf **Run**

.. hint::

   Tipp: Mit einem Style Sheet (.css) kannst du das Aussehen deiner ganzen Webseite bearbeiten. Alles in nur einer Datei!

- Die Interaktion mit einer HTML Seite 
   * Öffne den Link zu `HTML JavaScript <https://www.w3schools.com/html/tryit.asp?filename=tryhtml_script_html>`__
   * **Verändere** den *Click Me!* und klicke auf **Run**
   * Passe den Coode wie folgt an und lasse es erneut runnen

.. code-block::

   // Code
   <script>
      function myFunction() {
      document.getElementById("demo").innerHTML = "Hello JavaScript!";
      }
   </script>

.. code-block::

   // Neuer Code
   <script>
      function myFunction() {
      document.getElementById("demo").innerHTML = "Download Bebauungsplan!";
      }
   </script>

Du hast die Basics HTML, CSS & JavaScript kennengelernt!
   * HTMl = Grundgerüst
   * CSS = Sytling
   * JavaScript = Interaktionen


.. figure:: img/code-1076536_1280.jpg
   :alt: Code 
   :width: 800px

   Code


.. figure:: https://v1.scrimba.com/articles/content/images/size/w1000/2022/11/image-1.png
   :alt: Karte von Osnabrück

   How HTML, CSS, JavaScript work; Quelle: `Jaye H @ Scrimba <https://v1.scrimba.com/articles/html-css-javascript/>`__