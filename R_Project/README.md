---
output: html_document
editor_options: 
  chunk_output_type: inline
---
WineQualityWhites by yijigao92@gmail.com
========================================================
```{r global_options, include=FALSE}
knitr::opts_chunk$set(message = FALSE, warning = FALSE, echo = FALSE)
```




```{r echo=FALSE, message=FALSE, warning=FALSE, packages}
# Load all of the packages that you end up using
# in your analysis in this code chunk.

# Notice that the parameter "echo" was set to FALSE for this code chunk.
# This prevents the code from displaying in the knitted HTML output.
# You should set echo=FALSE for all code chunks in your file.

library(ggplot2)
library(gridExtra)
library(GGally)
library(scales)
library(memisc)
library(ggthemes)

theme_set(theme_few())
```

```{r echo=FALSE, Load_the_Data}
# Load the Data
WineQualityWhites <- read.csv("wineQualityWhites.csv")

```

# Univariate Plots Section
```{r echo=FALSE, Univariate_Plots}
dim(WineQualityWhites)
str(WineQualityWhites)
summary(WineQualityWhites)
```

���ݼ��а�����13��������4898���۲�ֵ

```{r echo=FALSE}
table(WineQualityWhites$quality)

ggplot(WineQualityWhites, aes(quality)) +
  geom_histogram(binwidth = 1,fill = "#0000 CD") +
  ggtitle("Quality")

```

���ݼ��е�Ʒ�ʴ��³���̬�ֲ���������İ����Ѿ�Ʒ����5-7֮�䡣Ʒ�ʺܸߺͺܵ͵ľ����������ࡣ

```{r echo=FALSE}
table(WineQualityWhites$fixed.acidity)
ggplot(WineQualityWhites, aes(fixed.acidity)) +
  geom_histogram(binwidth = 0.1,fill = "#0000CD") +
  ggtitle("Fix acidity")
```

�����ѾƵĹ̶������6-8֮�䣬����̬�ֲ���

```{r echo=FALSE, message=FALSE, warning=FALSE}

f1 <-  ggplot(WineQualityWhites, aes(volatile.acidity)) +
  geom_histogram(fill = "#0000CD")

f2 <- ggplot(WineQualityWhites, aes(volatile.acidity), xlab) +
  geom_histogram(fill = "#8A2BE2")+
  xlab("volatile.acidity(log10)")
  scale_x_log10()

f3 <- ggplot(WineQualityWhites, aes(residual.sugar)) +
  geom_histogram(fill = "#0000CD")

f4 <- ggplot(WineQualityWhites, aes(residual.sugar)) +
  geom_histogram(fill = "#8A2BE2") +
  scale_x_log10() +
  xlab("residual.sugar(log10)")

f5 <- ggplot(WineQualityWhites, aes(chlorides)) +
  geom_histogram(fill = "#0000CD")

f6 <- ggplot(WineQualityWhites, aes(chlorides)) +
  geom_histogram(fill = "#8A2BE2") +
  scale_x_log10() +
  xlab("chlorides(log10)")

f7 <- ggplot(WineQualityWhites, aes(free.sulfur.dioxide)) +
  geom_histogram(fill = "#0000CD")

f8 <- ggplot(WineQualityWhites, aes(free.sulfur.dioxide)) +
  geom_histogram(fill = "#8A2BE2") +
  scale_x_log10() +
  xlab("free.sulfur.dioxide(log10)")

grid.arrange(f1, f2, f3, f4, f5, f6, f7, f8, ncol = 2)
```

�����ѾƵĻӷ������/����/�Ȼ���/����������򣬳�������ƫб���г���βֵ������ת��Ϊ����������Ե���̬�ֲ�����Ȥ���ǣ����ǳ����������ֵ��


```{r echo=FALSE, message=FALSE}

ggplot(WineQualityWhites, aes(total.sulfur.dioxide)) +
  geom_histogram(fill = "#0000CD") +
  ggtitle("Total sulfur dioxide")

ggplot(WineQualityWhites, aes(density)) +
  geom_histogram(fill = "#0000CD") +
  ggtitle("Density")

ggplot(WineQualityWhites, aes(pH)) +
  geom_histogram(fill = "#0000CD") +
  ggtitle("pH")

ggplot(WineQualityWhites, aes(sulphates)) +
  geom_histogram(fill = "#0000CD") +
  ggtitle("Sulphates")

```

