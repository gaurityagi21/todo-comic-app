<template>
  <div>
    <h3 class="mb-3">To-Do List</h3>
    <div class="mb-2 d-flex">
      <input v-model="newItem" class="form-control me-2" placeholder="Add a new to-do" />
      <button class="btn btn-success" @click="addItem">Add</button>
    </div>
    <table class="table table-bordered mt-3">
      <thead>
        <tr><th>#</th><th>Task</th><th>Action</th></tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in items" :key="index">
          <td>{{ index + 1 }}</td>
          <td>{{ item }}</td>
          <td>
            <button class="btn btn-danger btn-sm" @click="removeItem(index)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const newItem = ref('')
const items = ref([])

const addItem = () => {
  if (newItem.value.trim()) {
    items.value.push(newItem.value.trim())
    newItem.value = ''
  }
}

const removeItem = (index) => {
  items.value.splice(index, 1)
}
</script>
