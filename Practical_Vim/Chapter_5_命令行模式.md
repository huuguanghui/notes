# Practical Vim
## Edit Text at the Speed of Thought

# 第一部分 模式

## 第五章 命令行模式

1. 技巧27：结识Vim的命令行模式

2. 技巧28：在一行或多个连续行上执行命令

3. 技巧29：使用‘:t’和‘:m’命令复制和移动行

    :copy命令（简写形式:t）可以把一行或者多行从文档的一个部分复制到另一个部分。
    
    :[range]copy{address}
    <table>
    <tr><td>命令</td><td> 用途</td></tr>
    <tr><td>:6t.</td><td> 把第6行拷贝到当前行下方</td></tr>
    <tr><td>:t6 </td><td> 把当前行拷贝到第六行下方</td></tr>
    <tr><td>:t. </td><td> 为当前行创建一个副本，类似于普通模式下的yyp</td></tr>
    <tr><td>:t$ </td><td> 把当前行复制到文本结尾</td></tr>
    <tr><td>:'<,'\>t0 </td><td>把当前行复制到文件开头</td></tr>
    </table>

    :move命令（简写形式:m）可以把一行或者多行从文档的一个部分移动到另一个部分。

