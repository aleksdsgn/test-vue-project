<script setup>
import { ref, reactive } from 'vue';

const count = ref(0);
const counter = reactive({
  count: 5
});

const increment = () => {
  count.value++
}
const increment1 = () => {
  counter.count++
}
</script>

<template>
  <div>
    <button @click="increment">
      Count:
      <strong>{{ count }}</strong>
    </button>
    <button @click="increment1">
      Count1:
      <strong>{{ counter.count }}</strong>
    </button>
  </div>
</template>
