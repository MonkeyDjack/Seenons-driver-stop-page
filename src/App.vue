<template>
  <Header :stopData="stopData" :chosenStop="chosenStop"/>
  <StopBody :stopData="stopData"/>
</template>

<script>
import Header from './components/Header.vue'
import StopBody from './components/StopBody.vue'
import stopData from "./json/driver_route_sample.json"
export default {
  name: 'App',
  components: {
    Header,
    StopBody,
  },
  data(){
    return{
        stopData: stopData,
    };
},



}
</script>

<style>
body{
  margin: 0;
}
.poppins-font{
  font-family: 'Poppins', 'arial';

}
.round{
    border-top-right-radius: 20px;
    border-top-left-radius: 20px;
}

.round-full{
  border-radius: 20px;
}
.shadow-box{
  box-shadow: 1px 2px 84px -18px rgba(0,0,0,0.75);
  -webkit-box-shadow: 1px 2px 84px -18px rgba(0,0,0,0.75);
  -moz-box-shadow: 1px 2px 84px -18px rgba(0,0,0,0.75);   
}
#app {
  font-family: 'Poppins', 'arial';;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: rgb(50,126,134);
  background: linear-gradient(90deg, rgba(50,126,134,1) 0%, rgba(76,193,149,1) 100%);
}
.container {
  min-width: 320px;
  max-width: 800px;
  margin: 0 auto;
}

.green-btn{
  background: #2CA6A4;
}

.red-btn{
  background: #A63446;
}

.map-flex-width{
  width: 65%;
}

.fade-enter-from{
    opacity: 0;
}

.fade-enter-active{
    transition: all 0.5s ease-in;
}

 .btn{
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

 .hide{
   opacity: 0;
   z-index: -1;
   transition: 2s ease-in;
 }
</style>
