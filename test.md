---
layout: none
time-horizon: 36
---
<html>
<head>
	<title>My first chart using FusionCharts Suite XT</title>
	<script type="text/javascript" src="https://cdn.fusioncharts.com/fusioncharts/latest/fusioncharts.js"></script>
	<script type="text/javascript" src="https://cdn.fusioncharts.com/fusioncharts/latest/themes/fusioncharts.theme.fusion.js"></script>
	<script type="text/javascript">

	</script>
	</head>
	<body>

<h2 id="title"></h2>


<div id="number"></div>
<div id="Array"></div>
<div id="Object"></div>



<script>
var returnArray = [

  {% for return in site.data.returns %}{{ return.Return }}, {% endfor %}

];

var monthArray = [

  {% for return in site.data.returns %}{{ return.Month }}, {% endfor %}

];

var yearArray = [

  {% for return in site.data.returns %}{{ return.Year }}, {% endfor %}

];

var length = returnArray.length - {{ page.time-horizon }};
var startMonth = Math.floor(Math.random() * length);
var endMonth = startMonth + {{ page.time-horizon }};
var month = monthArray[startMonth];
var year = yearArray[startMonth];
console.log(length);
console.log(startMonth);
console.log(endMonth);
const portfolioValue = [100];
const portfolioValueA = [100];
const portfolioValueB = [100];
const portfolioValueC = [100];
const portfolioValueD = [100];
const portfolioValueE = [100];
const portfolioValueF = [100];
const portfolioValueG = [100];
const portfolioValueH = [100];
const portfolioValueI = [100];
const portfolioValueJ = [100];
var randomNumbers = [];
var timeHorizon = {{ page.time-horizon }};


