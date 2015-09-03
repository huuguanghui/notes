# Practical Vim
## Edit Text at the Speed of Thought

# 第一部分 模式

## 第三章 插入模式

1. 技巧13：在插入模式中及时更改错误

	在插入模式下使用以下命令可以删除你的输入
	<table>
	<tr><td> &lt;Ctrl-h&gt; </td><td> 删除前一个字符，和退格键相同。 </td></tr>
	<tr><td> &lt;Ctrl-w&gt; </td><td> 删除前一个单词 </td></tr>
	<tr><td> &lt;Ctrl-u&gt; </td><td> 删除至行首 </td></tr>
	</table>
	以上命令也可以在Vim命令模式或者shell中使用，效果相同。

2. 技巧14：返回普通模式

	<table>
	<tr><td> 按键 </td><td> 用途  </td></tr>
	<tr><td> &lt;ESC&gt; </td><td> 切换到普通模式。</td></tr>
	<tr><td> &lt;Ctrl-[&gt; </td><td> 切换到普通模式。</td></tr>
	<tr><td> &lt;Ctrl-o&gt; </td><td> 切换到插入-普通模式</td></tr>
	</table>

	当我们处于插入模式，想运行一个普通模式的命令，然后回到插入模式继续输入时，可以使用*插入-普通模式*。

3. 技巧15：不离开插入模式，粘贴寄存器中的文本

	在插入模式中，可以是用\<Ctrl-r\>{register}很方便地粘贴字符，其中{register}是我们想要插入的寄存器的名字。

	删除和复制命令把文本保存到寄存器中，粘贴命令把寄存器里的内容插入到文档中。

4. 技巧16：随时随地做运算

	表达式寄存器可以用来执行一段Vim脚本，并返回结果。

	我们使用 = 表示*表达式寄存器*。

	在插入模式中，使用\<Ctrl-r\>= 就可以访问该寄存器。该命令会在屏幕下方显示一个提示符，在提示符后输入要执行的表达式，然后敲回车键\<CR\>，Vim就会把表达式执行的结果插入到当前输入位置。

5. 技巧19：用替换模式替换已有文本

	用 R 命令可以从普通模式切换到替换模式。

	使用 gR 命令可以从普通模式切换到*虚拟替换模式*（Virtual Replace mode）。在虚拟替换模式中，Vim按照屏幕显示的宽度来替换字符，而不是按照文件中保存的字符进行替换。比如，Tab键会被当成一组空格进行处理。

	Vim也提供了单次版本的替换模式和虚拟替换模式。r{char} 和 gr{char} 命令覆盖一个字符，然后回到普通模式。

6. 技巧17：用字符编码插入不常用的字符

	Vim可以使用字符编码输入任意字符。要输入字符编码，在插入模式中使用\<Ctrl-v\>{code}即可，其中{code}是要插入的字符的编码。

	如果你想知道一个字符的编码，将光标移到该字符上并按下ga即可，在屏幕左下角会显示十进制和十六进制形式的编码。

	<table>
	<tr><td>&lt;Ctrl-v&gt;{123}</td><td>以十进制编码插入字符，必须是三位。</td></tr>
	<tr><td>&lt;Ctrl-v&gt;u{1234}</td><td>以十六进制字符编码插入字符。</td></tr>
	<tr><td>&lt;Ctrl-v&gt;{nondigit}</td><td>按照愿意插入非数字字符</td></tr>
	<tr><td>&lt;Ctrl-k&gt;{cahr1}{char2}</td><td>插入以二合字母{char1}{char2}表示的字符</td></tr>
	</table>

7. 技巧18：用二合字母插入非常用字符

	<table>
	<tr><td>命令</td><td>输出</td></tr>
	<tr><td>&lt;Ctrl-k&gt;12</td><td>½</td></tr>
	<tr><td>&lt;Ctrl-k&gt;?I</td><td>¿</td></tr>
	<tr><td>&lt;Ctrl-k&gt;>></td><td>»</td></tr>
	</table>

	可以使用以下命令获取更多关于二合字母的知识：
	* :h digraph-table
	* :h digraphs-default
	* :digraphs



