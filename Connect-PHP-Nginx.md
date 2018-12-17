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

nginx.repo
~~~
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/7/$basearch/
gpgcheck=0
enabled=1
~~~

![4](https://user-images.githubusercontent.com/43987455/50079583-52f3bd00-022d-11e9-800c-bd6788ea3903.JPG)
