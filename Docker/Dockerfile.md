# Dockerfile介紹

### [FROM](https://docs.docker.com/engine/reference/builder/#from)
``` dockerfile
FROM ubuntu:20.10 
# 架構像下面
# FROM image:版本號
```
* image : 放上想用的容器名稱 請參考[Dockerhub](https://hub.docker.com/search?q=&type=image)
，假如需要最基礎的可以選擇[Alpine image](https://hub.docker.com/_/alpine/)他為最小大小的容器(5MB)
* 版本號 : 選擇的image的tage但是通常tage會使用版本號，來做版本控制

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
用來讓容器內的 port 與內部連接 ＊當你需要讓內部port與主機post連接需要在run時使用`docker run -p 80:80 [image名稱]`
