
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


