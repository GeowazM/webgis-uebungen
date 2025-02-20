Exercise 8
=======

.. note::
   
   Ziel der Übung
      - Räumliche Interpolation anwenden
      - Rasterfunktionen vertiefen

.. hint::

      -  `Räumliche Interpolationsverfahren <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Räumliche-Interpolationsverfahren>`__
      -  `lokale Rasterfunktionen <https://courses.gistools.geog.uni-heidelberg.de/giscience/gis-einfuehrung/wikis/qgis-Konvertierung>`__

.. seealso::

   Daten
      - Lade dir `die Daten herunter <https://drive.google.com/file/d/1LRswuG792SCZF1e50aCnRTwc5VMiyN0K/view?usp=drive_link>`__ und speichert sie auf eurem PC. Lege einen lokalen Ordner an und speichere dort die obigen Daten. (.zip Ordner müssen vorher entpackt werden.) 
      - Höhenmodell - germany_dem.tif (Quelle: `GTOPO30 USGS <https://www.usgs.gov/centers/eros/science/usgs-eros-archive-digital-elevation-global-30-arc-second-elevation-gtopo30?qt-science_center_objects=0#qt-science_center_objects>`__)
      - Messstationen `DWD <%5Bhttps://www.geo.fu-berlin.de/en/v/soga/Geodata-analysis/geostatistics/Data-sets-used/DWD-weather-data-Germany/index.html%5D(https://www.dwd.de/DE/leistungen/cdc/climate-data-center.html;jsessionid=19070115479E2AED22A5D5D622F8CA58.live31083?nn=17626)>`__

Aufgaben
--------

Aufgabe 1: Vorbereitung
~~~~~~~~~~~~~~~~~~~~~~~

-  Bringe die Daten in ein geeignetes Koordinatensystem.

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

   ``germany_dem`` -> Funktion Warp (Reproject), Ziel-KBS “EPSG: 25832 - ETRS 84 / UTM zone 32N”

   .. raw:: html

      <li>

   ``temp_stations`` -> Funktion “Reproject layer”, Ziel-KBS “EPSG: 25832 - ETRS 89 / UTM zone 32N”

   .. raw:: html

      </ul>

   .. raw:: html

      </details>

-  Selektiere die Stationen mit einer gültigen Höhenangabe.

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

   Werfe einen Blick in die Attributtabelle des ``temp_stations``-Layers; Höhenangabe in der Spalte “ELEV”; NoData-Value entspricht dem Wert -999.

   .. raw:: html

      <li>

   Entferne die Stationen mit diesem Höhenwert, z.B. über Select features using an expression in der Attributtabelle oder Funktion
   Select by expression jeweils mit Ausdruck ‘“ELEV” = -999’. Anschließend den Layer mit Toggle Editing in den Bearbeitungsmodus
   bringen und dann delete selected layers. Alternativ kann auch die Filterfunktion des Layers genutzt werden mit Rechtsklick auf den
   Layer -> Filter -> Ausdruck ‘“ELEV” != -999’.

   .. raw:: html

      </ul>

   .. raw:: html

      </details>

-  Fügt die durchschnittliche Jahrestemperatur als Attribut der
   Messstationen hinzu. Nutzt dazu einen Join.

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

   Übereinstimmende Felder: “TEMP_STA_1” von ``temp_stations`` und “STATION_ID” von ``mean_temp``. Allerdings ist “TEMP_STA_1” als Zahl
   (Integer) und “STATION_ID” als Text (String) abgespeichert. Mögliche Lösung: Erstelle ein neues Feld in z.B. dem ``temp_stations``-Layer
   mit der Funktion Field calculator. Dort als result field type “Text (string)” auswählen und als Ausdruck nur ‘“TEMP_STA_1”’ eingeben
   (Name des neuen Feldes z.B. “ID”).

   .. raw:: html

      <li>

   Funktion Join attributes by field value, Inputlayer ``temp_stations``  Table field “ID”, Inputlayer 2 ``mean_temp`` Table field
   “STATION_ID”, optional bei Layer 2 fields to copy die Spalte “YEAR” auswählen, da es die einzige ist, die wir weiterhin brauchen

   .. raw:: html

      </ul>

   .. raw:: html

      </details>

