------
### **video标签属性**
 - src ：视频的属性
 - poster：视频封面，没有播放时显示的图片
 - preload：预加载
 - autoplay：自动播放
 - loop：循环播放
 - controls：浏览器自带的控制条
 - width：视频宽度
 - height：视频高度

``` html
 <video id="media" src="h264.mp4" controls width="400px" heigt="400px"></video>  
```
### **获取video对象**
``` javascript
  Media = document.getElementById("media"); 
```
Media方法和属性：
HTMLVideoElement和HTMLAudioElement 均继承自HTMLMediaElement

Media.error; //null:正常
Media.error.code; //1.用户终止 2.网络错误 3.解码错误 4.URL无效

### **网络状态**
- Media.currentSrc; //返回当前资源的URL
- Media.src = value; //返回或设置当前资源的URL
- Media.canPlayType(type); //是否能播放某种格式的资源
- Media.networkState; //0.此元素未初始化 1.正常但没有使用网络 2.正在下载数据 3.没有找到资源
- Media.load(); //重新加载src指定的资源
- Media.buffered; //返回已缓冲区域，TimeRanges
- Media.preload; //none:不预载 metadata:预载资源信息 auto:

### **准备状态**
- Media.readyState;//1:HAVE_NOTHING 2:HAVE_METADATA 3.HAVE_CURRENT_DATA 4.HAVE_FUTURE_DATA 5.HAVE_ENOUGH_DATA
- Media.seeking; //是否正在seeking

### **回放状态**

 - Media.currentTime = value; //当前播放的位置，赋值可改变位置

 - Media.startTime; //一般为0，如果为流媒体或者不从0开始的资源，则不为0
 - Media.duration; //当前资源长度 流返回无限
 - Media.paused; //是否暂停
 - Media.defaultPlaybackRate = value;//默认的回放速度，可以设置
 - Media.playbackRate = value;//当前播放速度，设置后马上改变
 - Media.played; //返回已经播放的区域，TimeRanges，关于此对象见下文
 - Media.seekable; //返回可以seek的区域 TimeRanges
 - Media.ended; //是否结束
 - Media.autoPlay; //是否自动播放
 - Media.loop; //是否循环播放
 - Media.play(); //播放
 - Media.pause(); //暂停

### **视频控制**
 - Media.controls;//是否有默认控制条
 - Media.volume = value; //音量
 - Media.muted = value; //静音
 - TimeRanges(区域)对象
 - TimeRanges.length; //区域段数
 - TimeRanges.start(index) //第index段区域的开始位置
 - TimeRanges.end(index) //第index段区域的结束位置

### **相关事件**
``` javascript
var eventTester = function(e){
     Media.addEventListener(e,function(){
         console.log((new Date()).getTime(),e)
     },false);
}
```
 - eventTester("loadstart"); //客户端开始请求数据
 - eventTester("progress"); //客户端正在请求数据
 - eventTester("suspend"); //延迟下载
 - eventTester("abort"); //客户端主动终止下载（不是因为错误引起）
 - eventTester("loadstart"); //客户端开始请求数据
 - eventTester("progress"); //客户端正在请求数据
 - eventTester("suspend"); //延迟下载
 - eventTester("abort"); //客户端主动终止下载（不是因为错误引起），
 - eventTester("error"); //请求数据时遇到错误
 - eventTester("stalled"); //网速失速
 - eventTester("play"); //play()和autoplay开始播放时触发
 - eventTester("pause"); //pause()触发
 - eventTester("loadedmetadata"); //成功获取资源长度
 - eventTester("loadeddata"); //
 - eventTester("waiting"); //等待数据，并非错误
 - eventTester("playing"); //开始回放
 - eventTester("canplay"); //可以播放，但中途可能因为加载而暂停
 - eventTester("canplaythrough"); //可以播放，歌曲全部加载完毕
 - eventTester("seeking"); //寻找中
 - eventTester("seeked"); //寻找完毕
 - eventTester("timeupdate"); //播放时间改变
 - eventTester("ended"); //播放结束
 - eventTester("ratechange"); //播放速率改变
 - eventTester("durationchange"); //资源长度改变
 - eventTester("volumechange"); //音量改变

### **video标签支持播放的媒体类型**

