<script setup>
import { reactive, computed } from 'vue';

const review = reactive({
  author: '',
  stars: null,
  text: '',
  photo: null,
  isRecommended: true,
});
const previewFilePath = computed(() => {
  if(review.photo) {
    return URL.createObjectURL(review.photo);
  }

  return '#';
});

const stars = [1,2,3,4,5];

const submit = () => {
  console.log('submit!');
};
const uploadFile = (e) => {
  const [file] = e.target.files;
  review.photo = file;
};
</script>

<template>
  <form
    @submit.prevent.stop="submit"
    class="container pt-5 pb-5"
  >
    <input
      v-model="review.author"
      type="text"
      placeholder="Как вас зовут?"
      class="form-control mb-3"
    >

    <textarea
      v-model="review.text"
      rows="3"
      placeholder="Что понравилось что нет?"
      class="form-control mb-3"
    ></textarea>

    <h4>Оценка</h4>
    <div
      v-for="star in stars"
      :key="star"
      class="form-check"
    >
      <input
        class="form-check-input"
        type="checkbox"
        v-model="review.stars"
        :true-value="star"
        :false-value="null"
        :id="`star${ star }`"
      >
      <label class="form-check-label" :for="`star${ star }`">
        {{ star }}
      </label>
    </div>
    <!-- /.form-check -->

    <div class="mb-3 mt-3">
      <label class="form-label">Фото</label>
      <input
        class="form-control"
        type="file"
        @change="uploadFile"
      >

      <img :src="previewFilePath" alt="" class="w-100 mt-2">
    </div>
    <!-- /.mb-3 mt-3 -->

    <div class="form-check">
      <input
        class="form-check-input"
        type="radio"
        id="advice1"
        v-model="review.isRecommended"
        :value="false"
      >
      <label class="form-check-label" for="advice1">
        Не советую
      </label>
    </div>
    <!-- /.form-check -->

    <div class="form-check">
      <input
        class="form-check-input"
        type="radio"
        id="advice2"
        v-model="review.isRecommended"
        :value="true"
      >
      <label class="form-check-label" for="advice2">
        Советую!
      </label>
    </div>
    <!-- /.form-check -->

    <button class="btn btn-primary mt-4">
      Отправить!
    </button>
  </form>
</template>

<style>

</style>