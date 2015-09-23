# Practical Vim
## Edit Text at the Speed of Thought

## 第六章 管理多个文件

1. 技巧36 用缓冲区列表管理打开的文件

    在一次编辑会话中，可以打开多个文件。文件存储在磁盘上，而缓冲区存在于内存中。当Vim打开一个文件时，该文件内容被读入一个具有相同名字的缓冲区。刚开始缓冲区内容和文件内容完全相同，当我们对缓冲区做出修改时，两者内容出现差别。我们可以把缓冲区内容写回到文件中
    。

    Vim允许我们同时在多个缓冲区上工作。可以在命令模式下运行ls命令查看缓冲区。

    :bnext 命令可以切换到列表中下一个缓冲区。按<Ctrl-^>可以在当前文件和轮换文件中快速切换。

    我们可以用4条命令来便利缓冲区列表。:bnext 和 :bprev 在列表中正向或者反向移动，每次移动一项；而:bfirst 和 :blast 则分别跳到列表的开头和结尾。

    :ls 列表的开头有一个数字，他是在缓冲区创建时由Vim自动分配的编号，我们可以用:buffer N 命令直接凭编号跳转到一个缓冲区。

2. 用参数列表将缓冲区分组

    参数列表记录了在启动时候作为参数传递给Vim的文件列表。使用命令:args 可以查看参数列表。

    实际上，我们可以在任意时刻改变参数列表的内容，就是说 :args 列表不一定反映启动Vim时所传参数。

    当不带参数运行 :args 命令时，它会打印当前参数列表的内容。另外，我们可以设置参数列表内容，:args {arglist}。 比如：:args abc 就会创建一个名字为abc的缓冲区。

    用Glob模式指定文件，* 用于在当前目录下匹配0个或多个字符，** 也可以通配0个或者多个字符，但它可以递归进入子目录。

    <table>
    <tr>
    <td>Glob模式</td><td>所匹配的文件</td></tr>
<tr>    <td>:args *.*</td><td>index.html <br> app.js</td></tr>
   <tr> <td>:args **/*.js</td><td>app.js <br> lib/framework.js <br> app/contrillers/Mailer.js </td></tr>
<tr>    <td>:args **/*.*</td><td>app.js <br> index.html <br> lib/framework.js <br> lib/theme.css <br>app/controllers/Mailer.js</td>
    </tr>
    </table>

    使用反引号结构指定文件。:args `cat chapters.txt`。Vim会在shell中执行反撇号括起来的命令，然后再把该命令的输出作为 :args 命令的参数。

3. 技巧38 管理隐藏缓冲区

    Vim对别修改过的缓冲区会给予特殊对待，以防止未加保存就意外退出。

    如果修改了缓冲区内容，在没有保存的情况下切换缓冲区，Vim会提示如下错误：No write since last change (add ! to override)。

    根据Vim的提示，在切换缓冲区的命令后添加感叹号(!)，即使当前缓冲区被修改，也会继续切换。切换后，原来的缓冲区被标记为h，表示一个隐藏缓冲区（hidden）。

    如果要保留修改，可以执行:write命令把缓冲区保存到文件；如果想摒弃本次修改，可以执行:edit!，重新从磁盘读取文件覆盖缓冲区内容。当缓冲区内容和磁盘文件一致，再次运行:q命令就不再提示未保存。

    如果会话中有不止一个被修改过的隐藏缓冲区，每次执行:q命令都会激活下一个没有保存的缓冲区。当没有其他窗口和隐藏缓冲区的时候，:q 命令会关闭Vim.

    :qall! 命令会放弃所有的缓冲区修改检查，直接退出Vim。

    :wall 可以将所有改动的缓冲区写入到磁盘文件。

    退出时处理隐藏缓冲区的方式：
    <table>
    <tr><td>:w[rite]</td><td>把缓冲区内容写入磁盘</td></tr>
    <tr><td>:e[edit]!</td><td>把磁盘文件读入缓冲区（回滚所有的修改)</td></tr>
    <tr><td>:qa[ll]!</td><td>关闭所有窗口，摒弃修改且无需警告</td></tr>
    <tr><td>:wa[ll]!</td><td>把所有修改的缓冲区写入磁盘</td></tr>
    </table>

