<script setup>
import Card from "./Card.vue";
import { api } from "../services/api";
import { ref } from "vue";
import { watch } from "vue";

const props = defineProps({
  page: {
    type: Number,
    required: true,
  },
});

const pokemons = ref([]);

watch(
  () => props.page,
  async () => {
    pokemons.value = [];
    const initialIndex = props.page * 20 - 19;

    for (let i = initialIndex; i <= initialIndex + 20; i++) {
      const { data } = await api.get(`${i}`);

      pokemons.value = [...pokemons.value, data];
    }
  },
  {
    immediate: true,
  }
);
</script>

<template>
  <div class="container">
    <Card
      v-for="pokemon in pokemons"
      :name="pokemon.name"
      :id="pokemon.id"
      :types="[...pokemon.types]"
    />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
}
</style>
