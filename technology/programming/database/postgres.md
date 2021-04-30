# Postgres

## Backup database

```text
 pg_dump -Ft -U cmdi -h 192.168.1.1 -p 5432 -f file.tar database
```

## Concat rows to column

```text
select column1, array_to_string(array_agg(distinct column2),',') from table group by 1
```

