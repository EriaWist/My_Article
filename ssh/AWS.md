# AWS SSH連線與傳送資料

取得ssh私鑰 [官方連結](https://lightsail.aws.amazon.com/ls/docs/zh_tw/articles/amazon-lightsail-ssh-using-terminal)
[參考資料](https://medium.com/@wyingqian365/%E5%AF%A6%E7%BF%92%E6%97%A5%E8%AA%8C-3-19-scp-to-ec2-%E8%97%89%E7%94%B1-ssh-%E7%9A%84%E9%81%A0%E7%AB%AF%E6%AA%94%E6%A1%88%E5%82%B3%E8%BC%B8%E6%8C%87%E4%BB%A4-778c24ef359)</br>
* 使用金鑰連線:`ssh -i /金鑰存放位置/下載下來的檔案 username@ip-address`</br>
* 使用scp傳送檔案:`scp -i /金鑰存放位置/金鑰.pem檔案 要傳送的檔名 username@ip-address: `

