<template>
    <div class="order-card round" v-for="order in stop.orders" :key="order.order_id">
        <div  :class="[isRotated ? 'flip-card-inner-rotate' : '',  'flip-card-inner round clearfix']">
            <div class="flip-card-front">
                <img src="" alt="">
                <h3>{{order.stream_type}}</h3>
                <ul>
                    <li>quantity: {{order.quantity}}</li>
                    <li>size: {{order.size}} kg</li>
                    <li>status: {{order.status}}</li>
                    <li>type: {{order.type}}</li>
                </ul>
                <div class="btn-flex">
                    <button class="order-btn">Complete</button>
                    <button class="order-btn" @click="addClass()">Send Issue</button>
                </div>
            </div>
            <div class="flip-card-back">
                <h2>Choose Issue</h2>
                <select name="issue" id="issue-type">
                  <option value="0">other</option>
                  <option value="1">wrong quantity ordered</option>
                  <option value="2">wrong container type</option>
                  <option value="3">container not accessible</option>
                </select>
                <h2>Add Comment</h2>
                <textarea id="issue-type-comment" name="comment" rows="4" cols="50" />
                <button class="order-btn" @click="addClass()">Send Issue</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default{
        name: 'OrderCard',
        props:{
            stop: Object,
        },
        data(){
            return{
                isRotated: false,
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
            }
        }
    }
</script>

<style scoped>
 .order-card{
     position: relative;
    color: white;
    min-width: 320px;
    max-width: 500px;
    height: 350px;
    margin: 80px auto;
    perspective: 1000px;

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
    border-radius: 15px;
    padding-left: 1rem;
    padding-right: 1rem;
    padding-top: 0.75rem;
    padding-bottom: 0.75rem;
    box-shadow: 0px 2px 4px -1px rgb(0 0 0 / 20%), 0px 4px 5px 0px rgb(0 0 0 / 14%), 0px 1px 10px 0px rgb(0 0 0 / 12%);
    width: 40%;
 }


 .completed{
     text-align: center;
    opacity: 0;
    z-index: 2;
    width: 100%;
    height: 100%;
    background: rgb(50,126,134);
    background: linear-gradient(90deg, rgba(50,126,134,1) 0%, rgba(76,193,149,1) 100%);

 }

.flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    transition: transform 0.8s;
    transform-style: preserve-3d;
    background: rgb(50,126,134);
    background: linear-gradient(90deg, rgba(50,126,134,1) 0%, rgba(76,193,149,1) 100%);
}

.flip-card-inner-rotate {
  transform: rotateY(180deg);
}

.flip-card-back {
  color: white;
  transform: rotateY(180deg);
}


 .flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}
</style>