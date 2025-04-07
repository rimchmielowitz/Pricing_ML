## 📄 Data Description: `TWD.csv`

This file contains the input data for an optimization model focused on routing and pricing. It includes information about nodes (e.g., pickup, delivery) and driver-specific parameters. The following table describes each column in detail.

---

### 🔹 Column Overview

| Column                      | Type       | Description                                                                                       |
|-----------------------------|------------|---------------------------------------------------------------------------------------------------|
| `i`                         | Integer    | Node number. Each node (pickup, delivery, origin, destination) has a unique ID.                  |
| `lat`, `long`               | Float      | Geographic coordinates of the node. Used for validation only, not processed in the model.        |
| `l`                         | Float      | Load at the node: positive for pickup, negative for delivery.                                    |
| `Time a`, `Time b`          | Integer    | Earliest (`a`) and latest (`b`) arrival times at the node in minutes.                            |
| `s`                         | Integer    | Service time in minutes. Only relevant for pickup and delivery nodes.                            |
| `nodetype`                  | String     | Type of node: `pickup`, `delivery`, `origin`, or `destination`.                                  |
| `distance_lat_lat_long_long` | Float (optional) | Auxiliary column for distance validation (not relevant to the model).                      |
| `m`                         | Integer    | Total number of drivers in the model.                                                            |
| `n`                         | Integer    | Total number of jobs.                                                                            |
| `R`                         | Integer    | Capacity constraint per driver, as defined by their origin.                                      |
| `Speed`                     | Float      | Vehicle speed (e.g., km/h), used with distance to calculate travel time.                         |
| `Fahrernummer`              | Integer    | Helper column: assigns origin and destination nodes to drivers (e.g., Origin1/Destination1 → Driver 1). |
| `WTP_Faktor`                | Float      | Willingness-to-pay factor for sensitivity analysis.                                              |
| `ETP_Faktor`                | Float      | Expectation-to-be-paid factor for sensitivity analysis.                                          |
| `Stundenzeitfenster driver`| Integer or String | Time window of driver availability (per hour, format may vary).                          |

---

### 🧠 Model Usage Notes
- **Time Windows**: `Time a` and `Time b` are critical for time constraints and must be interpreted correctly (e.g., minutes from midnight).
- **Service Time (`s`)** is only considered for actual jobs (pickup/delivery).
- **Capacity (`R`)** and **Driver Assignment (`Fahrernummer`)** impact which jobs each driver may handle.
- **WTP/ETP Factors** are used for economic modeling and sensitivity analysis.

---

### 🧾 Example Row (Sample Data)

```csv
i,lat,long,l,Time a,Time b,s,nodetype,distance_lat_lat_long_long,m,n,R,Speed,Fahrernummer,WTP_Faktor,ETP_Faktor,Stundenzeitfenster driver
1,52.52,13.405,100,480,540,10,pickup,0.0,2,3,1000,60,1,1.2,1.0,8-18
2,52.54,13.405,-100,500,600,10,delivery,0.0,2,3,1000,60,1,1.2,1.0,8-18
3,52.50,13.39,0,0,1440,0,origin,0.0,2,3,1000,60,1,1.0,1.0,8-18
4,52.49,13.38,0,0,1440,0,destination,0.0,2,3,1000,60,1,1.0,1.0,8-18
```

**Explanation**:
- Row 1 is a **pickup** node at 08:00–09:00 with 100 units of load and a 10-minute service time.
- Row 2 is the matching **delivery** node for that pickup, scheduled between 08:20–10:00.
- Row 3 is an **origin** node for the driver, available all day.
- Row 4 is the matching **destination** node.

This simplified example shows one job and one driver. You can scale this structure to multiple drivers and multiple pickup-delivery pairs.

---

Feel free to extend this document with additional examples or visualizations.

