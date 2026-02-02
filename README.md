# Data Engineering Zoomcamp Homework Module 2: Kestra/Orchestration

[Module 2 homework](https://github.com/DataTalksClub/data-engineering-zoomcamp/blob/main/cohorts/2026/02-workflow-orchestration/homework.md)

### Quiz

1. Within the execution for Yellow Taxi data for the year 2020 and month 12: what is the uncompressed file size (i.e. the output file yellow_tripdata_2020-12.csv of the extract task)?

- [ ] 128.3 MiB
- [x] 134.5 MiB
- [ ] 364.7 MiB
- [ ] 692.6 MiB

Answer found in executions section of the Kestra dashboard.

2. What is the rendered value of the variable file when the inputs taxi is set to green, year is set to 2020, and month is set to 04 during execution?

- [ ] {{inputs.taxi}}_tripdata_{{inputs.year}}-{{inputs.month}}.csv
- [x] green_tripdata_2020-04.csv
- [ ] green_tripdata_04_2020.csv
- [ ] green_tripdata_2020.csv

[09_gcp_taxi_scheduled](.flows/09_gcp_taxi_scheduled.yaml)! variables section: `"{{inputs.taxi}}_tripdata_{{trigger.date | date('yyyy-MM')}}.csv"`

3. How many rows are there for the Yellow Taxi data for all CSV files in the year 2020?

- [ ] 13,537.299
- [x] 24,648,499
- [ ] 18,324,219
- [ ] 29,430,127

```sql
SELECT
  COUNT(*)
FROM `dez-terraform.zoomcamp.yellow_tripdata` 
WHERE tpep_pickup_datetime BETWEEN '2020-01-01' AND '2020-12-31';
```

4. How many rows are there for the Green Taxi data for all CSV files in the year 2020?

- [ ] 5,327,301
- [ ] 936,199
- [x] 1,734,051
- [ ] 1,342,034

```sql
SELECT
  COUNT(*)
FROM `dez-terraform.zoomcamp.green_tripdata` 
WHERE lpep_pickup_datetime >= '2020-01-01' AND lpep_pickup_datetime < '2021-01-01';
```

5. How many rows are there for the Yellow Taxi data for the March 2021 CSV file?

- [ ] 1,428,092
- [ ] 706,911
- [x] 1,925,152
- [ ] 2,561,031

```sql
SELECT
  COUNT(*)
FROM `dez-terraform.zoomcamp.yellow_tripdata` 
WHERE filename = 'yellow_tripdata_2021-03.csv';
```

6. How would you configure the timezone to New York in a Schedule trigger?

- [ ] Add a timezone property set to EST in the Schedule trigger configuration
- [x] Add a timezone property set to America/New_York in the Schedule trigger configuration
- [ ] Add a timezone property set to UTC-5 in the Schedule trigger configuration
- [ ] Add a location property set to New_York in the Schedule trigger configuration

Answer in [docs](https://kestra.io/docs/workflow-components/triggers/schedule-trigger#examples)

---

[Kestra docs: GCP service account](https://kestra.io/docs/how-to-guides/google-credentials)