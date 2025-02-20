Datenorganisation
=================

Im Rahmen der Aufgaben werden eine Vielzahl von Daten heruntergeladen. Eine ordentliche Verwaltung beugt nicht nur Fehlern und Komplikationen
vor, sondern schafft auch eine bessere Übersichtlichkeit in der ihr eure Daten schnell wiederfinden könnt.

Speicherort
-----------

Die GIS-Dateien sollten auf einem lokalen Speichermedium abgelegt werden, um schnelle Abläufe zu gewährleisten und Komplikationen zu
vermeiden. Vom Speichern der Daten in einem Cloud-Server wird abgeraten, da dies durch fehlerhafte Datenzugriffe eures GIS Programms zu
Fehlermeldungen oder einfrierenden Programmen führen kann (siehe dazu auch “Umlaute/Sonderzeichen/Leerzeichen in Dateipfaden” auf der Seite `Hinweise <Hinweise-Arbeiten-mit-GIS>`__).

Datenbenennung
--------------

Wie bereits in den `Hinweisen <Hinweise-Arbeiten-mit-GIS>`__ beschrieben, können bestimmte Schriftzeichen zu Fehlern in der
Verarbeitung von Daten durch euer GIS Programm führen. Sowohl der Dateipfad, unter dem die GIS-Daten gespeichert werden, als auch die
Namen der Daten selbst sollten daher keine Leerzeichen, Sonderzeichen oder Umlaute(ä,ö,ü) enthalten. Versucht zudem eure Datennamen kurz zu
halten. Zum einen werden dadurch Fehlerquellen reduziert. Zum Anderen muss für lange Datennamen die `Layers
List <http://giscience.courses-pages.gistools.geog.uni-heidelberg.de/qgis-book//content/karto/benutzeroberfläche/GUI>`__
verbreitert werden, um den vollständigen Namen lesen zu können. Dies reduziert die Größe der
`Kartenansicht <http://giscience.courses-pages.gistools.geog.uni-heidelberg.de/qgis-book//content/karto//benutzeroberfläche/GUI>`__
und somit die Übersichtlichkeit beim Arbeiten im GIS Programm (siehe dazu auch “Umlaute/Sonderzeichen/Leerzeichen in Dateipfaden” auf der
Seite `Hinweise <Hinweise-Arbeiten-mit-GIS>`__).

Ordnerstruktur
--------------

Eine gute und übersichtliche Ordnerstruktur erleichtert das Arbeiten mit GIS Programmen enorm. Legt euch daher am besten noch vor dem ersten
Tutorium Ordner für die Dateien an, mit denen ihr im Laufe des Semesters arbeiten werdet. Achtet darauf die Dateipfade nicht zu lang werden zu
lassen, um Komplikationen zu vermeiden. Wir empfehlen dabei folgende Struktur:

Dokumente/studium/geo/gis/ex0/

In diesem Ordner dann jeweils Unterordner input, interim und output (keine Umlaute) in denen ihr jeweils alle benötigten Daten speichern könnt.

Im Rahmen der Kartographie Übung werden neben den Eingangsdaten, die in diesem GitLab Repository verfügbar sind und runtergeladen werden sollen
eigentlich nur die QGIS Projektdateien eine Rolle spielen. Um die sich eine saubere Struktur anzugewöhnen ist die Empfehlung trotzdem, Daten
und Projektdateien in separten Ordnern *daten/* und *projekte/* abzulegen.

Somit würde der Teil des Dateisystems für die Übung z.B. wie folgt aussehen:

.. figure:: https://courses.gistools.geog.uni-heidelberg.de/giscience/kartographie_uebung/-/wikis/uploads/img/datenorgaTree.png
   :alt: Screenshot_from_2021-08-13_08-43-20

   Screenshot_from_2021-08-13_08-43-20

**Hinweis:** Achtet bei der Ordnerstruktur darauf diese nachträglich möglichst nicht mehr zu verändern. Ansonsten kann es wie
`hier <http://giscience.courses-pages.gistools.geog.uni-heidelberg.de/qgis-book//content/karto/benutzeroberfläche/GUI>`__
beschrieben zu Problemen beim Öffnen alter Projektdateien kommen, die dann in mühseliger Kleinstarbeit manuell wieder repariert werden müssen
oder unbrauchbar geworden sind. Macht euch also wirklich vor dem Bearbeiten der ersten Aufgaben bereits darüber Gedanken welche Ordner
ihr im Verlauf des Semesters benötigen werdet und wo ihr diese anlegen wollt.
