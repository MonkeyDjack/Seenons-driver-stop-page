<template>
    <div class="order-card round-full clearfix" v-for="order in stop.orders" :key="order.order_id">
        <div class="order-card-image round">
            <img :src="`../../img/orderImg_id${order.stream_product_id}.png`"  />
        </div>
        <h3>{{order.stream_type}}</h3>
        <ul>
            <li>quantity: <ChangeValue :change="order.quantity" /></li>
            <li>size: {{order.size}} kg</li>
            <li>status: {{displayStatus(order.status)}}</li>
            <li>type: {{displayType(order.type)}}</li>
        </ul>
        <div class="btn-flex">
            <button class="order-btn green-btn">Complete</button>
            <button class="order-btn red-btn" >Send Issue</button>
        </div>    
    </div>
</template>

<script>
import ChangeValue from './ChangeValue.vue'
    export default{
        name: 'OrderCard',
        props:{
            stop: Object,
        },
        components:{
            ChangeValue,
        },
        data(){
            return{
                isIssue: false,
                publicPath: process.env.BASE_URL,
            };
            
        },
        methods: {
            addClass: function() {
                if(this.isRotated == false){
                this.isRotated = true;
                }
                else if(this.isRotated == true){
                    this.isRotated = false
                }
            },
            displayStatus(statusId){
                if(statusId == 0){
                    return 'new';
                }
                else if(statusId == 1){
                    return 'pending'
                }
                else if(statusId == 2){
                    return 'scheduled'
                }
                else if(statusId == 3){
                    return 'in progress'
                }
                else if(statusId == 4){
                    return 'completed'
                }
            },
            displayType(typeId){
                if(typeId == 0){
                    return 'pick up';
                }
                else if(typeId == 1){
                    return 'drop off'
                }
            },
        }
    }
</script>

<style scoped>
 .order-card{
    position: relative;
    color: black;
    max-width: 40%;
    min-width: 300px;
    padding-bottom: 20px;
    background: #F4FCFB;
    margin:20px;
    box-shadow: 10px 10px 30px 0px rgba(0,0,0,0.75);
    -webkit-box-shadow: 10px 10px 30px 0px rgba(0,0,0,0.75);
    -moz-box-shadow: 10px 10px 30px 0px rgba(0,0,0,0.75);
    background: white;

 }

 .order-card ul{

     margin: 0;
     padding-left: 30px;
 }

 .order-card ul li{
     text-align: left;
     padding: 10px;
 }
.btn-flex{
    margin-top: 20px;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
}
 .order-btn{
    align-content: center;
    border: none;
    color: white;
    border-radius: 15px;
    padding-left: 1rem;
    padding-right: 1rem;
    padding-top: 0.75rem;
    padding-bottom: 0.75rem;
    box-shadow: 0px 2px 4px -1px rgb(0 0 0 / 20%), 0px 4px 5px 0px rgb(0 0 0 / 14%), 0px 1px 10px 0px rgb(0 0 0 / 12%);
    width: 40%;
 }

.card-issue{
    visibility: hidden;
}


.order-card-image{
    width: 100%;
    height: 200px;
    overflow: hidden;
}

</style>