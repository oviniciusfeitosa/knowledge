# SQLServer

## Install SQLServer Linux

```
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install -y mssql-server
sudo /opt/mssql/bin/mssql-conf setup

# host: localhost
# port: 1433
# username: SA
# senha: Abcd123456
```

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

