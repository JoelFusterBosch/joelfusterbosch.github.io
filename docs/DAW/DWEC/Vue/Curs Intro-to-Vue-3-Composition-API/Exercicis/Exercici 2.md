## Enuciat:

Crea un enllaç usant `v-bind` mitjançant `href

### Codi proporcionat
v-bind
```vue
<div class="product-image">
          <img :src="imgverd">
        </div>
```

### Solució
```vue
<script setup>
import { ref } from 'vue'
import imgverd from './assets/images/socks_green.jpeg'
import imgbal from './assets/images/socks_blue.jpeg'
const product = ref('Socks')
const url = ref('https://www.google.com/')
</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img :src="imgverd">
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <a :href="url">{{ url }}</a>
      </div>
    </div>
  </div>
</template>
```