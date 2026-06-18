<template>
  <q-page class="q-pa-md">
    <h3>Dragon Ball Characters</h3>

    <SearchBar @search="handleSearch" />

    <CharacterList :characters="filteredCharacters" />
  </q-page>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue'
import axios from 'axios'

import SearchBar from '@/components/SearchBar.vue'
import CharacterList from '@/components/CharacterList.vue'

const characters = ref([])
const searchText = ref('')

function handleSearch(value) {
  searchText.value = value
}

const filteredCharacters = computed(() => {
  return characters.value.filter(character =>
    character.name.toLowerCase().includes(searchText.value.toLowerCase())
  )
})

async function loadCharacters() {
  try {
    const response = await axios.get(
      'https://dragonball-api.com/api/characters?page=1&limit=20'
    )

    characters.value = response.data.items
  } catch (error) {
    console.error(error)
  }
}

onMounted(() => {
  loadCharacters()
})
</script>