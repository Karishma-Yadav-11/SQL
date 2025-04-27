# SQL

## Introduction  
**LeetCode - SQL Interview in 50 Qs**

## Questions

1. Select Recyclable and Low Fat Products
Table: Products

# SQL Problem: Find Low Fat and Recyclable Products

## Table Structure: Products

| Column Name | Type | Description |
|------------|------|-------------|
| product_id | int | Primary key |
| low_fats | enum | 'Y' for low fat, 'N' for not |
| recyclable | enum | 'Y' for recyclable, 'N' for not |

## Example Data

### Input Table: Products

| product_id | low_fats | recyclable |
|------------|----------|------------|
| 0 | Y | N |
| 1 | Y | Y |
| 2 | N | Y |
| 3 | Y | Y |
| 4 | N | N |

### Expected Output

| product_id |
|------------|
| 1 |
| 3 |

## Explanation
Only products 1 and 3 are both low fat (`low_fats = 'Y'`) and recyclable (`recyclable = 'Y'`).


```sql
SELECT product_id
FROM products
WHERE low_fats ="Y" AND recyclable ="Y";
```

2. Find Customer Referee

Table: Customer
    
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| referee_id  | int     |
+-------------+---------+

    

    
In SQL, id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.

Write an SQL query to find the names of the customer that are not referred by the customer with id = 2.

Return the result table in any order.

Example 1:
Input:

    
Customer table:
+----+------+------------+
| id | name | referee_id |
+----+------+------------+
| 1  | Will | null       |
| 2  | Jane | null       |
| 3  | Alex | 2          |
| 4  | Bill | null       |
| 5  | Zack | 1          |
| 6  | Mark | 2          |
+----+------+------------+

    

    
Output:

    
+------+
| name |
+------+
| Will |
| Jane |
| Bill |
| Zack |
+------+

```sql
SELECT name
FROM Customer
WHERE referee_id <>2 OR referee_id is NULL;
```

3. Big Countries  
```sql
SELECT name, population, area
FROM World
WHERE area >= 3000000 OR population >=25000000;
```

4. Article Views I  
```sql
SELECT DISTINCT author_id AS id
FROM views
WHERE author_id = viewer_id
ORDER BY author_id;
```

5. Invalid Tweets  
```sql
SELECT tweet_id
FROM Tweets
WHERE LENGTH(content)>15;
```

6. Basic Joins – Replace Employee ID With The Unique Identifier  
```sql
SELECT eu.unique_id, e.name
FROM Employees e
LEFT JOIN EmployeeUNI eu
ON e.id=eu.id;
```

7. Product Sales Analysis I  
```sql
SELECT p.product_name,s.year,s.price
FROM Sales s
JOIN Product p
ON s.product_id=p.product_id;
```

8. Customer Who Visited but Did Not Make Any Transactions  
```sql
SELECT customer_id, count(*) AS count_no_trans
FROM Visits
WHERE visit_id NOT IN (SELECT visit_id FROM Transactions)
GROUP BY customer_id;
```

9. Rising Temperature  
```sql

```

10. Average Time of Process per Machine  
```sql

```

11. Employee Bonus  
```sql

```

12. Students and Examinations  
```sql

```

13. Managers with at Least 5 Direct Reports  
```sql

```

14. Confirmation Rate  
```sql

```

15. Basic Aggregate Functions – Not Boring Movies  
```sql

```

16. Average Selling Price  
```sql

```

17. Project Employees I  
```sql

```

18. Percentage of Users Attended a Contest  
```sql

```

19. Queries Quality and Percentage  
```sql

```

20. Monthly Transactions I  
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
