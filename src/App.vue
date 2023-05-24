<script setup>
import { ref, computed } from 'vue';

const products = ref([
  'Бананы',
  'Яблоки',
  'Хлеб',
  'Сметана',
  'Молоко',
  'Снеки',
  'Шоколад',
  'Морковь',
]);

const query = ref('');

const queryProducts = computed(() => {
  return products.value.filter((product) => product.indexOf(query.value) !== -1);
})
</script>

<template>
  <div>
    <input
      type="search"
      placeholder="Поиск продуктов..."
      v-model="query"
    >
    <br>
    <br>

    {{ query }}

    <ul>
      <li
        v-for="product in queryProducts"
        :key="product"
      >
        {{ product }}
      </li>
    </ul>
  </div>
</template>

<style>

</style>