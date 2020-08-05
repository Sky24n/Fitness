Language: [English](README-EN.md) | 中文简体

## Fitness（个人项目，暂未开源）
Flutter开发的微博客户端，同时支持Android和iOS。与官方微博x9.99%相似度体验，离线模式，多语言支持，主题随心换，超乎想象的流畅度，各种惊喜的细节等待你一一发现。

### 支持功能：
查看微博动态、正文、评论  
查看热门话题、微博、热搜  
支持话题、@、表情、全文  
离线模式  
国际化  
主题色


### 项目动态
应用于2020.05.06提交至微博开发平台，目前还在审核中，暂无法申请微博授权!  
ps：作者也不清楚是否能通过审核，何时通过审核，但大家还是可以本地体验相关功能。  
目前运动和消息板块未开发，运动板块暂时放的实时疫情，消息板块展示九宫格示例。

### 分享内容

#### 1、九宫格图片控件 [NineGridView](https://juejin.im/post/5ee825ab5188251f3f07af75)
类似微博动态，微信朋友圈，微信群组，钉钉群组，支持单张大图预览。
```yaml
NineGridView(
  margin: EdgeInsets.all(12),
  padding: EdgeInsets.all(5),
  space: 5,
  type: NineGridType.weChatGp,
  itemCount: itemCount,
  itemBuilder: (BuildContext context, int index) {},
);
```

#### 2、拖拽九宫格图片控件 [DragSortView](https://juejin.im/post/5ee825ab5188251f3f07af75)
类似微博/微信发布动态九宫格，支持按压放大效果，拖拽排序，拖拽到指定位置删除。
```yaml
DragSortView(
  imageList,
  space: 5,
  margin: EdgeInsets.all(20),
  padding: EdgeInsets.all(0),
  itemBuilder: (BuildContext context, int index) {},
  initBuilder: (BuildContext context) {},
  onDragListener: (MotionEvent event, double itemWidth) {
    /// 判断拖动到指定位置删除
    /// return true;
    if (event.globalY > 600) {
      return true;
    }
    return false;
  },
);     
```

#### 3、获取图片尺寸 [ImageUtil](https://github.com/Sky24n/flustars)
大图功能必备工具。
```yaml
Image image = new Image(image: new CachedNetworkImageProvider("Url"));
Image imageAsset = new Image.asset("");
Image imageFile = new Image.file(File("path"));
Image imageNetwork = new Image.network("url");
Image imageMemory = new Image.memory(null);

ImageUtil imageUtil = ImageUtil();
Rect rect = await imageUtil.getImageSize(image: image);  
ImageUtil().getImageSize(image: image).then((Rect rect) {
  print("rect: " + rect.toString();
});

```

#### 4、简单加解密 [EncryptUtil](https://github.com/Sky24n/common_utils)
异或对称加解密 + Base64加解密
```yaml
const String key = '11, 22, 33, 44, 55, 66';
String value = 'Sky24n';
String encode = EncryptUtil.xorBase64Encode(value, key); // WH1YHgMs
String decode = EncryptUtil.xorBase64Decode(encode, key); // Sky24n
```
#### 5、[JsonUtil](https://github.com/Sky24n/common_utils)
简单封装json字符串转对象。
```yaml
String objStr = "{\"name\":\"成都市\"}";
City hisCity = JsonUtil.getObj(objStr, (v) => City.fromJson(v));

String listStr = "[{\"name\":\"成都市\"}, {\"name\":\"北京市\"}]";
List<City> cityList = JsonUtil.getObjList(listStr, (v) => City.fromJson(v));
```

#### 6、时间格式化 [DateUtil](https://github.com/Sky24n/common_utils)
格式化时间戳。
```yaml
/// year -> yyyy/yy   month -> MM/M    day -> dd/d
/// hour -> HH/H      minute -> mm/m   second -> ss/s

DateUtil.formatDateMs(DateTime.now().millisecondsSinceEpoch, format: DataFormats.full); // 2019-07-09 16:51:14
DateUtil.formatDateStr("2019-07-09 16:51:14", format: "yyyy/M/d HH:mm:ss"); // 2019/7/9 16:51:14
DateUtil.formatDate(DateTime.now(), format: "yyyy/MM/dd HH:mm:ss");  // 2019/07/09 16:51:14
DateUtil.formatDateMs(ms, format: "yyyy年MM月dd日 HH时mm分ss秒");  // 2019年07月09日 16时51分14秒
```
#### 7、时间轴 [TimelineUtil](https://github.com/Sky24n/common_utils)
类似微信朋友圈，微博动态时间线。
```yaml
enum DayFormat {
  ///(less than 10s->just now)、x minutes、x hours、(Yesterday)、x days.
  ///(小于10s->刚刚)、x分钟、x小时、(昨天)、x天.
  Simple,

  ///(less than 10s->just now)、x minutes、x hours、[This year:(Yesterday/a day ago)、(two days age)、MM-dd ]、[past years: yyyy-MM-dd]
  ///(小于10s->刚刚)、x分钟、x小时、[今年: (昨天/1天前)、(2天前)、MM-dd],[往年: yyyy-MM-dd].
  Common,

  ///日期 + HH:mm
  ///(less than 10s->just now)、x minutes、x hours、[This year:(Yesterday HH:mm/a day ago)、(two days age)、MM-dd HH:mm]、[past years: yyyy-MM-dd HH:mm]
  ///小于10s->刚刚)、x分钟、x小时、[今年: (昨天 HH:mm/1天前)、(2天前)、MM-dd HH:mm],[往年: yyyy-MM-dd HH:mm].
  Full,fitness_rec_list.json
}

TimelineUtil.format(timeMillis, locale: Localizations.localeOf(context).languageCode, dayFormat: DayFormat.Common);
```

