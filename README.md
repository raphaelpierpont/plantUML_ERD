# ERD Diagrams with PlantUML

## Description
This repository contains **Entity-Relationship Diagrams (ERD)** created using **PlantUML**, with additional functionality for filtering diagram elements. This allows you to hide specific entities or relationships that you may not want to visualize at the moment, making the diagrams more manageable and focused.

## Prerequisites
To use the ERD diagrams, you need the following:
- **PlantUML**: [Install PlantUML](http://plantuml.com/download)
- **Java**: PlantUML requires Java to run. Download Java from [here](https://www.java.com/en/download/).

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/raphaelpierpont/plantUML_ERD.git
   cd your-repository

2. Create a .puml file and import the script
  ```plantuml
  @startuml
  !include ERD_procedures.puml
  '----------------------------------------
  ' Configuration for node visibility, colors, and links
  '----------------------------------------
  !$hide = {
      "terms": []
  }
  !$search = {
      "terms": [
          {"term":"EMP"},
          {"term":"DEPT"},
          {"term":"SALARY"},
          {"term":"JOB"}
      ]
  }
  !$showMainLinks = 4
  !$showAlternateLinks = 0
  '----------------------------------------
  ' Table Definitions for Extended EMP DEPT Database
  '----------------------------------------
  $table("EMP")
  $pk("EMP", "emp_id", "INT")
  $cl("EMP", "emp_name", "VARCHAR(50)")
  $cl("EMP", "job", "VARCHAR(50)")
  $fk("EMP", "dept_id", "INT")
  $fk("EMP", "manager_id", "INT")
  $cl("EMP", "hire_date", "DATE")
  $cl("EMP", "salary", "DECIMAL(10,2)")
  $cl("EMP", "comm", "DECIMAL(7,2)")
  '----------------------------------------
  $table("DEPT")
  $pk("DEPT", "dept_id", "INT")
  $cl("DEPT", "dept_name", "VARCHAR(50)")
  $cl("DEPT", "location", "VARCHAR(50)")
  '----------------------------------------
  $table("SALARY_GRADE")
  $pk("SALARY_GRADE", "grade", "INT")
  $cl("SALARY_GRADE", "low_salary", "DECIMAL(10,2)")
  $cl("SALARY_GRADE", "high_salary", "DECIMAL(10,2)")
  '----------------------------------------
  ' Relationships between tables
  '----------------------------------------
  $n1("EMP", "DEPT", "dept_id", "dept_id")
  $n1("EMP", "EMP", "manager_id", "emp_id") 
  ' self-join for manager relationships
  $n1("EMP", "SALARY_GRADE")
  @enduml
```
## Results
### Emp Dept:
![image](https://github.com/user-attachments/assets/6b1f11ce-fdb1-41d3-a57d-9128be2c0dbe)
### World:
![image](https://github.com/user-attachments/assets/c21e3990-fa9d-4627-8e09-82044498853b)
### Sakila:
![image](https://github.com/user-attachments/assets/3ba71f8b-866b-4c54-8a2a-06836de94803)


---

This version includes the filtering feature, helping users customize their diagrams by hiding unnecessary elements. Let me know if you need more updates!
