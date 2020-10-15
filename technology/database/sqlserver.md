# SQLServer

## Error when trying to drop database

SQL Error \[3702\] \[S0004\]: Cannot drop database "my\_database" because it is currently in use.

Solution:

```text
use master;

DECLARE @DatabaseName nvarchar(50)
SET @DatabaseName = N'my_database'

DECLARE @SQL varchar(max)

SELECT @SQL = COALESCE(@SQL,'') + 'Kill ' + Convert(varchar, SPId) + ';'
FROM MASTER..SysProcesses
WHERE DBId = DB_ID(@DatabaseName) AND SPId <> @@SPId

--SELECT @SQL 
EXEC(@SQL)


drop database my_database;
```

