Exercise 4 - Optional
================================================

Copernicus Emergency Managment Service (EMS) & Zenus 2022 Daten verknüpfen
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. admonition:: Hochwasserkatastrophe im Ahrweiler 2021
    :class: admonition-youtube

    ..  youtube:: 3xYOMy3-PJU
    
    `NZZ erklärt <https://www.youtube.com/watch?v=3xYOMy3-PJU>`_.

Welchen Mehrwert bieten Geodaten im Falle einer Katastrophe?
----------

Hier kannst du dir einen Überblick verschaffen: `Copernicus EMS (EMSR517) <https://cems-mapping-website.s3.eu-west-1.amazonaws.com/static/activations/EMSR517/EMSR517_AOI15_GRA_PRODUCT_r1_RTP01_v1.pdf>`__

Bei der Reaktion auf eine Katastrophe oder der Planung von Maßnahmen zur Katastrophenvorsorge ist es oft entscheidend, die betroffene Bevölkerung oder die Auswirkungen von Infrastrukturausfällen auf angrenzende Regionen zu schätzen. 
In solchen Situationen wird häufig eine Kombination mehrerer Datensätze verwendet. In unserem Beispiel ist das die Verknüpfung von OSM & Copernicus EMS Daten.

.. hint::

   **Geodaten, OpenStreetMap & Kathastrophen**
   To reduce the severe consequences of natural hazards,the humanitarian system focuses on measures to reduce disaster risks. Relevant actions
   include risk analysis, disaster prevention and mitigation measures as well as measures for strengthening the preparedness of communities in
   most affected areas. […] An interesting approach lies with the increasing use of geoinformation services combined with the efforts
   of digital volunteers. Both have already proven to substantially support relief activities of humanitarian organizations, such as the
   mapping activities after the earthquake in Nepal in 2015 or during the Ebola epidemic in 2014/2015. `Scholz et al. (2018) <https://doi.org/10.3390/rs10081239>`__


Wie viele Gebäude wurden durch die Ahrtal-Flut beschädigt und wie viele Menschen sind betroffen?
------------------------------------------------------------------------------------------

Die Ahrtal-Flut im Jahr 2021 in Deutschland zerstörte Hunderte von Gebäuden und unzählige Straßen in den betroffenen Gebieten oder machte sie vorübergehend unpassierbar. 
Das Deutsche Rote Kreuz war eine der Organisationen, die vor Ort Katastrophenhilfe leisteten und langfristige Unterstützung in den flutbetroffenen Regionen boten. 
In den ersten Tagen nach der Katastrophe hatte das Deutsche Rote Kreuz keine Zahlen vorliegen, wie viele Menschen Hilfe benötigten. 
Das Heidelberg Institute for Geoinformation Technology (HeiGIT) half bei der Koordination der Ressourcen auf der Grundlage der Verteilung der betroffenen Menschen, indem GIS-Workflows ausgeführt wurden, 
die Daten aus mehreren Quellen wie Copernicus EMS und OpenStreetMap kombinierten. In dieser Übung wirst Du Teile dieser Analyse nachbilden, die das HeiGIT 2021 für das Deutsche Rote Kreuz durchgeführt hat.

.. seealso::

   Download Daten
      * `Google Drive Ordner <https://drive.google.com/drive/folders/1ilvLYw8bkQMsny7WvaNkjnVfTxHiwpg3>`__

   Copernicus EMS liefert nahezu in Echtzeit Informationen und Geodaten über verschiedene Naturkatastrophen wie Überschwemmungen oder Erdbeben. 
   In dieser Übung verwenden wir die bereitgestellten Daten zum Flutereignis 2021 in Deutschland (`EMSR517: Flood in Western Germany <https://emergency.copernicus.eu/mapping/list-of-components/EMSR517>`__).
   Nach der Ahrtal-Flut erstellte Copernicus EMS mehrere Produkte wie eine Schadensklassifizierung und Abgrenzungskarten für die betroffenen Regionen.

   For the analysis we will use the Grading Product for `Bad Neuenahr-Ahrweiler <https://emergency.copernicus.eu/mapping/ems-product-component/EMSR517_AOI15_GRA_PRODUCT_r1_VECTORS/1>`__.
   Just get the ``.zip`` vector package.

   Für die erste Schätzung der betroffenen Bevölkerung werden wir WorldPop Daten verwenden. Diese kannst du hier `herunterladen - 2020: 100m Constrained Population Count <https://hub.worldpop.org/geodata/summary?id=49789>`__ dataset.

   Um die Nummer der betroffenen Bevölkerung genauer bestimmen zu können, benutzen wir Daten des `Zensus 2022 <https://www.zensus2022.de/DE/Was-ist-der-Zensus/_inhalt.html>`__, der von Bund und der Länder erhoben wurde.
   In diesen Zensus 2022 Daten befinden sich Bevölkerungsdaten als 1km oder 100m "Gitternetz", die Informationen über die Anzahl der dort lebenden Personen beinhaltet. 
   
   Im Downloadordner findet ihr die Zensus Daten als Excel. Ladet die Daten herunter & importiert die Excel-Tabelle als *Delimited Text*. Tipp: Schaut euch die Metadaten des Zenus an! *#EPSG*
 
   Download the district boundary of the Landkreis Ahrweiler and all municipalities within it, from `OSM Boundaries <https://osm-boundaries.com/>`__.

   Finally, download all buildings mapped in OSM for the Landkreis Ahrweiler. Maybe add a small buffer of two kilometers, so that also buildings on the edge are included.

