<template>
    <nav class="my-5">
      <ul class="pagination justify-content-center">
        <li v-if="prev" class="page-item">
          <button class="page-link" @click="handlePrevious">Previous</button>
        </li>
        <li v-if="next" class="page-item">
          <button class="page-link" @click="handleNext">Next</button>
        </li>
      </ul>
    </nav>
  </template>
  
  <script lang="ts">
  import { defineComponent, type PropType } from "vue";
  
  export default defineComponent({
    name: "Paginacion",
    props: {
      prev: {
        type: String as PropType<string | null>,
        default: null,
      },
      next: {
        type: String as PropType<string | null>,
        default: null,
      },
      onPrevious: {
        type: Function as PropType<() => void>,
        required: true,
      },
      onNext: {
        type: Function as PropType<() => void>,
        required: true,
      },
    },
    methods: {
      handlePrevious() {
        this.onPrevious();
      },
      handleNext() {
        this.onNext();
      },
    },
  });
  </script>
  