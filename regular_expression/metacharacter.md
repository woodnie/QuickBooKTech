## metacharacter {#metacharacter}

**表达式全集**

正则表达式有多种不同的风格。下表是在 PCRE 中元字符及其在正则表达式上下文中的行为的一个完整列表

| **字符** | **描述** |
| --- | --- |
| **\** | 将下一个字符标记为一个特殊字符、或一个原义字符、或一个向后引用、或一个八进制转义符。例如， &quot; n &quot; 匹配字符 &quot; n &quot; 。 &quot; \n &quot; 匹配一个换行符。串行 &quot; \\ &quot; 匹配 &quot; \ &quot; 而 &quot; \( &quot; 则匹配 &quot; ( &quot; 。 |
| **^** | 匹配输入字符串的开始位置。如果设置了 RegExp 对象的 Multiline 属性， ^ 也匹配 &quot; \n &quot; 或 &quot; \r &quot; 之后的位置。 |
| **$** | 匹配输入字符串的结束位置。如果设置了 RegExp 对象的 Multiline 属性， $ 也匹配 &quot; \n &quot; 或 &quot; \r &quot; 之前的位置。 |
| ***** | 匹配前面的子表达式零次或多次。例如， zo* 能匹配 &quot; z &quot; 以及 &quot; zoo &quot; 。 * 等价于 {0,} 。 |
| **+** | 匹配前面的子表达式一次或多次。例如， &quot; zo+ &quot; 能匹配 &quot; zo &quot; 以及 &quot; zoo &quot; ，但不能匹配 &quot; z &quot; 。 + 等价于 { 1,} 。 |
| **?** | 匹配前面的子表达式零次或一次。例如， &quot; do(es)? &quot; 可以匹配 &quot; does &quot; 或 &quot; does &quot; 中的 &quot; do &quot; 。 ? 等价于 { 0,1} 。 |
| **{** **_n_** **}** | _n_ 是一个非负整数。匹配确定的 _n_ 次。例如， &quot; o{2} &quot; 不能匹配 &quot; Bob &quot; 中的 &quot; o &quot; ，但是能匹配 &quot; food &quot; 中的两个 o 。 |
| **{** **_n_** **,}** | _n_ 是一个非负整数。至少匹配 _n_ 次。例如， &quot; o{2,} &quot; 不能匹配 &quot; Bob &quot; 中的 &quot; o &quot; ，但能匹配 &quot; foooood &quot; 中的所有 o 。 &quot; o{1,} &quot; 等价于 &quot; o+ &quot; 。 &quot; o{0,} &quot; 则等价于 &quot; o* &quot; 。 |
| **{** **_n_** **,** **_m_** **}** | _m_ 和 _n_ 均为非负整数，其中 _n_ &lt;= _m_ 。最少匹配 _n_ 次且最多匹配 _m_ 次。例如， &quot; o{1,3} &quot; 将匹配 &quot; fooooood &quot; 中的前三个 o 。 &quot; o{0,1} &quot; 等价于 &quot; o? &quot; 。请注意在逗号和两个数之间不能有空格。 |
| **?** | 当该字符紧跟在任何一个其他限制符（ *,+,? ， { _n_ } ， { _n_ ,} ， { _n_ , _m_ } ）后面时，匹配模式是非贪婪的。非贪婪模式尽可能少的匹配所搜索的字符串，而默认的贪婪模式则尽可能多的匹配所搜索的字符串。例如，对于字符串 &quot; oooo &quot; ， &quot; o+? &quot; 将匹配单个 &quot; o &quot; ，而 &quot; o+ &quot; 将匹配所有 &quot; o &quot; 。 |
| **.** | 匹配除 &quot; \ _n_ &quot; 之外的任何单个字符。要匹配包括 &quot; \ _n_ &quot; 在内的任何字符，请使用像 &quot; (.|\n) &quot; 的模式。 |
| **(pattern)** | 匹配 pattern 并获取这一匹配。所获取的匹配可以从产生的 Matches 集合得到，在 VBScript 中使用 SubMatches 集合，在 JScript 中则使用 $0 … $9 属性。要匹配圆括号字符，请使用 &quot; \( &quot; 或 &quot; \) &quot; 。 |
| **(?:pattern)** | 匹配 pattern 但不获取匹配结果，也就是说这是一个非获取匹配，不进行存储供以后使用。这在使用或字符 &quot; (|) &quot; 来组合一个模式的各个部分是很有用。例如 &quot; industr(?:y|ies) &quot; 就是一个比 &quot; industry|industries &quot; 更简略的表达式。 |
| **(?=pattern)** | 正向肯定预查，在任何匹配 pattern 的字符串开始处匹配查找字符串。这是一个非获取匹配，也就是说，该匹配不需要获取供以后使用。例如， &quot; Windows(?=95|98|NT|2000) &quot; 能匹配 &quot; Windows2000 &quot; 中的 &quot; Windows &quot; ，但不能匹配 &quot; Windows3.1 &quot; 中的 &quot; Windows &quot; 。预查不消耗字符，也就是说，在一个匹配发生后，在最后一次匹配之后立即开始下一次匹配的搜索，而不是从包含预查的字符之后开始。 |
| **(?!pattern)** | 正向否定预查，在任何不匹配 pattern 的字符串开始处匹配查找字符串。这是一个非获取匹配，也就是说，该匹配不需要获取供以后使用。例如 &quot; Windows(?!95|98|NT|2000) &quot; 能匹配 &quot; Windows3.1 &quot; 中的 &quot; Windows &quot; ，但不能匹配 &quot; Windows2000 &quot; 中的 &quot; Windows &quot; 。预查不消耗字符，也就是说，在一个匹配发生后，在最后一次匹配之后立即开始下一次匹配的搜索，而不是从包含预查的字符之后开始 |
| **(?&lt;=pattern)** | 反向肯定预查，与正向肯定预查类似，只是方向相反。例如， &quot; (?&lt;=95|98|NT|2000)Windows &quot; 能匹配 &quot; 2000Windows &quot; 中的 &quot; Windows &quot; ，但不能匹配 &quot; 3.1Windows &quot; 中的 &quot; Windows &quot; 。 |
| **(?&lt;!pattern)** | 反向否定预查，与正向否定预查类似，只是方向相反。例如 &quot; (?&lt;!95|98|NT|2000)Windows &quot; 能匹配 &quot; 3.1Windows &quot; 中的 &quot; Windows &quot; ，但不能匹配 &quot; 2000Windows &quot; 中的 &quot; Windows &quot; 。 |
| **x|y** | 匹配 x 或 y 。例如， &quot; z|food &quot; 能匹配 &quot; z &quot; 或 &quot; food &quot; 。 &quot; (z|f)ood &quot; 则匹配 &quot; zood &quot; 或 &quot; food &quot; 。 |
| **[xyz]** | 字符集合。匹配所包含的任意一个字符。例如， &quot; [abc] &quot; 可以匹配 &quot; plain &quot; 中的 &quot; a &quot; 。 |
| **[^xyz]** | 负值字符集合。匹配未包含的任意字符。例如， &quot; [^abc] &quot; 可以匹配 &quot; plain &quot; 中的 &quot; p &quot; 。 |
| **[a-z]** | 字符范围。匹配指定范围内的任意字符。例如， &quot; [a-z] &quot; 可以匹配 &quot; a &quot; 到 &quot; z &quot; 范围内的任意小写字母字符。 |
| **[^a-z]** | 负值字符范围。匹配任何不在指定范围内的任意字符。例如， &quot; [^a-z] &quot; 可以匹配任何不在 &quot; a &quot; 到 &quot; z &quot; 范围内的任意字符。 |
| **\** **b** | 匹配一个单词边界，也就是指单词和空格间的位置。例如， &quot; er\b &quot; 可以匹配 &quot; never &quot; 中的 &quot; er &quot; ，但不能匹配 &quot; verb &quot; 中的 &quot; er &quot; 。 |
| **\** **B** | 匹配非单词边界。 &quot; er\B &quot; 能匹配 &quot; verb &quot; 中的 &quot; er &quot; ，但不能匹配 &quot; never &quot; 中的 &quot; er &quot; 。 |
| **\** **cx** | 匹配由 x 指明的控制字符。例如， \ cM 匹配一个 Control-M 或回车符。 x 的值必须为 A-Z 或 a-z 之一。否则，将 c 视为一个原义的 &quot; c &quot; 字符。 |
| **\** **d** | 匹配一个数字字符。等价于 [0-9] 。 |
| **\** **D** | 匹配一个非数字字符。等价于 [^0-9] 。 |
| **\** **f** | 匹配一个换页符。等价于 \ x0c 和 \ cL 。 |
| **\** **n** | 匹配一个换行符。等价于 \ x0a 和 \ cJ 。 |
| **\** **r** | 匹配一个回车符。等价于 \ x0d 和 \ cM 。 |
| **\** **s** | 匹配任何空白字符，包括空格、制表符、换页符等等。等价于 [ \f\n\r\t\v] 。 |
| **\** **S** | 匹配任何非空白字符。等价于 [^ \f\n\r\t\v] 。 |
| **\** **t** | 匹配一个制表符。等价于 \ x09 和 \ cI 。 |
| **\** **v** | 匹配一个垂直制表符。等价于 \ x0b 和 \ cK 。 |
| **\** **w** | 匹配包括下划线的任何单词字符。等价于 &quot; [A-Za-z0-9_] &quot; 。 |
| **\** **W** | 匹配任何非单词字符。等价于 &quot; [^A-Za-z0-9_] &quot; 。 |
| **\** **x** **_n_** | 匹配 _n_ ，其中 _n_ 为十六进制转义值。十六进制转义值必须为确定的两个数字长。例如， &quot; \x41 &quot; 匹配 &quot; A &quot; 。 &quot; \x041 &quot; 则等价于 &quot; \x04&amp;1 &quot; 。正则表达式中可以使用 ASCII 编码。 . |
| **\** **_num_** | 匹配 _num_ ，其中 _num_ 是一个正整数。对所获取的匹配的引用。例如， &quot; (.)\1 &quot; 匹配两个连续的相同字符。 |
| **\** **_n_** | 标识一个八进制转义值或一个向后引用。如果 \ _n_ 之前至少 _n_ 个获取的子表达式，则 _n_ 为向后引用。否则，如果 _n_ 为八进制数字（ 0-7 ），则 _n_ 为一个八进制转义值。 |
| **\** **_nm_** | 标识一个八进制转义值或一个向后引用。如果 \ _nm_ 之前至少有 _nm_ 个获得子表达式，则 _nm_ 为向后引用。如果 \ _nm_ 之前至少有 _n_ 个获取，则 _n_ 为一个后跟文字 _m_ 的向后引用。如果前面的条件都不满足，若 _n_ 和 _m_ 均为八进制数字（ 0-7 ），则 \ _nm_ 将匹配八进制转义值 _nm_ 。 |
| **\** **_nml_** | 如果 _n_ 为八进制数字（ 0-3 ），且 _m_ _和_ _l_ 均为八进制数字（ 0-7 ），则匹配八进制转义值 _nm_ l 。 |
| **\** **u** **_n_** | 匹配 _n_ ，其中 _n_ 是一个用四个十六进制数字表示的 Unicode 字符。例如， \ u00A9 匹配版权符号（ © ）。 |