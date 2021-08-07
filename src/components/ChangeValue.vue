<template>
    <input type="text" class="changeInput poppins-font" ref="change" :value="change"> <button onclick="changeinput(change)">change</button>
    <!--<span @click = "todo.edit = true;"> {{todo.title}}</span>-->
</template>

<script>
    export default{
        name: 'ChangeValue',
        props:{
           change : Number,
        },
        
    }
</script>

<style scoped>
.changeInput{
    background: transparent;
    border:  none;
    width: cover;
    color: white;
}
</style>