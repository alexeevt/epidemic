# Epidemic
Timur Alexeev, Insight July-Aug 2018

Epidemic is a project that models a simplified data pipeline in a hospital environment. Occasionally hospitals experience surges in data transfer, which may occur during tragic events such as the 2013 Boston marathon bombing, 2017 Las Vegas shooting, or even flu seasons. During such events, hospitals experience a high patient traffic, that requires hospitals to realocate and request additional resources, staff, and medications.

During administration, high througput of data is read and written. This data may include past history, current diaganoses, text, images, pharmacy orders, and billing. It is important to minimize any delay and lag time to have a reliable infrustructure for patient administration.


Dataset: Simple patient post visit records will be generated for the project.
Each patient's data includes 1.3 GB of images and 10 pages of text records.



Resource type: S3 bucket

Goals:
1. Use Docker for containerization.
2. Deploy multiple pipelines for data aggregationg from the hospital and the clinic using Jenkins.
3. Use Kafka for streaming data.
4. Ansible for configuration and change management. 
5. Deepdive into Kubernetes for scheduling, and automatic deployment when a pipeline goes down.
6. Stretch goal: Fault detection

### Pipeline:

<img src="img/.png" width="800"> 
