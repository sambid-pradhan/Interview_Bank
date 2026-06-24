# Histogram of Tweets

**Source:** [DataLemur](https://datalemur.com/questions/sql-histogram-tweets) · Easy · Twitter SQL Interview Question

## Problem

Assume you're given a table of Twitter tweet data. Write a query to obtain a **histogram of tweets posted per user in 2022**.

Output:
- `tweet_bucket` — tweet count per user
- `users_num` — number of users in that bucket

In other words: group users by how many tweets they posted in 2022, then count users in each group.

## Table: `tweets`

| Column Name | Type      |
|-------------|-----------|
| tweet_id    | integer   |
| user_id     | integer   |
| msg         | string    |
| tweet_date  | timestamp |

## Example Input

| tweet_id | user_id | msg                                                               | tweet_date          |
|----------|---------|-------------------------------------------------------------------|---------------------|
| 214252   | 111     | Am considering taking Tesla private at $420. Funding secured.     | 12/30/2021 00:00:00 |
| 739252   | 111     | Despite the constant negative press covfefe                       | 01/01/2022 00:00:00 |
| 846402   | 111     | Following @NickSinghTech on Twitter changed my life!              | 02/14/2022 00:00:00 |
| 241425   | 254     | If the salary is so competitive why won't you tell me what it is? | 03/01/2022 00:00:00 |
| 231574   | 148     | I no longer have a manager. I can't be managed                    | 03/23/2022 00:00:00 |

## Example Output

| tweet_bucket | users_num |
|--------------|-----------|
| 1            | 2         |
| 2            | 1         |

## Explanation

- User 111 posted **2** tweets in 2022
- Users 148 and 254 each posted **1** tweet in 2022
- So bucket `1` has 2 users, bucket `2` has 1 user

## Solution

```sql
WITH total_tweets AS (
    SELECT
        user_id,
        COUNT(tweet_id) AS tweet_count_per_user
    FROM tweets
    WHERE tweet_date BETWEEN '2022-01-01' AND '2022-12-31'
    GROUP BY user_id
)

SELECT
    tweet_count_per_user AS tweet_bucket,
    COUNT(*) AS users_num
FROM total_tweets
GROUP BY tweet_count_per_user
ORDER BY tweet_bucket;
```
