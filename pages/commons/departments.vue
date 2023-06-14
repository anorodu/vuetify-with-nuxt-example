<template>
  <div>
    <v-table>
      <thead>
      <tr>
        <th class="text-left">Fullname</th>
        <th class="text-left">Email</th>
      </tr>
      </thead>
      <tbody>
      <tr></tr>
      </tbody>
    </v-table>
  </div>
</template>
<script setup lang="ts">
const {data} = await useFetch('/users?_quantity=10', {
  method: 'GET'
})
</script>