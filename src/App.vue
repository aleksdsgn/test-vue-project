<script setup>
import { ref } from 'vue';

const users = ref([
  {id: 1, name: 'Emily', age: 21},
  {id: 2, name: 'Eva', age: 25},
  {id: 3, name: 'Oleg', age: 50},
]);

</script>

<template>
  <div>
    <ul>
      <li
        v-for="user in users"
        :key="user.id"
      >
        {{  user.name }}
        <sup :class="{
          'red': user.age < 30,
          'fz-24': user.name === 'Eva',
          }">
          {{ user.age }}
        </sup>
      </li>
    </ul>
  </div>
</template>

<style>
  .red {
    color: red;
  }

  .fz-24 {
    font-size: 24px;
  }
</style>