# mysql
    sudo apt update
    sudp apt install mariadb-server

# more info
    data save ===>> /var/lib/mysql ===>> you have mount this directory to another dis
    config file ===>> /etc/mysql/mariadb.cnf

## secure you're mariadb
    mysql_secure_installation
        root password ===>> enter if you don't have password
        switch to unix_socket ===>> yes
        change the root password ===>> yes
        new password ===>> 12345678
        re-enter new password ===>>12345678 
        remove anonymous users ===>> yes
        disallow root login remotely ===>> yes
        remove test database ===>> yes
        reload privilege tables now ===>> yes
    
## comman check your mysql
    systemctl status mariadb.service
    systemctl start mariadb.service
    systemctl enable mariadb.service

## command enter mariadb
    mysql -u root -p
    enter password

##  if you want login with user    
        sudo mysql -u root ===>> I had to use "sudo" since it was a new installation

        mysql> USE mysql;
        mysql> UPDATE user SET plugin='mysql_native_password' WHERE User='root';
        mysql> FLUSH PRIVILEGES;
        mysql> exit;

        sudo service mysql restart
    
## comand inside mariadb
    show databases; ===>> show all databases
    create dabase (behnam); ===>> make database
    use behnam;
    create table students(id int, name varchar(255));
    show dables;
    INSERT into students(id, name) valuse (1, behnam), (2, emami);
    SELECT * FROM students;
    show columns from city;
    exit

## import
### first
    mysql -u root -p
        source /home/behnam/world_x.sql
### second    
    mysql -u root -p mydatabase < /home/behnam/world_x.sql

## export
    mysqldump -u root -p --all database /tmp/mybackup.sql
    mysqldump -u root -p mydatabase > /tmp/mybackup-database.sql
    mysqldump -u root -p mydatabase | gzip > /tmp/mybackup-database.sql.gz ===>> make zip file
### crontab
    sudo crontab -e
        00 23 * * * mysqldump -u root -p mydatabase | gzip > /tmp/mydatabase.sql.gz ===> make zip file
        00 23 * * * mysqldump -u root -p mydatabase > /tmp/mydatabase.sql


