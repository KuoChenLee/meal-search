<template>
    <header class="bg-white shaddow h-16 flex justify-between item-stretch">
      <router-link :to="{name: 'home'}" class="text-xl inline-flex items-center px-5">
        Home
      </router-link>
      <div class="flex items-center gap-1 ">
        <router-link :to="{name: 'byName'}" class="px-2 h-full hover:bg-purple-100 rounded-lg inline-flex items-center transition-colors">
          Search Meals
        </router-link>
        <router-link :to="{name: 'byLetter'}" class="px-2 h-full hover:bg-purple-100 rounded-lg inline-flex items-center transition-colors">
          Meals By Letter
        </router-link>
        <router-link :to="{name: 'byIngredient'}" class="px-2 h-full hover:bg-purple-100 rounded-lg inline-flex items-center transition-colors">
          Meals By Ingredients
        </router-link>
      </div>
    </header>
</template>
<script setup></script>
<style></style>