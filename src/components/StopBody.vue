<template>
    <div class="stop-body round">
        <div class="stop-body-header round">
            <h2 class="poppins-font" >Stop general information</h2>
        </div>
        <div class="stop-info" v-for="stop in stopData.stops" :key="stop.stop_id" >
            <div v-if="stop.stop_id == 2">
                <p><img src="" alt=""></p>
                <p>Telephone:{{stop.telephone}} </p>
                <p>House number:{{stop.address.house_number}} </p>
                <p>Street: {{stop.address.street}}</p>
                <p>Town: {{stop.address.town}}</p>
                <p>Postal Code: {{stop.address.postal_code}}</p>
                <p>Country: {{stop.address.country}}</p>

                <div class="stop-body-header round">
            <h2 class="poppins-font" >ORDERS</h2>
        </div>
            
            <OrderCard :stop="stop" />
            </div>
            
        </div>
    </div>
</template>

<script>
import OrderCard from './OrderCard.vue'
export default{
    name: 'StopBody',
    props:{
        stopData: Object,
    },
    components:{
        OrderCard,
    },
    
    methods:{
        //getStatusImg(id){
        //    var images = require.context('../assets/img/', false, /\.png$/)
        //    return images('./' + pet + ".png")
        //}
    }
};
</script>

<style scoped>
.stop-body{
    background: #fff;
}



.stop-body-header{
    background: #F4FCFB;
   
    padding: 20px 0px 20px 0px;
}

.stop-body-header h2{
    margin: 10px;
    color: black;
}
</style>