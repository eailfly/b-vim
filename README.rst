b-vim
=====

Fork自 `k-vim <https://github.com/wklken/k-vim>`__
--------------

    LAST\_UPDATE\_TIME: 2015-12-15

目标
====

    Just a Better Vim Config. Keep it Simple.


安装步骤
========

1. clone 到本地
~~~~~~~~~~~~~~~

::

    git clone https://github.com/eailfly/b-vim.git

2. 安装依赖包
~~~~~~~~~~~~~

2.1 使用Python
''''''''''''''

::

    sudo pip install pyflakes
    sudo pip install pylint
    sudo pip install pep8

3. 安装
~~~~~~~

::

    进入目录, 执行安装
    # 不要到~/.vim下执行(这是软连接指向b-vim真是目录)，必须到b-vim原生目录执行
    # 会进入安装插件的列表，一安装是从github clone的，完全取决于网速, 之后会自动编译 YCM, 编译失败的话需要手动编译, 有问题见YCM文档
    # 如果发现有插件安装失败 可以进入vim, 执行`:PlugInstall'

    cd b-vim/
    sh -x install.sh

------------------------
------------------------

常见问题
========

详见 `wiki <https://github.com/wklken/k-vim/wiki>`__ 以及
`issues <https://github.com/wklken/k-vim/issues>`__

------------------------
------------------------

插件
====

选择安装插件集合
~~~~~~~~~~~~~~~~

编辑vimrc.bundles中

::

    " more options: ['json', 'nginx', 'golang', 'ruby', 'less', 'json', ]
    let g:bundle_groups=['python', 'javascript', 'markdown', 'html', 'css', 'tmux', 'beta']

选定集合后, 使用插件管理工具进行安装/更新

插件管理
~~~~~~~~

使用 `vim-plug <https://github.com/junegunn/vim-plug>`__ 管理插件

``vim-plug`` 常见问题: `vim-plug
faq <https://github.com/junegunn/vim-plug/wiki/faq>`__ 

管理插件的命令

::

    :PlugInstall     install                      安装插件
    :PlugUpdate      install or update            更新插件
    :PlugClean       remove plugin not in list    删除本地无用插件
    :PlugUpgrade     Upgrade vim-plug itself      升级本身
    :PlugStatus      Check the status of plugins  查看插件状态

插件列表
~~~~~~~~

说明/演示/自定义快捷键等, 待处理

------------------------
------------------------

自定义快捷键
============

