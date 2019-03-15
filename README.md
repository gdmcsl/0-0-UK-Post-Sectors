# 0-0-UK-Post-Sectors
===================

#################################################################### 

UK Post Sectors
===============

#################################################################### 

Figure 0-0 code
===============

    library(ggplot2)
    library(ggpubr)

    ## Loading required package: magrittr

    library(magrittr)

    # read data to dataframe
    df<-read.csv("ukpostsectors.csv") 

    # scatter-chart
    v <- ggplot(df, aes(x=AverageLongitude, y=AverageLatitude, col=RowLabels)) # define initial plot object
    v <- v + geom_point() # give it scatter chart-type

    vline <- function(p, yValue){
      if(yValue<50){return(p)}else
        {
          p <- p + geom_point(x=0, y=yValue, colour="grey20", size=0.5)
          vline(p, yValue-0.2)
        }
    }
    v <- vline(v, 60)

    v <- v + xlim(c(-7.5,1.8))
    v <- v + labs(x=NULL, y=NULL)
    v <- v + theme(legend.position="none") # removes the legend

    # read data to dataframe
    df<-read.csv("ukpo-codes.csv") 

    # scatter-chart
    w <- ggplot(df, aes(x=AverageLongitude, y=AverageLatitude, col=RowLabels)) # define initial plot object
    w <- w + geom_point() # give it scatter chart-type
    w <- w + xlim(c(-7.5,1.8))
    w <- w + labs(x=NULL, y=NULL)
    w <- w + theme(legend.position="none") # removes the legend

    v #w

<img src="0-0 UK Post Sectors-1.png" style="display: block; margin: auto auto auto 0;" />

Figure 0.0 A scatter-plot showing average longitudes plotted against
average latitudes, by post-code sectors. Pivoted from a CSV file of
1,048,575 unique UK postcodes, from www.freemaptools.com. The vertical
dotted-line is the Greenwich Meridian.
