# R Beginner's Guide

This repository contains the source of [R Beginner's Guide](https://adams.quarto.pub/rbg/) book.
The book is built using [Quarto](https://quarto.org/).

## O'Reilly

To generate book for O'Reilly, build the book then:

```{r}
# pak::pak("hadley/htmlbook")
htmlbook::convert_book()

html <- list.files("oreilly", pattern = "[.]html$", full.names = TRUE)
file.copy(html, "../r-for-data-science-2e/", overwrite = TRUE)

pngs <- list.files("oreilly", pattern = "[.]png$", full.names = TRUE, recursive = TRUE)
dest <- gsub("oreilly", "../r-for-data-science-2e/", pngs)
fs::dir_create(unique(dirname(dest)))
file.copy(pngs, dest, overwrite = TRUE)
```

Then commit and push to atlas.

## Code of Conduct

Please note that rbg uses a [Contributor Code of Conduct](https://contributor-covenant.org/version/2/0/CODE_OF_CONDUCT.html).
By contributing to this book, you agree to abide by its terms.