4. 技巧39：将工作区切分成窗口

    在Vim中，窗口是缓冲区的显示区域。我们既可以打开多个窗口，在这些窗口中显示同一个缓冲区，也可以在每个窗口中载入不同的缓冲区。

    &lt;Ctrl-w&gt;s命令可以水平切分当前窗口；
    &lt;Ctrl-w&gt;v命令可以垂直切分当前窗口；

    <table>
    <tr><td>命令</td><td> 用途</td></tr>
    <tr><td>&lt;Ctrl-w&gt;s</td><td> 水平拆分当前窗口，新窗口仍显示当前缓冲区</td></tr>
    <tr><td>&lt;Ctrl-w&gt;v </td><td>垂直拆分当前窗口，新窗口仍显示当前缓冲区</td></tr>
    <tr><td>:sp[lit] {file} </td><td>水平拆分当前窗口，并在新窗口中载入{file}</td></tr>
    <tr><td>:vsp[lit] {file} </td><td>垂直拆分当前窗口，并在新窗口中载入{file}</td></tr>
    </table>

    Vim提供了一些在窗口间切换的命令：
    <table>
    <tr><td>命令</td><td> 用途</td></tr>
    <tr><td>&lt;Ctrl-w&gt;w</td><td> 在窗口间循环切换</td></tr>
    <tr><td>&lt;Ctrl-w&gt;h</td><td> 切换到左边窗口</td></tr>
    <tr><td>&lt;Ctrl-w&gt;j</td><td> 切换到下边窗口</td></tr>
    <tr><td>&lt;Ctrl-w&gt;k</td><td> 切换到上边窗口</td></tr>
    <tr><td>&lt;Ctrl-w&gt;l</td><td> 切换到右边窗口</td></tr>
    </table>

    关闭窗口
    <table>
    <tr><td>Ex命令</td><td>普通模式命令</td><td> 用途</td></tr>
    <tr><td>:clo[se]</td><td> &lt;Ctrl-w&gt;c</td><td> 关闭活动窗口</td></tr>
    <tr><td>:on[ly] </td><td>&lt;Ctrl-w&gt;o</td><td> 只保留活动窗口，关闭其他所有窗口</td></tr>
    </table>

    改变窗口大小
    Vim提供了一些用于改变窗口大小的按键映射项，完整列表请查看:h window-resize,下表给出常用的命令：
    <table>
    <tr><td>命令</td><td>用途</td></tr>
    <tr><td>&lt;Ctrl-w&gt;=</td><td> 使所有的窗口等宽，等高</td></tr>
    <tr><td>&lt;Ctrl-w&gt;_ </td><td>最大化活动窗口的宽度</td></tr>
    <tr><td>&lt;Ctrl-w&gt;| </td><td>最大化活动窗口的高度</td></tr>
    <tr><td>[N]&lt;Ctrl-w&gt;_ </td><td>把活动窗口的宽度设置为N行</td></tr>
    <tr><td>[N}&lt;Ctrl-w&gt;| </td><td>把活动窗口的宽度设置为N行</td></tr>
    </table>

5. 技巧40：用标签也将窗口分组

    在Vim中，标签页可以容纳一系列的窗口，这个和其他的编辑器不同。

    用:tabedit {filename} 命令可以打开一个新的标签页，如果省略了{filename}参数，那么Vim会创建一个新的标签页，里面包含一个空的缓冲区。

    如果当前标签页中包含了不止一个窗口，我们可以用&lt;Ctrl-w&gt;T命令把当前窗口移到一个新的标签页中。

    如果活动标签页中只包含一个窗口，那么:close 命令将关闭此窗口以及包含此窗口的标签页。

    我们也可以用 :tabclose 来关闭当前标签页以及其中所有窗口。

    可以用:tabonly 命令关闭初当前标签以外的所有标签。

    <table>
    命令 用途
    <tr><td>:table[dit] {filename}</td><td> 在新标签页中打开{filename}</td></tr>
    <tr><td>&lt;Ctrl-w&gt;T </td><td>把当前窗口移到一个新标签页</td></tr>
    <tr><td>:tabc[lose] </td><td>关闭当前标签页及其中所有的窗口</td></tr>
    <tr><td>:tabo[nly] </td><td>只保留活动标签页，关闭所有其他标签页</td></tr>
    </table>

    在标签页间切换
    标签页编号从1开始，我们可以使用{N}gt命令在标签页间切换，Vim会跳到指定编号的标签页；如果省略了数字前缀，Vim会跳转到下一个标签页。
    gT命令功能和gt相同，只是跳转方向相反。

    <table>
    <tr><td>Ex命令</td><td> 普通模式命令</td><td> 用途</td></tr>
    <tr><td>:tabn[ext]</td><td> {N}gt</td><td> 切换到编号为{N}的标签页</td></tr>
    <tr><td>:tabn[ext]</td><td> gt</td><td> 切换到下一标签页</td></tr>
    <tr><td>:tabp[revious]</td><td> gT</td><td> 切换到上一标签页</td></tr>
    </table>

    重排标签页
    用 :tabmove [N] 命令可以重新排列标签页。当[N]为0时，当前标签页会被移到开头；如果省略了[N], 当前标签页会被移到结尾。
