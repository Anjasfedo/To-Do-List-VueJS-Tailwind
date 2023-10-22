<script setup>
import Title from './components/Title.vue';
import ListToDo from './components/ListToDo.vue'


import { ref } from 'vue';

// data to do

const modalToDo = ref(false);

const cModalToDo = () => {
  modalToDo.value = false
}

// button

const modalAdd = ref(false);

const cModalAdd = () => {
  modalAdd.value = false
}

</script>

<template>
  <div class="w-5/6 bg-blue-300 mx-auto rounded-2xl m-8 font-sans flex items-center justify-center">
    <div class="p-8 bg-gray-300 w-11/12 ">
      <Title msg="To Do List" class="mb-10"/>
      <ListToDo :modalToDo="modalToDo" :cModalToDo="cModalToDo" :modalAdd="modalAdd" :cModalAdd="cModalAdd"/>
    </div>
  </div>
</template>