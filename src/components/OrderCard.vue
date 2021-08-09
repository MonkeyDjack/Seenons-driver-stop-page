<template>
    <div class="order-card round-full shadow-box"  v-for="order in stop.orders" :key="order.order_id">
        <div  class="complete round-full" :class="{hide : order.status !== 4}" :ref="'complete'+order.order_id">
            <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px"
                width="50%" height="50%"
                viewBox="0 0 172 172"
                style=" fill:#000000;"><g fill="none" fill-rule="nonzero" stroke="none" stroke-width="1" stroke-linecap="butt" stroke-linejoin="miter" stroke-miterlimit="10" stroke-dasharray="" stroke-dashoffset="0" font-family="none" font-weight="none" font-size="none" text-anchor="none" style="mix-blend-mode: normal"><path d="M0,172v-172h172v172z" fill="none"></path><g fill="#ffffff"><path d="M86,0c-6.34196,0 -11.49139,4.45011 -13.06125,10.32h-11.01875h-30.96c-5.6587,0 -10.32,4.6613 -10.32,10.32v134.16c0,5.6587 4.6613,10.32 10.32,10.32h110.08c5.6587,0 10.32,-4.6613 10.32,-10.32v-134.16c0,-5.6587 -4.6613,-10.32 -10.32,-10.32h-30.96h-11.01875c-1.56986,-5.86989 -6.71929,-10.32 -13.06125,-10.32zM86,6.88c3.84133,0 6.88,3.03867 6.88,6.88c0.00019,1.89978 1.54022,3.43981 3.44,3.44h10.32v6.88h-41.28v-6.88h10.32c1.89978,-0.00019 3.43981,-1.54022 3.44,-3.44c0,-3.84133 3.03867,-6.88 6.88,-6.88zM30.96,17.2h27.52v10.32c0.00019,1.89978 1.54022,3.43981 3.44,3.44h48.16c1.89978,-0.00019 3.43981,-1.54022 3.44,-3.44v-10.32h27.52c1.9437,0 3.44,1.4963 3.44,3.44v134.16c0,1.9437 -1.4963,3.44 -3.44,3.44h-110.08c-1.9437,0 -3.44,-1.4963 -3.44,-3.44v-134.16c0,-1.9437 1.4963,-3.44 3.44,-3.44zM116.94656,68.75969c-1.01377,0.01324 -1.97008,0.47296 -2.6136,1.25641l-35.60265,42.07953l-21.45297,-18.38922c-1.44345,-1.23565 -3.61529,-1.0672 -4.85094,0.37625c-1.23565,1.44345 -1.0672,3.61529 0.37625,4.85094l24.08,20.64c0.69559,0.59602 1.60015,0.89003 2.51324,0.81688c0.91309,-0.07315 1.75931,-0.50741 2.35114,-1.20657l37.84,-44.72c0.89423,-1.02297 1.10263,-2.47642 0.53187,-3.70944c-0.57076,-1.23302 -1.81376,-2.01463 -3.17234,-1.99478z"></path></g></g></svg>
        </div>
        <div class="order-card-image round">
            <img :src="`../../img/orderImg_id${order.stream_product_id}.png`"  />
        </div>
        <h3>{{order.stream_type}}</h3>
        <ul>
            <li>quantity: <input type="text" :ref="'quantity'+order.order_id" class="poppins-font change-input" :value="order.quantity">
            <button @click="toggleChange('quantity'+order.order_id)">change</button></li>
            <li>size: {{order.size}} kg</li>
            <li>status: {{displayStatus(order.status)}}</li>
            <li>type: {{displayType(order.type)}}</li>
        </ul>
        <div class="btn-flex">
            <button class="btn green-btn" @click="completeOrder('complete'+order.order_id)">Complete</button>
            <button class="btn red-btn"  v-on:click="$emit('togglePopup')" >Send Issue</button>
        </div>    
    </div>
</template>

<script>
    export default{
        name: 'OrderCard',
        props:{
            stop: Object,
            
        },
        components:{
        },
        data(){
            return{
                isIssue: false,
                isChangeValue: false,
            };
            
        },
        methods: {
            
            

            completeOrder(ref){
                
                this.$refs[ref].classList.remove('hide')
            
            },
            toggleChange(ref){
                
                this.$refs[ref].focus()
                
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
        },
    }
</script>

<style scoped>
 .order-card{
    position: relative;
    color: black;
    width: 40%;
    padding-bottom: 20px;
    background: #F4FCFB;
    margin:20px;
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

.issue-card{
    position: fixed;
    top: 50%;
    left: 50%;
    width: 50%;
    height: auto;
    background: linear-gradient(90deg, rgba(50,126,134,1) 0%, rgba(76,193,149,1) 100%);
}


.order-card-image{
    width: 100%;
    height: 200px;
    overflow: hidden;
}

.change-input{
    width: 20px;
    border:  none;
    height: auto;
}

.complete{
    
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 70%;
    display: flex;
    justify-content: space-around;
    align-items: center;
    background:  rgba(50,126,134,1);
    transition: 2s ease-in;
}
@media screen and (max-width:720px){
  .order-card{
      width: 90%;
  }
}

</style>