�����ᡢ�ܶ��������ܶȡ�pH�������ξ����³���̬�ֲ���

```{r echo=FALSE, message=FALSE, warning=FALSE}
ggplot(WineQualityWhites, aes(alcohol)) +
  geom_histogram(fill = I("#0000CD")) +
  ggtitle("Alcohol")

ggplot(WineQualityWhites, aes(alcohol)) +
  geom_histogram(fill = I("#0000CD")) +
  ggtitle("Alcohol") +
  scale_x_log10() +
  xlab("Alcohol(log10)")
```




# Univariate Analysis

### What is the structure of your dataset?
һ����13��������4898���۲�ֵ��

* �����Ѿ�Ʒ��ƽ��ֵΪ5.88��75%�İ����Ѿ�Ʒ����5����
* ����������ѾƵĹ̶����6-8֮��
* �����ѾƵĲ��Ǻ���Ϊ1-2֮����������
* �����ѾƵ�pH��ΧΪ2.7-3.8��ƽ��ֵΪ3.19

### What is/are the main feature(s) of interest in your dataset?
�������Ȥ���ǰ����ѾƵ�Ʒ�ʣ�����֪���ĸ���������Ԥ������ѾƵ�Ʒ�������

### What other features in the dataset do you think will help support your investigation into your feature(s) of interest?
�̶���ȣ����ǣ�pH���ƾ�

### Did you create any new variables from existing variables in the dataset?
δ�����±���

### Of the features you investigated, were there any unusual distributions? Did you perform any operations on the data to tidy, adjust, or change the form of the data? If so, why did you do this?
�ӷ�����ȣ����Ǻ������Ȼ��������������ҽ���Щ����ȡ������ʹ֮�ֲ�������̬�ֲ������ڷ�����


# Bivariate Plots Section
```{r echo=FALSE, Bivariate_Plots}
cor(WineQualityWhites)
```

Ϊ���о�quality��������Щ������أ��ȸ�����quality������������ϵ�������Կ�����quality��alcohol, density�������ǿ�������volatile.acidity, chlorides, total.sulfur.dioxide, ��citric.acidity, residual.sugar, free.sulfur.dioxide, pH, sulphates����Բ���

```{r fig.width=15, fig.height=15}
ggpairs(WineQualityWhites, 
        lower = list(continuous = wrap("points", shape = I("."))),
        upper = list(combo = wrap("box", outlier.shape = I("."),
                                  continuous = wrap("cor", size = 3))))
```

```{r echo=FALSE, message=FALSE}
ggplot(WineQualityWhites, aes(factor(quality),alcohol)) +
  geom_point()

ggplot(WineQualityWhites, aes(factor(quality),alcohol)) +
  geom_point(alpha = 0.3, size =2, position = "jitter")
```

�����˾ƾ�-Ʒ��ɢ��ͼ����һ��ͼ���Կ������Ȼ��ƣ���ͼ���Ӷ������Ӿƾ���Ʒ�ʵ�ɢ��ͼ���Կ������ƾ�Ũ��Խ�ߣ���Ʒ�ʵľƸ����У����³�����ع�ϵ��

```{r message=FALSE, warning=FALSE, echo=FALSE}
ggplot(WineQualityWhites, aes(factor(quality),density)) +
  geom_point(alpha = 1/10, size = 2, position = "jitter") +
  ylim(min(WineQualityWhites$density), quantile(WineQualityWhites$density, .99))
```

���ܶ�-Ʒ��ɢ��ͼ�����ܶȵİ����ѾƵ�Ʒ����5���и��࣬�����ܶȵľƸ�Ʒ�ʼ��С�������Ҳ�����⣬��Ϊ�ƾ�Ũ��Խ�ߣ��ܶ�ԽС�����ǿ��������ƾ�Ũ������ܶȵĹ�ϵ

```{r echo=FALSE, message=FALSE, warning=FALSE}
ggplot(WineQualityWhites, aes(alcohol, density)) +
  geom_point(alpha = 1/20,size = 1.5, position = "jitter") +
  geom_smooth(method = "lm") +
  ylim(min(WineQualityWhites$density), quantile(WineQualityWhites$density, .99))

```

��ͼ֤ʵ�����ǵĽ��ͣ��Ƶ��ܶ���ƾ�Ũ�����߶����͡�

