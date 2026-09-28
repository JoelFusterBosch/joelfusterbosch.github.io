## Enuciat:

Crea una descripció des de `App.vue`

### Codi proporcionat
product
```vue
<script setup>
  const product = ref('Socks')
</script>
  <template>
    <div class="product-display">
      <div class="product-container">
        <div class="product-info">
          <h1>{{ product }}</h1>
        </div>
      </div>
    </div>
  </template>
```

### Solució
```vue
<script setup>
import {ref} from 'vue'

const product = ref('Socks')
const description = ref('Nano')

</script>
<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p>{{ description }}</p>
      </div>
    </div>
  </div>
</template>
```