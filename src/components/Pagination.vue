<script setup>
import { ref, watch } from "vue";

const emit = defineEmits(["selectPage"]);

const page = ref(1);

const increasePage = () => {
  page.value = page.value + 1;
};
const decreasePage = () => {
  if (page.value > 1) {
    page.value = page.value - 1;
  }
};

watch(page, (newValue) => {
  emit("selectPage", newValue);
});
</script>

<template>
  <div class="pagination">
    <button
      @click="decreasePage"
      :disabled="page <= 1"
      class="pagination__button"
    >
      <img src="../assets/chevron-left-solid.svg" />
    </button>
    <div class="pagination__number">{{ page }}</div>
    <button @click="increasePage" class="pagination__button">
      <img src="../assets/chevron-right-solid.svg" />
    </button>
  </div>
</template>

<style scoped lang="scss">
.pagination {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
  font-family: "Andika", Arial, Helvetica, sans-serif;

  &__number {
    font-size: 2rem;
  }

  &__button {
    height: 3rem;
    width: 3rem;
    border-radius: 100%;
    border: 0;

    img {
      height: 1rem;
    }

    &:hover {
      border: 2px solid rgb(0, 224, 108);
      cursor: pointer;
    }
  }
}
</style>
