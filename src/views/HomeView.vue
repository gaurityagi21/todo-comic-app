<template>
  <div class="container mt-5">
    <h2>Welcome!</h2>
    <ul class="nav nav-tabs mt-4">
      <li class="nav-item">
        <button class="nav-link" :class="{ active: currentTab === 'todo' }" @click="currentTab = 'todo'">To-Do List</button>
      </li>
      <li class="nav-item">
        <button class="nav-link" :class="{ active: currentTab === 'comic' }" @click="currentTab = 'comic'">Random Comic</button>
      </li>
    </ul>

    <div class="mt-4">
      <TodoList v-if="currentTab === 'todo'" />
      <RandomComic v-if="currentTab === 'comic'" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import TodoList from '../components/TodoList.vue'
import RandomComic from '../components/RandomComic.vue'

const currentTab = ref('todo')
</script>