```{r echo=FALSE, message=FALSE, warning=FALSE}
ggplot(WineQualityWhites, aes(factor(quality), volatile.acidity)) +
  geom_point(alpha = 0.3, size = 1.5, position = "jitter")

ggplot(WineQualityWhites,aes(factor(quality), chlorides))+
  geom_point(alpha = 0.3, size = 1.5, position = "jitter") +
  ylim(0, quantile(WineQualityWhites$chlorides, .99))
```

������volatile.acidity �� chlorides �ʸ����

```{r echo=FALSE, message=FALSE}

by(WineQualityWhites$alcohol, factor(WineQualityWhites$quality), summary)

ggplot(WineQualityWhites, aes(x = factor(quality), y = alcohol)) +
   geom_jitter(alpha = 0.1) +
   geom_boxplot(alpha = 0.5, size = 0.5) +
   theme_gray()
```

```{r}
by(WineQualityWhites$density, factor(WineQualityWhites$quality), summary)

ggplot(WineQualityWhites, aes(x = factor(quality), y = density)) +
   geom_jitter(alpha = 0.1) +
   geom_boxplot(alpha = 0.5, size = 0.5) +
   coord_cartesian(ylim = c(0.989, 1.000)) +
   theme_gray()
```


Ϊ�˽�һ���о���Ʒ����ص����أ�����ͼʱʹ��factor��quality����ת��Ϊordered���ͱ���,��ͼ�Ƿֱ���quality��alcoholŨ��, density������ͼ���������Կ�������Ʒ�ʵİ����Ѿ�alcohol��λ��Ҫ���ڵ�Ʒ�ʰ����Ѿ�,density��λ����Ʒ�ʾ����Ե��ڵ�Ʒ�ʾơ�

```{r echo=FALSE, message=FALSE}
by(WineQualityWhites$volatile.acidity, factor(WineQualityWhites$quality), summary)

ggplot(WineQualityWhites, aes(x = factor(quality), y = volatile.acidity)) +
   geom_jitter(alpha = 0.1) +
   geom_boxplot(alpha = 0.5, size = 0.5) +
   coord_cartesian(ylim = c(0, 0.55)) +
   theme_gray()

```


```{r echo=FALSE, message=FALSE}
by(WineQualityWhites$chlorides, factor(WineQualityWhites$quality), summary)
ggplot(WineQualityWhites, aes(x = factor(quality), y = chlorides)) +
  geom_jitter(alpha = 0.1) +
  geom_boxplot(alpha = 0.5, size = 0.5) +
  coord_cartesian(ylim = c(0, 0.101)) +
  theme_gray()
```


�����������ͼ���Ƿ��֣���ͬƷ�ʵ÷ֵ�volatile.acidity���󣬶�����chlorides, ���Եģ���Ʒ�ʵİ����ѾƵ�chloridesҪ���ڵ�Ʒ�ʵľơ�

# Bivariate Analysis

### Talk about some of the relationships you observed in this part of the investigation. How did the feature(s) of interest vary with other features in the dataset?

����һ���֣����о���������Ѿ�quality���ϵ���ϴ�ļ���������alcohol, density, volatile.acidty, chlorides����
������£�

* �����Ѿ�quality��alcohol����أ�alcoholŨ��Խ��quality�÷�Խ�ߣ�
* chloridesԽ�ͣ�quality�÷�Խ�ߡ�
* quality��volatile.acidity����Բ���

### Did you observe any interesting relationships between the other features (not the main feature(s) of interest)?

density �� alcohol �ʸ���أ�alcoholŨ��Խ�ߣ�densityԽ�ͣ�quality�÷�Խ��

### What was the strongest relationship you found?

quality ��alcoholŨ���н�ǿ���


# Multivariate Plots Section

```{r echo=FALSE, warning=FALSE, Multivariate_Plots}

ggplot(WineQualityWhites, aes(x = alcohol, y = density, color = factor(quality))) +
  geom_jitter(alpha = 0.2) +
  ylim(0.985, 1.005) +
  scale_color_brewer(palette = 18) +
  geom_smooth(method = "lm", se = FALSE, size = 1) +
  labs(x = "Alcohol", y = "Density") +
  ggtitle("Density VS Alcohol VS Quality") +
  theme_gray()
```

��ͼ��density-alcoholʹ��quality��ɫ�Ķ����ͼ�� density��alcohol����أ�Ҳ�ܿ����ϸ�Ʒ�ʵľƷֲ���ͼ�����½ǣ���alcohol�ϴ�density��С������

