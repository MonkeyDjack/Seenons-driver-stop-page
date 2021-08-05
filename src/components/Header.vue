<template>
    <div class="header">
        <div class="header-container">

            <img src="../assets/img/avatar-empty.png" alt="avatar" class="avatar">
        </div>
        <div v-for="stop in stopData.stops" :key="stop.stop_id">
            <h2 class="place_name poppins-font"  v-if="stop.stop_id == chosenStop">{{stop.name}}</h2>
        </div>
        
    </div>
</template>

<script>
export default{
    name: 'Header',
    props:{
        stopData: Object,
        chosenStop: Number,
    }
};
</script>

<style scoped>
.header-container{
    display: flex;
    justify-content: space-around;
}
.avatar{
    width: 120px;
    height: 100px;
}

.place_name{
    text-align: center;
    color: white;
}

.header{
    padding-top:40px;
    padding-bottom: 40px;
}

</style>