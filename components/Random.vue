<template>
  <div class="random">
    <div class="random__container container">
      <h2>
        {{ title }}
      </h2>

      <div class="random__container--characters">
        <div v-for="character in characters" :key="character.id">
          <Character :character="character" />
        </div>
      </div>
      <Loading v-if="loading" />
      <button class="btn" v-if="button" @click="loadMore">
        Load More
      </button>
    </div>
  </div>
</template>

<script>
import Character from "./Character";
import Loading from "./Loading";
export default {
  props: {
    characters: { type: Array, default: [] },
    title: { type: String },
    button: { type: Boolean, default: false },
    loading: { type: Boolean, default: false }
  },
  components: {
    Character,
    Loading
  },
  methods: {
    loadMore() {
      this.$emit("load");
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
      grid-gap: 1.5rem;
      @media (max-width: 980px) {
        grid-template-columns: 1fr;
      }
    }
  }
  button {
    margin-top: 3rem;
  }
}
</style>
