# qtl2shinyApp
QTL2 Shiny App Operations

This repo has building blocks for operational QTL2 Shiny App
constructed with
[qtl2shiny](https://github.com/byandell-sysgen/qtl2shiny).
The instance will have a folder `qtl2shinyData` that is **not**
synced with GitHub.

The package, and related packages
[qlt2pattern](https://github.com/byandell-sysgen/qtl2pattern)
and
[qtl2mediate](https://github.com/byandell-sysgen/qtl2mediate),
were developed around 2010 for the simpler DO500 experiment.
Several changes are needed to accommodate the DO1200 experiment.
Likely path is to tag current version of packages as a branch
(say `legacy`) and create a new branch (say `refactor`).

These needed changes include:

- modify data entry to new formats and directory structure
  - initial work in `DO1200Data.Rmd`
  - further use in `DO1200Study.Rmd`
- modify scan (`scan1covar`) to handle new data and extensions
  - `addcovar` and `intcovar` as formula
  - extensions for user-supplied add and int covar modifications
    - `sex` and/or `diet` interactions
    - SNP or other covariates
- modify mediation to handle new data
  - revisit mrna mediator code, which has been dormant

In addition to these issues, the modular design of the shiny modules
needs to be refactored.
The modules have many parameters, which is helpful to speed up code
but makes it difficult to follow server logic.

A version of the shiny module structure is laid out in
[Documentation: qtl2hiny](https://github.com/AttieLab-Systems-Genetics/Documentation/blob/main/ShinyApps.md#qtl2shiny-localized-qtl-analysis-and-visualization).
This was created with 
[inst/scripts/network_igraph.Rmd](https://github.com/byandell-sysgen/qtl2shiny/blob/master/inst/scripts/network_igraph.Rmd),
which uses 
[inst/extdata/qtl2shinyEdge.csv](https://github.com/byandell-sysgen/qtl2shiny/blob/master/inst/extdata/qtl2shinyEdge.csv)
and
[inst/extdata/qtl2shinyNode.csv](https://github.com/byandell-sysgen/qtl2shiny/blob/master/inst/extdata/qtl2shinyNode.csv).
The nodes and edges have more information about output and parameters,
but some of the details may differ from current code.
Studying this will help us understand the components--parameters,
intermediate objects, and server logic.
