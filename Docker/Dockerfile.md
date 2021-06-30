# Dockerfile介紹

### [FROM](https://docs.docker.com/engine/reference/builder/#from)
``` dockerfile
FROM ubuntu:20.10 
# 架構像下面
# FROM image:版本號
```
* image : 放上想用的容器名稱 請參考[Dockerhub](https://hub.docker.com/search?q=&type=image)
，假如需要最基礎的可以選擇[Alpine image](https://hub.docker.com/_/alpine/)他的大小為(5MB) or [scratch image](https://hub.docker.com/_/scratch)(他只能夠執行二進制檔案)
* 版本號 : 選擇的image的tage但是通常tage會使用版本號，來做版本控制

---
### [COPY](https://docs.docker.com/engine/reference/builder/#copy)
複製資料夾到Docker系統裡面
``` dockerfile
COPY . /app
```
前面：本機電腦的資料夾 `.`代表整個資料夾

後面：複製檔案的目的位置 在Docker內的資料夾

---

### [RUN](https://docs.docker.com/engine/reference/builder/#run)
``` dockerfile
RUN mkdir app
# RUN shell指令
RUN cd app && touch test
# 可以使用 && 將兩條指令連再一起
```
執行 docker build 時會執行的 shell指令 
> ＊注意只有在build image時會執行 run 時，並不會執行它而是CMD

---
### [WORKDIR](https://docs.docker.com/engine/reference/builder/#workdir)
簡單來講就是移動到那個資料夾
``` dockerfile
WORKDIR /app
```
移動到app資料夾 假如在下方打 `pwd` 就會顯示當前位置 `/app`

---
### [CMD](https://docs.docker.com/engine/reference/builder/#cmd)
``` dockerfile
CMD ls
#CMD shell指令
CMD ["ls"]
# 也可以這樣
```
這裡是在跑 docker run 後會執行的shell指令

---

### [EXPOSE](https://docs.docker.com/engine/reference/builder/#expose)
``` dockerfile
# 開啟port 80:80 也可以開啟特定tcp或udp
EXPOSE 80
EXPOSE 80/tcp
EXPOSE 80/udp
```
用來讓容器內的 port 與內部連接 **＊當你需要讓內部port與主機post連接需要在run時使用`docker run -p 80:80 [image名稱]`**
