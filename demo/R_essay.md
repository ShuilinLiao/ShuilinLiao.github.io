---
title: Essays
date: 2020-10-15 19:17:56
categories: 
- Essays
tags:
- 
---

一个demo。
<!-- more -->

# R语言

## 数据塑性
### 过滤0值大于一定比例的行/列

```R
dat %>% filter(apply(dat, 1, function(x) {sum(x != 0)/length(x)}) > occurrence) 
dat[apply(dat,1,function(a){length(a[a!=0])/ncol(dat) > 0.2 }),] 
```

### 找出重复的名称
repeat_name <- rownames(matrix.data)[duplicated(rownames(matrix.data))]

###  根据某一列对数据进行运算
dat %>% group_by(tax)  %>% summarise_all(sum) 