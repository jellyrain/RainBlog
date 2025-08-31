---
title: Expressive Code 示例
published: 2024-04-10
description: 使用 Expressive Code 在 Markdown 中的代码块展示效果。
tags: [Markdown, 博客, 演示]
category: 示例
draft: false
---

在这里，我们将探索如何使用 [Expressive Code](https://expressive-code.com/) 展示代码块。提供的示例基于官方文档，你可以参考官方文档获取更多详细信息。

## Expressive Code

### 语法高亮

[语法高亮](https://expressive-code.com/key-features/syntax-highlighting/)

#### 常规语法高亮

```js
console.log('这段代码被语法高亮了!')
```

#### 渲染 ANSI 转义序列

```ansi
ANSI colors:
- Regular: [31mRed[0m [32mGreen[0m [33mYellow[0m [34mBlue[0m [35mMagenta[0m [36mCyan[0m
- Bold:    [1;31mRed[0m [1;32mGreen[0m [1;33mYellow[0m [1;34mBlue[0m [1;35mMagenta[0m [1;36mCyan[0m
- Dimmed:  [2;31mRed[0m [2;32mGreen[0m [2;33mYellow[0m [2;34mBlue[0m [2;35mMagenta[0m [2;36mCyan[0m

256 colors (showing colors 160-177):
[38;5;160m160 [38;5;161m161 [38;5;162m162 [38;5;163m163 [38;5;164m164 [38;5;165m165[0m
[38;5;166m166 [38;5;167m167 [38;5;168m168 [38;5;169m169 [38;5;170m170 [38;5;171m171[0m
[38;5;172m172 [38;5;173m173 [38;5;174m174 [38;5;175m175 [38;5;176m176 [38;5;177m177[0m

Full RGB colors:
[38;2;34;139;34mForestGreen - RGB(34, 139, 34)[0m

Text formatting: [1mBold[0m [2mDimmed[0m [3mItalic[0m [4mUnderline[0m
```

### 编辑器和终端框架

[编辑器和终端框架](https://expressive-code.com/key-features/frames/)

#### 代码编辑器框架

```js title="my-test-file.js"
console.log('标题属性示例')
```

---

```html
<!-- src/content/index.html -->
<div>文件名注释示例</div>
```

#### 终端框架

```bash
echo "这个终端框架没有标题"
```

---

```powershell title="PowerShell 终端示例"
Write-Output "这个有标题!"
```

#### 覆盖框架类型

```sh frame="none"
echo "看，没有框架!"
```

---

```ps frame="code" title="PowerShell Profile.ps1"
# 不覆盖的话，这会是一个终端框架
function Watch-Tail { Get-Content -Tail 20 -Wait $args }
New-Alias tail Watch-Tail
```

### 文本和行标记

[文本和行标记](https://expressive-code.com/key-features/text-markers/)

#### 标记完整行和行范围

```js {1, 4, 7-8}
// 第 1 行 - 按行号定位
// 第 2 行
// 第 3 行
// 第 4 行 - 按行号定位
// 第 5 行
// 第 6 行
// 第 7 行 - 被范围 "7-8" 定位
// 第 8 行 - 被范围 "7-8" 定位
```

#### 选择行标记类型 (mark, ins, del)

```js title="line-markers.js" del={2} ins={3-4} {6}
function demo() {
  console.log('这一行被标记为删除')
  // 这一行和下一行被标记为插入
  console.log('这是第二个插入行')

  return '这一行使用中性的默认标记类型'
}
```

#### 为行标记添加标签

```jsx {"1":5} del={"2":7-8} ins={"3":10-12}
// labeled-line-markers.jsx
<button
  role="button"
  {...props}
  value={value}
  className={buttonClassName}
  disabled={disabled}
  active={active}
>
  {children &&
    !active &&
    (typeof children === 'string' ? <span>{children}</span> : children)}
</button>
```

#### 在独立行上添加长标签

```jsx {"1. Provide the value prop here:":5-6} del={"2. Remove the disabled and active states:":8-10} ins={"3. Add this to render the children inside the button:":12-15}
// labeled-line-markers.jsx
<button
  role="button"
  {...props}

  value={value}
  className={buttonClassName}

  disabled={disabled}
  active={active}
>

  {children &&
    !active &&
    (typeof children === 'string' ? <span>{children}</span> : children)}
</button>
```

#### 使用类似 diff 的语法

```diff
+这一行将被标记为插入
-这一行将被标记为删除
这是一个常规行
```

---

```diff
--- a/README.md
+++ b/README.md
@@ -1,3 +1,4 @@
+这是一个真正的 diff 文件
-所有内容将保持不变
 空白字符也不会被删除
```

#### 将语法高亮与类似 diff 的语法结合

```diff lang="js"
  function thisIsJavaScript() {
    // 整个块被高亮为 JavaScript，
    // 我们仍然可以为其添加 diff 标记！
-   console.log('要删除的旧代码')
+   console.log('全新闪亮的代码!')
  }
```

#### 标记行内的单个文本

```js "给定文本"
function demo() {
  // 标记行内的任何给定文本
  return '支持给定文本的多个匹配项';
}
```

#### 正则表达式

```ts /ye[sp]/
console.log('单词 yes 和 yep 将被标记。')
```

#### 转义正斜杠

```sh /\/ho.*\//
echo "Test" > /home/test.txt
```

#### 选择内联标记类型 (mark, ins, del)

```js "return true;" ins="inserted" del="deleted"
function demo() {
  console.log('这些是插入和删除标记类型');
  // return 语句使用默认标记类型
  return true;
}
```

### 自动换行

[自动换行](https://expressive-code.com/key-features/word-wrap/)

#### 为每个代码块配置自动换行

```js wrap
// 启用换行的示例
function getLongString() {
  return '这是一个非常长的字符串，除非容器极其宽大，否则很可能不适合可用空间'
}
```

---

```js wrap=false
// 禁用换行的示例
function getLongString() {
  return '这是一个非常长的字符串，除非容器极其宽大，否则很可能不适合可用空间'
}
```

#### 配置换行的缩进

```js wrap preserveIndent
// 启用 preserveIndent 的示例（默认启用）
function getLongString() {
  return '这是一个非常长的字符串，除非容器极其宽大，否则很可能不适合可用空间'
}
```

---

```js wrap preserveIndent=false
// 禁用 preserveIndent 的示例
function getLongString() {
  return '这是一个非常长的字符串，除非容器极其宽大，否则很可能不适合可用空间'
}
```

## 可折叠部分

[可折叠部分](https://expressive-code.com/plugins/collapsible-sections/)

```js collapse={1-5, 12-14, 21-24}
// 所有这些样板设置代码将被折叠
import { someBoilerplateEngine } from '@example/some-boilerplate'
import { evenMoreBoilerplate } from '@example/even-more-boilerplate'

const engine = someBoilerplateEngine(evenMoreBoilerplate())

// 这部分代码默认可见
engine.doSomething(1, 2, 3, calcFn)

function calcFn() {
  // 你可以有多个折叠部分
  const a = 1
  const b = 2
  const c = a + b

  // 这部分将保持可见
  console.log(`计算结果: ${a} + ${b} = ${c}`)
  return c
}

// 直到代码块结束的所有代码将再次被折叠
engine.closeConnection()
engine.freeMemory()
engine.shutdown({ reason: '示例样板代码结束' })
```

## 行号

[行号](https://expressive-code.com/plugins/line-numbers/)

### 为每个代码块显示行号

```js showLineNumbers
// 这个代码块将显示行号
console.log('来自第 2 行的问候!')
console.log('我在第 3 行')
```

---

```js showLineNumbers=false
// 此代码块禁用行号
console.log('你好?')
console.log('抱歉，你知道我在第几行吗?')
```

### 更改起始行号

```js showLineNumbers startLineNumber=5
console.log('来自第 5 行的问候!')
console.log('我在第 6 行')
```
