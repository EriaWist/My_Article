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
docker run -dp 80:80 [image名稱:tag]
```
- `-d` 在背景執行 `Run container in background and  print container ID`
- `-p` 把電腦的 80 port 對應到 Docker Container 的 80 port `Publish a container's port(s) to the host`
> 限制記憶體使用量 (限制300M)
```
docker run -dp 80:80 -m 300M [image名稱:tag]
```
> 終端操作
```
docker run -it ubuntu
```
- `-i` 需要與 Container 做互動(輸入、輸出)時使用 `Keep STDIN open even if not attached`
- `-t` 簡單來講就是用 terminal 的方式進入 Container `Allocate a pseudo-TTY`

---
### 進入背景執行的容器 Container 有兩種方法
> docker attach 讓在背景執行的Container回到前台，退出時Container也跟著被關閉
```
docker attach [容器 ID]
```
> docker exec 進入後退出時也不會使Container關閉
```
docker exec -it [容器 ID] bash
```
ex.
```
docker run -itd ubuntu
docker exec -it [容器 ID] bash
docker attach [容器 ID]
```