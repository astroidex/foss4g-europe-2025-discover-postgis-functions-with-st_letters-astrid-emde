# Discover PostGIS Functions with ST_Letters

[FOSS4G Europe 2025 Mostar (Bosnia-Herzegovina)](https://2025.europe.foss4g.org/)

![FOSS4G Europe 2025 Mostar (Bosnia-Herzegovina)](img/foss4g-europe-2025.png ) ![](img/postgresql_postgis.png)

![Program Link](https://talks.osgeo.org/foss4g-europe-2025/talk/PNYWM8/)


[![Creative Commons License](http://i.creativecommons.org/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/)


## Astrid Emde

* WhereGroup GmbH Germany
* astrid.emde@wheregroup.com
* [@astroidex fediverse](https://mastodon.social/@astroidex)


![WhereGroup](img/WhereGroup.png )

* FOSS Academy https://www.foss-academy.com/

![FOSS Academy](img/FOSSAcademy.png)


## Why ST_Letters? 
* Try PostGIS Functions without data
* ST_Letters >= PostGIS 3.3.0
* Function creates string as a multipolygon geometry
* https://postgis.net/docs/ST_Letters.html

![ST_Letters PostGIS documentation](img/st_letters_function.png)


## Try it out!

```sql
SELECT ST_Letters('FOSS4G Europe 2025 Mostar');
```

![DBeaver ST_Letters](img/dbeaver_first_st_letters.png)


## Scale the text and move it to Mostar

```sql
SELECT 
  ST_SetSrid(
    ST_Translate(
      ST_Scale(
        ST_Letters('FOSS4G Europe 2025 Mostar')
      , 0.00005, 0.00005),
    17.787, 43.34603), 
    4326);
```

![DBeaver ST_Letters move to Mostar](img/dbeaver_st_letters_in_mostar.png)


## Try the example in the demo script

* Create database
* Activate the Extension postgis
* Run **script/st_letters_demo.sql** in DBeaver or pgAdmin or psql 
* Have a look at your data in QGIS (try demo project st_letters.qgz - update your .pg_service.conf)


### QGIS

![Show ST_Letters example in QGIS](img/qgis_st_letters.png)


## Video

* Have a look at the video


### Publish QGIS Server WMS and show it in Mapbender

![QGIS2Mapbender](img/qgis2mapbender.png)



![Mapbender](img/mapbender_application_dimensions.png)




## Making of

* Create demo table with **script/st_letters_demo.sql** Every example represents a day
* QGIS project with **Temporal Controller** on st_letters to show only one demo at once
* Export images via **Temporal Controller**
* Create a video with ffmpeg
* Publish the QGIS project as QGIS Server WMS via the QGIS Plugin QGIS2Mapbender
* Activate Dimensions for the WMS in Mapbender to show only one demo at once


## See also

* Fun with Letters in PostGIS 3.3! Jacob Coblentz Crunchy Data https://www.crunchydata.com/blog/fun-with-letters-in-postgis-33


Have fun with ST_Letters & PostGIS!