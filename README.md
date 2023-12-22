# Telegram 文本格式和解析模式（Markdown、HTML）

## 目录

- 前言
- 文本消息的格式
- 解析模式
- Telegram 内置链接

## 前言

Telegram 支持信息的基本格式。您可以在机器人信息中使用粗体、斜体、下划线、删除线和扰流文字，以及内嵌链接和预设格式的代码。
Telegram 客户端会相应地呈现它们。您可以直接指定文本实体，也可以使用下划线样式或 HTML 样式的格式。

## 文本消息的格式

在 Telegram 中，消息支持以下特殊格式：**粗体**、*斜体*、__下划线__、~~删除线~~、`等宽字体` 和 [超链接](#)。

在最新版的 Telegram 客户端中，用户可以直接选择文本并应用这些格式。在旧版本的 Telegram 中，要应用这些文本格式，必须通过机器人发送。

## 解析模式

如果你在使用机器人 Bot API，需要通过设置解析模式（`parse_mode`）来应用文本格式。
例如：在 `sendMessage` 方法中设置 `parse_mode=HTML` 或 `parse_mode=Markdown`。然后，可以在 `text` 或 `caption` 参数中使用以下语法来发送特殊格式的消息。

### Markdown 语法示例v1

```markdown v1.0
*粗体文本*
_斜体文本_
__下划线文本__
~~删除线文本~~
*粗体 _粗斜体 ~~粗斜体删除线~~ __粗斜体下划线___ 粗体*
[超链接文本](链接地址)
`等宽字体`
“```多行等宽字体```”
```

```markdown v2.0
*bold \*text*
_italic \*text_
__underline__
~strikethrough~
||spoiler||
*bold _italic bold ~italic bold strikethrough ||italic bold strikethrough spoiler||~ __underline italic bold___ bold*
[inline URL](http://www.example.com/)
[inline mention of a user](tg://user?id=123456789)
![👍](tg://emoji?id=5368324170671202286)
`inline fixed-width code`
"```
pre-formatted fixed-width code block
```"
```

这两个版本都是可用的

### HTML 语法示例

```html
<b>粗体文本</b> 或 <strong>粗体文本</strong>
<i>斜体文本</i> 或 <em>斜体文本</em>
<u>下划线文本</u>, <ins>下划线文本</ins>
<s>删除线文本</s> 或 <strike>删除线文本</strike> 或 <del>删除线文本</del>
<b>粗体文本 <i>粗斜体文本 <s>粗斜体删除线文本</s> <u>粗斜体下划线文本</u></i> 粗体文本</b>
<a href="链接地址">超链接文本</a>
<code>等宽字体</code>
<pre>多行等宽字体
文本区块</pre>


Telegram 内置链接
要在文本消息中提及（mention）某人，或使用深度链接（Deep link），可按以下方式操作。这类似于超链接功能，但是链接使用 Telegram 客户端软件可以解析的协议。

使用 Markdown 的示例
markdown
Copy code
[自定义超链接文本](tg://user?id=用户UID)
[王小明](tg://user?id=123456789)
[点击这里切换语言](tg://setlanguage?lang=zhhanttw)
[用户名](tg://resolve?domain=用户名)
[打开bot查询](tg://resolve?domain=用户名Bot&start=payload)
[将bot加入群组](https://t.me/用户名Bot?startgroup=payload)
[加入私人群组](tg://join?invite=邀请链接哈希)
[添加贴纸包](tg://addstickers?set=贴纸包名称)
[跳转到私人群组中的目标消息](https://t.me/c/群组ID/消息ID)
[跳转到公开群组中的目标消息](https://t.me/用户名/消息ID)
链接格式详解
tg://user?id={UID}：{UID} 是用户的唯一标识码，数字格式，机器人也有相应的识别码。
tg://resolve?domain={Username}：{Username} 是用户名，由英文、数字、下划线组成。
tg://join?invite={InviteHash}：{InviteHash} 是邀请链接的哈希部分，通常为 22 位字符。
tg://setlanguage?lang={LangPackName}：{LangPackName} 是语言包的短名称。
tg://addstickers?set={PacksetName}：{PacksetName} 是贴纸包的短名称。
tg://resolve?domain={Username}&post={MessageId}：{MessageId} 是聊天室内消息的唯一标识码。

