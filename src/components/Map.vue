<template>
    <div id="mapid"></div>
</template>

<script>
import leaflet from "leaflet"
import { onMounted } from '@vue/runtime-core'
    export default{
        name: Map,
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
                var i = 0;
                var markers = []
                props.stopData.stops.forEach(stop => {
                    
                    var marker = leaflet.marker([stop.address.lat, stop.address.lon]);
                    
                    markers.push(marker);
                    markers[i].on('click', markerClicked);
                    markers[i].addTo(mymap);
                    
                    i++;
                    function markerClicked(){
                        context.emit('chooseStop', stop.stop_id)
                        
                    }
                })

                
                
                 
            })
        },
        
    

        
    }
    
</script>

<style scoped>
#mapid { height: 400px; }
</style>