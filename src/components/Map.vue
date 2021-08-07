<template>
    <div id="mapid" ref="map"></div>
</template>

<script>
import leaflet from "leaflet"
import { onMounted } from '@vue/runtime-core'
    export default{
        name: 'Map',
        props:{
            stopData: Object,
        },
        data(){
            return{
                
            };
        },
        methods:{
            
        },
        setup(props,context) {
            let mymap
            onMounted(() =>{
                mymap = leaflet.map("mapid").setView([52.36607, 4.8672816], 13)
                leaflet.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=pk.eyJ1IjoibXVoaXRkaW4iLCJhIjoiY2tyeGNub2twMHBkbjJucHNmZndpN2k4NyJ9.YcpexF36dCDvDIORcLezXQ', {
                    attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
                    maxZoom: 18,
                    id: 'mapbox/streets-v11',
                    tileSize: 512,
                    zoomOffset: -1,
                    accessToken: 'pk.eyJ1IjoibXVoaXRkaW4iLCJhIjoiY2tyeGNub2twMHBkbjJucHNmZndpN2k4NyJ9.YcpexF36dCDvDIORcLezXQ'
                }).addTo(mymap);
                
                var stopMarkerIcon = leaflet.icon({ //add this new icon
                    iconUrl: i+'.png',
                    shadowUrl: 'leaf-shadow.png',

                    iconSize:     [38, 95], // size of the icon
                    shadowSize:   [50, 64], // size of the shadow
                    iconAnchor:   [22, 94], // point of the icon which will correspond to marker's location
                    shadowAnchor: [4, 62],  // the same for the shadow
                    popupAnchor:  [-3, -76] // point from which the popup should open relative to the iconAnchor
                });
                console.log(stopMarkerIcon)

                var garageMark = leaflet.marker([props.stopData.garage.address.lat, props.stopData.garage.address.lon])
                garageMark.addTo(mymap).on('click', garageClicked)

                function garageClicked(){
                        console.log('garage')
                    }

                var i = 0;
                var stops = []
                props.stopData.stops.forEach(stop => {
                    
                    var stopMarker = leaflet.marker([stop.address.lat, stop.address.lon]);
                    
                    stops.push(stopMarker);
                    stops[i].on('click', stopClicked);
                    stops[i].addTo(mymap);
                    
                    i++;
                    function stopClicked(){
                        context.emit('chooseStop', stop.stop_id)
                        
                    }

                    
                })

                
                
                 
            })
        },
        
    

        
    }
    
</script>

<style scoped>
#mapid { 
    height: 400px;
    width: 65%;  
    margin: 44px, 0; 
    border-radius: 40px; 
    box-shadow: 10px 10px 30px 0px rgba(0,0,0,0.75);
    -webkit-box-shadow: 10px 10px 30px 0px rgba(0,0,0,0.75);
    -moz-box-shadow: 10px 10px 30px 0px rgba(0,0,0,0.75); }


</style>