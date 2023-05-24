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
        v-show="user.age <= 21"
      >
        {{  user.name }}
        <sup>{{ user.age }}</sup>
      </li>
    </ul>
  </div>
</template>
