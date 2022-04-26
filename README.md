# Sql-Practice--04-


create database project
use project

create table Employee_Detail(ID int primary key not null,F_Name varchar(20),
L_NAme varchar(20),Salary money,Joining_Date date,Department varchar(20),Gender varchar(20))

insert into Employee_Detail values
(1,'vikul','ahalabat',60000,'2013-02-15','IT','Male'),
(2,'nikki','jain',53000,'2014-01-09','HR','Female'),
(3,'ramisha','sharma',50000,'2013-02-15','IT','Female'),
(4,'jack','rana',60000,'2013-02-15','HR','Male'),
(5,'rocky','ram',45000,'2013-02-20','IT','Male'),
(6,'revansh','kumar',60000,'2013-02-15','IT','Male')

create table Project_Detail(PD_ID int primary key identity , ED_ID int , Project_Name varchar(20))

insert into Project_Detail values
(1,'Task Track'),
(1,'HRM'),
(2,'CRM'),
(3,'Policy Management'),
(3,'Sales Management'),
(3,'GRS'),
(4,'DDS'),
(6,'CLP'),
(7,'Survey Management')

select * from Employee_Detail
select * from Project_Detail

select f_name,project_name from Employee_Detail a inner join Project_Detail b on a.ID = b.ED_ID order by f_name

select f_name,project_name from Employee_Detail a left join Project_Detail b on a.ID = b.ED_ID order by f_name

select f_name,isnull(Project_Name,'No Project') from Employee_Detail a left join Project_Detail b on a.ID = b.ED_ID order by f_name

select f_name,project_name from Employee_Detail a right join Project_Detail b on a.ID = b.ED_ID order by f_name

select f_name,project_name from Employee_Detail a full join Project_Detail b on a.ID = b.ED_ID order by f_name

select F_Name,isnull(Project_Name,'Not Project Assigned') from Employee_Detail a left join Project_Details b on a.ID = b.ED_ID order by f_name

select project_name from Employee_Detail a right join Project_Details b on a.ID = b.ED_ID  where f_name is null

select f_name,project_name from Employee_Detail a inner join Project_Detail b on a.ID = b.ED_ID where ID in
(select ED_ID from Project_Details group by ED_ID having count(*)>1)
