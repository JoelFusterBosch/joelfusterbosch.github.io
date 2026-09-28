## Enuciat:

Crea un apartat de **"Would you recommend this product"** al formulari

### Codi proporcionat

?

### Solució
#### Form.vue
```vue
<script setup>
import { reactive } from 'vue'

const emit = defineEmits(['review-submitted'])

const review = reactive({
  name: '',
  content: '',
  rating: null,
  recommends: null
})

const onSubmit = () => {
  if (review.name === '' || review.content === '' || review.rating === null || review.recommends === null) {
    alert('Review is incomplete. Please fill out every field.')
    return
  }

  const productReview = {
    name: review.name,
    content: review.content,
    rating: review.rating,
    recommends: review.recommends
  }
  emit('review-submitted', productReview)

  review.name = ''
  review.content = ''
  review.rating = null
  review.recommends = null
}
</script>

<template>
  <form class="review-form" @submit.prevent="onSubmit">
    <h3>Leave a review</h3>
    <label for="name">Name:</label>
    <input id="name" v-model="review.name">

    <label for="review">Review:</label>      
    <textarea id="review" v-model="review.content"></textarea>

    <label for="rating">Rating:</label>
    <select id="rating" v-model.number="review.rating">
      <option>5</option>
      <option>4</option>
      <option>3</option>
      <option>2</option>
      <option>1</option>
    </select>
    <label for="recommend">Do you recommend ths product?</label>
    <select id="recommend" v-model.number="review.recommends">
      <option>Yes</option>
      <option>No</option>
    </select>

    <input class="button" type="submit" value="Submit">
  </form>
</template>
```

#### List.vue
```vue
<script setup>
defineProps({
  reviews: {
    type: Array,
    required: true
  }
})
</script>

<template>
  <div class="review-container">
    <h3>Reviews:</h3>
    <ul>
      <li v-for="(review, index) in reviews" :key="index">
        <span>{{ review.name }} gave this {{ review.rating }} stars</span>
        <br/>
        <span>"{{ review.content }}"</span><br/>
        <span>Do you recommend this product: {{ review.recommends }}</span>
      </li>
    </ul>
  </div>
</template>
```