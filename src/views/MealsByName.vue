<template>
    <div class="p-8 pb-0">
        <input
             type="text"
             class="rounded border-2 border-gray-200 w-full"
             placeholder="搜尋食譜(例如: 炒蛋、滷肉飯)"
             v-model="text"
             @change="searchmeals"
            />
    </div>
    <h1>{{ text }}</h1>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
        <div v-for="meal of meals" :key="meal.idMeal" class="bg-white shadow rounded-xl">
           <router-link :to="{name: 'mealDetails', params: {id: meal.idMeal}}">
            <img :src="meal.strMealThumb" :alt="strMeal" class="rounded-t-2xl w-full h-64 object-cover"/>
           </router-link>
            
            <!-- <p>{{ meal.strInstructions }}</p> -->
            <div class="p-3">
                <h3 class="font-bold mb-4">{{ meal.strMeal }}</h3>
                <div class="flex items-center justify-between">
                    <a :href="meal.strYoutube" target="_blank" class="text-white px-3 py-2 rounded border-2 border-red-600 bg-red-500 hover:bg-red-600 hover:text-white transition-colors" style="font-family: fantasy;">Youtube</a>
                    <!-- <a :href="meal.strSource" class="text-white px-3 py-2 rounded border-2 border-green-600 bg-green-500 hover:bg-green-600 hover:text-white transition-colors" style="font-family: fantasy;">Source</a> -->
                    <!-- <router-link to="/" class="px-3 py-2 rounded border-2 border-gray-600 hover:bg-gray-600 hover:text-white transition-colors">
                        View
                    </router-link> -->
                </div>
            </div>
        </div>
    </div>
    <!-- <pred>{{ meals }}</pred> -->
</template>
<script setup>
    import { computed, onMounted, ref } from 'vue'
    import store from '../store'
import { useRoute } from 'vue-router';

    const route = useRoute()
    const text = ref('')
    const keyword = ref('')
    const meals = computed(() => store.state.searchedMeals)

    const searchmeals=()=>{
        store.dispatch('searchMeals', keyword.value)
    }
    onMounted(() => {
        keyword.value = route.params.name
        if (keyword.value){
            searchmeals()
        }
    })   
</script>
<script>
</script>