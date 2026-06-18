<template>
  <q-page class="q-pa-md">
    <h3>Dragon Ball Characters</h3>

    <SearchBar @search="handleSearch" />

    <p>Búsqueda: {{ searchText }}</p>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
import SearchBar from '@/components/SearchBar.vue'

const searchText = ref('')

function handleSearch(value) {
  searchText.value = value
}
</script>