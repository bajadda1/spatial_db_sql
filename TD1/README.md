# 🗺️ TD-1: Installation of PostGIS and Creation of a Spatial Database

## 📖 Overview
This tutorial guides you through the installation of PostgreSQL and PostGIS, the creation of a spatial database, and the verification of your setup. Follow the steps below to get started with spatial data management.

---

## 🚀 Step 1: Install PostgreSQL
1. Download PostgreSQL from the [official website](https://www.postgresql.org/download/).
2. Select the version suitable for your operating system (Windows, Linux, macOS, etc.).
3. During installation:
   - Follow the setup wizard.
   - Set a password for the `postgres` user. Make sure it is easy to remember.

For OS-specific instructions:
- [Windows Installation Guide](https://www.postgresql.org/download/windows/)
- [Linux Installation Guide](https://www.postgresql.org/download/linux/)
- [macOS Installation Guide](https://www.postgresql.org/download/macosx/)

---

## 🚀 Step 2: Install PostGIS
1. During PostgreSQL installation, ensure all components, including **Stack Builder**, are selected.
2. After the installation, launch **Stack Builder**.
3. Select your installed PostgreSQL version.
4. From the available options, choose **PostGIS** as the spatial database extension.
5. (Optional) Skip the "Create a spatial database" option since we will create one manually.
6. Complete the installation process.

---

## 🚀 Step 3: Create a Database in pgAdmin
1. Open **pgAdmin 4**, which was installed with PostgreSQL.
2. Log in using the `postgres` user password you set during installation.
3. Navigate to:
   - Expand **Servers** > Right-click on your PostgreSQL server > **Create** > **Database**.
4. Name the database (e.g., `spatial_db_1`) and click **Save**.

---

## 🚀 Step 4: Add the PostGIS Extension
1. In **pgAdmin**, expand **Databases** and select your newly created database (e.g., `spatial_db_1`).
2. Right-click on the database and open the **Query Tool**.
3. Run the following SQL command to enable PostGIS:
   ```sql
   CREATE EXTENSION postgis;

---

## 🚀 Step 5: Verify PostGIS Installation
1. In **pgAdmin**, navigate to:
2. Expand your database > Schemas > Public > Tables.
3.Look for a table named spatial_ref_sys.
   - Its presence confirms that the PostGIS extension is successfully installed.
