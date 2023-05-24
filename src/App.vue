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
        <sup v-if="user.name !== 'Oleg'">
          {{ user.age }}
        </sup>

        <span v-else-if="user.age === 50">
          В расцвете сил
        </span>

        <span v-else>
          В возрасте
        </span>
      </li>
    </ul>
  </div>
</template>
