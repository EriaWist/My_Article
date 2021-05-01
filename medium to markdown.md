# 把 medium 轉換成 markdown
[參考文章(付費)](https://macropus.medium.com/export-your-medium-posts-to-markdown-b5ccc8cb0050)
1. 安裝 mediumexporter(npm可以參考[安裝與移除node.js](https://github.com/EriaWist/My_Article/blob/main/nod.js/%E5%AE%89%E8%A3%9D%E8%88%87%E7%A7%BB%E9%99%A4.md))
``` npm
npm install -g mediumexporter
```
2. 移動到要儲存的地方 ex:桌面

``` cml
cd Desktop
```
3. 輸入網址以及儲存檔案名稱

```
mediumexporter 網址 > 檔名.md
範例: 
mediumexporter https://eriawist.medium.com/%E5%96%AE%E4%BE%8B%E6%A8%A1%E5%BC%8F-singleton-977dfb4dfb66 > medium_post.md
```
Google Chrome上也有一些插件可做使用