# View Table

## Create 

`t1` 라는 `members` 테이블과 `t2` 라는 `amounts` 테이블을 `JOIN` 해서 
`VIEW`를 만든다라고 가정했을 때 예제.

```sql
CREATE VIEW view_table_name
AS SELECT
  t1.name
  t2.deposit
FROM (
  SELECT
    id,
    name
  FROM members
) t1 
LEFT JOIN amounts t2 ON t2.member_id = t1.id
```
