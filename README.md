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
![Architecture Diuagram](https://github.com/GrowingStone07/DE_Bootcamp_hackathon/blob/f91db72a61a3d107f447c96e668e5f1a39b796cf/Architecture.PNG)

### Implementation- Data Flow
1. Used 2 lambda functions as Producer to generate Mock Data and pushed into Kinesis streams
   - Lambda producer code to generate Ad Click Stream
   - Lambda producer code to generate Ad Conversions Stream
2. Used lambda function as consumer code to consume data from Kinesis stream.
3. DLQ (Dead letter Queue) is attached to Lambda Consumer to store data which are arriving late.
4. From lambda consumer, data is ingested into Glue pipelines
5. In glue pipeline, we are joining streaming data with Dimension tables
6. The joined data is stored into Redshift(Data Warehouse) and DynamoDB(NoSQL).
7. Glue is attached with SNS(Simple Notification Service) to get notified if glue job fails.
8. Then we are connectig DynamoDB with Graphana to perform real-time dashboarding, you can find the queries we used for analysis [here](https://github.com/GrowingStone07/DE_Bootcamp_hackathon/blob/4ffc00cd137f43444c0a9fb3598507912dba7024/hackathon_queries.txt)

### Step-By-Step Excecution
1. Create mentioned 2 dimension tables in Redshift
2. Run both lambda producer code to generate Ad-click stream and Ad-Conversion stream
3. Check Kinesis stream whether data is arrived or not
4. Run lambda consumer code to consume the data from Kinesis stream.
5. Trigger the glue job to consume data from Lambda Consumer
6. Glue job will perform joining the stream data with dimension tables present in Redshift and will put the joined data into Redshift and DynamoDB
7. DynamoDB is connected to Graphana for dashboarding, which will show real-time insights on refresh


