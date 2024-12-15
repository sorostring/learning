# BASIC #
主要记录一些联系性不强、系统性不强的知识。
# `虚拟环境` #
在Python开发中，虚拟环境是一个非常重要的工具，它可以帮助我们隔离项目的依赖，避免不同项目之间的冲突。常见的虚拟环境工具有`venv`和`Conda`，它们各有优缺点，适用于不同的场景。

虚拟环境的存在，是因为工业上的开发，常常需要用到不同的代码版本，不同的项目（不同的python脚本）也会遇到需要引用不同的库文件。这个时候，就需要给我们的python脚本划定一个单独的`虚拟环境`，让代码在这个虚拟环境里面跑就可以了，互相之间是不会干扰的。

在学习Python时，理解虚拟环境非常重要。虚拟环境是一个隔离的Python运行环境，它可以让你为不同的项目，分别创建独立的环境，每个环境有自己的库和依赖，不会与其他项目的环境冲突。

虚拟环境的作用：
1. **隔离不同项目的依赖**：有时候不同的项目需要不同版本的库。虚拟环境让你可以为每个项目创建独立的环境，避免库的版本冲突。
2. **避免污染全局环境**：如果直接在全局Python环境中安装库，可能会导致全局环境中的库版本不一致。虚拟环境帮你避免这种问题。
3. **便于管理**：通过虚拟环境，你可以更方便地管理每个项目所需的依赖包，并且便于分享给他人，确保他们的开发环境与我们的一致。

- `venv环境`

    venv环境是Python内置的虚拟环境模块，从Python 3.3版本开始引入。它的作用与`conda`类似，都是为了帮助你创建和管理独立的Python虚拟环境。不过`venv`是Python标准库的一部分，不需要额外安装，只要你安装了Python，就可以直接使用了。
    
    而`conda`则是一个独立的包管理器，通常与`Anaconda`或`Miniconda`一起使用。它的主要特点是轻量级，适用于纯Python项目。使用venv`创建虚拟环境`的命令如下：
    - 在Windows上
        >python -m venv myenv

    - 在Linux/macOS上
        >python3 -m venv myenv
    
    创建虚拟环境后，需要`激活`它：

    - 在Windows上
        >myenv\Scripts\activate

    - 在Linux/macOS上
        >source myenv/bin/activate

    在Windows下，当你激活Python虚拟环境后，可以看到cmd的变化：
    ```
    (myenv) C:\Python\Python38-32>pip list
    Package    Version
    ---------- -------
    pip        20.2.3
    setuptools 49.2.1
    ```
    LOOK！这个时候，发生了变化，有个`(myenv)`显示在那里！如果你运行 pip list命令，可以看到只有基本的packages，并没有你之前装了的那些packages!
    
    
    在`激活的虚拟环境中，可以使用pip安装项目所需的包`：
        
    >pip install numpy pandas

    这样，numpy和pandas两个库就会被安装到myenv虚拟环境中，而不会影响到其他环境。
    
    当完成工作后，可以使用以下命令`退出虚拟环境`：

    >deactivate

    `删除虚拟环境`：如果不需要可以删除这个虚拟环境对应的文件夹即可。比如
    > rm -rf myenv  【Unix】

    > rmdir /s myenv  【Windows系统，或者手动删除对应的文件夹】

    venv的优点是它是Python标准库的一部分，不需要额外安装，适用于需要轻量级环境的纯Python项目。
- `Conda环境`
    
    Conda环境，是一个开源的跨平台包管理器和环境管理器，适用于Python、R、Java等多种语言。它不仅可以管理Python包，还可以管理其他语言的包和依赖项。使用Conda创建虚拟环境的命令如下：
    >conda create --name myenv python=3.8

    创建虚拟环境后，需要激活它：
    >conda activate myenv

    在激活的虚拟环境中，可以使用conda或pip安装项目所需的包：

    >conda install numpy pandas
    
    当完成工作后，可以使用以下命令退出虚拟环境：
    >conda deactivate

    Conda的优点是它功能强大，适用于复杂项目，特别是涉及多种语言或非Python依赖项的项目。
选择`venv`还是`Conda`，主要取决于项目的需求和个人偏好。如果你正在开发一个纯Python项目，并且希望使用Python的标准包管理工具，那么使用`venv`是一个不错的选择。如果你需要更强大的包管理和跨语言支持，以及更丰富的生态系统，那么`Conda`可能更适合你的需求

