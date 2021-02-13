<template>
  <div class="subHeader">
    <div class="subHeader__container container">
      <h1>{{ title }}</h1>
      <input
        v-model="searchText"
        @keyup="SearchCharacter(searchText)"
        type="text"
        placeholder="Search by name"
      />
      <br />
      <span class="color-main">{{ message }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: { type: String },
    button: { type: Boolean, default: true },
    message: { type: String, default: "" }
  },
  data() {
    return {
      searchText: ""
    };
  },
  methods: {
    async SearchCharacter(val) {
      if (this.searchText.length > 2) {
        await this.$emit("searchC", val);
      }
    }
  }
};
</script>

<style lang="scss">
.subHeader {
  height: 400px;
  max-height: 600px;
  background-image: url("../assets/images/silueta.png");
  background-repeat: no-repeat;
  background-size: 17%;
  background-position: bottom center;
  display: flex;
  align-items: center;
}
</style>
