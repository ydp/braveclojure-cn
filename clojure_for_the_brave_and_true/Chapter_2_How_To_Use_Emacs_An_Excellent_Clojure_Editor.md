
### 如何使用emacs编写clojure程序 ###

在成为clojure大师之路上，编辑器是你最亲密的盟友。我极力推荐你使用emacs编写clojure代码，当然，你也可以使用其他编辑器。如果你不按本章的说明配置emacs，或者你打算用其他的编辑器，但至少你应该花一些时间，让你的编辑器可以在clojure的REPL模式下工作。

我推荐emacs的原因是它对clojure的REPL模式有非常强大的支持，允许你随时运行写好的代码。REPL模式的循环反馈功能在编写clojure程序的过程中非常有用，以后你会经常用到。当然emacs本身就是用lisp方言实现的，叫emacs lisp（elisp），它对编写所有lisp方言程序都有很好的支持。

当你学完本章，你的Emacs会变成下面这个样子：

![](http://www.braveclojure.com/assets/images/cftbat/basic-emacs/emacs-final.png)
Figure 2-1 代码在左，REPL在右

你会学到：安装emacs，设置个性化的emacs配置，如何打开、编辑和保存文件，如何使用快捷键与emacs交互，以及如何编辑clojure代码并在REPL模式下交互运行。

#### 安装 ####

使用最新的emacs版本，emacs 24，不同的操作系统安装方法如下：

* OS X  从http://emacsformacosx.com/下载vanilla Emacs，Aquamacs可以把emacs风格变得更接近mac，但那会带来比较多的问题，不建议使用。
* Uuntu 安装说明在这里 https://launchpad.net/~cassou/+archive/emacs
* Windows 下载地址http://ftp.gnu.org/gnu/emacs/windows/，下载完解压，运行可执行文件bin/runemacs.ext。

安装完成，你应该会看到下图所示的UI：

![](http://www.braveclojure.com/assets/images/cftbat/basic-emacs/emacs-fresh.png)
Figure 2-2 欢迎加入Emacs神教，Richard Stallman以你为傲

#### 配置 ####

我把配置clojure所需的文件都放到了一个仓库里，https://github.com/flyingmachine/emacs-for-clojure/archive/book1.zip，按下面的操作删除原来的emacs配置，安装clojure的emacs专属配置：

1. 关闭emacs
2. 删除~/.emacs 或 ~/.emacs.d 
3. 下载我的仓库文件，解压，把目录emacs-for-clojure-book1重命名为~/.emacs.d
4. 创建文件~/.lein/profiles.clj，在其中加入下面一行代码:
```clojure
{:user {:plugins [[cider/cider-nrepl "0.8.1"]]}} 
```
5. 重新打开emacs

打开emacs的时候，emacs可能会下载一些包，等下载完，关闭emacs重新打开（如果emacs没有下载任何东西，没关系，直接使用就ok），操作完成你会看到emacs变成如下界面：

![](http://www.braveclojure.com/assets/images/cftbat/basic-emacs/emacs-configged.png)
Figure 2-3 添加新配置的emacs外观

你已经完成了所有配置工作，可以正式开始进入使用环节。

#### Emacs逃生舱 ####

在尝试使用emacs之前，我想先告诉你一个最重要的emacs快捷键：Ctrl-G，这个快捷键会停止当前任何正在进行的emacs命令，一旦你发现有什么不对的地方，马上按下这个快捷键，它不会关闭Emacs，也不会让你丢失任何正在进行的工作，它只是撤销你当前正在进行的动作。

#### Emacs缓冲区 ####

emacs的所有编辑操作都只是写到缓冲区，你第一次打开emacs的时候，一个名叫`*scratch*`的缓冲区被打开了。任何时候，你都可以看到当前正在编辑的缓冲区名字，就在界面的最下方。如图:

![](http://www.braveclojure.com/assets/images/cftbat/basic-emacs/emacs-buffer-name.png)
Figure 2-4 emacs总是把当前缓冲区的名字显示在底部

默认情况下，`*scratch*`缓冲区以开发Lisp的方式处理括号匹配和缩进，这不便于普通的文字处理。这里我们创建一个全新的缓冲区，防止不可预见的情况发生。创建缓冲区，操作如下：

1. 按住Ctrl同事按住X
2. 释放Ctrl
3. 按住B

这个过程用快捷键表示为：C-x b
执行这些操作之后，emacs的底部会弹出一个提示窗，如下：

![](http://www.braveclojure.com/assets/images/cftbat/basic-emacs/emacs-buffer-prompt.png)
Figure 2-5 emacs为了接收输入的迷你缓冲区

这块区域叫做迷你缓冲区，emacs弹出这个小窗以方便接收你的输入。当前，它希望你输入一个缓冲区名字。此时，既可以输入一个已经存在的缓冲区名字，也可以输入一个新的缓冲区名字。输入 emacs-fun-times，回车。现在你会看到一个空白缓冲区，并且随时可以开始输入。你会发现随意的输入基本都会符合你的预期，输入字符就会显示字符，按下方向键光标也会按预想的方式移动，回车会新起一行。



