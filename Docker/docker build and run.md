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


---
### 停止刪除容器和镜像檔(image)
> 顯示所有容器的ID
``` 
docker ps -aq
```
[參數參考](https://docs.docker.com/engine/reference/commandline/ps/)
> 停止所有容器
```
docker stop $(docker ps -aq)
```
> 刪除所有容器
```
docker rm $(docker ps -aq)
```
> 刪除所有鏡像檔(image)
```
docker rmi $(docker images -q)
```
想要刪除單個只需要將`$(docker ps -aq)`替換成容器ID

---
### 執行image
> 執行
```
docker run [image名稱:tag]
```
> 執行有對外(server)接口的 ex.開啟80(外)對80(內)接口
```
docker run -p 80:80 [image名稱:tag]
```