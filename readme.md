# aws-rds-s3-upimage-python 🐳

![Stars](https://img.shields.io/github/stars/tquangdo/aws-rds-s3-upimage-python?color=f05340)
![Issues](https://img.shields.io/github/issues/tquangdo/aws-rds-s3-upimage-python?color=f05340)
![Forks](https://img.shields.io/github/forks/tquangdo/aws-rds-s3-upimage-python?color=f05340)
[![Report an issue](https://img.shields.io/badge/Support-Issues-green)](https://github.com/tquangdo/aws-rds-s3-upimage-python/issues/new)

## reference
[youtube](https://trungquandev.com/viet-mot-crud-api-su-dung-serverless-framework-dynamodb/)

## mysql
+ connect `$ mysql -h employee.cigsfjyovtsz.us-west-2.rds.amazonaws.com -u intellipaat -p`
```sql
create database employee;
use employee
create table employee(
    empid varchar(20),
    fname varchar(20),
    lname varchar(20),
    pri_skill varchar(20),
    location varchar(20)
);
```
+
```sql
show tables;
+--------------------+
| Tables_in_employee |
+--------------------+
| employee           |
+--------------------+
```

## deploy python in local
```shell
pip3 install flask pymysql boto3
python3 EmpApp.py
```

## aws deploy
1. 
![lambda](screenshots/lambda.png)


sudo apt-get update
# For Sql-client
sudo apt-get install mysql-client

# For python and related frameworks

sudo apt-get install python3 python3-pip python3-flask python3-pymysql python3-boto3

# for running application
sudo python3 Empapp.py
