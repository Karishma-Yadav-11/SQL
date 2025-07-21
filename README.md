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

```

15. Basic Aggregate Functions – Not Boring Movies  

## Solution

```sql

```

16. Average Selling Price  

## Solution

```sql

```

17. Project Employees I  

## Solution

```sql

```

18. Percentage of Users Attended a Contest  

## Solution

```sql

```

19. Queries Quality and Percentage  

## Solution

```sql

```

20. Monthly Transactions I  

## Solution

```sql

```

21. Immediate Food Delivery II  
```sql

```

22. Game Play Analysis IV  
```sql

```

23. Sorting and Grouping – Number of Unique Subjects Taught by Each Teacher  
```sql

```

24. User Activity for the Past 30 Days I  
```sql

```

25. Product Sales Analysis III  
```sql

```

26. Classes More Than 5 Students  
```sql

```

27. Find Followers Count  
```sql

```

28. Biggest Single Number  
```sql

```

29. Customers Who Bought All Products  
```sql

```

30. Advanced Select and Joins – The Number of Employees Which Report to Each Employee  
```sql

```

31. Primary Department for Each Employee  
```sql

```

32. Triangle Judgement  
```sql

```

33. Consecutive Numbers  
```sql

```

34. Product Price at a Given Date  
```sql

```

35. Last Person to Fit in the Bus  
```sql

```

36. Count Salary Categories  
```sql

```

37. Subqueries – Employees Whose Manager Left the Company  
```sql

```

38. Exchange Seats  
```sql

```

39. Movie Rating  
```sql

```

40. Restaurant Growth  
```sql

```

41. Friend Requests II: Who Has the Most Friends  
```sql

```

42. Investments in 2016  
```sql

```

43. Department Top Three Salaries  
```sql

```

44. Advanced String Functions / Regex / Clause – Fix Names in a Table  
```sql

```

45. Patients With a Condition  
```sql

```

46. Delete Duplicate Emails  
```sql

```

47. Second Highest Salary  
```sql

```

48. Group Sold Products By The Date  
```sql

```

49. List the Products Ordered in a Period  
```sql

```

50. Find Users With Valid E-Mails  
```sql

```

## Thank you
