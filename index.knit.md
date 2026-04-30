---
title: "How Inflation Impacts Presidential Approval Ratings"
author: "Carson Phillips"
description: "The relationship between yearly inflation and presidential approval rates."
output:
  distill::distill_article:
    self_contained: false
---




## Introduction

**My research question is as follows**: does higher inflation have an impact on presidential approval ratings? **I hypothesize that higher inflation is associated with lower presidential approval ratings.** The **null hypothesis (H0)** in this case is that there is no relationship between yearly inflation and presidential approval ratings. The **alternative hypothesis (H1)** would be that higher inflation is associated with lower presidential approval ratings. I believe this relationship will be evident, because the public generally pays attention to inflation as a general indicator of economic health, and also attributes economic outcomes to the sitting president. By extension, they should disapprove more of a president who is in office while inflation is higher. 

**This research question is important**, because it seeks to provide explanation for presidential approval ratings, the primary indicator used to define the public's assessment of the president. Presidential approval ratings have a wide berth of consequences. They indicate the president's likelihood of reelection, the likelihood that president's party will find success at midterm elections, the level of difficulty the president will incur in trying to pass legislation, and other considerations. As a result, it's important to understand what variables impact presidential approval ratings. The rate of inflation is one of the most visible aspects of the economy in the public's eyes, and the public also looks to the president to generate economic success. Thus, it is logical to research whether the rate of inflation informs the public's opinion of the president. 

## Data

My explanatory variable of interest, or **predictor variable, is** yearly inflation from 1960 - 2024, sourced from the Federal Reserve Bank of St. Louis's "Inflation, consumer prices for the United States" indicator. This variable is measured annually and expressed as a percentage. **My outcome variable of interest is** Gallup's yearly presidential approval ratings from time in office, ranging from Harry Truman to Joe Biden, and also expressed as a percentage. I specifically recorded yearly presidential approval ratings from Gallup's "Presidential Job Approval Center" into an Excel document, using polls conducted between March and April of the given year. If the results are statistically significant, and a given increase in inflation corresponds to a lower presidential approval rating, **this would provide support for my alternative hypothesis.** If a given increase in inflation has no correlation with presidential approval ratings, or if a given increase in inflation is associated with higher presidential ratings, **this would mean that I reject my hypothesis.** The **decision rule** would indicate that I should reject the **null hypothesis** if the regression coefficient for inflation is negative, and the p-value is less than 0.05 (since I will run this regression at the 95% Confidence Interval). According to the **rejection criteria**, I should will fail to reject the null hypothesis if the p-value is greater than 0.05, or if the regression coefficient for inflation is positive. 

### Preview of Inflation and Presidential Approval Ratings Datasets



### **Plot Visualizing Presidential Voting Records**



### Joining Datasets



## Results

### **Visualizing Relationship Between Inflation and Presidential Approval Ratings**



### **Regression Output**

According to my regression analysis, the predicted presidential approval rating when yearly inflation is 0% is 57.43%. **The estimated slope is -1.27, meaning that** every 1% increase in yearly inflation corresponds to a drop in presidential approval ratings of 1.27%. These findings support my hypothesis that higher inflation is associated with lower presidential approval ratings. Since this analysis is run at the 95% confidence interval, **a p-value lower than 0.05 (0.03) indicates statistically significant results.** Furthermore, the p-value of 3% also tells us that if the null hypothesis were to be true, and if inflation were to have no effect on presidential approval ratings, there would only be a 3% chance of observing a relationship between inflation and presidential ratings this strong or stronger due to simply random chance. The standard error value, or the standard deviation of the sample statistic across repeated samples, of my coefficient of interest is 0.56. This value is relatively small, and suggests that my findings are precise. In sum, the regression coefficient is negative (-1.27), and the p-value is less than 0.05 (0.03), so I can reject the null hypothesis and accept my alternative hypothesis, which suggests that higher inflation is associated with lower presidential approval ratings.

**Substantively, my results suggest that** every 1% increase in yearly inflation is associated with a 1.27% decrease in presidential approval ratings. However, I should be weary to interpret my results causally. This study is not a randomized experiment, and instead relies off of observational data, since it borrows naturally occurring inflation and presidential approval ratings. I am unable to randomly assign inflation levels to different years to ensure balance. It is often difficult to observe the counterfactual when utilizing observational data. For example, it is impossible for me to know how presidential approval ratings would have behaved without the effects of inflation. There are many other variables that may impact both inflation and presidential approval ratings, and it is very difficult to isolate the effects of the predictor variable on the outcome variable without randomization. As a result, my study **suffers from internal validity as observational studies often do, and cannot be interpret causally.**

