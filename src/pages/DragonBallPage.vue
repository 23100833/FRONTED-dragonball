<template>
  <q-page class="q-pa-lg dragonball-page">
    <h2 class="title-dragonball text-center q-mb-xl">
        Dragon Ball Explorer
    </h2>

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
      'https://dragonball-api.com/api/characters?page=1&limit=100'
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

<style scoped>
.dragonball-page {
  min-height: 100vh;
  background: linear-gradient(
    180deg,
    #fff3e0 0%,
    #e3f2fd 100%
  );
}

.title-dragonball {
  color: #ff6f00;
  font-size: 3rem;
  font-weight: 900;
  letter-spacing: 2px;
}
</style>