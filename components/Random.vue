<template>
  <div class="random">
    <div class="random__container container">
      <h2>
        Characters
      </h2>
      <div class="random__container--characters">
        <div v-for="character in characters" :key="character.id">
          <Characters :character="character" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Characters from "./Characters";
export default {
  components: {
    Characters
  },
  data() {
    return {
      characters: [],
      pages: "",
      charactersRandom: []
    };
  },
  mounted() {
    this.charactersAll();
  },
  methods: {
    charactersAll() {
      for (let i = 0; i < 6; i++) {
        let randomN = Math.floor(Math.random() * (670 - 1 + 1) + 1);

        this.charactersRandom.push(randomN + i);
      }
      console.log(this.charactersRandom.join());
      return axios
        .get(
          `https://rickandmortyapi.com/api/character/${this.charactersRandom.join()}`
        )
        .then(res => {
          this.characters = res.data;
        });
    }
  }
};
</script>

<style lang="scss">
.random {
  background-color: var(--color-dark);
  &__container {
    padding: 5rem 0;
    h2 {
      color: var(--color-white);
    }
    &--characters {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      grid-gap: 3rem;
      @media (max-width: 560px) {
        grid-template-columns: 1fr;
      }
    }
  }
}
</style>
