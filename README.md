# HW5
---
Title: "California Wind Turbines"
Author: "Muzammal Shafique"
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE, message = FALSE, warning = FALSE)
```

## Load Libraries
```{r}
library(ggplot2)
library(dplyr)
```

## Load and Prepare Data
```{r}
# California map data
california <- map_data("state") %>%
  filter(region == "california")

# Wind turbine data
load("DATA/wind_turbines.rda")
wind_ca <- wind_turbines %>%
  filter(t_state == "CA")
```

## Create the Map
```{r}
ggplot() +
  geom_polygon(
    data = california,
    aes(x = long, y = lat, group = group),
    fill = "white", color = "black"
  ) +
  geom_point(
    data = wind_ca,
    aes(x = xlong, y = ylat),
    color = "blue", size = 1
  ) +
  guides(fill = "none") +
  coord_fixed(1.3) +
  labs(title = "Wind Turbines in California")
```
