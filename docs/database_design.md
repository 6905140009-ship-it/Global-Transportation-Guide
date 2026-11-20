
# Database Design
## Global Transportation Guide Website

### 1. Introduction
This document describes the proposed database design for the Global Transportation Guide Website. The database will organize information about countries, cities, transportation types, routes, fares, and travel tips.

### 2. Database Overview
The database is designed to store transportation information in a structured way. It will help the website retrieve and display relevant information to users.

### 3. Database Tables

#### 3.1 Countries
Stores information about countries.

| Field | Data Type | Key | Description |
|---|---|---|---|
| country_id | INT | Primary Key | Unique country ID |
| country_name | VARCHAR(100) | | Country name |
| country_code | VARCHAR(10) | | Country code |

#### 3.2 Cities
Stores information about cities.

| Field | Data Type | Key | Description |
|---|---|---|---|
| city_id | INT | Primary Key | Unique city ID |
| city_name | VARCHAR(100) | | City name |
| country_id | INT | Foreign Key | Related country ID |

#### 3.3 Transportation_Types
Stores different transportation types.

| Field | Data Type | Key | Description |
|---|---|---|---|
| transport_id | INT | Primary Key | Unique transportation ID |
| transport_name | VARCHAR(100) | | Transportation name |
| description | TEXT | | Transportation details |

#### 3.4 Routes
Stores transportation route information.

| Field | Data Type | Key | Description |
|---|---|---|---|
| route_id | INT | Primary Key | Unique route ID |
| city_id | INT | Foreign Key | Related city ID |
| transport_id | INT | Foreign Key | Related transportation ID |
| start_location | VARCHAR(150) | | Starting point |
| end_location | VARCHAR(150) | | Destination |
| route_description | TEXT | | Route details |

#### 3.5 Fares
Stores estimated transportation fare information.

| Field | Data Type | Key | Description |
|---|---|---|---|
| fare_id | INT | Primary Key | Unique fare ID |
| route_id | INT | Foreign Key | Related route ID |
| estimated_fare | DECIMAL(10,2) | | Estimated fare |
| currency | VARCHAR(10) | | Currency code |

#### 3.6 Travel_Tips
Stores useful travel information and tips.

| Field | Data Type | Key | Description |
|---|---|---|---|
| tip_id | INT | Primary Key | Unique tip ID |
| city_id | INT | Foreign Key | Related city ID |
| tip_title | VARCHAR(150) | | Tip title |
| tip_description | TEXT | | Tip details |

### 4. Database Relationships
- One country can have many cities.
- One city can have many routes.
- One transportation type can be used by many routes.
- One route can have fare information.
- One city can have many travel tips.

### 5. Entity Relationship Diagram (ERD)

```text
COUNTRIES
    |
    | 1 to Many
    |
  CITIES
    |-------------------|
    |                   |
    | 1 to Many         | 1 to Many
    |                   |
  ROUTES             TRAVEL_TIPS
    |
    | Many to One
    |
TRANSPORTATION_TYPES

ROUTES
    |
    | 1 to Many
    |
  FARES
```

### 6. Primary Keys and Foreign Keys
- Primary keys uniquely identify each record in a table.
- Foreign keys connect related tables.
- These keys help maintain relationships and data consistency.

### 7. Conclusion
This database design provides a structured way to manage transportation information. It supports the main features of the Global Transportation Guide Website and can be expanded in the future.
