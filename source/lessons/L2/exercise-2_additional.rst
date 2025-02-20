Exercise 2 - Optional
==========

Das ist eine freiwillige Zusatzaufgabe.

.. hint::

   Du bist früher fertig als angedacht? Dann versuche die obigen Geodaten selbstständig zu beschaffen und aufzubereiten. Ziel der Übung:
      * Einen WMS-Dienst hinzufügen

.. note::

   **Support findest du im Wiki**
      *  `WMS-Dienste <https://giscience.courses-pages.gistools.geog.uni-heidelberg.de/qgis-book//content/gis/01_karto-basics/home-Geodatenformate.html#web-map-service-wms>`__
   
.. seealso::

   Daten
      *  Punkt-Layer - Bodenschätze Punkte (`EGDI <https://geoserver.geo-zs.si/egdi-surface-geology/gsmlp/wms>`__)
      *  DLR EOC - Gelände On- & offshore (`DLR EOC basmaps <https://geoservice.dlr.de/eoc/basemap/wms>`__)


Web Map Service (WMS) - WMS-Dienste (OGC-Standards)
--------
Web Map Services (WMS) erlauben es euch, Geodaten aus dem Web mit eurem GIS zu verknüpfen und abzurufen. 
Als Ergebnis wird euch dabei dann ein georeferenziertes Kartenbild angezeigt. Dieses Prinzip wird beispielsweise auch bei Basemaps angewendet. 
Im zugehörigen Wikibeitrag finden sich Informationen darüber, wie sich WMS Daten in QGIS hereinladen lassen, und welche Funktionen genutzt werden können.

Further Resources: Weitere Informationen zu WMS finden sich auch unter: `OGC-Standards <https://www.ogc.org/standards/wms>`__.


Aufgabe
--------

1. Arbeite in deinem Projekt von Exercise 2 weiter
2. Füge aus dem WMS-Dienstportfolio des DLR EOC den Layer **EGDI 1:1M Surface Geologic Units Lithology** hinzu
3. Füge aus dem WMS-Dienstportfolio des DLR EOC den Layer **Bathymetrie-und-DEM_43200x21600_unsigned_HILLSHADE_8bit_2013-GEO** hinzu
4. Aktuallisiere dein Projekt im QGIS Print Composer
5. Speicher erneut deine Karte als PDF


So (oder ähnlich) kann das Ergebnis aussehen
-------------------------------------

.. figure:: img/bodenschaetze_bw_map.png
   :alt: Karte erstellt in QGIS 
   :width: 800px

   Einfache Karte der Bidenschätze in Baden-Württemberg. Quelle: Eigene Erhebung mit Daten des LGL & des BGR.