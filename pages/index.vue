<template>
  <Login @onLoginClick="onLoginClick" />
</template>
<script setup lang="ts">
import funql from "@/libs/funql";

const name = ref("Foo");
const { onLoginClick } = useCanLogin();
const { public: publicEnvs } = useRuntimeConfig();
let { savoieBackendUrl } = publicEnvs;

const fql = funql(savoieBackendUrl);
console.log({ fql });

let todos = ref();

onMounted(async () => {
  if (process.client) {
    todos.value = await fql(
      "crud",
      {
        action: "get_all",
      },
      {
        namespace: "todo",
      }
    );
  }
});
</script>
