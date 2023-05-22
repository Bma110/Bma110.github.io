---
title: "备忘录1"
date: 2023-05-21T11:19:05+08:00
lastmod: 2022-11-28T16:53:08+08:00
comments: true
math: false
---

## 注意事项{alias="别名=ps 蒸\_汽\_波"}

1. 文章标题时，标题从二级标题开始：`## xxx`
|二级标题将作为大标，居中显示，后续标题左对齐

## Hugo 命令和网站部署

- 部署网站：`./utils/deploy.sh`
- 在本地服务器上运行：`hugo server`
|注意文件路径

## Shortcodes

见[Daisilia 主题文档](https://daisilia.com/projects/daisilia-%E4%B8%BB%E9%A2%98/)

## Snippets

### 使用 Vscode Snippet 功能

编辑代码片段（Snippets）：<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>p</kbd>，搜索“snipets”，选择“配置用户代码片段”,选择“markdown.js”

使用自动补全（输入时在光标处的弹出窗口）：

- <kbd>Up</kbd>、<kbd>Down</kbd>
- <kbd>Tab</kbd>/<kbd>Enter</kbd>：确定

### 内置 Snippets

- `bold`：粗体
- `italic`：斜体
- `fenced codeblock`：代码块
- `code`：行内代码
- `fenced math`：数学公式
- `inline math`：行内数学公式
- `heading1` ... `heading6`：1 到 6 级标题（小技巧：输入 h4 即可触发 heading4 的提示，其他类似）
- ...

### 自定义 Snippets


[CHEERFUL]({{< relref "test" >}})

新建 content 目录下的 test.md 文件：

```bash
hugo new test.md
```

markdown.json 文件示例：

```json
{
  "rrf": {
    "prefix": "rrf",           // 触发文本
    "description": "rellink",
    "body": [                  // 多行
      "[${1:name}]({{</* relref \"${2:ref}\" */>}})",
      "hello"
    ]
  },
  "kbd": {
    "prefix": "kbd",
    "body": "<kbd>${1:keys}</kbd>", // 单行
  }
}
```

#### 一般格式

每一个代码片段格式为：

```json
"rellink": {
  "prefix": "rrf",
  "description": "relative permalink",
  "body": [
    "[${1:name}]({{</* relref \"${2:ref}\" */>}})",
    "hello"
  ]
}, // 注意这个逗号
```

- 每个*代码片段*均有一个唯一的标识符，如`"rellink"`
- `prefix`: 触发文本，输入该文本（如`rrf`）
- `description`：描述文本，随意
- `body`：代码块主体，可以用一个字符串表示单行，或一个列表表示多行。

{{< tab type="default" >}}
json 文件两项之间用逗号，最后一项后的逗号也不违反语法。因此，推荐**每一项之后都加一个逗号**。
{{< /tab >}}

#### 占位符

{{< tab type="default" >}}
使用 <kbd>Tab</kbd> 和 <kbd>Shift</kbd>+<kbd>Tab</kbd> 可以在占位符之间移动。
{{< /tab >}}

```
${<num>:<prefill text>}
```

- `<num>`：移动顺序
- `<prefill text>`：预填充文本

特殊占位符：

- `$<num>`：复制 `<num>` 号占位符
- `$0`：移动的终点，移动到此处时结束，不能再反向移动

[显示内容]({{< relref "临床常见病原微生物#葡萄球菌" >}})
relref指向ID

hugo new diary/2023/05/22.md