<template>
    <div class="wrapper">
        <TheTravalizer/>
    </div>
</template>

<script>
import TheTravalizer from './components/TheTravalizer.vue'

export default {
    components: {TheTravalizer},
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
}
</style>
