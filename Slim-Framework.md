# Slim-Framework

## composer設置

> composerを設置するため、vi /etc/php.ini ファイルを編集

![1](https://user-images.githubusercontent.com/43987455/50081312-7a4c8900-0231-11e9-9576-5cf746960d04.JPG)

> composerを設置
~~~
curl -sS https://getcomposer.org/installer | php -- -- install-dir=[設置するフォルダ]
~~~
![2](https://user-images.githubusercontent.com/43987455/50081349-93edd080-0231-11e9-8011-469e13cb6183.jpg)

> composerを全域命令語で変える（全域命令語はどんなフォルダでも、composerを使用することが可能です。）
~~~
mv composer.phar /usr/local/bin/composer
~~~
![3](https://user-images.githubusercontent.com/43987455/50081379-a962fa80-0231-11e9-81a2-c97ed5292f3b.JPG)

## Slim-framework設置

> プロジェクトフォルダに Slim-frameworkを設置（pwdを入力してフォルダ経路を確認）
~~~
composer require slim/slim "^3.0"
~~~
![4](https://user-images.githubusercontent.com/43987455/50081443-d57e7b80-0231-11e9-8d98-eacf185f57fb.JPG)

> 設置すると、composer.json composer.lock vendor ファイルが自動的に追加

![5](https://user-images.githubusercontent.com/43987455/50081444-d57e7b80-0231-11e9-9035-961afce5f93b.JPG)

> composer.json ファイルを編集

~~~
vi composer.json
~~~
monolog と autoload を追加

![6](https://user-images.githubusercontent.com/43987455/50081522-0959a100-0232-11e9-8c69-55d5c973d1a4.JPG)

## nginxに連結

> composer が入っているフォルダに src フォルダを追加して index.php を作る

index.php
~~~
<?php
use \Psr\Http\Message\ServerRequestInterface as Request;
use \Psr\Http\Message\ResponseInterface as Response;
require '/usr/share/nginx/html/bin/vendor/autoload.php';   // autoloadがあるフォルダの経路
$app = new \Slim\App;
$app->get('/', function($request, $response, $args) {   // root url
    return $response->withStatus(200)->write('Root address!');
});
$app->get('/test', function($request, $response, $args) {  //  ip:port/test
    return $response->withStatus(200)->write('Hello world test!');
});
$app->run();
?>
~~~

> url を確認

![10](https://user-images.githubusercontent.com/43987455/50081642-550c4a80-0232-11e9-8223-2d53bed430f3.JPG)

## REST-API練習
[REST-API File](https://github.com/JWLEE0425/testRestapi)
> index.php
~~~
<?php
use \Psr\Http\Message\ServerRequestInterface as Request;
use \Psr\Http\Message\ResponseInterface as Response;
require '/usr/share/nginx/html/bin/vendor/autoload.php';
$app = new \Slim\App;
$app->get('/', function($request, $response, $args) {
    return $response->withStatus(200)->write('Root address!');
});
$app->get('/test', function($request, $response, $args){
    return $response->withStatus(200)->write('Hello world test!');
});
$app->get('/product/{name}', function(Request $request, Response $response){
    $name=$request->getAttribute('name');
    $price = get_price($name);
    if(empty($price)) {
 $json = response(200, "Product Not Found", NULL);
    } else {
 $json = response(200, "Product Found", $price);
    }
    $response->getbody()->write("JSON : ".$json);
    return $response;
});
function get_price($name) {
    $products = [
 "book"=>20,
 "pen"=>10,
 "pencil"=>5
    ];
    foreach($products as $product=>$price) {
 if($product==$name) {
     return $price;
     break;
 }
    }
}
function response($status, $status_message, $data) {
    header("HTTP/1.1".$status);
    $response['status']=$status;
    $response['status message']=$status_message;
    $response['data']=$data;
    $json_response = json_encode($response);
    return $json_response;
}
$app->run();
~~~

> 結果画面

![11](https://user-images.githubusercontent.com/43987455/50081758-9866b900-0232-11e9-99e0-fee116e6d74b.JPG)

## DBを使ってREST-API、JSON練習

> 作ったDBテーブル

![17](https://user-images.githubusercontent.com/43987455/50081819-bc29ff00-0232-11e9-8125-861766130038.JPG)

> DB連結ファイル : config.php

~~~
<?php
function db_con() {
    $hostname = "localhost";
    $user = "root";
    $password = "pswd";  // DBのパスワード
    $dbname = "test";  // DBの名前
    $con = mysqli_connect($hostname, $user, $password, $dbname);  // 連結
    if (mysqli_connect_errno()) {
        echo "Failed to connect to MySQL: " . mysqli_connect_error();
    }
    return $con;
}
?>
~~~

> index.php の GET api
~~~
$app->get('/product', function($request, $response, $args) {
    $myArray = array();
    $con = db_con();
    $sql = 'select * from product';
    $result = mysqli_query($con, $sql);
    
    while($row = mysqli_fetch_array($result)) {
        $myArray[] = $row;
    }
    
    $response->getbody()->write("JSON : " . json_encode($myArray));
    return $response;
});
~~~

> 結果画面

![19](https://user-images.githubusercontent.com/43987455/50081886-ea0f4380-0232-11e9-9927-0b0e6bb637dc.JPG)

