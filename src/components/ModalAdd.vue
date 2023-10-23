<script setup lang="js">
import { ref } from 'vue';

const props = defineProps({
modalAdd: {
    type: Boolean,
    required: true,
  },
  cModalAdd: {
    type: Function,
    required: true,
  },
  toDoList: {
    type: Array,
    required: true,
  },
  addToDoList: {
    type: Function,
    required: true,
  }
})

const dataInput = ref({id: Date.now(), toDo: '', description: ''})

</script>

<template lang="html">
    <div class="bg-slate-500 w-full h-80 p-12">
        <button @click="cModalAdd">tutup</button>
      <form @submit.prevent="addToDoList(dataInput)" class="flex flex-col space-y-4">
        <div>
          <label for="nameToDo" class="text-white">Name To Do</label>
          <input v-model="dataInput.toDo" type="text" id="nameToDo" class="w-full bg-gray-200 p-2 rounded" />
        </div>
  
        <div>
          <label for="Description" class="text-white">Description</label>
          <input v-model="dataInput.description" type="text" id="Description" class="w-full bg-gray-200 p-2 rounded" />
        </div>
  
        <div>
          <button type="submit" class="w-full bg-green-500 text-white p-2 rounded hover:bg-green-600">
            Submit
          </button>
        </div>
      </form>
    </div>
  </template>
  
  
<style lang="css">

</style>
