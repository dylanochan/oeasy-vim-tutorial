---
show: step
version: 1.0
enable_checker: true
---

# 缩写abbreviation

## 回忆上次折叠的细节

- 这次了解到了`:mkview`、`:loadview`
- 保存和加载视图
- 可以把当前的状态保存下来
- 可以在 `viewoption` 中配置保存选项，设置哪些需要保存
- 还可以保存多个视图
	- 在整个文档中跳来跳去
- 视图里面可以有很多本地窗口的设置
	- 折叠
	- 缩写
	- 映射
- 那么到底什么是缩写(`abbreviations`)和映射(`mappings`)呢？🤔

### 缩写就是`abbreviations`
- 缩写之类的东西我们早就见过
	- `:se nu`
	- `:se[t] nu[mber]`
- 不用都打上，打上缩写形式就自动能好使

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20211220-1639960265439)

- 类似的还有
	- `:%s`
	- 等价于`:%substitute`

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20211220-1639960300497)


### 缩写abbreviation
- 我们可以快速地定义缩写
- `:abbreviate hi hello` 
	- 这个时候如果输入`hi`<kbd>空格</kbd>
	- hi就自动变成了hello
	- 不过目前系统配置有点问题

### 调整设置
- 当前系统配置有点问题
- 需要看一下 `~/.vimrc`

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20210724-1627118976197)

- 把177这句 `set paste` 是控制粘贴用的
- 有的时候粘贴出来时对不齐就用 `:set paste`
- 粘贴完之后 `:set nopaste`
- 现在我们 `:set nopaste` 确保缩写可以用起来

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20211220-1639960942492)

### 设置缩写
- 这有点像颜文字转化工具
- `:abbreviate sml ヾ(❀╹◡╹)ﾉ~`
	- 还挺好使 哈哈
- 还可以使用缩写形式`ab`
	- `:ab o1z oeasy`
- 还可以用来改错
	- `:ab teh the`

- 不论是在插入模式下，还是在命令行模式下
- 只要输入缩写形态，然后加一个空格
- 就自动完成切换

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20211220-1639960593417)


- 这个东西其实还是有一定实用性的
	- `:ab sysout System.out.println();`
	- 不过我可以控制最终的光标位置么?

### 光标的控制

- 定义新的缩写
	- `:ab sysout System.out.println("");<left><left><left>`
	- 这样就可以在快速得到输出语句之后
	- 还把光标放在最合适的位置

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20211220-1639963186729)

- 这样就可以快速插入一些复杂的语句
- 那么这个可以换行么？

### 添加换行符号

- `:ab htmlbase <html><cr><tab><head></head><cr><body></body><cr><backspace></html><up><right><right>`

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20211220-1639963228069)

- 这样就可以快速插入一些更大规模的模板之类的内容
- 目前有什么缩写abbreviate 
- 可以列表出来么

### 列出所有的缩写abbreviate
- `ab[breviate]`可以列出所有的缩写

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20210724-1627115680457)

- 第一列代表使用范围
	- `!` - 全部模式包括输入和命令行
	- `i `- 输入模式 insert
	- `c `- 命令行模式 command
- 单独定义某模式下的ab
	- `:iab o1z oeasy` 只在插入模式下进行缩写替换
	- `:cab o1z oeasy` 只在命令模式下进行缩写替换
	- `:ab o1z oeasy` 在全部模式下都能进行缩写替换

### 取消缩写

- `:ab`先看看有啥
- `:una o1z`

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20210724-1627117290994)

- 再 `:ab` 发现这个`o1z`已经删除了
- 清空  `clear`
- `:iabc[lear]` 
	- 清空输入(insert)状态下的缩写abbreviate
- `:cabc[lear]` 
	- 清空命令(command)状态下的缩写abbreviate
- `:abc[lear]` 
	- 清空一切状态下的缩写abbreviate

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20210724-1627117122470)


- 一个个定义映射有点麻烦
- 我能直接利用曾经写过的单词么？

### 自动补全

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20210725-1627174405321)

- 我们的缓冲中有很多已经写出来的单词
- 我们可以用这些来做自动补全
- 我们写下S然后按下<kbd>ctrl</kbd><kbd>p</kbd>
	- 出现一个提示框我们可以选择里面的单词
	- <kbd>ctrl</kbd><kbd>p</kbd> - previous
	- <kbd>ctrl</kbd><kbd>n</kbd>  - next
	- 随着输入的进行还可以缩小查找范围

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20210725-1627174613432)

- 这个东西也是非常实用的小技巧 

## 总结

- 这次了解到了`:abbrivate`缩写
- 可以定义缩写
	- `:ab o1z oeasy`
	- 这里面还可以包括方向键、回车键之类的东西
- 可以定义到指定的模式
	- `iab`
	- `cab`
- 查看缩写
	- `:ab` - 所有的
	- `:ab o1z` - o1z
- 自动补全
	- <kbd>ctrl</kbd><kbd>p</kbd>
	- <kbd>ctrl</kbd><kbd>n</kbd>
- 这些缩写都可以保存在视图里
	- 保存的选项在`viewoption`中
- 可以保存的除了 `缩写abbreviate` 还有个 `映射map`
- `映射map` 什么意思呢？🤔
- 下次再说！