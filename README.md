# Puntos
## Hasta ahora, hemos incluido únicamente datos de otras fuentes, pero no así nuestra propia información.
 ### En este tutorial aprenderemos a cargar puntos a nuestros mapas únicamente utilizando coordenadas, esto puede ser muy útil para localizar paradas, o algún sitio de interés.
 
Para esto, lo único que hay que hacer es declarar una nueva variable a la que denominaremos “marcador1” es importante que la nombremos de una manera que podamos recordar y reconocer rápidamente, pues esto nos facilitará tareas posteriores.

Utilizaremos el comando de leaflet “L.marker” para declarar en el código que agregaremos un nuevo punto, o marcador, entre paréntesis y entre corchetes agregamos las coordenadas del punto, iniciando con la latitud, y luego la longitud, esto es de manera invertida a la forma usual de escribir las coordenadas. Finalmente utilizamos la instrucción addTo, para agregar la nueva información al mapa.

``` html
<script>	
var marcador1 = L.marker([20.83748 , -99.71396].addTo(map);
</script>
```

### Sin embargo, aunque ya podemos visualizar una nueva característica, esta no es de gran ayuda del todo, pues no muestra información que nos ayude a identificarlo, o a saber porque es importante este punto.

Existen diferentes atributos que se pueden editar y mejorar de los marcadores, veremos algunos ejemplos. 

Para iniciar, algo sencillo que podemos implementar rápidamente para solucionar la falta de información es lo siguiente:

``` html
<script>	
  var marcador1 = L.marker([20.83748 , -99.71396], {title:"Parada 1",alt:"",draggable:true}) .addTo(map);
</script>
```
Te habrás dado cuenta de que, al declarar la variable, usamos la palabra “marker” esto es porqué está clase tiene más opciones de eventos y existen métodos para realizar acciones con ellos, que sean más interactivas y útiles. Posteriormente, tocaremos el tema, en particular, utilizando popups. 

### Por lo pronto nuestro código debería parecerse a lo siguiente
``` html
<html>
<head>
	<meta charset="utf-8">
	<title>Mapa E14C17_2</title>
	<link rel="stylesheet" href="https://unpkg.com/leaflet@1.6.0/dist/leaflet.css"
  integrity="sha512-xwE/Az9zrjBIphAcBb3F6JVqxf46+CDLwfLMHloNu6KEQCAWi6HcDUbeOfBIptF7tcCzusKFjFw2yuvEpDL9wQ=="
  crossorigin=""/>
	<script src="https://unpkg.com/leaflet@1.6.0/dist/leaflet.js"
  integrity="sha512-gZwIG9x3wUXg2hdXF6+rVkLF/0Vi9U8D2Ntg4Ga5I5BZpVkVxlJWbSQtXPSiUTtC0TjtGOmxa1AJPuV0CPthew=="
  crossorigin=""></script>
	<style>
	#mapDIV {
	height: 100%;
	width: 100%;
	border: solid 2px black;
	}
	</style>
</head>
<body>
<div id="mapDIV"></div>

 <script>	
 var map = L.map('mapDIV', {
		center:[20.83748 , -99.71396],
		zoom:12
	});
	
	var scale = L.control.scale({
		'imperial':false
	});
	scale.addTo(map);
	
	var osm = L.tileLayer('http://a.tile.openstreetmap.org/{z}/{x}/{y}.png',
	{attribution: 'Map Data &copy; OpenStreetMap contributors'
	});
	osm.addTo(map);
	
	var topo = L.tileLayer('https://{s}.tile.opentopomap.org/{z}/{x}/{y}.png', {
	maxZoom: 17,
	attribution: 'Map data: &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, <a href="http://viewfinderpanoramas.org">SRTM</a> | Map style: &copy; <a href="https://opentopomap.org">OpenTopoMap</a> (<a href="https://creativecommons.org/licenses/by-sa/3.0/">CC-BY-SA</a>)'
	}); 
	topo.addTo(map);
	
	var sat = L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}', {
	attribution: 'Tiles &copy; Esri &mdash; Source: Esri, i-cubed, USDA, USGS, AEX, GeoEye, Getmapping, Aerogrid, IGN, IGP, UPR-EGP, and the GIS User Community'
	});

	
	var basemaps = {
		"OSM": osm,
		"Topografía": topo,										
		"Satélite": sat
		};
	L.control.layers(basemaps).addTo(map);
	
	
	var marcador1 = L.marker([20.83748 , -99.71396],{title:"Parada 1",alt:"",draggable:true}).addTo(map);
	
 </script>
</body>
</html>
```
### Al ejecutar en tu navegador deberías tener algo como esto.

![screenshot](https://raw.githubusercontent.com/sampach95/Puntos/master/img/punto.png )



Haz click en el siguiente enlace para volver a la pagina inicial
https://github.com/sampach95/ComoCrearMapasEnLaWebConLeaflet
