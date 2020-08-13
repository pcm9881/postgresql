# createdb

## Creat Database & User

```sql
postgres=# create database <db_name>;
postgres=# create user <user_name> with encrypted password '<user_password>';
postgres=# grant all privileges on database <db_name> to <user_name>;
```