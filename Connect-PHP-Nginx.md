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

> 追加設置
~~~
yum install php70w-mysql php70w-gd php70w-curl php70w-mbstring php70w-mcrypt php70w-gettext php70w-pear
~~~

> 設置確認
~~~
php -v
~~~

![18](https://user-images.githubusercontent.com/43987455/50080132-c0ecb400-022e-11e9-992b-7d00cbefc7c0.JPG)

> 設定ファイル変更 - vi /etc/php.ini ファイルを下のコマンドに編集

![19](https://user-images.githubusercontent.com/43987455/50080241-00b39b80-022f-11e9-8d88-cfd5a4825b51.JPG)

~~~
cgi.fix_pathinfo = 0
allow_url_fopen = Off
expose_php = Off
display_errors = Off
upload_max_filesize = 10M
~~~

* 探す方法 <br>
' / ' を入力して、探す単語を入力します。
例：cgi.fix pathinfo = 0 を探す場合、/cgi.fix を入力します。<br>
'ｎ' ボタンは次です。

![21](https://user-images.githubusercontent.com/43987455/50080259-0a3d0380-022f-11e9-82d7-a6936bd93511.JPG)
![22](https://user-images.githubusercontent.com/43987455/50080260-0a3d0380-022f-11e9-8323-77edd2c4604c.JPG)
![23](https://user-images.githubusercontent.com/43987455/50080261-0a3d0380-022f-11e9-9514-8c4fe00f2428.JPG)

> vi /etc/php-fpm.d/www.conf ファイルを下のコマンドに編集

~~~
user = nginx
group = nginx
listen.owner = nginx 
listen.group = nginx 
listen.mode = 0664
listen = /var/run/php70w-fpm.sock
~~~

![24](https://user-images.githubusercontent.com/43987455/50080320-28a2ff00-022f-11e9-80bc-344386fe0b46.JPG)
![25](https://user-images.githubusercontent.com/43987455/50080319-28a2ff00-022f-11e9-9c28-0aa8b54c7ec3.JPG)

> 起動と確認

![26](https://user-images.githubusercontent.com/43987455/50080479-82a3c480-022f-11e9-96fc-0ee7ab0c0a8e.JPG)

## PHP連結

> vi /etc/nginx/conf.d/default.conf　ファイルを編集
~~~
vi /etc/nginx/conf.d/default.conf
~~~

![27](https://user-images.githubusercontent.com/43987455/50080527-a6670a80-022f-11e9-9de6-ebca25ebfbba.JPG)

hostname -I でIPアドレス確認可能

![29](https://user-images.githubusercontent.com/43987455/50080526-a6670a80-022f-11e9-9155-ff35b7f14d87.JPG)
![28](https://user-images.githubusercontent.com/43987455/50080525-a6670a80-022f-11e9-81e2-a40b549f7440.JPG)

> port番号の設定 vi /etc/sysconfig/iptables ファイルを変更
~~~
vi /etc/sysconfig/iptables
~~~

> iptablesに下のコマンド追加
~~~
-A INPUT -p tcp -m state --state NEW -m tcp --dport 80 -j ACCEPT
~~~
![33](https://user-images.githubusercontent.com/43987455/50080738-23927f80-0230-11e9-883e-1f8605d5e78c.JPG)

> iptablesをreloadして、iptables -nLで確認

![34](https://user-images.githubusercontent.com/43987455/50080740-24c3ac80-0230-11e9-9383-33c58c94c93a.JPG)

## テスト

> Nginxテスト

![31](https://user-images.githubusercontent.com/43987455/50080924-8a179d80-0230-11e9-9b83-ff83f3bbd982.JPG)
![36](https://user-images.githubusercontent.com/43987455/50080824-52105a80-0230-11e9-9a86-1a05e0a05cea.JPG)

urlでIPアドレス入力してNginxが出たら成功

> PHPテスト

vi /uar/share/nginx/html/でindex.phpファイルを作る
~~~
<?php phpinfo() ?>
~~~

![35](https://user-images.githubusercontent.com/43987455/50080825-52105a80-0230-11e9-95e9-2894629d321f.JPG)
![37](https://user-images.githubusercontent.com/43987455/50080942-93a10580-0230-11e9-858a-567cf253f901.JPG)

urlでIPアドレス入力してphpが出たら成功


## portを追加する時

> vi /etc/nginx/conf.d/default.conf ファイルにサーバを追加します。

![38](https://user-images.githubusercontent.com/43987455/50081035-ce0aa280-0230-11e9-9721-8edb239db9af.JPG)
上の場合URLは 192.168.100.25:9001 になります。
最初見えるファイルは、/usr/share/nginx/html/testCentos フォルダにある index.php ファイルです。

最後にportを連結すると、使用できます。

![39](https://user-images.githubusercontent.com/43987455/50081072-e975ad80-0230-11e9-979a-8b5064fc69c7.JPG)
![40](https://user-images.githubusercontent.com/43987455/50081073-e975ad80-0230-11e9-9540-ec1a91bf2c81.JPG)
![41](https://user-images.githubusercontent.com/43987455/50081074-e975ad80-0230-11e9-90e8-87703f0cb3ef.JPG)

## nginxが実行されない時、文法検査

~~~
nginx -t
~~~

![43](https://user-images.githubusercontent.com/43987455/50081124-08743f80-0231-11e9-9ec4-8c027b80b56e.JPG)