# `安装和运行` #
笔者常用的是*PyCharm*和*VS Code*这两个IDE。其中*Pycharm*是自己不带有Python 3.0的解释器的，需要使用者自己去[Python.org](www.python.org)去下载newest released version，然后在*Pycharm*中指定编译环境才可以。

在使用*PyCharm*的时候，是要指定运行环境的，这个时候就存在上文提到的`venv环境`和`conda环境`，要细心配置。

而对于*Microsoft*的*VS Code*，貌似只需要在插件市场（extention market）载入*Python*的插件就可以了。 

# `Anaconda的介绍` #
Anaconda是一个非常流行的Python和R语言的发行版，主要由于数据科学、机器学习等领域。它包含了众多常用的科学计算库，比如Numpy、Pandas、Matplotlib等，并且提供了方便的包管理和环境管理工具。**作为发行版的Anaconda，本身就带有完善的packages，所以它不会出现到处找package版本，这里不兼容那里不兼容，pip时不时也要更新，安装一个库的前提是另一个库存在，pip下载的package版本不对又无法安装，等等诸如此类的麻烦问题，就不会占用开发者的精力了。**

- Anaconda有什么用？
    
    1. 简化软件包管理：Anaconda通过`conda`命令，可以轻松地安装、更新和卸载各种python包和环境。

    2. 创建独立的环境：不同项目可能需要不同版本的Python和不同的库，Anaconda可以创建多个独立的环境，避免不同项目之间的冲突。

    3. 预装大量科学计算库： Anaconda预装了大量的科学计算库，省去了你动手安装的麻烦。
- Anaconda的组成
    1. `conda`：Anaconda的核心包管理器，用于管理软件包和环境。

    2. `Python`：内置了Python的解释器。也就是说，Anaconda部署的时候，自己是自带一个Python解释器的，这个Python的解释器是内嵌其中的。如果我们同时在Python官网上下载并安装了官方的IDLE，那么相当于我们有两个Python，一个是Anaconda，另一个是python.org的。

    3. `众多科学计算库`：NumPy、Pandas、Matplotlib、Scikit-learn等。

    4. `Juypter Notebook`：交互式编程环境，方便数据分析和可视化。
- Anaconda中的`conda`命令
    
    Anaconda的`核心工具`是`conda`，它用于管理`软件包`、`环境`、`通道（channels）`。通过conda命令，我们可以轻松地安装、更新、删除软件包，创建、激活、克隆和删除环境。
    - Anaconda Prompt/Anaconda Powershell Prompt：
    
        这两个工具类似于Windows系统下的cmd和powershell，可以理解成Anaconda的shell，是介于系统和用户之间的桥梁。下面所说的conda命令，都是在这两个shell内输入的。
    
- 常用的conda命令：
    
    1. 查看conda版本：
        > conda --version

    2. 查看所有环境：
        > conda info --envs
        
        如果没有虚拟环境建立，系统会提示：
        ```
        # conda environments:
        #
        base                  *  C:\Anaconda3
        ```
    3. 创建新的虚拟环境：
        > conda create -n myenv1 python=3.8

        "myenv1"就是你新建的conda环境的名字，下同。

        `这里还能选择安装的虚拟环境的Python版本，比如Python=3.8, python=3.9等`
    4. 激活虚拟环境：
        > conda activate myenv1

        激活虚拟环境后，shell内部的提示会变成myenv1打头。
        ```
        (myenv1) PS C:\Users\Administrator>
        ```
    5. 退出虚拟环境：
        > conda deactivate
        退出后一般会回到base环境。
        ```
        (base) PS C:\Users\Administrator>
        ```
    6. 查看当前环境已经安装的包：
        > conda list
    7. 安装新包：
        > conda install numpy pandas matplotlib
    8. 更新包：
        > conda update numpy
    9. 删除包：
        > conda  remove numpy
    10. 搜索包：
        > conda search numpy
        
        `这个搜索包的功能，是将现在conda能够搜的到的这个numpy的所有版本罗列出来  TBC`

        `因为你使用conda install命令的时候，可以指定这个包的版本~~~`
    11. 克隆环境：
        > conda create -n newenv1 --clone myenv1
        
        `从虚拟环境myenv1，克隆出来，新克隆的环境叫做newenv1`
    12. 删除环境
        > conda remove -n myenv1 --all
    13. 更新conda自身
        > conda update conda
    14. 查看帮助
        > conda --help
