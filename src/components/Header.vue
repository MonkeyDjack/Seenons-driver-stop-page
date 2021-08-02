<template>
    <div class="header">
        <div class="header-container">

            <img src="../assets/img/avatar-empty.png" alt="avatar" class="avatar">
        </div>
        <h2 class="place_name poppins-font">Place Name</h2>
    </div>
</template>

<script>
export default {
  name: 'Header',
  
}
</script>

<style scoped>
.header-container{
    display: flex;
    justify-content: space-around;
}
.avatar{
    width: 120px;
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