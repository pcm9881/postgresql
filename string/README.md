# string

## 개행문자

개행문자 삽입 chr(10)

``` sql
SELECT 'Hello' || chr(10) || 'World' as str FROM dual
```

```
Hello
Wolrd
```

## replace

```sql
SELECT replace('2020-08-10', '-', '');
```

```
20200810
```

## split_part

```sql
SELECT split_part('name|age|country', '|', 2)
```

```
age
```

## 