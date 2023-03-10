# MySQL

## docker mysql

docker Host is not allowed to connect to this mysql server

host 机器无法使用root用户
需要更改权限

- 进入容器更改权限
  
        docker exec -it mysql bash
        mysql -uroot -proot
        use mysql;
        update user set host = '%' where user ='root';
        flush privileges;
        quit;


