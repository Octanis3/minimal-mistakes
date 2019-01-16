---
  title: "Configuration Center"
  layout: splash
  permalink: /config
  sidebar: false
  header:
      overlay_image: /assets/img/pcbs.JPG
      caption: "RFID readers powering the smart Nestboxes"
---

<html>
  <head>
    <title>Nestbox Control Center</title>
    <style>
      html, pre {
        font-family: sans-serif;
      }

      body {
        margin: 0 auto;
        background-color: white;
      }


      label {
        width: 200px;
        margin-right: 33px;
      }

      select {
        width: 350px;
        padding: 5px;
      }

      .slidecontainer {
      width: 96%;
      }

      .slider {
        -webkit-appearance: none;
        width: 100%;
        height: 25px;
        background: #d3d3d3;
        outline: none;
        opacity: 0.7;
        -webkit-transition: .2s;
        transition: opacity .2s;
      }

      .slider:hover {
        opacity: 1;
      }

      .slider::-webkit-slider-thumb {
        -webkit-appearance: none;
        appearance: none;
        width: 25px;
        height: 25px;
        background: #4CAF50;
        cursor: pointer;
      }

      .slider::-moz-range-thumb {
        width: 25px;
        height: 25px;
        background: #4CAF50;
        cursor: pointer;
      }
    </style>
    <!--[if lt IE 9]>
      <script src="https://cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.3/html5shiv.js"></script>
    <![endif]-->
  </head>
  <body>
    <h2 id="online_status">Please connect to the Nestbox Wi-Fi.</h2>
    <h4>Nestbox ID: <em id="mac_addr">?</em></h4>
    <h4>Current time on your Computer: <em id="time_local">?</em></h4>
    <h4>Current time on the Nestbox: <em id="time_remote">?</em></h4>
     <button type="button" id="btn_fetch_time" style="width:150px"
     >Get time from the Nestbox
     </button> 
     <button type="button" id="btn_set_time" style="width:150px" >Set time on the Nestbox to browser time</button> 

     <div class="slidecontainer">
      <p>Daily shut-down time: <b id="shdn">9:00</b> CET</p>
        <input type="range" min="6" max="138" value="54" class="slider" id="shdn_slider">
      <p>Daily wake-up time: <b id="wake">17:00</b> CET</p>
        <input type="range" min="6" max="138" value="102" class="slider" id="wake_slider">
      <p id="rtcwarning" style="color:red;"></p>

    </div>
    <div>
      <button type="button" id="btn_get_rtc" style="width:170px"
     >Fetch programmed shut-down and wake-up times.
     </button> 

      <button type="button" id="btn_set_rtc" style="width:170px" >Set shut-down and wake-up times</button> 
    </div>

    <p>Programmed shutdown: Nestbox is asleep form <b id="shdn_dev">?</b> to <b id="wake_dev">?</b> CET.</p>

     <h4>Current battery level: <em id="battery_level">?</em></h4>


    <hr>


    <h3> Weight measurement </h3>

     <table border="1" style="text-align: left;">
      <tr>
        <th>measured ADC sensor value: <em id="adc_val">?</em></th>
        <th>measured ADC offset value: <em id="offset_val">?</em></th>
      </tr>
      <tr>
      </tr>
      <tr>
        <th>ADC calculated slope: <input type="number" id="ADC_scaling" value="0.0"></th>
        <th>ADC calculated offset: <input type="number" id="ADC_offset" value="0.0"></th>
      </tr>
    </table>

    <div>
      <button type="button" id="btn_weight_update" style="width:130px"
       >Get new weight measurement.
       </button> 
        <button type="button" id="btn_offset_update" style="width:130px"
       >Get last offset value.</button>
       <!--button type="button" id="get_adc_final_value" style="width:130px"
       >Get ADC scaling value.
       </button--> 
      <h4>Estimated weight: <em id="weight_estimate">?</em></h4>
    </div>


<hr>  
  <button type="button" id="btn_start_calib" style="width:130px"
     >Start Calibration mode
     </button> 
  <button type="button" id="btn_stop_calib" style="width:130px"
     >Stop Calibration mode
     </button> 
  <p id="calib_status" style="color:black;"></p>

