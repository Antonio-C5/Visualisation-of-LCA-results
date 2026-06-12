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

Tabelle1 is then imported into RStudio.
<br>
This is how Tabelle1 looks like:
<br>
<br>
<img width="1452" height="742" alt="Dataset_Tabelle1" src="https://github.com/user-attachments/assets/b8141a71-4aa9-421c-8a20-d81fd316e4dc" />

Tabelle1 is assigned to the object named Stacked_barchart_data.
<br>
Now, let's start "transforming" the dataset into the first version of our chart, which resembles the one in the paper using the package ggplot2.
<br>
<br>
```r
Stacked_barchart_data |>
  ggplot(aes(x = Impact_category, y = Relative_to_total)) + 
  geom_col(aes(fill = Process), col = "white", width = 0.6) + 
  theme_bw() + 
  labs(x = "", 
       y = "") + 
  theme(axis.title = element_text(size = 20), 
        axis.text = element_text(size = 18), 
        legend.title = element_text(size = 18), 
        legend.text = element_text(size = 15), 
        legend.key.size = unit(1, "cm"))
```
<br>
<br>
The following code will produce the following chart (1).
<br>
<br>
<img width="1891" height="957" alt="image" src="https://github.com/user-attachments/assets/760219ea-6e65-46ff-9fb2-367109d4f41d" />
<br>
Well, the order of the processes shown in the legend is different compared to the original image; the colors are different; the labels on the x-axis do not fit in the available space.
<br>
<br>
How to fix that? As you may notice, ggplot2 inserts the items in the legend by alphabetical order.
<br>
Well, it is not necessary to add such a detail. But we are going to do that for the sake of the example. Let's start be changing the order of the Processes and substituting the label Processing with Pelleting, as indicated in the original image.
<br>
<br>
```r
Stacked_barchart_data$Process <- factor(Stacked_barchart_data$Process, 
                                        levels = c("Transport", 
                                       "Pelleting", # instead of Processing 
                                       "Crop removal", 
                                       "Harvest",
                                       "Maintenance", 
                                       "Planting", 
                                       "Land preparation"))
```
<br>
<br>
We need also to organize the impact category in the same order:
<br>
<br>
```r
Stacked_barchart_data$Impact_category <- factor(Stacked_barchart_data$Impact_category, 
                                                levels = c("Acidification potential", 
                                                           "Eutrophication potential", 
                                                           "Global warming potential", 
                                                           "Cumulative Energy Demand")) 
```
<br>
<br>
Let's check what the output of such a change is. Scale_fill_manual is used to change the colour of the stacked bars.
<br>
<br>
```r
Stacked_barchart_data |> 
  ggplot(aes(x = Impact_category, y = Relative_to_total)) + 
  geom_col(aes(fill = Process), col = "white", width = 0.3) +
  theme_light() + 
  labs(x = "", 
       y = "", 
       fill = "") + 
  theme(axis.title = element_text(size = 20), 
        axis.text.x = element_text(size = 10, angle = 45, vjust = 0.5), 
        axis.text.y = element_text(size = 10), 
        legend.title = element_text(size = 15), 
        legend.text = element_text(size = 13), 
        legend.key.size = unit(0.5, "cm")) + 
  scale_y_continuous(limits = c(0, 100), 
                     breaks = seq(0, 100, 10)) + 
  scale_fill_manual(values = c("#93B1EB", "#F87531", "#089CC5", "#694189", "#6A8701","#8D1920", "#12396B" ))  
```
<br>
<br>
<img width="1887" height="956" alt="image" src="https://github.com/user-attachments/assets/0deeca31-1c0c-4316-a975-8d53ba92d356" />
<br>
<br>






