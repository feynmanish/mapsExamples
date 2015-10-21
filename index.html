<!DOCTYPE html>
<html>
<head>

<title>MCslp Maps Chapter 13, Ex 1</title>

 <script src="http://maps.google.com/maps/api/js?sensor=true"></script>
 <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.3/jquery.min.js"></script>
 <script type=text/javascript>
var map;              // the main map object
var mapOptions = new google.map.mapOptions(zoom: 4, center: {lat: -33, lng: 151});
var points = [];      // the list of active points in the current route
var route;            // the google.maps.Polyline of the current route
var routelistener;    // the listener object for updating the current route
var rrecording;       // the HTML reference for current recording mode
var routeidfield;     // the HTML reference of the ID in the form
var routetitle;       // the HTML reference of the title in the form
var routedescription; // the HTML reference of the description in the form
var message;          // the document reference of the message panel
var infopanel;        // the document reference of the info panel
var icontags = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';

function onLoad() {
	infopanel = document.getElementById("infopanel");
	message = document.getElementById("message");
	rrecording = document.getElementById("rrecording");
	routeidfield = document.getElementById("routeid");
	routetitle = document.getElementById("routetitle");
	routedescription = document.getElementById("routedesc");
	routeidfield.value = 0;
	routetitle.value = '';
	routedescription.value = '';
	map = new google.maps.Map(document.getElementById("map"), mapOptions);
}

function startRoute() {
    routelistener = google.maps.event.addDomListener(map, 'click', function(overlay,point) {
	if (route) {
	    map.removeOverlay(route);
	}
	points.push(point);
	if (points.length == 1) {
	    addmarker(point,'Start Point');
	}
	if (points.length > 1) {
	    route = new google.maps.Polyline(points);
	    map.addOverlay(route);
	}
    });
    rrecording.innerHTML = 'Enabled';
}

function clearLastPoint() {
    if (points.length > 0) {
	points.pop();
    }
    if (points.length == 0) {
	map.clearOverlays();
	return;
    }
    map.removeOverlay(route);
    route = new google.maps.Polyline(points);
    map.addOverlay(route);
}

function endRoute() {
    google.maps.event.removeListener(routelistener);
    rrecording.innerHTML = 'Disabled';
}

function clearRoute() {
    map.clearOverlays();
    points = [];
}

function newRoute() {
    points = [];
    routeidfield.value = 0;
    routetitle.value = '';
    routedescription.value = '';
    infopanel.innerHTML = '';
    message.innerHTML = 'Recording a new route';
    map.clearOverlays();
    startRoute();
}

function delRoute() {
    if (routeidfield.value != 0) {
	routeidtext = '&routeid=' + encodeURI(routeidfield.value);
	var request = window.XMLHttpRequest ? new XMLHttpRequest() : new ActiveXObject('Microsoft.XMLHTTP');
	request.open('GET','/examples/ch13-backend.cgi?m=delroute' + routeidtext,true);
	request.onreadystatechange = function() {
	    if (request.readyState == 4) {
		var xmlsource = request.responseXML;

		var msg = xmlsource.documentElement.getElementsByTagName("message");
		if (msg.length > 0) {
		    message.innerHTML = msg[0].getAttribute('text');
		}
		else
		{
		    message.innerHTML = 'Error sending request';
		}
	    }
	}
    }
    request.send(null);
    map.clearOverlays();
    routeidfield.value = 0;
    routetitle.value = '';
    routedescription.value = '';
    infopanel.innerHTML = '';
}