<pre> 
<table style="width:100%">
  <tr>
  	<th>ID</th>
    <th>ADC sensor value</th>
    <th>Weight (g)</th> 
    <th>Insert from above</th> 
  </tr>
  <tr>
  	<td>N°1</td> 
   	<td><input type="text" id="adc_sensor_value1" value="?"></td>
	<td><input type="number" id="manual_weight1" value="110"></td>	
	<td><button type="button" id="btn_get1" style="width:130px">Insert ADC value</button></td>

  </tr>
  <tr>
  	<td>N°2</td> 
    <td><input type="text" id="adc_sensor_value2" value="?"></td>
    <td><input type="number" id="manual_weight2" value="219"></td>
    <td><button type="button" id="btn_get2" style="width:130px">Insert ADC value</button></td>
  </tr>
  <tr>
  	<td>N°3</td> 
    <td><input type="text" id="adc_sensor_value3" value="?"></td>
    <td><input type="number" id="manual_weight3" value="328"></td>
    <td><button type="button" id="btn_get3" style="width:130px">Insert ADC value</button></td>
  </tr>
  <tr>
  	<td>N°4</td> 
    <td><input type="text" id="adc_sensor_value4" value="?"></td>
    <td><input type="number" id="manual_weight4" value="438"></td>
    <td><button type="button" id="btn_get4" style="width:130px">Insert ADC value</button></td>
  </tr>
  <tr>
  	<td>N°5</td> 
    <td><input type="text" id="adc_sensor_value5" value="?"></td>
    <td><input type="number" id="manual_weight5" value="547"></td>
    <td><button type="button" id="btn_get5" style="width:130px">Insert ADC value</button></td>
  </tr>
</table>
<button type="button" id="btn_get_adc_final_value" style="width:150px">Calculate</button>	

<table>
	<tr>
	<td></td>
	<td>Results</td>
	</tr>
	<tr>
	<td>Slope</td>
	<td><input type="text" id="ADC_slope"></td>
	</tr>
	<tr>
	<td>Intercept</td>
	<td><input type="text" id="ADC_intercept"></td>
	</tr>
	<tr>
	<td>Correlation</td>
	<td><input type="text" id="ADC_r2"></td>
	</tr>
</table>



