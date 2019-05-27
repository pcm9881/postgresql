# Comment 주석

## SELECT 테이블 컬럼별 주석
- 예시
```
SELECT 
  c.table_schema, c.table_name, c.column_name, pgd.description
FROM 
  pg_catalog.pg_statio_all_tables as st
inner join 
  pg_catalog.pg_description pgd on (pgd.objoid=st.relid)
inner join 
  information_schema.columns c on (             
    pgd.objsubid=c.ordinal_position
    and c.table_schema=st.schemaname 
    and c.table_name=st.relname
  );
-- WHERE c.table_name = '테이블이름'
```