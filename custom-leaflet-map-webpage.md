---
title: "Custom Leaflet Map Webpage - Developing Data Products - Assignment 1"
author: "Sebastian Gomez Gomez"
date: "6/7/2021"
output: 
        html_document:
                keep_md: yes
---



## Summary

This web page describes the leaflet map generated from the Carpooling Slugging Locations dataset, a list of 40 slugging locations (pick-up and drop-off points) for casual carpooling in the District of Columbia. The data was originally obtained from http://sluglines.com/.



## Data loading and preprocessing

The dataset was downloaded from the following URL:

https://query.data.world/s/icapdknm7ox4x72odwzecrjqre3plz

Below is the code to load a process data:


```r
carpooling = read.dbf('Carpooling_Slugging_Locations.dbf', as.is = FALSE)
carpooling = mutate(carpooling, pop = paste("<a href = '", carpooling$SOURCE, "'>", 
                                            carpooling$STOPDESCRI, "</a>"))
carpoolingstop = carpooling[, c('LATITUDE', 'LONGITUDE')]
names(carpoolingstop) = c('lat', 'lng')
carpoolingpop = carpooling$pop
```

## Leaflet Map

The plot below maps all 40 slugginc pick-up and drop-off carpooling locations with dynamic clustering capabilities using the markerClusterOptions parameter as well as a popup with each stop description and web source for future reference:


```r
carpoolingstop %>% leaflet() %>% addTiles() %>% 
        addMarkers(popup = carpoolingpop, clusterOptions = markerClusterOptions())
```

```{=html}
<div id="htmlwidget-42500ebb094b06fb31d5" style="width:100%;height:800px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-42500ebb094b06fb31d5">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["//{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":1,"detectRetina":false,"attribution":"&copy; <a href=\"http://openstreetmap.org\">OpenStreetMap<\/a> contributors, <a href=\"http://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA<\/a>"}]},{"method":"addMarkers","args":[[38.46711,38.607151,38.88503,38.896687,38.900711,38.85238,38.876611,38.877402,38.898094,38.899151,38.868263,38.89462,38.889938,38.62624,38.779487,38.778141,38.576817,38.421204,38.755989,38.475561,38.346172,38.289688,38.951038,38.25132,38.640717,38.675777,38.715012,38.658592,38.89687,38.86214,38.674301,38.646938,38.670113,38.775859,38.835972,38.88733,38.7459,38.831035,38.766778,38.658051],[-77.416153,-77.334976,-77.02446,-77.043549,-77.043549,-77.04964,-77.001444,-77.270605,-77.071716,-77.033066,-77.052223,-77.03207,-77.032021,-77.348183,-77.231524,-77.187467,-77.315826,-77.425514,-77.238098,-77.412999,-77.501804,-77.562561,-77.384453,-77.508324,-77.293884,-77.276543,-77.213593,-77.280746,-77.05139,-77.04862,-77.255623,-77.341232,-77.250771,-77.263037,-77.455147,-77.03216,-77.209253,-77.117748,-77.170118,-77.288749],null,null,null,{"interactive":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},["<a href = ' https://sluglines.com/a/mwiki/index.php?title=Mine_Road '> Rt 610 - Mine Rd <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Montclair_Northgate '> Montclair Northgate <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=L_Enfant_Plaza '> L Enfant Plaza <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=19th_%26_F_St '> 19th & F St <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=19th_%26_I_St '> 19th & I St <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Crystal_City_23rd_St '> Crystal City 23rd St <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Navy_Yard '> Navy Yard <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Vienna_Metro '> Vienna Metro <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Rosslyn '> Rosslyn <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=15th_Street_%26_New_York_Ave '> 15th St & New York Ave <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Pentagon '> Pentagon <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=14th_St_at_Commerce_Dept. '> 14th St at Commerce Dept. <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=14th_Street_and_Constitution_Ave '> 14th St & Constitution Ave <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Montclair_Fire_Station '> Montclair Fire Station <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Cardinal_Forest_Plaza '> Cardinal Forest Plaza <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Bobs_(Old_Keene_Mill_Rd) '> Bobs (Old Keene Mill Rd) <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Route_234 '> Rt 234 <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Route_630 '> Rt 630 <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Sydenstricker_Rd '> Sydenstricker Rd <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Route_610(Stafford) '> Rt 610 - Staffordboro Blvd <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Route_17 '> Rt 17 <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Route_3_-_Gordon_Rd '> Rt 3 - Gordon Rd <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Herndon/Reston_-_Monroe_Deck '> Herndon/Reston - Monroe Deck <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Route_208 '> Rt 208 <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Potomac_Mills '> Potomac Mills <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Tacketts_Mill '> Tacketts Mill <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Lorton '> Lorton <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Horner_Rd '> Horner Rd <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Foggy_Bottom_Metro '> Foggy Bottom Metro <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Crystal_City_12thSt '> Crystal City 12th St <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Old_Hechingers '> Old Hechingers <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Dale_City '> Dale City <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Route_123 '> Rt 123 <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Rolling_Valley '> Rolling Valley <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Centreville '> Centreville <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=14th_and_Independence '> 14th St  & Independence <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Saratoga '> Saratoga <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Mark_Center '> Mark Center <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Franconia-Springfield '> Franconia/Springfield Metro <\/a>","<a href = ' https://sluglines.com/a/mwiki/index.php?title=Telegraph_Rd '> Telegraph Rd <\/a>"],null,{"showCoverageOnHover":true,"zoomToBoundsOnClick":true,"spiderfyOnMaxZoom":true,"removeOutsideVisibleBounds":true,"spiderLegPolylineOptions":{"weight":1.5,"color":"#222","opacity":0.5},"freezeAtZoom":false},null,null,{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]}],"limits":{"lat":[38.25132,38.951038],"lng":[-77.562561,-77.001444]}},"evals":[],"jsHooks":[]}</script>
```
