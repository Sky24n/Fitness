Language: English | [中文简体](https://github.com/Sky24n/Fitness)

## Fitness (Person Repos)
A Weibo client application developed with Flutter, which supports both Android and iOS.Similar to the official Weibo x9.99% experience, offline mode, multi-language support, themes can be changed at will, the fluency is beyond imagination, all kinds of surprise details are waiting for you to discover.

### Supported Features：
View Weibo News, Content, Comments  
View Hot Topics, Weibo, Hot Search  
Support Topics, @, Emoticons, Full Text  
Offline mode  
International  
Theme Color

### Share Content

#### 1、[NineGridView](https://github.com/flutterchina/nine_grid_view)
Similar to Weibo news, WeChat circle of friends, WeChat group, DingDing group, support single big picture preview.
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

#### 2、[DragSortView](https://github.com/flutterchina/nine_grid_view)
Similar to the Weibo / WeChat publish dynamic NineGridView, it supports pressing the zoom effect, dragging and sorting, and dragging to the specified location to delete.
```yaml
DragSortView(
  imageList,
  space: 5,
  margin: EdgeInsets.all(20),
  padding: EdgeInsets.all(0),
  itemBuilder: (BuildContext context, int index) {},
  initBuilder: (BuildContext context) {},
  onDragListener: (MotionEvent event, double itemWidth) {
    /// Judge to drag to the specified position to delete
    /// return true;
    if (event.globalY > 600) {
      return true;
    }
    return false;
  },
);   
```

#### 3、Get image size [ImageUtil](https://github.com/Sky24n/flustars)
Large picture function tool class.
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

#### 4、Simple encryption and decryption [EncryptUtil](https://github.com/Sky24n/common_utils)
XOR + Base64
```yaml
const String key = '11, 22, 33, 44, 55, 66';
String value = 'Sky24n';
String encode = EncryptUtil.xorBase64Encode(value, key); // WH1YHgMs
String decode = EncryptUtil.xorBase64Decode(encode, key); // Sky24n
```
#### 5、JsonUtil [JsonUtil](https://github.com/Sky24n/common_utils)
Simply encapsulate json string to object.
```yaml
String objStr = "{\"name\":\"成都市\"}";
City hisCity = JsonUtil.getObj(objStr, (v) => City.fromJson(v));

String listStr = "[{\"name\":\"成都市\"}, {\"name\":\"北京市\"}]";
List<City> cityList = JsonUtil.getObjList(listStr, (v) => City.fromJson(v));
```

#### 6、Date format [DateUtil](https://github.com/Sky24n/common_utils)
Format timestamp.
```yaml
/// year -> yyyy/yy   month -> MM/M    day -> dd/d
/// hour -> HH/H      minute -> mm/m   second -> ss/s

DateUtil.formatDateMs(DateTime.now().millisecondsSinceEpoch, format: DataFormats.full); // 2019-07-09 16:51:14
DateUtil.formatDateStr("2019-07-09 16:51:14", format: "yyyy/M/d HH:mm:ss"); // 2019/7/9 16:51:14
DateUtil.formatDate(DateTime.now(), format: "yyyy/MM/dd HH:mm:ss");  // 2019/07/09 16:51:14
DateUtil.formatDateMs(ms, format: "yyyy年MM月dd日 HH时mm分ss秒");  // 2019年07月09日 16时51分14秒
```
#### 7、Timeline [TimelineUtil](https://github.com/Sky24n/common_utils)
Similar to WeChat Moments, Weibo dynamic timeline.
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
  Full,
}

TimelineUtil.format(timeMillis, locale: Localizations.localeOf(context).languageCode, dayFormat: DayFormat.Common);
```

### Screenshots

|Home|Discover|Me|
|:---:|:---:|:---:|
|<img src="https://s1.ax1x.com/2020/08/05/ar01fA.jpg" width="220" height="465"/>|<img src="https://s1.ax1x.com/2020/08/05/ar0Zy6.jpg" width="220" height="465"/>|<img src="https://s1.ax1x.com/2020/08/05/ar0neO.png" width="220" height="465"/>|
|Weibo publish|Weibo content|User Page|
|<img src="https://s1.ax1x.com/2020/08/05/ar0rpn.gif" width="220" height="391"/>|<img src="https://s1.ax1x.com/2020/08/05/ar0fk4.gif" width="220" height="391"/>|<img src="https://s1.ax1x.com/2020/08/05/ar07X6.gif" width="220" height="391"/>|
|Auth|Setting|Photo|
|<img src="https://s1.ax1x.com/2020/08/05/arBiB8.jpg" width="220" height="465"/>|<img src="https://s1.ax1x.com/2020/08/05/arB8N4.png" width="220" height="465"/>|<img src="https://s1.ax1x.com/2020/08/05/arBQBT.jpg" width="220" height="465"/>|
|<img src="https://s1.ax1x.com/2020/08/05/ar88bR.jpg" width="260" height="513"/>|<img src="https://s1.ax1x.com/2020/08/05/arG6OJ.jpg" width="260" height="513"/>|<img src="https://s1.ax1x.com/2020/08/05/artZyF.jpg" width="260" height="513"/>|
|<img src="https://s1.ax1x.com/2020/08/05/artlJx.jpg" width="260" height="513"/>|<img src="https://s1.ax1x.com/2020/08/05/artJyD.jpg" width="260" height="513"/>|<img src="https://s1.ax1x.com/2020/08/05/art2wj.jpg" width="260" height="513"/>|
|<img src="https://s1.ax1x.com/2020/08/05/art4f0.jpg" width="260" height="513"/>|<img src="https://s1.ax1x.com/2020/08/05/artIpV.jpg" width="260" height="513"/>|<img src="https://s1.ax1x.com/2020/08/05/artIpV.jpg" width="260" height="513"/>|

### About App
GitHub &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;： [Fitness](https://github.com/Sky24n/Fitness)  
Apk &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;：[v0.0.1](https://github.com/Sky24n/Doc/blob/master/apks/fitness.apk) (arm64-v8a)  
Baidu Pan ：[code ttbn](https://pan.baidu.com/s/1HgBaR68oJYe7nnOTJlSg0Q)  
Others &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;：[v0.0.1](https://github.com/Sky24n/Doc)

### About Author
GitHub&nbsp;&nbsp;&nbsp;&nbsp;: [Sky24n](https://github.com/Sky24n)  
JianShu&nbsp;&nbsp;: [Sky24n](https://www.jianshu.com/u/cbf2ad25d33a)  
JueJin&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;: [Sky24n](https://juejin.im/user/5b9e8a92e51d453df0440422)