# AWS SSH連線與傳送資料

取得ssh私鑰 [官方連結](https://lightsail.aws.amazon.com/ls/docs/zh_tw/articles/amazon-lightsail-ssh-using-terminal)</br>
* 使用金鑰連線:`ssh -i /金鑰存放位置/下載下來的檔案 username@ip-address`</br>
* 使用scp傳送檔案:`scp -i /金鑰存放位置/金鑰.pem檔案 要傳送的檔名 username@ip-address: `