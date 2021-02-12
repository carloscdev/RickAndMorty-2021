<template>
  <div class="random">
    <div class="random__container container">
      <h2>
        {{ title }}
      </h2>
      <Loading v-if="characters.length < 1" />
      <div v-else class="random__container--characters">
        <div v-for="character in characters" :key="character.id">
          <Character :character="character" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Character from "./Character";
import Loading from "./Loading";
export default {
  props: {
    characters: { type: Array, default: [] },
    title: { type: String }
  },
  components: {
    Character,
    Loading
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
      @media (max-width: 980px) {
        grid-template-columns: 1fr;
      }
      @media (max-width: 620px) {
        grid-template-columns: 1fr;
      }
    }
  }
}
</style>