**视频编码**
<table>
    <tr>
        <td>名称</td>
        <td>推出机构</td>
        <td>推出时间</td>
        <td>目前使用领域</td>
    </tr>
    <tr>
        <td>HEVC(H.265)</td><td>MPEG/ITU-T</td><td>2013</td><td>研发中</td>
    </tr>
    <tr>
        <td>H.264</td><td>MPEG/ITU-T</td><td>2003</td><td>各个领域</td>
    </tr>
    <tr>
        <td>MPEG4</td><td>MPEG</td><td>2001</td><td>不温不火</td>
    </tr>
    <tr>
        <td>MPEG2</td><td>MPEG</td><td>1994</td><td>数字电视</td>
    </tr>
    <tr>
        <td>VP9</td><td>Google</td><td>2013</td><td>研发中</td>
    </tr>
    <tr>
        <td>VP8</td><td>Google</td><td>2008</td><td>不普及</td>
    </tr>
    <tr>
        <td>VC-1</td><td>Microsoft Inc.</td><td>2006</td><td>微软平台</td>
    </tr>
</table>

**音频编码**
<table>
    <tr>
        <td>名称</td>
        <td>推出机构</td>
        <td>推出时间</td>
        <td>目前使用领域</td>
    </tr>
    <tr>
        <td>AAC</td><td>MPEG</td><td>1997</td><td>各个领域（新）</td>
    </tr>
    <tr>
        <td>AC-3</td><td>Dolby Inc.</td><td>1992</td><td>电影</td>
    </tr>
    <tr>
        <td>MP3</td><td>MPEG</td><td>1993</td><td>各个领域（旧）</td>
    </tr>
    <tr>
        <td>WMA</td><td>Microsoft Inc.</td><td>1999</td><td>微软平台</td>
    </tr>
</table>

**封装格式的主要作用是把视频码流和音频码流按照一定的格式存储在一个文件中**
<table>
    <tr>
        <td>名称</td>
        <td>推出机构</td>
        <td>流媒体</td>
        <td>支持的视频编码</td>
        <td>支持的音频编码</td>
    </tr>
    <tr>
        <td>AVI</td><td>Microsoft Inc.</td><td>不支持</td><td>几乎所有格式</td><td>几乎所有格式</td>
    </tr>
    <tr>
        <td>MP4</td><td>MPEG</td><td>支持</td><td>MPEG-2,MPEG-4,H.264,H.263等</td><td>AAC, MPEG-1 Layers I, II, III, AC-3等</td>
    </tr>
    <tr>
        <td>FLV</td><td>Adobe Inc.</td><td>支持</td><td>Sorenson,VP6,H.264</td><td>MP3, ADPCM, Linear PCM, AAC等</td>
    </tr>
    <tr>
        <td>MKV</td><td>CoreCodec Inc.</td><td>支持</td><td>几乎所有格式</td><td>几乎所有格式</td>
    </tr>
    <tr>
        <td>RMVB</td><td>RealNetworks Inc.</td><td>支持</td><td>RealVideo 8, 9, 10</td><td>AAC, Cook Codec, RealAudio Lossless</td>
    </tr>
</table>
**流媒体协议**
<table>
    <tr>
        <td>名称</td>
        <td>推出机构</td>
        <td>传输层协议</td>
        <td>客户端</td>
        <td>目前使用领域</td>
    </tr>
    <tr>
        <td>RTMP</td>
        <td>Adobe Inc.</td>
        <td>TCP</td>
        <td>Flash</td>
        <td>互联网直播</td>
    </tr>
    <tr>
        <td>HTTP</td>
        <td>WWW+IETF</td>
        <td>TCP</td>
        <td>Flash/h5video</td>
        <td>互联网点播</td>
    </tr>
</table>
由于早期播放客户端都是flash，而flash只支持.flv、.mp4后缀的音视频文件。由于flv早期使用起来更加方便，所以起初大量的网络视频都是以flv文件进行传输的，但是进入h5video时代后，video标签并不支持flv文件，所以一系列关于是否转向h5媒体的讨论，b站开源的flv.js也就是为了做好平滑过渡而出现的，它做了一件最重要的事，就是在将flv文件切成片段转成mp4碎片片段，然后通过[Media Source Extensions][1] 将 MP4 片段喂进浏览器,从而让浏览器间接的去支持了flv文件，并处理了一大批遗留的flv视频。

**Media Source Extensions**

支持类型：
 - Ogg = 带有 Theora 视频编码和 Vorbis 音频编码的 Ogg 文件
 - MPEG4 = 带有 H.264 视频编码和 AAC 音频编码的 MPEG 4 文件
 - WebM = 带有 VP8 视频编码和 Vorbis 音频编码的 WebM 文件


  [1]: https://w3c.github.io/media-source/