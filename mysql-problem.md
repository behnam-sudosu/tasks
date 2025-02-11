# mysql problem

## add user without use password root
sudo mysql -u root # I had to use "sudo" since it was a new installation

mysql> USE mysql;
mysql> UPDATE user SET plugin='mysql_native_password' WHERE User='root';
mysql> FLUSH PRIVILEGES;
mysql> exit;

sudo service mysql restart