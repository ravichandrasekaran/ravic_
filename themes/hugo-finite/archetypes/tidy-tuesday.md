+++
+++


A #tidytuesday for transit costs.

<!--more-->

A #tidytuesday for transit costs.

```{r set-options, include=FALSE, message=FALSE, warning=FALSE}
options(scipen=999)
options(digits=4)
options(tidyverse.quiet=TRUE)
set.seed(722)
```
```{r load-packages, include=FALSE, message=FALSE, warning=FALSE}
library("tidyverse")
library("tidytuesdayR")
library("scales")
library("glue")
library("tidymodels")
```
```{r package-options, include=FALSE, message=FALSE, warning=FALSE}
theme_set(theme_light())
```

```{r import-data, include=FALSE, message=FALSE, warning=FALSE}
tuesdata <- tidytuesdayR::tt_load('2021-02-23')  
employed_raw <- tuesdata$employed
earn_raw <- tuesdata$earn
```
```{r clean-data, include=FALSE, message=FALSE, warning=FALSE}
employed_clean <- employed_raw 
```
```{r basic-features, include=FALSE, message=FALSE, warning=FALSE}
employed <- employed_clean
```
```{r skim-data, eval=FALSE, include=FALSE}
library("skimr")
skimr::skim(employed)
```
```{r view-data, eval=FALSE, include=FALSE}
employed %>%
  view(title="employed")
```



<!--Appendix-->
```{r correlations-pairs, include=FALSE, eval=FALSE, message=FALSE, warning=FALSE}
library("ggcorrplot")
train %>% 
  select(where(is.numeric)) %>%
  filter(complete.cases(.)) %>%
  cor(.) %>%
  ggcorrplot(., hc.order = TRUE, legend.title=bquote(rho)) +
  labs(title="Correlation plot",
       y = NULL,
       x = NULL) +
  theme(axis.text.x = element_text(angle = 90, hjust=1))
```




