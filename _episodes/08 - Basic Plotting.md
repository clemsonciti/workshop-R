---
title: "Basic plotting with R"
teaching: 30
exercises: 0
questions:
- "How to plot in R"
objectives:
- "Learn using plotting tool in R"
- "Learn to export graphical to file"
keypoints:
- "Plot"
---

<!---
## Course content:
- Making exploratory graphs
- Principles of analytic graphics
- Plotting systems and graphics devices in R
- The base, lattice, and ggplot2 plotting systems in R

## Exploratory graph
### Why do we use graphs in data analysis?
- To understand data properties
- To find patterns in data
- To suggest modeling strategies
- To "debug" analyses
- To communicate results

## Ploting System
There are 3 main plotting systems in R:
### The Base plotting system
```
- Start with blank plot and build up the plot
- Plot is just a series of R command
- Flexible
```
###  The Lattice plotting system (using package::lattice)
```
- Plots created using single function call
- Good for putting many plots to screen
- Cannot add to plots once created
```

### The ggplot plotting system (using package::ggplot2)
```
- Similar to Lattice but easier
- Many default mode
- Flexible between Base and Lattice
```
Tue's old screenshots:
![image](https://user-images.githubusercontent.com/43855029/114093880-a7515980-9889-11eb-800e-0152f2e8c207.png)
![image](https://user-images.githubusercontent.com/43855029/114093825-94d72000-9889-11eb-953f-2b232708b37d.png)
![image](https://user-images.githubusercontent.com/43855029/114093954-b932fc80-9889-11eb-8532-f3db53f6278f.png)
![image](https://user-images.githubusercontent.com/43855029/114093764-82f57d00-9889-11eb-8e8a-bb7d11340f02.png)
![image](https://user-images.githubusercontent.com/43855029/114094073-dff13300-9889-11eb-9f97-6675f7408d04.png)
-->

R is a data analysis language, so naturally it comes with many built-in functions for plotting. Let's look at some of them, in application to the `mtcars` datast.

```r
data(mtcars)
dim(mtcars)
names(mtcars)
head(mtcars)
print(mtcars)
```

First, let's make a bar plot of the miles-per-gallon values of the 32 cars. `col` specifies the colour.
```r
barplot(mtcars$mpg, col="green")
```

Now, let's make a histogram for horsepower values.
```r
hist(mtcars$hp, col="magenta")
```
Let's display two jistorgrams on the same plot. We'll use the function `par` to specify that the two histograms will be plotted stacked to each other, one on the left and one on the right. 

```r
par(mfrow=c(1,2))
hist(mtcars$mpg,col="blue")
hist(mtcars$wt,col="blue")
```

Let's create a box plot for miles-per-gallon data. We'll have to reset the plot options to let R know we don't use multiple plots anymore; this is done with `dev.off()`.

```r
dev.off()
boxplot(mtcars$mpg,col="blue",main="Boxplot for mpg")
```

Now, let's make this box plot for every value of cylinders (`mtars$cyl`). We will use the same function `boxplot`, but with a few more parameters. We will specify the data explicitly, as well as `col` (for colour scheme), `main` (main figure title), `xlab` and `ylab` (X- and Y-axis labels). We will use the function `legend` to create a legend. We call `factors` to find out the unique cylinder values.

```r
factor(mtcars$cyl)
boxplot(mpg~cyl,data=mtcars,
        col=terrain.colors(3),main="MPG by car cylinders",
        xlab = "cylinders",ylab="mpg")
legend("topright",c("4","6","8"),fill = terrain.colors(3))
```

And a scatter plot
```r
plot(mtcars$mpg,mtcars$wt,main="Car Fuel vs Weight",
     xlab="Mileage per Gallon",ylab="Weight",
     col = mtcars$cyl,pch=16,cex=3)
legend("topright",legend=c(8,6,4),pch=16,cex=3,
       col=c("grey","magenta","blue"))
```

Here, `pch` is the plotting character; 16 corresponds to a circle. The full table of plotting characters is here:
![img](https://r-lang.com/wp-content/uploads/2021/02/plot-character-in-R.png)


```
pch: the plotting character (default is open circle)
lty: the line type (default is solid line), can be dashed, dotted, etc.
lwd: the line width, specified as an integer multiple
col: the plotting color, specified as a number, string, or hex code; the colors() function gives you a vector of colors by name
xlab: character string for the x-axis label
ylab: character string for the y-axis label
```
### Important BASE plotting function
```
plot: make a scatterplot, or other type of plot depending on the class of the object being plotted
lines: add lines to a plot, given a vector x values and a corresponding vector of y values (or a 2-column matrix); this function just connects the dots
points: add points to a plot
text: add text labels to a plot using specified x, y coordinates
title: add annotations to x, y axis labels, title, subtitle, outer margin
mtext: add arbitrary text to the margins (inner or outer) of the plot
axis: adding axis ticks/labels
```

### Motor Trend Car Road Tests example
The data was extracted from the 1974 Motor Trend US magazine, and comprises fuel consumption and 10 aspects of automobile design and performance for 32 automobiles (1973--74 models).
- Usage:
```r
data(mtcars)
dim(mtcars)
names(mtcars)
head(mtcars)
print(mtcars)
```
* Simple Summaries of Data Simple Summaries of Data
Five-number summary
```r
summary(mtcars)
```
* Boxplots:
```r
boxplot(mtcars$mpg,col="blue",main="Boxplot for mpg")
```
```r
factor(mtcars$cyl)
boxplot(mpg~cyl,data=mtcars,
        col=terrain.colors(3),main="MPG by car cylinders",
        xlab = "cylinders",ylab="mpg")
legend("topright",c("4","6","8"),fill = terrain.colors(3))
```
![image](https://user-images.githubusercontent.com/43855029/114093764-82f57d00-9889-11eb-8e8a-bb7d11340f02.png)

* Histograms
```r
hist(mtcars$hp, col="magenta")
```
![image](https://user-images.githubusercontent.com/43855029/114093825-94d72000-9889-11eb-953f-2b232708b37d.png)

* Barplot
```r
barplot(mtcars$mpg,col="green",
        main="MPG for 32 cars")
```
![image](https://user-images.githubusercontent.com/43855029/114093880-a7515980-9889-11eb-800e-0152f2e8c207.png)

* Multiple historgrams
```r
par(mfrow=c(1,2))
hist(mtcars$mpg,col="blue")
hist(mtcars$wt,col="blue")
```
![image](https://user-images.githubusercontent.com/43855029/114093954-b932fc80-9889-11eb-8532-f3db53f6278f.png)

* Scatter plot
```r
plot(mtcars$mpg,mtcars$wt,main="Car Fuel vs Weight",
     xlab="Milage per Gallon",ylab="Weight",
     col = mtcars$cyl,pch=16,cex=3)
legend("topright",legend=c(8,6,4),pch=16,cex=3,
       col=c("grey","magenta","blue"))
```
![image](https://user-images.githubusercontent.com/43855029/114094073-dff13300-9889-11eb-9f97-6675f7408d04.png)


## Graphics Devices
A graphics device is something where you can make a plot appear When you make a plot in R, it has to be "sent" to a specific graphics device.

- A window on your computer (screen device): quick visualization
- A PDF, PNG, JPEG file (file device) #recommended for documents, paper, presentation

The most common place for a plot to be "sent" is the screen device

- On a Mac the screen device is launched with the quartz()
- On Windows the screen device is launched with windows()
- On Unix/Linux the screen device is launched with x11()
- save graphic to PDF
- save graphic to PNG, JPEG

```r
dev.copy(png,"filename.png") # to save the image to file
dev.off() # to close all the graphical devices
```

