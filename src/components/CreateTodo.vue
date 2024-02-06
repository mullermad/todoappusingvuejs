<template>
    <form @submit.prevent="handleSubmit">
        <label class="font-bold mr-2">What's Up</label>
        <input type="text" v-model="name" placeholder="Name Here" class="border border-gray-300 rounded px-3 py-2 mt-1 outline-none">
   <h1 class="m-2">CREATE A TODO</h1>
   
   <label class="font-bold mr-2">Whats on your todo list?</label>
        <input type="text" placeholder="e.g make a video" v-model="todo" class="border border-gray-300 rounded px-3 py-2 mt-1 w-full outline-none">
    <h1 class="font-bold">pick a catagory</h1>
    
 <div class="flex items-center">
  <div class="inline-flex items-center">
    <input type="radio" id="radioButton1" v-model="radiobutton" value="buisness"/>
    <p class="ml-2 text-gray-700">Business</p>
  </div>

  <div class="inline-flex items-center ml-4">
    <input type="radio" id="radioButton2" v-model="radiobutton" value="personal" />
<p class="ml-2 text-gray-700">Personal</p>
  </div>
  
</div>
<button class="bg-purple-500 w-full mt-2 p-1">Add todo</button>
   
    </form>
</template>



<script setup>
import { ref } from 'vue';

const name=ref('');
const todo=ref('');
const radiobutton=ref(false)
const emit=defineEmits(['formDataSubmitted'])


const handleSubmit=()=>{
if(!name.value || !todo.value ||!radiobutton.value){
  return;
}
  const formData=[
    {
      name:name.value,
      todo:todo.value,
      catagory:radiobutton.value
    }
  ]
emit("formDataSubmitted",formData)

  console.log('working form data in Createtodolist component',formData);
 name.value='',
 todo.value='',
 radiobutton.value=false
 
}


</script>
