
# HEALTHCARE ANALYTICS

This report presents the developmental process and final implementation of a comprehensive database system designed for Splendor HealthCare, aimed at managing patient registrations, appointments, medical records, and doctor-patient interactions. The system was built in accordance with the specific needs of the healthcare industry, with particular focus on user experience for both patients and staff, data integrity, and adherence to the principles of database normalization up to the third normal form (3NF).

## Introduction

### Purpose of the Database
The database has been developed to support Splendor HealthCare in its transition to a more digitized and efficient record-keeping system. This system is designed to handle various aspects of hospital management, including patient registrations, appointment scheduling, medical record maintenance, and feedback collection.

### Scope of the Project
The project involves the design, creation, and population of the database, including thorough planning to ensure that the system meets the complex requirements of the healthcare sector. Additionally, the project involved the formulation of T-SQL queries for data manipulation and retrieval, all tailored to the specific needs outlined by the healthcare provider.

### Client Requirements
The design and development of the database system were guided by the following requirements specified by the client:
- A registration system that captures comprehensive patient information.
- An appointment scheduling system that verifies doctor availability.
- Detailed record-keeping of appointments, including their status and associated doctors.
- Functionality for doctors to review and update medical records post-consultation.
- A feedback system to capture patient experiences post-appointment.
- A mechanism to handle rebooking of cancelled appointments.
- The retention of patient information with recorded exit dates for those leaving the hospital system.

## Database Design

### Design Overview
The design of the database reflects a thoughtful approach to creating a relational system that captures the complex relationships between different entities in a hospital setting. The database was structured to facilitate the efficient storage and retrieval of information while ensuring the integrity and security of the data.

### Normalization and Schema Design
The database was normalized up to the third normal form (3NF) to eliminate redundant data, prevent anomalies, and ensure that dependencies are logical. The schema was carefully crafted to reflect real-world relationships and constraints, making use of appropriate data types and ensuring that each table serves a clear purpose.

<img width="960" alt="Screenshot 2024-08-01 010747" src="https://github.com/user-attachments/assets/49a8b5af-8c3f-4f59-b252-ceba26ff1c32">


The database schema diagram (Figure 1) illustrates the logical structure of the Healthcare Database, including entities, attributes, and relationships. This visual representation is foundational for understanding the interactions within the database and ensuring data integrity.

#### Entities and Their Attributes:
- Patients: Contains personal and contact information for each patient. Every patient record is uniquely identified by a PatientID.
- Doctors: Stores details of each doctor, including their department affiliation through DepartmentID.
- Departments: Lists the hospital departments, serving as a lookup table for doctor specialties.
- Appointments: Records details of patient appointments, linking to both the Patients and Doctors tables.
- Medical Records: Holds detailed medical information for each appointment made by a patient.

#### Relationships:
- Patients to Appointments: One-to-Many (A patient can have multiple appointments over time).
- Doctors to Appointments: One-to-Many (A doctor can be associated with many appointments).
- Appointments to Medical Records: One-to-One (Each appointment can generate one medical record).
- Doctors to Departments: Many-to-One (Many doctors can belong to one department, reflecting their specialty).

#### Justifications for Design Decisions:
- Separate tables for Patients, Doctors, and Departments to avoid data duplication and ensure that updates to one type of information (e.g., a change in department name) do not require changes across multiple doctor or appointment records.
- Appointments and Medical Records are related to ensure that each medical interaction is documented and traceable.
- The inclusion of feedback within the Appointments table allows for direct association with the corresponding appointment, facilitating immediate access to patient evaluations.

#### Integrity and Normalization:
The design ensures the database is normalized to the Third Normal Form (3NF) by eliminating transitive dependencies and repeating groups. Primary keys and foreign keys are utilized to reinforce data integrity and establish clear relationships.

## T-SQL Statement Description

### Database and Table Creation
A new database named Healthcare_DB was initialized, followed by the creation of several tables essential for hospital management: Patients, Doctors, Appointments, Departments, and MedicalRecords. The tables were defined using T-SQL CREATE TABLE statements, carefully selecting appropriate data types like INT for numeric identifiers, VARCHAR for variable-length strings, and NVARCHAR for special character support. The inclusion of constraints such as NOT NULL, UNIQUE, and MAX ensured data integrity and consistency across the database.

![Figure 2 showing the tables created, the data types and constraints that was applied](link_to_figure_2_image)

### Table Modification and Enhancement
To refine the database structure and accommodate additional information, ALTER TABLE commands were utilized to modify existing tables. Columns were added to capture crucial data such as dates of birth, gender, feedback, and allergies.

![Figure 3 showing the alter commands.](link_to_figure_3_image)

## Data Population Techniques

### Insertion of Data Records
The INSERT INTO statement was employed to populate the database tables with manual data entries. This process involved careful consideration of the data types and constraints defined during the table creation phase to ensure accurate and meaningful dataset input.

![Figure 4 shows the INSERT commands.](link_to_figure_4_image)

## Querying Skills

### Complex Query Execution
For data retrieval, we leveraged the SELECT statement to extract information from various tables within the database. The use of JOIN clauses allowed for the merging of rows from two or more tables based on related columns, leading to flexible data access. To refine our dataset, we incorporated the WHERE clause with logical operators such as AND, OR, BETWEEN, and LIKE, alongside comparison operators to filter the results based on specified criteria.

![Figure 5 shows an example of how join, where clauses with logical operators were use.](link_to_figure_5_image)

### Sorting and Distinct Selection
The ORDER BY clause sorted our query results for enhanced readability and analysis, specifying either ascending or descending order as necessary. To eliminate redundancy, the DISTINCT keyword ensured that only unique result sets were returned.

![Figure 6: Example of sorting with ORDER BY and DISTINCT record retrieval.](link_to_figure_6_image)

## Use of SQL Functions for Data Manipulation

### Working with Date and Time
SQL Server provides a plethora of built-in functions to handle date and time data types, which are essential for organizing and analyzing temporal data within our healthcare database. Functions such as DATEPART and DATENAME are particularly useful for extracting specific parts from date and time columns and converting them into human-readable form. Below are examples of how these functions have been applied:

- DATEPART: This function extracts a specific part of a date or time, such as the year, month, or day. We used DATEPART to filter appointments within specific weekdays, enhancing our ability to retrieve data relevant to business hours and operational days.
- DATENAME: Translates the numeric representation of date parts into a textual name, like translating '1' to 'Sunday'. We utilized DATENAME to make the query results more intuitive for end-users by showing the name of the day on which appointments are booked.
- Conversion and Formatting: Data presentation is key in reporting and analytics. The CONVERT function, for instance, allows us to change data types or format data. In the context of our database, we used CONVERT to transform date and time values into more readable formats without the fractional seconds that SQL Server includes by default.

![Figure 7 shows an example of Datepart, datename and convert function usage.](link_to_figure_7_image)

## Testing Strategy
Our testing strategy was primarily manual, focusing on verifying the accuracy and reliability of each query. We conducted thorough tests for each use case to ensure:
- The correct execution of SQL statements.
- The integrity of data after manipulation.
- The expected outcomes for data retrieval operations.

## Conclusion
The database system designed has successfully met the specialized needs of Splendor Health Care, ensuring a smooth and effective digital transition. Our approach focused on usability, data integrity, and adherence to third normal form principles, resulting in a system that adeptly manages patient information and healthcare processes.

The strategic application of T-SQL and commitment to data security has established a reliable and scalable platform. This foundation not only serves current operations but is also ready to adapt to future enhancements, setting Splendor Health Care on a path toward continued excellence in patient care and service efficiency.
