create database entern
use entern

////Table 1///
CREATE TABLE MasterDesignation (
ID INT PRIMARY KEY IDENTITY(1,1),
DesignationName VARCHAR(50)
);
////Table 2///
Create table Employee1(
ID int Primary key Identity(1,1),
EmployeeName varchar(100),
BirthDate date,
DesignationId int FOREIGN KEY REFERENCES MasterDesignation(ID) ,
Gender int,
EmailId varchar(100),
PhoneNo varchar(50),
);
drop table Employee1


INSERT INTO MasterDesignation VALUES ( 'Manager');
INSERT INTO MasterDesignation VALUES ('CEO');
INSERT INTO MasterDesignation VALUES ('CTO');

INSERT INTO Employee1 VALUES ( 'John', '2001-09-09', 1,1,'abcd@gmail.com',9876541011);
INSERT INTO Employee1 VALUES ( 'Jane','2001-09-09', 2,1,'abcd@gmail.com',9876541011);
INSERT INTO Employee1 VALUES ( 'Bob', '2001-09-09', 3,1,'abcd@gmail.com',9876541011);

///Stored Procedure///
--To insert employee data

CREATE PROCEDURE USP_addemployeedetails 
@ID int=0,
@EmployeeName varchar(100),
@BirthDate date,
@DesignationId int, 
@Gender int,
@EmailID varchar(100),
@PhoneNo varchar(50)
AS
BEGIN
INSERT INTO Employee1(EmployeeName,BirthDate,DesignationId,Gender,EmailID,PhoneNo)
values(@EmployeeName,@BirthDate,@DesignationId,@Gender,@EmailID,@PhoneNo)
END
GO

USP_addemployeedetails 1,'sujata','2001-11-01',2,0,'sujata@gmail.com','1234567895';


--To diplay inserted data in table

CREATE PROCEDURE USP_Getemployeedetails 
AS
BEGIN
select * from Employee1
END

USP_Getemployeedetails


--To edit employee details 
CREATE PROCEDURE USP_Updateemployeedetails 
@ID int=0,
@EmployeeName varchar(100),
@BirthDate date,
@DesignationId int, 
@Gender int,
@EmailID varchar(100),
@PhoneNo varchar(50)
AS
BEGIN
update Employee1 set EmployeeName=@EmployeeName,BirthDate=@BirthDate,DesignationId=@DesignationId,Gender=@Gender,EmailID=@EmailID,PhoneNo=@PhoneNo where ID = @ID
END

USP_Updateemployeedetails 1,'Niranjan','2019-01-01',2,1,'niranjan@gmail.com','8275901072'


--To delete employee details
CREATE PROCEDURE USP_deleteemployeedetails 
@ID int=0
AS
BEGIN
delete Employee1  where ID = @ID
END

USP_deleteemployeedetails 4

--To display designation name in drop_down


CREATE PROCEDURE USP_GetDesignationList
 AS
BEGIN
    SELECT DesignationName FROM MasterDesignation
END;

USP_GetDesignationList

