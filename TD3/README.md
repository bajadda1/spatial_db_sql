# Spatial Database TD-3 SQL Spatial Functions

## Exercise Objective
Determine how many parcels are located within 1 km of fire points using PostGIS SQL functions.

## Context
In this exercise, you will:
- Import a shapefile into PostGIS.
- Use SQL spatial functions to analyze the data.
- Use QGIS to visualize and filter spatial data.

## Steps to Follow

### 1. Import the Shapefile into PostGIS
1. **Download the shapefile**
   - Ensure the shapefile for Florida parcels is downloaded.

2. **Use PostGIS Shapefile Import/Export Manager**
   - Open the manager (on Windows, press the Windows key and search for `Shapefile Import/Export Manager`).
   - Select the Florida parcels shapefile and import it into a PostgreSQL table.

### 2. Queries to Analyze the Data

#### Count Total Number of Parcels
```sql
SELECT COUNT(*) FROM parcels;
```
*Returns the total number of parcels in the table.*

#### Get Fire Point (Centroid of Parcel 462273)
```sql
SELECT ST_Centroid(geom) AS fire_point
FROM parcels
WHERE gid = 462273;
```
*Returns the centroid of parcel 462273.*

#### Parcels within a 1 km Radius of Fire Point (QGIS Filter)
Filter for parcels within 1 km of parcel 462273:
```sql
ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 1000);
```

#### Modify the Filter for Two Zones
Detect parcels within 1 km of parcels 462273 and 460957:
```sql
ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 1000) 
OR ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 460957), 1000);
```

### 3. Advanced Spatial Queries

#### Count Parcels within 1 km of Both Zones
```sql
SELECT COUNT(*) 
FROM parcels 
WHERE ST_DWithin(geom, 
  (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 462273), 1000) 
OR ST_DWithin(geom, 
  (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 460957), 1000);
```
*Returns the number of parcels within 1 km of either parcel.*

#### Calculate Total Area of Parcels Near Fire Points
```sql
SELECT SUM(ST_Area(geom)) 
FROM parcels 
WHERE ST_DWithin(geom, 
  (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 462273), 1000) 
OR ST_DWithin(geom, 
  (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 460957), 1000);
```
*Returns the total area of parcels within 1 km of fire points.*

## Additional Resources
- [PostGIS Documentation](https://postgis.net/documentation/)
- [QGIS Documentation](https://qgis.org/en/docs/index.html)

## Author
This project was developed for learning spatial database functions and spatial analysis using PostGIS and QGIS.
