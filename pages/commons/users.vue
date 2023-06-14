<template>
  <div>
    <v-card child-flex>
      <v-table :hover="true">
        <thead>
        <tr>
          <th class="text-left">Name</th>
          <th class="text-left">User Name</th>
          <th class="text-left">Email</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="user in data.data">
          <td>{{ user.firstname }} {{user.lastname}}</td>
          <td>{{ user.username }}</td>
          <td>{{ user.email }}</td>
        </tr>
        </tbody>
      </v-table>
    </v-card>
  </div>
</template>
<script setup>
const {data} = await useFetch('https://fakerapi.it/api/v1/users?_quantity=10', {
  method: 'GET'
})
</script>