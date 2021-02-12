<template>
  <div>
    <Header />
    <Random title="Characters" :characters="characters" />
  </div>
</template>

<script>
import Header from "~/components/Header";
import Random from "~/components/Random";
export default {
  components: {
    Header,
    Random
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
      for (let i = 0; i < 6; i++) {
        let randomN = Math.floor(Math.random() * (670 - 1 + 1) + 1);
        this.charactersRandom.push(randomN + i);
      }
      /* console.log(this.charactersRandom.join()); */
      const res = await this.$axios.$get(
        `/character/${this.charactersRandom.join()}`
      );
      this.characters = res;
    }
  }
};
</script>
