<template>
    <div class="row">
      <div v-for="(character, index) in characters" :key="index" class="col mb-4">
        <div class="card" style="min-width: 200px;">
          <img :src="character.image" alt="Imagen" />
          <h5 class="card-title">{{ character.name }}</h5>
          <hr />
          <p>Species: {{ character.species }}</p>
          <p>Location: {{ character.location.name }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, type PropType } from "vue";
  
  interface Character {
    name: string;
    image: string;
    species: string;
    location: {
      name: string;
    };
  }
  
  export default defineComponent({
    name: "Characters",
    props: {
      characters: {
        type: Array as PropType<Character[]>,
        default: () => [],
      },
    },
  });
  </script>
  