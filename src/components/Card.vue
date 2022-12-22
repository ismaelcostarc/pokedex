<script setup>
const props = defineProps({
  id: {
    type: Number,
    required: true,
  },
  name: {
    type: String,
    required: true,
  },
  backgroundColor: {
    type: String,
    required: true,
  },
  types: {
    type: Array,
    required: true,
  },
});

const url = `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${props.id}.png`;
</script>

<template>
  <div class="card" :style="{ backgroundColor: props.backgroundColor }">
    {{ props.types[0].name }}
    <div class="card__img">
      <img :src="url" :alt="`${name} Image`" />
    </div>
    <h1 class="card__name">
      {{ props.id + ". " + props.name }}
    </h1>
    <div class="card__type">
      <span v-for="(type, index) in props.types">
        {{ type.type.name }}
        <span v-if="index !== props.types.length - 1"> / </span>
      </span>
    </div>
  </div>
</template>

<style scoped lang="scss">
.card {
  height: 15rem;
  width: 15rem;
  border-radius: 7%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-family: "Andika", sans-serif;

  &__name {
    font-weight: bold;
    font-size: 1.5rem;
  }

  &__type {
    padding: 0.4rem;
    color: grey;
  }

  &__img {
    background-color: #fff;
    border-radius: 100%;
    margin-bottom: 1rem;
  }
}
</style>
