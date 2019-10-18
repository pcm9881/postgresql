# deadlock 조회 

## 현재 테이블 lock 확인 

``` sql
SELECT 
  t.relname, l.locktype,
  page, virtualtransaction,
  pid, mode,granted
FROM 
  pg_locks l,
  pg_stat_all_tables t
WHERE 
  l.relation = t.relid
ORDER BY 
  relation ASC;
```

## 해당 작업 kill 

``` sql
SELECT pg_cancel_backend(pid); -- 해당 pid 중지  

SELECT pg_terminate_backend(pid) FROM pg_stat_activity ; -- 연계된 pid 전체 중지 
```

## 상세파악 

``` sql
SELECT blocked_locks.pid         AS blocked_pid,
       blocked_activity.usename  AS blocked_user,
       blocking_locks.pid        AS blocking_pid,
       blocking_activity.usename AS blocking_user,
       blocked_activity.query    AS blocked_statement,
       blocking_activity.query   AS current_statement_in_blocking_process,
       blocked_activity.query_start
FROM   pg_catalog.pg_locks blocked_locks
JOIN   pg_catalog.pg_stat_activity blocked_activity
ON     blocked_activity.pid = blocked_locks.pid
JOIN   pg_catalog.pg_locks blocking_locks
ON     blocking_locks.locktype = blocked_locks.locktype
AND    blocking_locks.database IS NOT distinct
FROM   blocked_locks.DATABASE
AND    blocking_locks.relation IS NOT DISTINCT
FROM   blocked_locks.relation
AND    blocking_locks.page IS NOT DISTINCT
FROM   blocked_locks.page
AND    blocking_locks.tuple IS NOT DISTINCT
FROM   blocked_locks.tuple
AND    blocking_locks.virtualxid IS NOT DISTINCT
FROM   blocked_locks.virtualxid
AND    blocking_locks.transactionid IS NOT DISTINCT
FROM   blocked_locks.transactionid
AND    blocking_locks.classid IS NOT DISTINCT
FROM   blocked_locks.classid
AND    blocking_locks.objid IS NOT DISTINCT
FROM   blocked_locks.objid
AND    blocking_locks.objsubid IS NOT DISTINCT
FROM   blocked_locks.objsubid
AND    blocking_locks.pid != blocked_locks.pid
JOIN   pg_catalog.pg_stat_activity blocking_activity
ON     blocking_activity.pid = blocking_locks.pid
WHERE  NOT blocked_locks.granted; 
```
