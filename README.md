# Epidemic
Timur Alexeev, Insight July-Aug 2018

## Summary
Epidemic is a project that models a simplified data pipeline in a hospital environment. Occasionally hospitals experience surges in data transfer, which may occur during tragic events such as the 2013 Boston marathon bombing, 2017 Las Vegas shooting, or even flu seasons. During such events, hospitals experience a high patient traffic, that requires hospitals to realocate and request additional resources, staff, and medications.

During administration, high througput of data is read and written. This data may include past history, current diaganoses, text, images, pharmacy orders, and billing. It is important to minimize any delay and lag time in order to have a reliable infrustructure for patient administration.

The project will build a data pipeline that takes streaming data in the form of patient records (images and health history/diagnoses) and billing in the form of batch data, check the data and generate a pharmacy order.

I am interested in looking at automatic granular scaliing and stress testing. While many tools such as terraform or mesos support automatic scaling, it is often difficult to set this up in a granular way. For instance, if you manage a pipeline including a web server and a spark cluster, it is most likely that they do not need to be scaled at the same time.

## Goals
* Orchestrate containers.
* Automation and efficient scaling.

## Technology

Dataset: Simple patient records and post visit summary will be generated for this project. Each patient's data will include 1.3 GB of images and 10 pages of text records. I will use CT images of phantoms from my previous research and generate arbitrary text data to mimic patient health history and diagnosis.

Resource type: S3 bucket

* Deploy multiple pipelines for data aggregationg for billing and clinical records using Jenkins.
* Use Docker for containerization.
* Kubernetes or Mesos for container orchestration and scaling.
* Pass streaming and batch data through Kafka.
* Check quality of data using Spark Streaming.

## Pipeline:

<img src="img/.png" width="800"> 
