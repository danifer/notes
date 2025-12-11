MySQL database administration including users, passwords, replication, mysqldump, gzip backup, SSH tunnel, and database size queries.

Replication - used the following articles:
    https://www.linode.com/docs/databases/mysql/configure-master-master-mysql-database-replication/
    https://www.digitalocean.com/community/tutorials/how-to-set-up-mysql-master-master-replication

Add a user:
    GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' IDENTIFIED BY 'password';

Change root password:
    Try this first (especially for new installations)
        As root: mysqladmin -u root password newpassword
    https://support.rackspace.com/how-to/mysql-resetting-a-lost-mysql-root-password/
    https://www.digitalocean.com/community/tutorials/how-to-reset-your-mysql-or-mariadb-root-password-on-ubuntu-18-04
        UPDATE mysql.user SET password = PASSWORD('new_password') WHERE user = 'root';
        UPDATE mysql.user SET authentication_string = '' WHERE user = 'root';
        UPDATE mysql.user SET plugin = '' WHERE user = 'root';
        FLUSH PRIVILEGES;


Get the sizes of the installed databases.
    SELECT table_schema AS "Database", ROUND(SUM(data_length + index_length) / 1024 / 1024, 2) AS "Size (MB)" FROM information_schema.TABLES GROUP BY table_schema;

Compressing mysqldump output with gzip
    Compressing:
        mysqldump <mysqldump options> | gzip > outputfile.sql.gz
    Restoring:
        gunzip < outputfile.sql.gz | mysql <mysql options>
    Alternative one-liner:
        mysqldump mydatabase -u root -p | gzip -c | cat > mydatabase-$(date +%Y-%m-%d-%H.%M.%S).sql.gz

Show mysql database info
    Show tables
        SHOW TABLES;
    Show columns on a table
        SHOW COLUMNS from TABLE;

Tunnel local MySql server through SSH. This lets you connect your local dev environment to a production MySql server over SSH. Useful for real-time debugging of edge cases where you don't want to or can't dump the database from the production server.
    ssh -L [PORT]:[LOCAL ADDRESS]:[PORT] USER@REMOTE-SERVER-ADDRESS
        ssh -p 1246 -L 3306:127.0.0.1:3306 keeton@dfw1.danifer.com
