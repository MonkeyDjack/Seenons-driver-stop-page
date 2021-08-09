<template>
    <div id="mapid" class="
map-flex-width" ref="map"></div>
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
                

                //var garageMark = leaflet.marker([props.stopData.garage.address.lat, props.stopData.garage.address.lon])
                //garageMark.addTo(mymap).on('click', garageClicked)

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
    margin: 44px, 0; 
    border-radius: 40px; 
    z-index: 5;
    box-shadow: 10px 10px 30px 0px rgba(0,0,0,0.75);
    -webkit-box-shadow: 10px 10px 30px 0px rgba(0,0,0,0.75);
    -moz-box-shadow: 10px 10px 30px 0px rgba(0,0,0,0.75); }


</style>