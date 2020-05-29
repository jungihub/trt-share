# 基于jquery实现分享到新浪微博、qq空间、豆瓣、微信功能

## 直接引入css,js
```$xslt
<link href="share.css">
<script src="share.js"></script>
```

## HTML代码
```$xslt
<div class="bdsharebuttonbox size30">
    <a class="bds_tsina" data-cmd="tsina" title="分享到新浪微博"></a>
    <a class="bds_weixin" data-cmd="weixin" title="分享到微信"></a>
    <a class="bds_qzone" data-cmd="qzone" title="分享到QQ空间"></a>
    <a class="bds_douban" data-cmd="douban" title="分享到豆瓣"></a>
</div>
```

## 使用
```$xslt
//可不设置options
$.trt_share(options)

```

## options参数说明
参数 | 说明 | 类型 | 可选值 | 默认值
---- | ---- | ---- | ----- | ----
id | 需要绑定分享框元素，样式是根据bdsharebuttonbox设置 | string | ----- | .bdsharebuttonbox
types | 分享类型参数，默认只有新浪微博(参数：tsina)、微信（参数：weixin）、qq空间(参数：qzone)、豆瓣(参数：douban) | object | ----- | ----
cmd_attr | 分享类型按钮属性，需要根据cmd_attr值获取标签上的types中的类型 | string | ----- | ----
size | 图标大小 | number | 16/24/30 | 24

### options参数types说明

```$xslt
types: {
    tsina: {
        url: 'http://service.weibo.com/share/share.php'
    },
    weixin: '',
    qzone: {
        url: 'https://sns.qzone.qq.com/cgi-bin/qzshare/cgi_qzshare_onekey'
    },
    douban: {
        url: 'https://www.douban.com/share/service?sharesource=weibo'
    }
}
```

参数 | 说明 | 可选值 | 默认值
----- | ----- | ----- | -----
url | 各类网站分享地址 | ----- | -----
title | 分享到网站设置标题字段，用于拼接分享链接，如：http://service.weibo.com/share/share.php?title=标题 | ---- | title
tempURLKey | 分享到网站设置网站链接，用于凭借分享链接，如：http://service.weibo.com/share/share.php?url=链接 | ---- | url
args | 如需在分享链接上新增参数args对象，如：{name:'author'}，链接http://service.weibo.com/share/share.php?name=author | ---- | ----

## 新增分享链接
##### 样式值包含新浪、微信、qq空间、豆瓣，如需增加需自己增加样式

```$xslt
<body>
<div class="bdsharebuttonbox size30">
    <a class="bds_tsina" data-cmd="tsina" title="分享到新浪微博"></a>
    <a class="bds_weixin" data-cmd="weixin" title="分享到微信"></a>
    <a class="bds_qzone" data-cmd="qzone" title="分享到QQ空间"></a>
    <a class="bds_douban" data-cmd="douban" title="分享到豆瓣"></a>
    //新增分享到人人网
    <a class="bds_renren" data-cmd="renren" title="分享到豆瓣"></a>
</div>
</body>
<script>
$.trt_share({
    types: {
        renren: {
            url: 'http://widget.renren.com/dialog/share',
            tempURLKey: 'resourceUrl'
        }
    }
})
</script>
```
