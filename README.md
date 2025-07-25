# SQL

## Introduction  
**LeetCode - SQL Interview in 50 Qs**

## Questions

1. Select Recyclable and Low Fat Products

## Solution

```sql
SELECT product_id
FROM products
WHERE low_fats ="Y" AND recyclable ="Y";
```

2. Find Customer Referee

## Solution

```sql
SELECT name
FROM Customer
WHERE referee_id <>2 OR referee_id is NULL;
```

OR

```sql
SELECT name
FROM Customer
WHERE IFNULL(referee_id,0) !=2;
```

3. Big Countries

## Solution

```sql
SELECT name, population, area
FROM World
WHERE area >= 3000000 OR population >=25000000;
```

4. Article Views I

## Solution
  
```sql
SELECT DISTINCT author_id AS id
FROM views
WHERE author_id = viewer_id
ORDER BY author_id;
```

5. Invalid Tweets 

## Solution

```sql
SELECT tweet_id
FROM Tweets
WHERE LENGTH(content)>15;
```

6. Basic Joins – Replace Employee ID With The Unique Identifier  

## Solution

```sql
SELECT eu.unique_id, e.name
FROM Employees e
LEFT JOIN EmployeeUNI eu
ON e.id=eu.id;
```

7. Product Sales Analysis I

## Solution

```sql
SELECT p.product_name,s.year,s.price
FROM Sales s
JOIN Product p
ON s.product_id=p.product_id;
```

8. Customer Who Visited but Did Not Make Any Transactions

## Solution
 
```sql
SELECT customer_id, count(*) AS count_no_trans
FROM Visits
WHERE visit_id NOT IN (SELECT visit_id FROM Transactions)
GROUP BY customer_id;
```

9. Rising Temperature 

## Solution
 
```sql
SELECT w1.id
FROM Weather w1
INNER JOIN Weather w2
ON DATEDIFF(w1.recordDate ,w2.recordDate) =1 
AND w1.temperature > w2.temperature;
```

10. Average Time of Process per Machine  

## Solution

```sql
SELECT a1.machine_id, ROUND(AVG(a2.timestamp - a1.timestamp),3) AS processing_time
FROM Activity a1
JOIN Activity a2
ON a1.machine_id = a2.machine_id
AND a1.process_id = a2.process_id
AND a1.activity_type = 'start'
AND a2.activity_type = 'end'
GROUP BY a1.machine_id;
```

11. Employee Bonus  

## Solution

```sql
SELECT e.name, b.bonus
FROM Employee e
LEFT JOIN Bonus b
ON e.empID = b.empID
WHERE b.bonus IS NULL OR b.bonus < 1000;
```

12. Students and Examinations  

## Solution

```sql
SELECT s.student_id, s.student_name, sub.subject_name, COUNT(e.subject_name) AS attended_exams 
FROM Students s
CROSS JOIN Subjects sub
LEFT JOIN Examinations e
ON s.student_id  = e.student_id
AND sub.subject_name = e.subject_name
GROUP BY s.student_id, sub.subject_name
ORDER BY s.student_id, sub.subject_name;
```

13. Managers with at Least 5 Direct Reports 

## Solution
 
```sql
SELECT e1.name
FROM Employee e1
INNER JOIN Employee e2
ON e1.id = e2.managerId
GROUP BY e2.managerId
HAVING COUNT(e2.managerId) >=5;
```

14. Confirmation Rate  

## Solution

```sql
SELECT s.user_id, IFNULL(ROUND(COUNT(CASE WHEN action='confirmed' THEN 1 END)/COUNT(*),2),0.00) AS confirmation_rate
FROM Signups s
LEFT JOIN Confirmations c
ON s.user_id = c.user_id
GROUP BY s.user_id;
```

OR

```sql
SELECT s.user_id, IFNULL(ROUND(SUM(action= 'confirmed')/COUNT(*),2),0.00) AS confirmation_rate
FROM Signups s
LEFT JOIN Confirmations c
ON s.user_id = c.user_id
GROUP BY s.user_id;
```

15. Basic Aggregate Functions – Not Boring Movies  

## Solution

```sql
SELECT id, movie, description, rating
FROM Cinema
WHERE id%2 !=0 AND description<> 'boring'
ORDER BY rating DESC;
```

16. Average Selling Price  

## Solution

```sql
SELECT p.product_id, IFNULL(ROUND(SUM(p.price * u.units)/SUM(u.units),2),0) AS average_price
FROM Prices p
LEFT JOIN UnitsSold u
ON p.product_id = u.product_id AND u.purchase_date BETWEEN p.start_date AND p.end_date
GROUP BY p.product_id;
```

17. Project Employees I  

## Solution

```sql
SELECT p.project_id, ROUND(AVG(experience_years),2) AS average_years
FROM Project p
LEFT JOIN Employee e
ON p.employee_id = e.employee_id
GROUP BY p.project_id;
```

18. Percentage of Users Attended a Contest  

## Solution

```sql
SELECT contest_id, ROUND(COUNT(DISTINCT user_id)*100/(SELECT COUNT(user_id) FROM Users),2) AS percentage
FROM Register
GROUP BY contest_id
ORDER BY percentage DESC, contest_id;
```

