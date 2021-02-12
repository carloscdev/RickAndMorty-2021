<template>
  <div class="characterId">
    <SubHeader :title="character.name" :button="false" />
    <div class="characterId__detail">
      <div class="characterId__container container">
        <Character :character="character" :height="true" />
      </div>
    </div>
  </div>
</template>

<script>
import Character from "~/components/Character";
export default {
  components: {
    Character
  },
  data() {
    return {
      idC: "",
      character: {}
    };
  },
  async asyncData({ params, $axios }) {
    const res = await $axios.$get(`character/${params.id}`);
    return {
      character: res,
      idC: params.id
    };
  }
};
</script>

<style lang="scss">
.characterId {
  &__detail {
    background-color: var(--color-dark);
    padding: 5rem 0;
  }
}
</style>
