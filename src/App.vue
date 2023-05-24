<script setup>
import { ref, computed } from 'vue';

const products = ref([
  {title: 'Яблоки', price: 54.5},
  {title: 'Бананы', price: 32},
  {title: 'Хлеб', price: 21.59},
  {title: 'Сметана', price: 179},
  {title: 'Молоко', price: 122},
  {title: 'Снеки', price: 46},
  {title: 'Шоколад', price: 119.50},
  {title: 'Морковь', price: 11.29},
]);

const query = ref('');

const queryProducts = computed(() => {
  let p = products.value;
  let search = query.value;

  if(search) {
    p = p.filter((product) => {
      return product.title.indexOf(search) !== -1 ||
      // product.price.toString().indexOf(search) !== -1
      product.price <= search;
    })
  }
  return p;
});
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

    {{  }}

    <ul>
      <li
        v-for="product in queryProducts"
        :key="product"
      >
        {{ product.title }} -
        <sup>
          {{ product.price.toLocaleString() }}₽
        </sup>
      </li>
    </ul>
  </div>
</template>

<style>

</style>