- 清华大学的镜像：
    
    清华大学是有自己的一个镜像源的，因为很多时候国外网络下载耗时长。

    [清华大学镜像源-anaconda-pkgs-free-win-64](https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/win-64/)，这里就储存着64位windows的anaconda的包。

    其实要善于运用清华大学、阿里云的这些镜像源系统。以Anaconda来说，它的官方网站只有最新版本的发行版，但是有时候你需要低版本的Anaconda，官网上没有，但是这些镜像源都会有保存。

# `Jupyter Notebook`
在Anaconda的cmd或者PowerShell中就可以打开Jupyter Notebook:
     
>(base) PS C:\Users\Administrator> jupyter notebook

在Anaconda的shell中打开了Jupyter notebook之后，就会自动部署好服务器。这个时候，会默认使用IE打开。你想用chrome去输入代码调试python文件的话，可以在chrome的地址栏输入：
> localhost:8888

然后会让你输入token，这个token在Anaconda PowerShell prompt/cmd中就有。Jupyter notebook的运行是基于服务器的，这个操作相当于是登录进去服务器了。

- 修改Jupyter Notebook的页面字体：

    > C:\Anaconda3\Lib\site-packages\notebook\static\components\codemirror\lib\codemirror.css
    
    请改动这个.css文件，就是进入到notebook的安装包内，去找这个文件。


