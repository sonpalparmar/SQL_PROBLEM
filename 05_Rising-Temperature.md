### Rising-Temperature


**Problem Statement:**

You are given a table named `Weather` with the following structure

**Table: Weather**

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| recordDate  | date    |
| temperature | int     |

`id` is the column with unique values for this table. This table contains information about the temperature on a certain day.

Write a solution to find all dates' IDs with higher temperatures compared to their previous dates (yesterday). Return the result table in any order.

**Example 1:**

**Input:**

*Weather table:*

| id | recordDate | temperature |
|----|------------|-------------|
| 1  | 2015-01-01 | 10          |
| 2  | 2015-01-02 | 25          |
| 3  | 2015-01-03 | 20          |
| 4  | 2015-01-04 | 30          |

**Output:**

| id |
|----|
| 2  |
| 4  |

**Explanation:**

In 2015-01-02, the temperature was higher than the previous day (10 -> 25).

In 2015-01-04, the temperature was higher than the previous day (20 -> 30).

### Solution

```SQL
SELECT t1.id
FROM Weather t1, Weather t2
WHERE DATEDIFF(t1.recordDate, t2.recordDate) = 1 AND t1.temperature > t2.temperature;
