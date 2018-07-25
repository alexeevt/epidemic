# genoPipe
Timur Alexeev, Insight July-Aug 2018

The Cancer Genome Atlas (TCGA) is a joint effort of the National Cancer Institute (NCI) and the National Human Genome Research Institute (NHGRI) to accelerate our understanding of the molecular basis of cancer. TCGA-funded researchers across the United States have produced a corpus of raw and processed genomic, transcriptomic, and epigenomic data from thousands of cancer patients. I am aming to set up a multipipeline system to enable high data throughput as well as CI/CD.

Dataset: https://registry.opendata.aws/tcga/
Use the data provided by cancer genome atlas, which contains the raw and processed genomic, transcriptomic, and epigenomic data from thousands of cancer patients

Resource type: S3 bucket

About the data: more than a petabyte in size,

•	Problem requires high throughput workflows
•	Various regulatory agencies have to be factored into the solution
•	Each workload must be modified to answer domain specific questions
•	Scientific computing has to be fast, easy, and effective

Goals:
1.	Deploy pipeline
2.	Implement CI
3.	Implement CD
4.	Deepdive into Kubernetes for managing multiple pipelines 
5.	Autoscaling
6.	Fault detection

Realistic project goals are 1-4, with 4 being a deepdive. Goals 5 and 6 are ambitious stretch goals and may not be accomplished in the given timeframe.


Technology description:
•	Docker for containerization
	o	Container platform
	o	Tool for building, distributing, and running containers
•	Kubernetes for container orchestration
	o	Container orchestration system
	o	Automate deployment
	o	Scheduling and scaling containerized applications
•	Jenkins for CI (maybe Travis CI as I read it is simple to set it up on GitHub)
•	Ansible for configuration and change management
	o	Better security than chef
	o	Fast and agent-less
	o	Supports almost any language

