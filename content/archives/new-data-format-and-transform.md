---
title: 121.5_R_data-format and exchange
tags:
  - R
date: 2021-06-09 11:46:49
---
<!--more-->

数据的存储不仅要方便人录入也要方便程序进行阅读。

数据有许多存储格式，在此我探究了那些数据存储的格式和一些转换方法。提醒我们关注在输入数据时遵守一些规则，使程序在读取时不会报错。

![](/img/image-20211111213248387.png)

update

## R语言数据帧

在导入数据之前，先了解R中数据测存在方式。

数据帧是一个表或二维数组状结构，其中每一列包含一个可变的值和每行包含一组来自每列的值。

下面是一个数据帧的特征。

+ 列名应为非空。
+ 行的名称应该是唯一的。
+ 存储在数据帧中的数据可以是数字，因子或字符类型。
+ 每列应包含数据项的数量相同。

 

### 创建数据帧

 

\# Create the data frame.

emp.data <- data.frame(

emp_id = c (1:5), 

emp_name = c("Rick","Dan","Michelle","Ryan","Gary"),

salary = c(623.3,515.2,611.0,729.0,843.25), 

start_date = as.Date(c("2012-01-01","2013-09-23","2014-11-15","2014-05-11","2015-03-27")),

stringsAsFactors=FALSE

)

\#数据按照列输入，相同属性在同一列；列标题相同。

\# Print the data frame.    

print(emp.data)

 

### 得到数据帧的结构

数据帧的结构可以通过使用函数 str()了解到

str(emp.data)

 

'data.frame':  5 obs. of 4 variables:

 $ emp_id  : int 1 2 3 4 5

 $ emp_name : chr "Rick" "Dan" "Michelle" "Ryan" ...

 $ salary  : num 623 515 611 729 843

 

### 数据在数据帧摘要

print(summary(emp.data)) 

 

### 从数据帧中提取数据

#### *使用列名称从数据帧提取特定的列*

result <- data.frame(emp.data$emp_name,emp.data$salary)

\# 提出emp.data.emp_name和emp.data.salary

 

result <- emp.data[1:2,]

\#提出第一行到第二行的所有列

 emp_id emp_name salary start_date

1   1   Rick 623.3 2012-01-01

2   2   Dan 515.2 2013-09-23

 

#### *提取第**3**和第**5**行与第**2**和第**4**列*

result <- emp.data[c(3,5),c(2,4)]

\# 列表中的（3,2）和（5,4）位置的数据

\#先提出行，再提出列

 

### 扩展数据帧

#### *添加列*

只需使用新列名称添加列向量。为每个研究对象添加新的属性。

新列：数据，数据，数据

emp.data$dept <- c("IT","Operations","IT","HR","Finance")

#### *添加行*

要添加更多的行永久到现有的数据帧，我们需要引入**新的行中的结构要与现有数据帧相同**，并使用 rbind()函数。

即加入一个研究对象，但是他的属性要和原来的形同。


\# Create the first data frame.

emp.data <- data.frame(

emp_id = c (1:5), 

emp_name = c("Rick","Dan","Michelle","Ryan","Gary"),

salary = c(623.3,515.2,611.0,729.0,843.25), 

start_date = as.Date(c("2012-01-01","2013-09-23","2014-11-15","2014-05-11","2015-03-27")),

dept=c("IT","Operations","IT","HR","Finance"),

stringsAsFactors=FALSE

)

 

\# Create the second data frame

emp.newdata <-     data.frame(

emp_id = c (6:8), 

emp_name = c("Rasmi","Pranab","Tusar"),

salary = c(578.0,722.5,632.8), 

start_date = as.Date(c("2013-05-21","2013-07-30","2014-06-17")),

dept = c("IT","Operations","Fianance"),

stringsAsFactors=FALSE

)

 

\# Bind the two data frames.

emp.finaldata <- rbind(emp.data,emp.newdata)

print(emp.finaldata)

 

可以看成合并两个研究对象的数据到一个表。

 

<hr>

使用R处理导入的数据有时候需要程序包的使用。

## R语言软件包

R程序包是R里面的函数，编译后的代码和样本数据的集合。它们是存储在在R环境下的 “library” 目录下。默认情况下R安装过程中会安装一组/些软件包。更多的包以后添加，当需要为某些特定目的使用时。当我们开始R控制台，只有默认默认情况下安装的包可用。已经安装了哪些其它包必须显式地装入要使用R程序，当在需要使用它们的时候。

 

R中语言，所有的包列在 R Packages.

 

### 检查可用R程序包

#### *获取包含R程序包库位置*

.libPaths()

#### *获取所有安装的软件包列表*

library()

#### *获取当前在**R**环境中加载的所有软件包*

search()

#### *安装一个新的软件包*

有两种方法来添加新的R语言软件包。一种是直接从CRAN目录中进行安装，另一个是在将软件包下载到本地系统，并手动安装。

##### 直接从CRAN安装

下面的命令直接从CRAN网页获取包，并在R语言环境中安装软件包。可能会提示您选择一个最近的镜像。选择一个适合自己的位置。

 install.packages("Package Name")

 

\# Install the package named "XML".

 install.packages("XML")

 

##### 手动安装软件包

[下载]('https://cran.r-project.org/web/packages/available_packages_by_name.html')需要的软件包。保存该包在一个合适的位置，在本地系统中的一个 .zip 文件。

 

