URL = http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/50m/cultural/ne_50m_admin_0_countries.zip

ne_50m_admin_0_countries.zip:
	curl -LO $(URL)

ne_50m_admin_0_countries.shp: ne_50m_admin_0_countries.zip
	unzip ne_50m_admin_0_countries.zip
	touch ne_50m_admin_0_countries.shp

countries.json: ne_50m_admin_0_countries.shp
	ogr2ogr -f GeoJSON countries.json ne_50m_admin_0_countries.shp

countries.topojson: countries.json
	topojson -p -o countries.topojson countries.json

clean:
	rm ne_50m_admin_0_countries*
	rm countries.json