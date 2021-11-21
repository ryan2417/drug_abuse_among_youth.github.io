Data
================

#### 1 个人体征

包括年纪，性别，种族，地区

-   Q8 之前 (问题序号)  
-   1 (Final Product)

#### 2 Car

包括酒驾，安全带

-   Q8 \~ Q11  
-   2

#### 3 暴力行为

包括武器携带，校园安全，校园性暴力，校园暴力

-   Q12 \~ Q 24  
-   2

#### 4 自杀，抑郁，个人心理健康状况

-   Q25 \~ Q29  
-   2

#### 5 吸烟情况

包括烟草，电子烟，口嚼烟，戒烟

-   Q30 \~ Q39  
-   2

#### 6 喝酒情况

-   Q40 \~ Q44  
-   2

#### 7 毒品使用情况

包括大麻，冰毒，被迫售毒等

-   Q45 \~ Q57  
-   3

#### 8 性行为

包括艾滋，性行为和毒品联动行为

-   Q58 \~ Q64 性行为  
-   Q84 \~ Q85 艾滋，性传播疾病  
-   Q65 \~ Q66 性向（不管）
-   2

#### 9 健康饮食相关

包括绿食,早饭，胡萝卜，沙拉

-   Q69 \~ Q77 （都不管）
-   2

#### 10 个人健康运动相关

包括运动健身，看电视等

-   Q78 \~ Q83  
-   2

#### 11 口腔健康

-   Q86  
-   2

#### 12 哮喘

-   Q87  
-   2

#### 13 睡觉情况

-   Q88  
-   2

#### 14 学校成绩

-   Q89  
-   2

# 问题 list

### 问题：1 Analysis over States

1，States 毒品使用情况(使用毒品率越高颜色越深)  
2，States + Proportion + race(横坐标barchart`facit grid ~ race`)  
3, Gender + Proportion + age (人口老龄化图,金字塔的)  
4，State + Proportion + drug type (side by side bar
chart)只分大麻和其他两种毒品  
5，State + 大麻初体验average (年龄越早颜色越深)

### 问题：2 Analysis over behavior

##### 1，三线图

自变量：吸所有的毒品frequency。  
因变量：{bivariate（只分yes/no两种情况）}
酒驾，武器携带，自杀，戒烟，打架，初次性行为年纪（14以下和14以上，高中年龄）,屏幕使用（Q79+Q80&gt;5小时，就是重度），睡眠时间（&lt;8
or &gt;8）,学习成绩（<c or >c)  
因变量：{多元} 吸烟（不吸，重度吸烟，轻度）,
喝酒（不喝醉，一月醉1～5天，一月醉6天以上Q42)

##### 2，额外图

1，吸毒各个frequency段的，吸烟初始年龄分布。  
2, …………………，喝酒初始年龄分布。  
3, …………………, bmi box plot 分男女 or 金字塔图。

### 问题 3 Analysis over different drug type

待定

# Data Tidy

### 1，自变量清理

所有的毒品找到对应的问题序列，命名为统一的列名 (均为life time)
1，marijuana\_age 2, marijuana 3, pain\_medicine 4, cocaine 5, inhalants
6, heroin 7, methamphetamines 8, ecstasy 9, steroid 10,inject\_drug

### 2, 因变量清理

按照自己划分的问题清理
