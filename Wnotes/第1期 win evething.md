
# 第1期 win:`Evething`

>  官网：[evething](https://www.voidtools.com/zh-cn/)
>
>  下载地址：[Everything 1.4.1.1017便携版 64 位](https://www.voidtools.com/Everything-1.4.1.1017.x64.zip)

"Everything" 是 Windows 上一款搜索引擎，它能够基于文件名快速定文件和文件夹位置。

[TOC]


## 1.使用教程

- 如何`快速`搜索电脑上某一个文件(搜索语法见4)
  - 在`特定文件夹`里搜索
    - 名称`folder:hello`快速搜索名字带hello的文件夹
    - 时间`folder:<dm:today>` 快速搜索今日`修改`的文件夹
  - 搜索硬盘里`特定文件`
    - 名称`d: *.mp4` 搜索分区 D:上 mp4 文件
    - 大小`size:>1mb` 搜索大于1MB文件
    - 时间`file:<dm:today>` 快速搜索今日`修改`的文件
    - 格式（.zip等）`file:毕业*.zip` 查找wi开头的zip文件
  
- 如何局域网快速传输文件（见HTTP服务7）
  - 连接wifi，手机快速访问电脑文件
    
    - 电脑访问手机文件可以使用APP-`ES文件管理`
    
  - 两台电脑快速传输文件（大型文件可以使用网线构建局域网，传输更快）
  
    - 插上网线利用PING命令测试两台电脑是否连通
      - 在终端输入 ping `*.*.*.*` (同样在第二台电脑上ping `*.*.*.*`)
      - 不通的话设置自动获得IP
    - 接收文件电脑，win+R运行`\\*.*.*.*`
  
    连接不通时候：
    
    - 电脑（文件储存的）：
      - gpedit.msc（guest账户激活）
      - 计算机配置-管理模板-网络-lanman工作站-启用不安全的来宾登录
      - 共享-添加一个everyone用户-共享
      - 网络和共享中心-更改高级共享设置-所有网络-无密码保护的共享
    - 电脑（取文件）：gpedit.msc（guest账户激活）【上一步设置完，不行的话，也启用不安全的来宾登录】
      - guest账户激活（账户：guest 密码：空）
    
  
- 如何快速重命名文件或者文件夹

  - 工具-选项-常规-集成到资源管理器右键菜单
  - 按shift键，选中需要修改的文件或文件夹
  - 正则表达式（见 5）来进行修改

- 如何搜索文件内容(搜索语法见4)
  
  - 调用函数content:<text>（`*.eml dm:thisweek content:skills`搜索邮件、修改于此周且包含有关键词 "skills"：）
  
- 如何查找重复文件(搜索语法见4)
  
  - 调用函数`depe:`,`sizedupe:`（`dupe: .mp4 size:>1gb sizedupe:` 搜索大于1GB的mp4重复文件）
  
- 如何清理空文件夹(搜索语法见4)
  - 调用函数`empty：`（`"E:\abc\"  empty: `-E盘abc文件夹里空文件夹）
  - ctrl+a 全选删除
  
- 添加经常使用文件，管理书签

## 2.同类对比

- win自带搜索——索引时间长，搜索没有系统的语法（可以开启索引）

  - 设置-搜索-搜索windows
  - 查找我的文件-增强
  - 高级搜索索引器设置-修改常用磁盘

- listary——付费软件，软件没evething精简，但是其他功能，快速启动应用、搜索引擎和网站倒是很方便

- AnyTXT Searcher——文本内容搜索最完整，eve作者都推荐过，但是启动时间过长，占用CPU。

- Quick Search——类似evething但是不够流畅，界面不灵活

- UltraSearch、FileSearchEX等全面性不如evething

总之evething是我最喜欢的文件搜索工具，功能齐全，占用内存少，是我每更换系统必装软件

## 3.常用搜索实例

> everything搜索文件名超快，但是基于其他的条件未知，搜索条件可能是
> `从左到右`，所以尽量先添加一些限定条件把文件限制的一定的范围，比如文件格式”.txt”等
>
> 常用`修饰符`和`函数`已进行`标注`

- `123 abc` 搜索包含123和abc的文件和文件夹
- `123|abc` 搜索包含123或abc的文件和文件夹
- `!abc` 搜索除了 abc的其他文件
- `!. `搜索无扩展名的文件或文件夹：
- `case:ABC` 搜索大写 ABC
- `d: *.mp4` 搜索分区 D:上 mp4 文件：
- `*.txt|*.doc` 搜索txt或doc后缀文件
- `a*.b`,搜索所有以a开头，以.b结尾的文件。
- `?.c`,搜索出名字只有一个字符，以.c结尾的文件。
- `*.eml dm:thisweek content:keyboard`搜索邮件、修改于此周且包含有关键词 "keyboard"：
  -  注意：content: 使用在搜索最后，Everything 则只有搜索匹配 `*.eml dm:thisweek` 的文件内容。
- `dupe: .mp4 size:>1gb sizedupe:` 搜索大于1GB的mp4重复文件
- `file:` 仅搜索文件：
- ` folder: `仅搜索文件夹：
- `parent:c:\windows` 限定搜索单个文件夹：
- `c:\windows` 搜索包含子文件夹内文件
  - 带空格的记得使用转义符""
- `size:>1mb` 搜索大于1MB文件
- `dm:today` 快速搜索今日`修改`的文件和文件夹：
- `dc:thisweek` 搜索这周`创建`的文件和文件夹：
- `dc:1/8/2014-31/8/2014 or: dc:8/1/2014-8/31/2014` 搜索创建于2014 年 8 月 1 日到 2014 年 8 月 31 日的文件和文件夹: (日期格式取决于本地设置)
- `d:\music\ !child:mp3` 搜索 D:\music 下不包含 mp3 的文件夹：
- `\work order` 使用空格以组合搜索条件，例如，在以 work 开头文件夹下搜索包含 order 的文件和文件夹：
- `*.txt size:large`1MB-16 MB的txt文件
- `*.txt len:5-10` 文件名长5至10的txt文件
- `*.txt attrib:a` 所有存档属性的txt文件
- `*.txt dc:last year` 去年创建的txt文件
- `*.txt dm:2020-2021`2020-2021修改的
- `*.txt file:size:0 ` 搜索空txt文件 
- `<*.bmp|*.jpg|*.png|*.tga> size:>1mb` 搜索所有大于1MB的常见图像文件
- `file:<wi*.h|wi*.cpp> 或wi* <ext:h|cpp> ` 查找wi开头的h文件和cpp文件
- `regex:^[^0-9a-z]*$ ` 搜索所有纯中文目标
- `regex:^.*[^!-~]+.*$`  搜索带中文字符的目标

## 4.搜索语法

#### 操作符: 
|    符号     |       解释       |      列子       |              解释              |
| :---------: | :--------------: | :-------------: | :----------------------------: |
| space(空格) |     与 (AND)     |     123 abc     | 搜索包含123和abc的文件和文件夹 |
|     \|      |     或 (OR)      |    123\|abc     | 搜索包含123或abc的文件和文件夹 |
|      !      |     非 (NOT)     |      !abc       |  搜索不包含abc的文件和文件夹   |
|     < >     | 分组(提高优先级) | file:<123\|abc> | 搜索包含123或abc的文件和文件夹 |
|     " "     | 搜索引号内的词组 |    "my abc"     |       特殊字符串如“空格”       |

#### 通配符:

| 符号 |        解释         | 列子 |                  解释                  |
| :--: | :-----------------: | :--: | :------------------------------------: |
|  *   | 匹配 0 个或多个字符 |  a*  |         以a开头的文件和文件夹          |
|  ?   |    匹配 1 个字符    | ?.c  | 搜索出名字只有一个字符，以.c结尾的文件 |

#### 修饰符: 

|       符号       |            解释            |         列子         |                 解释                  |
| :--------------: | :------------------------: | :------------------: | :-----------------------------------: |
|      ascii:      | 启用快速 ASCII 大小写对比. |                      |                                       |
|     `case:`      |        区分大小写.         |       case:ABC       |             搜索大写 ABC              |
|     `file:`      |        仅匹配文件.         |       file:abc       |             仅搜索文件abc             |
|    `folder:`     |       仅匹配文件夹.        |      folder:abc      |            仅搜索文件夹abc            |
|     noascii:     | 禁用快速 ASCII 大小写对比. |                      |                                       |
|     nocase:      |       不区分大小写.        |                      |                                       |
|  nodiacritics:   |      不匹配变音标记.       |                      |                                       |
|   nofileonly:    |       仅不允许文件.        |                      |                                       |
|  nofolderonly:   |      仅不允许文件夹.       |                      |                                       |
|    `nopath:`     |        不匹配路径.         |      nopath:abc      | 路径不进行搜索，仅搜索abc文件夹或文件 |
|     noregex:     |      禁用正则表达式.       |                      |                                       |
|      nowfn:      |     不匹配完整文件名.      |                      |                                       |
| nowholefilename: |     不匹配完整文件名.      |                      |                                       |
|   nowholeword:   |      仅禁用全字匹配.       |                      |                                       |
|   nowildcards:   |        禁用通配符.         |                      |                                       |
|      noww:       |      仅禁用全字匹配.       |                      |                                       |
|      path:       |     匹配路径和文件名.      |                      |                                       |
|     `regex:`     |      启用正则表达式.       | `regex:^[^0-9a-z]*$` |          搜索所有纯中文目标           |
|      utf8:       | 禁用快速 ASCII 大小写对比. |                      |                                       |
|      `wfn:`      |      匹配完整文件名.       |       wfn:abc        |       仅搜索文件abc或文件夹abc        |
|  wholefilename:  |      匹配完整文件名.       |                      |                                       |
|    wholeword:    |       仅匹配全字符.        |                      |                                       |
|    wildcards:    |        启用通配符.         |                      |                                       |
|       ww:        |        仅全字匹配.         |                      |                                       |

#### 函数: 

`搜索一般从左到右`

|           符号           |                             解释                             |         例子          |               解释               |
| :----------------------: | :----------------------------------------------------------: | :-------------------: | :------------------------------: |
|       album:<text>       |                     搜索媒体专辑元数据.                      |                       |                                  |
|    ansicontent:<text>    |                   搜索 ANSI 格式文本内容.                    |                       |                                  |
|      artist:<text>       |                    搜索媒体艺术家元数据.                     |                       |                                  |
|   attrib:<attributes>    |              搜索指定的文件属性的文件和文件夹.               |                       |                                  |
|       attribdupe:        |               搜索含有相同属性的文件和文件夹.                |                       |                                  |
| attributes:<attributes>  |              搜索指定的文件属性的文件和文件夹.               |                       |                                  |
|   bitdepth:<bitdepth>    |                   搜索指定像素密度的图片.                    |                       |                                  |
|    `child:<filename>`    |               搜索包含匹配文件名文件的文件夹.                |      `!child:mp4      |     搜索不包含 mp4 的文件夹      |
|    childcount:<count>    |          搜索包含有指定数目子文件夹或文件的文件夹.           |                       |                                  |
|  childfilecount:<count>  |               搜索包含有指定数目文件的文件夹.                |                       |                                  |
|   childfoldercount:<n>   |              搜索包含有指定数目子文件的文件夹.               |                       |                                  |
|      comment:<text>      |                     搜索媒体注释元数据.                      |                       |                                  |
|     `content:<text>`     |                        搜索文本内容.                         |  `*.doc content:abc`  | 搜索包含有关键词 "abc"的doc文档  |
|       count:<max>        |                     指定搜索结果最大值.                      |                       |                                  |
|   dateaccessed:<date>    |               搜索指定访问时间的文件和文件夹.                |                       |                                  |
|    datecreated:<date>    |               搜索指定创建日期的文件和文件夹.                |                       |                                  |
|   datemodified:<date>    |               搜索指定修改日期的文件和文件夹.                |                       |                                  |
|      daterun:<date>      |               搜索指定打开时间的文件和文件夹.                |                       |                                  |
|        da:<date>         |               搜索指定访问时间的文件和文件夹.                |                       |                                  |
|         dadupe:          |             搜索含有相同访问时间的文件和文件夹.              |                       |                                  |
|       `dc:<date>`        |               搜索指定创建日期的文件和文件夹.                |      dc:thisweek      |  搜索这周`创建`的文件和文件夹：  |
|         dcdupe:          |             搜索含有相同创建时间的文件和文件夹.              |                       |                                  |
|    dimensions:<w>X<h>    |                     搜索指定长宽的图片.                      |                       |                                  |
|       `dm:<date>`        |               搜索指定修改日期的文件和文件夹.                |       dm:today        | 快速搜索今日`修改`的文件和文件夹 |
|         dmdupe:          |             搜索含有相同修改时间的文件和文件夹.              |                       |                                  |
|       `dr:<date>`        |               搜索指定打开时间的文件和文件夹.                |       dr:today        | 快速搜索今日`打开`的文件和文件夹 |
|         `dupe:`          |                      搜索重复的文件名.                       |      dupe: .mp4       |     搜索重复文件名的mp4文件      |
|         `empty:`         |                        搜索空文件夹.                         |        empty:         |           搜索空文件夹           |
|      endwith:<text>      |            搜索以指定文本结尾的文件 (包含扩展名).            |                       |                                  |
|  `ext:<ext1;ext2;...>`   |    搜索和列表中指定的扩展名匹配的文件 (扩展名以分号分隔).    |   `wi* <ext:h|cpp>`   |    查找wi开头的h文件和cpp文件    |
| filelist:<fn1\|fn2\|...> |                   搜索文件名列表中的文件.                    |                       |                                  |
| filelistfilename:<name>  |               搜索文件名列表中的文件和文件夹.                |                       |                                  |
|        frn:<frn>         |              搜索指定文件索引号的文件和文件夹.               |                       |                                  |
|       fsi:<index>        | 搜索指定盘符索引中文件或文件夹 (索引 0 表示 C 盘, 以此类推). |                       |                                  |
|       genre:<text>       |                     搜索媒体流派元数据.                      |                       |                                  |
|     height:<height>      |                   搜索指定像素高度的图片.                    |                       |                                  |
|     infolder:<path>      |        搜索指定路径下的文件和文件夹 (不包含子文件夹).        |                       |                                  |
|      `len:<length>`      |         搜索和指定的文件名长度相匹配的文件和文件夹.          |   `*.txt len:5-10`    |      文件名长5至10的txt文件      |
|      namepartdupe:       |             搜索含有相同名称部分的文件和文件夹.              |                       |                                  |
|    orientation:<type>    |               搜索指定方向的图片 (水平或竖直).               |                       |                                  |
|     `parent:<path>`      |       搜索指定路径下的文件和文件夹  (不包含子文件夹).        |   parent:c:\windows   |        限定搜索单个文件夹        |
|     parents:<count>      |            搜索有指定数目父文件夹的文件和文件夹.             |                       |                                  |
|        rc:<date>         |             搜索指定最近修改日期的文件和文件夹.              |                       |                                  |
|   recentchange:<date>    |             搜索指定最近修改日期的文件和文件夹.              |                       |                                  |
|          root:           |               搜索没有父文件夹的文件和文件夹.                |                       |                                  |
|     runcount:<count>     |               搜索指定打开次数的文件和文件夹.                |                       |                                  |
|       shell:<name>       |        搜索已知的 Shell 文件夹名称, 包括子目录和文件.        |                       |                                  |
|      `size:<size>`       |              搜索指定大小的文件 (以字节为单位).              |       size:>1mb       |         搜索大于1MB文件          |
|       `sizedupe:`        |                     搜索大小重复的文件.                      |  size:>1gb sizedupe:  |      搜索大于1GB的重复文件       |
|     startwith:<text>     |                   搜索指定文本开头的文件.                    |                       |                                  |
|       title:<text>       |                     搜索媒体标题元数据.                      |                       |                                  |
|      track:<number>      |                  搜索指定音轨号的媒体文件.                   |                       |                                  |
|       type:<type>        |              搜索指定的文件类型的文件和文件夹.               |                       |                                  |
|   utf16content:<text>    |                  搜索 UTF-16 格式文本内容.                   |                       |                                  |
|  utf16becontent:<text>   |                 搜索 UTF-16 BE 格式文本内容.                 |                       |                                  |
|   `utf8content:<text>`   |                   搜索 UTF-8 格式文本内容.                   | *.doc utf8content:abc |              UTF-8               |
|      width:<width>       |                   搜索指定像素宽度的图片.                    |                       |                                  |



#### 函数语法: 

|        符号         |           解释            |
| :-----------------: | :-----------------------: |
|   function:value    |       等于某设定值.       |
|  function:<=value   |     小于等于某设定值.     |
|   function:<value   |       小于某设定值.       |
|   function:=value   |       等于某设定值.       |
|   function:>value   |       大于某设定值.       |
|  function:>=value   |     大于等于某设定值.     |
| function:start..end | 在起始值和终止值的范围内. |
| function:start-end  | 在起始值和终止值的范围内. |



#### 大小语法: 

```size[kb|mb|gb]```

#### 大小常数: 

|   符号   |          解释          |
| :------: | :--------------------: |
|  empty   |                        |
|   tiny   |  0 KB < 大小 <= 10 KB  |
|  small   | 10 KB < 大小 <= 100 KB |
|  medium  | 100 KB < 大小 <= 1 MB  |
|  large   |  1 MB < 大小 <= 16 MB  |
|   huge   | 16 MB < 大小 <= 128 MB |
| gigantic |     大小 > 128 MB      |
| unknown  |                        |

#### 日期语法: 

```
    year
	month/year 或者 year/month 取决于本地设置
	day/month/year, month/day/year 或者 year/month/day 取决于本地设置
	YYYY[-MM[-DD[Thh[:mm[:ss[.sss]]]]]]
	YYYYMM[DD[Thh[mm[ss[.sss]]]]]
```

#### 日期常数: 

| today                                                        |
| ------------------------------------------------------------ |
| yesterday                                                    |
| tomorrow                                                     |
| <last\|past\|prev\|current\|this\|coming\|next><year\|month\|week> |
| <last\|past\|prev\|coming\|next><x><years\|months\|weeks\|days\|hours\|minutes\|mins\|seconds\|secs> |
| january\|february\|march\|april\|may\|june\|july\|august\|september\|october\|november\|december |
| jan\|feb\|mar\|apr\|may\|jun\|jul\|aug\|sep\|oct\|nov\|dec   |
| sunday\|monday\|tuesday\|wednesday\|thursday\|friday\|saturday |
| sun\|mon\|tue\|wed\|thu\|fri\|sat                            |
| unknown                                                      |

#### 宏: 

```
	符号		解释				
	quot:	双引号 (")
	apos:	单引号 (')
	amp:	与号 (&)
	lt:	小于 (<)
	gt:	大于 (>)
	#<n>:	十进制 Unicode 字符 <n>.
	#x<n>:	十六进制 Unicode 字符 <n>.
	audio:	搜索音频文件.
	zip:	搜索压缩文件.
	doc:	搜索文档文件.
	exe:	搜索可执行文件.
	pic:	搜索图片文件.
	video:	搜索视频文件.
```

#### 属性常数: 

```
	A	存档
	C	压缩
	D	目录
	E	加密
	H	隐藏
	I	未索引的内容
	L	重解析点
	N	一般
	O	离线
	P	稀疏文件
	R	只读
	S	系统
	T	临时
	V	设备
```

## 5.正则表达式语法: 

| 符号  |                             解释                             |      例子      |                             解释                             |
| :---: | :----------------------------------------------------------: | :------------: | :----------------------------------------------------------: |
|  \|   |                            逻辑或                            |   gray\|grey   |                         gray或者grey                         |
|   \   | 转义字符,用于匹配一些保留的字符 [ ] ( ) { } . * + ? ^ $ \ \| |     at\.?      |                           匹配at.                            |
|  ()   |                          提升优先级                          |   gr(a\|e)y    |                       等价于gray\|grey                       |
|   ?   |                      匹配0或1个指定字符                      |    colou?r     |                    匹配”color”  “colour”                     |
|   *   |                   匹配前一项内容  0 或多次                   |     c(ab)*     |                    匹配”c”  “cab” “cabab”                    |
|   +   |                   匹配前一项内容  1 或多次                   |      ab+c      |                  匹配”abc”  “abbc” “abbbc”                   |
|   .   |                       匹配任意单个字符                       |      a.c       |                       匹配”abc”  “aac”                       |
|  []   |                     字符集,匹配单个字符                      | [a.c]  、[a-z] |                  匹配”a”  “.” “c”、匹配a到z                  |
|  [^]  |                  匹配指定集合之外的单个字符                  |     [^a-z]     |                    匹配所有不是a到z的字符                    |
|   ^   |                       匹配字符串的开始                       |      ^abc      |                       开头为abc的字串                        |
|   $   |                       匹配字符串的结尾                       |      abc$      |                       结尾为abc的字串                        |
| {m,n} |                  匹配字符个数最小值和最大值                  |     a{3,5}     |                  匹配”aaa”  “aaaa” “aaaaa”                   |
|  \b   |        匹配一个单词边界，也就是指单词和空格间的位置。        |      er\b      |     可以匹配“never”中的“er”，但不能匹配“verb”中的“er”。      |
|  \B   |                       匹配非单词边界。                       |      er\B      |        匹配“verb”中的“er”，但不能匹配“never”中的“er”         |
|  \cx  |                   匹配由x指明的控制字符。                    |      \cM       | 匹配一个Control-M或回车符。x的值必须为A-Z或a-z之一。否则，将c视为一个原义的“c”字符。 |
|  \d   |                      匹配一个数字字符。                      |                |                         等价于[0-9]                          |
|  \D   |                     匹配一个非数字字符。                     |                |                          等价于0-9                           |
|  \f   |                       匹配一个换页符。                       |                |                       等价于\x0c和\cL                        |
|  \n   |                       匹配一个换行符。                       |                |                       等价于\x0a和\cJ                        |
|  \r   |                       匹配一个回车符。                       |                |                       等价于\x0d和\cM                        |
|  \s   |       匹配任何空白字符，包括空格、制表符、换页符等等。       |                |                     等价于[  \f\n\r\t\v]                     |
|  \S   |                     匹配任何非空白字符。                     |                |                      等价于 \f\n\r\t\v                       |
|  \t   |                       匹配一个制表符。                       |                |                       等价于\x09和\cI                        |
|  \v   |                     匹配一个垂直制表符。                     |                |                       等价于\x0b和\cK                        |
|  \w   |                匹配包括下划线的任何单词字符。                |                |                                                              |
|  \W   |                     匹配任何非单词字符。                     |                |                      等价于“A-Za-z0-9_”                      |
| \num  |     匹配num，其中num是一个正整数。对所获取的匹配的引用。     |    “(.)\1”     |                   匹配两个连续的相同字符。                   |
|  ?=   |                        前置约束-存在                         |                |                                                              |
|  ?!   |                        前置约束-排除                         |                |                                                              |
|  ?<=  |                        后置约束-存在                         |                |                                                              |
|  ?<!  |                        后置约束-排除                         |                |                                                              |
|   i   |                         忽略大小写.                          |    /The/gi     |                                                              |
|   g   |                          全局搜索.                           |    /.(at)/g    |                                                              |
|   m   |       多行的: 锚点元字符 `^` `$` 工作范围在每行的起始.       |  /.at(.)?$/gm  |                                                              |



其他正则表达式

```
正整数: ^\d+$
负整数: ^-\d+$
手机国家号: ^+?[\d\s]{3,}$
手机号: ^+?[\d\s]+(?[\d\s]{10,}$
整数: ^-?\d+$
用户名: ^[\w\d_.]{4,16}$
数字和英文字母: ^[a-zA-Z0-9]*$
数字和应为字母和空格: ^[a-zA-Z0-9 ]*$
密码: ^(?=^.{6,}$)((?=.*[A-Za-z0-9])(?=.*[A-Z])(?=.*[a-z]))^.*$
邮箱: ^([a-zA-Z0-9._%-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4})*$
IP4 地址: ^((?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?))*$
纯小写字母: ^([a-z])*$
纯大写字母: ^([A-Z])*$
URL: ^(((http|https|ftp):\/\/)?([[a-zA-Z0-9]\-\.])+(\.)([[a-zA-Z0-9]]){2,4}([[a-zA-Z0-9]\/+=%&_\.~?\-]*))*$
VISA 信用卡号: ^(4[0-9]{12}(?:[0-9]{3})?)*$
日期 (MM/DD/YYYY): ^(0?[1-9]|1[012])[- /.](0?[1-9]|[12][0-9]|3[01])[- /.](19|20)?[0-9]{2}$
日期 (YYYY/MM/DD): ^(19|20)?[0-9]{2}[- /.](0?[1-9]|1[012])[- /.](0?[1-9]|[12][0-9]|3[01])$
MasterCard 信用卡号: ^(5[1-5][0-9]{14})*$
```



## 6.快捷键

> 快捷键可以自定义，不过才常用的快捷键默认如下

```
F2 重命名
F11 全屏
Ctrl+N 新建搜索窗口（N）
Ctrl+O 打开文件列表
Ctrl+Enter 打开路径
Ctrl+Shift+C 复制完整路径和文件名
Alt+Enter 属性
Alt+P 预览
Enter 打开
Ctrl+W或Esc 关闭
Ctrl+S 导出
Ctrl+Q 退出
Ctrl+A 全选
Ctrl+l 区分大小写
Ctrl+B 全字匹配
Ctrl+U 匹配路径
Ctrl+M 匹配变音标记
Ctrl+R 使用正则表达式
Ctrl + = 增加字体大小。
Ctrl + - 减小字体大小。
Ctrl + 0 重置字体大小。
Ctrl+Shift+1 超大图标（X）
Ctrl+Shift+2 大图标（L）
Ctrl+Shift+3 中等图标（M）
Ctrl+Shift+6 详情
Ctrl+Shift+F 管理筛选器
Ctrl+Shift+B 管理书签
Ctrl+D 添加书签
```



## 7.HTTP服务

- 工具-选项-HTTP 服务器
- - [x] 启用HTTP服务器
  - [x] 允许HTTP文件下载
- win+R启动cmd
- 使用命令`ipconfig`查看IP地址
- 局域网打开`*.*.*.*`即可下载浏览文件

