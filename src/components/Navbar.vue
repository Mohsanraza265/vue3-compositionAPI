<template>
    <RouterLink active-class="active" to="/">Home</RouterLink>
    <RouterLink active-class="active" to="/about">About</RouterLink>
</template>

<script setup>
    import { RouterLink } from 'vue-router';
</script>

<style scoped>
a {
    color: black;
    padding: 12px;
    font-weight: bold;
    text-decoration: none;
}
.active {
    background-color: black;
    color: white;
    margin: 0px 10px;
}
</style>