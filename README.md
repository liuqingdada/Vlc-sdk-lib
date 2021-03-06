### Vlc-sdk-lib

构建切换大小屏播放器  参考<br>

  * [VideoHeaderView]https://github.com/mengzhidaren/RecylerViewMultiHeaderView <br>

转码视频的命令行工具  参考<br>

  * [FFmpegCmdSdk]https://github.com/mengzhidaren/FFmpegCmdSdk <br>
  
在RecyclerView中播放器的实现  参考<br>
  * [VlcPlayer]https://github.com/mengzhidaren/VlcPlayer <br>

---

# 实现的功能
```
能支持MP4,FLV,AVI,TS,3GP,RMVB,WM,WMV等格式还有网络流 http,rtsp,rtmp,mms,m3u8.
软硬解切换.支持vlc指令  < transform:rotation=90>
当前缓冲百分比    <MediaPlayer.Event.Buffering>
视频(音频)播放速度可调,任意速度可调. (0.25-4)   < player.setRate(float rate); >
加载字幕，设置镜面<>
```
# 使用方法
```
 <org.videolan.vlc.VlcVideoView
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
VlcVideoPlayer   player = new VlcVideoPlayer(context);
                 player.setMediaListenerEvent(new MediaListenerEvent());
                 player.startPlay(path);
 thumbnail 
 不是很推荐用这个方法，不稳定
 如果你有截图需求最好用我写的ffmpeg截图       
 截图方法   byte[] b = VLCUtil.getThumbnail(media, width, height);
           if (b != null) {
                 Bitmap thumbnail = Bitmap.createBitmap(width, height, Bitmap.Config.ARGB_8888);
                 thumbnail.copyPixelsFromBuffer(ByteBuffer.wrap(b));
           }
```

#引用库文件
```
   dependencies {
   
   过期了 //compile 'com.yyl.vlc:vlc-android-sdk:1.3.0'
   
   最好下载我整理的官方的库
   推荐使用  2.5.12 library 配合videoCache使用
   具体看demo
   }
    ndk {
               abiFilters 'armeabi-v7a'//,'x86_64','arm64-v8a','x86' //支持的abi    可选 精简的库
    }
         
  目前支持的库 ： x86_64     x86    armeabi-v7a    arm64-v8a    mips    mips64
```
### 说明 ###
```
版本libvlc 是我自已搭建环境编译的库尽量同步服务器  版本：3.0.0-2.1.0
版本libvlc2.0.0 我自已编译修改的库文件
版本libvlc2.0.6 官方库文件 方便测试
版本libvlc2.5.5 官方库文件
版本libvlc2.5.12 官方库文件 最新版本 推荐

V1.0.1
1.提交第一版
V1.2.0
1更新播放控件
发现bug或有好的建议欢迎[issue]
V1.3.0
增加 mips   mips64  指令集的支持
V1.4.0 //有空在更新
可下载2.5.12代码引用至工程中 
```

## Donate ##
Alipay:<br>
![](https://raw.githubusercontent.com/mengzhidaren/Vlc-sdk-lib/master/screenshots/yyl.png)
<br>
谢谢支持我会和官方同步更新<br>


### 官方网站 ###
* [vlc](https://www.videolan.org)

### 编译方法 ###

```
vlc-android的代码在  linux  ubuntu64  16.4  中搭建编绎环境
android-sdk 版本 api25
ndk版本 r13b
java 版本 8
vlc-android 版本 3.0.0-v2.1.0版本
```

1.在win10中安装的  VMware Workstation Pro
安装ubuntu 64  16 的最新版
![](https://raw.githubusercontent.com/mengzhidaren/Vlc-sdk-lib/master/screenshots/1.png)

2.安装  linux 版的  jdk   sdk 最新版

```
安装包管理工具和开源库等
参考：https://wiki.videolan.org/AndroidCompile/

## sudo apt-get install automake ant autopoint cmake build-essential libtool \
     patch pkg-config protobuf-compiler ragel subversion unzip git
```
3.  ubuntu 64 vlc-android环境设置
```
sudo gedit /etc/profile
$source /etc/profile

export NDK=/opt/sdk/android-sdk-linux/ndk-bundle
export ANDROID_NDK=/opt/sdk/android-sdk-linux/ndk-bundle
export PATH=${ANDROID_NDK}:$PATH
export ANDROID_SDK=/opt/sdk/android-sdk-linux
export PATH=$ANDROID_SDK/tools:$ANDROID_SDK/platform-tools:$PATH

export JAVA_HOME=/opt/sdk/jdk1.8.0_101
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib:${JAVA_HOME}/lib/tools.jar
export PATH=${JAVA_HOME}/bin:$PATH

export ANDROID_ABI=armeabi-v7a   //对应的cpu平台 .so包
#export ANDROID_ABI=x86   //编译对应的平台
```

![](https://raw.githubusercontent.com/mengzhidaren/Vlc-sdk-lib/master/screenshots/3.png)
![](https://raw.githubusercontent.com/mengzhidaren/Vlc-sdk-lib/master/screenshots/4.png)
![](https://raw.githubusercontent.com/mengzhidaren/Vlc-sdk-lib/master/screenshots/8.png)
![](https://raw.githubusercontent.com/mengzhidaren/Vlc-sdk-lib/master/screenshots/9.png)


### DEMO效果预览
![image](https://github.com/mengzhidaren/VlcPlayer/blob/master/GIF/j1.gif)