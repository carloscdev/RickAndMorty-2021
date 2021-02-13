<template>
  <div>
    <Header />
    <Random title="Random" :characters="characters" :loading="loading" />
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
      charactersRandom: [],
      loading: false
    };
  },
  mounted() {
    this.charactersAll();
  },
  methods: {
    async charactersAll() {
      this.loading = true;
      for (let i = 0; i < 6; i++) {
        let randomN = Math.floor(Math.random() * (670 - 1 + 1) + 1);
        this.charactersRandom.push(randomN + i);
      }
      const res = await this.$axios.$get(
        `/character/${this.charactersRandom.join()}`
      );
      this.characters = res;
      this.loading = false;
    }
  }
};
</script>
