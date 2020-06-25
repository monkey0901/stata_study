# 第二章  Stata入门

## 2.3  Stata操作实例

- **打开数据文件**

  ``` 
  use file_path,clear  
  (clear用于清空内存中的数据)
  ```
  
- **审视数据**

  观看数据集中的变量名、标签等

  ```
  describe
  ```

  查看部分数据：

  ```Stata
  list s lnw in 1/5
  # 观测第1-5个数据
  ```

  逻辑关系定义数据集子集：

  ```Stata
  list s lnw if s >= 16
  ```

  删除/保留观测值：

  ```Stata
  drop/keep if s >= 16
  ```

  按照变量 s 升/降序排列：

  ```Stata
  sort s/gsort -s
  ```

  

- **画图**

  直方图，s 为横轴且组宽为1，frequency为纵轴

  ```Stata
  histogram s,width(1) frequency
  ```

  帮助文档：

  ```Stata
  help histogram
  ```

  散点图，其中lnw为纵轴，s为横轴：

  ```Stata
  scatter lnw s
  ```

- **统计分析**

  样本描述性数据：

  ```stata
  summarize s
  ```

  样本的累积分布函数：

  ```stata
  tabulate s
  ```

  显示变量之间的相关系数，其中sig表示相关性系数的显著水平：

  ```stata
  pwcorr lnw s expr,sig star(.05)
  ```
  
- **生成新变量**

  ```stata
  gennerate lns = log(s)
  ```

  重命名：

  ```stata
  rename colleg college
  ```

  更改变量的内容：

  ```stata
  replace college = (s >= 15)
  ```

- **Stata的计算器功能**

  ```stata
  display log(2)
  ```

  注：stata中log为ln

- **调用命令与终止命令**

- **Stata日志**

  ```stata
  log using today
  ```

  

  

## 2.4 Stata命令库的更新

- **方法一**

  更新Stata命令数据库：

  ```stata
  update all
  ```

- **方法二**
  
  从SSC下载Stata程序命令：
  
  ```stata
  ssc install newcommand
  ```
  
  