# `官方文档` #
Python官方文档的链接是
>[https://docs.python.org/3/](https://docs.python.org/3/)

其中对于初学者最重要的两个链接是：
> - Turorial: https://docs.python.org/3/turorial/index.html
> - Library Reference: https://docs.python.org/3/library/index.html
> 
### 为什么一定要阅读官方文档？###

市面上你能看到的教程和官方文档的属性都是不同的。官方文档没有办法对于入门者、初学者过分友好，毕竟`全面`、`权威`、`准确`才是官方文档应该做到的。所以很多入门者在刚开始学习的时候，会求助于各种非官方的教材、教程。这就造成了一个奇怪的现象：
>原本是在入门了之后，就应该“只阅读官方文档”，或者“第一查询对象只能是官方文档”。但是很多人那里居然变成了“从始至终都在回避官方文档”（或者说“回避最专业的文字”）。

Please keep the following principles in your heart:
> 第一查询对象只能是官方文档

当使用google的时候，常常可以使用这样的格式：
> < querries > site:python.org

有时候甚至可以在指定目录内搜索：
>  bytes site:python.org/3/library

你可以自己试一下"bytes site:pythoon.org/3/library"。这不仅仅是对于Python，对于其他很多编程语言和学习新的软件包（库）的新特性，都可以。

`所谓超强的自学能力，基本上就是由一些类似这样的学习习惯，和另外一些特别基础的方法，所构成的强大能力。`

# 运行和调试代码 #
## `Bash and Batch` ##
这个是困扰很多人的东西，那些莫名其妙的符号是什么意思？
- Bash

    Bash，`Unix shell的一种`，在1987年由布莱恩·福克斯为了GNU计划而编写。1989年发布第一个正式版本，原先是计划用在GNU操作系统上，但能运行于大多数类Unix系统的操作系统之上，包括Linux与Mac OS X v10.4都将它作为默认shell。
    - SHELL
        
        Unix shell，通常被称作“命令行”，为Unix和类Unix操作系统提供了传统的用户界面。用户通过输入shell所执行的命令，引导计算机的操作。在微软Windows操作系统平台，类似程序是command.com，或者基于Windows NT内核操作系统的cmd.exe。

        >我们可以把SHELL看做是介于用户和操作系统内核中间的一壳“层”。这壳层叫做SHELL是很形象的。

        > In fact，shell这个概念不仅仅在UNIX上有，Windows系统上也有。more details presented below.

        shell术语最普通的解释就是：**用户用来输入命令的任何程序**。自从在Unix操作系统中用户能够选择所使用的shell（登录时应当执行哪种程序）以来，许多shell已经被开发出来。**`所以有很多不同种类的shell，他们都具有shell的定义，能够充当用户和操作系统内核之间的桥梁`**。之所以被称为“shell”，是因为它隐藏了shell界面下面的操作系统的细节（这与最底层的“kernel”相反）。
        
        类似地，Unix图形化用户界面，注入`GNOME`、`KDE`和`Xfce`等，偶尔被称作“`可视shell`”或“`图形shell`”。图形shell，这是一个很形象的称呼。
        
        `shell术语通常与命令行相关联`。在Unix中，任何程序都可能是用户的shell。希望使用不同语法输入命令的用户，可以指定一个不同的程序作为他们的shell。
        
        术语shell也与一个特殊的程序相关，比如Bourne shell，`sh`（这是我们经常能够看到的一个词，sh）。Bourne shell是早期版本Unix所使用的shell，并成为一个事实上的标准；`任何类Unix系统至少拥有一个与Bourne shell相兼容的shell`。
        
        Bourne shell程序位于Unix系统的`/bin/sh`。在某些系统中，比如BSD，“/bin/sh”是一个或等同于Bourne shell，但在Linux等其他系统上，“/bin/`sh`”更多的是一个兼容的、更加富功能性的shell链接。POSIX将其标准shell制定为Korn shell的一个严格子集。

    - shell的作用：

        1. 命令解释器：shell接收用户输入的命令，然后调用相应的程序或者系统命令来执行。
        2. 用户界面：shell提供了用户与操作系统交互的界面，可以是命令行界面（`CLI`），也可以是图形用户界面（`GUI`）。
        3. 脚本语言：许多shell本身也是一种脚本语言，允许用户编写脚本来自动化任务。
    - shell的类型
        1. 命令行shell
            - `Bash`：Bourne Again Shell，是Linux和macOS系统默认的shell，功能强大，定制性高。
            - `Zsh`：Z shell，在Bash的基础上进行了扩展，提供了更丰富的功能和更友好的交互。
            - `Fish`: Friendly Interactive Shell，强调用户体验，提供智能命令补全和语法高亮等功能。
        2. 图形shell
            - `Windows Explorer`: Windows系统的文件管理器，也是一种图形shell。
            - `Finder`:  MacOS系统的文件管理器。
    - Bash 和 Zsh的区别与选择：
        
        Bash, as mentioned above, is short for "Bourne Again SHell". 历史悠久，是UNIX系统的传统shell，兼容性广。稳定可靠被广泛使用。配置相对简单适合新手。

        Zsh, as mentioned above, is "Z SHell". 它功能强大，在Bash的基础上进行了扩展，提供了更丰富的功能。能够高度可定制，并且有丰富的插件。

        - macOS Mojave(10.14)及以前：默认Shell是Bash。
        - macOS Catalina(10.15)及以后：默认Shell是Zsh。

    >Bash (GNU Bourne-Again Shell) 是许多Linux发行版的`默认Shell`。事实上，还有许多*传统UNIX上用的Shell*，例如`tcsh`、`csh`、`ash`、`bsh`、`ksh`等等。
    
    Shell Script大致都类同，当您学会一种Shell以后，其它的Shell会很快就上手，大多数的时候，一个Shell Script通常可以在很多种Shell上使用。
    
    `Bash`是大多数Linux系统以及Mac OS X`默认的shell`，它能运行于大多数类Unix风格的操作系统之上，甚至被移植到了Microsoft Windows上的Cygwin系统中，以实现Windows的POSIX虚拟接口。此外，它也被DJGPP项目移植到了MS-DOS上。
    
    Bash的命令语法是Bourne shell命令语法的超集。数量庞大的Bourne shell脚本大多不经修改即可以在bash中执行，只有使用了Bourne的特殊变量或内置命令的脚本才需要修改。 bash的命令语法很多来自**Korn shell** (`ksh`) 和 **C shell** (`csh`)， 例如命令行编辑，命令历史，目录栈，$RANDOM 和 $PPID 变量，以及POSIX的命令置换语法： $(...)。作为一个交互式的shell，按下TAB键即可自动补全已部分输入的程序名、文件名、变量名等等。
    >一句话概括，Bash是大多数Linux系统默认的Shell；Shell有很多种，在UNIX/Linux上面有特殊的作用。Bash是Shell的特例。
- Batch

    批处理是一种简化的脚本语言，也称作宏。它应用于DOS和Windows系统中，它是由DOS或者Windows系统内嵌的命令解释器（通常是COMMAND. COM或者CMD.EXE）解释运行。类似于Unix中的Shell脚本。批处理文件具有`.bat`或者`.cmd`的扩展名，其最简单的例子，是逐行书写在命令行中会用到的各种命令。更复杂的情况，需要使用if、for、goto等命令控制程序的运行过程，如同C，Basic等中高级语言一样。如果需要实现更复杂的应用，利用`外部程序`是必要的，这包括系统本身提供的外部命令和第三方提供的工具或者软件。

    Bash是UNIX系统的一种Shell，类比一下，`cmd也就是Windows系统的一种Shell（more information supplied below）。`
    
    批处理文件，或称为批处理程序，是由一条条的DOS命令组成的普通文本文件，可以用记事本直接编辑或用DOS命令创建，也可以用DOS下的文本编辑器Edit.exe来编辑。在“命令提示”下键入批处理文件的名称，或者双击该批处理文件，系统就会调用cmd.exe运行该批处理程序。一般情况下，每条命令占据一行；当然也可以将多条命令用特定符号（如：&、&&、|、||等）分隔后写入同一行中；还有的情况就是像if、for等较高级的命令则要占据几行、几十甚至几百行的空间。系统在解释运行批处理程序时，首先扫描整个批处理程序，然后从第一行代码开始向下逐句执行所有的命令，直至程序结尾或遇见exit命令或出错意外退出。

    >以下代码是输出hello world的批处理命令
    ```
    @echo off
    echo hello world
    pause & exit
    ```
    >以下代码从键盘读入，然后打印出来。
    ```
    @echo off
    set /p "input=>"
    echo 您输入的是%input%
    pause
    ```
    我们在工程运算中，是经常会遇到批处理*bat*文件的。输入的脚本运行好了之后，由处理程序挨个调用，就可以利用晚上的时间进行集中计算。
- `Batch 和 PowerShell`

    大家会很好奇，为什么whindows提供了两个命令提示符，一个是`cmd`，一个是`PowerShell`。这两个都叫做`Command-in Shell`。官网的描述是：Windows has two command-line shells: the *Command shell* and *PowerShell*. Each shell is a software program that provides `direct communication` between you and the operating system or applicatin, providing an environment to automate IT operations.

    - 从本质上说，cmd和PowerShell都是Windows系统的`shell`。CMD shell是最早内置于Windows的Shell，用于执行Windows命令和批处理文件等。PowerShell的设计目的是扩展CMD shell的功能，可以运行称之为“`cmdlet`”的PowerShell命令。cmdlet类似于Windows命令，但是提供了更多可扩展的脚本语言功能。你可以`在PowerShell中运行win命令和PowerShell专属的cmdlet命令`。但是CMD shell只能运行Windows命令，不能运行cmdlet命令。实际上CMD是DOS操作系统的继承，功能很有限。
    
    - PowerShell就更强了，除了运行普通的Windows命令外，它还是一个完整的脚本语言运行环境。

        `cmdlet`是`command let`的缩写，是专门在Windows系统的PowerShell中使用的命令。cmdlet是由`.net`库编写的，命令的命名规范遵循`“动词-名词”`的格式。如`Set-location`（类似于CMD下的cd命令）。cmdlet命令返回的是一个`.net对象`。
    - CMD的命令可以在PowerShell中用，但是反过来不行。另外，LINUX系统中的一些命令，也可以在PowerShell中运行，如`ls`等。
    - CMD和PowerShell都可以编写`脚本程序语言的批处理程序`。CMD的脚本语言扩展名 `.bat`格式，而PowerShell的脚本语言扩展名是`.ps1`格式。Power可以作为CMD的上位替代。
---

# 环境变量 #
这个问题对于windows系统是经常存在的。我们在安装python.org下载的python中有一个步骤是需要添加环境变量的。如果没添加的话，就会存在问题。
> 一个方便操作：

> 在任何一个Windows桌面的路径上，我们在标题栏输入`cmd`，然后回车，就会看到`cmd`自动打开，`cmd`的工作路径就是当前的文件夹。这样你就不需要在cmd里面一行一行地进入到你要的工作路径了。（也可以输入`powershell`，这个时候就会在当前路径下调用`PowerShell`了）

>还有一个tips: `windows键`+`R`,输入cmd/powershell，就可以调出CMD/powershell的窗口了。

- 我们遇到的问题，pip命令无法工作（注意,pip命令是要在cmd里面进行的，在Python的IDLE里面是不能进行的）
    
    这一般就是环境变量没有设置好导致的。`pip.exe`一般是在`\python\scripts\`这个文件夹里面的。如果没有设置好环境变量，就会导致系统找不到`pip.exe`这个文件。自然也就没有办法运行它了。
    > what is 环境变量？

    > 你可以理解环境变量就是，在系统找不到路径的时候，需要去找的路径。我早不到我要的文件了，我就去环境变量找一下看看。

所以最终的解决方案就是，把`\python\script\`这个文件夹添加到环境变量`PATH`里面去就好了。
- 另外还要提到的就是镜像的问题。有时候直接从国外的网站下载packages比较慢。这个时候可以从国内的镜像下载。
- 如果我们只安装了python 3.x和PyCharm。在PyCharm中新建一个project，然后这个project的interpret就指定我们装的python 3.x。如果要安装package，也是需要到pip安装好了之后，才能在PyCharm中显示出来的。
- 从外部下载的package，一般保存的路径是`\Lib\site-packages`
## pip命令 ##
1. `pip list`：查看本机上所有的已安装的packages.
2. `pip install -i 包名`：安装包。这个general option参数`-i`，是depends on version of Python，低版本的不一定有。
3. pip install -i 镜像源：镜像源的选择有，阿里的镜像源、清华大学的镜像源等等。

# Postional Argument / Keyword Argument #
这两个concepts存在于`函数的参数`中。分别是指`位置参数`和`关键字参数`。我们以print()函数为例：

>**`print`**(**objects, `sep`=' ', `end`='\n', `file`=sys.stdout, `flush`=False*)

Print objects to the text stream file, separated by `sep` and followed by `end`. 
>`sep`, `end`, `file` and `flush`, if present, must be given as `keyword arguments`.

All non-keyword arguments are `converted to strings like str() does` and written to the stream, separated by `sep` and followed by `end`. Both `sep` and `end` must be `strings`; they can also be None, which means to use the `default values`. If no objects are given, print() will just write `end`.

The file argument must be an `object with a write(string) method`; if it is not present or None, sys.stdout will be used. Since printed arguments are converted to text strings, `print() cannot be used with binary mode file objects`. For these, use `file.write(...)` instead.

Whether output is buffered is usually determined by file, but if the flush keyword argument is true, the stream is forcibly flushed.

**`print`**(**objects, `sep`=' ', `end`='\n', `file`=sys.stdout, `flush`=False*)    ：这是一个系统自带的internal function。


这里就清晰的提到了：`sep`, `end`, `file` and `flush`, if present, must be given as `keyword arguments`。这个print()函数有4个`keyword argument`，缩写为`kwarg`。这是`关键字参数`，他们对于函数是不可或缺的，有时候不写出来：they can also be None, which means to use the `default values`，但是它们依然是函数参数的一部分。也就是说：
>print('Hello', 'world')

>print('Hello', 'world', sep=' ', end='\n', file=sys.stdout, flush=False)

这两个语句是一样的，输出的结果都是：
```
Hello world
        <---new line here!
```
仔细阅读之后我们就会发现，原来print()函数也是可以往文件里写数据的，因为有个`file=`这个`kwarg`。只要file这个参数为一个已经打开的文件对象就可以了！

```python
print('hello', 'world')
print('hello', 'world', sep='')
print('hello', 'world', sep='$')
print('hello', 'world', sep=' ', end='--END--')
```
上述代码块输出：
>hello world

>helloworld

>hello$world

>hello world--END--

这里有要注意：
- print()函数，输出完了之后，默认是有'\n'在结尾的，也就是说，输出完了字符串之后，默认是有一个回车另起一行的。这就造成了如果我们print('\n'),你会看到`2个`空白行。
- print()函数的官方文档定义中，可以看到是print(*objects, XXXX)。这个objects默认是个复数，也就是说可以指定多个对象。这就是说下列用法都是被允许的：
    >print('I', 'Love', 'this', 'world!')
    
    >print('My age is:', a)
    
    >print('I am', a, 'years old.')

thus, 我们可以对`keyword argument`和`Positional argument`进行区分和总结：
- `Keyword Argument`：缩写为kwarg
    
    1. 函数在调用的时候，必然要`接收`关键字参数kwarg。

    2. kward是有自己的默认值default value的。没有进行“kwarg = XXX”这样的指定，会默认接收kwarg的default value。

    3. 如果给kwarg指定默认值以外的value，请使用`kwarg = XXX`的形式。

    4. 调用函数接收kwarg的时候，位置可以有调整（具体的规则请参阅函数那部分的细致讲解）

    5. 形式上，在函数定义中，`带有=，并设置了默认值的参数argument`，就是`keyword argument/kwarg`。
    
- `Positional Argument`
    
    位置参数。顾名思义，就是由位置决定其值的参数。比如`divmod(a,b)`函数，其中的a、b就是位置参数，第1个参数是被除数，第2个参数是除数。整个函数返回一个tuple，第1个值是商，第2个值是余数。很明显，a和b就是positional argument。具体的细节请参看`function.md`文件。
    - `Optional Positional Argument`：可选位置参数

        举例：
        > `pow(x, y[,z])`
        
        3个arguments。z是Optional Positional Argument，可选位置参数。Pow()函数其实有两种用法，执行结果是不一样的。
        > pow(x, y)：返回的是x**y

        > pow(x, y, z)：返回的是x**y%z
        
# CR & LF
CR就是：Carriage Return
LF就是：Line Feed

很久以前，有电传打字机Teletype(tty)。这是现代信息编码的雏形。tty是接受电信号，并完成文件的打印。那么tty上有2个操作，一个是CR，就是打印头咻的一下回到本行的开始处（但是没有换行）。

另一个就是LF，这个操作是，打印头没有动，但是整个纸张向上挪动了一行。

所以，CR并没有换行。LF虽然新启了一行，但是打印头也并没有回到行首。Thus it is concluded that `现在计算机中的一个回车 = CR+LF。`本质上是tty的CR和LF两个操作，才能完成现在我们电脑上的一个回车！

所以对于`转义字符`（`Escaping Character`）中的控制字符，我们可以这么理解：
> \n：在Python中相当于CR+LF

> \t：制表符

> \r：相当于CR，光标只是回到本行行首。

举例：
```python
print('fuck you',end=' -$-')
print('\r',end='')
print('A')
```
输出的内容（在python官方的`IDLE`中运行）为：
```
Auck you -$-

```
> 但是呢，这个代码的执行也依赖于具体的环境。在pycharm中，上述诊断代码就不会输出上述的结果。而是只输出一个A。说明第三行`print('A')`在执行的时候，PyCharm和Python IDLE的处理是不同的。

# pip 安装的问题
1. 打印当前python的版本
    > python --version

    打印当前pip的版本
    > pip --version

    pip如果出错，升级pip的命令
    > python -m ensurepip --upgrade

    pip没出错，还想要升级pip的命令
    > pip install --upgrade pip
2. 一般安装python package的命令
    
    pip install pandas
    由于网络的问题，GFW的问题，可能会造成链接到[pypi.org](www.pypi.org)超时，可以将默认的超时时间调整到200秒。
    >pip --default-timeout=200 install pandas
3. 镜像源切换的问题
    下载实在太慢了，就要考虑更换镜像源了。
    - 清华镜像源

    - 官方镜像源：https://pypi.org

    - 阿里云镜像原

    使用方法：
    > pip install --index-url https://pypi.tuna.tsinghua.edu.cn/simple/pandas

4. 版本的问题
    
    packages都存在安装版本的问题，这个时候要安装特定版本，需要额外的命令。在www.pypi.org上，找到要安装的版本后，标题会给出安装的命令。比如：
    > pip install notebook==6.0.0
    
    这样就专门安装6.0.0版本的juypter notebook包了。
5. 还有一种方法，从pypi上下载package的文件进行本地安装。
    在安装包所处的文件夹下：
    > pip install xxxxxxxx.tar.gz

Actually，使用Python自带的pip进行包管理费劲不说，主要是稳定性不好，总会出现各种各样的问题。倒不如使用Anaconda这样的发行版软件。

---
