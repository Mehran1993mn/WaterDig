# VESLA API Water Quality Data Retrieval

## Overview

This notebook retrieves water quality monitoring data from the Finnish Environment Institute (SYKE) VESLA API using paginated requests. The script downloads records in batches and stores them locally for further analysis.

The notebook is designed for large-scale environmental data extraction, allowing users to download specific water quality variables such as **pH**, **dissolved oxygen**, **turbidity**, and **nutrients** across Finnish lakes.

The retrieved data are saved to a CSV file for further processing and analysis.

---

## Data Source

Data are accessed from the VESLA OData API:

https://rajapinnat.ymparisto.fi/api/vesla/2.0/odata/

The script specifically queries the endpoint:

`Result_Wide`

which contains wide-format monitoring results.

---

## Features

- Retrieve large datasets using API pagination
- Filter by water quality parameter (`Determination_Id`)
- Filter by sampling depth
- Filter by specific monitoring sites
- Download large datasets in manageable chunks
- Save results to CSV files for further analysis

---

## Pagination Settings

The API limits the number of rows returned per request. Therefore, the notebook retrieves data in chunks using the `$skip` parameter.

### Key Parameters
INITIAL_SKIP = 1000
MAX_SKIP = 10000
STEP = 1000
These values control how much data is retrieved.

| Parameter | Description |
| ----------- | ----------- |
| INITIAL_SKIP | Starting offset for API query |
| MAX_SKIP | Maximum offset for API requests |
| STEP | Increment between API calls |

### Example Request Sequence
skip=0
skip=1000
skip=2000
skip=3000
...
skip=10000


Increasing `MAX_SKIP` allows retrieval of larger datasets.

---

## Selecting Water Quality Variables

Water quality parameters are identified using `Determination_Id`.

To download a specific parameter, modify:
TARGET_DETERMINATION_ID = X
### Example Determination IDs

| Variable | Determination_Id |
| ----------- | ----------- |
| pH | 308 |
| Dissolved Oxygen | 494 |
| Turbidity | 76 |
| Total Nitrogen (TN) | 322 |
| Total Phosphorus (TP) | 315 |

Example:
TARGET_DETERMINATION_ID = 308
---

## Filtering by Time

Time filtering can be added directly to the API query.

Example:&$filter=Time ge 2010-01-01 and Time le 2020-12-31


This allows downloading time-specific monitoring data.

---

## Filtering by Sampling Depth

Water quality measurements can be filtered by sampling depth.

Example filter:

This allows downloading time-specific monitoring data.

---

## Filtering by Sampling Depth

Water quality measurements can be filtered by sampling depth.

Example filter:SampleDepth_m eq 1


---

## Filtering by Site (Specific Water Body)

To retrieve data from a specific monitoring location, filter by:

`Site_Id`

Example:
&$filter=Site_Id eq 3825
This allows downloading data for specific lakes or monitoring stations.

---

## Output Data

Downloaded data are saved to:~/WaterDig/Project3/aci_records.csv



---

## Running the Notebook

### Requirements

Install required packages:

pip install pandas requests


### Execution

1. Query the API
2. Retrieve data in batches
3. Combine results
4. Save the dataset as a CSV file

---

## Example Use Case

Download **Total Phosphorus (TP)** measurements:

TARGET_DETERMINATION_ID = 315
INITIAL_SKIP = 0
MAX_SKIP = 200000
STEP = 1000


This will retrieve phosphorus monitoring data across Finnish lakes.

---

## Storage and Disk Usage

Large downloads may require significant disk space. The notebook includes a disk check using Python utilities such as `shutil` to monitor available storage.

---

## Notes

> API response speed may vary.

The script includes a small delay between requests to avoid overwhelming the server.

Example:

DELAY_SECONDS = 0.2


Increase the delay if API throttling occurs.

---

## Potential Extensions

- [ ] Retrieve multiple water quality parameters simultaneously
- [ ] Automatically loop through all Determination IDs
- [ ] Store results in Parquet format for faster analysis
- [ ] Integrate results with lake ecological status models