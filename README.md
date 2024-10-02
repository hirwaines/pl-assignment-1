 # Employee Management System

   ## Problem Statement
   This system manages employee records, including assigning employees to departments and projects. The database allows for managing departments, employees, projects, and assignments between employees and projects.

   ## SQL Commands
   The following SQL commands were used in this system:
   1. Table Creation: Created tables for Departments, Employees, Projects, and Employee_Project_Assignments.
   2. Insert Operations: Added records to each table to represent employees, departments, and project assignments.
   3. Update Operations: Updated employee records.
   4. Delete Operations: Deleted an assignment record from the Employee_Project_Assignments table.
   5. Join Operations: Retrieved data by joining tables (e.g., employees and their respective departments, employees and projects).

   ## Screenshots
   those are the codes :
     CREATE TABLE Departments (
       DepartmentID INT PRIMARY KEY,
       DepartmentName VARCHAR(50) NOT NULL
   );

   create
   
 CREATE TABLE Employees (
       EmployeeID INT PRIMARY KEY,
       FirstName VARCHAR(50),
       LastName VARCHAR(50),
       DepartmentID INT,
       FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
   );
   
   create
   
 CREATE TABLE Projects (
       ProjectID INT PRIMARY KEY,
       ProjectName VARCHAR(100)
   );

   create
   
 CREATE TABLE Employee_Project_Assignments (
       AssignmentID INT PRIMARY KEY,
       EmployeeID INT,
       ProjectID INT,
       FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
       FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
   );
   
   insert
   
 INSERT INTO Departments (DepartmentID, DepartmentName) 
   VALUES (1, 'Human Resources'), (2, 'Engineering'), (3, 'Sales');
  INSERT INTO Employees (EmployeeID, FirstName, LastName, DepartmentID) 
   VALUES (1, 'John', 'Doe', 2), (2, 'Jane', 'Smith', 1), (3, 'Michael', 'Johnson', 3);
  INSERT INTO Projects (ProjectID, ProjectName) 
   VALUES (1, 'Project A'), (2, 'Project B');
 INSERT INTO Employee_Project_Assignments (AssignmentID, EmployeeID, ProjectID) 
   VALUES (1, 1, 1), (2, 2, 2), (3, 3, 1);
   
   update
   
  UPDATE Employees 
   SET LastName = 'Brown' 
   WHERE EmployeeID = 1;
   
   delete
   
 DELETE FROM Employee_Project_Assignments 
   WHERE AssignmentID = 2;
   
   inner join

  SELECT Employees.FirstName, Employees.LastName, Departments.DepartmentName 
   FROM Employees 
   INNER JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
   
inner join 

 SELECT Employees.FirstName, Projects.ProjectName 
   FROM Employees 
   INNER JOIN Employee_Project_Assignments ON Employees.EmployeeID = Employee_Project_Assignments.EmployeeID
   INNER JOIN Projects ON Employee_Project_Assignments.ProjectID = Projects.ProjectID;
   


