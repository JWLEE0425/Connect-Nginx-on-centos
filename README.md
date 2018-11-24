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

![19](https://user-images.githubusercontent.com/43987455/48971720-d8d27d00-f060-11e8-945c-5ad47ba3fb3e.JPG)
![20](https://user-images.githubusercontent.com/43987455/48971721-d8d27d00-f060-11e8-990e-291563ea37ed.JPG)
![21](https://user-images.githubusercontent.com/43987455/48971722-d96b1380-f060-11e8-9d82-3838a24d1bc4.JPG)
![22](https://user-images.githubusercontent.com/43987455/48971723-d96b1380-f060-11e8-95f4-4257cc9ec107.JPG)
![23](https://user-images.githubusercontent.com/43987455/48971724-d96b1380-f060-11e8-9e74-d95da572fd78.JPG)
![24](https://user-images.githubusercontent.com/43987455/48971725-d96b1380-f060-11e8-8e80-497a59eca631.JPG)
![25](https://user-images.githubusercontent.com/43987455/48971726-d96b1380-f060-11e8-913a-b7e5939ceba8.JPG)
![26](https://user-images.githubusercontent.com/43987455/48971701-d6702300-f060-11e8-861d-0e3410d1dff4.JPG)
![27](https://user-images.githubusercontent.com/43987455/48971702-d6702300-f060-11e8-94ca-da4b398c71f2.JPG)
![28](https://user-images.githubusercontent.com/43987455/48971703-d6702300-f060-11e8-9aff-19dc823be91b.JPG)
![29](https://user-images.githubusercontent.com/43987455/48971704-d708b980-f060-11e8-94af-d6639724d3ac.JPG)
![30](https://user-images.githubusercontent.com/43987455/48971705-d708b980-f060-11e8-9d2d-7d42a2a8bfa8.JPG)
![31](https://user-images.githubusercontent.com/43987455/48971706-d708b980-f060-11e8-80aa-e8a06f1296cb.JPG)
![32](https://user-images.githubusercontent.com/43987455/48971707-d708b980-f060-11e8-83e6-626fc4b1f4de.JPG)
![33](https://user-images.githubusercontent.com/43987455/48971708-d7a15000-f060-11e8-979f-7c406f9b6b26.JPG)
![34](https://user-images.githubusercontent.com/43987455/48971709-d7a15000-f060-11e8-8504-4649d2bb6e98.JPG)
![35](https://user-images.githubusercontent.com/43987455/48971710-d7a15000-f060-11e8-9f12-7004332ce017.JPG)
![36](https://user-images.githubusercontent.com/43987455/48971711-d7a15000-f060-11e8-9381-272b5181c7a4.JPG)
![37](https://user-images.githubusercontent.com/43987455/48971712-d839e680-f060-11e8-9bc5-d1f9b296af84.JPG)
![38](https://user-images.githubusercontent.com/43987455/48971713-d839e680-f060-11e8-87b1-56c644251470.JPG)
![39](https://user-images.githubusercontent.com/43987455/48971714-d839e680-f060-11e8-9269-cc2959710fa7.JPG)
![40](https://user-images.githubusercontent.com/43987455/48971715-d839e680-f060-11e8-8802-8b4b4210a1a1.JPG)
![41](https://user-images.githubusercontent.com/43987455/48971716-d839e680-f060-11e8-8ab1-585d6a12c42a.JPG)
![42](https://user-images.githubusercontent.com/43987455/48971717-d8d27d00-f060-11e8-8963-86160f093984.JPG)
![43](https://user-images.githubusercontent.com/43987455/48971718-d8d27d00-f060-11e8-991b-bf6eb450425b.JPG)
![44](https://user-images.githubusercontent.com/43987455/48971719-d8d27d00-f060-11e8-84e2-2e955345ef44.JPG)








