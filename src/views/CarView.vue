<script setup>
import { useRoute, RouterView, useRouter } from "vue-router"
import { ref, onBeforeMount } from "vue"
import carsData from "../data.json"

const router = useRouter()
const currentCar = ref(null)
const route = useRoute()
const { id } = route.params

onBeforeMount(() => {
    currentCar.value = carsData.find(car => car.id === parseInt(id))
})
</script>

<template>
    <div class="container">
        <div v-if="currentCar">
            <h1>Car Information</h1>
            <p>Make: {{ currentCar.make }}</p>
            <p>Body: {{ currentCar.body }}</p>
            <p>Price: {{ currentCar.price }}</p>
            <p>Year: {{ currentCar.year }}</p>
        </div>
        <div v-else>
            <p>Car Not Found</p>
        </div>
    </div>
    <button @click="router.back()">Go Back</button>
    <RouterView />
</template>

<style scoped>
.container {
    background-color: white;
    padding: 10px 20px;
    border: 1px solid black;
}

button {
    margin-top: 20px;
    padding: 5px 20px;
    border: 1px solid black;
}
</style>