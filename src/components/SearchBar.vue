<template>
  <div class="q-mb-md">
    <q-input
      outlined
      v-model="search"
      label="Buscar personaje"
      @update:model-value="emitSearch"
    >
      <template v-slot:prepend>
        <q-icon name="search" />
      </template>
    </q-input>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['search'])

const search = ref('')

function emitSearch() {
  emit('search', search.value)
}
</script>