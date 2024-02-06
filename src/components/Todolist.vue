<template>
  <h1>Todo List </h1>
  <ul>
 <li v-for="todoList in todoLists" :key="todoList.id" class="flex items-center justify-between py-2 bg-gray-200 border m-2 border-gray-300 rounded-lg">
  <span class="px-4">{{ todoList.name }}</span>
  <span class="px-4">{{ todoList.todo }}</span>
  <span class="px-4">{{ todoList.catagory }}</span>
</li>
</ul>
</template>

<script setup>

const props=defineProps({
  todoLists:{
    type:Array,
    required:true
  }
  
})



</script>
