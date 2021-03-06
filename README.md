# pocmap
A proof of concept of self hosted map to embed on your websit, using Openstreetmap data and tools.  
Goal was to :
1) have a mapserver serving tiles (TileServer GL) running locally
2) have a geolocation service (Nominatim) running locally
3) have a simple html page displaying map, with js frontend framework for user interacting (Leaflet and needed plugins : https://leafletjs.com)

## pre-requisite

Have docker installed : https://www.docker.com
Clone this repo

## 1- Use tileserver-gl with Docker

View readme here : https://github.com/klokantech/tileserver-gl 

Download your desired mbtiles file, place it this root folder, run their docker image : 

```bash
docker run --rm -it -v $(pwd):/data -p 9080:80 klokantech/tileserver-gl
```

http://localhost:9080 should show the tool with your map. (use 9080, not 8080)

## 2- Use Nominatim, clone it, then Docker build it

View readme here : https://github.com/mediagis/nominatim-docker 

Clone their repository in this root folder, modify their docker file to reflect the geolocation data you want. Build their docker file as explained :

```bash
docker run --restart=always -d -p 8080:8080 --name nominatim mediagis/nominatim:latest
```

http://localhost:8080 should show the nominatim application service, this allow you to query addresses to get corresponding coordinates. (use 9080, not 8080)

## 3- Open the map in browser

Open the file index.html of this repo in your browser. You may modify the hardcoded address variable in the javascript to test the markup and zoom feature.
You could disconnected completely the computer running the 2 docker services and still navigate in this map : no external dependency! Bye bye Googlemap!



