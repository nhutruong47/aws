---
title: "Proposal"
date: 2025-09-09
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only; please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

In this section, you need to summarize the workshop contents that you **plan** to do.

# IoT Weather Platform for Lab Research

## Unified AWS Serverless Solution for Real-time Weather Monitoring

### 1. Executive Summary

The IoT Weather Platform is designed for the _ITea Lab_ team in Ho Chi Minh City to enhance weather data collection and analysis capabilities. The platform supports up to 5 weather stations, scalable to 10–15 stations, using Raspberry Pi edge devices combined with ESP32 sensors to transmit data via MQTT. The platform leverages AWS Serverless services to provide real-time monitoring, predictive analytics, and cost savings, with access limited to 5 lab members via Amazon Cognito.

### 2. Problem Statement

_Current Issue_
Current weather stations require manual data collection, which is difficult to manage as the number of stations increases. There is no centralized system for data or real-time analysis, and third-party platforms are often expensive and overly complex.

_Solution_
The platform uses AWS IoT Core to ingest MQTT data, AWS Lambda and API Gateway for processing, Amazon S3 for storage (including a data lake), and AWS Glue Crawlers along with ETL jobs to extract, transform, and load data from the S3 data lake to another S3 bucket for analysis. AWS Amplify with Next.js provides the web interface, and Amazon Cognito ensures secure access. Similar to Thingsboard and CoreIoT, users can register new devices and manage connectivity, but this platform operates on a smaller scale and serves internal purposes. Key features include a real-time dashboard, trend analysis, and low operating costs.

_Benefits and Return on Investment (ROI)_
The solution creates a foundational platform for lab members to develop a larger IoT platform, while providing a data source for AI researchers for model training or analysis. The platform reduces manual reporting for individual stations through a centralized system, simplifies management and maintenance, and improves data reliability. Estimated monthly cost is $0.66 (according to AWS Pricing Calculator), totaling $7.92 for 12 months. All IoT devices are already equipped from the existing weather station system, incurring no additional development costs. Payback period is 6–12 months due to significant savings in manual operation time.

### 3. Solution Architecture

The platform applies AWS Serverless architecture to manage data from 5 Raspberry Pi-based stations, scalable to 15 stations. Data is ingested via AWS IoT Core, stored in an S3 data lake, and processed by AWS Glue Crawlers and ETL jobs to transform and load into another S3 bucket for analysis purposes. Lambda and API Gateway handle additional processing, while Amplify with Next.js provides a dashboard secured by Cognito.

![IoT Weather Station Architecture](/images/2-Proposal/edge_architecture.jpeg)

![IoT Weather Platform Architecture](/images/2-Proposal/platform_architecture.jpeg)

_AWS Services Used_

- _AWS IoT Core_: Ingests MQTT data from 5 stations, scalable to 15.
- _AWS Lambda_: Processes data and triggers Glue jobs (2 functions).
- _Amazon API Gateway_: Communicates with the web application.
- _Amazon S3_: Stores raw data (data lake) and processed data (2 buckets).
- _AWS Glue_: Crawlers catalog data, ETL jobs transform and load data.
- _AWS Amplify_: Hosts the Next.js web interface.
- _Amazon Cognito_: Manages access rights for lab users.

_Component Design_

- _Edge Device_: Raspberry Pi collects and filters sensor data, sending it to IoT Core.
- _Data Ingestion_: AWS IoT Core receives MQTT messages from edge devices.
- _Data Storage_: Raw data stored in S3 data lake; processed data stored in another S3 bucket.
- _Data Processing_: AWS Glue Crawlers catalog data; ETL jobs transform it for analysis.
- _Web Interface_: AWS Amplify hosts the Next.js application for the dashboard and real-time analysis.
- _User Management_: Amazon Cognito limited to 5 active accounts.

### 4. Technical Implementation

_Implementation Phases_
The project consists of 2 parts — setting up the edge weather station and building the weather platform — each going through 4 phases:

1. _Research and Architecture Design_: Research Raspberry Pi with ESP32 sensors and design AWS Serverless architecture (1 month before internship).
2. _Cost Estimation and Feasibility Check_: Use AWS Pricing Calculator to estimate and adjust (Month 1).
3. _Architecture Adjustment for Cost/Solution Optimization_: Refine (e.g., optimizing Lambda with Next.js) to ensure efficiency (Month 2).
4. _Development, Testing, Deployment_: Program Raspberry Pi, AWS services with CDK/SDK and Next.js application, then test and put into operation (Months 2–3).

_Technical Requirements_

- _Edge Weather Station_: Sensors (temperature, humidity, rainfall, wind speed), ESP32 microcontroller, Raspberry Pi as edge device. Raspberry Pi runs Raspbian, uses Docker to filter data, and sends 1 MB/day/station via MQTT over Wi-Fi.
- _Weather Platform_: Practical knowledge of AWS Amplify (Next.js hosting), Lambda (minimized due to Next.js handling), AWS Glue (ETL), S3 (2 buckets), IoT Core (gateway and rules), and Cognito (5 users). Use AWS CDK/SDK for programming (e.g., IoT Core rules to S3). Next.js helps offload Lambda for the fullstack web application.

### 5. Roadmap & Milestones

- _Pre-internship (Month 0)_: 1 month for planning and assessing the old station.
- _Internship (Months 1–3)_:
  - Month 1: Learn AWS and upgrade hardware.
  - Month 2: Design and adjust architecture.
  - Month 3: Deploy, test, and launch.
- _Post-deployment_: Further research within 1 year.

### 6. Budget Estimation

Costs can be viewed on the [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01)
Or download the [budget estimation file](../attachments/budget_estimation.pdf).

_Infrastructure Costs_

- AWS Lambda: $0.00/month (1,000 requests, 512 MB storage).
- S3 Standard: $0.15/month (6 GB, 2,100 requests, 1 GB scanned).
- Data Transfer: $0.02/month (1 GB in, 1 GB out).
- AWS Amplify: $0.35/month (256 MB, 500 ms request).
- Amazon API Gateway: $0.01/month (2,000 requests).
- AWS Glue ETL Jobs: $0.02/month (2 DPUs).
- AWS Glue Crawlers: $0.07/month (1 crawler).
- MQTT (IoT Core): $0.08/month (5 devices, 45,000 messages).

_Total_: $0.7/month, $8.40/12 months

- _Hardware_: $265 one-time (Raspberry Pi 5 and sensors).

### 7. Risk Assessment

_Risk Matrix_

- Network Loss: Medium impact, medium probability.
- Sensor Failure: High impact, low probability.
- Budget Overrun: Medium impact, low probability.

_Mitigation Strategies_

- Network: Local storage on Raspberry Pi with Docker.
- Sensors: Periodic checks, spare parts backup.
- Cost: AWS budget alerts, service optimization.

_Contingency Plan_

- Revert to manual collection if AWS encounters issues.
- Use CloudFormation to restore configurations related to costs.

### 8. Expected Outcomes

_Technical Improvements_: Real-time data and analysis replace manual processes. Scalable to 10–15 stations.
_Long-term Value_: 1-year data platform for AI research, reusable for future projects.
