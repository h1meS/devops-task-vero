Sources: Ubuntu 20.04 Vm, Docker Engine and Docker Compose, MSSQL Server 2022 and PHP-apache 8.2 images

**Errors and solutions during the task:**
1. SQLSTATE[HYT00]: [Microsoft][ODBC Driver 18 for SQL Server]Login timeout expired.
- This error occurs because Its using **localhost** throught the connection. I added `network_mode: host` into **compose.yaml** file to solve it.  
2. SQLSTATE[08001]: [Microsoft][ODBC Driver 18 for SQL Server]SSL Provider: [error:0A000086:SSL routines::certificate verify failed:self-signed certificate]
- When SQL Server gets installed it is configured with a self-signed certificate and I believe It's for security about remote connection. I used easiest way to fix it with adding `TrustServerCertificate=true` in the connection string on **QuickDbTest.php** page.
3. SQLSTATE[42000]: [Microsoft][ODBC Driver 18 for SQL Server][SQL Server]Cannot open database "db_vero_digital" requested by the login. The login failed
- On the initial setup after the **docker compose up**, I execute `docker exec -it <container_id> /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P 'Un!q@to2023' -i db.sql` command on host machine to create the database with sqlcmd tool. 
