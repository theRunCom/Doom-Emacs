# Doom-Emacs
🛠️Customize my personal Emacs configuration based on Doom Emacs according to my own needs

[Fetching Title#d6i2](https://emacstalk.codeberg.page/)

[Fetching Title#uii0](https://tecosaur.github.io/emacs-config/config.html)

[Fetching Title#d39s](https://docs.doomemacs.org/latest/)

[Guides & Tutorials - Doom Emacs Discourse](https://discourse.doomemacs.org/c/guides/5)

# 一、Emacs 简单介绍
Emacs 是一款自由软件，它是一款可扩展、自定义的文本编辑器。Emacs 在1976年由 Richard Stallman 开发，并于1984年发布了 GNU Emacs，现在由 GNU 项目维护。Emacs 的特点是可以通过 Lisp 编程语言进行扩展，使得用户可以自定义编辑器的行为和功能。Emacs 是一款非常强大的文本编辑器，它的强大功能和扩展性使得它成为了众多程序员的首选。

> An extensible, customizable, free/libre text editor and more.

🫶我目前使用的配置是基于 [Doom Emacs](https://github.com/doomemacs/doomemacs)，根据自身情况进行修改的。正如[一年成为Emacs高手 (像神一样使用编辑器)](https://github.com/redguardtoo/mastering-emacs-in-one-year-guide/blob/master/guide-zh.org) 所说的“站在巨人的肩膀上”，Emacs 本质是个平台, 提供了无限可能性✨。

# 二、为什么选择 Doom Emacs? 📥 

## 1. 个人折腾经历

我生性是一个爱折腾的人，因为我相信这些都会是值得的！“工欲善其事，必先利其器”，熟练掌握后必会大大提高我的工作效率。我最开始接触到的编辑器是 Sublime Text , 当时被它默认的主题 Monokai Pro 深深吸引，很是炫酷。后来又接触到了 VS Code，它的插件生态和主题都非常丰富，我也是非常喜欢的。不过当时 VS Code 刚出来没多久，由于在 Linux 上学习开发，后续便相继尝试了 Vim，neovim，Emacs 等编辑器。最后在 Vim 和 Emacs 中来回横跳，两款编辑器的可扩展性都非常强，最终我选择了 Emacs，而且 Evil-mode 出现，它完美的模拟了 Vim 的按键方式。就像 spacemac 的 slogan：“The best editor is neither Emacs nor Vim, it's Emacs and Vim!”说的那样，我也是这么认为的。而现在 Emacs 社区已经有了相当多的「明星配置包」，比如 [Spacemacs](https://github.com/syl20bnr/spacemacs) 、 [Purcell](https://github.com/purcell/emacs.d) 、 [Doom Emacs](https://github.com/hlissner/doom-emacs) 等。这些框架都十分全面且易用，在经过不断尝试后发现 Doom Emacs 最适合我!

## 2. Doom Emacs 介绍

Doom Emacs 是一个基于 Emacs 的高度定制化发行版，它旨在提供一个现代化、高效且易于配置的 Emacs 环境。与传统的 Emacs 不同，Doom Emacs 通过预配置和优化，为用户提供了一个功能强大的编辑器框架，使得用户可以更快速地上手和定制编辑器。默认是使用 vim 按键风格的，这是通过包 evil 实现的，也就是说在 emacs 内可以使用 vim 这种高效按键设计风格。

# 三、Doom Emacs 配置 🗒️ 

## 1. 安装

在保证网络科学畅通😷的情况下，都能安装成功！

[安装相关依赖 Prerequisites](https://github.com/doomemacs/doomemacs#prerequisites)

[正式安装 Install](https://github.com/doomemacs/doomemacs#install)

### doom 命令

doom 是个可执行文件，将其添加到 PATH 中  `export PATH="$PATH:/home/你的用户名路径（👀注意需更改）/.config/emacs/bin"`

- doom sync 用于同步私有配置和 Doom 配置。意味着只要你修改了私有配置的包相关的内容，都需要运行此命令，例如你要为私有配置添加了新的包 (插件)，或升级/降级了某个包，doom sync 会自动为你做好那些安装/降级/编译/链接操作。


- doom upgrade 用于更新 Doom 配置或更新所有包时，如果你看到 doom 的最新更新正好解决了你提的 issue 便可使用此命令让 Doom 更新为最新版本，又如果你想要升级所有的包 (插件)那么你也可以通过此命令进行升级。


- doom doctor 此命令效果是尝试找到 Doom 出错的问题，通常只能监测出常见的问题，如果你有问题可以先试试这个命令，再去群或者翻 issues。


- doom env 基本不用使用，其作用是让 doom 的环境变量和你的 shell 环境变量同步一下，除非你 shell 环境变量经常变动，否则是几乎不会用到这个功能的。


- doom build 重新编译所有的包 (把 el 文件编译成 elc 以提高运行速度)。


- doom info 输出 doom 的相关信息，用来给 doom 提 issue 用的。如果你需要提 issue，那么你需要将这个命令的输出也贴上去，用于判断是否是环境问题。


- doom clean 这个命令会删除所有的 elc 文件，执行后你需要使用 doom build 重新编译它们。


- doom run 从 doom 可执行文件的父级目录下启动 Emacs。我猜测可能是为了解决一些路径问题。


- doom compile 将私有配置和已开启的模块编译成字节码。提高运行效率的。


- doom purge 删除那些已安装，但是没有使用的包，并将其压缩。你有时可能会通过 M-x package-install 来安装包，这样是不太好的，你应该通过后面我说的方法来安装，否则就会出现有些包已安装但却没有使用的情况。


## 2. 基本配置

### 配置文件

Doom Emacs 的配置都在变量 `doom-user-dir` 指向的目录下（根据安装时的选择可能是 `~/.doom.d/` 或 `~/.config/doom/` ），主要是三个文件：

- `init.el` ：启用/停用 Doom 预先配置好的模块（ _modules_ ）；
  
- `package.el` ：自己另行下载安装的软件包（ _packages_ ），或对已启用的软件包版本进行配置，Doom Emacs 使用 `straight.el` 包管理器 [→](https://github.com/radian-software/straight.el)；
  
- `config.el` ：各种配置，大部分预制模块不需要或者只需要少许配置，因为 Doom 已经做了相对好的缺省安排，自行安装的包则需要做相应的配置；当然如果对 Doom 提供的缺省安排不满意，也可以在此动手覆盖。
  
### 包管理安装使用

> Next-generation, purely functional package manager for the Emacs hacker.

straight.el 将自己描述为“Emacs 的下一代包管理器”。实际上，straight.el 是 Emacs 内置包管理器 package.el 的替代品。对于任何 Emacs 用户来说日常使用都非常简单！Doom Emacs 使用自己的构建在 straight.el 上的陈述式包管理器，以下是其使用方法：

- 从官方的源 [MELPA](https://melpa.org/) / [GNU ELPA](http://elpa.gnu.org/) / [emacsmirror](https://emacsmirror.net/) 安装
    
 ```emacs-lisp
(package! some-package)
```
    
- 关闭某些包
    
```emacs-lisp
(package! some-package :disable t)
```
    
- 从 Git Repo 安装

```emacs-lisp
;; github 
(package! github-package :recipe (:host github :repo "username/repo")) 
;; gitlab
(package! gitlab-package :recipe (:host gitlab :repo "username/repo")) 
;; other
(package! other-package :recipe (:host nil :repo "https://example.com/repo"))
```
    
- 如果 repo 仅中只有某个 / 某些文件是你需要的
    
```emacs-lisp
(package! some-package
  :recipe (:host github :repo "username/repo"
	   :files ("some-file.el" "src/elisp/*.el")))
```

- 如果需要指定某个 `commit` 或某个 `branch`
```emacs-lisp
;; commit
(package! some-package :pin "abcdefghijk")
;; branch
(package! some-package :recipe (:branch "stable"))

```

    
- 使用本地的 repo
    
```emacs-lisp
(package! some-package :recipe (:local-repo "/path/to/repo"))
```
### 配置 packages
如果你的配置需求很简单，那么 `use-package!` ， `after!` ， `add-hook!` 和 `setq-hook!` 宏


## 3. 进阶配置

## 4. 使用方法
### 按键表示

### 状态（state）切换
Vim 的“模式”在 Doom 中称为“状态”（因为“模式”在 Emacs 中已有其他意义），是 Evil 包引入和实现。
默认是普通状态（normal state），可进行 vim 普通模式下的操作
按 Esc 键可从其他状态返回普通状态
从普通状态切换到其他状态的按键
i：插入状态
v：视图状态
V：行视图状态（整行选取）
C-v：块视图状态（矩形框选取）
C-z：正常 Emacs 状态切换，可在所有模式中使用该按键。“Emacs 状态”是没有打扮过的 Emacs，该状态下可以使用原生 Emacs 的编辑方式。
### 常用命令
文件操作（SPC f ）：
- f：打开/查找文件
- d：打开目录（Dired）
- s：保存文件
- r：最近文件列表
- y：拷贝当前文件名（路径）
- C：大写，拷贝当前文件（询问目标位置）
- D：大写，删除当前文件
- R：大写，重命名/移动文件
- S：另存

缓冲区操作（SPC b）：
- b：缓冲区列表
- n/[：切换到前一个缓冲区
- p/]：切换到后一个缓冲区
- s：保存当前缓冲区（使用命令和 SPC f s 可能不同）
- S：保存所有缓冲区
- d/k：关闭当前缓冲区
- O：关闭其他缓冲区
- K：关闭所有缓冲区
- z：隐藏/最小化当前缓冲区
- Z：关闭所有隐藏的缓冲区

窗口操作（SPC w）：
- v：垂直分割窗口
- s：水平分割窗口
- h/j/k/l：在窗口间移动光标（激活编辑窗口）
- w/W：向前/后窗口移动光标（比hjkl顺手）
- H/J/K/L：窗口位置置换/移动命令
- T：撕开窗口（把当前撕出来，试试就知道什么效果了）
- q：关闭当前窗口
- n：和s作用相同
- m：最大化当前窗口（全部、水平或垂直最大化，有提示）
- =：等分所有窗口（其他调整大小的命令不大实用，不如自己绑定按键）

打开其他程序/界面（SPC o）：
- p：打开/关闭 treemacs 目录树
- T：打开终端
- f：打开一个新窗口（显示当前缓冲区内容，等于在多窗口中同时编辑一个文件，内容同步！）
- a：org agenda (SPC a A 等于 SPC o a a)

切换（SPC t）：
- l：行号
- b：字体模式
- F：全屏模式等

其他：
- SPC q q：退出程序
- SPC h：帮助菜单，还有主题切换（SPC h t，不知道为啥放到这里）
- SPC p：项目操作。本人不习惯此类操作，不介绍。
# 四、学习资料推荐
## 1. Elisp 学习
[Emacs Lisp 简明教程](http://smacs.github.io/elisp/)

[Practical Emacs Tutorial By Xah Lee](http://xahlee.info/emacs/emacs/emacs.html)
# 五、致谢

[Fetching Title#nlzo](https://www.bilibili.com/read/cv11371146/)
[Fetching Title#9zkt](https://gitconnected.com/learn/emacs)






lsp-bridge 已经支持 Codeium 了：
1. 更新到最新版，打开选项 `(setq acm-enable-codeium t)`
2. 运行命令 `lsp-bridge-install-update-codeium` 来安装 Codeium
3. 运行命令 `lsp-bridge-codeium-auth` 来获取 auth token
4. 运行命令 `lsp-bridge-codeium-input-auth-token` 获取 API Key 后就可以使用了

[Fetching Title#35it](https://docs.doomemacs.org/latest/)