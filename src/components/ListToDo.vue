<script setup lang="js">

import Modal from './Modal.vue';
import ToDoModal from './ToDoModal.vue';

const props = defineProps({
  modalToDo: {
    type: Boolean,
    required: true,
  },
  cModalToDo: {
    type: Function,
    required: true,
  },
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
  },
  openModalToDo: {
    type: Function,
    required: true,
  },
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

</script>

<template lang="html">
    <div class="text-white" >
        <div>
            <h1 class="w-full bg-blue-500 rounded-md px-2 text-3xl">To Do List</h1>
            <div class="mt-2 text-center">
              
            </div>
        </div>

        <div class="flex flex-wrap item-center justify-center border-2 m-4 border-gray-400 rounded-2xl">
            <button @click="openModalToDo(item)" v-for="item in toDoList" :key="item.id" class="bg-orange-500 w-44 h-44 m-6 p-6 rounded-xl flex item-center justify-center">
                <p class="text-lg p-2 m-auto">{{ item.toDo }}</p>
            </button>
        </div>
    </div>

    <Modal :show="modalToDo" @close="cModalToDo" :maxWidth="'sm'">
        <ToDoModal :idModalToDo="idModalToDo" :deleteToDoList="deleteToDoList" :editToDoList="editToDoList"/>
    </Modal>


</template>
  
<style lang="css">

</style>
