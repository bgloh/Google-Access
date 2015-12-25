# Google-Access
Google access

```html

<head>
  <title>Google sheet QUERRY</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
  <script src="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js"></script>
   <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.6/d3.min.js" charset="utf-8"></script>
<!--  <script src="https://googledrive.com/host/0B9LyIEern34dd2hScDhndGk2Q0E" type="text/javascript"></script> -->
  <script type="text/javascript" src="https://www.google.com/jsapi"></script> 
</head>
<body>
	
<div class="container">
  <h1>GOOGLE QUERRY</h1>
  <text><u>record ... 'font-family'='arial' </u></text>
  <br></br>
  <a href="https://script.google.com/macros/s/AKfycbxDriYxpBdQpm9iPOyOG67ivzEB9nXxMCHfmAJ7ZPiGoWCG8Vfe/exec" 
     class="btn btn-info" role="button">GoTo GOOGLE </a>
  <button type="button" class="btn btn-default" onclick="window.open('https://script.google.com/macros/s/AKfycbxDriYxpBdQpm9iPOyOG67ivzEB9nXxMCHfmAJ7ZPiGoWCG8Vfe/exec')">
	 Go to Google 2</button> 
</div>
<h5> This google pie chart: pieChart();   </h5>
<div id="chart_div" style="width:100; height:50"></div>

 
 
 <!-- ******** JAVA SCRIPT CUSTOM FUNCTIONS ************  -->
<script>
var matrix = [['apple',50],['orange',150],['olives', 12],['zucchini',5.5]];
var tableHead =['topping','slices'];

function pieChart(tableHead){
    
      // Load the Visualization API and the piechart package.
      google.load('visualization', '1.0', {'packages':['corechart']});

      // Set a callback to run when the Google Visualization API is loaded.
      google.setOnLoadCallback(drawChart);

      // Callback that creates and populates a data table,
      // instantiates the pie chart, passes in the data and
      // draws it.
       function drawChart() {

        // Create the data table.
        var data = new google.visualization.DataTable();
       // data.addColumn('string', 'Topping');
	   data.addColumn(tableHead[0],tableHead[1]);
        data.addColumn('number', 'Slices');
        data.addRows([
          ['Apple', 3],
          ['Orange', 3],
          ['Olives', 3],
          ['Zucchini', 1],
          ['Pepperoni', 2]
        ]);

        // Set chart options
        var options = {'title':'How Much Pizza I Ate Last Night',
                       'width':300,
                       'height':200};
        // Instantiate and draw our chart, passing in some options.
        var chart = new google.visualization.PieChart(document.getElementById('chart_div'));
        chart.draw(data, options);
        }
} 

   

function tableFromMatrix(matrix,tableHead)
{
var myTable = d3.select("body")
             .append("g") 
              .append("table")
              .attr("class","table table-stripped")
              .style("width", "50%")
              .style("margin-left", "20px");
thead = myTable.append("thead"),
tbody = myTable.append("tbody");           
thead.append("tr")
        .selectAll("th")
        .data(tableHead)
        .enter()
        .append("th")
        .text(function(d) { return d; })
		.attr("style","color : #234568")
		.style("font-size","80%")
		.style("text-align","center");;            

var tableRow = tbody
           .selectAll("tr")
           .data(matrix);

tableRow.enter().append("tr");
var tableData = tableRow.selectAll("td")
             .data(function(d,i) {return d;})
             .enter()
             .append("td")
             .text(function(d,i) {return d;})
             .attr("style","color : #234568")
              //.style("background-color",function(d,i){ return i % 2 ? "blue" : "#e0e0ee";})
              .style("font-size","80%")
              .style("text-align","center");
} 

// table from matrix
tableFromMatrix(matrix,tableHead);

pieChart(tableHead); 
    
</script>
</body>
'''




