<template>
  <Login @onLoginClick="onLoginClick" />
</template>
<script setup lang="ts">
const name = ref('Foo');
const { onLoginClick } = useCanLogin();
const backendURL = 'https://b3adf14e3b3e23b7e291f8b3426938cd.serveo.net/';
</script>
