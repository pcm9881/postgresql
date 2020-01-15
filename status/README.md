# Status 현황

## 상황
1. payments 라는 테이블이 있다라고 가정
1. payments 테이블에 컬럼 amount (bigint), created_at (timestamp) 있다라고 가정
1. 오늘과 어제 금액 합산을 구한다고 가정   

### 1차

``` sql
SELECT 
  SUM( CASE WHEN created_at < now()::date ),
  SUM( CASE WHEN created_at 
FROM
  payments
```

### 2차
