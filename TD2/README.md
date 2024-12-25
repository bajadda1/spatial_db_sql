# 🌍 TD-2: Creating Tables with Spatial Columns

This tutorial demonstrates how to create spatial tables in PostgreSQL with PostGIS, populate them using QGIS, and verify the data through SQL queries.

---

## 🗂️ Table of Contents
1. [Creating a Spatial Table (Points)](#-step-1-creating-a-spatial-table-points)
2. [Creating a Spatial Table (Polygons)](#-step-2-creating-a-spatial-table-polygons)
3. [Creating a Spatial Table (LineStrings)](#-step-3-creating-a-spatial-table-linestrings)
4. [Using QGIS to Insert Data](#-using-qgis-to-insert-data)

---

## 🚀 Step 1: Creating a Spatial Table (Points)
### 📋 SQL Command
Run the following SQL command in pgAdmin to create a `points_of_interests` table with a `Point` geometry column:
```sql
CREATE TABLE points_of_interests (
  id SERIAL PRIMARY KEY,
  nom VARCHAR(255),
  geom GEOMETRY(Point, 4326)
);
```

### 🛠️ Using QGIS to Insert Data
1. Open **QGIS** and establish a connection to your database:
   - Right-click **PostgreSQL** in the Explorer panel.
   - Select **New Connection**, then input the required details and test the connection.
2. Add the `points_of_interests` table as a layer:
   - Double-click the table to load it as a layer.
3. Switch to **Edit Mode**:
   - Add some points on the map.
   - Save your changes.

### 🔍 Verifying Data
In pgAdmin, execute the following query to view the data:
```sql
SELECT * FROM points_of_interests;
```

---

## 🚀 Step 2: Creating a Spatial Table (Polygons)
### 📋 SQL Command
Run this SQL command in pgAdmin to create a `zones_protegees` table with a `Polygon` geometry column:
```sql
CREATE TABLE zones_protegees (
  id SERIAL PRIMARY KEY,
  nom VARCHAR(255),
  geom GEOMETRY(Polygon, 4326)
);
```

### 🛠️ Using QGIS to Insert Data
1. Follow the same steps as in **Step 1** to load the `zones_protegees` table in QGIS.
2. Draw polygons on the map in **Edit Mode** and save your changes.

### 🔍 Verifying Data
In pgAdmin, execute the following query to view the data:
```sql
SELECT * FROM zones_protegees;
```

---

## 🚀 Step 3: Creating a Spatial Table (LineStrings)
### 📋 SQL Command
Run this SQL command in pgAdmin to create a `routes` table with a `LineString` geometry column:
```sql
CREATE TABLE routes (
  id SERIAL PRIMARY KEY,
  nom VARCHAR(255),
  geom GEOMETRY(LINESTRING, 4326)
);
```

### 🛠️ Using QGIS to Insert Data
1. Load the `routes` table in QGIS.
2. Draw lines on the map in **Edit Mode** and save your changes.

### 🔍 Verifying Data
In pgAdmin, execute the following query to view the data:
```sql
SELECT * FROM routes;
```

---

## 🛠️ Using QGIS to Insert Data
For all spatial tables:
1. Connect to the PostgreSQL database in QGIS.
2. Load the desired table as a layer.
3. Switch to **Edit Mode** and add spatial data (points, polygons, or lines).
4. Save the changes to persist data in the database.

---

## 🏁 Summary
After completing these steps, you will have:
- Created three spatial tables (`points_of_interests`, `zones_protegees`, `routes`) with different geometry types.
- Populated them with data using QGIS.
- Verified the data using SQL queries in pgAdmin.

Feel free to extend these examples for more complex spatial operations! 🚀

---

## 🔗 Resources
- [PostGIS Documentation](https://postgis.net/documentation/)
- [QGIS Documentation](https://docs.qgis.org/)
- [pgAdmin Documentation](https://www.pgadmin.org/docs/)

---
