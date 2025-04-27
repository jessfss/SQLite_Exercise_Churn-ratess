# SQLite_Exercise_Churn-ratess

Questions

1. Take a look at the first 100 rows of data in the subscriptions table. How many different segments do you see?

2. Determine the range of months of data provided. Which months will you be able to calculate churn for?

Calculate churn rate for each segment
3. You’ll be calculating the churn rate for both segments (87 and 30) over the first 3 months of 2017 (you can’t calculate it for December, since there are no subscription_end values yet). To get started, create a temporary table of months.

4. Create a temporary table, cross_join, from subscriptions and your months. Be sure to SELECT every column.

5. Create a temporary table, status, from the cross_join table you created. This table should contain:

id selected from cross_join
month as an alias of first_day
is_active_87 created using a CASE WHEN to find any users from segment 87 who existed prior to the beginning of the month. This is 1 if true and 0 otherwise.
is_active_30 created using a CASE WHEN to find any users from segment 30 who existed prior to the beginning of the month. This is 1 if true and 0 otherwise.

6. Add an is_canceled_87 and an is_canceled_30 column to the status temporary table. This should be 1 if the subscription is canceled during the month and 0 otherwise.

7. Create a status_aggregate temporary table that is a SUM of the active and canceled subscriptions for each segment, for each month.

The resulting columns should be:

sum_active_87
sum_active_30
sum_canceled_87
sum_canceled_30

8. Calculate the churn rates for the two segments over the three month period. Which segment has a lower churn rate?

Bonus

9. How would you modify this code to support a large number of segments?

## Output would look like:

| month      | segment | churn_rate          |
|------------|---------|---------------------|
| 2017-01-01 | 30      | 0.0756013745704467  |
| 2017-01-01 | 87      | 0.251798561151079   |
| 2017-02-01 | 30      | 0.0733590733590734  |
| 2017-02-01 | 87      | 0.32034632034632    |
| 2017-03-01 | 30      | 0.11731843575419    |
| 2017-03-01 | 87      | 0.485875706214689   |


