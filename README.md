# Telegram 文本格式和解析模式（Markdown、HTML）
![](https://cdn.icon-icons.com/icons2/2699/PNG/512/telegram_logo_icon_168691.png)

![](https://img.shields.io/github/stars/pandao/editor.md.svg) ![](https://img.shields.io/github/forks/pandao/editor.md.svg) ![](https://img.shields.io/github/tag/pandao/editor.md.svg) 

## 目录
Telegram 文本格式和解析模式（Markdown、HTML）
-  前言
  - 文本消息的格式
  - 解析模式
- Markdown
  - 语法示例 v1.0（2018-2020版本）
  - 语法示例 v2.0（2020-2023版本）
- HTML
  - 语法示例 v1.0（2018-2020版本）
  - 语法示例 v2.0（2020-2023版本）
- 内置链接
  - 语法示例
  - 注解

<br>
<br>

## 前言

Telegram 支持信息的基本格式。您可以在机器人信息中使用粗体、斜体、下划线、删除线和扰流文字，以及内嵌链接和预设格式的代码。
Telegram 客户端会相应地呈现它们。您可以直接指定文本实体，也可以使用下划线样式或 HTML 样式的格式。
<br>

### 文本消息的格式

在 Telegram 中，消息支持以下特殊格式：**粗体**、*斜体*、__下划线__、~~删除线~~、`等宽字体` 和 [超链接](#)。

在最新版的 Telegram 客户端中，用户可以直接选择文本并应用这些格式。在旧版本的 Telegram 中，要应用这些文本格式，必须通过机器人发送。
<br>

### 解析模式

如果你在使用机器人 Bot API，需要通过设置解析模式（`parse_mode`）来应用文本格式。
例如：在 `sendMessage` 方法中设置 `parse_mode=HTML` 或 `parse_mode=Markdown`。然后，可以在 `text` 或 `caption` 参数中使用以下语法来发送特殊格式的消息。

<br><br>

## Markdown

### 语法示例 v1.0（2018-2020版本）
```
*粗体文本*
_斜体文本_
__下划线文本__
~~删除线文本~~
*粗体 _粗斜体 ~~粗斜体删除线~~ __粗斜体下划线___ 粗体*
[超链接文本](链接地址)
`等宽字体`
"   ```多行等宽字体```    ”
```

### 语法示例 v2.0（2020-2023版本）

```
*粗体文本*
_斜体文本_
__下划线文本__
~~删除线文本~~
||剧透字符||
*粗体 _斜体 粗体 ~斜体 粗体 删除线 ||斜体 粗体 删除线 剧透||~ __下划线 斜体 粗体___ 粗体*
[叮当猫](http://www.example.com/)
[叮当猫](tg://user?id=123456789)
![👍](tg://emoji?id=5368324170671202286)     #个性化表情
`等宽字体`
"```张晓丽
生日：1992-10-03         #多行等宽字体
```"
```
这两个版本都是可用的，v2.0需要将电报升级到最新版，机器人也支持！。


<br><br>

## HTML

### 语法示例 v1.0（2018-2020版本）
```
<b>粗体文本</b> 或 <strong>粗体文本</strong>
<i>斜体文本</i> 或 <em>斜体文本</em>
<u>下划线文本</u>, <ins>下划线文本</ins>
<s>删除线文本</s> 或 <strike>删除线文本</strike> 或 <del>删除线文本</del>
<b>粗体文本 <i>粗斜体文本 <s>粗斜体删除线文本</s> <u>粗斜体下划线文本</u></i> 粗体文本</b>
<a href="链接地址">超链接文本</a>
<code>等宽字体</code>
<pre>多行等宽字体
文本区块</pre>
```

### 语法示例 v2.0（2020-2023版本）
```
<b>粗体</b>, <strong>粗体</strong>
<i>斜体</i>, <em>斜体</em>
<u>下划线</u>, <ins>下划线</ins>
<s>删除线</s>, <strike>删除线</strike>, <del>删除线</del>
<span class="tg-spoiler">剧透</span>, <tg-spoiler>剧透</tg-spoiler>
<b>粗体 <i>斜体 粗体 <s>斜体 粗体 删除线 <span class="tg-spoiler">斜体 粗体 删除线 剧透</span></s> <u>下划线 斜体 粗体</u></i> 粗体</b>
<a href="http://www.example.com/">内联 URL</a>
<a href="tg://user?id=123456789">内联提及用户</a>
<tg-emoji emoji-id="5368324170671202286">👍</tg-emoji>
<code>内联固定宽度代码</code>
<pre>预格式化固定宽度代码块</pre>
<pre><code class="language-python">用Python编程语言编写的预格式化固定宽度代码块</code></pre>
```


<br><br>

## 内置链接

要在文本消息中提及（mention）某人，或使用深度链接（Deep link），可按以下方式操作。这类似于超链接功能，但是链接使用 Telegram 客户端软件可以解析的协议。
<br>

### 语法示例

```
[自定义超链接文本](tg://user?id=用户UID)
[叮当猫](tg://user?id=123456789)
[简体中文](tg://setlanguage?lang=zhhanttw)
[用户名](tg://resolve?domain=用户名)
[打开bot查询](tg://resolve?domain=用户名Bot&start=payload)
[将bot加入群组](https://t.me/用户名Bot?startgroup=payload)
[加入私人群组](tg://join?invite=邀请链接哈希)
[添加贴纸包](tg://addstickers?set=贴纸包名称)
[跳转到私人群组中的目标消息](https://t.me/c/群组ID/消息ID)
[跳转到公开群组中的目标消息](https://t.me/用户名/消息ID)
```


- `t.me/+ （hash)`
- `tg://join?invite=（hash）`    #加好友or群
- `t.me/addlist/（slug）`
- `tg://addlist?slug=（slug）`     #聊天文件夹链接
- `t.me/proxy?server=（server）&port=（port）&secret=（secret）`   
- `tg://proxy?server=（server）&port=（port）&secret=（secret）`         #电报代理
- `t.me/addtheme/（name）`
- `tg://addtheme?slug=（name）`   #name=主题包
- `tg://user?id=（id）` # 用户 ID
- `tg://emoji?id=（id）` # 自定义表情符号 ID
- `t.me/（bot_username）?start=（parameter）` # 链接到机器人并可能传递启动参数
- `tg://resolve?domain=（bot_username）&start=（parameter）` # 链接到机器人并可能传递启动参数
- `t.me/（username）?videochat` # 链接到群组的视频聊天
- `t.me/（username）?videochat=（invite_hash）` # 指定邀请码的视频聊天
- `t.me/（username）?livestream` # 链接到频道的直播
- `t.me/（username）?livestream=（invite_hash）` # 指定邀请码的直播
- `t.me/（username）?voicechat` # 链接到群组的语音聊天
- `t.me/（username）?voicechat=（invite_hash）` # 指定邀请码的语音聊天
- `tg://resolve?domain=（username）&videochat` # 链接到群组的视频聊天
- `tg://resolve?domain=（username）&videochat=（invite_hash）` # 指定邀请码的视频聊天
- `tg://resolve?domain=（username）&livestream` # 链接到频道的直播
- `tg://resolve?domain=（username）&livestream=（invite_hash）` # 指定邀请码的直播
- `tg://resolve?domain=（username）&voicechat` # 链接到群组的语音聊天
- `tg://resolve?domain=（username）&voicechat=（invite_hash）` # 指定邀请码的语音聊天
- `t.me/addstickers/（slug）` # 导入贴纸集
- `t.me/addemoji/（slug）` # 导入自定义表情符号贴纸集
- `tg://addstickers?set=（slug）` # 导入贴纸集
- `tg://addemoji?set=（slug）` # 导入自定义表情符号贴纸集
- `t.me/proxy?server=（server）&port=（port）&secret=（secret）` # MTProxy 链接
- `tg://proxy?server=（server）&port=（port）&secret=（secret）` # MTProxy 链接
- `t.me/socks?server=（server）&port=（port）&user=（user）&pass=（pass）` # Socks5 代理链接
- `tg://socks?server=（server）&port=（port）&user=（user）&pass=（pass）` # Socks5 代理链接
- `t.me/addtheme/（name）` # 安装主题
- `tg://addtheme?slug=（name）` # 安装主题
- `t.me/bg/（slug）?mode=（mode）` # 图像壁纸
- `tg://bg?slug=（slug）&mode=（mode）` # 图像壁纸
- `t.me/bg/（hex_color）` # 纯色填充壁纸
- `tg://bg?color=（hex_color）` # 纯色填充壁纸
- `t.me/bg/（top_color）-（bottom_color）?rotation=（rotation）` # 渐变填充壁纸
- `tg://bg?gradient=（top_color）-（bottom_color）&rotation=（rotation）` # 渐变填充壁纸
- `t.me/bg/（hex_color1）~（hex_color2）~（hex_color3）` # 自由渐变填充壁纸
- `tg://bg?gradient=（hex_color1）~（hex_color2）~（hex_color3）` # 自由渐变填充壁纸
- `t.me/bg/（slug）?intensity=（intensity）&bg_color=（bg_color）&mode=（mode）` # 图案壁纸
- `tg://bg?slug=（slug）&intensity=（intensity）&bg_color=（bg_color）&mode=（mode）` # 图案壁纸
- `t.me/login/（code）` # 登录码链接
- `tg://login?code=（code）` # 登录码链接
- `t.me/invoice/（slug）` # 发票链接

<br>

### 注解

```
tg://user?id={UID}：{UID} 是用户的唯一标识码，数字格式，机器人也有相应的识别码。
tg://resolve?domain={Username}：{Username} 是用户名，由英文、数字、下划线组成。
tg://join?invite={InviteHash}：{InviteHash} 是邀请链接的哈希部分，通常为 22 位字符。
tg://setlanguage?lang={LangPackName}：{LangPackName} 是语言包的短名称。
tg://addstickers?set={PacksetName}：{PacksetName} 是贴纸包的短名称。
tg://resolve?domain={Username}&post={MessageId}：{MessageId} 是聊天室内消息的唯一标识码。
```


