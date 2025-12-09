---
title: "Blog 1"
date: 2025-09-09
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# AWS for Industries: Equinox Builds a Scalable, Repeatable Architecture Using AWS IoT Services

**by Girish Nazhiyath on 07 JUL 2025**
_Categories: Amazon Data Firehose, Amazon SageMaker AI, Amazon Simple Storage Service (S3), AWS IoT Core, AWS IoT Greengrass, Industries, Kinesis Data Streams, Retail_

---

With over 100 clubs globally, premium fitness company Equinox requires scalable, repeatable infrastructure that can support its integrated digital and physical experiences. Its connected experiences, which include competitive cycling classes, are a key offering that motivates its members to track and meet their fitness goals in a mobile app.

However, delivering fitness insights in near real time was a challenge for the company. When it first developed its connected experiences, Equinox ran its workloads on a Windows-based server. Each service ran as an individual task. This meant that Equinox’s engineers had to broker updates for each service, which was time-consuming and led to inconsistencies in software updates.

> “It was a nightmare,” says Sindhura Nallapareddy, senior director of engineering at Equinox. “It wasn’t just one component that we had to manage. We had to check on our servers, databases, and the message broker installations every time we made an update.”

Equinox wanted to streamline software updates for its engineers and support near real-time data streaming. So, the company turned to Amazon Web Services (AWS) to rearchitect its stack.

> “We did not want to be held back with operational challenges,” says Nallapareddy. “We wanted to focus on the possibilities that we could create, including fitness challenges in our studios and across our clubs.”

## Connecting Its In-Club Devices to the Cloud Using AWS IoT Core

Equinox evaluated cloud-based solutions to support near real-time data processing and streamline engineering workflows. Prioritizing for stability and ease of use, Equinox tested AWS IoT Core, which easily and securely connect devices to the cloud.

To gather data from its bikes, Equinox uses VAST Internet of Things (IoT) devices that are installed on its workout equipment. These devices followed MPU protocol. Before adopting AWS IoT Core, the company gathered data from its bikes in user datagram protocol (UDP) packets, which were stored on PCs connected to local networks.

After collection, data was processed using custom actions and jobs. These jobs would run for several hours before delivering fitness insights to the mobile app for members.

> “The proof of concept that we created was to see if we could sync data from our edge servers to AWS and if we could reliably establish cloud connectivity to support more seamless deployments,” says Aneesh Pillai, engineer at Equinox.

Using AWS IoT core, the company can collect UDP packets from its bikes using MQTT protocol, which then transmits data into its edge servers and Amazon Simple Storage Service (Amazon S3), an object storage service built to retrieve any amount of data from anywhere.

By storing its data on edge devices and in the cloud, Equinox has reduced the likelihood of data loss, improving overall data quality.

> “We appreciate the reliability of the data that is sent between our edge servers and AWS,” says Pillai. “The speed and ease of managing these components are top-tier benefits for me.”

## Making Unified Software Deployments with AWS IoT Greengrass

Streamlining software deployments was essential to helping engineers focus on building more personalized member experiences. So, Equinox built a software management application for its engineering team using AWS IoT Greengrass, which is an open-source edge runtime and cloud service for building, deploying, and managing device software.

To start, Equinox deployed a single AWS IoT Greengrass instance onto one of its edge servers. After stabilizing, the Equinox team replicated this setup across all its edge servers. Previously, Equinox collected cycling data from 48 of its clubs; using AWS IoT Greengrass, the company was able to onboard 80 clubs in a matter of months.

When a software update is available, Equinox can trigger deployments while classes are occurring without experiencing data loss. Additionally, the company can initiate deployments in a single club or across all its locations.

> “That has been an important improvement for us to overcome the operational challenges we dealt with before,” says Nallapareddy. “AWS IoT Greengrass has alleviated our teams by sending updates in a bundled package.”

## Securing Data Streaming in the Cloud

Equinox implemented Amazon Data Firehose to reliably load near real-time streams into data lakes, warehouses, and analytics services. To stream its data into the cloud, Equinox’s engineers created two sets of rules for collecting data from IoT devices using Amazon Kinesis Data Streams, which can easily stream data at any scale.

One stream collects heartbeats and biometrics. The other stream transmits data related to bike usage, such as battery power. Data is synced into the cloud on an event basis in near real time. The company also added additional logic to its solution to calculate the number of calories burned and miles cycled, which it provides to its members through its mobile app.

> “Amazon Kinesis Data Streams is absolutely amazing,” says Pillai. “I can look right now and see all the data that’s available and which equipment is being used. It’s in near real time, and there’s no data latency or loss.”

To avoid duplicating data from its bikes, Equinox implemented data filtering. The engineering team also set up a second, private network for transmitting UDP packets from its bikes and other workout equipment, helping keep its members’ data secure.

## Boosting Engineering Productivity and Experimenting with AI/ML

With a scalable, repeatable stack running on AWS, Equinox has freed its engineers from complex deployments and integrations. Using a custom script, Equinox can scale its IoT solution to clubs in minutes, and its engineers are saving on deployments every month.

> “We can focus on the business instead of operational challenges,” says Pillai. “We don’t have to worry about the connections between the cloud and local computers. Seamless deployments are one of the biggest benefits of our architecture.”

The automated setup has empowered Equinox’s engineers to focus on value-added tasks, including experimenting with artificial intelligence and machine learning. Its teams plan to use Amazon SageMaker AI to build, train, and deploy machine learning models—including foundation models—for any use case with fully managed infrastructure, tools, and workflows.

Equinox’s engineering team is looking forward to building more personalized member offerings and predictive maintenance recommendations for its workout equipment.

> “The confidence that we have in our data has unlocked so much potential,” says Eswar Veluri, executive vice president and chief technology officer at Equinox. “We can explore club-to-club challenges, cycling milestones, and individual competitions. There is a lot of excitement across the company to uncover and unlock even more experiences.”

---

### Girish Nazhiyath

<img src="https://d2908q01vomqb2.cloudfront.net/c5b76da3e608d34edb07244cd9b875ee86906328/2025/07/07/Girish-Nazhiyath_rev.png" align="left" width="150" style="margin-right: 20px; margin-bottom: 10px;" alt="Girish Nazhiyath" />

Girish Nazhiyath currently serves as a Senior Solutions Architect at AWS. In his current role, Girish provides retail industry and technology expertise to retailers across the US to enable them to leverage best-of-breed AWS technologies and practices. Prior to working at AWS, Girish has over 25 years of retail career experience with global retail and technology companies like Microsoft, IBM, NEC, Fujitsu/ICL, Csoft International, Marconi Commerce Systems and Gilbarco Veeder-Root focusing on store systems, omnichannel, customer experience, biometric payments, and retail innovation. He has worked with retailers within the convenience store, grocery, telecom, big box/department and specialty retail verticals throughout his career and his focus areas include both brick-and-mortar and online Point-Of-Service and corporate/back-office systems.

<br clear="left"/>
