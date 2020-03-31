# Rasdaman-Install-guide
安裝Rasdaman database到Ubuntu 18.04上

* [Rasdaman官方網站]( https://rasdaman.org/ "Title")  
* [Rasdaman]( https://doc.rasdaman.org/index.html/ "Title")

1.在terminal裡用wget指令新增Rasdaman repository 

```console
user@ubuntu:~$ sudo wget -O - https://download.rasdaman.org/packages/rasdaman.gpg | sudo apt-key add -
```

2.選擇stable版本  
```console
user@ubuntu:~$ echo "deb [arch=amd64] https://download.rasdaman.org/packages/deb bionic stable" \
| sudo tee /etc/apt/sources.list.d/rasdaman.list
```

3.透過apt-get安裝Rasdaman
```console
user@ubuntu:~$ sudo apt-get update
user@ubuntu:~$ sudo apt-get install rasdaman

#用source命令讓rasdaman.sh立即生效，將rasql加到環境變數中
user@ubuntu:~$ source /etc/profile.d/rasdaman.sh
```
4.確認Rasdaman伺服器能回傳rasql的query的結果
```console
user@ubuntu:~$ rasql -q 'select c from RAS_COLLECTIONNAMES as c' --out string
```
結果應如下
```console
rasql: rasdaman query tool v1.0, rasdaman 9.8.0.
Opening database RASBASE at 127.0.0.1:7001... ok.
Executing retrieval query... ok.
Query result collection has 3 element(s):
  Result object 1: mr2
  Result object 2: mr
  Result object 3: rgb
rasql done.
```
5.確認Petascope是否初始化，開啟瀏覽器，輸入以下URL:  
<http://localhost:8080/rasdaman/ows>   
若看到畫面即代表安裝成功！

6.其他相關指令
```console
#啟動關閉Rasdaman服務
user@ubuntu:~$ service rasdaman start
user@ubuntu:~$ service rasdaman stop
#檢視Rasdaman
user@ubuntu:~$ service rasdaman status
```