```{r echo=FALSE, message=FALSE, warning=FALSE}
ggplot(WineQualityWhites, aes(residual.sugar, density, color = factor(quality))) +
  geom_jitter(alpha = 0.3) +
  xlim(0, quantile(WineQualityWhites$residual.sugar, .99)) +
  ylim(0.985, 1.005) +
  geom_smooth(method = "lm", se = FALSE, size = 1) +
  scale_color_brewer(palette = 18) +
  labs(x = "Residual Sugar", y = "Density") +
  ggtitle("Density VS Residual Sugar VS Quality")

```

residual.sugar �� density ��أ� ��densityԽ�ͣ�qualityԽ��

```{r echo=FALSE, message=FALSE, warning=FALSE}

ggplot(WineQualityWhites, aes(total.sulfur.dioxide, density, color = factor(quality))) +
  geom_jitter(alpha = 0.3) +
  geom_smooth(method = "lm", se = FALSE, size = 1) +
  ylim(0.985, 1.005) +
  scale_color_brewer(palette = 18) +
  labs(x = "Total sulfur dioxide", y = "Density") +
  ggtitle("Density VS Total sulfur dioxide VS Quality")
```


# Multivariate Analysis

### Talk about some of the relationships you observed in this part of the investigation. Were there features that strengthened each other in terms of looking at your feature(s) of interest?

��һ���ֽ�һ��������qulaity��density��alcohol��residual.sugar��total.sulfur.dioxide��Ĺ�ϵ���ⲿ��Ҳ��֤��quality��alcohol��density��ǿ��ع�ϵ��������residual.sugar��total.sulfur.dioxide����Ȼ����density�����ǿ�������ƺ���qualityӰ�첻��

### Were there any interesting or surprising interactions between features?

density����������alcohol��residual.sugal��total.sulfur.dioxide���У�������أ���alcoholӰ�����

### OPTIONAL: Did you create any models with your dataset? Discuss the strengths and limitations of your model.

------

# Final Plots and Summary

### Plot One
```{r echo=FALSE, Plot_One}
ggplot(WineQualityWhites, aes(quality, fill = I("#4169E1"))) +
  geom_histogram(binwidth = 1) +
  ggtitle("Quality")
```

### Description One

�����ѾƵ�quality�÷ֳ���̬�ֲ����󲿷ֵ÷���5-7֮��

### Plot Two

```{r echo=FALSE, Plot_Two}
ggplot(WineQualityWhites, aes(factor(quality), alcohol)) +
  geom_boxplot(alpha = 0.5, size = 0.75) +
  geom_jitter(alpha = 0.1) +
  ggtitle("Quality vs alcohol") +
  labs(x = "Quality", y = "Alcohol") +
  theme_gray()


```

### Description Two

quality�÷ָߵİ����ѾƵ�alcoholŨ�ȶ��ϸ�

### Plot Three

```{r echo=FALSE,message=FALSE,warning=FALSE,Plot_Three}
ggplot(WineQualityWhites, aes(x = alcohol, y = density, color = factor(quality))) +
  geom_jitter(alpha = 0.2) +
  ylim(0.985, 1.005) +
  scale_color_brewer(palette = 18) +
  geom_smooth(method = "lm", se = FALSE, size = 1) +
  labs(x = "Alcohol", y = "Density") +
  ggtitle("Density VS Alcohol VS Quality") +
  theme_gray()
```

### Description Three

��ͼ��ʾ��alcohol��density �����Թ�ϵ��ͬʱ��ʾ��quality��alcohol������ؼ�density�ĸ���ع�ϵ��

------

# Reflection

������ݼ������˰����ѾƵ�13������������Ҫ���о������Ѿ�quality����Щ��������ء������Ǳ��η����ķ�˼���ܽ᣺

* ���ڷ������������Ͷ������ʱ�����˴��ۣ���Ϊ���ݼ���û������������������ǿ��ǵ�qualityֻ��7��ȡֵ���ҽ���ת��Ϊ��������������Ϊ�Һ��潨��Ԥ��ģ��Ҳ�������鷳�������ⲿ�ִ������á�
* �������ҵ���������Ѿ�quality����صı�������alcohol��alcoholŨ��Խ�ߣ������Ѿ�Ʒ��Խ�ߡ�
* �����Ĺ����У��һ�ϣ������һ���ܹ������Ѿ�Ʒ�ʽ���Ԥ���ģ�ͣ�ͨ���仯ѧ���������Ԥ����Ʒ�ʵ÷֡