# EC2-MySQL-Setup-SampleDB

Based on the provided information, here's a small README file that you could use for your GitHub repository, guiding users through the installation process on an EC2 instance:

---

# Installation Guide for EC2 Instance

This guide provides step-by-step instructions for setting up MySQL and cloning a sample database on an Amazon EC2 instance.

## Prerequisites
- An AWS account
- An EC2 instance running Amazon Linux 2/Amazon Linux AMI

## Steps

1. **Update YUM Package Repository**
   ```bash
   sudo yum update -y
   ```

2. **Download MySQL Community Release**
   ```bash
   sudo wget https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm
   ```

3. **Install MySQL Community Release**
   ```bash
   sudo yum localinstall mysql57-community-release-el7-11.noarch.rpm
   ```

4. **Import MySQL GPG Key**
   ```bash
   sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
   ```

5. **Install MySQL Community Server**
   ```bash
   sudo yum install mysql-community-server
   ```

6. **Start MySQL Service**
   ```bash
   sudo systemctl start mysqld.service
   ```

7. **Find Temporary MySQL Password**
   ```bash
   sudo grep 'temporary password' /var/log/mysqld.log
   ```

8. **Secure MySQL Installation**
   ```bash
   sudo mysql_secure_installation
   ```

9. **Access MySQL**
   ```bash
   mysql -h localhost -uroot -p
   ```

10. **Install Git**
    ```bash
    sudo yum install git
    ```

11. **Clone Sample Database**
    ```bash
    git clone https://github.com/datacharmer/test_db
    ```

12. **Navigate to Database Directory**
    ```bash
    cd test_db
    ```

13. **Load the Sample Database**
    ```bash
    mysql -h localhost -uroot -p < employees.sql
    ```

14. **Verify Installation**
    Within the MySQL shell, you can verify the installation by running the following commands:
    ```sql
    show databases;
    use employees;
    show tables;
    select count(*) from salaries;
    select * from employees limit 10;
    ```

## Additional Information

This setup uses MySQL 5.7. For different MySQL versions, the setup steps might vary slightly. Ensure to adjust the MySQL version in your commands accordingly.

## Acknowledgments

This guide utilizes the `datacharmer/test_db`, a sample MySQL database with an integrated test suite, useful for testing applications and database servers.
