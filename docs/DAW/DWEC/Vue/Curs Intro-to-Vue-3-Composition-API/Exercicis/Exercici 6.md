## Enuciat:

Crea una variable booleana `onSale` que mostre el `brand + product` quan estiga en true

### Codi proporcionat

computed
```vue
import { ref, computed } from 'vue'
<script setup>
const product = ref('Socks')
const brand = ref('Vue Mastery')

const title = computed(() => {
  return brand.value + ' ' + product.value
})
</script>
<template>
   <h1>{{ title }}</h1>
</template>
```
canviar imatge
```vue
<script setup>
  import socksGreenImage from './assets/images/socks_green.jpeg'
  import socksBlueImage from './assets/images/socks_blue.jpeg'
  const selectedVariant = ref(0)
</script>
<template>

  <div class="product-image">    
    <img v-bind:src="image">
  </div>

  <div 
    v-for="(variant, index) in variants" 
    :key="variant.id"
    @mouseover="updateVariant(index)"
    class="color-circle"
    :style="{ backgroundColor: variant.color }"
  >
</template>
```

### Solució 1
```vue
<script setup>
import { ref, computed } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'
import socksBlueImage from './assets/images/socks_blue.jpeg'

const product = ref('Socks')
const brand = ref('Vue Mastery')
const onSale = ref(true)
const selectedVariant = ref(0)
  
const details = ref(['50% cotton', '30% wool', '20% polyester'])

const variants = ref([
  { id: 2234, color: 'green', image: socksGreenImage, quantity: 50 },
  { id: 2235, color: 'blue', image: socksBlueImage, quantity: 0 },
])

const cart = ref(0)

const title = computed(() => {
  return brand.value + ' ' + product.value
})

const image = computed(() => {
  return variants.value[selectedVariant.value].image
})

const inStock = computed(() => {
  return variants.value[selectedVariant.value].quantity > 0
})

const addToCart = () => cart.value += 1

const updateVariant = (index) => {
  selectedVariant.value = index
}

</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart }})</div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1 v-if="onSale">{{ title }}</h1>
        <h1 v-else>Not on Sale</h1>
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
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

## Solució 2
```vue
<script setup>
import { ref, computed } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'
import socksBlueImage from './assets/images/socks_blue.jpeg'

const product = ref('Socks')
const brand = ref('Vue Mastery')
const onSale = ref(true)
const selectedVariant = ref(0)
  
const details = ref(['50% cotton', '30% wool', '20% polyester'])

const variants = ref([
  { id: 2234, color: 'green', image: socksGreenImage, quantity: 50 },
  { id: 2235, color: 'blue', image: socksBlueImage, quantity: 0 },
])

const cart = ref(0)

const title = computed(() => {
  return onSale.value ? brand.value + ' ' + product.value : 'Not on Sale' 
})

const image = computed(() => {
  return variants.value[selectedVariant.value].image
})

const inStock = computed(() => {
  return variants.value[selectedVariant.value].quantity > 0
})

const addToCart = () => cart.value += 1

const updateVariant = (index) => {
  selectedVariant.value = index
}

</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart }})</div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1 v-if="onSale">{{ title }}</h1>
        <h1 v-else>Not on Sale</h1>
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
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