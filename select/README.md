# SELECT
select 사용시 자주 사용하는 내용

## COALESCE
null -> 0

``` sql
-- case1
SELECT 
  COALESCE({COLUMN_NAME}, 0 ) 
FROM 
  {TABLE_NAME}
-- case2
SELECT 
  COALESCE( sum({COLUMN_NAME}) , 0) 
FROM 
  {TABLE_NAME}
```

## FILTER
Used Aggregate Functions (SUM, MAX, MIN, COUNT)

``` sql
-- case1
SELECT 
  SUM({COLUMN_NAME}) FILTER (WHERE {COLUMN_NAME} = true)
FROM
  {TABLE_NAME}
-- case2
SELECT
  SUM({COLUMN_NAME}) FILTER (WHERE {COLUMN_NAME} = 'payment'),
  SUM({COLUMN_NAME}) FILTER (WHERE {COLUMN_NAME} = 'repayment')
FROM
  {TABLE_NAME}
```