## Conclusion

**In summary,** my results show that higher inflation is associated with lower presidential approval ratings. **There is strong support for this hypothesis** (my alternative hypothesis) given that my  regression coefficient is negative (-1.27), that my p-value less than 0.05 (0.03), and that my standard error is relatively small (0.56).  
 
The **main limitation of this analysis is the fact that it uses observational data.** Not incorporating randomization into the study stunts the internal validity, and as a result we can not presume causality. **Additionally, there could be confounding variables** which could impact both inflation and presidential approval ratings, for example a military conflict like the Vietnam War. The Vietnam War significantly increased inflation and decreased presidential approval ratings. These kinds of confounding variables which impact both inflation rates and presidential approval rates could produce an artificially strong association between high inflation and low presidential approval ratings. Because my presidential approval ratings data comes from Gallup polls, it could suffer from nonresponse bias. For example, if individuals who feel strongly about the economy are more likely to respond to these polls, my presidential approval ratings data would be skewed. Furthermore, the fact that I am using averages to measure inflation, and drawing on presidential approval ratings at a specific point in time within a given year to measure presidential approval ratings, means that I may be glossing over some nuance. More precise measurements, for example daily values for each data set would be more effective, but are not feasible. 

**A way to combat the internal validity issues brought on by observational data** would be to instead utilize a multiple regression method. Multiple regression models are often better predictors, because they incorporate multiple predictor variables, like military conflicts and other confounders in addition to inflation. This allows the researcher to interpret ceteris paribus relationships, where other explanatory variables are held constant, and the effects of the explanatory variable of interest on the outcome variable can be viewed in isolation. 