::

    注意, 以下 ',' 代表<leader>
    1. 可以自己修改vimrc中配置，决定是否开启鼠标

    set mouse-=a           " 鼠标暂不启用, 键盘党....
    set mouse=a            " 开启鼠标

    2. 退出vim后，内容显示在终端屏幕, 可以用于查看和复制, 如果不需要可以关掉
        好处：误删什么的，如果以前屏幕打开，可以找回....惨痛的经历

    set t_ti= t_te=

    3. 可以自己修改vimrc决定是否使用方向键进行上下左右移动，默认关闭，强迫自己用 hjkl，可以注解
    hjkl  上下左右

    map <Left> <Nop>
    map <Right> <Nop>
    map <Up> <Nop>
    map <Down> <Nop>

    4. 上排F功能键

    F1 废弃这个键,防止调出系统帮助
    F2 set nu/nonu,行号开关，用于鼠标复制代码用
    F3 set list/nolist,显示可打印字符开关
    F4 set wrap/nowrap,换行开关
    F5 set paste/nopaste,粘贴模式paste_mode开关,用于有格式的代码粘贴
    F6 syntax on/off,语法开关，关闭语法可以加快大文件的展示

    F9 tagbar
    F10 运行当前文件(quickrun)

    5. 搜索
    <space> 空格，进入搜索状态
    /       同上
    ,/      去除匹配高亮

    (交换了#/* 号键功能, 更符合直觉, 其实是离左手更近)
    #       正向查找光标下的词
    *       反向查找光标下的词

    优化搜索保证结果在屏幕中间

    6. tab操作
    ctrl+t 新建一个tab

    (hjkl)
    ,th    切第1个tab
    ,tl    切最后一个tab
    ,tj    下一个tab
    ,tk    前一个tab

    ,tn    下一个tab(next)
    ,tp    前一个tab(previous)

    ,td    关闭tab
    ,te    tabedit
    ,tm    tabm

    ,1     切第1个tab
    ,2     切第2个tab
    ...
    ,9     切第9个tab
    ,0     切最后一个tab

    ,tt 最近使用两个tab之间切换
    (可修改配置位 ctrl+o,  但是ctrl+o/i为系统光标相关快捷键, 故不采用)

    7. buffer操作(不建议, 建议使用ctrlspace插件来操作)
    [b    前一个buffer
    ]b    后一个buffer
    <-    前一个buffer
    ->    后一个buffer


    8. 按键修改
    Y         =y$   复制到行尾
    U         =Ctrl-r
    ,sa       select all,全选
    ,v        选中段落

    ctrl+n    相对/绝对行号切换
    <enter>   normal模式下回车选中当前项

    更多细节优化:
        1. j/k 对于换行展示移动更友好
        2. HL 修改成 ^$, 更方便在同行移动
        4. <和> 代码缩进后自动再次选中, 方便连续多次缩进, esc退出
        5. 对py文件，保存自动去行尾空白，打开自动加行首代码
        6. 'w!!'强制保存, 即使readonly
        7. 去掉错误输入提示
        8. 交换\`和', '能跳转到准确行列位置
        9. python/ruby 等, 保存时自动去行尾空白
        10. 统一所有分屏打开的操作位v/s[nerdtree/ctrlspace] (特殊ctrlp ctrl+v/x)
        11. ',zz' 代码折叠toggle
        12. python使用"""添加docstring会自动补全三引号
        13. Python使用#进行注释时, 自动缩进

------------------------
------------------------

UPDATE\_LOG
~~~~~~~~~~~

version 9.1

::

    插件部分:
    1. 使用 'junegunn/vim-plug' 替代 'VundleVim/Vundle.vim' 来管理插件, 安装/更新速度更快
    2. 支持自定义插件集合, 可以配置自己需要安装的插件
    3. 去除tomorrow主题插件 'chriskempson/vim-tomorrow-theme'
    4. 去除 minibufferexpl 所有配置(ctrlspace替代)
    5. 去除 taglist 所有配置(tagbar和ctrl-funky替代)
    6. Python插件, 增加 'hynek/vim-python-pep8-indent'
    7. Python插件, 去除 'kevinw/pyflakes-vim'
    10. 快速移动, 增加插件 'unblevable/quick-scope', 按f/F/t/T时触发, 行内快速移动, 与 easymotion 互补
    11. (bundle_groups配置了tmux)tmux插件 'christoomey/vim-tmux-navigator'

    细节:
    1. 插件 'terryma/vim-expand-region', 增加自定义每次加减的区域配置
    2. 解决在insert mode粘贴代码缩进错乱问题(以前需要:set paste . 即k-vim中F5快捷键, 现在不需要了)


Contributors
~~~~~~~~~~~~


查看详情
`git-contributors <https://github.com/wklken/k-vim/graphs/contributors>`__

Inspire
~~~~~~~

1. vimrc文件布局\ ``vimrc+vimrc.bundles``\ 配置方式参考
   `maximum-awesome <https://github.com/square/maximum-awesome>`__

2. install.sh 参考\ ``spf13-vim`` 的\ ``bootstrap.sh``
   `spf13-vim <https://github.com/spf13/spf13-vim>`__

3. 插件管理使用\ `Vundle <https://github.com/gmarik/Vundle.vim>`__

4. 自动补全 `YCM <https://github.com/Valloric/YouCompleteMe>`__

5. 插件挑选 `VimAwesome <http://vimawesome.com/>`__

Resources
~~~~~~~~~

`链接 <http://www.wklken.me/posts/2014/10/03/vim-resources.html>`__

Donation
~~~~~~~~

如果你认为对你有所帮助, You can Buy *wklken* a coffee:)

.. figure:: https://raw.githubusercontent.com/wklken/gallery/master/donation/donation.png
   :alt: donation

   donation

------------------------
------------------------
