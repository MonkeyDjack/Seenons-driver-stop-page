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
        setup(props) {
            let mymap
            onMounted(() =>{
                mymap = leaflet.map("mapid").setView([props.stopData.garage.address.lat, props.stopData.garage.address.lon], 13)
                leaflet.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=pk.eyJ1IjoibXVoaXRkaW4iLCJhIjoiY2tyeGNub2twMHBkbjJucHNmZndpN2k4NyJ9.YcpexF36dCDvDIORcLezXQ', {
                    attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
                    maxZoom: 18,
                    id: 'mapbox/streets-v11',
                    tileSize: 512,
                    zoomOffset: -1,
                    accessToken: 'pk.eyJ1IjoibXVoaXRkaW4iLCJhIjoiY2tyeGNub2twMHBkbjJucHNmZndpN2k4NyJ9.YcpexF36dCDvDIORcLezXQ'
                }).addTo(mymap);
            })
        }
        
    }
    
</script>

<style scoped>
#mapid { height: 200px; }
</style>