Aufgabe 2: Temperaturwerte anpassen und Interpolation durchführen.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Berechnet für jede Messstation eine normalisierte Jahresdurchschnittstemperatur. Diese soll die Temperatur angeben,
   wenn die Messstation auf 0 m üNN liegen würde. Nutzt dafür folgenden Zusammenhang:

   -  Temperaturabnahme um 0,54°C je 100 Höhenmeter

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

   Beachte, dass die “YEAR”-Spalte im Textformat vorliegt und nicht für die Interpolationgenutzt werden kann bevor der Datentyp geändert wurde.

   .. raw:: html

      <li>

   Da für diese Aufgabe sowieso noch eine Umrechnung stattfindet, bei der der Datentyp automatisch angepasst werden kann, ist das nicht
   unbedingt nötig. Falls doch gwünscht, kann hierfür wieder die Funktion field calculator genutzt werden. Das result field sollte
   diesmal “decimal number (real)” genutzt werden und als Ausdruck nur “YEAR”. Ansonsten kann die Normalisierung der Temperaturwerte auch
   über den “field calculator” erfolgen. Mit dem Ausdruck:

      .. code-block::

         “YEAR” + (“ELEV” / 100 \* 0.54)

   .. raw:: html

      </ul>

   .. raw:: html

      </details>

-  Inpterpoliert anhand der gewonnenen Werte die
   Durchschnittstemperaturen in Deutschland.

   -  Nutzt dazu Inverse Distanz Gewichtung (IDW)
   -  und einen Power-Wert von 2

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

   Für die Interpolation sollte die Funktion IDW Interpolation genutzt werden. Hier den bearbeiteten “temp_stations”-Layer als Inputlayer
   und als Interpolation attribute das zuvor berechnete Feld mit der normalisierten Temperatur. Anschließendauf das grüne Plus drücken.
   Beim Extent rechts calculate from layer auswählen und den bearbeiteten “temp_stations”-Layer nutzen. Anschließend muss noch die
   Pixel size X angepasst werden (Pixel size Y) wird automatisch mit angepasst. Wir empfehlen eine pixel size X von 1000 (in diesem Fall Metern).

   .. raw:: html

      </ul>

   .. raw:: html

      </details>

-  Korrigiert eure gewonnenen Ergebnisse erneut unter Berücksichtigung der tatsächlichen Höhe. Nutzt dazu den Raster-Calculator und den oben
   genannten Zusammenhang und das Höhenmodell.

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

   Nach der Ausführung der Interpolation muss nun wieder die Höheninformation in das Ergebnis einfließen. Dafür wird der
   Raster-Calculator genutzt. Folgender Ausruck sollte genutzt werden: 
   
   .. code-block::

         “Interpolated@1” - ( “germany_dem_eprojected@1”/100 \* 0.54)

   .. raw:: html

      </ul>

   .. raw:: html

      </details>

-  Stylt das Ergebnis, sodass Temperaturunterschiede deutlich erkennbar
   werden.

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

   Das Styling kann unter Properties->Symbology unter singleband
   pseudocolor angepasst werden.

   .. raw:: html

      </ul>

   .. raw:: html

      </details>

.. figure:: https://raw.githubusercontent.com/GeowazM/Einfuehrung-GIS-fur-Geowissenschaften/refs/heads/main/exercise_08/temperatur_idw_pow2.PNG
   :alt: 3D Model

   Quelle: Daten vom Deutschen Wetter Dienst (`SWS - CDC (Climate Data Center) <https://www.dwd.de/DE/leistungen/cdc_portal/cdc_portal.html;jsessionid=C122F15176D4A325829CC896BBAAE9B9.live31093?nn=17626>`__)
