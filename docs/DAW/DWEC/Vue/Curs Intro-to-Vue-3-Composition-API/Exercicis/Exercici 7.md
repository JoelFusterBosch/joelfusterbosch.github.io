## Enuciat:

Crea una nova classe anomenada `ProductDetails` que reba els detalls en forma de `Array` 

### Codi proporcionat

### App.vue
```vue
<script setup>
import { ref } from 'vue'
import ProductDisplay from '@/components/ProductDisplay.vue'

const cart = ref(0)
const premium = true

</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart }})</div>
  <ProductDisplay :premium="premium"></ProductDisplay>
</template>
```

### ProductDisplay.vue
```vue
<script setup>
import { ref, computed } from 'vue'
import socksGreenImage from '../assets/images/socks_green.jpeg'
import socksBlueImage from '@/assets/images/socks_blue.jpeg'

const props = defineProps({
  premium: {
    type: Boolean,
    required: true
  }
}) 

const product = ref('Socks')
const brand = ref('Vue Mastery')

const selectedVariant = ref(0)
  
const details = ref(['50% cotton', '30% wool', '20% polyester'])

const variants = ref([
  { id: 2234, color: 'green', image: socksGreenImage, quantity: 50 },
  { id: 2235, color: 'blue', image: socksBlueImage, quantity: 0 },
])

const title = computed(() => {
  return brand.value + ' ' + product.value
})

const image = computed(() => {
  return variants.value[selectedVariant.value].image
})

const inStock = computed(() => {
  return variants.value[selectedVariant.value].quantity > 0
})

const shipping = computed(() =>{
  if (props.premium){
    return 'Free'
  }
  else {
    return 2.99
  }
})

const addToCart = () => cart.value += 1

const updateVariant = (index) => {
  selectedVariant.value = index
}
</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1>{{ title }}</h1>
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <p>Shipping: {{ shipping }}</p>
        <ul>
          <li v-for="detail in details">{{ detail }}</li>
        </ul>
        <div 
          v-for="(variant, index) in variants" 
          :key="variant.id"
          @mouseover="updateVariant(index)"
          class="color-circle"
          :style="{ backgroundColor: variant.color }"
        >
        </div>
        <button
          class="button" 
          :class="{ disabledButton: !inStock }"
          :disabled="!inStock"
          v-on:click="addToCart"
        >
          Add to cart
        </button>
      </div>
    </div>
  </div>
</template>
```

### Solució
#### App.vue
```vue
<script setup>
import { ref } from 'vue'
import ProductDisplay from '@/components/ProductDisplay.vue'
import ProductDetails from '@/component/ProductDetails.vue'

const cart = ref(0)
const premium = ref(true)
const details = ref(true)
</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart }})</div>
  <ProductDisplay :premium="premium"></ProductDisplay>
  <ProductDetails :details="details"></ProductDetails>
</template>
```

#### ProductDisplay.vue

```vue
<script setup>
import { ref, computed } from 'vue'
import socksGreenImage from '@/assets/images/socks_green.jpeg'
import socksBlueImage from '@/assets/images/socks_blue.jpeg'

const props = defineProps({
  premium: {
    type: Boolean,
    required: true
  }
})

const product = ref('Socks')
const brand = ref('Vue Mastery')

const selectedVariant = ref(0)
  

const variants = ref([
  { id: 2234, color: 'green', image: socksGreenImage, quantity: 50 },
  { id: 2235, color: 'blue', image: socksBlueImage, quantity: 0 },
])

const title = computed(() => {
  return brand.value + ' ' + product.value
})

const image = computed(() => {
  return variants.value[selectedVariant.value].image
})

const inStock = computed(() => {
  return variants.value[selectedVariant.value].quantity > 0
})

const shipping = computed(() => {
  if (props.premium) {
    return 'Free'
  }
  else {
    return 2.99
  }
})

const addToCart = () => cart.value += 1

const updateVariant = (index) => {
  selectedVariant.value = index
}
</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1>{{ title }}</h1>
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <p>Shipping: {{ shipping }}</p>
        
        <div 
          v-for="(variant, index) in variants" 
          :key="variant.id"
          @mouseover="updateVariant(index)"
          class="color-circle"
          :style="{ backgroundColor: variant.color }"
        >
        </div>
        <button
          class="button" 
          :class="{ disabledButton: !inStock }"
          :disabled="!inStock"
          v-on:click="addToCart"
        >
          Add to cart
        </button>
      </div>
    </div>
  </div>
</template>
```

#### ProductDetails.vue

```vue
<script setup>
import { ref, computed } from 'vue'
import socksGreenImage from '@/assets/images/socks_green.jpeg'
import socksBlueImage from '@/assets/images/socks_blue.jpeg'

const props = defineProps({
  details: {
    type: Boolean,
    required: true
  }
})


const details = computed(() => {
  if (props.details) {
    return ['50% cotton', '30% wool', '20% polyester']
  }
  else {
    return 'No details available'
  }
})

</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-info">
        <ul>
          <li v-for="detail in details">{{ detail }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>
```