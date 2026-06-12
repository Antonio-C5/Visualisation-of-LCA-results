# Visualisation of LCA results

## What the Project does
This repository includes projects on the visualisation of Life Cycle Assessment (LCA) results in R using the package ggplot2.

## Why the Project is Useful
Professional software for LCA typically display results by means of tables and figures: for instance, openLCA offers a variety of chart types (e.g., bar charts, spider charts) at the Project level. 
Relying solely on what professional software for LCA has to offer in terms of data visualization can be limiting: a user might not be able to modify the content of a chart; the quality of the exported image may be poor and not suitable for publication in an academic journal.<br>
Each project is useful for LCA practitioners who wish to improve the visualization and presentation of their LCA results.

## Material and Methods
The data used in the tutorials is sourced from academic publications and from the calculation of product systems in openLCA.
The first thing to do is to import the necessary data from a file.<br>
You will notice that the structure of a dataset is not necessarily the same as the one shown in the original source (e.g., the supplementary material of a paper) from which the data required to build the plot of interest is taken. You might be wondering why. <br> 
Each chart is developed as a series of layers: each layer includes something relative to a specific element of the same chart. This is the reason why a dataset is structured in a certain way; in other words, the way a table is structured will more or less dictate how the code chunk behind the chart will be built.


