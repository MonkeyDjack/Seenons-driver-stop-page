<template>
    <div class="header">
        <div class="header-container">
            <img src="../assets/img/avatar-empty.png" alt="avatar" class="avatar">
        </div>
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

</style>