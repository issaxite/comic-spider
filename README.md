# ic-comic-spider
a script to get the comic from xxx

## 安装
```
npm i -g ic-comic-spider
```

## 快速使用
- 登录 [http://www.verydm.com](http://www.verydm.com) 找需要的漫画，复制目录页链接，例如《亚人》的目录：http://www.verydm.com/manhua/yaren

1. 使用脚本搜索漫画：

```
icsdr --search xxx
```
比如：
```
icsdr --search 火影
✔ search result: 10
火影忍者: http://www.verydm.com/manhua/huoyingrenzhe
博人传-火影次世代: http://www.chuixue.net/manhua/30841
火影同人-我的第一次: http://www.chuixue.net/manhua/27308
火影忍者外传: http://www.chuixue.net/manhua/23713
火影同人 An Important Day: http://www.chuixue.net/manhua/26541
火影忍者特典: http://www.chuixue.net/manhua/24324
火影同人四格: http://www.chuixue.net/manhua/23205
火影忍者-者之书: http://www.chuixue.net/manhua/8579
火影同人短篇: http://www.chuixue.net/manhua/12739
火影忍者: http://comic.kukudm.com/comiclist/3/
```

2. 登陆相关网站搜索资源，并复制目录url。当前支持的资源站点如下：
```
  吹雪漫画：http://www.chuixue.net

  非常爱漫：http://www.verydm.com/

  kuku漫画：http://comic.kukudm.com/
```


- 下载漫画
```
icsdr http://www.verydm.com/manhua/yaren
```
可下载多个，空格分隔

## 主要功能
- 下载漫画；
- 自定义分卷；
- 搜索漫画；

## 更多下载选项
```
Usage: icsdr [options]

Options:

-V, --version                output the version number

# 初始化配置 或 读取配置执行脚本
--config [filePath]          config file path

// 在当前目录初始化配置
icsdr --config

// 当前目录存在配置文件则读取，否则初始化配置
icsdr

// 若存在配置文件则读取配置，否则初始化配置
icsdr --config ../

// 初始化配置
icsdr --config

# 设置漫画保存目录（不可单独使用）
--out [filePath]             file path of save dir

// exp
icsdr --catalogs http://www.verydm.com/manhua/kuangduzhiyuan --out ../

# 设置下载漫画的目录链接，可多个，半角逗号分割
--catalogs [url]             catalog url list

// 下载单个
icsdr --catalogs http://www.verydm.com/manhua/kuangduzhiyuan
// or
icsdr http://www.verydm.com/manhua/kuangduzhiyuan

// 下载多个
icsdr --catalogs http://www.verydm.com/manhua/kuangduzhiyuan,http://www.verydm.com/manhua/kuangduzhiyuan
// or
icsdr http://www.verydm.com/manhua/kuangduzhiyuan http://www.verydm.com/manhua/kuangduzhiyuan

# 搜索漫画
--search [string]            search comic keyword

// exp
icsdr --search 一拳超人

# 设置下载漫画的范围，可以简写章节名，但必须是目录上章节名的简称

// 设置下载的起始章节，不设置结束章节则直至结束
--start [string]             name of start-chapter

// 设置结束章节，不设置起始章节则从头开始下载
--end [string]               name of end-chapter

// 以半角逗号分割起始章节和结束章节
--range [string]             Separated by commas, such as 10,20

// 指定某一章节下载
--chapter [string]           download designated chapter

// exp
icsdr http://www.verydm.com/manhua/kuangduzhiyuan --start 19

icsdr http://www.verydm.com/manhua/kuangduzhiyuan --end 第28

icsdr http://www.verydm.com/manhua/kuangduzhiyuan --start 19 --end 28话

icsdr http://www.verydm.com/manhua/kuangduzhiyuan --range 19,28

icsdr http://www.verydm.com/manhua/kuangduzhiyuan --range 19

icsdr http://www.verydm.com/manhua/kuangduzhiyuan --range ,28

icsdr http://www.verydm.com/manhua/kuangduzhiyuan --chapter 28

# 合并分卷

// 指定分卷大小
--volsize [number | string]  volume number(chapter or picture), such as 200(p) or 20c

// 指定需要合并的漫画
--merge [filepath]           comic dir path

// 默认基于图片数量合并分卷，并不会严格按章200张合并，同时会弱依赖于章节
icsdr --merge ./comic/一拳超人 --volsize 200

icsdr --merge ./comic/一拳超人 --volsize 200p

// 基于章节数合并
icsdr --merge ./comic/一拳超人 --volsize 200c


# 分页切割

// 居中分割横向长图（主要应用于单行本漫画的双页图片）
--crop [filepath]            picture filepath, chapter dir or comic dir

// 默认分割后的两张图的命名顺序从右到左，将该属性设置为true则交换顺序
--swap [boolean]             is need to swap crop order

// 分割整本漫画
icsdr --crop ./comic/一拳超人 --out ./comic

// 分割单独章节
icsdr --crop ./comic/一拳超人/第16话/ --out ./comic

// 分割指定图片
icsdr --crop ./comic/一拳超人/第16话/008.jpg --out ./comic

// 交换分割图片的顺序
// [left | right]
// 默认：1.jpg(right) 2.jpg(left)
// swap: 1.jpg(left) 2.jpg(right)
icsdr --crop ./comic/一拳超人/第16话/008.jpg --out ./comic --swap true

-h, --help                   output usage information
```
以上命令大多可以自由组合使用，若发现必要的组合不生效可异步 [issue] 提出你的bug与需求!

## License

MIT

[issue]: https://github.com/issaxite/ic-comic-spider/issues
