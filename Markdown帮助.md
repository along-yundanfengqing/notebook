## 欢迎使用 MarkdownPad 2 ##

**MarkdownPad** 是 Windows 平台上一个功能完善的 Markdown 编辑器。

### 专为 Markdown 打造 ###

提供了语法高亮和方便的快捷键功能，给您最好的 Markdown 编写体验。

来试一下：

- **粗体** (`Ctrl+B`) and *斜体* (`Ctrl+I`)
- 引用 (`Ctrl+Q`)
- 代码块 (`Ctrl+K`)
- 标题 1, 2, 3 (`Ctrl+1`, `Ctrl+2`, `Ctrl+3`)
- 列表 (`Ctrl+U` and `Ctrl+Shift+O`)

### 实时预览，所见即所得 ###

无需猜测您的 [语法](http://markdownpad.com) 是否正确；每当您敲击键盘，实时预览功能都会立刻准确呈现出文档的显示效果。

### 自由定制 ###
 
100% 可自定义的字体、配色、布局和样式，让您可以将 MarkdownPad 配置的得心应手。

### 为高级用户而设计的稳定的 Markdown 编辑器 ###
 
 MarkdownPad 支持多种 Markdown 解析引擎，包括 标准 Markdown 、 Markdown 扩展 (包括表格支持) 以及 GitHub 风格 Markdown 。
 
 有了标签式多文档界面、PDF 导出、内置的图片上传工具、会话管理、拼写检查、自动保存、语法高亮以及内置的 CSS 管理器，您可以随心所欲地使用 MarkdownPad。

----------

###如何在Linux下使用Markdown进行文档工作

自从使用了markdown，做文档工作就很顺手。我几乎将工作中所有的文档工作都用markdown来完成。最近有了一些新的体验，也发现了一些新的问题。

在Linux系统中，编辑markdown可以用retext工具：

```
# Debian/Ubuntu
sudo apt-get install retext
retext Release-Notes.md
```

要将markdown文件转换成html文件，可以用discount或python-markdown软件包提供的markdown：

```
# Debian/Ubuntu
sudo apt-get install discount
```

或：

```
# Debian/Ubuntu
sudo apt-get install python-markdown
```

转换工作很简单：

```
# 用discount提供的markdown工具
markdown -o Release-Notes.html Release-Notes.md
# 用python-markdown提供的markdown_py工具
markdown_py -o html4 Release-Notest.md > Release-Notes.html
```

如果要生成PDF，也很简单，可以用python-pisa提供的xhtml2pdf：


```
# Debian/Ubuntu
sudo apt-get install python-pisa

# 将html转换成PDF
xhtml2pdf --html Release-Notes.html Release-Notes.pdf
```

所以，你可以在文档目录下放置这样一个Makefile来自动这个过程：

```make
# Makefile
MD = markdown
MDFLAGS = -T
H2P = xhtml2pdf
H2PFLAGS = --html
SOURCES := $(wildcard *.md)
OBJECTS := $(patsubst %.md, %.html, $(wildcard *.md))
OBJECTS_PDF := $(patsubst %.md, %.pdf, $(wildcard *.md))

all: build

build: html pdf

pdf: $(OBJECTS_PDF)

html: $(OBJECTS)

$(OBJECTS_PDF): %.pdf: %.html
    $(H2P) $(H2PFLAGS) $< > $@ 

$(OBJECTS): %.html: %.md
    $(MD) $(MDFLAGS) -o $@ $<
clean:
    rm -f $(OBJECTS)
```

这样你就可以通过简单的一个命令生成当前目录下所有md文件的pdf或html输出了：

```
# html 输出
make html

# pdf输出
make pdf
```

这里有个问题是如果markdown的内容是中文，那么转换出来的html在浏览器中打开就无法自动识别编码，pdf更惨，直接是一堆乱码。这时我们可以借助markdown对html标记的支持来在markdown文件中加入编码信息。例如我们要将markdown转换为html4文件，可以在文件的开头加上meta标记，指明编码格式：

```
sed -i '1i\<meta http-equiv="content-type" content="text/html; charset=UTF-8">' *.md
```

这样就可以了。另外，最近使用图灵社区的编辑系统时，markdown会时不时将下划线（_）当作斜体的标记，结果函数名就成了这样的：

```
# 实际上是ssl_use_cabundle
sslusecabundle
```

我建议斜体字标记采用单个星号（*），加粗字体采用两个星号（\*\*），这样使用起来就方便多了。当然，这个问题本身在于markdown说用星号或下划线都可以。但实际上，两个都支持反倒会造成一些问题。比如有的地方用下划线（\_\_粗体\_\_ -> 粗体），有的地方用星号（\*\*粗体\*\* -> 粗体），看起来反倒混乱不堪（选星号*的另一个理由是下划线在内容中出现的概率比星号高很多）。

建议图灵社区的在线编辑系统指定其中一种，然后在例子中和在线编辑器里都采用统一的一种，这样大多数人一看就明白该用哪种了。

---

###Markdown语法帮助

[Markdown标准语法](http://daringfireball.net/projects/markdown/syntax)

[Markdown扩展语法](http://michelf.ca/projects/php-markdown/extra/)

[GitHub风格Markdown语法](http://github.github.com/github-flavored-markdown/)



2016/6/30 19:51:45 

----------
###超链接用法
![baidu](http://www.baidu.com/img/bdlogo.gif)

![baidu](http://www.baidu.com/img/bdlogo.gif "百度logo")

[![baidu](http://www.baidu.com/img/bdlogo.gif "百度Logo")](http://baidu.com)
