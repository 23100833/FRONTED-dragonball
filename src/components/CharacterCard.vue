<template>
  <q-card class="my-card bg-blue-1">
    <q-img
      :src="character.image"
      :alt="character.name"
      height="320px"
      fit="contain"
    />

    <q-card-section>
      <div class="text-h6">
        {{ character.name }}
      </div>

      <div>
        <strong>Raza:</strong>
        {{ character.race }}
      </div>

      <div>
        <strong>Género:</strong>
        {{ character.gender }}
      </div>

      <div>
        <strong>Afiliación:</strong>
        {{ character.affiliation }}
      </div>

      <div>
        <strong>Ki:</strong>
        {{ character.ki }}
      </div>
    </q-card-section>
  </q-card>
</template>

<script setup>
defineProps({
  character: {
    type: Object,
    required: true,
  },
})
</script>

<style scoped>
.my-card {
  width: 320px;
  border-radius: 20px;
  transition: transform 0.3s;
}

.my-card:hover {
  transform: scale(1.03);
}
</style>