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
library("scales")
library("glue")
library("tidymodels")
```
```{r package-options, include=FALSE, message=FALSE, warning=FALSE}
theme_set(theme_light())
```
```{r import-data, include=FALSE, message=FALSE, warning=FALSE}
base_url <- "https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/"
file_path <- "2021/2021-01-05/transit_cost.csv"
  
df_raw <- 
  readr::read_csv(
    paste0(base_url, file_path),
    col_types = cols(
      e = col_double(),
      country = col_character(),
      city = col_character(),
      line = col_character(),
      start_year = col_character(),
      end_year = col_character(),
      rr = col_double(),
      length = col_double(),
      tunnel_per = col_character(),
      tunnel = col_double(),
      stations = col_double(),
      source1 = col_character(),
      cost = col_double(),
      currency = col_character(),
      year = col_double(),
      ppp_rate = col_double(),
      real_cost = col_character(),
      cost_km_millions = col_double(),
      source2 = col_character(),
      reference = col_character()
    )
  )
readr::spec(df_raw)
```

```{r clean-data, include=FALSE, message=FALSE, warning=FALSE}
df <- df_raw 
```
```{r basic-features, include=FALSE, message=FALSE, warning=FALSE}
df <- df 
```
```{r split-data, include=FALSE}
splitter <- initial_split(df)
train <- training(splitter)
test <- testing(splitter)
```
```{r skim-data, eval=FALSE, include=FALSE}
library("skimr")
skimr::skim(train)
```

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

```{r view-data, eval=FALSE, include=FALSE}
train %>%
  view(title="train")
```




