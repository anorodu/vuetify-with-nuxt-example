<template>
  <div>
    <NuxtLayout :name="layout">
      <NuxtPage/>
    </NuxtLayout>
  </div>
</template>
<script setup>
const layout = "app-layout"
</script>