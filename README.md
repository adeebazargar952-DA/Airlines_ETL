# Airlines_ETL
End-to-end airline analytics project: Python/SQL ETL on a 2.3M-row SQLite database, visualized in a 4-page Power BI dashboard covering network demand, operations, and commercial performance.
Airline Network & Commercial Analytics
# Airline Network & Commercial Analytics

An end-to-end data project built on a real airline booking database — from raw SQLite tables through Python/SQL ETL to a 4-page interactive Power BI dashboard.

## Dataset

A relational airline booking database (`travel.sqlite`) with 8 tables and over 2.3 million rows:

| Table | Rows | Contents |
|---|---|---|
| `bookings` | 262,788 | Booking reference, date, total amount |
| `tickets` | 366,733 | Ticket number, passenger, linked booking |
| `ticket flights` | 1,045,726 | Ticket ↔ flight mapping, fare class, amount |
| `flights` | 33,121 | Flight number, schedule, route, status, aircraft |
| `boarding_passes` | 579,686 | Ticket, flight, seat, boarding number |
| `seats` | 1,339 | Seat map per aircraft |
| `airports_data` | 104 | Airport code, name, city, coordinates |
| `aircrafts_data` | 9 | Aircraft model, seating range |

## Process

Three Jupyter notebooks handle the ETL and analysis pipeline:

- **`01_database_exploration.ipynb`** — schema discovery, null/duplicate profiling, and initial revenue queries across all 8 tables.
- **`Airlines_ETL_Demand_network.ipynb`** — route and airport demand concentration, fare-class revenue mix, booking lead-time analysis, and Pareto-style traffic distribution.
- **`Airlines_ETL_operations.ipynb`** — aircraft and route utilization, delay/cancellation reliability, and commercial route strategy.

Each notebook exports clean, analysis-ready CSVs consumed directly by the Power BI dashboard.

## Key Findings

- **Business class disproportionately drives revenue.** Business tickets are just 10.3% of volume but 26.5% of total revenue — a 3.2× revenue-per-ticket multiplier over Economy.
- **Demand is highly concentrated.** The top 25% of routes carry roughly two-thirds of all passenger traffic; the top 10% of routes and airports account for an outsized share of both passengers and revenue.
- **Cancellations outpace delays across the fleet** — an unusual pattern, since airline operations typically see the reverse. This holds true for nearly every aircraft type in the fleet, with the Bombardier CRJ-200 showing the highest cancellation rate.
- **Booking lead time is consistent across fare classes**, averaging ~20 days regardless of whether a passenger books Economy or Business.
- **Revenue and passenger volume aren't tightly linked at the route level.** Some routes generate revenue disproportionate to their traffic (premium/business-heavy routes), while others carry high passenger volume at comparatively low revenue.

## Dashboard

A 4-page Power BI report (`airline.pbix`):

1. **Executive Overview** — top-line KPIs (passengers, flights, revenue, revenue/passenger, delay rate, cancellation rate, seat utilization), top routes by volume and revenue, and traffic concentration.
2. **Network & Demand** — monthly demand trends, airport and route passenger concentration, and median booking lead time by route.
3. **Operations** — aircraft-level delay and cancellation reliability, fleet utilization, flight status breakdown, and airport flight activity (routes filtered to ≥100 flights to avoid small-sample distortion).
4. **Commercial Performance** — fare-class revenue vs. passenger share, revenue-per-ticket by route, revenue vs. passenger volume relationships, and high-demand/low-fare vs. low-demand/high-fare route segments.

## Tools

- **Python** — pandas, NumPy, json
- **SQL** — SQLite (via `sqlite3` / `pandas.read_sql_query`)
- **Jupyter Notebook**
- **Power BI Desktop** — data modeling, DAX measures, interactive visuals
- **Git/GitHub** — version control
