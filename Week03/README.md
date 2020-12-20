# 学习笔记
## 使用LL算法构建AST
1. AST：叫做抽象语法树；
2. 代码在计算机分析过程中：1、编程语言分词；2、把词构成层层相嵌套的语法树的一个树形结构；3、如何去解析代码去执行；
3. 构建AST抽象语法树的过程又被叫做“语法分析”；
4. 最著名的“语法分析算法”核心思想有两种：1、LL算法（L：Left）；2、LR算法；
5. LL（Left Left）算法：从左到右扫描，从左到右规约[什么是扫描？什么是规约？]
6. 四则运算分析：
（1）词法定义：有效的Token有数字（TokenNumber-[0,1,2,3,4,5,6,7,8,9]）和运算符（Operrator-[+、-、*、/]），其余无效换行等操作（Whitespace-<SP>,LineTerminator-<LF><CR>）
（2）语法定义：
AdditiveExpression 加法运算：加法是由左右两个乘法组成的,且加法可以进行连加。重复自身的一个序列。
（定义里有一个递归的产生式结构，在做产生式处理无限的列表一个常用的手法）
MultiplicativeExpression 乘法运算：一个单独的数字，认为它是一种特殊的乘法（只有一项的乘法）
只有乘号：认为是一种特殊的加法（只有一项的加法）
比较方便我们去递归的定义一个表达式

终结符（TerminalSymbol）：<EOF><+><-><*></><Number>直接从词法扫描出来的.其余的是
非终结符（NoneTerminalSymbol）：拿终结符的组合定义出来的

最后我们认为能处理的表达式（Expression）就是一个“加法表达式”，后面引入特殊符号EOF（End of File）：不是一个真实可见的字符，但是我们的语法需要一个终结（标识所有源代码的结束），常常被用在计算机里面表示各种终结的场景。

```
<Expression>::=
    <AdditiveExpression><EOF>

<AdditiveExpression>::=
    <MultiplicativeExpression>
    |<AdditiveExpression><+><MultiplicativeExpression>    
    |<AdditiveExpression><-><MultiplicativeExpression>   

用乘号或者除号相连接的Number的序列
<MultiplicativeExpression>::=
    <Number>
    |<MultiplicativeExpression><*><Number>     
    |<MultiplicativeExpression></><Number>     
}
```

（3）语法分析：加法为例——总是从输入的序列里看拿到的是什么东西，

```
<AdditiveExpression>::=
    <Number>
    |<MultiplicativeExpression><*><Number>     
    |<MultiplicativeExpression></><Number>  
    |<AdditiveExpression><+><MultiplicativeExpression>    
    |<AdditiveExpression><-><MultiplicativeExpression>    
}
```

#### 数组知识点回忆
1. 正则表达式；
2. 相关API；