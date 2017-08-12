---
title: Venir au labyrinhe
permalink: acces.html
layout: page
---


<script type="text/javascript">
function init_gmap_gmap(id, addr, centerLatitude, centerLongitude, startZoom, description, kml, control, maptype, show_marker, addoverview, addscale, addgoogle) {
     if (addr!='') {
 		geocoder = new GClientGeocoder();
	    geocoder.getLatLng(addr, function(pt) {
	    	if (pt == null) {
         var mapdiv = document.getElementById("gmap_gmap"+id);
        mapdiv.innerHTML = '<p style="background:#ffff00">Google cannot find the address you specified: <b>'+addr+'</b><br />Please double check your address.</p><ul><li>Please make sure you enter the full address in double quotes.</li><li>For countries other than US, please do not forget to enter the country name.</li></ul><p>Click here for <a href="http://gmaps-samples.googlecode.com/svn/trunk/mapcoverage_filtered.html">full list of supported countries</a>.</p>';
    } else {
		display_gmap_gmap(id, pt.lat(), pt.lng(), startZoom, description, kml, control, maptype, show_marker, addoverview, addscale, addgoogle);
    }
	    });
	} else {
	     display_gmap_gmap(id, centerLatitude, centerLongitude, startZoom, description, kml, control, maptype, show_marker, addoverview, addscale, addgoogle);
	}
}

function display_gmap_gmap(id, centerLatitude, centerLongitude, startZoom, description, kml, control, maptype, show_marker, addoverview, addscale, addgoogle) {
    var mapdiv = document.getElementById("gmap_gmap"+id);
	if (GBrowserIsCompatible()) {
		var map = new GMap2(mapdiv);
		map.setCenter(new GLatLng(centerLatitude, centerLongitude), startZoom);
		if (kml!='') {
		    var gx = new GGeoXml(kml);
		    map.addOverlay(gx);
		} else {
			if (show_marker) {
				var marker = new GMarker(new GLatLng(centerLatitude, centerLongitude));
				if (description!='') {GEvent.addListener(marker, 'click', function() {marker.openInfoWindowHtml(description);});}
				map.addOverlay(marker);
			}
		}
		format_gmap(map, control, maptype, show_marker, addoverview, addscale, addgoogle);
	} else {
	    mapdiv.innerHTML = 'Sorry, your browser is not compatible with Google Maps.';
	}
}

</script>
