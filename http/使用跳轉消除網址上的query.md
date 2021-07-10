# 使用302(redirect)重新導向跳轉消除網址上的查詢
> 有時候我們會在網址傳送一些query像是`http://localhost/?key=value`，但有時候我們不希望，查詢停留在使用者的網址上，這時我們就能夠利用跳轉，將query清除

### 利用cookie的方式去將我們要傳遞的query存在client端儲存，並且在跳轉後取得cookie
在複雜點，可以利用將query存到server的一個空間，並且給他獨立id，再將這組id存入cookie，等待跳轉後透過id判斷剛剛存的query是什麼