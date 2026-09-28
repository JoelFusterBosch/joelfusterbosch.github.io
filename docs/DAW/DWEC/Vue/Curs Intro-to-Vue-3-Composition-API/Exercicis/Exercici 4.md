## Enuciat:

Mostra urls en forma de llista usant `v-for`:

### Codi proporcionat
fors
```vue
<script setup>
    const details = ref(['50% cotton', '30% wool', '20% polyester'])
  </script>
<template>
  <p v-for="detail in details">{{ detail }}</p>
</template>
```

### Solució
```vue
<script setup>
import { ref } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'

const product = ref('Socks')
const image = ref(socksGreenImage)
const inStock = true
const details = ref(['50% cotton', '30% wool', '20% polyester'])
const urls = ref(["https://www.google.com/","https://github.com/"])
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
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <p v-for="detail in details">{{ detail }}</p>
        <li v-for="url in urls">
          <ul>
            <a href= url >{{ url }}</a>
          </ul>
        </li>
      </div>
    </div>
  </div>
</template>
```