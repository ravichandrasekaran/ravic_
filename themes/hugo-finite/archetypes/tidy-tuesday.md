+++
+++


A #tidytuesday for transit costs.

<!--more-->

A #tidytuesday for transit costs.

```{r set-options, include = FALSE}
options(scipen=999)
options(digits=4)
set.seed(722)
```
```{r knit-options, include = FALSE}
library("knitr")
knitr::opts_chunk$set(
  cache = TRUE, warning = FALSE, message = FALSE, 
  echo = TRUE, dev = "svg", dpi = 300, cache.lazy = FALSE,
  tidy = "styler", fig.width = 8, fig.height = 5)
```
```{r load-packages, include=FALSE}
options(tidyverse.quiet=TRUE)
require("tidyverse", quietly = TRUE, warn.conflicts = FALSE)
require("scales", quietly = TRUE, warn.conflicts = FALSE)
require("glue", quietly = TRUE, warn.conflicts = FALSE)
tidymodels::tidymodels_prefer(quiet = TRUE)
require("tidymodels", quietly = TRUE, warn.conflicts = FALSE)
```
```{r theme-options, include=FALSE}
theme_set(theme_light())
update_geom_defaults("point", list(alpha = .5))
update_geom_defaults("rect", list(colour = "lightblue"))
```

```{r import-data, include=FALSE}
tuesdata <- tidytuesdayR::tt_load('2021-02-23')  
employed_raw <- tuesdata$employed
earn_raw <- tuesdata$earn
```
```{r clean-data, include=FALSE}
employed_clean <- employed_raw 
```
```{r basic-features, include=FALSE}
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
```{r correlations-pairs, include=FALSE, eval=FALSE}
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




