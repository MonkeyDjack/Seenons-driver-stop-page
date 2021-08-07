<template>
    <transition name="fade">
    <Popup v-if="isPopup" :togglePopup="togglePopup"> 
        <p><select name="pets" id="pet-select">
                <option value="0">other</option>
                <option value="1">wrong quantity ordered</option>
                <option value="2">wrong container type</option>
                <option value="3">container not accessible</option>
            </select></p>
            <p><textarea name="issue" cols="30" rows="10"></textarea></p>
            <p><button @click="togglePopup">Send</button></p>
    </Popup>
    </transition>
    <div class="stop-body round">
        <div class="stop-body-header round">
            <h2 class="poppins-font" >Stop general information</h2>
        </div>

        <div class="stop-flex">
            <transition name="fade">
            <Map @chooseStop="chooseStop" :stopData="stopData" />
            </transition>
            <transition-group name="fade">
            <div class="stop-info round-border" v-for="stop in filteredStops" :key="stop.stop_id" >
                <h3>{{stop.name}}</h3>
                <span class="stop-underline"></span>
                <p>Comment: {{filteredValue(stop.comment)}}</p>
                <p>Telephone: <a :href='stop.telephone'>{{filteredValue(stop.telephone)}}</a> </p>
                <p>House number: {{filteredValue(stop.address.house_number)}} </p>
                <p>Street: {{filteredValue(stop.address.street)}}</p>
                <p>Town: {{filteredValue(stop.address.town)}}</p>
                <p>Postal Code: {{filteredValue(stop.address.postal_code)}}</p>
                <p>Country: {{filteredValue(stop.address.country)}}</p>
                  
                
            </div>
            </transition-group>
        </div>
         <div class="stop-body-header round">
             <h2 class="poppins-font" >ORDERS</h2>
        </div>
    </div>
    
        <div class="stop-flex"  v-for="stop in filteredStops" :key="stop.stop_id">
           <OrderCard @togglePopup="togglePopup"  :stop="stop" />
           
         </div>
</template>

<script>
import OrderCard from './OrderCard.vue'
import Map from './Map.vue'
import Popup from './Popup.vue'
export default{
    name: 'StopBody',
    props:{
        stopData: Object,
    },

    data(){
        return{
            chosenStop: null,
            isPopup: false,
        };
    },
    computed:{
        filteredStops(){
            let filterStop = this.stopData.stops
            filterStop = filterStop.filter( stop => stop.stop_id === this.chosenStop)
            return filterStop
        },
        
    },

    components:{
        OrderCard,
        Map,
        Popup,
    },
    methods:{
        chooseStop(id){
            this.chosenStop = id
        },
        filteredValue(value){
            if(value == null){
                return ' -'
            }
            else{
                return value
            }
        },
        togglePopup(){
           this.isPopup = !this.isPopup
        }

    },
};
</script>

<style scoped>

.round-border{
    border-radius: 40px;
}
.stop-underline{
    height: 1px;
    width: 100%;
    margin: 10px 0;
    display: block;
    background: #fff;
}
.stop-flex{
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    padding: 30px 10px;
}
.stop-body{
    background: white;
}
.stop-info{
    padding: 20px;
    width: 25%;
    text-align: left;
    padding-left: 20px;
    background: rgb(50,126,134);
    background: linear-gradient(90deg, rgba(50,126,134,1) 0%, rgba(76,193,149,1) 100%);
    color: white;
    height: 100%;
    font-size: 12;
    box-shadow: 10px 10px 30px 0px rgba(0,0,0,0.75);
    -webkit-box-shadow: 10px 10px 30px 0px rgba(0,0,0,0.75);
    -moz-box-shadow: 10px 10px 30px 0px rgba(0,0,0,0.75);
}

.stop-info h3{
    margin: 0;
}

.fade-enter-from{
    opacity: 0;
}

.fade-enter-active{
    transition: all 0.5s ease-in;
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