### Sample Table: Worker

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE | DEPARTMENT |
| -------- | -------- | -------- | -------- | -------- | -------- |
| 1     | Siddharth     | Singh     | 80,000     | 2019-03-20 09:00:00     | HR     |
| 2     | Lavesh     | Ahir     | 300,000     | 2019-07-11 09:00:00     | Admin     |
| 3     | Abhishek     | Midha     | 500,000     | 2019-03-20 09:00:00     | HR     |
| 4     | Rahul     | Mahar     | 200,000     | 2019-03-20 09:00:00     | Admin     |
| 5     | Saurabh     | Madavi     | 90,000     | 2019-07-11 09:00:00     | Admin     |
| 6     | Aman     | Nain     | 75,000     | 2019-07-11 09:00:00     | Account     |
| 7     | Vaibhav     | Varshney     | 100,000     | 2019-02-20 09:00:00     | Account     |
| 8     | Farhaan     | Majied     | 500,000     | 2019-05-11 09:00:00     | Admin     |

### Sample Table: Title

| WORKER_REF_ID | WORKER_TITLE | AFFECTED_FROM |
| -------- | -------- | -------- |
| 1     | Manager     | 2021-02-20 00:00:00     |
| 2     | Executive     | 2021-06-11 00:00:00     |
| 8     | Executive     | 2021-06-11 00:00:00     |
| 5     | Manager     | 2021-06-11 00:00:00     |
| 4     | Asst.Manager     | 2021-06-11 00:00:00     |
| 7     | Executive     | 2021-06-11 00:00:00     |
| 6     | Lead     | 2021-06-11 00:00:00     |
| 3     | Lead     | 2021-06-11 00:00:00     |

### Sample Table: Job Grades

| GRADE_LEVEL | LOWEST_SALARY | HIGHEST_SALARY |
| -------- | -------- | -------- |
| A     | 10,000     | 75999     |
| B     | 76,000     | 80999     |
| C     | 81,000     | 99999     |
| D     | 100,000     | 199999     |
| E     | 200,000     | 299999     |
| F     | 300,000     | 600000     |

#### 1 | Write a SQL query to create `WORKER` Table.

```sql 
CREATE TABLE Worker (
    WORKER_ID INT NOT NULL PRIMARY KEY,
    FIRST_NAME CHAR(25),
    LAST_NAME CHAR(25),
    SALARY INT(15),
    JOINING_DATE DATETIME,
    DEPARTMENT CHAR(25)
);
```

#### 2 | Write a SQL Query to insert above values in `WORKER` Table.

```sql 
INSERT INTO Worker (WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE,
DEPARTMENT) 
VALUES
(1, ‘Siddharth’, ‘Singh’, 80000, ‘2019-03-20 09:00:00’, ‘HR’)
(2, ‘Lavesh’, ‘Ahir’, 300000, ‘2019-07-11 09:00:00’, ‘Admin’)
(3, ‘Abhishek’, ‘Midha’, 500000, ‘2019-03-20 09:00:00’, ‘HR’)
(4, ‘Rahul’, ‘Mahar’,200000, ‘2019-03-20 09:00:00’, ‘Admin’)
(5, ‘Saurabh’, ‘Madavi’, 90000, ‘2019-07-11 09:00:00’, ‘Admin’)
(6, ‘Aman’, ‘Nain’, 75000, ‘2019-07-11 09:00:00’,’Account’)
(7, ‘Vaibhav’, ‘Varshney’, 100000, ‘2019-02-20 09:00:00’, ‘Account’)
(8, ‘Farhaan’, ‘Majied’, 500000, ‘2019-05-11 09:00:00’, ‘Admin’);
```

#### 3 | Write a SQL Query to create table `Title` which has `WORKER_REF_ID` as foreign key.

```sql 
CREATE TABLE Title (
    WORKER_REF_ID INT,
    WORKER_TITLE CHAR(25),
    AFFECTED_FROM DATETIME,
    FOREIGN KEY (WORKER_REF_ID)
    REFERENCES Worker(WORKER_ID)
    ON DELETE CASCADE
);
```

#### 4 | Write a SQL query to clone a new table `WorkCopy` from another table.

* The general query to clone a table with data is:

```sql 
SELECT * INTO WorkerCopy FROM Worker;
```
* The general way to clone a table without information is:

```sql 
SELECT * INTO WorkerCopy FROM Worker WHERE 1 = 0;
```
* An alternate way to clone a table (for MySQL) without is:

```sql
CREATE TABLE WorkerCopy LIKE Worker;
```

#### 5 | Write a SQL query to fetch “FIRST_NAME” from `Worker` table using the alias name as <WORKER_NAME>.

```sql 
Select FIRST_NAME AS WORKER_NAME from Worker;
```

#### 6 | Write a SQL query to fetch “FIRST_NAME” from Worker table in upper case.

```sql 
Select upper(FIRST_NAME) from Worker;
```

#### 7 | Write an SQL query to fetch unique values of `DEPARTMENT` from Worker table.

```sql 
Select distinct DEPARTMENT from Worker;
```

#### 8 | Write a SQL query to print the FIRST_NAME from Worker table after replacing "a" with "A".

```sql 
Select REPLACE(FIRST_NAME, "a", "A") from Worker;
```

#### 9 | Write a SQL query to print the FIRST_NAME and LAST_NAME from Worker table into a single column COMPLETE_NAME. A space char should separate them.

```sql 
Select CONCAT(FIRST_NAME, " ", LAST_NAME) AS
"COMPLETE_NAME" from Worker;
```

#### 10 | Write a SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending.

```sql 
Select * from Worker order by FIRST_NAME asc;
```

#### 11 | Write a SQL query to print all Worker details from the `Worker` table order by `FIRST_NAME` Ascending and DEPARTMENT Descending.

```sql 
Select * from Worker order by FIRST_NAME asc, DEPARTMENT desc;

```

#### 12 | Write a SQL query to print details for Workers with the first name as “Rahul” and “Lavesh” from Worker table.

```sql 
Select * from Worker where FIRST_NAME in ('Rahul','Lavesh');
```

#### 13 | Write a SQL query to print details of workers excluding first names, “Rahul” and “Lavesh” from Worker table.

```sql 
Select * from Worker where FIRST_NAME not in ('Rahul','Lavesh');
```

#### 14 | Write a SQL query to print details of the Workers whose FIRST_NAME starts with ‘S’.

```sql 
Select * from Worker where FIRST_NAME like 'S%';
```
