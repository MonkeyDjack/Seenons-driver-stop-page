<template>
    <div class="popup">
        <div class="popup-inner">
            <h3>Describe Stop Issue</h3>
            <slot/>
            <img class="close-popup" src="https://img.icons8.com/material-outlined/24/000000/close-window.png" @click="togglePopup"/>
        </div>
    </div>
</template>

<script>
    export default{
        name: 'Popup',
        props:['togglePopup']
    }
</script>

<style scoped>
.popup{
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 98;
    background-color: rgba(0,0,0,0.2);
    display: flex;
    align-items: center;
    justify-content: center;
}

.popup-inner{
    z-index: 99;
    position: relative;
    background: #fff;
    padding: 32px;
}

.close-popup{
    position: absolute;
    top:10px;
    right: 10px;
}
</style>