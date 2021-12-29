## 命令

#### 普通模式

> '>G' 当前行到文件末尾缩进(tab)，>>和<<仅仅是当前行缩进
>
> f{char} (当前行)查找下一处指定的字符，; 重复查找上次f命令所查找的字符， ,与;相反，反方向查找f{char}的字符
>
> C 删除光标到行尾所有字符,同时进入插入模式, c+($/0/c(删除当前行并进入编辑状态)/w(从光标所在的位置开始到该单词结束进行修改. 进入编辑状态))删除光标到行尾字符

- c

```
C or c$
表示修改当前行上光标后面的部分. 进入编辑状态.
c0 or c^
表示从光标处到当前行行首的部分进行修改，^代表首个非空格处。
cc OR S
修改当前行. 进入编辑状态.
cw
从光标所在的位置开始到该单词结束进行修改. 进入编辑状态
cfx AND cFx
这里的 x 为一任意字符, cfx 表示修改从光标到下一个字符 x 之间的文本;
cFx 表示修改从光标到上一个字符 x 之间的文本.
cn|
修改从光标到当前行的第 n 个字符间的所有字符, n 正整数.
cnG and cG
这里的 n 为一任意自然数, cnG 表示修改当前行到第 n 行之间的所有行;
cG 表示修改当前行直至末行. 
```



#### 插入模式

> ```
> a 当前光标之后添加内容，A当前行尾添加内容
> o 为在目前光标所在的下一行处输入新的一行， O 为在目前光标所在的上一行处输入新的一行
> i 为从目前光标所在处输入，I 为在目前所在行的第一个非空格符处开始输入
> r 只会取代光标所在的那一个字符一次，R会一直取代光标所在的文字，直到按下 ESC 为止
> s 删除光标字符，并进入插入模式
> ```
>
> 
>
> 



#### 命令模式

- 搜索替换

> ```
> :n1,n2s/word1/word2/g
> :1,$s/word1/word2/g 或 :%s/word1/word2/g 从第一行到最后一行寻找 word1 字符串，并将该字符串取代为 word2 
> :1,$s/word1/word2/gc 或 :%s/word1/word2/gc 从第一行到最后一行寻找 word1 字符串，并将该字符串取代为 word2 ！且在取代前显示提示字符给用户确认 (confirm) 是否需要取代
> ```
>
> 

#### 可视模式(按v)

> ```
> >和<可视模式下缩进
> ```
>
> 

## 配置

:map   :noremap  :unmap     普通、可视、选择、操作符等待
:nmap  :nnoremap :nunmap    普通
:vmap  :vnoremap :vunmap    可视与选择
:smap  :snoremap :sunmap    选择
:xmap  :xnoremap :xunmap    可视
:omap  :onoremap :ounmap    操作符等待
:map!  :noremap! :unmap!    插入与命令行
:imap  :inoremap :iunmap    插入
:lmap  :lnoremap :lunmap    插入、命令行、Lang-Arg
:cmap  :cnoremap :cunmap    命令行
:tmap  :tnoremap :tunmap    终端作业





## url

```
https://yianwillis.github.io/vimcdoc/doc/map.html#map-overview

```

