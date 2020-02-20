# union

테이블끼리 병합하기 위한 기능.

## example

아래 예시를 넣어놨다.

### users

| id | name | age | 
|----|------|-----|
| 1  | pcm  | 30  |


### infos

| id | name | age | 
|----|------|-----|
| 2  | hgd  | 20  |

### SQL

``` sql
with users as (
  select 1 as id, 'pcm'::text as name, 30 as age
), infos as (
  select 2 as id, 'hgd'::text as name, 20 as age
)

select * from users
union
select * from infos
```

### result 

| id | name | age | 
|----|------|-----|
| 1  | pcm  | 30  |
| 2  | hgd  | 20  |