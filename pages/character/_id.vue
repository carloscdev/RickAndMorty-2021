<template>
  <div class="characterId">
    <SubHeader :title="character.name" :button="false" />
    <div class="characterId__detail">
      <div class="characterId__container container">
        <Character :character="character" :height="true" :detail="true" />
      </div>
      <div class="characterId__episode container">
        <h2>Episodes</h2>
        <div>
          <div v-for="(e, index) in character.episode" :key="index">
            <Episode :episode="e" />
          </div>
        </div>
      </div>
      <Loading v-if="loading" />
    </div>
  </div>
</template>

<script>
import Character from "~/components/Character";
import Episode from "~/components/Episode";
export default {
  components: {
    Character,
    Episode
  },
  data() {
    return {
      idC: "",
      character: {
        name: "",
        created: "",
        epise: "",
        gender: "",
        image: "",
        location: { name: "" },
        origin: { name: "" },
        species: "",
        status: ""
      },
      loading: true
    };
  },
  /* async asyncData({ params, $axios }) {
    const res = await $axios.$get(`character/${params.id}`);
    return {
      character: res,
      idC: params.id,
      loading: false
    };
  } */
  created() {
    this.characterDetail();
  },
  methods: {
    async characterDetail() {
      this.loading = true;
      try {
        const res = await this.$axios.$get(
          `character/${this.$route.params.id}`
        );
        this.character = res;
        this.idC = this.$route.params.id;
        this.loading = false;
      } catch (error) {
        this.$router.push("/sorry");
        this.loading = false;
      }
    }
  }
};
</script>

<style lang="scss">
.characterId {
  &__detail {
    background-color: var(--color-dark);
    padding: 5rem 0;
  }
  &__episode {
    & > div {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      grid-gap: 1rem;
      @media (max-width: 980px) {
        grid-template-columns: 1fr;
      }
    }
    h2 {
      color: var(--color-white);
      margin: 3rem 0;
    }
  }
}
</style>