<style>table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
}</style>

    </pre>

    <script>
      var onlineStatus = document.getElementById('online_status');  
      var idDisplay = document.getElementById('mac_addr');
      var timestampDisplay = document.getElementById('time_local');
      var timestampRemoteDisplay = document.getElementById('time_remote');
      var batterylevel = document.getElementById('battery_level');
      var weightEstimate = document.getElementById('weight_estimate');
      var offsetVal = document.getElementById('offset_val');
      var adcVal = document.getElementById('adc_val');
      var b_field = document.getElementById('ADC_offset');
      var a_field = document.getElementById('ADC_scaling');

      var btnFetch = document.getElementById('btn_fetch_time');
      var btnSet = document.getElementById('btn_set_time');
      var btnFetchRTC = document.getElementById('btn_get_rtc');
      var btnSetRTC = document.getElementById('btn_set_rtc');

      var btnWeight = document.getElementById('btn_weight_update');
      var btnOffset = document.getElementById('btn_offset_update');

      var btnStartCalib = document.getElementById('btn_start_calib');
      var btnStopCalib = document.getElementById('btn_stop_calib');
      var calibStatus = document.getElementById('calib_status');

      var shdn_slider = document.getElementById("shdn_slider");
      var wake_slider = document.getElementById("wake_slider");
      
      var shdn_time = document.getElementById("shdn");
      var wake_time = document.getElementById("wake");
      var rtcwarning = document.getElementById("rtcwarning");
      var shdn_dev = document.getElementById("shdn_dev");
      var wake_dev = document.getElementById("wake_dev");
      var adcSensorvalue1 = document.getElementById("adc_sensor_value1");
      var adcSensorvalue2 = document.getElementById("adc_sensor_value2");
      var adcSensorvalue3 = document.getElementById("adc_sensor_value3");
      var adcSensorvalue4 = document.getElementById("adc_sensor_value4");
      var adcSensorvalue5 = document.getElementById("adc_sensor_value5");
      var testnbresensorvalue = 0;

      var btnget1 = document.getElementById("btn_get1");
      var btnget2 = document.getElementById("btn_get2");
      var btnget3 = document.getElementById("btn_get3");
      var btnget4 = document.getElementById("btn_get4");
      var btnget5 = document.getElementById("btn_get5");

      var manualweight1 = document.getElementById("manual_weight1");
      var manualweight2 = document.getElementById("manual_weight2");
      var manualweight3 = document.getElementById("manual_weight3");
      var manualweight4 = document.getElementById("manual_weight4");
      var manualweight5 = document.getElementById("manual_weight5");

      var BtngetADCscalingFinalvalue = document.getElementById("btn_get_adc_final_value");
      var ADCslope = document.getElementById("ADC_slope");
      var ADCintercept = document.getElementById("ADC_intercept");
      var ADCr2 = document.getElementById("ADC_r2");
      var AllFieldsFull = document.getElementById("all_fields_full");
      var resultADC = document.getElementById("Result_adc");



      // Update the current slider value (each time you drag the slider handle)
      shdn_slider.oninput = function() {
        shdn_time.innerHTML = Math.floor(this.value/6) + ":" + (this.value*10-Math.floor(this.value/6)*60);
        if(shdn_slider.value>wake_slider.value-6)
        {
          rtcwarning.innerHTML = "Wake-up time must be at least one hour after shut-down time!"
        }
        else
        {
          rtcwarning.innerHTML = "";
        }
      } 

      // Update the current slider value (each time you drag the slider handle)
      wake_slider.oninput = function() {
        wake_time.innerHTML = Math.floor(this.value/6) + ":" + (this.value*10-Math.floor(this.value/6)*60);
        if(shdn_slider.value>wake_slider.value-6)
        {
          rtcwarning.innerHTML = "Wake-up time must be at least one hour after shut-down time!";
        }
        else
        {
          rtcwarning.innerHTML = "";
        }
      }

      btnFetchRTC.onclick = function() {
        var url = "http://www.nestbox.local/rtcAlarmUpdate";
        fetch(url).then(function(response) {
          response.text().then(function(text) {
            parseServerResponse(text);
          });
        });  
      };

      btnSetRTC.onclick = function() {
        var ph = "ph="+Math.floor(shdn_slider.value/6-1);
        var pm = "&pm="+(shdn_slider.value*10-Math.floor(shdn_slider.value/6)*60);
        var rh = "&rh="+Math.floor(wake_slider.value/6-1);
        var rm = "&rm="+(wake_slider.value*10-Math.floor(wake_slider.value/6)*60);

        var url = "http://www.nestbox.local/rtcAlarmUpdate?"+ph+pm+rh+rm;
        fetch(url).then(function(response) {
          response.text().then(function(text) {
            parseServerResponse(text);
          });
        });  
      };




      function updateClock()
      {
        var date = new Date();
        var t = date.getTime();

        
        var dt = new Date(t);
        var hr = dt.getHours();
        var m = "0" + dt.getMinutes();
        var s = "0" + dt.getSeconds();
        var timestamp =  hr+ ':' + m.substr(-2) + ':' + s.substr(-2); 
        timestampDisplay.textContent = dt.toLocaleString() //timestamp;

        setTimeout(updateClock, 1000);
      }
      updateClock();

      function parseServerResponse(text)
      {
        if(text)
        {
           onlineStatus.textContent = "Device online!";
           if(idDisplay.textContent == '?')
           {
             fetchMac();
           }
        }
        if(text[0] == 'B')
        {
          var voltage = parseInt(text.substr(1,10))/1000;
          console.log(voltage);

          batterylevel.textContent = voltage + " Volts";
        } 
        if(text[0] == 'W')
        {
          var weight = parseInt(text.substr(1,20));
          adcVal.textContent = weight;
                  calculateWeight();
        }
        if(text[0] == 'O')
        {
          var weight = parseInt(text.substr(1,20));
          offsetVal.textContent = weight;
                  calculateWeight();
        }
        if(text[0] == 'L')
        {
          calibStatus.innerHTML = "Calibration mode STARTED"
          calibStatus.style = "color:green;"

        }
        if(text[0] == 'l')
        {
          calibStatus.innerHTML = "Calibration mode OFF"
          calibStatus.style = "color:black;"
        }
        if(text[0] == 'Z')
        {
          var timeremote = parseInt(text.substr(1,11));
          console.log(timeremote);
          
          var dt = new Date(timeremote*1000);
          var hr = dt.getHours();
          var m = "0" + dt.getMinutes();
          var s = "0" + dt.getSeconds();
          var timestamp =  hr+ ':' + m.substr(-2) + ':' + s.substr(-2); 
          timestampRemoteDisplay.textContent = dt.toLocaleString(); //timestamp;

        }
        if(text[0] == 'S')
        {
          var rtcremote = parseInt(text.substr(1,11));
          
          var ph = ((rtcremote>>24) & 0xFF) +1;
          var pm = (rtcremote>>16) & 0xFF;
          var rh = ((rtcremote>>8) & 0xFF) + 1;
          var rm = (rtcremote) & 0xFF;

          shdn_dev.innerHTML =  ph+ ':' + pm; 
          wake_dev.innerHTML =  rh+ ':' + rm; 
        }
        if(text[0] == 'M')
        {
          var macadd = text.substr(1,20);
          idDisplay.textContent = macadd;
        }

      }

   function linearRegression(x, y)
{	
    var xs = 0;  // sum(x)
    var ys = 0;  // sum(y)
    var xxs = 0; // sum(x*x)
    var xys = 0; // sum(x*y)
    var yys = 0; // sum(y*y)

    var n = 0;
    var nsous = 0;
    for (; n < x.length && n < y.length; n++)
    {
    	if((x[n] == "?" || y[n] == "?"))
    	{
    		//console.log("not full")
    		nsous++;
    	}
    	else if((x[n] == "0" || y[n] == "0"))
    	{
    		nsous++;
    	}
    	else
    	{
    	console.log("n="+n)
    	console.log(" x[n]="+ x[n])
    	console.log(" xs="+xs)
    	console.log(" xxs="+xxs)
    	var xn = parseInt(x[n], 10);
    	var yn = parseInt(y[n], 10);
        xs += xn;
        ys += yn;
        xxs += xn * xn;
        xys += xn * yn;
        yys += yn * yn;
    	}
    }

    n -= nsous;
    var div = n * xxs - xs * xs;
    var gain = (n * xys - xs * ys) / div;
    var offset = (ys * xxs - xs * xys) / div;
    var correlation = Math.abs((xys * n - xs * ys) / Math.sqrt((xxs * n - xs * xs) * (yys * n - ys * ys)));

    return { gain: gain, offset: offset, correlation: correlation, xs: xs, ys: ys, xxs: xxs, xys: xys, yys: yys};
}
      function updateBattery()
      {
        var url = "http://www.nestbox.local/battery";
        fetch(url).then(function(response) {
          response.text().then(function(text) {
            parseServerResponse(text)
          });
        });  
        setTimeout(updateBattery, 30000);
      }
      updateBattery();

      function fetchWeight()
      {
        var url = "http://www.nestbox.local/weight";
        fetch(url).then(function(response) {
          response.text().then(function(text) {
                        console.log("weight resp: "+text)   
            parseServerResponse(text)
          });
        });  
      }

      function fetchMac()
      {
        var url = "http://www.nestbox.local/mac";
        fetch(url).then(function(response) {
          response.text().then(function(text) {
            parseServerResponse(text)
          });
        });  
      }
      
      function fetchOffset()
      {
        var url = "http://www.nestbox.local/offset";
        fetch(url).then(function(response) {
          response.text().then(function(text) {
            console.log("offset resp: "+text)
            parseServerResponse(text)
          });
        });  
      }

      function calculateWeight()
      {
        var a = a_field.value;
        var b = b_field.value;
        console.log("a="+a)
        console.log("b="+b)

        var weight_est = (parseInt(adcVal.textContent) - b)/a;
        weightEstimate.textContent = weight_est;

      }

      function ConnectionTest()
      {
        // var url = "http://www.nestbox.local/";
        // fetch(url).then(function(response) {
        //   response.text().then(function(text) {
        //     if(text=="Hello world")
        //     {
        //       alert("Connected to Nestbox Control Center");
        //     }
        //     else
        //     {
        //       alert("Connection failed")
        //     }
        //   }, function(resp) {alert("Connection failed")});
        // });  
        var url = "http://www.nestbox.local/heartbeat";
        fetch(url).then(function(response) {
          response.text().then(function(text) {
            
          });
        });  
       
        setTimeout(ConnectionTest, 10010);
      }
      //ConnectionTest();
      

      btnFetch.onclick = function() {
      console.log("fetch time")    
        var url = "http://www.nestbox.local/time";
        fetch(url).then(function(response) {
          response.text().then(function(text) {
            parseServerResponse(text);
          });
        });  
      };

      btnSet.onclick = function() {
        console.log("Set time");
        var ts = Math.round((new Date()).getTime() / 1000);
        console.log("epoch = "+ts);

        var url = "http://www.nestbox.local/time?set="+ts;
        fetch(url).then(function(response) {
          response.text().then(function(text) {
            parseServerResponse(text);
          });
        });  
      };

      btnWeight.onclick = function() {
        console.log("Weight update");
        fetchWeight();  
        calculateWeight();
      };

      btnOffset.onclick = function() {
        console.log("Offset update");
        fetchOffset();  
      };

      btnStartCalib.onclick = function() {
      var url = "http://www.nestbox.local/LoadCellOn";
        fetch(url).then(function(response) {
          response.text().then(function(text) {
            parseServerResponse(text);
          });
        });  
      };

      btnStopCalib.onclick = function() {
      var url = "http://www.nestbox.local/LoadCellOff";
        fetch(url).then(function(response) {
          response.text().then(function(text) {
            parseServerResponse(text);
          });
        });  
      };

      btnget1.onclick = function() {
      	console.log(adcSensorvalue1.value);
      	adcSensorvalue1.value = adcVal.textContent
      	testnbresensorvalue++;
      	console.log(testnbresensorvalue);

      };
      btnget2.onclick = function() {
      	adcSensorvalue2.value= adcVal.textContent
      };
      btnget3.onclick = function() {
      	adcSensorvalue3.value= adcVal.textContent
      };
      btnget4.onclick = function() {
      	adcSensorvalue4.value= adcVal.textContent
      };
      btnget5.onclick = function() {
      	adcSensorvalue5.value= adcVal.textContent
      };




      BtngetADCscalingFinalvalue.onclick = function(){

      	testnbresensorvalue = 5;
      	if(adcSensorvalue1.value == "?"){

      		testnbresensorvalue--;
      	}
      	if(adcSensorvalue2.value == "?"){
      	
      		testnbresensorvalue--;
      	}
      	if(adcSensorvalue3.value == "?"){
   
      		testnbresensorvalue--;
      	}
      	if(adcSensorvalue4.value == "?"){
 
      		testnbresensorvalue--;
      	}
      	if(adcSensorvalue5.value == "?"){
      
      		testnbresensorvalue--;
      	}


      	if(testnbresensorvalue > 1){

      		var array_y = [adcSensorvalue1.value, adcSensorvalue2.value, adcSensorvalue3.value, adcSensorvalue4.value, adcSensorvalue5.value]
      	var array_x = [manualweight1.value, manualweight2.value, manualweight3.value, 
      	manualweight4.value, manualweight5.value]
      	console.log(array_x)
      	console.log(array_y)

      	var linreg = linearRegression(array_x, array_y)
      	console.log(linreg)
      	console.log(linreg.xs)
      	console.log(linreg.ys)
      	console.log(linreg.xxs)
      	console.log(linreg.xys)
      	console.log(linreg.yys)



      	a_field.value = linreg.gain
      	ADCslope.value = linreg.gain
      	ADCintercept.value = linreg.offset
      	ADCr2.value = linreg.correlation

        b_field.value = linreg.offset
      	}
      	else{
      		//console.log("false");
      		//alert("Please complete all \"ADC sensor value\" fields")
      		alert("Please complete at least 2 \"ADC sensor value\" fields")
      	}


      	



		//console.log("Nombre de champs remplis = " + testnbresensorvalue);
      };

      window.onload = function () {
 
var chart = new CanvasJS.Chart("chartContainer", {
	animationEnabled: true,
	theme: "light2",
	title:{
		text: "Simple Line Chart"
	},
	axisY:{
		includeZero: false
	},
	data: [{        
		type: "line",       
		dataPoints: [
			{ y: 450 },
			{ y: 414},
			{ y: 520, indexLabel: "highest",markerColor: "red", markerType: "triangle" },
			{ y: 460 },
			{ y: 450 },
			{ y: 500 },
			{ y: 480 },
			{ y: 480 },
			{ y: 410 , indexLabel: "lowest",markerColor: "DarkSlateGrey", markerType: "cross" },
			{ y: 500 },
			{ y: 480 },
			{ y: 510 }
		]
	}]
});
chart.render();
 
}     

      
  
      // var imgTestInternet = "Hello World";
      // var urltest = "http://www.nestbox.local/";
      
      // fetch(urltest).then(alert("Connected to Nestbox Control Center"),alert("Connection failed"));
        
    </script>
  </body>
</html>