# Practical Vim
## Edit Text at the Speed of Thought

## 第一章 Vim解决问题的方式

1. Vim会记录我们最近的操作，让我们用一次按键就可以重复上次的修改。所以我们要规划好按键动作，使得在重复时能完成一项有用的工作。
2. 命令.可以让我们重复上次的*修改*。
3. 我们每次进入插入模式时，都会形成一次*修改*。从进入插入模式的那一刻起（例如，输入i），直到返回普通模式时为止（输入<Esc>），Vim会记录每一个按键操作。
4. 理想模式：*一键移动，另一键操作。*
5. 在面对重复性工作时候，我们要让移动动作和修改都能够重复，这样就可以达到一个最佳编辑模式。 
6. 可重复的操作以及如何回退

<table>
<tr>
<td>目的</td>
<td>操作</td>
<td>重复</td>
<td>回退</td>
</tr>
<tr>
<td>做出一个修改</td>
<td>{edit}</td>
<td>.</td>
<td>u</td>
</tr>
<tr>
<td>在行内查找下一个指定字符</td>
<td>f{char}/t{char}</td>
<td>;</td>
<td>,</td>
</tr>
<tr>
<td>在行内查找上一个指定字符</td>
<td>F{char}/T{char}</td>
<td>;</td>
<td>,</td>
</tr>
<tr>
<td>在文档中查找下一处匹配项</td>
<td>/pattern<CR></td>
<td>n</td>
<td>N</td>
</tr>
<tr>
<td>在文档中查找上一处匹配项</td>
<td>?pattern<CR></td>
<td>n</td>
<td>N</td>
</tr>
<tr>
<td>执行替换</td>
<td>:s/target/replacement</td>
<td>&</td>
<td>u</td>
</tr>
<tr>
<td>执行一系列修改</td>
<td>qx{changes}q</td>
<td>@x</td>
<td>u</td>
</tr>
</table>

# 第一部分 模式

## 第二章 普通模式

## 第三章 插入模式
## 第四章 可视模式
## 第五章 命令模式