### Screenshots

截图无法查看？  
掘金地址：[Flutter 仿微博客户端](https://juejin.im/post/5ebd74b5f265da7bbd2f9aa6)  
简书地址：[Flutter 仿微博客户端](https://www.jianshu.com/p/0f761fe6ad66)

|首页|探索|我的|
|:---:|:---:|:---:|
|<img src="https://s1.ax1x.com/2020/08/05/ar0FY9.jpg" width="220" height="465"/>|<img src="https://s1.ax1x.com/2020/08/05/ar0Zy6.jpg" width="220" height="465"/>|<img src="https://s1.ax1x.com/2020/08/05/ar0neO.png" width="220" height="465"/>|
|微博发布|微博正文|个人页面|
|<img src="https://s1.ax1x.com/2020/08/05/ar0rpn.gif" width="220" height="391"/>|<img src="https://s1.ax1x.com/2020/08/05/ar0fk4.gif" width="220" height="391"/>|<img src="https://s1.ax1x.com/2020/08/05/ar07X6.gif" width="220" height="391"/>|
|授权|设置|图片|
|<img src="https://s1.ax1x.com/2020/08/05/arBiB8.jpg" width="220" height="465"/>|<img src="https://s1.ax1x.com/2020/08/05/arBm3n.png" width="220" height="465"/>|<img src="https://s1.ax1x.com/2020/08/05/arBQBT.jpg" width="220" height="465"/>|
|<img src="https://s1.ax1x.com/2020/08/05/ar88bR.jpg" width="260" height="513"/>|<img src="https://s1.ax1x.com/2020/08/05/arG6OJ.jpg" width="260" height="513"/>|<img src="https://s1.ax1x.com/2020/08/05/artZyF.jpg" width="260" height="513"/>|
|<img src="https://s1.ax1x.com/2020/08/05/artlJx.jpg" width="260" height="513"/>|<img src="https://s1.ax1x.com/2020/08/05/artJyD.jpg" width="260" height="513"/>|<img src="https://s1.ax1x.com/2020/08/05/art2wj.jpg" width="260" height="513"/>|
|<img src="https://s1.ax1x.com/2020/08/05/art4f0.jpg" width="260" height="513"/>|<img src="https://s1.ax1x.com/2020/08/05/artIpV.jpg" width="260" height="513"/>|<img src="https://s1.ax1x.com/2020/08/05/artIpV.jpg" width="260" height="513"/>|

### 关于App
GitHub &nbsp;&nbsp;： [Fitness](https://github.com/Sky24n/Fitness)  
Apk &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;：[v0.0.2](https://github.com/Sky24n/Doc) (arm64-v8a)  
百度云盘：[提取码 ttbn](https://pan.baidu.com/s/1HgBaR68oJYe7nnOTJlSg0Q)  
腾讯微云：[点击下载](https://share.weiyun.com/5T2hhs8c)  
请使用微信或QQ浏览器扫码下载！  
  
![](https://upload-images.jianshu.io/upload_images/13222938-0bcbf2ba5a046d25.png)

测试帐号：有10个测试帐号供大家体验，有需要的请微博[私信](https://weibo.com/u/3743796227)作者，并附带个人Github。  

### 关于作者
GitHub : [Sky24n](https://github.com/Sky24n)  
简书 &nbsp;&nbsp;&nbsp;&nbsp;: [Sky24n](https://www.jianshu.com/u/cbf2ad25d33a)  
掘金 &nbsp;&nbsp;&nbsp;&nbsp;: [Sky24n](https://juejin.im/user/5b9e8a92e51d453df0440422)

### 意见与反馈
大家在使用中有任何问题，bug或者有需要改进但地方，可以提交[issues](https://github.com/Sky24n/Fitness/issues)反馈。  
当然也可以通过微博[私信](https://weibo.com/u/3743796227)反馈。

### 常见问题 - [更多](docs/md/common_problem.md)
#### 1.微博授权过程中可能发生闪退！
    已知问题！重新点授权即可。（设备：乐视1s）
#### 2.如何退出微博登录？
    长按帐号栏，点击确定即可，同时微博授权会被回收。 
#### 3.部分页面没有返回键，如何返回上一个页面？
    可以使用侧滑（右滑）返回，也可以使用手机Back键返回。
#### 4.探索页面没有回退按钮，如何返回上一个页面？
    长按探索Tab即可。 

