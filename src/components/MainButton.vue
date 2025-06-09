<script setup>
const name = "Garin Caesar";

const showName = () => console.log(name);
</script>

<template>
  <h1>{{ name }}</h1>
  <button @click="showName" className="bg-red-300">Show Name</button>
</template>

<style scoped></style>
