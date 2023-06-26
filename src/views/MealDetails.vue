<template>
    <div class="w-[800px] mx-auto">
        <pre>{{ meal }}</pre>
        <h1 class="text-5xl font-bold mb-5">{{ meal.strMeal }}</h1>
        <img :src="meal.strMealThumb" :alt="meal.strMeal"/>
        <div class="grid grid-cols-1 md:grid-cols-3 text-lg py-2">
            <div>
                <strong class="font-bold">Category: </strong>{{ meal.strCategory }}
            </div>
            <div>
                <strong class="font-bold">Area: </strong>{{ meal.strArea }}
            </div>
            <div>
                <strong class="font-bold">Tags: </strong>{{ meal.strTags }}
            </div>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-2">
            <h2 class="text-2xl font-semibold mb-3">Ingredients: </h2>
            <ul>
                
            </ul>
        </div>
        <div>
            <h2 class="text-2xl font-semibold mb-3">Measures</h2>

        </div>
        <p>{{ meal.strInstructions }}</p>
    </div>
</template>
<script setup>
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router';
import axiosClient from '../axiosClient.js'

const route = useRoute()
const meal = ref({})

onMounted(() => {
    axiosClient.get(`lookup.php?i=${route.params.id}`)
     .then(( {data} ) => {
        meal.value = data.meals[0]
     })
})
</script>
<style></style>