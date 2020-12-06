
# 学习笔记


## 优秀的工程师

1. 领域知识
2. 能力、潜力
3. 成就
4. 职业规划


## TicTacToe

1. `week01/` 代表第一周作业提交目录，以此类推。
2. 请在对应周的目录下新建或修改自己的代码作业。
2. 每周均有一个 `NOTE.md` 文档，你可以将自己当周的学习心得以及做题过程中的思考记录在该文档中。

## 异步函数

1. callback
2. Promist
3. async/await
4. generator/yield

## 编程技巧
 
1. 拷贝

(1)
```
let pattern = [[0, 0, 0], [0, 0, 0], [0, 0, 0]]
let copy = JSON.parse(JSON.stringify(pattern))
```


(2)
```
let pattern = [0, 0, 0]
let copy = Object.create(pattern)
```

2. label跳出循环

```
outer: for(let i = 0; i < 3; i++) {
    for(let j = 0; j < 3; j++) {
        break outer
    }
}
```

## 问题记录
【问题】出现死循环

【原因】写代码不够仔细，对老师的讲解没有吃透。

【解决】写代码1小时，找错3小时。哎呀妈呀，脑瓜疼。


### 学习复盘
1. 没有安排足够的时间来学习，导致理解不足；
2. 对TicTacToe AI部分还没理解透彻；
3. async/await 课下加强练习；
4. 补全追溯法信息，时间仓促没好好整理；
5. 加强解偶功能函数的能力，否则代码一团糟，且维护成本高；
6. 避免眼高手低；

## 注意事项 【补录职业生涯规划】
