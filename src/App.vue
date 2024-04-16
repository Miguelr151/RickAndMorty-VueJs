<template>
  <div>
    <Navbars :brand="'Rick and Morty'" />
    <div class="container mt-5">
      <Paginacion :prev="info?.prev" :next="info?.next" @onPrevious="onPrevious" @onNext="onNext" />
      <Characters :characters="characters" />
      <Paginacion />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from "vue";
import Navbars from "src/components/Navbars.vue";
import Characters from "src/components/Characters.vue";
import Paginacion from "src/components/Paginacion.vue";

interface Character {
  name: string;
  // Otras propiedades
}

export default defineComponent({
  name: "App",
  components: {
    Navbars,
    Characters,
    Paginacion,
  },
  setup() {
    const characters = ref<Character[]>([]);
    const info = ref<any>({});
    const initialUrl = "https://rickandmortyapi.com/api/character";

    const fetchCharacter = (url: string) => {
      fetch(url)
        .then((response) => response.json())
        .then((data) => {
          characters.value = data.results;
          info.value = data.info;
        })
        .catch((error) => console.error(error));
    };

    const onPrevious = () => {
      fetchCharacter(info.value.prev);
    };

    const onNext = () => {
      fetchCharacter(info.value.next);
    };

    onMounted(() => {
      fetchCharacter(initialUrl);
    });

    return {
      characters,
      info,
      onPrevious,
      onNext,
    };
  },
});
</script>
