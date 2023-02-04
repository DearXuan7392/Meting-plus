<h1 align="center">
Meting-plus
</h1>

## 仓库说明

本仓库是我对[metingjs](https://github.com/metowolf/MetingJS)的修改版,用于在[volantis](https://volantis.js.org/)主题中实现加载本地音乐功能.除此之外其他功能不变,可以方便地由``metingjs``快速转到``meting-plus``

## 如何使用

只需要在原``meting-js``标签中添加``audio``属性,即可加载本地音乐.如果没有该属性,则使用原``meting-js``方法

将歌曲以数组的方式储存,如下所示

```js
const MyList = [{
        "name": "Flower Dance",
        "artist": "Oturans - DJ Okawari",
        "title": "Flower Dance",
        "url": "music/Flower Dance.mp3",
        "lrc": "music/all.lrc",
        "cover": "music/Flower Dance.jpg"
    }, {
        "name": "夜的钢琴曲",
        "artist": "K. Williams",
        "title": "夜的钢琴曲",
        "url": "music/夜的钢琴曲.mp3",
        "lrc": "music/all.lrc",
        "cover": "music/夜的钢琴曲.jpg"
    }]
```

### 从``js``加载(推荐)

创建如下标签

```html
<meting-js audio="MyList">
</meting-js>
```

则``meting-plus``会通过``eval``的方式执行``MyList``,返回值作为歌曲列表传入``Aplayer``

### 从标签属性加载

将歌曲列表转化为字符串,并使用``URI``编码

```js
const MyListStr = encodeURI(JSON.stringify(MyList))
```

此时``MyListStr``的值为

> %5B%7B%22name%22:%22Flower%20Dance%22,%22artist%22:%22Oturans%20-%20DJ%20Okawari%22,%22title%22:%22Flower%20Dance%22,%22url%22:%22music/Flower%20Dance.mp3%22,%22lrc%22:%22music/all.lrc%22,%22cover%22:%22music/Flower%20Dance.jpg%22%7D,%7B%22name%22:%22%E5%A4%9C%E7%9A%84%E9%92%A2%E7%90%B4%E6%9B%B2%22,%22artist%22:%22K.%20Williams%22,%22title%22:%22%E5%A4%9C%E7%9A%84%E9%92%A2%E7%90%B4%E6%9B%B2%22,%22url%22:%22music/%E5%A4%9C%E7%9A%84%E9%92%A2%E7%90%B4%E6%9B%B2.mp3%22,%22lrc%22:%22music/all.lrc%22,%22cover%22:%22music/%E5%A4%9C%E7%9A%84%E9%92%A2%E7%90%B4%E6%9B%B2.jpg%22%7D%5D

将该值作为``meting-js``标签的``audio``属性写入

```html
<meting-js audio="%5B%7B%22name%22:%22Flower%20Dance%22,%22artist%22:%22Oturans%20-%20DJ%20Okawari%22,%22title%22:%22Flower%20Dance%22,%22url%22:%22music/Flower%20Dance.mp3%22,%22lrc%22:%22music/all.lrc%22,%22cover%22:%22music/Flower%20Dance.jpg%22%7D,%7B%22name%22:%22%E5%A4%9C%E7%9A%84%E9%92%A2%E7%90%B4%E6%9B%B2%22,%22artist%22:%22K.%20Williams%22,%22title%22:%22%E5%A4%9C%E7%9A%84%E9%92%A2%E7%90%B4%E6%9B%B2%22,%22url%22:%22music/%E5%A4%9C%E7%9A%84%E9%92%A2%E7%90%B4%E6%9B%B2.mp3%22,%22lrc%22:%22music/all.lrc%22,%22cover%22:%22music/%E5%A4%9C%E7%9A%84%E9%92%A2%E7%90%B4%E6%9B%B2.jpg%22%7D%5D">
</meting-js>
```

## 完整代码

```html
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>Meting-plus</title>
    <script defer src="APlayer.min.js"></script>
    <link type="text/css" rel="stylesheet" href="APlayer.min.css" />
    <script defer src="source/Meting-plus.js"></script>
</head>
<body>
<meting-js audio="MyList">
</meting-js>
</body>
</html>
<script>
    const MyList = [{
        "name": "Flower Dance",
        "artist": "Oturans - DJ Okawari",
        "title": "Flower Dance",
        "url": "music/Flower Dance.mp3",
        "lrc": "music/all.lrc",
        "cover": "music/Flower Dance.jpg"
    }, {
        "name": "夜的钢琴曲",
        "artist": "K. Williams",
        "title": "夜的钢琴曲",
        "url": "music/夜的钢琴曲.mp3",
        "lrc": "music/all.lrc",
        "cover": "music/夜的钢琴曲.jpg"
    }]
</script>
```
