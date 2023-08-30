# Vim 速查手册

下面是我根据课程内容整理的一份 Vim 操作手册, 不会进行详细解释, 因此想要了解 Why 的同学建议去看原版教学视频.

PS: 感谢崔sir录制了这么优秀的 Vim 课程, 如果你也想学习的话, 可以[戳这里](https://learn.cuixueshe.com/p/t_pc/course_pc_detail/camp_pro/course_2Eo5kBtrovv2UqWVy75SmYZP6UM)加入训练营.

## 安装代码编辑器
Visual Studio Code(VScode)

[下载链接](https://code.visualstudio.com/Download)

## 安装插件
VSCodeVim

[下载链接](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)

## 手册

> 说明: 
> 1. 如果键位之间用 `+` 连接, 代表是组合键, 需要同时按下. 而如果键位之间直接连接, 则代表是先后分开连续按下.
> 2. 某些操作并不是 Vim 原生的, 而是通过改键配置实现的, 详细的配置我放到了文章最后, 有需要的可以自取.
> 3. 注意区分大小写

### Vim 语法
操作(operation) + 动作(scope)
数字 + 操作(operation) + 动作(scope)
操作(operation) + 数字 + 动作(scope)
#### 操作

删除: `d`

删除并进入 insert 模式: `c`

复制: `y`

重复上一次的修改: `.`

#### 动词
配合光标移动去确定接受操作的范围

### normal 模式下的光标移动

#### 基于字符

向左移动一个字符: `h`

向右移动一个字符: `l`

#### 基于单词/字符串(会忽略空格)

往后移动到单词的结尾: `e`

往后移动到字符串的结尾: `E`

往后移动到单词的开头: `w`

往后移动到字符串的开头: `W`

移动到上一个单词的开头: `b`

移动到上一个字符串的开头: `B`

移动到上一个单词的结尾: `ge`

#### 基于行

向上移动一行: `k`

向下移动一行: `j`

移动到光标所在行行首: `0`

移动到光标所在行行首第一个不是 blank 字符(空格、Tab、换行、回车)的位置: `^`, `H`

移动到光标所在行行尾: `$`

移动到光标所在行行尾最后一个不是 blank 字符的位置: `g_`, `L`

### 单文件中的移动

向下滚动一屏: `Ctrl` + `f` (forward)

向上滚动一屏: `Ctrl` + `b` (backward)

向下滚动半屏: `Ctrl` + `d`

向上滚动半屏: `Ctrl` + `u`

向下滚动一行: `Ctrl` + `e`

向上滚动一行: `Ctrl` + `y`

向下滚动 5 行: `J`

向上滚动 5 行: `K`

跳转到下一个段落: `}`

跳转到上一个段落: `{`

将当前行置于屏幕中央: `zz`

将当前行置于屏幕顶部: `zt`

将当前行置于屏幕底部: `zb`

跳到文件首: `gg`

跳到文件尾: `G`

跳到指定行: `<number>gg`, `<number>G`(<number>指行数)

单文件内标记并跳转
  - 标记: `m{小写字母}`, 例如: `mm`
  - 跳转: `'{小写字母}`, ``{小写字母}`

多文件间标记并跳转
  - 标记: `m{大写字母}`, 例如: `mM`
  - 跳转: `'{大写字母}`, ``{大写字母}`

跳到变量定义/使用处: `gd`

向前跳转: `Ctrl` + `i`

向后跳转: `Ctrl` + `o`

查看跳转历史: `:jumps`
### 使用 vim-easymotion

往下移动到单词的开头: `<leader>w`

往下移动到单词的结尾: `<leader>e`

往上移动到单词的开头: `<leader>b`

往上移动到单词的结尾: `<leader>ge`

往下移动到行首: `<leader>j`

往上移动到行首: `<leader>k`

Matches beginning & ending of word, camelCase, after _, and after # forwards: `<leader>l`

Matches beginning & ending of word, camelCase, after _, and after # backwards: `<leader>h`

JumpToAnywhere motion; default behavior matches beginning & ending of word, camelCase, after _ and after #: `<leader><leader><leader>j`

### normal 模式下的操作

#### 基于字符

删除光标所在的字符: `x`

删除光标前的字符: `X`

删除当前光标的字符并进入 insert 模式: `s`

删除当前光标所在行并进入 insert 模式: `S`

替换一个字符: `r`

替换多个字符: `R`

#### 基于行

复制光标所在行: `yy`

光标所在行行后粘贴: `p`

删除光标所在行: `dd`

#### undo/redo

undo: `u`

redo: `Ctrl` + `r`

### 从 normal 模式进入 insert 模式

光标前进入: `i`

光标当前行行首第一个不是 blank 字符前进入: `I`

光标后进入: `a`

光标当前行行尾进入: `A`

光标当前行行后添加一个新行并进入: `o`

光标当前行行前添加一个新行并进入: `O`

### 从 normal 模式进入 visual 模式

基于字符进入 visual 模式: `v`

基于行进入 visual 模式: `V`

基于块进入 visual 模式: `Ctrl` + `v`

### visual 模式下的操作

> 语法: 先选中 + 后操作

切换可视区的光标(可视区中内含一对光标, 可来回切换对可视区范围进行控制): `o`

回到上一次选择的选择区域: `gv`

### 从 visual 模式退回到 normal 模式

从 visual 模式进入 normal 模式: `Esc`, `Ctrl` + `[`, `v`(对应基于字符的 visual 模式), `V`(对应基于行的 visual 模式)

### 从 insert 模式回到 normal 模式

从 insert 模式进入 normal 模式: `Esc`, `Ctrl` + `[`, `jk`

### 在终端中使用 Vim 后退出(在 normal 模式下)

保存并退出: `:wq` + `Enter`

强制退出: `:q!`

### 操作文本对象
> 文本对象是结构化的, 可以快速选择. 可以通俗的将文本对象理解为一种特殊的范围, 并且可以通过某个键位进行指代

#### 语法
- operator + (内部/外部) + 文本对象
- 可视化模式 + (内部/外部) + 文本对象

#### 内部/外部
`i` 表示内部

`a` 表示外部

#### 文本对象
- 一个单词: `w`
- 一对(): `(` 或 `)` 或 `b`
- 一对[]: `[` 或 `]`
- 一对{}: `{` 或 `}` 或 `B`
- 一对<>: `<` 或 `>`
- XML标签: `t`
- 一对'': `'`
- 一对"": `"`
- 一对\`: ` ` `
- 一个句子: `s`
  - 在 Vim 中只有以`.`, `!`, `?` 结尾才算一个句子, 与英语句子对应.
- 一个段落: `p`
  - 被空行隔开的文本

- vim-textobj-arguments
  - 不包含分隔符: `ia`
  - 包含分隔符: `aa`
  - 技巧
    - 删除一个参数: `daa`
    - 修改一个参数: `cia`

- vim-textobj-entire
  - 当前文本所有内容, 但是不包含前面和后面的空格: `ie`
  - 当前文本所有内容: `ae`

#### vim-surround
Change existing surround to desired: `cs<existing><desired>`

Add desired surround around text defined by: `ys<motion><desired>`

Delete existing surround: `ds<existing>`

Surround when in visual modes(surround full selection): `S<desired>`
### 搜索
#### 单行搜索
光标正向移动到下一个{char}所在之处的前一个字符上: `t{char}`

光标反向移动到上一个{char}所在之处的后一个字符上: `T{char}`

重复上次的字符查找命令: `;`

反转方向查找上次的字符查找命令: `,`
#### 全局搜索

向后查: `/{string}`, `f{2char|(char Enter)}`

向前查: `?{string}`, `F{2char|(char Enter)}`

重复上次的字符串查找命令: `n`

反转方向查找上次的字符串查找命令: `N`

查看搜索历史: `/` + `上下方向键`

对光标所停留之处的单词进行严格向下查找: `*`

对光标所停留之处的单词进行严格向上查找: `#`

### 特定场景的超好用组合键分享

删除当前单词: `ciw`, `diw`

给下一行行尾添加分号: `A;`

在当前单词结尾处添加: `ea`

跨多行编辑:
  - 给多个行后面加分号: `V` 配合 `A` 或者 `I`

### Tips
在normal模式下使用`p`粘贴是往光标后插入内容, 而使用 `Ctrl` + `v` 则是往光标前插入内容

可撤销块: 进入 insert 模式开始, 直到返回 normal 模式为止, 在此期间输入或删除的任何内容都被当成一次修改. 另外在 insert 模式中使用上下左右方向键也会产生可撤销块.