function saveRoute(oldnew) {
    pointstring = "";
    for(i=0;i<points.length;i++) {
	pointstring = pointstring + i + ':' + points[i].x + ':' + points[i].y + ',';
    }
    var request = window.XMLHttpRequest ? new XMLHttpRequest() : new ActiveXObject('Microsoft.XMLHTTP');
    var routeidtext = '';
    if ((routeidfield.value != 0) &&
	(oldnew == 1)) {
	routeidtext = '&routeid=' + encodeURI(routeidfield.value);
    }
    request.open('GET','/examples/ch13-backend.cgi?m=saveroute&title=' +
		 encodeURI(routetitle.value) + routeidtext +
		 '&desc=' + encodeURI(routedescription.value) +
		 '&points=' + encodeURI(pointstring), true);
    request.onreadystatechange = function() {
	if (request.readyState == 4) {
	    var xmlsource = request.responseXML;

	    var msg = xmlsource.documentElement.getElementsByTagName("message");
	    if (msg.length > 0) {
		if (msg[0].getAttribute('routeid') > 0) {
		    loadRoute(msg[0].getAttribute('routeid'),
			      msg[0].getAttribute('text'));
		}
	    }
	    else
	    {
		message.innerHTML = 'Error sending request';
	    }
	}
    }
    request.send(null);
}

function showRouteList() {
    map.clearOverlays();
    points = [];
    message.innerHTML = 'Select a route';
    infopanel.innerHTML = '';
    routetitle.value = '';
    routedescription.value = '';

    var baseIcon = new GIcon();
    baseIcon.shadow = "http://www.google.com/mapfiles/shadow50.png";
    baseIcon.iconSize = new GSize(20,34);
    baseIcon.shadowSize = new GSize(37,34);
    baseIcon.iconAnchor = new google.maps.Point(9,34);
    baseIcon.infoWindowAnchor = new google.maps.Point(9,2);
    baseIcon.infoShadowAnchor = new google.maps.Point(18,25);

    var request = GXmlHttp.create();
    request.open('GET','/examples/ch13-backend.cgi?m=listroutes', true);
    request.onreadystatechange = function() {
	if (request.readyState == 4) {
	    var xmlsource = request.responseXML;
	    var routelist = xmlsource.documentElement.getElementsByTagName("route");
	    for (var i=0;i < routelist.length;i++) {
		var iconloc =  'http://www.google.com/mapfiles/marker' + icontags.charAt(i) + '.png';

		infopanel.innerHTML = infopanel.innerHTML +
		    '<img src="' + iconloc + '" border="0">' +
		    '<a href="#" onClick="loadRoute(' +
		    routelist[i].getAttribute("routeid") +
		    ');">' + routelist[i].getAttribute("title") +
		    '</a><br/>';
		var point = new google.maps.Point(parseFloat(routelist[i].getAttribute("lat")),
				       parseFloat(routelist[i].getAttribute("lng")));
		points.push(point);

		var thisIcon = new GIcon(baseIcon);
		thisIcon.image = iconloc

		addmarker(point,
			  '<a href="#" onClick="loadRoute(' +
			  routelist[i].getAttribute("routeid") +
			  ');">' + routelist[i].getAttribute("title") +
			  '</a>',
			  thisIcon);
	    }
	    recenterandzoom(points);
	}
    }
    request.send(null);
}

function loadRoute(routeid,msgtext) {
    map.clearOverlays();
    points = [];
    routes = [];
    message.innerHTML = 'Loading route';
    infopanel.innerHTML = '';
    var request = GXmlHttp.create();
    request.open('GET','/examples/ch13-backend.cgi?m=getroute&routeid=' + routeid, true);
    request.onreadystatechange = function() {
	if (request.readyState == 4) {
	    var xmlsource = request.responseXML;

	    var msg = xmlsource.documentElement.getElementsByTagName("message");
	    if (msg.length > 0) {
		message.innerHTML = msg[0].getAttribute('text');
		return;
	    }

	    if (msgtext) {
		message.innerHTML = msgtext;
	    }
	    else {
		message.innerHTML = 'Route Loaded';
	    }

	    var routeinfo = xmlsource.documentElement.getElementsByTagName("routeinfo");

	    routeidfield.value = routeinfo[0].getAttribute('routeid');
	    routetitle.value = routeinfo[0].getAttribute('title');
	    routedescription.value = routeinfo[0].getAttribute('description');

	    var distanceinfo = xmlsource.documentElement.getElementsByTagName("distance");

	    infopanel.innerHTML = 'Distance: ' + distanceinfo[0].getAttribute('km') + ' km, ' +
	    distanceinfo[0].getAttribute('miles') + ' miles';

	    var routepoints = xmlsource.documentElement.getElementsByTagName("point");
	    for (var i=0;i < routepoints.length;i++) {
		var point = new google.maps.Point(parseFloat(routepoints[i].getAttribute("lat")),
				       parseFloat(routepoints[i].getAttribute("lng")));

		points.push(point);
	    }
	    route = new google.maps.Polyline(points);
	    map.addOverlay(route);
	    addmarker(points[0],'Start here');
	    addmarker(points[points.length-1],'Finish here');
	    recenterandzoom(points);
	}
    }
    request.send(null);
}

