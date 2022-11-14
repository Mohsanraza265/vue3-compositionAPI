<template>
    <h2>Home View Page</h2>
    <div class="cars">
        <RouterLink :to="`/cars/${car.id}`" v-for="car in cars" :key="car.id" >
            {{car.name}}
        </RouterLink>
    </div>
</template>

<script setup>
    import cars from '../data/cars.json'
    import { RouterLink } from 'vue-router';
</script>

<style scoped>
a {
    color: black;
    padding: 12px;
    font-weight: bold;
    text-decoration: none;
}
.cars{
    display: flex;
}
.cars a {
    text-decoration: none;
    color: black;
    width: 100%;
    box-shadow: 1px 1px 10px black;
    margin: 10px;
}
</style>