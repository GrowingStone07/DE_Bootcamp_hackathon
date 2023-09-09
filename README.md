# Real-Time Ad Engagement Analysis
In this project, we developed a real-time data processing pipeline in AWS to ingest, process, and visualize ad data from the click and conversion streams, then Integrated this data with existing dimensional data to derive actionable insights.

### Sample Real-Time Streams and DataSets

Refer this link to get sample data - [Data Sources](https://github.com/GrowingStone07/DE_Bootcamp_hackathon/blob/f1551155749a928925e6f3e3eb38c096f7e2a31b/Data%20Sources.pdf) 

### Pre-Requisites
- AWS Free-Tier Account
- Easy-Medium level Python Knowledge
- Some basic knowledge of various AWS services (related to data engineering)

### Technologies Used
- Python Language
- Lambda Function
- Kinesis Streams
- Dynamo DB
- Redshift
- Glue Catalog and Glue Crawler
- Grafana

### Architecture Diagram

### Implementation- Data Flow
1. Used 2 lambda functions as Producer to generate Mock Data and pushed into Kinesis streams
   - Lambda producer code to generate Ad Click Stream
   - Lambda producer code to generate Ad Conversions Stream


