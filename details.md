<h1 style="text-align:center;">关于TEST仓库的文件详细说明</h1>

[TOC]

## 键盘与输入事件测试
### 按下的是非字符键时
- 仅触发`keydown`与`keyup`事件，通过`event.keyCode`可以查询按下的是什么键。
- 按下键按住不放会重复触发`keydown`事件，出于性能考虑有必要进行防抖处理或者进行其它限制。

### 按下的是字符键时
- 在`input`输入框中按下字符键，触发`keydown`,`keypress`,`textInput`,`keyup`事件。
- 在`document`按下字符键，触发`keydown`,`keypress`,`keyup`事件。
- `keypress`在用户按下某个字符键时触发，无论这个字符是否显示。通过`charCode`属性获取按键字符对应的ASCII编码，再通过`String.fromCharCode()`方法获取输入值。在DOM3事件中被废弃，转而推荐`textInput`事件。
- 按下字符键不放会重复触发`keydown`与`keypress`。
- `textInput`事件只能在输入框中触发，通过`data`属性获取输入的字符。

### 使用中文输入法时
- 在`document`中与英文输入法无区别
- 在输入框中，每次按键会触发`keyup`事件两次且两次触发的`e.keyCode`不一致，其触发顺序为`keydown`,`keyup`,`keyup`。
- 通过按键选中输入法中的候选字符时，触发顺序为`keydown`,`textInput`,`keyup`,`keyup`。
- `textInput`事件的data属性返回的只是编辑区域内的文本。通过点击字符键`1`选取某个汉字时，`e.data`返回的是具体的汉字文本而不是字符`1`。

[测试文件查看](https://syinho.github.io/TEST/%E9%94%AE%E7%9B%98%E4%B8%8E%E8%BE%93%E5%85%A5%E4%BA%8B%E4%BB%B6.html)
