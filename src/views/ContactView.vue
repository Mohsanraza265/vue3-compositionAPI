<template>
    <div>
        <h2>Contant Page</h2>
        <p>{{car.contact.dealer}}</p>
        <p>{{car.contact.number}}</p>
    </div>
</template>

<script setup>
import { useRoute} from 'vue-router';
import cars from '../data/cars.json'
const route = useRoute()
const car = cars.find(c => c.id === parseInt(route.params.id))


</script>