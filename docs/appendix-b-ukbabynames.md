
# ukbabynames Live Coding {#ukbabynames}

Here is the script that we developed during the live coding on Day 1. <a href="misc/names.R" download>(click here to download)</a>


```r
library("tidyverse")
library("ukbabynames")

nam0 <- read_csv("PSYCH5077 Grades-20180921_0719-comma_separated.csv") %>%
  select(name = `First name`)

nam1 <- tibble(name = c("Dale", "Lisa", "Rebecca"))

nam_uk <- bind_rows(nam0, nam1) %>%
  inner_join(ukbabynames, "name") 

ggplot(nam_uk, aes(x = year, y= n,
                   colour = sex)) +
  geom_line() +
  facet_wrap(~name, scales = "free_y")

ggsave("names.png", width = 10, height = 5)
```

<a href="misc/names.Rmd" download>Click here to download the RMarkdown version.</a>

For privacy reasons, the csv file with the list of names from the course is only available on the Moodle site.
