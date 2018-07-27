# Epidemic
Timur Alexeev, Insight July-Aug 2018

Epidemic is a project designed to model early detection of virus epidemic. A simple data analytics app will calculate a linear regression model (LRM) from patient post visti records. The system is comprised of two ques: 1) a high throughput hospital that will deliver patient records as streaming data 2) a small clinic that will deliver 100 records every 24 hours in a batch. An analytics app will calculate an LRM from patient data correlating post visit summary that will include patient's standard attributes such as name/age/sex, as well as temperature and whether the patient has been out of the country.

Dataset: Simple patient post visit records will be generated for the project.

Resource type: S3 bucket

Goals:
1.	Use Docker for containerization.
2.	Deploy multiple pipelines for data aggregationg from the hospital and the clinic using Jenkins.
3.	Deepdive into Kubernetes for automatic deployment, scheduling, and automatic deployment when a pipeline goes down. 
4.	Stretch goal: Fault detection

• Use Kafka for streaming data.

• Ansible for configuration and change management.
	o Better security than Chef.
	o Fast and agent-less.
	o Supports almost any language.


