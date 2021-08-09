<template>
   <slot/> <button @click="toggleChange(id)">change</button>
</template>

<script>
    export default{
        name: 'ChangeValue',
        props:{
           change : Number,
           id: String,
        },
        methods: {
            toggleChange(id){
                console.log(id)
                console.log(this.$refs)
                console.log(this.$refs[id])
                
            },
        }
        
    }
</script>

<style scoped>
</style>