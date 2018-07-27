# Epidemic
Timur Alexeev, Insight July-Aug 2018

Epidemic is a project designed to model an early detection of virus epidemic in a geographical region based on patient records. A simple data analytics app will calculate a linear regression model (LRM) from patients post visit. The system is comprised of two ques: 1) a high throughput hospital that will deliver patient records as streaming data 2) a small clinic that will deliver 100 records every 24 hours in a batch. An analytics app will calculate an LRM from patient data correlating post visit summary that will include patient's standard attributes such as name/age/sex, as well as temperature and whether the patient has been out of the country. When a pipeline goes down, it should be built back up using IaC. Scheduling and automatic deployment has to be implemented. Lastly streaming data has to be consistent.

Dataset: Simple patient post visit records will be generated for the project.

Resource type: S3 bucket

Goals:
1. Use Docker for containerization.
2. Deploy multiple pipelines for data aggregationg from the hospital and the clinic using Jenkins.
3. Use Kafka for streaming data.
4. Ansible for configuration and change management. 
5. Deepdive into Kubernetes for scheduling, and automatic deployment when a pipeline goes down.
6. Stretch goal: Fault detection





