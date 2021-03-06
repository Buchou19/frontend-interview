## 1. 什么是编译?

就是将高级语言（源语言）翻译成汇编语言或机器语言（目标语言）的过程。

## 2. 编译器的结构

词法分析——语法分析——语义分析——中间代码生成——机器无关代码优化——目标代码生成——机器相关代码优化

## 3. 文法

文法**G** = { 终结符集合，非终结符集合，推导规则（或产生式集合），开始符号 }

经过词法分析后，按照**文法**定义的**规则**，可以由非终结符**推导**为最终的终结符，或把所有非终结符**规约**为最终的非终结符，都视为符合这个**文法规则**。文法可以生成标识符、表达式等（即生成**语言**）......

如果根据结果可以生成两种或两种以上的分析树，那么就认为它是有二义性的。

## 4. 词法分析

从左向右逐行扫描源代码中的字符，识别各个单词并确定单词种类：

**token：< 种别码，属性值 >** 

种别有关键字（一词一码）、标识符（多词一码）、常量、运算符等......

**正则表达式**可以方便的表示语言，对于任何**正则文法G**，都存在定义同一语言的正则表达式。

正则文法能描述程序设计语言的多数单词。

**NFA**、**DFA**了解...

关键字、标识符、常量、运算符、注释等都有对应的正则文法来识别，识别完成后生成token。

词法分析阶段也可以检测到错误，根据规则引导进入错误处理程序。

## 5. 语法分析

语法分析器从词法分析器输出的token序列中识别出各类短语，并**构造出语法分析树**。

我认为跟词法分基本析没有什么区别，无非是自顶向下（推导）或自底向上（规约）来判断这个句子是否属于这个语言，如程序、语句、表达式。

至于**词法分析和语法分析**的**区别**如下：

词法分析的时候用正则表达式（也就是正则文法，3型文法，范围最小）就可以描述。但是在语法分析的时候，就得用上下文无关文法（2型文法）来描述。语法分析中，很多东西是不能用正则表达式来描述的，因此得用上下文无关语法。

## 6. 语法制导翻译

语义翻译 === 语义分析 + 中间代码生成

语法制导翻译 === 语法分析 + 语义分析 + 中间代码生成

**语法制导翻译 **使用上下文无关文法来引导对语言的翻译，是一种面向文法的翻译技术。

**语法制导定义SDD**是对上下文无关文法的推广：

1. 将每个文法符号和一个语义属性集合相关联
2. 将每个产生式和一组语义规则相关联，用来计算该产生式中各文法符号的属性值

自己理解：将一些语义操作及翻译的动作嵌入在文法规则中。

**语法制导翻译方案SDT**是在产生式右部中嵌入了程序片段（称为语义动作）的上下文无关文法，SDT可以看作是SDD的具体实施方案。