
# Beschreibung

## Aufgabenstellung
* Importieren sie die Bänder 1-7 einer MODIS Szene vom 9. Dezember 2011
	- Welche temporale Auflösung besitzt MODIS?
	- Welche geometrische Auflösung besitzen die vorliegenden Daten?
	- Welche Kanalkombination entspricht am ehesten einer Echtfarbendarstellung?
* Erstellen sie einen Layerstack mit den 7 Bändern
* Erstellen sie ein Subset vom Bereich Südtirol- Gardasee

# MODIS Bilddaten downloaden
Hab mir die MODIS Datei selber online gesucht und runter geladen. MOD09GA bietet dabei Band 1-7 an und ist für die Fragestellung genau passend.
- [Overview](https://lpdaac.usgs.gov/products/modis_overview)
- [MOD09GA](https://lpdaac.usgs.gov/products/modis_products_table/mod09ga)
- [Data Policy](https://lpdaac.usgs.gov/products/modis_policies): "MODIS data and products acquired through the LP DAAC have no restrictions on subsequent use, sale, or redistribution."
- [Dateiübersicht MOD09GA 005 h18v05](http://e4ftl01.cr.usgs.gov/MOLT/MOD09GA.005/2011.12.09/)
- [hdf](http://e4ftl01.cr.usgs.gov/MOLT/MOD09GA.005/2011.12.09/MOD09GA.A2011343.h18v04.005.2011345042926.hdf): image data
- [xml](http://e4ftl01.cr.usgs.gov/MOLT/MOD09GA.005/2011.12.09/): metadata
- [Known issues in MOD09 product (Surface reflectance)](http://landweb.nascom.nasa.gov/cgi-bin/QA_WWW/getSummary.cgi?esdt=MOD09)

Durch die Recherche ließen sich auch gleich die Fragen beantworten:
- Temporale Auflösung: 1-2 Tage
- Geometrische Auflösung: 500m

# MODIS Bilddaten umwandeln
Zuerst das *.hdf file mittels Drag & Drop oder als neuen Rasterlayer importieren. Beim öffnendne Dialog nur die Bänder 1, 3 und 4 auswählen.

Das Verschmelzen Tool nimmt nur GeoTIFF Dateien an, also müssen die 3 Bänder nun jeweils als GeoTIFF exportiert werden.

# Layerstack erstellen
Im Menu unter "Raster -> Sonstiges -> Verschmelzen" die drei zuvor erstellten GeoTIFF Dateien auswählen und die Optionen "Layerstack" und "Nach Abschluss zu Karte hinzufügen" auswählen.

# Kanalkombination Echtfarbendarstellung

Kanalkombination für Echtfarbendarstellung: 
- Band 1 = rot
- Band 3 = blau
- Band 4 = grün


# Subset Südtirol-Gardasee
Unter "Raster -> Extraktion -> Clipper" auswählen. Im Menu den Stack-Layer auswählen und die Grenzkoordinaten eingeben. Anbei das passende gdal script, welches auch manuel im Fenster eingegeben werden kann.

´´´gdal_translate -a_nodata 0 -srcwin 1700 700 500 400 -of GTiff /myData/science/academia/vu-fernerkundung-digitale-bildverarbeitung/data/stack /myData/science/academia/vu-fernerkundung-digitale-bildverarbeitung/data/subset´´´



