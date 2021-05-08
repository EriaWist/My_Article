# fatal: unable to checkout working tree
主要也是因為Windows在路徑文件上的規定(不能有特殊符號或[空格](https://github.com/EriaWist/My_Article/blob/main/Git/warning:Clone%20succeeded,but%20checkout%20failed.md))
Ex:
```
error: invalid path 'Kotlin/<T>泛型編程(Generic programming).md'
```
理論上`\，/，：，*，？，“，<，>或|`都會出問題

可以看到`<T>`的`<和>`在Windows上無法當作檔案名稱可以用下載Zip來看系統把哪些符號替換掉了[參考資料](https://stackoverflow.com/questions/24898680/fatal-unable-to-checkout-working-tree/63860987)
