---
title: Leaflet简介
date: 2016-04-08 17:30:23
tags: 
- leaflet
- osm
categories: 前端杂货
---

## 简介
[Leaflet](http://leafletjs.com)是一个领先的轻量级开源JS交互式地图库，大约只有33KB大小的JS，拥有大多数开发者所需要的所有地图特性。
Leaflet的设计基于简洁、性能和可用性，它能有效的应用于主流的桌面系统和移动平台，而且有大量的插件可扩展，同时还有一个易于使用的文档化的api[文档](http://leafletjs.com/reference.html)。
Leaflet无法单独提供地图服务，所以需要加载相应的地图瓦片。它可以加载各种地图瓦片，其中就包括OpenStreetMap。
OpenStreetMap(OSM) 是开放数据，由OpenStreetMap基金会（OSMF）采用开放数据共享开放数据库许可协议（ODbL）授权。只要您表明来源为 OpenStreetMap 及其贡献者，您就可以自由地复制、分发、传送和改编OSM的数据，所以在使用OSM瓦片的时候，需要注明[OSM著作权](http://www.openstreetmap.org/copyright)
	```{bash}
	L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
		attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
	}).addTo(map);
	```
## 接口介绍

具体可参考api文档。
 
## 插件介绍

具体可参考[插件介绍](http://leafletjs.com/plugins.html)
 
### Leaflet Control Geocoder 

同时支持地址编码和逆地址解析的插件，内置支持Nominatim, Bing, MapQuest, Mapbox, What3Words, Google and Photon等服务而且可以简单的扩展其他供应商的服务，其中Nominatim是免费的服务，也是这个插件默认使用的服务，这个逆地址解析服务的返回数据会根据客户浏览器的语言而返回相应语言的地址信息，同时可以通过设置返回数据语言来固定一种语言，代码如下
	```{bash}
	var map = L.map('map').setView([0, 0], 2),
	geocoder = L.Control.Geocoder.nominatim({
		reverseQueryParams: {
			"accept-language": "en-US",
			"zoom": 18
		}
	}),
	control = L.Control.geocoder({
		geocoder: geocoder
	}).addTo(map);
	```
### Leaflet.label 

Leaflet自身api不支持label，可以使用该插件代替，这个插件源码简单易读，如果有需要可以自己扩展。
