Visualizing Holt Winters Exponential Smoothing
==============================================
This chart shows actuals and a trend/smoothing line calculated through Holt-Winters exponential smoothing. However, this chart should work for any similar smoothing visualizations: i.e. it doesn't really care if it is Holt-Winters or another algorithm. The main thing is that it allows for visualization of two data columns as line graphs, where the 2nd column has initial and last values missing (depending on the depth of smoothing, or running averages, for instance).

Use of SVG Path mini language
-----------------------------
Once again we're using the SVG path mini language. Since there are values missing from the column with HW exponential smoothing (at the beginning and at the end, a natural result of applying the algorithm), we cannot simply use `d3.svg.line()`. So, I am using the SVG path mini language directly. This means, then, generating a string of coordinates for the lines to be drawn. That looks something like this: M0,0L10,0L10,10L10,0L0,0 which would create a little square.  `d3.svg.line()`  and  `d3.svg.area()`  are basically helper functions around this.

Data File
---------
A sample data file is supplied. This is the results of some analysis in R on tomatoes sold. First a seasonal adjustment was made, and then a Holt-Winters exponential smoothing was applied. The results were then exported as CSV. Of course, if you are using HANA, you could do this through direct R integration via SQLScript that embeds R script as well.

Attention: version impact for .profile file
-------------------------------------------
SAP Lumira development progresses quickly, and this extension was originally built in a previous version. The extension works just fine in SAP Lumira 1.21, but VizPacker can't read this profile file anymore and returns undefined. However, you should just be able to copy the render function, upload the data file and name the canvas fields, and use the content of the .profile file to understand how the data should be included.

Resources
---------
* Blog [SAP Lumira Chart Extensions with a Predictive Flavor](http://scn.sap.com/community/lumira/blog/2015/01/27/sap-lumira-chart-extensions-with-a-predictive-flavor)

