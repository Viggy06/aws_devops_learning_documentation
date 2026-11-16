# Querying CSV Data in S3 with Glue and Athena

**Concept**
Glue Crawler discovers the structure of data and records its metadata in the Glue Data Catalog. Athena uses SQL to query data stored in S3.

**What I worked on**
I uploaded a CSV file to S3, used a Glue Crawler to create its catalog metadata, and queried the data through Athena.

**How I did it**
- Uploaded the CSV file to an S3 bucket.
- Created an IAM role that allowed the crawler to read the bucket.
- Configured and ran a Glue Crawler against the file location.
- Created or selected a Glue database for the catalog table.
- Opened the table in Athena and ran a SQL query.

**Problem it solves**
It allows basic analysis of files in S3 without first loading them into a traditional database or managing query servers.
