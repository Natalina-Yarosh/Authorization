<template>
    <div class="wrapper">
        <!-- <TheTravalizer/> -->
        <TheWeather />
    </div>
</template>

<script>
// import TheTravalizer from './components/TheTravalizer.vue'
import TheWeather from './components/TheWeather.vue'

export default {
    // components: {TheTravalizer},
    components: {TheWeather},
}
</script>

<style scoped>
.wrapper{
    background-color: #355B3E;
    display: grid;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    padding: 20px;

    @media(max-width: 767px){
     padding: 0;
     display: block;
    }
}
</style>
