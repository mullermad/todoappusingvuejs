

<template>
  <div class="flex mt-4 justify-center flex-col items-center">
    <CreateTodo @formDataSubmitted="handleTodo"/>
    <div class="block mt-4">
        <Todolist :todoLists="todoLists"/>
    </div>
</div>
</template>

<script setup>
import { ref } from 'vue';
import Todolist from './components/Todolist.vue'
import CreateTodo from './components/CreateTodo.vue';

const todoLists=ref([
  {id:1,name:"muller",todo:'make a video',catagory:'personal'},
  
]);



function generateUniqueId() {
  const timestamp = new Date().getTime(); // Get current timestamp
  const randomNum = Math.random(); // Generate a random number
  const uniqueId = `${timestamp}-${randomNum}`; // Combine timestamp and random number
  
  return uniqueId;
};

const handleTodo=(todoData)=>{
  console.log("todo data inside handletodo is  :",todoData);
  todoLists.value.push(...todoData,
  {id:generateUniqueId(),
    name:todoData.name,
    todo:todoData.todo,
    catagory:todoData.catagory
  })
  
}

console.log("in app component after push",todoLists);
</script>