<div class="layout-chunk" data-layout="l-body">
<div class="sourceCode"><pre class="sourceCode r"><code class="sourceCode r"><span><span class='kw'><a href='https://rdrr.io/r/base/library.html'>library</a></span><span class='op'>(</span><span class='va'><a href='https://tidyverse.tidyverse.org'>tidyverse</a></span><span class='op'>)</span></span>
<span><span class='va'>inflation</span> <span class='op'>&lt;-</span> <span class='fu'><a href='https://readr.tidyverse.org/reference/read_delim.html'>read_csv</a></span><span class='op'>(</span><span class='st'>"data/inflation.csv"</span>, show_col_types <span class='op'>=</span> <span class='cn'>FALSE</span><span class='op'>)</span></span>
<span><span class='va'>presapp</span> <span class='op'>&lt;-</span> <span class='fu'><a href='https://readr.tidyverse.org/reference/read_delim.html'>read_csv</a></span><span class='op'>(</span><span class='st'>"data/presapp270.csv"</span>, show_col_types <span class='op'>=</span> <span class='cn'>FALSE</span><span class='op'>)</span></span>
<span></span>
<span><span class='fu'><a href='https://rdrr.io/r/utils/head.html'>head</a></span><span class='op'>(</span><span class='va'>inflation</span><span class='op'>)</span></span>
<span><span class='fu'><a href='https://rdrr.io/r/utils/head.html'>head</a></span><span class='op'>(</span><span class='va'>presapp</span><span class='op'>)</span></span>
<span><span class='va'>presapp</span> <span class='op'>&lt;-</span> <span class='va'>presapp</span> <span class='op'>|&gt;</span></span>
<span>  <span class='fu'><a href='https://dplyr.tidyverse.org/reference/rename.html'>rename</a></span><span class='op'>(</span>year <span class='op'>=</span> <span class='va'>Date</span><span class='op'>)</span> <span class='op'>|&gt;</span></span>
<span>  <span class='fu'><a href='https://dplyr.tidyverse.org/reference/mutate.html'>mutate</a></span><span class='op'>(</span></span>
<span>    approval <span class='op'>=</span> <span class='fu'><a href='https://readr.tidyverse.org/reference/parse_number.html'>parse_number</a></span><span class='op'>(</span><span class='va'>`Approval Rating`</span><span class='op'>)</span><span class='op'>)</span></span>
<span></span>
<span><span class='va'>presapp</span> <span class='op'>|&gt;</span></span>
<span><span class='fu'>knitr</span><span class='fu'>::</span><span class='fu'><a href='https://rdrr.io/pkg/knitr/man/kable.html'>kable</a></span><span class='op'>(</span></span>
<span>    digits <span class='op'>=</span> <span class='fl'>2</span>,</span>
<span>    col.names <span class='op'>=</span> <span class='fu'><a href='https://rdrr.io/r/base/c.html'>c</a></span><span class='op'>(</span><span class='st'>"President"</span>, <span class='st'>"Year"</span>, <span class='st'>"Approval Rating (%)"</span>, <span class='st'>"Approval Rating"</span><span class='op'>)</span>,</span>
<span>    caption <span class='op'>=</span> <span class='st'>"Presidential Approval Ratings Data Preview"</span></span>
<span>  <span class='op'>)</span></span>
<span></span>
<span><span class='va'>inflation</span> <span class='op'>&lt;-</span> <span class='va'>inflation</span> <span class='op'>|&gt;</span></span>
<span>  <span class='fu'><a href='https://dplyr.tidyverse.org/reference/rename.html'>rename</a></span><span class='op'>(</span>inflation <span class='op'>=</span> <span class='va'>FPCPITOTLZGUSA</span><span class='op'>)</span> <span class='op'>|&gt;</span></span>
<span>  <span class='fu'><a href='https://dplyr.tidyverse.org/reference/mutate.html'>mutate</a></span><span class='op'>(</span>year <span class='op'>=</span> <span class='fu'><a href='https://rdrr.io/r/base/integer.html'>as.integer</a></span><span class='op'>(</span><span class='fu'><a href='https://rdrr.io/r/base/format.html'>format</a></span><span class='op'>(</span><span class='va'>observation_date</span>, <span class='st'>"%Y"</span><span class='op'>)</span><span class='op'>)</span><span class='op'>)</span></span>
<span></span>
<span><span class='va'>inflation</span> <span class='op'>|&gt;</span></span>
<span>  <span class='fu'>knitr</span><span class='fu'>::</span><span class='fu'><a href='https://rdrr.io/pkg/knitr/man/kable.html'>kable</a></span><span class='op'>(</span></span>
<span>    digits <span class='op'>=</span> <span class='fl'>2</span>,</span>
<span>    col.names <span class='op'>=</span> <span class='fu'><a href='https://rdrr.io/r/base/c.html'>c</a></span><span class='op'>(</span><span class='st'>"Observation Date"</span>, <span class='st'>"Inflation"</span>, <span class='st'>"Year"</span><span class='op'>)</span>,</span>
<span>    caption <span class='op'>=</span> <span class='st'>"Inflation Data Preview"</span></span>
<span>  <span class='op'>)</span></span>
<span><span class='va'>presappplot</span> <span class='op'>&lt;-</span> <span class='fu'><a href='https://ggplot2.tidyverse.org/reference/ggplot.html'>ggplot</a></span><span class='op'>(</span>data <span class='op'>=</span> <span class='va'>presapp</span>, mapping <span class='op'>=</span> <span class='fu'><a href='https://ggplot2.tidyverse.org/reference/aes.html'>aes</a></span><span class='op'>(</span>x <span class='op'>=</span> <span class='va'>year</span>, y <span class='op'>=</span> <span class='va'>approval</span>, color <span class='op'>=</span> <span class='va'>President</span><span class='op'>)</span><span class='op'>)</span> <span class='op'>+</span></span>
<span>  <span class='fu'><a href='https://ggplot2.tidyverse.org/reference/geom_point.html'>geom_point</a></span><span class='op'>(</span><span class='op'>)</span> <span class='op'>+</span></span>
<span>  <span class='fu'><a href='https://ggplot2.tidyverse.org/reference/geom_smooth.html'>geom_smooth</a></span><span class='op'>(</span>method <span class='op'>=</span> <span class='st'>"lm"</span>, se <span class='op'>=</span> <span class='cn'>FALSE</span>, color <span class='op'>=</span> <span class='st'>"indianred1"</span><span class='op'>)</span> <span class='op'>+</span></span>
<span>  <span class='fu'><a href='https://ggplot2.tidyverse.org/reference/labs.html'>labs</a></span><span class='op'>(</span>x <span class='op'>=</span> <span class='st'>"Year"</span>,</span>
<span>       y <span class='op'>=</span> <span class='st'>"Presidential Approval Rating (%)"</span>,</span>
<span>       title <span class='op'>=</span> <span class='st'>"Presidential Approval Ratings by Year"</span><span class='op'>)</span></span>
<span></span>
<span><span class='va'>presappplot</span></span>
<span><span class='kw'><a href='https://rdrr.io/r/base/library.html'>library</a></span><span class='op'>(</span><span class='va'><a href='https://tidyverse.tidyverse.org'>tidyverse</a></span><span class='op'>)</span></span>
<span></span>
<span><span class='va'>joined</span> <span class='op'>&lt;-</span> <span class='va'>presapp</span> <span class='op'>|&gt;</span></span>
<span>  <span class='fu'><a href='https://dplyr.tidyverse.org/reference/mutate-joins.html'>inner_join</a></span><span class='op'>(</span><span class='va'>inflation</span>, by <span class='op'>=</span> <span class='st'>"year"</span><span class='op'>)</span> </span>
<span></span>
<span><span class='va'>joined</span></span>
<span><span class='va'>visual</span> <span class='op'>&lt;-</span> <span class='fu'><a href='https://ggplot2.tidyverse.org/reference/ggplot.html'>ggplot</a></span><span class='op'>(</span>data <span class='op'>=</span> <span class='va'>joined</span>, mapping <span class='op'>=</span> <span class='fu'><a href='https://ggplot2.tidyverse.org/reference/aes.html'>aes</a></span><span class='op'>(</span>x <span class='op'>=</span> <span class='va'>inflation</span>, y <span class='op'>=</span> <span class='va'>approval</span>, color <span class='op'>=</span> <span class='va'>President</span><span class='op'>)</span><span class='op'>)</span> <span class='op'>+</span></span>
<span>  <span class='fu'><a href='https://ggplot2.tidyverse.org/reference/geom_point.html'>geom_point</a></span><span class='op'>(</span><span class='op'>)</span> <span class='op'>+</span></span>
<span>  <span class='fu'><a href='https://ggplot2.tidyverse.org/reference/geom_smooth.html'>geom_smooth</a></span><span class='op'>(</span>method <span class='op'>=</span> <span class='st'>"lm"</span>, se <span class='op'>=</span> <span class='cn'>FALSE</span>, color <span class='op'>=</span> <span class='st'>"indianred1"</span><span class='op'>)</span> <span class='op'>+</span></span>
<span>  <span class='fu'><a href='https://ggplot2.tidyverse.org/reference/labs.html'>labs</a></span><span class='op'>(</span>x <span class='op'>=</span> <span class='st'>"Yearly Inflation (%)"</span>,</span>
<span>       y <span class='op'>=</span> <span class='st'>"Yearly Presidential Approval Rating (%)"</span>,</span>
<span>       title <span class='op'>=</span> <span class='st'>"Relationship Between Inflation and Presidential Approval Ratings"</span><span class='op'>)</span> <span class='op'>+</span></span>
<span>  <span class='fu'><a href='https://ggplot2.tidyverse.org/reference/ggtheme.html'>theme_minimal</a></span><span class='op'>(</span><span class='op'>)</span></span>
<span></span>
<span><span class='va'>visual</span></span>
<span><span class='kw'><a href='https://rdrr.io/r/base/library.html'>library</a></span><span class='op'>(</span><span class='va'><a href='https://broom.tidymodels.org/'>broom</a></span><span class='op'>)</span></span>
<span><span class='va'>approval_fit</span> <span class='op'>&lt;-</span> <span class='fu'><a href='https://rdrr.io/r/stats/lm.html'>lm</a></span><span class='op'>(</span><span class='va'>approval</span> <span class='op'>~</span> <span class='va'>inflation</span>, data <span class='op'>=</span> <span class='va'>joined</span><span class='op'>)</span></span>
<span></span>
<span><span class='va'>regression_table</span> <span class='op'>&lt;-</span> <span class='fu'><a href='https://generics.r-lib.org/reference/tidy.html'>tidy</a></span><span class='op'>(</span><span class='va'>approval_fit</span><span class='op'>)</span></span>
<span></span>
<span><span class='va'>regression_table</span> <span class='op'>|&gt;</span> </span>
<span>  <span class='fu'>knitr</span><span class='fu'>::</span><span class='fu'><a href='https://rdrr.io/pkg/knitr/man/kable.html'>kable</a></span><span class='op'>(</span></span>
<span>    digits <span class='op'>=</span> <span class='fl'>2</span>,</span>
<span>    col.names <span class='op'>=</span> <span class='fu'><a href='https://rdrr.io/r/base/c.html'>c</a></span><span class='op'>(</span><span class='st'>"Term"</span>, <span class='st'>"Estimate"</span>, <span class='st'>"Std. Error"</span>, <span class='st'>"Statistic"</span>, <span class='st'>"p-value"</span><span class='op'>)</span>,</span>
<span>    caption <span class='op'>=</span> <span class='st'>"Table 1: Linear Regression of Presidential Approval on Inflation"</span></span>
<span>  <span class='op'>)</span></span></code></pre></div>

</div>

```{.r .distill-force-highlighting-css}
```
