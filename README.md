<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a>
    <img src="readme-assets/DALL.E-panda-dashboard-2.png" width="224" height="224" alt="Logo">
  </a>

  <h1 align="center"><img src="readme-assets/computer-display-lineal.gif" width="29px"> Adidas Sales BI Dashboard</h1>
</div>

<img alt="GitHub Repo stars" src="https://img.shields.io/github/stars/himalayasharma/adidas-sales-dashboard?style=social"> <img alt="GitHub forks" src="https://img.shields.io/github/forks/himalayasharma/adidas-sales-dashboard?style=social"> <img alt="GitHub pull requests" src="https://img.shields.io/github/issues-pr/himalayasharma/adidas-sales-dashboard"> <img alt="GitHub issues" src="https://img.shields.io/github/issues-raw/himalayasharma/adidas-sales-dashboard">

A BI dashboard desgined using AWS QuickSight by leveraging Adidas US sales data consolidated in an AWS RDS PostgreSQL database.
 
Project Organization
------------

    ├── LICENSE                  
    ├── README.md              <- The top-level README for developers using this project
    └──  readme-assets         <- Contains images to be used in README.md

Prerequisites
------------
Before you begin, ensure you have met the following requirements:
* You have a `Linux/Mac/Windows` machine.
* You have installed `PostgreSQL` and a pgsql client like `pgAdmin`.
* You have created an account on `AWS` and `AWS Quicksight`. Accounts have to be created for both separately.

NOTE: I've used [AWS Free Tier](http://surl.li/epsmz) to do this project.

Architecture diagram
------------

The architecuture diagram is as follows:

![alt text](readme-assets/aws-architecture-diagram.png)

A brief overview of steps to reproduce the project is as follows:

- Download the Adidas US Sales Dataset PostgreSQL dump from [data.world](https://data.world/stellabigail/adidas-us-sales-datasets) to your local system.
- Create a publicly accessible [AWS Relational Database Service (RDS)](http://surl.li/epsnp) instance with [PostgreSQL](https://www.postgresql.org/) database engine, and restrict access to your personal IP address by adjusting the inbound rules in the security group.
- Connect AWS RDS instance to [pgAdmin](https://www.pgadmin.org/) on local system using the instance server endpoint and credentials.
- Import the PostgreSQL dump of the Adidas sales data into a newly created empty database on AWS RDS.
- Run filtering and analysis queries, and adjust data types as necessary (e.g. converting `VARCHAR` to `FLOAT` and `INT`) on [AWS QuickSight](https://aws.amazon.com/quicksight/).
- On AWS, restrict public access to the RDS instance and create 2 security groups, one for RDS and the other for QuickSight. Enable bi-directional traffic flow between the two services by modifying inbound and outbound rules in both security groups. Finally, associate the RDS security group with the RDS instance.
- On AWS QuickSight, log in and create a VPC connection to the RDS instance for private communication. By setting up security groups on AWS and a VPC connection on QuickSight, back-and-forth communication between the two will be facilitated within the VPC.

QuickSight Dashboard
------------

This a screenshot of the dashboard:

![alt text](readme-assets/aws-quicksight-dashboard.png)

I'll give a brief description of each dashboard component/plot and insights gained from it:

1. Line graph

    ![alt text](readme-assets/qs-db-line-graph.png)

    The graph showcases the sales performance of various product lines from 2020 to 2021. It is evident that "Men's Street Footwear" (represented by the orange line) was the top-performing product line, while "Women's Street Footwear" (represented by the magenta line) had the lowest sales.

    ![alt text](readme-assets/qs-db-line-graph-1.png)

    Additionally, the QuickForest algorithm, which is integrated within QuickSight, generates forecasts. The projected total sales for the month of January 2022 are estimated to be $118 million.

2. Donut chart

    ![alt text](readme-assets/qs-db-donut-chart.png)

    The graph displays the distribution of total sales among retailers from 2020 to 2021. Westgear recorded the highest sales, accounting for 27% of the total, followed closely by Footlocker with 24%. On the other hand, Walmart had the smallest share, accounting for 8% of total sales.

3. Map

    ![alt text](readme-assets/qs-db-map.png)

    The map illustrates the distribution of product units sold across various states. New York recorded the highest number of units sold, followed by California and Texas. Conversely, Nebraska had the lowest number of units sold.
    
License
------------
Distributed under the MIT License. See `LICENSE.txt` for more information.

--------