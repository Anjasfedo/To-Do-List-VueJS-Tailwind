<script setup lang="js">

import Modal from './Modal.vue';
import ToDoModal from './ToDoModal.vue';

import ModalAdd from './ModalAdd.vue'

defineProps({
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
  }
})

</script>

<template lang="html">
    <div class="text-white" >
        <div>
            <h1 class="w-full bg-blue-500 rounded-md px-2 text-3xl">To Do List</h1>
            <div class="mt-2 text-center">
              <button class="w-44 h-10 bg-green-500 rounded-lg text-white"  @click="modalAdd = true">Add To Do</button>
            </div>
        </div>

        <div class="flex flex-wrap item-center justify-center border-2 m-4 border-gray-400 rounded-2xl">
            <button class="w-44 h-44 bg-green-400 m-6 p-6 rounded-xl flex item-center justify-center" @click="modalToDo = true">
                <p class="text-lg p-2 m-auto">Makan</p>
            </button>
        </div>
    </div>

    <Modal :show="modalToDo" @close="modalToDo = false">
        <ToDoModal/>
    </Modal>

    <Modal :show="modalAdd" @close="modalAdd = false">
      <ModalAdd/>
  </Modal>
</template>
  
<style lang="css">

</style>
