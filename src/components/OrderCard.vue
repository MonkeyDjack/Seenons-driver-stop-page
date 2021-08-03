<template>
    <div class="order-card" v-for="order in stop.orders" :key="order.order_id">
        <img src="" alt="">
        <h3>{{order.stream_type}}</h3>
        <ul>
            <li>quantity: {{order.quantity}}</li>
            <li>size: {{order.size}} kg</li>
            <li>status: {{order.status}}</li>
            <li>type: {{order.type}}</li>
        </ul>
    </div>
</template>

<script>
    export default{
        name: 'OrderCard',
        props:{
            stop: Object,
        },
    }
</script>

<style scoped>

</style>