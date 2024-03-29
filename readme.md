# aws-rds-s3-route53-listemployee-python 🐳

![Stars](https://img.shields.io/github/stars/tquangdo/aws-rds-s3-route53-listemployee-python?color=f05340)
![Issues](https://img.shields.io/github/issues/tquangdo/aws-rds-s3-route53-listemployee-python?color=f05340)
![Forks](https://img.shields.io/github/forks/tquangdo/aws-rds-s3-route53-listemployee-python?color=f05340)
[![Report an issue](https://img.shields.io/badge/Support-Issues-green)](https://github.com/tquangdo/aws-rds-s3-route53-listemployee-python/issues/new)

![overview](screenshots/overview.png)

## reference
[youtube](https://www.youtube.com/watch?v=7Gym2XVcA5A)

## ssh to ubuntu EC2
```shell
ssh -i "DTQUbuntu184_20220101.pem" ubuntu@ec2-54-213-116-161.us-west-2.compute.amazonaws.com
```
+ install & config
```shell
sudo apt-get update
sudo apt-get install mysql-client
sudo apt-get install python3 python3-pip python3-flask python3-pymysql python3-boto3
```
+ for running application
```shell
git clone https://github.com/tquangdo/aws-rds-s3-route53-listemployee-python.git
cd aws-rds-s3-route53-listemployee-python
sudo python3 EmpApp.py
 * Running on http://0.0.0.0:80/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 163-797-406
```
+ access on browser `Public IPv4 address`
![ipv4](screenshots/ipv4.png)
+ condition to access on browser: MUST open port 80 on `inbound rules`
![port80](screenshots/port80.png)

## mysql
+ create db name `employee`
+ condition to connect RDS: EC2 --> RDS
+ RDS's SG > Inbound > add EC2's SG
![rdssg](screenshots/rdssg.png)
+ connect `$ mysql -h employee.cigsfjyovtsz.us-west-2.rds.amazonaws.com -u intellipaat -p`
```sql
create database employee;
use employee;
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
```
+ `python3 EmpApp.py` will output this ERR because local can NOT connect to RDS
> `pymysql.err.OperationalError: (2003, "Can't connect to MySQL server on 'employee.cigsfjyovtsz.us-west-2.rds.amazonaws.com' (timed out)")`

## s3
+ make public all objects in `dtqaddemployee` bucket: edit in bucket policy:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Statement1",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::dtqaddemployee/*"
            ]
        }
    ]
}
```
+ s3 contains files that user uploaded on browser
![s3](screenshots/s3.png)

## route53: dns for `Public IPv4 address` -> `route53dn.tk`
+ create host zone `route53dn.tk`
+ in host zone create 2 record name
![recname](screenshots/recname.png)
+ buy domain name `route53dn.tk` (💣💣)
+ access on browser `route53dn.tk` (💣💣)
![dn](screenshots/dn.png)
