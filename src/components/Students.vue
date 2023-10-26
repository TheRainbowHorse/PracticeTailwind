<script setup>
import { onMounted, ref } from 'vue'
import axios from 'axios'

const students = ref([]);

onMounted(() => {
  axios.get('http://34.82.81.113:3000/students')
  .then((response) => {
    students.value = response.data;
  })
});
</script>

<template>
  <table class="w-full border-3 text-left">
    <thead class="border-b bg-red-300">
      <tr>
        <th>Name</th>
        <th>Group</th>
      </tr>
    </thead>
    <tbody class="bg-yellow-200">
      <tr class="border-2" v-for="st in students" v-bind:key="st._id">
        <td class="px-6 py-4">{{st.name}}</td>
        <td>{{st.group}}</td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
</style>
