### **支持安卓14**
反编译AndroidManifest.xml，修改找到如下代码：
```
<uses-sdk
        android:minSdkVersion="17"
        android:targetSdkVersion="22" />

```
将其中的targetSdkVersion值改为24即可，修改后的代码如下
```
<uses-sdk
        android:minSdkVersion="17"
        android:targetSdkVersion="24" />
```

### **流量进服**
编辑classes.dex文件，修改路径为com/mojang/minecraftpe/MainActivity下的类。

在MainActivity类中，找到isNetworkEnabled函数。

定位到这一部分代码：

   ```
 .line 626
    .restart local v1  # "info":Landroid/net/NetworkInfo;
    :cond_1d
    const/4 v2, 0x0
```
将IPv4参数中的0x0改为 0x1即可
如下
   ```
 .line 626
    .restart local v1  # "info":Landroid/net/NetworkInfo;
    :cond_1d
    const/4 v2, 0x1
```
