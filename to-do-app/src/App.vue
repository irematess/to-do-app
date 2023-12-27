<script setup>
import { ref } from 'vue';

const todos = ref([
    {
     todo:"Spor yap.",
     isDone:false   
    },
    {
     todo:"Ders çalış.",
     isDone:false   
    },
    {
     todo:"Kitap oku.",
     isDone:false   
    },
    {
     todo:"Yemek yap.",
     isDone:false   
    },
    {
     todo:"Temizlik yap.",
     isDone:false   
    },
    {
     todo:"Kod yaz.",
     isDone:false   
    },
    {
     todo:"Dizi izle.",
     isDone:false   
    },
]);

const handleClick = (tdo) => {
   console.log(tdo)
    todos.value = todos.value.map(t =>{
        if(t.todo == tdo.todo){
            t.isDone = !t.isDone
        }
        return t
 })
 console.log(tdo)

 
}

const newTodo = ref('');
const handleNewCreateTodo = () => {
  todos.value.push({
    todo:newTodo.value,
    isDone:false
  })
  newTodo.value = ('');
}

</script>

<template>
  <div class="container">
    <div class="to-do-list">
        <h2>to do list</h2>
        <ul>
            <li :class="{completed : tdo.isDone}" v-for="tdo in todos" ><input type="checkbox" @click="handleClick(tdo)">{{ tdo.todo }}</li>
            <input type="text" class="newTodo" v-model="newTodo" @keydown.enter="handleNewCreateTodo">
        </ul>
    </div>
  </div>
</template>


