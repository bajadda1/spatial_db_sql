-- Exercise: Spatial Database TD-3 SQL Spatial Functions

-- 1. Total number of parcels in the table
SELECT COUNT(*) FROM parcels;
-- Answer: This query returns the total number of parcels in the table.

-- 2. Fire point (centroid of parcel 462273)
SELECT ST_Centroid(geom) AS fire_point
FROM parcels
WHERE gid = 462273;
-- Answer: This query returns the centroid (fire point) of parcel 462273.

-- 3. Parcels within a 1 km radius of the fire point (462273)
-- In QGIS, use the following filter:
ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 1000);

-- 4. Modify the filter to detect both zones (462273 and 460957)
-- In QGIS, use the following adjusted filter:
ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 1000) 
OR ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 460957), 1000);

-- 5. SQL query: How many parcels are located within 1 km of both target parcels?
SELECT COUNT(*) 
FROM parcels 
WHERE ST_DWithin(geom, 
  (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 462273), 1000) 
OR ST_DWithin(geom, 
  (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 460957), 1000);
-- Answer: Returns the number of parcels within 1 km of either parcel 462273 or 460957.

-- 6. SQL query: What is the total area of parcels near the fire?
SELECT SUM(ST_Area(geom)) 
FROM parcels 
WHERE ST_DWithin(geom, 
  (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 462273), 1000) 
OR ST_DWithin(geom, 
  (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 460957), 1000);
-- Answer: Returns the total area of all parcels within 1 km of the fire points.
