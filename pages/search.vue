<template>
  <div class="search">
    <SearchHeader title="Search ..." @searchC="Search" :message="message" />
    <Random :title="title" :characters="characters" />
  </div>
</template>

<script>
import SearchHeader from "~/components/SearchHeader";
export default {
  components: {
    SearchHeader
  },
  data() {
    return {
      characters: [],
      charactersRandom: [],
      message: "",
      title: "Characters"
    };
  },
  mounted() {
    this.charactersAll();
  },
  methods: {
    async charactersAll() {
      const res = await this.$axios.$get(`/character`);
      this.characters = res.results;
    },
    async Search(val) {
      await this.$axios
        .$get(`/character/?name=${val}`)
        .then(res => {
          this.characters = res.results;
          this.message = `${this.characters.length} matches`;
          this.title = `Character: ${val}`;
        })
        .catch(error => {
          this.message = "Not found";
          console.log(error);
        });
    }
  }
};
</script>

<style></style>
