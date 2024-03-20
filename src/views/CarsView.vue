<script setup>
import carsData from "../data.json"
import { ref, watch, onMounted } from "vue";
import { useRouter, useRoute } from "vue-router";

const router = useRouter()
const route = useRoute()
const cars = ref(carsData)

const make = ref("All")


onMounted(() => {
    make.value = route.query.make || ""
})


watch(make, () => {
    if (make.value) {
        if (make.value === "All") cars.value = carsData
        else {
            cars.value = carsData.filter(car => car.make === make.value)
        }
    }
})


//Query parameter.
function handleChange() {
    router.push({ query: { make: make.value } })

}

</script>

<template>
    <main class="container">
        <h1>Our Cars</h1>
        <select
            @change="handleChange"
            v-model="make"
        >
            <option value="All">All</option>
            <option value="Chevrolet">Chevrolet</option>
            <option value="Porsche">Porsche</option>
            <option value="Audi">Audi</option>
        </select>
        <p>Press on the car for more information!</p>
        <div class="cars">
            <div
                v-for="car in cars"
                class="cards"
                :key="car.id"
                @click="router.push(`/car/${car.id}`)"
            >
                <h2>{{ car.make }}</h2>
                <p class="price">${{ car.price }}</p>
            </div>
        </div>
    </main>
</template>

<style scoped>
.cars {
    flex-wrap: wrap;
    display: flex;
    padding: 10px;
    gap: 10px;
    cursor: pointer;
}

.cards {
    display: flex;
    flex-direction: column;

    padding: 10px;
    border: 1px solid black;

    min-width: 150px;

    background-color: white;

}

.price {
    margin-top: 15px;
}
</style>


