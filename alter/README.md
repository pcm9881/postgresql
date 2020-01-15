# ALTER

## 테이블 컬럼 타입 변경 int -> bigint

``` sql
ALTER TABLE public.{TABLE NAME} ALTER COLUMN {COLUMN NAME} TYPE bigint USING {COLUMN NAME}::bigint;
```
