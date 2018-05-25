# pocmap
A proof of concept of self hosted map to embed on your website  goal was to :
1) have a mapserver serving tiles (TileServer GL)
2) have a geolocation service (Nomnatim)
3) have asimple html page displaying map, with js frontend framewokr for user interacting (Leaflet and needed plugins)

## pre-requisite

Have docker installed.
Clone this repo.

## 1- Use tileserver-gl with Docker

View readme here : https://github.com/klokantech/tileserver-gl 

Download yur desired mbtiles file, place it this root folder, run their docker image : 

```bash
docker run --rm -it -v $(pwd):/data -p 9080:80 klokantech/tileserver-gl
```

localhost:9080 should show the tool with your map. (use 9080, not 8080)

## 2- Use Nominatim, clone it then Docker build it

View readme here : https://github.com/mediagis/nominatim-docker 

Clone their reposotiry in this root folder, modify their docker filebuild their docker file as explained :

```bash
docker run --restart=always -d -p 8080:8080 --name nominatim mediagis/nominatim:latest
```

localhost:8080 should show the nominatim application the tool with your map. (use 9080, not 8080)

## 3- Open the map in browser

Open the file index.html of this repo in your browser. You may modify the hardcoded address variable in the javascript to test the markup and zoom feature.
You could disconncted completly the computer running the 2 docker services and still navigate in this app : no external dependency! Bye bye Googlemap!



