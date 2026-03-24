# DS-2002 Data Project 1 

## Overview
This project uses the hotel booking demand dataset to then create an ETL pipeline for a hotel bookings data warehouse. 
The business model that is modeled is the relationship between guests, hotel, room types and date.

## Dataset
Hotel Booking Demand dataset (https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand/data) 
Originial data set is 119,390 records sampled down to ~3,000 rows using proportional random sampling across two hotel types for a more manageable dataset to work with.

## Source Systems
| Source | Contents |
|--------|----------|
| MySQL `hotel_src.guests` | Guest data |
| MongoDB `hotel_bookings_db.hotels` | Hotel attributes |
| `data/room_types_clean.csv` | Room type & meal combinations |

## Destination
MySQL data mart `hotel_dw` containing 5 tables: `dim_guests`, `dim_hotels`, `dim_rooms`, `dim_date`, `fact_bookings`

## Process
1. Split up CSV file into seperate tables (guests, hotels, room_types, other columns to build fact_table) - Done with the help from Claude Sonnet 4.6 
2. Convert (to JSON/SQL/leave as CSV) and load the different tables into their respective sources. (Shown above under Source Systems)
3. Create Dimension Tables
4. Load Tables into destination database
5. Create Fact Table
6. Verify with SQL Queries

## Deployment
### Prerequisites
```
pip install sqlalchemy pymysql pymongo pandas
```

### Steps to Run
1. Clone this GitHub repo
2. Start MySQL and MongoDB locally
3. Run `dim_date.sql` in MySQL Workbench
4. Launch Jupyter Notebook on the ds-2002 env we set up in class (or something with the same dependencies)
5. Open `ds2002_project1.ipynb` and update the password fields in the connection variables cell to your MySQL and MongoDB connections
6. Run all cells top to bottom