function addmarker(point,message,icon)
{
    var marker = new google.maps.Marker(point,icon);
      google.maps.event.addDomListener(marker,
			 'click',
			 function() {
	  marker.openInfoWindowHtml('<b>' + message + '</b>');
      }
			 );
      map.addOverlay(marker);
}

function recenterandzoom(points) {
    var latpoints = [];
    var lngoogle.maps.Points = [];

    for(var i=0;i<points.length;i++) {
	latpoints.push(points[i].y);
	lngoogle.maps.Points.push(points[i].x);
    }

    latpoints.sort(function(x,y) { return x-y; });
    lngoogle.maps.Points.sort(function(x,y) { return x-y; });
    var new google.maps.Lat = latpoints[0] + ((latpoints[latpoints.length-1] - latpoints[0])/2);
    var newlng = lngoogle.maps.Points[0] + ((lngoogle.maps.Points[lngoogle.maps.Points.length-1] - lngoogle.maps.Points[0])/2);

    var newpoint = new google.maps.Point(parseFloat(newlng),parseFloat(newlat));

    var idealspan = new GSize(parseFloat(Math.abs(lngoogle.maps.Points[lngoogle.maps.Points.length-1]-lngoogle.maps.Points[0])),
			      parseFloat(Math.abs(latpoints[latpoints.length-1]-latpoints[0])));

    map.zoomTo(1);
    var idealzoom = 1;

    for(var i=1;i<16;i++) {
	var currentsize = map.getSpanLatLng();
		if ((currentsize.width < idealspan.width) ||
	    (currentsize.height < idealspan.height)) {
	    map.zoomTo(i);
	    idealzoom = i;
	}
	else {
	    break;
	}
    }

    map.centerAndZoom(newpoint,idealzoom);
}

  //]]>
  </script>
  </head>
  <body onload="onLoad()">

  <div id="map" style="width: 800px; height: 350px"></div>
<table width="100%" cellspacing="5" cellpading="0" border="0">
<tr valign="top">
<td width="33%"><h3>Controls</h3>
<a href="#" onClick="newRoute()">New route</a><br/>
<a href="#" onClick="startRoute()">Enable route recording</a><br/>
<a href="#" onClick="endRoute()">Disable route recording</a><br/>
<a href="#" onClick="clearLastPoint()">Clear last point</a><br/>
<a href="#" onClick="clearRoute()">Clear current route</a><br/>
<a href="#" onClick="showRouteList()">List saved routes</a><br/>
<a href="#" onClick="delRoute()">Delete current route</a>
<h3>Messages</h3><div id="message">None</div>
<h3>Route Recording</h3><div id="rrecording">Disabled</div>
</td>
<td width="33%"><h3>Information</h3>
<div id="infopanel"></div></td>
<td width="33%"><h3>Route information</h3>
<input type="hidden" id="routeid" value="0" size="10">
<b>Name</b><br/> <input type=text id="routetitle" size="40"/><br/>
<b>Description</b><br/> <textarea id="routedesc" rows=10 cols=40></textarea><br/>
<a href="#" onClick="saveRoute(1)">Save route</a>&nbsp;|&nbsp;<a href="#" onClick="saveRoute(0)">Save as new route</a></td>
</tr>
</table>
</body>
</html>