2. Estimate affected population using flood extent
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For this analysis we will use the flood delineation provided by Copernicus EMS. Here, we want to provide a quick estimate on how many people are affected by the flood per municipality.

Load the dataset with the flood extent and dissolve the individual polygons.

.. raw:: html

   <details>

.. raw:: html

   <summary>

Show the steps in QGIS

.. raw:: html

   </summary>

::

   Dissolve flood extent polygons

.. raw:: html

   </details>

:literal:`{dropdown} Show the steps in QGIS. ```{figure} ../figs/ahrtal_dissolve_flood_extent.png --- width: 100% name: ahrtal-dissolve --- Dissolve flood extent polygons. ``\``

Intersect the flood extent with the municipality boundaries for the Landkreis Ahrweiler.

:literal:`{dropdown} Show the steps in QGIS. ```{figure} ../figs/ahrtal_intersection_flood_extent_and_districts.png --- width: 100% name: ahrtal-intersection-municipalities --- Intersection of flood extent and municipality boundaries. ``\``

Finally, derive a rough estimate for the number of people affected by the flood per municipality using the Worldpop population data using the zonal stats tool.

:literal:`{dropdown} Show the steps in QGIS. ```{figure} ../figs/ahrtal_zonal_stats.png --- width: 100% name: ahrtal-zonal-stats --- Zonal Statistics to estimate affected population per municipality. ``` ```{figure} ../figs/ahrtal_zonal_stats_results.png --- width: 100% name: ahrtal-zonal-stats-results --- According to our estimate there are 3165 persons affected by the flood in Bad Neuenahr-Ahrweiler. ``\``

3. Estimate affected population using building damage grades
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In this step, we want to derive the average number of people per building per Zensus Grid cell. First, join the population information
from the Zensus Spreadsheet to the Zensus Grid geometries.

:literal:`{dropdown} Show the steps in QGIS. ```{figure} ../figs/ahrtal_pop_per_grid.png --- width: 100% name: ahrtal-pop-per-grid --- Join Zensus grid geometries and population values from CSV file. ``\``

In a second, step count the number of residential buildings (values: ``yes``, ``house``, ``residential``, ``appartements``) per Zensus Grid
cell (for simplicity use the building centroid here as the reference).

:literal:`{dropdown} Show the steps in QGIS. ```{figure} ../figs/ahrtal_building_centroids.png --- width: 100% name: ahrtal-building-centroids --- Derive Building Centroids. ``` ```{figure} ../figs/ahrtal_select_buildings.png --- width: 100% name: ahrtal-select-buildings --- Select buildings with the tag values "yes", "residential", "house" or "appartement". ``` ```{figure} ../figs/ahrtal_osm_buildings_per_grid.png --- width: 100% name: ahrtal-osm-buildings-per-grid --- Count the number of OSM buildings per Zensus grid cell. ``\``

Then, use the Field Calculater to add the average people per buildings (``grid population / grid building count``).

:literal:`{dropdown} Show the steps in QGIS. ```{figure} ../figs/ahrtal_pop_per_building.png --- width: 100% name: ahrtal-pop-per-building --- Compute the average number of people per building for each Zensus grid geometry. ``\``

Finally, estimate the number of person which live in buildings which
have been damaged or destroyed by the flood. Use a spatial join to add
the population per building derived earlier to each damaged building as
marked by Copernicus EMS. Then, derive summary population statistics per
Copernicus EMS damage grade and object type.

:literal:`{dropdown} Show the steps in QGIS. ```{figure} ../figs/ahrtal_cems_buildings.png --- width: 100% name: ahrtal-cems-buildings --- Join average population count to damaged buildings. ``` ```{figure} ../figs/ahrtal_cems_buildings_stats.png --- width: 100% name: ahrtal-cems-buildings-stats --- Calculate the total affected population per damage grade. ``` ```{figure} ../figs/ahrtal_cems_buildings_stats_results.png --- width: 100% name: ahrtal-cems-buildings-stats-results --- There are 672 damaged residential buildings and an estimated directly affected population of 1373 persons living in these buildings. ``\``

.. note::

   🙏 Danke. Angepasst nach `HeiGIT & Benjamin Herfort <https://giscience.courses-pages.gistools.geog.uni-heidelberg.de/openstreetmap-analyses-with-qgis-python-and-r/content/chapter_4/flooding_analysis.html>`__.
   Du interessierst dich für für QGIS und OpenStreetMap. Dann schau `hier <https://giscience.courses-pages.gistools.geog.uni-heidelberg.de/openstreetmap-analyses-with-qgis-python-and-r/content/chapter_1/aims_and_goals.html>`__ vorbei.