现在可以运行下面的命令在R环境中安装该软件包。

install.packages(file_name_with_path, repos = NULL, type="source")

 

\# Install the package named "XML"

install.packages("E:/XML_3.98-1.3.zip", repos = NULL, type="source")

#### *装载软件包到库*

在代码中使用一个软件包之前，它必须先加载到当前R环境。还需要加载一个已经以前安装的软件包，但在目前的环境中没有软件包。

 

一个软件包使用下面的命令加载：

library("package Name", lib.loc="path to library")

 

\# Load the package named "XML"

install.packages("E:/XML_3.98-1.3.zip", repos = NULL, type="source")

 

## R数据重塑

R语言中的数据重塑是关于变化的数据分为行和列的方式。大多数R地数据处理的时候是通过将输入的数据作为一个数据帧进行。这是很容易提取一个数据帧的行和列数据，但在某些情况，当我们需要的数据帧的格式是不同的来自收到它的格式。 R有许多函数用来分割，合并，改变行列，反之亦然在一个数据帧。

### 接合列和行中的数据帧

我们可以加入多个向量创建使用 cbind()函数返回数据帧。

同时，我们也可以使用 rbind()函数合并两个数据帧。

<u>简单来说,cbind()可以给所有人加个属性，rbind（）加个人和他的所有所学（加一排在后面）</u>



#`Create vector objects.`

`city <- c("Tampa","Seattle","Hartford","Denver")`

`state <- c("FL","WA","CT","CO")`

`zipcode <- c(33602,98104,06161,80294)`

`\# Combine above three vectors into one data frame.`

`addresses <- cbind(city,state,zipcode)`

`\# Print a header.`

`cat("# # # # The First data framen")` 

`\# Combine rows form both the data frames.`

`all.addresses <- rbind(addresses,new.address)`

 

### 合并数据帧

我们可以通过使用 merge()函数合并两个数据帧。该数据帧必须在其上合并发生相同的列名

### 熔化和转换

melt（）：将属性那一列容忍对象，变成属性变量·值的的形式

cast（）：将属性变量·值重构为一列属性

我们认为数据集被称为 ships 出现在库被称为 "MASS".

``library(MASS)`

`print(ships)`

#### *融化数据*

 

mo拆分数据进行重组，将除类型和年份以外的所有列转换为多行展示。

 

`lten.ships <- melt(ships, id = c("type","year"))`

`print(molten.ships)`

#### *转换数据*

我们可以将被拆分的数据转换为一种新形式，使用cast()函数创建每年每种类型的船的总和。

我们可以转化数据转换成在创建每种类型的 ships 每年的汇总的新形式。它是通过使用 case()函数。

 

 

 

## R语言处理CSV文件

### 获取和设置工作目录

 

可以获得 R 的工作空间目录指向使用 getwd()函数。也可以使用 setwd()函数来设置一个新的工作目录。

\`# Get and print current working directory.`

`print(getwd())`

`` 

`\# Set current working directory.`

`setwd("/web/com")`

`` 

`\# Get and print current working directory.`

`print(getwd())`

### 输入为CSV文件

CSV文件是以一个以列值是用逗号分隔的文本文件。让我们考虑目前命名文件：input.csv 的文件中的以下数据。

 

可以使用Windows记事本通过复制创建该文件，并粘贴这些数据到记事本中。使用另存为所有文件(*.*) ，在记事本选项将文件保存为：input.csv。

 

id,name,salary,start_date,dept

1,Rick,623.3,2012-01-01,IT

2,Dan,515.2,2013-09-23,Operations

3,Michelle,611,2014-11-15,IT

4,Ryan,729,2014-05-11,HR

,Gary,843.25,2015-03-27,Finance

6,Nina,578,2013-05-21,IT

7,Simon,632.8,2013-07-30,Operations

8,Guru,722.5,2014-06-17,Finance

 

### 读一个CSV文件

以下是 read.csv()函数的一个简单的例子，它读取在当前工作目录的可用的 CSV 文件：

`data <- read.csv("input.csv")`

`print(data)`

 

### 分析CSV文件

默认情况下，read.csv()函数给出一个数据帧的输出。这可以容易地确认如下。此外，我们可以检查列和行的数。

 

`data <- read.csv("input.csv")`

`` 

`print(is.data.frame(data))`

`print(ncol(data))`

`print(nrow(data))`

 

#### *获得的最高薪水*

`sal <- max(data$salary) #从data使用max函数访问salary，输出最大值给sal。`

 

#### *找最大薪水的人的细节信息*

`retval <- subset(data, salary == max(salary))`

`\#从data使用subset函数访问salsry中值为max（salary）的对象，输出对象的细节信息给retval。`

`` 

`retval <- subset( data, dept == "IT")`

同理，访问data之中IT的相关信息

 

就像人找表一样。

### 写入到CSV文件

R语言能够从现有的数据帧来创建 csv 文件。write.csv()函数用于创建CSV文件。这个文件会在工作目录中创建。

 

\`# Create a data frame.`

`data <- read.csv("input.csv")`

`retval <- subset(data, as.Date(start_date) > as.Date("2014-01-01"))`

`` 

`\# Write filtered data into a new file.`

`write.csv(retval,"output.csv")`

`newdata <- read.csv("output.csv")`

`print(newdata)`

`` 

读取，写入，再读取检验。

`write.csv(retval,"output.csv", row.names=FALSE)`

`\# 关闭行源id`
