## Enuciat:

Fes un condicional boolea si la variable `onSale` esta activa

### Codi proporcionat
if
```vue
<template>
  <p v-if="inStock >10">In stock</p>
</template>
```

### Solució 1
```vue
<script setup>
import { ref } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'

const product = ref('Socks')
const image = ref(socksGreenImage)
const inStock = ref(100)
const onSale = ref(true)

</script>
<template>
  <div class="nav-bar"></div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p v-if="inStock >10">In stock</p>
        <p v-else-if="inStock <= 10 && inStock > 0">Almost sold out!</p>
        <p v-else>Out of Stock</p>
        <p v-if="onSale">On Sale</p>
        <p v-else="onSale">Out of Sale</p>
      </div>
    </div>
  </div>
</template>
```

### Solució 2
```vue
<script setup>
import { ref } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'

const product = ref('Socks')
const image = ref(socksGreenImage)
const inStock = ref(100)
const onSale = ref(true)
</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p v-if="inStock >10">In stock</p>
        <p v-else-if="inStock <= 10 && inStock > 0">Almost sold out!</p>
        <p v-else>Out of Stock</p>
        <p v-show="onSale">On Sale</p>
      </div>
    </div>
  </div>
</template>
```