# docker build and run
### docker build

直接編譯 docker build 後面是Dockerfile的文件資料夾位置(建議開啟一個資料夾並且將需要使用到的檔案以及Dockerfile放入)
``` docker
docker build .
```
可以加上`--tag 標籤`標記標籤
```
docker build --tag myImage .  
```
使用`docker image ls`可以查看全部的image
