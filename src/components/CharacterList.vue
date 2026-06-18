<template>
  <div class="row justify-center q-col-gutter-lg">
    <div
      v-for="character in characters"
      :key="character.id"
      class="col-auto"
    >
      <CharacterCard :character="character" />
    </div>
  </div>
</template>

<script setup>
import CharacterCard from './CharacterCard.vue'

defineProps({
  characters: {
    type: Array,
    required: true,
  },
})
</script>