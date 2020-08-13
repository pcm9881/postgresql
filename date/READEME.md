# date 날짜 관련

## now timestamp
now 함수를 사용하면 현재기준 timestamp를 얻을 수 있다. (서버환경에 따라 다른나라 시간일 수도 있음)

``` sql
SELECT now()
-- ex: 2020-02-04 14:51:05.221168+09
```

## timestamp to date 
timestamp를 날짜로 convert

``` sql
SELECT now()::date
-- ex: 2020-02-04
```

## date_trunc 함수 활용

### 해당 월 첫번째 날 가져오기 

``` sql
select date_trunc('month', now()::date)
```

### 해당 월 마지막 날 가져오기 

``` sql
select date_trunc('month', now()::date) + interval '1 month' - interval '1 day'
```

## 날짜 차이 