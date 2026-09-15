# EXERCISE3-CASE-STATEMENT
EXERCISE 3




CREATE CATALOG IF NOT EXISTS brightlearn;

CREATE SCHEMA IF NOT EXISTS brightlearn.case1;

CREATE OR REPLACE TABLE brightlearn.case1.product_table(
    product_id INT,
    product_name STRING,
    price INT
);

INSERT INTO brightlearn.case1.product_table VALUES
(1,'Laptop','1200'),
(2,'Phone','800'),
(3,'Keyboard','45'),
(4,'Monitor','300'),
(5,'Mouse','25');

SELECT * FROM brightlearn.case1.product_table;

--QUESTION 1
SELECT product_name,
        price,
CASE 
WHEN price > 1000 THEN 'Expensive'
WHEN price BETWEEN 100 AND 1000 THEN 'Mid-range'
WHEN price < 100 THEN 'Budget'
END AS price_category
FROM brightlearn.case1.product_table;       

CREATE TABLE IF NOT EXISTS brightlearn.case1.orders_table;
   
CREATE OR REPLACE TABLE brightlearn.case1.orders_table(
    order_id INT,
    customer_name STRING,
    amount DECIMAL(10,2)
);

INSERT INTO brightlearn.case1.orders_table VALUES
(1,'Alice','150'),
(2,'Bob','560'),
(3,'Charlie','999.99'),
(4,'Diana','45.50'),
(5,'Ethan','1200');

SELECT * FROM  brightlearn.case1.orders_table;

--QUESTION 2
SELECT customer_name,   
        amount,
CASE 
WHEN amount >= 1000 THEN 'High_value'
WHEN amount BETWEEN 500 AND 999.99 THEN 'Medium_value'
WHEN amount < 500 THEN 'Low_value'
END AS order_value_category
FROM  brightlearn.case1.orders_table;


CREATE OR REPLACE TABLE brightlearn.case1.employees_table(
    employee_id INT,
    employee_name STRING,
    department STRING,
    salary INT
);

INSERT INTO brightlearn.case1.employees_table VALUES
(1,'John','IT','85000'),
(2,'Sara','HR','60000'),
(3,'Mark','IT','75000'),
(4,'Lucy','Finance','95000'),
(5,'Tom','HR','55000');

SELECT *
FROM brightlearn.case1.employees_table;

--QUESTION 3
SELECT employee_name,
        department,
        salary,
CASE 
WHEN department = 'IT' AND salary > 80000 THEN 'Senior IT'
WHEN department = 'HR' AND salary > 55000 THEN 'Experienced HR'
ELSE 'Staff'
END AS position_level
FROM brightlearn.case1.employees_table;

CREATE OR REPLACE TABLE brightlearn.case1.student_table(
    student_id INT,
    student_name STRING,
    score INT
);

INSERT INTO brightlearn.case1.student_table VALUES
(1,'Anna','92'),
(2,'Ben','76'),
(3,'Cara','59'),
(4,'David','83'),
(5,'Ella','68');

SELECT *
FROM brightlearn.case1.student_table;

--QUESTION 4
SELECT student_name,
        score,
CASE 
WHEN score >= 90 THEN 'A'
WHEN score BETWEEN 80 AND 89 THEN 'B'
WHEN score BETWEEN 70 AND 79 THEN 'C'
WHEN score BETWEEN 60 AND 69 THEN 'D'
ELSE 'F'
END AS grade
FROM brightlearn.case1.student_table;


CREATE OR REPLACE TABLE brightlearn.case1.delivery_table(
    delivery_id INT,
    delivery_time_minutes INT
);

INSERT INTO brightlearn.case1.delivery_table VALUES(
    1,'45'),
    (2,'80'),
    (3,'30'),
    (4,'65'),
    (5,'100');

 SELECT *
 FROM brightlearn.case1.delivery_table;

--QUESTION 5
SELECT delivery_id,
       delivery_time_minutes,
 CASE 
 WHEN delivery_time_minutes <= 30 THEN 'Fast'
 WHEN delivery_time_minutes BETWEEN 31 AND 60 THEN 'On_time'
 ELSE 'Late'
 END AS performance
 FROM  brightlearn.case1.delivery_table;
 
 CREATE OR REPLACE TABLE brightlearn.case1.ticket_table(
    ticket_id INT,
    issue_type STRING,
    priority INT
 );
 
 INSERT INTO brightlearn.case1.ticket_table VALUES(
    1,'Login_issue','1'),
    (2,'Server_down','3'),
    (3,'Slow_system','2'),
    (4,'Email_error','2'),
    (5,'Password_reset','1');

    SELECT *
     FROM  brightlearn.case1.ticket_table;

     --QUESTION 6
     SELECT issue_type,
            priority,   
    CASE
    WHEN priority = 3 THEN 'High'
    WHEN priority = 2 THEN 'Medium'
    WHEN priority = 1 THEN 'Low'
    END AS priority_label
    FROM brightlearn.case1.ticket_table;

             
            
--QUESTION 8
CREATE OR REPLACE TABLE  brightlearn.case1.inventory_table(
    product_id INT,
    stock_qty INT);

INSERT INTO brightlearn.case1.inventory_table VALUES
(1,'5'),
(2,'0'),
(3,'25'),
(4,'10'),
(5,'3');

SELECT * 
FROM brightlearn.case1.inventory_table;

SELECT product_id,
       stock_qty,
CASE
WHEN stock_qty = 0 THEN 'out_of_stock'
WHEN stock_qty BETWEEN 1 AND 5 THEN 'low_stock'
ELSE 'in_stock'
END AS stock_status
FROM brightlearn.case1.inventory_table;


--QUESTION 9
CREATE OR REPLACE TABLE  brightlearn.case1.classes_table(
    class_id INT,
    subject STRING,
    enrolled_students INT);

    INSERT INTO TABLE brightlearn.case1.classes_table VALUES
        (1,'math','30'),
        (2,'english','25'),
        (3,'science','15'),
        (4,'art','5'),
        (5,'history','20');

SELECT *
FROM brightlearn.case1.classes_table;

--QUESTION 9
SELECT subject,
        enrolled_students,
CASE
 WHEN enrolled_students >= 25 THEN 'Large'
 WHEN enrolled_students BETWEEN 10 AND 24 THEN 'Medium'
 ELSE 'Small'
 END AS class_size_category
 FROM brightlearn.case1.classes_table;

 CREATE OR REPLACE TABLE  brightlearn.case1.payment_method(
    payment_id INT,
    amount INT,
    payment_method STRING);

INSERT INTO  brightlearn.case1.payment_method VALUES
(1,'50','card'),
(2,'200','cash'),
(3,'150','card'),
(4,'75','pay_pal'),
(5,'300','cash');
 
 SELECT *
 FROM  brightlearn.case1.payment_method;

--QUESTION 10
 SELECT payment_id,
        payment_method,
        amount,
CASE 
WHEN payment_method = 'cash' AND amount >= 200 THEN 'eligible_for_discount'
ELSE 'not_eligible'
END AS discount_eligibility
FROM  brightlearn.case1.payment_method;
