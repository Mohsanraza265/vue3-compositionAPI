<template>
    <div v-if="car">
        <h2>Cars View</h2>
        <p>{{ car.name }}</p>
        <p>{{ car.price }}</p>
        <p>{{ car.year }}</p>
        <button @click="router.push(`/cars/${carID}/contact`)">Click Child Component</button>
        <RouterView />
    </div>
    <div v-else>
        <h2>Car not Found! </h2>
    </div>
</template>

<script setup>
import { useRoute, RouterView } from 'vue-router';
import cars from '../data/cars.json'
import router from '../router';
// import ContactView from './ContactView.vue'

const route = useRoute()
//only for open contact page
const carID = parseInt(route.params.id)

const car = cars.find(c => c.id === carID)


</script>