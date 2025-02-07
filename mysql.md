# mysql
    sudo apt update
    sudp apt install mariadb-server

    ```
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
    ```

    systemctl status mariadb.service
    systemctl start mariadb.service
    systemctl enable mariadb.service

    mysql -u root -p
    enter password

    ```
    if you want login with user 
        sudo mysql -u root ===>> I had to use "sudo" since it was a new installation

        mysql> USE mysql;
        mysql> UPDATE user SET plugin='mysql_native_password' WHERE User='root';
        mysql> FLUSH PRIVILEGES;
        mysql> exit;

        sudo service mysql restart
    ```

