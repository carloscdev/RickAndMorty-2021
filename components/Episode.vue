<template>
  <div class="episode">
    <div class="episode__container">
      <h3>Episode: {{ episodeDetail.episode }}</h3>
      <br />
      <span class="gray"> Name: <br /> </span>
      <span>
        {{ episodeDetail.name }}
      </span>
      <br />
      <br />
      <span class="gray">
        Air date:
        <br />
      </span>
      <span>{{ episodeDetail.air_date }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    episode: { type: String, default: {} }
  },
  data() {
    return {
      episodeId: "",
      episodeDetail: {}
    };
  },
  mounted() {
    this.getEpisode();
  },
  methods: {
    async getEpisode() {
      try {
        this.episodeId = this.episode.slice(32);
        const res = await this.$axios.$get(`${this.episodeId}`);
        this.episodeDetail = res;
      } catch (error) {
        console.log("episode", error);
      }
    }
  }
};
</script>

<style lang="scss">
.episode {
  height: 200px;
  width: 100%;
  background-color: var(--color-gray-dark);
  border-radius: 10px;
  display: flex;
  align-items: center;
  border-bottom: 5px solid #1c1c1f;
  &:hover {
    box-shadow: 0px 0px 7px 0px rgba(0, 0, 0, 0.48);
  }
  &__container {
    width: 100%;
    color: var(--color-white);
    padding: 0.5rem 1rem;
  }
}
</style>
