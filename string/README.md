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
