<h5>Directory</h5> 

<b>[Tech Portfolio Home](https://github.com/Jays1115/Jalen-Smith.git)</b>
<b>[AWS Projects](https://github.com/Jays1115/AWS-Projects.git)</b>

# Improving-Database-Efficiency

<h2>Description</h2>
Request: An insurance company aims to streamline database management, allowing employees to focus on innovation. They are concerned about protecting data in their development and test environments and seek to enhance resilience against potential disasters. Additionally, they want to improve performance for real-time queries and big data analytics.
<br><br>
Solution: Enhanced the insurance company's relational database operations, performance, and availability by creating an Amazon RDS for MySQL instance. Utilized Amazon RDS read replicas to boost database performance and implemented multi-AZ deployments to improve availability. Additionally, backups were enabled to ensure data protection

<h2>Program walk-through:</h2>

<p align="center">
Navigated to the RDS section within AWS and reviewed the selected region, making sure its set to N. Virginia (us-east-1): <br/>
<img src="images/Screenshot 2024-09-17 at 8.04.21 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
</p>

<p align="center">
Navigate to the databases page via RDS left sidebar: 
<br/>
<img src="images/Screenshot 2024-09-17 at 8.05.02 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
</p>

<p align="center">
Created an RDS database running on the MariaDB engine (version 10.11.8). Since this instance is intended for development, the 'Dev/Test' template was selected to optimize the setup for that environment: 
<br/>
<img src="images/Screenshot 2024-09-17 at 8.07.21 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<img src="images/Screenshot 2024-09-17 at 8.08.45 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
</p>

<p align="center">
I named the database 'my-database' and created self-managed credentials for this instance to maintain full control over access and security. By opting for self-managed credentials, I ensured that password policies, key rotations, and access permissions can be tailored to meet specific security and compliance requirements for the development environment: 
<br/>
<img src="images/Screenshot 2024-09-17 at 8.10.01 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
</p>

<p align="center">
Selected the db.t3.xlarge instance class for the database, providing 4 vCPUs, 16 GiB of RAM, and a network throughput of up to 2,780 Mbps. For storage, I opted for General Purpose SSD with 20 GiB allocated, ensuring a balance of performance and cost-efficiency. Additionally, I enabled storage auto-scaling to dynamically adjust capacity as needed, preventing potential performance issues due to storage limitations. To enhance availability and disaster recovery, I also selected to create a standby instance in a different Availability Zone, ensuring failover support in the event of a regional outage: 
<br/>
<img src="images/Screenshot 2024-09-17 at 8.10.54 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<img src="images/Screenshot 2024-09-17 at 8.12.03 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
</p>

<p align="center">
For connectivity settings, I chose not to connect the database directly to an EC2 compute instance, as it is not required for this setup. The database is configured to use an IPv4 network type to ensure compatibility with existing network infrastructure. Additionally, the database is placed within the default VPC (Virtual Private Cloud) to take advantage of its isolated networking environment, providing enhanced security and control over network traffic: 
<br/>
<img src="images/Screenshot 2024-09-17 at 8.12.33 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
</p>

<p align="center">
In the Additional Configuration settings, I enabled automated backups for the database to ensure data protection and recovery in case of failure. I configured the backups to be retained for 7 days, providing a reliable recovery window while minimizing storage overhead. This setup allows for point-in-time recovery, ensuring the ability to restore the database to any point within the retention period: 
<br/>
<img src="images/Screenshot 2024-09-17 at 8.14.18 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
</p>

<p align="center">
After about 5 to 10 miniutes, the RDS database set up is complete and availible for use: 
<br/>
<img src="images/Screenshot 2024-09-17 at 8.18.56 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
I created a read replica of the newly deployed RDS database to enhance performance and scalability, especially for read-intensive workloads. The replication process took approximately 15 minutes to complete, after which the replica became fully available. This read replica will help offload read traffic from the primary database, improving overall performance and ensuring better load distribution for queries and reporting tasks: 
<br/>
<img src="images/Screenshot 2024-09-17 at 8.21.25 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<img src="images/Screenshot 2024-09-17 at 8.22.35 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<img src="images/Screenshot 2024-09-17 at 8.47.52 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
This project successfully optimized the insurance company's database operations by deploying an Amazon RDS instance with enhanced performance, availability, and scalability. By implementing read replicas, multi-AZ deployments, and automated backups, we ensured resilience, high availability, and improved query performance. This setup not only streamlines database management but also positions the company for future growth and innovation with minimal administrative overhead.
</p>
