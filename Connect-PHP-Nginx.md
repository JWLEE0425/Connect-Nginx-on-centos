# Connect-PHP-Nginx

## 初期設定

> yum update

![56](https://user-images.githubusercontent.com/43987455/49986053-b2de2f80-ffb1-11e8-96a4-1c560b35c899.JPG)

> /etc/sysconfig/selinuxファイルを編集してselinuxを中止 <br>
SELINUX=enforcing を SELINUX=disabled に

![57](https://user-images.githubusercontent.com/43987455/49986054-b2de2f80-ffb1-11e8-93a6-adca96b86fc9.JPG)
![58](https://user-images.githubusercontent.com/43987455/49986055-b2de2f80-ffb1-11e8-815e-600ebbc7ed30.JPG)

> firewalld設定

![59](https://user-images.githubusercontent.com/43987455/49986056-b2de2f80-ffb1-11e8-9fed-5189f4282b43.JPG)
![60](https://user-images.githubusercontent.com/43987455/49986057-b376c600-ffb1-11e8-8237-cabe21c66bc9.JPG)

> iptablesアップデート

![1](https://user-images.githubusercontent.com/43987455/50079255-79fdbf00-022c-11e9-8649-da979416070a.png)


## Nginx設置

> vi /etc/yum.repos.d/nginx.repo を作って下のコマンドを追加
~~~
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/7/$basearch/
gpgcheck=0
enabled=1
~~~

![4](https://user-images.githubusercontent.com/43987455/50079583-52f3bd00-022d-11e9-800c-bd6788ea3903.JPG)

> nginxを設置して実行

![6](https://user-images.githubusercontent.com/43987455/50079658-846c8880-022d-11e9-95c6-411470e9c2d1.JPG)

## MariaDB設置

> vi /etc/yum.repos.d/MariaDB.repo を作って下のコマンドを追加
~~~
[mariadb]
name=MariaDB
baseurl=http://yum.mariadb.org/10.2/rhel7-amd64
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MairaDB
gpgcheck=1
~~~

![8](https://user-images.githubusercontent.com/43987455/50079715-ac5bec00-022d-11e9-93df-39746183be94.JPG)

> DBを設置して実行

![10](https://user-images.githubusercontent.com/43987455/50079625-6dc63180-022d-11e9-87c2-1d7f47ced0ed.JPG)

> vi /etc/my.cnf.d/mysql-clients.cnf ファイルを編集して下のコマンドを追加
~~~
default-character-set=uft8
~~~

![12](https://user-images.githubusercontent.com/43987455/50079823-fe047680-022d-11e9-93e1-72c236e8d633.JPG)

> vi /etc/my.cnf.d/server.cnf　ファイルを編集して下のコマンドを追加
~~~
max_connections=512
wait_timeout=30
character-set-server=utf8
~~~

![14](https://user-images.githubusercontent.com/43987455/50079925-3e63f480-022e-11e9-85cd-fd56de660549.JPG)

> DBを再実行

![16](https://user-images.githubusercontent.com/43987455/50079966-5b002c80-022e-11e9-90aa-5902b560fa0f.JPG)

> rootパスワード設定

~~~
$ systemctl stop mariadb

$ mysql -uroot mysql
Mariadb[mysql]> update user set password=password('変更するパスワード') where user='root';
Mariadb[mysql]> flush privileges;
Mariadb[mysql]> exit;

$ sudo mysql -uroot -p
パスワード入力 ...
 
MariaDB[(none)]>
~~~

## PHP設置

> PHP-FPMを設置
~~~
rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
~~~
上のコマンドができないなら、yum updateをしてください。'yum update' や 'yum install -y epel-release'

> php70w-fpm php70w-opcache設置
~~~
yum install php70w-fpm php70w-opcache
~~~



