<template>
  <div class="characters">
    <SubHeader title="Characters" />
    <Random title="Characters" :characters="characters" />
  </div>
</template>

<script>
import SubHeader from "~/components/SubHeader";
export default {
  components: {
    SubHeader
  },
  data() {
    return {
      characters: [],
      charactersRandom: []
    };
  },
  mounted() {
    this.charactersAll();
  },
  methods: {
    async charactersAll() {
      const res = await this.$axios.$get(`/character`);
      this.characters = res.results;
    }
  }
};
</script>

<style></style>
