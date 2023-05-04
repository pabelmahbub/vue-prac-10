<script setup lang="ts">
import ModalView from './ModalView.vue';
import { ref } from 'vue';

const modalActive = ref(null);
const data = []
const toggleModal = () =>{
  modalActive.value = !modalActive.value
}

fetch('https://jsonplaceholder.typicode.com/posts')
      .then(response => response.json())
      .then(json => console.log(json))

defineProps<{
  msg: string
}>()
</script>

<template>
  <div class="greetings">
   <h2>HHHH</h2>
   <button @click="toggleModal">Open Modal</button>
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
