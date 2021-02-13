<template>
  <div class="characters">
    <SubHeader title="Characters" />
    <Random
      title="Characters"
      :characters="characters"
      :button="button"
      @load="loadMore"
      :loading="loading"
    />
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
      charactersRandom: [],
      page: 2,
      totalPages: "",
      loading: false,
      button: true
    };
  },
  mounted() {
    this.charactersAll();
  },
  methods: {
    async charactersAll() {
      this.loading = true;
      const res = await this.$axios.$get(`/character`);
      this.characters = res.results;
      this.loading = false;
      this.totalPages = res.info.pages;
    },
    async loadMore() {
      if (this.page === this.totalPages) {
        this.button = false;
      } else {
        this.loading = true;
        await this.$axios
          .$get(`/character/?page=${this.page}`)
          .then(res => {
            this.page++;
            const characters2 = res.results;
            this.characters = this.characters.concat(characters2);
            this.loading = false;
            if (this.page === this.totalPages) {
              this.button = false;
            }
          })
          .catch(error => {
            this.loading = false;
            console.log(error);
          });
      }
    }
  }
};
</script>

<style></style>
