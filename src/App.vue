<script setup>
import Pagination from "./components/Pagination.vue";
import List from "./components/List.vue";
import Title from "./components/Title.vue";
import { ref } from "vue";

const page = ref(1);

const setPage = (number) => {
  page.value = number;
};
</script>

<template>
  <div class="parent">
    <Title />
    <Pagination @selectPage="setPage" />
    <Suspense>
      <List :page="1" />
      <template #fallback> Loading... </template>
    </Suspense>
  </div>
</template>

<style scoped>
.parent {
  background: rgb(0, 255, 46);
  background: linear-gradient(
    138deg,
    rgba(0, 255, 46, 1) 0%,
    rgba(254, 255, 0, 1) 20%,
    rgba(255, 0, 0, 1) 100%
  );
  height: 100vh;
  padding: 2rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
</style>
