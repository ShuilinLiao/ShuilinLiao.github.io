

---

title: 用Rmarkdown生成简历
date: 2020-11-17 
author: 廖水林

---

### 用Rmarkdown生成简历
- 将Y叔发表在GitHub上的代码用git clone下来
```
git clone https://github.com/GuangchuangYu/cv.git
```
- 为避免出现函数的冲突，建议将index.Rmd中select和rename函数前**声明所属包**，即有关部分将改成以下代码：
```R
xx[[i]] <- dplyr::select(y, -c(start, end)) %>%
      dplyr::rename(start=start2, end=end2)
```
- 教育经历，工作经历，发表的文章等都是一个一个的block，而简历正由这些block组成。这些信息全都存在`position.csv`中。`index.Rmd`也有部分个人信息。因此把`position.csv`和`index.Rmd`内的有关信息照着格式更改成自己的，不需要填写的用NA替代。不需要的block可直接删除（和相关代码一并删除）。
- 在按照模板在csv修改内容的时候，不需要的行/列**不要**用清除内容方式，而**直接进行行/列的删除**，以免在后续代码的运行中空白行/列产生干扰
- 在R命令行或者Rstudio中的脚本中输入以下命令：
  ```R
  rmarkdown::render("index.Rmd")
  ```
- 随即会生成`.html`格式的简历，另存为pdf即可。
- 在csv中把`position.csv`信息更改好之后，再用文本编辑器（此处为Notepad++）将编码方式换成UTF-8编码（此时再用csv打开会出现乱码），并将代码中关于读取positions_CN.csv的部分改成以下内容：
  ```R
  position_data <- read.csv('positions_CN.csv',encoding = 'UTF-8') %>% 
    mutate_all(fill_nas) %>% 
    arrange(order, desc(end)) %>% 
    mutate(id = 1:n()) %>% 
    nest(data = c(-id, -section)) # read.csv打开，并增加encoding = 'UTF-8'参数
  ```

### 参考链接
[Y叔笔记](https://mp.weixin.qq.com/s/Dz2fa83O_P5QPD8VLR7DRQ)