19. Queries Quality and Percentage  

## Solution

```sql
SELECT query_name, ROUND(AVG(rating/position) ,2) AS quality, ROUND((AVG(IF(rating <3,1,0)) *100),2) AS poor_query_percentage
FROM Queries
GROUP BY query_name;
```

20. Monthly Transactions I  

## Solution

```sql
SELECT 
    DATE_FORMAT(trans_date, '%Y-%m') AS month
    ,country
    ,COUNT(id) AS trans_count
    ,SUM(state='approved') AS approved_count
    ,SUM(amount) AS trans_total_amount
    ,SUM(IF(state='approved', amount, 0)) AS approved_total_amount
FROM Transactions
GROUP BY month, country;
```

21. Immediate Food Delivery II   

## Solution

```sql
SELECT ROUND(SUM(IF(order_date = customer_pref_delivery_date,1,0))*100/COUNT(customer_id),2) AS immediate_percentage
FROM Delivery
WHERE (customer_id,order_date) IN (
    SELECT customer_id, MIN(order_date)
    FROM Delivery
    GROUP BY customer_id);
```

22. Game Play Analysis IV  

## Solution

```sql
SELECT ROUND(COUNT(DISTINCT player_id)/ (SELECT COUNT( DISTINCT player_id) FROM Activity),2) AS fraction
FROM Activity
WHERE (player_id, DATE_SUB(event_date, INTERVAL 1 DAY)) IN (
    SELECT player_id, MIN(event_date) AS first_date
    FROM Activity
    GROUP BY player_id);
```

23. Sorting and Grouping – Number of Unique Subjects Taught by Each Teacher 

## Solution
 
```sql
SELECT teacher_id, COUNT(DISTINCT subject_id) AS cnt
FROM Teacher
GROUP BY teacher_id;
```

24. User Activity for the Past 30 Days I  

## Solution

```sql
SELECT activity_date AS day, COUNT(DISTINCT user_id) AS active_users
FROM Activity
WHERE activity_date BETWEEN '2019-06-28' AND '2019-07-27'
GROUP BY day;

```

25. Product Sales Analysis III  

## Solution

```sql
SELECT product_id, year AS first_year, quantity, price
FROM Sales
WHERE (product_id, year) IN(
    SELECT product_id, MIN(year) AS fy
    FROM Sales
    GROUP BY product_id);
```

26. Classes More Than 5 Students  

## Solution

```sql
SELECT class
FROM Courses
GROUP BY class
HAVING count(student)>=5;
```

27. Find Followers Count  

## Solution

```sql
SELECT user_id, count(follower_id) AS followers_count
FROM Followers
GROUP BY user_id
ORDER BY user_id;
```

28. Biggest Single Number  

## Solution

```sql
SELECT MAX(num) AS num
FROM MyNumbers
WHERE num IN(
    SELECT num
    FROM MyNumbers 
    GROUP BY num
    HAVING COUNT(*) = 1);
```

29. Customers Who Bought All Products  

## Solution

```sql
SELECT customer_id
FROM Customer
GROUP BY customer_id
HAVING COUNT(DISTINCT product_key) = (SELECT COUNT(DISTINCT product_key) FROM Product);
```

30. Advanced Select and Joins – The Number of Employees Which Report to Each Employee  

## Solution

```sql
SELECT e1.employee_id, e1.name, COUNT(e2.employee_id) AS reports_count, ROUND(AVG(e2.age)) AS average_age
FROM Employees e1
INNER JOIN Employees e2
ON e1.employee_id = e2.reports_to
GROUP BY e1.employee_id
ORDER BY e1.employee_id;
```

## 31. Primary Department for Each Employee  

# Solution

```sql
SELECT DISTINCT employee_id, department_id
FROM Employee
WHERE employee_id IN(
    SELECT employee_id
    FROM Employee
    GROUP BY employee_id
    HAVING COUNT(*) = 1
) OR primary_flag ='Y'
ORDER BY employee_id;
```

32. Triangle Judgement  

## Solution

```sql

```

33. Consecutive Numbers  

## Solution

```sql

```

34. Product Price at a Given Date  

## Solution

```sql

```

35. Last Person to Fit in the Bus  

## Solution

```sql

```

36. Count Salary Categories 

## Solution
 
```sql

```

37. Subqueries – Employees Whose Manager Left the Company  

## Solution

```sql

```

38. Exchange Seats

## Solution
  
```sql

```

39. Movie Rating  

## Solution

```sql

```

40. Restaurant Growth  

## Solution

```sql

```

41. Friend Requests II: Who Has the Most Friends  

## Solution

```sql

```

42. Investments in 2016  

## Solution

```sql

```

43. Department Top Three Salaries  

## Solution

```sql

```

44. Advanced String Functions / Regex / Clause – Fix Names in a Table  

## Solution

```sql

```

45. Patients With a Condition  

## Solution

```sql

```

46. Delete Duplicate Emails 

## Solution
 
```sql

```

47. Second Highest Salary  

## Solution

```sql

```

48. Group Sold Products By The Date 

## Solution
 
```sql

```

49. List the Products Ordered in a Period  

## Solution

```sql

```

50. Find Users With Valid E-Mails  

## Solution

```sql

```

## Thank you
