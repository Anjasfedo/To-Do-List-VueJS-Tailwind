<script setup>
import Title from './components/Title.vue';
import ListToDo from './components/ListToDo.vue'

import Modal from './components/Modal.vue';

import ModalAdd from './components/ModalAdd.vue'

import { ref } from 'vue';

// data to do

const modalToDo = ref(false);

const cModalToDo = () => {
  modalToDo.value = false
}

const idModalToDo = ref(null)

const openModalToDo = (val) => {
    idModalToDo.value = val;
    modalToDo.value = true
}

// button

const modalAdd = ref(false);

const cModalAdd = () => {
  modalAdd.value = false
}

// to do

const toDoList = ref([{id: 1, toDo: 'makan', description: 'makan sj'}])

const addToDoList = (val) => {
  toDoList.value.push(val)
  cModalAdd();
}

const deleteToDoList = (id) => {
  const index = toDoList.value.findIndex(item => item.id === id);
  if (index !== -1) {
    toDoList.value.splice(index, 1);
  }
  cModalToDo();
}

const editToDoList = () => {
  const index = toDoList.value.findIndex(item => item.id === idModalToDo.id);
  if (index !== -1) {
    // Mengganti isi name dan description
    toDoList.value[index].toDo = idModalToDo.toDo;
    toDoList.value[index].description = idModalToDo.description;
  }
  cModalToDo();
  idModalToDo.value = null; // Setelah mengedit, nuliskan kembali idModalToDo.
}

</script>

<template>
  <div class="w-5/6 bg-blue-300 mx-auto rounded-2xl m-8 font-sans flex items-center justify-center">
    <div class="p-8 bg-gray-300 w-11/12 ">
      <Title msg="To Do List" class="mb-10"/>
      <button class="w-44 h-10 bg-green-500 rounded-lg text-white mb-8"  @click="modalAdd = true">Add To Do</button>
      <ListToDo :modalToDo="modalToDo" :cModalToDo="cModalToDo" :modalAdd="modalAdd" :cModalAdd="cModalAdd" :toDoList="toDoList" :addToDoList="addToDoList" :openModalToDo="openModalToDo" :idModalToDo="idModalToDo" :deleteToDoList="deleteToDoList" :editToDoList="editToDoList"/>
    </div>
  </div>

  <Modal :show="modalAdd" @close="cModalAdd" :maxWidth="'sm'">
    <ModalAdd :toDoList="toDoList" :addToDoList="addToDoList"   :modalAdd="modalAdd" :cModalAdd="cModalAdd" />
</Modal>
</template>