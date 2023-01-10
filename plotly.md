---
title: "Interactive Plotly Webpage"
author: "Linli"
date: "2023-01-10"
output: 
  ioslides_presentation:
    keep_md: true
---



## Synopsis {.smaller}

Following instructions have been given for the assignment -   

1. Create a web page presentation using R Markdown that features a plot created with Plotly.  
2. Host your webpage on either RPubs, GitHub Pages, or NeoCities.   
3. Your webpage must contain the date that you created the document, and it must contain a plot created with Plotly.

The **Interactive Plots** presented in this Assignment are as follows -

1. A **Heatmap** depicting the Daily Ozone Levels in New York over a period of 5 months (May to September 1973).
2. A **Time-Series chart** of the Population of the United States (in millions) for the period 1790-1970.

## Data Processing for Plot 1 : Heatmap R Code{.smaller}


```r
library(datasets);library(plotly);library(reshape2)
data("airquality") ## Load the airquality dataset
airquality$Month=as.factor(airquality$Month) ## Convert Month to factor
ozone_daily=airquality[,c(1,5,6)] ## Extract Ozone, Month and Day columns
## Convert Long format to Wide for input to Heatmap
ozone_daily=dcast(ozone_daily,Day~Month,value.var = "Ozone") 
ozone_daily=as.matrix(ozone_daily[,-1]) ## Convert to Matrix
colnames(ozone_daily)=c("May","June","July","August","September")
## Plotly command
plot_ly(z=ozone_daily,colorscale="Hot",x=colnames(ozone_daily),type="heatmap",colorbar = list(title = "Ozone Levels (parts per billion)"))%>%layout(title = "Daily Ozone Levels in New York, May to September 1973", xaxis = list(title = "Month"),yaxis = list(title = "Day"))
```

## Plotly - Interactive Plot 1: Heatmap


```{=html}
<div id="htmlwidget-6c8178f706c044882883" style="width:720px;height:432px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-6c8178f706c044882883">{"x":{"visdat":{"91da133eb79b":["function () ","plotlyVisDat"]},"cur_data":"91da133eb79b","attrs":{"91da133eb79b":{"z":[[41,null,135,39,96],[36,null,49,9,78],[12,null,32,16,73],[18,null,null,78,91],[null,null,64,35,47],[28,null,40,66,32],[23,29,77,122,20],[19,null,97,89,23],[8,71,97,110,21],[null,39,85,null,24],[7,null,null,null,44],[16,null,10,44,21],[11,23,27,28,28],[14,null,null,65,9],[18,null,7,null,13],[14,21,48,22,46],[34,37,35,59,18],[6,20,61,23,13],[30,12,79,31,24],[11,13,63,44,16],[1,null,16,21,13],[11,null,null,9,23],[4,null,null,null,36],[32,null,80,45,7],[null,null,108,168,14],[null,null,20,73,30],[null,null,52,null,null],[23,null,82,76,14],[45,null,50,118,18],[115,null,64,84,20],[37,null,59,85,null]],"colorscale":"Hot","x":["May","June","July","August","September"],"colorbar":{"title":"Ozone Levels (parts per billion)"},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"heatmap"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Daily Ozone Levels in New York, May to September 1973","xaxis":{"domain":[0,1],"automargin":true,"title":"Month"},"yaxis":{"domain":[0,1],"automargin":true,"title":"Day"},"scene":{"zaxis":{"title":[]}},"hovermode":"closest","showlegend":false,"legend":{"yanchor":"top","y":0.5}},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"colorbar":{"title":"Ozone Levels (parts per billion)","ticklen":2,"len":0.5,"lenmode":"fraction","y":1,"yanchor":"top"},"colorscale":"Hot","showscale":true,"z":[[41,null,135,39,96],[36,null,49,9,78],[12,null,32,16,73],[18,null,null,78,91],[null,null,64,35,47],[28,null,40,66,32],[23,29,77,122,20],[19,null,97,89,23],[8,71,97,110,21],[null,39,85,null,24],[7,null,null,null,44],[16,null,10,44,21],[11,23,27,28,28],[14,null,null,65,9],[18,null,7,null,13],[14,21,48,22,46],[34,37,35,59,18],[6,20,61,23,13],[30,12,79,31,24],[11,13,63,44,16],[1,null,16,21,13],[11,null,null,9,23],[4,null,null,null,36],[32,null,80,45,7],[null,null,108,168,14],[null,null,20,73,30],[null,null,52,null,null],[23,null,82,76,14],[45,null,50,118,18],[115,null,64,84,20],[37,null,59,85,null]],"x":["May","June","July","August","September"],"type":"heatmap","xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```

## Plot 2 : Time-Series Chart R Code{.smaller}


```r
library(datasets)
library(plotly)
data(uspop) ## Load the data set that gives the population of the United States 
## (in millions) as recorded by the decennial census for the period 1790–1970.
```


```r
## Plotly Command
plot_ly(x=~time(uspop),y=~uspop,type="scatter",mode="lines") %>% layout(title = "U.S. Population in millions for the period 1790-1970", xaxis = list(title = "Year"),yaxis = list(title = "U.S. Population (millions)"))
```

```{=html}
<div id="htmlwidget-0b249f829c83d5feba20" style="width:720px;height:432px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-0b249f829c83d5feba20">{"x":{"visdat":{"925b60c59182":["function () ","plotlyVisDat"]},"cur_data":"925b60c59182","attrs":{"925b60c59182":{"x":{},"y":{},"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"U.S. Population in millions for the period 1790-1970","xaxis":{"domain":[0,1],"automargin":true,"title":"Year"},"yaxis":{"domain":[0,1],"automargin":true,"title":"U.S. Population (millions)"},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1790,1800,1810,1820,1830,1840,1850,1860,1870,1880,1890,1900,1910,1920,1930,1940,1950,1960,1970],"y":[3.93,5.31,7.24,9.64,12.9,17.1,23.2,31.4,39.8,50.2,62.9,76,92,105.7,122.8,131.7,151.3,179.3,203.2],"mode":"lines","type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```


## Plotly - Interactive Plot 2: Time-Series Chart


```{=html}
<div id="htmlwidget-60b9ce9247a07386c7ec" style="width:720px;height:432px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-60b9ce9247a07386c7ec">{"x":{"visdat":{"925b2c5c1871":["function () ","plotlyVisDat"]},"cur_data":"925b2c5c1871","attrs":{"925b2c5c1871":{"x":{},"y":{},"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"U.S. Population in millions for the period 1790-1970","xaxis":{"domain":[0,1],"automargin":true,"title":"Year"},"yaxis":{"domain":[0,1],"automargin":true,"title":"U.S. Population (millions)"},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1790,1800,1810,1820,1830,1840,1850,1860,1870,1880,1890,1900,1910,1920,1930,1940,1950,1960,1970],"y":[3.93,5.31,7.24,9.64,12.9,17.1,23.2,31.4,39.8,50.2,62.9,76,92,105.7,122.8,131.7,151.3,179.3,203.2],"mode":"lines","type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```
