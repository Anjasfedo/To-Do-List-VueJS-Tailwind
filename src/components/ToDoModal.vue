<script setup lang="js">
import { ref } from 'vue';

const props = defineProps({
  idModalToDo: {
    type: Object,
  },
  deleteToDoList: {
    type: Function,
    required: true,
  },
  editToDoList: {
    type: Function,
    required: true,
  }
})

const editable = ref(false)
</script>
<template lang="html">
    <div class="bg-slate-500 w-96 h-80 p-4">
      <div class="flex items-center space-x-2">
        <label for="editToDo" class="text-white">Edit To Do</label>
        <input id="editToDo" type="checkbox" v-model="editable" class="form-checkbox h-5 w-5 text-green-500">
      </div>
  
      <div v-if="!editable">
        <div class="text-white">
          <p class="text-lg">To Do: {{ props.idModalToDo.toDo }}</p>
          <p class="text-sm">Description: {{ props.idModalToDo.description }}</p>
        </div>
      </div>
      <div v-else>
        <div class="mt-4">
          <label for="editToDoText" class="text-white">To Do</label>
          <input type="text" v-model="props.idModalToDo.toDo" id="editToDoText" class="w-full bg-gray-200 p-2 rounded">
  
          <label for="editDescription" class="text-white">Description</label>
          <input type="text" v-model="props.idModalToDo.description" id="editDescription" class="w-full bg-gray-200 p-2 rounded">
        </div>
        <button @click="editToDoList(props.idModalToDo.id)" class="mt-4 bg-blue-500 mr-6 text-white p-2 rounded hover:bg-red-600">
            Edit To Do
        </button>
        <button @click="deleteToDoList(props.idModalToDo.id)" class="mt-4 bg-red-500 text-white p-2 rounded hover:bg-red-600">
            Delete To Do
        </button>
      </div>
    </div>
  </template>
  
  
  
<style lang="css">

</style>
