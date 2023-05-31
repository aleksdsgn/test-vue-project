<script>
import { reactive, defineComponent } from 'vue';
import UButton from './UButton.vue';
import axios from 'axios';
import UFile from './global/UFile.vue';

export default defineComponent({
  name: 'ReviewForm',

  components: {
    UButton,
    UFile
},

  setup() {
    const review = reactive({
      author: '',
      stars: null,
      text: '',
      photo: null,
      isRecommended: true,
    })

    const stars = [1,2,3,4,5]
    
    const submit = () => {
      console.log('submit!');

      axios.post('/api/review', review, {
        headers: {
          'Content-Type': 'multipart/form-data',
        }
      })
      .then((res) => {
        console.log(res);
      })
      .catch((err) => {
        console.log(err);
      })
      .finally(() => {
        console.log('Конец!');
      })
    }

    return {
      review,
      stars,
      submit
    }
  }

});
</script>

<template>
  <form
    @submit.prevent.stop="submit"
    class="container pt-5 pb-5"
  >
    <UInput
      v-model="review.author"
      placeholder="Как вас зовут?"
    />

    <UInput
      type ="textarea"
      v-model="review.text"
      placeholder="Что понравилось что нет?"
    />
    
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

    <UFile
      v-model="review.photo"
      label="Фото"
    />

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

    <UButton>
      Отправить!
    </UButton>
  </form>
</template>