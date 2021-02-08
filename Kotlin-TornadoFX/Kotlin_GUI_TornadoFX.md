# Kotlin_GUI_TornadoFX
## [gradle建立Kotlin應用](https://docs.gradle.org/current/samples/sample_building_kotlin_libraries.html)
```
$ mkdir demo
$ cd demo
建議新增資料夾
$ gradle init
//為了配合大多數開發者習慣
Select build script DSL:
  1: Groovy
  2: Kotlin
Enter selection (default: Groovy) [1..2] 1
我們選擇Groovy
```
## [TornadoFX](https://edvin.gitbooks.io/tornadofx-guide/content/part1/2_Setting_Up.html)
在app/build.gradle設定
```
plugins {
    id 'application'
    id 'org.openjfx.javafxplugin' version '0.0.8'
}
dependencies {
    implementation 'no.tornado:tornadofx:1.7.20'
}
javafx {
    version = "11.0.2"
    modules = ['javafx.controls', 'javafx.graphics']
}
compileKotlin {
    kotlinOptions.jvmTarget = "15"
}

```
因為版本現在jvm已經到15以及x.y.z是看TornadoFX目前版本為1.7.20
[TornadoFX版本](https://tornadofx.io/)

接下來建立[簡單頁面測試](https://edvin.gitbooks.io/tornadofx-guide/content/part1/3_Components.html)

``` Kotlin
package com.eria.app //這是我的package

import tornadofx.*

class MyApp: App(MyView::class)

fun main(args: Array<String>) {
    launch<MyApp>(args)
}

class MyView: View() {
    override val root = vbox {
        button(" 123 ")
        label(" 456 ")
    }
}
```
最後下指令[打包](https://docs.gradle.org/current/userguide/application_plugin.html)
```
gradle distZip 打包成 ZIP
gradle distTar 打包成 TAR
```
檔案放在`/Kotlin_GUI_TornadoFX/app/build/distributions`


github:[連結](https://github.com/EriaWist/Kotlin_GUI_TornadoFX)


