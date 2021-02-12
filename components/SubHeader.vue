<template>
  <div class="subHeader">
    <div class="subHeader__container container">
      <h1>{{ title }}</h1>
      <button v-if="button" class="btn">
        SEARCH
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: { type: String },
    button: { type: Boolean, default: true }
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
