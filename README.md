# Install-Nginx-on-CentOS

![1](https://user-images.githubusercontent.com/43987455/48970810-25fc2200-f054-11e8-925b-05bf54db256d.JPG)

* Virtualbox

* OS<br>
CentOS 7

* サーバー<br>
Nginx 1.14 1

* 言語<br>
PHP 7.0.32


## ダウンロード Virtual Box

https://www.virtualbox.org/wiki/Downloads

![2](https://user-images.githubusercontent.com/43987455/48970852-e6820580-f054-11e8-9b0b-06123f495e86.JPG)

## ダウンロード CentOS 7(File size : 4.16G)

https://www.centos.org/

![3](https://user-images.githubusercontent.com/43987455/48970903-c69f1180-f055-11e8-92ea-19ebbca6345f.JPG)
![4](https://user-images.githubusercontent.com/43987455/48970900-c272f400-f055-11e8-82e4-1bc0e6249f4b.JPG)

> ダウンロード **'CentOS-7-x86_64-DVD-1804.iso'**

![5](https://user-images.githubusercontent.com/43987455/48970901-c272f400-f055-11e8-9de2-9fabdc51074c.JPG)

## Virtual BoxにCentOSを設置するための準備

> 新規選択後、名前設定

![7](https://user-images.githubusercontent.com/43987455/48971121-26e38280-f059-11e8-80eb-5396f1dde756.JPG)

> メモリーサイズ設定(1Gまたは、2G)

![8](https://user-images.githubusercontent.com/43987455/48971122-26e38280-f059-11e8-9d1f-108db871a425.JPG)


> 基本設定

![9](https://user-images.githubusercontent.com/43987455/48971123-26e38280-f059-11e8-9522-a14631c2fea6.JPG)
![10](https://user-images.githubusercontent.com/43987455/48971124-26e38280-f059-11e8-8051-3089f513ef70.JPG)
![11](https://user-images.githubusercontent.com/43987455/48971125-277c1900-f059-11e8-88fb-e244a241ef4c.JPG)


> ハードディスク サイズ設定(私は50Gに設定しました。サイズを小さくする場合、容量不足で実行不可)

![12](https://user-images.githubusercontent.com/43987455/48971126-277c1900-f059-11e8-85fb-864cf960db9d.JPG)

> 設定

![13](https://user-images.githubusercontent.com/43987455/48971127-277c1900-f059-11e8-9145-0b61aa14324f.JPG)

> ストレージで前にダウンロードしたISOファイルを追加します。

![14](https://user-images.githubusercontent.com/43987455/48971128-2814af80-f059-11e8-8fab-6a0def49d39d.JPG)
![15](https://user-images.githubusercontent.com/43987455/48971129-2814af80-f059-11e8-884f-f06d7c82a188.JPG)
![16](https://user-images.githubusercontent.com/43987455/48971118-25b25580-f059-11e8-98ee-4167f6f40267.JPG)

> ネットワーク設定後、OKクリック。

![17](https://user-images.githubusercontent.com/43987455/48971119-264aec00-f059-11e8-8bc7-a495c978fb7a.jpg)

## Vitual BoxでCentOS設置

> 起動

![18](https://user-images.githubusercontent.com/43987455/48971120-264aec00-f059-11e8-9462-c119c5d05f06.JPG)

![19](https://user-images.githubusercontent.com/43987455/48971551-58ab1800-f05e-11e8-9179-b21d4df27e2c.JPG)
![20](https://user-images.githubusercontent.com/43987455/48971533-3ca77680-f05e-11e8-8363-b61779567b0c.JPG)
![21](https://user-images.githubusercontent.com/43987455/48971534-3ca77680-f05e-11e8-8d9e-afd7512d322e.JPG)
![22](https://user-images.githubusercontent.com/43987455/48971535-3ca77680-f05e-11e8-9160-8adaf7fc1d16.JPG)
![23](https://user-images.githubusercontent.com/43987455/48971536-3ca77680-f05e-11e8-955d-5754bc9a8270.JPG)
![24](https://user-images.githubusercontent.com/43987455/48971537-3d400d00-f05e-11e8-87f0-bdd1f3c8efa9.JPG)
![25](https://user-images.githubusercontent.com/43987455/48971538-3d400d00-f05e-11e8-81ed-72c2991a110a.JPG)
![26](https://user-images.githubusercontent.com/43987455/48971539-3d400d00-f05e-11e8-866e-c3e2ba470089.JPG)
![27](https://user-images.githubusercontent.com/43987455/48971540-3d400d00-f05e-11e8-8ad5-be4efd4cf424.JPG)
![28](https://user-images.githubusercontent.com/43987455/48971541-3d400d00-f05e-11e8-90c6-0317a4272457.JPG)
![29](https://user-images.githubusercontent.com/43987455/48971542-3dd8a380-f05e-11e8-8f94-30b64ba5b6a6.JPG)
![30](https://user-images.githubusercontent.com/43987455/48971543-3dd8a380-f05e-11e8-9b8f-a3cedc740d6f.JPG)
![31](https://user-images.githubusercontent.com/43987455/48971544-3dd8a380-f05e-11e8-904f-e6241b7a4590.JPG)
![32](https://user-images.githubusercontent.com/43987455/48971520-3addb300-f05e-11e8-89ec-1b22d650a741.JPG)
![33](https://user-images.githubusercontent.com/43987455/48971521-3addb300-f05e-11e8-9857-a2fb9cc468bd.JPG)
![34](https://user-images.githubusercontent.com/43987455/48971522-3b764980-f05e-11e8-8f84-5fc21cdf7fc8.JPG)
![35](https://user-images.githubusercontent.com/43987455/48971523-3b764980-f05e-11e8-986b-c986c45c81d6.JPG)
![36](https://user-images.githubusercontent.com/43987455/48971524-3b764980-f05e-11e8-89a5-41466f7fc028.JPG)
![37](https://user-images.githubusercontent.com/43987455/48971525-3b764980-f05e-11e8-8e89-8331ea86d794.JPG)
![38](https://user-images.githubusercontent.com/43987455/48971526-3b764980-f05e-11e8-91d0-c807953828bb.JPG)
![39](https://user-images.githubusercontent.com/43987455/48971527-3c0ee000-f05e-11e8-81f0-e89c185e3d58.JPG)
![40](https://user-images.githubusercontent.com/43987455/48971528-3c0ee000-f05e-11e8-9cee-487e89098bdc.JPG)
![41](https://user-images.githubusercontent.com/43987455/48971529-3c0ee000-f05e-11e8-9825-318c273ac437.JPG)
![42](https://user-images.githubusercontent.com/43987455/48971530-3c0ee000-f05e-11e8-85f0-63f3f4ff8c90.JPG)
![43](https://user-images.githubusercontent.com/43987455/48971531-3c0ee000-f05e-11e8-8e32-5324a6e2d9ff.JPG)
![44](https://user-images.githubusercontent.com/43987455/48971532-3ca77680-f05e-11e8-8026-f8591d1c92c4.JPG)












