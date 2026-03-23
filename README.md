# DS-2002 Data Project 1 — Hotel Bookings Data Mart

## Overview
This project implements an ETL pipeline for a hotel bookings dimensional data mart.
The business process modeled is hotel booking transactions, capturing the interaction
between guests, hotels, room types, and time.

## Dataset
Hotel Booking Demand dataset (Kaggle, jessemostipak) — 119,390 records sampled down
to ~3,000 rows using proportional random sampling across two hotel types.

## Source Systems
| Source | Type | Contents |
|--------|------|----------|
| MySQL `hotel_src.guests` | Relational DB | Guest demographic data |
| MongoDB `hotel_bookings_db.hotels` | NoSQL | Hotel & channel attributes |
| `data/room_types_clean.csv` | File System | Room type & meal combinations |

## Destination
MySQL data mart `hotel_dw` containing 5 tables:

| Table | Type | Description |
|-------|------|-------------|
| `dim_date` | Dimension | Date attributes — year, quarter, month |
| `dim_guests` | Dimension | Guest demographics — country, customer type, party size |
| `dim_hotels` | Dimension | Hotel & booking channel attributes |
| `dim_rooms` | Dimension | Room type & meal plan combinations |
| `fact_bookings` | Fact | Booking transactions — adr, lead time, cancellations |

## Repository Structure
```
ds2002-project1/
├── README.md
├── data/
│   ├── hotel_bookings.csv        # raw Kaggle dataset
│   ├── bookings_clean.csv        # cleaned fact table source (generated)
│   └── room_types_clean.csv      # room type dimension source (generated)
├── sql/
│   └── dim_date.sql              # date dimension creation script
└── notebooks/
    └── ds2002_project1.ipynb     # full ETL pipeline notebook
```

## Deployment
### Prerequisites
```
pip install sqlalchemy pymysql pymongo pandas
```

### Steps to Run
1. Download `hotel_bookings.csv` from Kaggle (jessemostipak — Hotel Booking Demand) and place it in the `data/` folder
2. Start MySQL and MongoDB locally
3. Run `dim_date.sql` against the `hotel_dw` database in MySQL Workbench
4. Open `ds2002_project1.ipynb` and update the password fields in the connection variables cell
5. Run all cells top to bottom

### Services Used
- MySQL (local) — source DB `hotel_src` and destination data mart `hotel_dw`
- MongoDB (local) — source DB `hotel_bookings_db`
- Python / Jupyter Notebook — ds2002-env (Anaconda)
