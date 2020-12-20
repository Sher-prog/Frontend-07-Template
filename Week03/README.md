# 学习笔记
## 使用LL算法构建AST

#### 算法
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




#### 技巧
1. 新api:fill用法
2. 同余特征：一维数字表示二维矩阵技巧——100*y+x(y外层循环，x内层循环)
3. js数组：天然的队列（queue）、栈（stack）
4. 搜索算法中重要，通用性特别好
5. 搜索算法中重要，通用性特别好

#### 寻路问题
1. 在地图上指定起点，终点，找到一条路径从起点走到终点
2. 问题简单化，分布实施，从而形成一个集合的点的过程
【从起点能走到哪去，1、从起点第一步能走到哪里去——相邻点「上下左右四个点」；】
3. 搜索算法中重要，通用性特别好
4. 我们采用(push入队 shift出队)两种方法；

#### 数组知识点回忆
1. js数组：天然的队列（queue）、栈（stack）
(shift,unshift)很少用、性能会变低,(push,pop) 栈行为
2. push:在数组的末属添加一个或多个元素
3. pop:删除数组中的最后一个元素
4. shift:删除数组中的第一个元素
5. unshift:在数组的前端添加一个或多个元素
6. 队列：先进先出，后进后出
7. 栈：后进先出
8. 整体代码结构寻路中path
搜索的差异（1）、深度优先搜索和广度优先搜索就差在一个“数据结构”上面；（2）、A*搜索，无非就是把queue变成了一个排序的接口


#### 总结相关功能函数留存方便下次使用
1. 搜索
2. sleep
3. 一维数字表示二维矩阵技巧
4. 克隆