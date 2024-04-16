<template>
    <nav class="navbar navbar-dark bg-dark">
      <div class="container">
        <a class="navbar-brand text-uppercase" href="/">{{ brand }}</a>
      </div>
    </nav>
  </template>
  
  <script lang="ts">
  import { defineComponent, type PropType } from "vue";
  
  export default defineComponent({
    name: "Navbars",
    props: {
      brand: {
        type: String as PropType<string>,
        required: true,
      },
    },
  });
  </script>
  