function market(){
  document.getElementById("title").innerHTML = startMonth + " Year: " + year + " Month: " + month;


  var counter;
  var counterMax = timeHorizon * 10;
  for (counter = 0; counter < counterMax; counter++) {
    randomNumbers[counter] = Math.random() * 2;
  }

  var text = "";
  value = 100;
  var i;
  var p = 1;
  for (i = startMonth; i < endMonth; i++) {
    text += returnArray[i] + " " + value + "<br>";
    value = value * (1 + returnArray[i]);
    value = value.toFixed(2);
    portfolioValue[p] = value;
    if (randomNumbers[p-1] < 1) {
      portfolioValueA[p] = (portfolioValueA[p-1]*(1 + returnArray[i])).toFixed(2);
      } else {
      portfolioValueA[p] = (portfolioValueA[p-1]*(1 - returnArray[i])).toFixed(2);
      }
      if (randomNumbers[p + timeHorizon - 1] < 1) {
        portfolioValueB[p] = (portfolioValueB[p-1]*(1 + returnArray[i])).toFixed(2);
        } else {
        portfolioValueB[p] = (portfolioValueB[p-1]*(1 - returnArray[i])).toFixed(2);
        }
        if (randomNumbers[p + (timeHorizon * 2) - 1] < 1) {
          portfolioValueC[p] = (portfolioValueC[p-1]*(1 + returnArray[i])).toFixed(2);
          } else {
          portfolioValueC[p] = (portfolioValueC[p-1]*(1 - returnArray[i])).toFixed(2);
          }
          if (randomNumbers[p + (timeHorizon * 3) - 1] < 1) {
            portfolioValueD[p] = (portfolioValueD[p-1]*(1 + returnArray[i])).toFixed(2);
            } else {
            portfolioValueD[p] = (portfolioValueD[p-1]*(1 - returnArray[i])).toFixed(2);
            }
            if (randomNumbers[p + (timeHorizon * 4) - 1] < 1) {
              portfolioValueE[p] = (portfolioValueE[p-1]*(1 + returnArray[i])).toFixed(2);
              } else {
              portfolioValueE[p] = (portfolioValueE[p-1]*(1 - returnArray[i])).toFixed(2);
              }

              if (randomNumbers[p + (timeHorizon * 5) - 1] < 1) {
                portfolioValueF[p] = (portfolioValueF[p-1]*(1 + returnArray[i])).toFixed(2);
                } else {
                portfolioValueF[p] = (portfolioValueF[p-1]*(1 - returnArray[i])).toFixed(2);
                }

                if (randomNumbers[p + (timeHorizon * 6) - 1] < 1) {
                  portfolioValueG[p] = (portfolioValueG[p-1]*(1 + returnArray[i])).toFixed(2);
                  } else {
                  portfolioValueG[p] = (portfolioValueG[p-1]*(1 - returnArray[i])).toFixed(2);
                  }
                  if (randomNumbers[p + (timeHorizon * 7) - 1] < 1) {
                    portfolioValueH[p] = (portfolioValueH[p-1]*(1 + returnArray[i])).toFixed(2);
                    } else {
                    portfolioValueH[p] = (portfolioValueH[p-1]*(1 - returnArray[i])).toFixed(2);
                    }

                    if (randomNumbers[p + (timeHorizon * 8) - 1] < 1) {
                      portfolioValueI[p] = (portfolioValueI[p-1]*(1 + returnArray[i])).toFixed(2);
                      } else {
                      portfolioValueI[p] = (portfolioValueI[p-1]*(1 - returnArray[i])).toFixed(2);
                      }

                      if (randomNumbers[p + (timeHorizon * 9) - 1] < 1) {
                        portfolioValueJ[p] = (portfolioValueJ[p-1]*(1 + returnArray[i])).toFixed(2);
                        } else {
                        portfolioValueJ[p] = (portfolioValueJ[p-1]*(1 - returnArray[i])).toFixed(2);
                        }
    p= p + 1;

  }

{% comment %}
  document.getElementById("number").innerHTML = text;
  document.getElementById("Array").innerHTML = portfolioValue + "XXX" + portfolioValueA[10];
  {% endcomment %}

  FusionCharts.ready(function(){
    var chartObj = new FusionCharts({
  type: 'line',
  renderAt: 'chart-container',
  width: '680',
  height: '390',
  dataFormat: 'json',
  dataSource: {
      "chart": {
          "theme": "fusion",
          "caption": "Total footfall in Bakersfield Central",
          "subCaption": "Last week",
          "xAxisName": "Day",
          "yAxisName": "No. of Visitors",
          "lineThickness": "2"
      },
      "data": [

      {% for counter in (0..page.time-horizon) %}
      {
          "label": "{{ counter }}",
          "value": portfolioValue[{{ counter }}]
      },

      {% endfor %}





      ],

  }
  });
    chartObj.render();
  });
  FusionCharts.ready(function() {
    var visitChart = new FusionCharts({
      type: 'msline',
      renderAt: 'chart-container2',
      width: '700',
      height: '400',
      dataFormat: 'json',
      dataSource: {
        "chart": {
          "theme": "fusion",
          "caption": "36 Month Stock Market Returns Starting in",
          "subCaption": "Bakersfield Central vs Los Angeles Topanga",
          "xAxisName": "Month"
        },
        "categories": [{
          "category": [
          {% for counter in (0..page.time-horizon) %}
          {
              "label": "{{ counter }}"
          },

          {% endfor %}

          ]
        }],
        "dataset": [{
            "seriesname": "Market Return",
            "data": [

            {% for counter in (0..page.time-horizon) %}
            {
                "value": portfolioValue[{{ counter }}]
            },

            {% endfor %}



            ]
          },
          {
            "seriesname": "Portfolio A",
            "data": [
            {% for counter in (0..page.time-horizon) %}
            {
                "value": portfolioValueA[{{ counter }}]
            },

            {% endfor %}
            ]
          },
          {
            "seriesname": "Portfolio B",
            "data": [
            {% for counter in (0..page.time-horizon) %}
            {
                "value": portfolioValueB[{{ counter }}]
            },

            {% endfor %}
            ]
          },

          {
            "seriesname": "Portfolio C",
            "data": [
            {% for counter in (0..page.time-horizon) %}
            {
                "value": portfolioValueC[{{ counter }}]
            },

            {% endfor %}
            ]
          },

          {
            "seriesname": "Portfolio D",
            "data": [
            {% for counter in (0..page.time-horizon) %}
            {
                "value": portfolioValueD[{{ counter }}]
            },

            {% endfor %}
            ]

          },

          {
            "seriesname": "Portfolio E",
            "data": [
            {% for counter in (0..page.time-horizon) %}
            {
                "value": portfolioValueE[{{ counter }}]
            },

            {% endfor %}
            ]

          },

          {
            "seriesname": "Portfolio F",
            "data": [
            {% for counter in (0..page.time-horizon) %}
            {
                "value": portfolioValueF[{{ counter }}]
            },

            {% endfor %}
            ]

          },

          {
            "seriesname": "Portfolio G",
            "data": [
            {% for counter in (0..page.time-horizon) %}
            {
                "value": portfolioValueG[{{ counter }}]
            },

            {% endfor %}
            ]

          },

          {
            "seriesname": "Portfolio H",
            "data": [
            {% for counter in (0..page.time-horizon) %}
            {
                "value": portfolioValueH[{{ counter }}]
            },

            {% endfor %}
            ]

          },

          {
            "seriesname": "Portfolio I",
            "data": [
            {% for counter in (0..page.time-horizon) %}
            {
                "value": portfolioValueI[{{ counter }}]
            },

            {% endfor %}
            ]

          },

          {
            "seriesname": "Portfolio J",
            "data": [
            {% for counter in (0..page.time-horizon) %}
            {
                "value": portfolioValueJ[{{ counter }}]
            },

            {% endfor %}
            ]

          },
        ],

      }
    }).render();
  });

}





market();





</script>

{% comment %}
<div id="chart-container">FusionCharts XT will load here!</div>
{% endcomment %}

<div id="chart-container2">The chart is loading. If the chart does not load, you probably have javascript disabled.</div>
	</body>
</html>
