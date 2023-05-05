<script setup lang="ts">
import ModalView from './ModalView.vue';
import { ref } from 'vue';

const modalActive = ref(null);
const products = ref(null);
fetch('https://testapi.jasonwatmore.com/products')
    .then(response => response.json())
    .then(data => products.value = data);

const toggleModal = () =>{
  modalActive.value = !modalActive.value
}



defineProps<{
  msg: string
}>()
</script>

<template>
  <div class="greetings">
   <h2>HHHH</h2>
   <button @click="toggleModal">Open Modal</button>
  </div>

  <h5 class="card-header text-center">Vue 3 fetch data from API</h5>
        <div class="card-body">
            <div v-if="products">
                <h5>Products</h5>
                <ul class="mb-0">
                    <li v-for="product in products" :key="product.id">{{product.name}}</li>
                </ul>
            </div>
            <div v-if="!products" class="text-center">
                <div class="spinner-border spinner-border-sm"></div>
            </div>
        </div>
        
  <ModalView :modalActive = modalActive @close-modal="toggleModal">
   <h2>This is modal</h2>
   <p>Lorem Ipsum</p>
   <h2>This is modal</h2>
   <p>Lorem Ipsum</p>


  </ModalView>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}


</style>
