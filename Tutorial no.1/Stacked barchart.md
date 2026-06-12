# Stacked barchart

## Introduction
This tutorial illustrates how to reproduce a stacked barchart that shows the contribution of different processes to four environmental impact categories.<br>
The original data is taken from Table 5 in (Murphy et al., 2013).<br>
<br>
The aim of this tutorial is to create Fig. 2, which is displayed below for convenience:<br>
<img width="795" height="477" alt="Fig  2" src="https://github.com/user-attachments/assets/c910f2eb-1796-43eb-957f-1f594da62acd" />
<br>
Fig. 2 shows the process contribution as percentages (on the y-axis) to the selected impact categories (on the x-axis). Each colour refers to a process, as indicated in the legend.
<br> 
<br>
Let's try to reproduce the same plot.

## The dataset 
Table 5 in the paper contains the results of the life cycle impact assessment, which are broken down by type of process; the overall result for each impact category ("Total" in the table) is included as well. 
<br> 
<br>
<img width="1266" height="227" alt="Table 5" src="https://github.com/user-attachments/assets/8c23dea1-9595-4ef2-9909-dd73e2017bcf" />
<br>
We have all the data we need. Great!
<br>
The same data was imported into Excel and organised in such a way as to enable the creation of Fig. 2 using the package ggplot2. 
<br>
The excel file includes two sheets: 
1) the source of the data;
2) the table used in the tutorial, which is Tabelle1 in this case.
<br>
Tabelle1 is then imported into RStudio.
<br>
To import the table, run the following code chunk:




