# grafana
grafana in my way

  In today's technology-driven world, there is an enormous amount of data unlike before. Users, assets, and tools contribute to creating this data, which companies use to analyze and plan their projects. However, there is an important step between collecting the data and analyzing it: presenting the data visually. This is where Grafana comes into picture.
  Grafana is an interactive visualization web application. It is open-source analytics application and compatible with multi-platform. As per needs, we can purchase enterprise license or Grafana Cloud services with additional capabilities. Grafana OSS provides charts, graphs, beautiful visual presentations and alerts for the connected data sources. Grafana services expandable through plugins. Grafana dashboards give insightful visual presentation of our data, which is collected from different sources. It’s allowing to explore the data together. 
Prerequisites:
	Grafana is light weight Open-source software. We can use it with minimum hardware. 2 core CPU and 2 GB RAM is minimum recommended resources. But it’s always better to have more resource for future expansion. If you want to collect real-time data and Visualization with complex combinations, you need more hardware. Grafana can install almost in all operating systems. It supports Windows, MacOS and all Linux flavors. RHEL is recommended OS. By default, Grafana uses SQLite. It comes along with Grafana package and stored in home directory. Grafana can install as package in our server. Otherwise, Grafana can install as docker container or Kubernetes pod. We can get Grafana docker image from docker hub and helm chart for Kubernetes pod. 

Points to keep in mind: -  
•	Launch in same placement group where your existing servers are running.
•	Disabling volume encryptions is a better choice. If you enable, it may cause errors while restarting the Grafana server.

Steps to install: 
1.	Sudo yum update -y  (To update packages in RHEL, Amazon Linux, apt for Ubuntu)
2.	Sudo vi /etc/yum.repos.d/Grafana.repo 		(to open the file )
3.	Add below text to the file and save
[grafana]
name=grafana
baseurl=https://packages.grafana.com/oss/rpm
repo_gpgcheck=1
enabled=1
gpgcheck=1
gpgkey=https://packages.grafana.com/gpg.key
sslverify=1
sslcacert=/etc/pki/tls/certs/ca-bundle.crt
4.	Sudo yum install Grafana -y 	( To install Grafana OSS )
5.	Sudo systemctl daemon-reload  ( To reload the system )
6.	sudo systemctl start grafana-server ( To start Grafana software )
7.	sudo systemctl status grafana-server ( To check Grafana server status )

Create an IAM Role for Grafana Server:
	If you installed Grafana in AWS, you need to create an IAM Role for Grafana server to access the data sources. We have added several data sources to Grafana dashboard. 

Grafana Dashboard:
	PORT 3000 should be opened in your security groups, Grafana server status check should be active. Now you can open your Grafana by accessing your Public IP/Elastic IP:3000/
Initial username and password are same. Both are admin only. While initial access, you can change your admin user id’s password. Once in Grafana, you can click on the data sources and dashboards. In administration tab you can add plugins and data sources as well. From there you can create your own dashboard as per your requirements. We used AWS IoT Twinmaker, Timestream plugins for connecting data sources to Grafana dashboard.
Features of Grafana:
A Grafana dashboard supports multiple panels in a single grid. You can visualize results from multiple data sources simultaneously. It is a powerful open-source analytical and visualization tool that consists of multiple individual panels arranged in a grid. The panels interact with configured data sources, including AWS CloudWatch, Twin Maker, Timestream DB, Prometheus, MySQL, InfluxDB, and the list is huge.
•	Visualize: Grafana has many visualization options to help you understand your data, from graphs, bars, pie charts to histograms.
•	Alerts: Grafana lets you define thresholds visually and get notified via Slack, mails…etc.
•	Unify: You can bring your data together to get a better context. Grafana supports dozens of databases natively.
•	Explore Logs: Using label filters, you can quickly filter and search through the laundry list of logs.
•	Display dashboards: Visualize data with templated or custom reports.

Limitations: 
Grafana can only use the data from external systems like Prometheus, MySQL, Azure Monitor and Amazon CloudWatch. That means Grafana has no means to collect data on its own, through agents or other data pipelines, and is thus dependent on other systems to provide data. Also, it supports only limited data type visualizations.

Reference:        https://grafana.com/docs/grafana/latest/
