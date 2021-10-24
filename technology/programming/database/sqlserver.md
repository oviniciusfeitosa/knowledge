# SQLServer

## Install SQLServer Linux

```
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install -y mssql-server
sudo /opt/mssql/bin/mssql-conf setup

# host: localhost
# port: 1433
# username: SA
# senha: Abcd123456
```

### Tools

```
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
sudo apt-get update 
sudo apt-get install mssql-tools unixodbc-dev
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.zshrc
source ~/.zshrc

# sqlcmd
```

## Backup database

```
touch /home/vinicius/demodatabase.bak
sudo chmod 777 /home/vinicius/demodatabase.bak
sqlcmd -S 127.0.0.1 -U SA -Q "BACKUP DATABASE demodatabase TO DISK = N'/home/vinicius/demodatabase.bak' WITH NOFORMAT, NOINIT, NAME = 'demodatabase', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
```

## Restore database

### DBeaver

```
USE master RESTORE DATABASE database_demo FROM 
DISK = N'/home/vinicius/Downloads/database_bkp.bak' WITH  FILE = 1, NOUNLOAD, REPLACE, STATS = 10
```

## Error when trying to drop database

SQL Error \[3702] \[S0004]: Cannot drop database "my\_database" because it is currently in use.

Solution:

```
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
