<template>
  <div class="header">
    <div class="header__container container">
      <div class="header__container--texto">
        <h1>
          Rick &amp; Morty API
        </h1>
        <div class="header-description">
          <div></div>
          <p>Find your favorites rick and morty characters</p>
        </div>
        <button class="btn">
          <nuxt-link to="/search">SEARCH</nuxt-link>
        </button>
      </div>
      <div class="header__container--image">
        <img
          class="floatUp"
          :src="require(`../assets/images/${image}.png`)"
          alt="Rick"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      image: 1
    };
  },
  mounted() {
    this.image = Math.floor(Math.random() * (3 - 1 + 1) + 1);
  }
};
</script>

<style lang="scss">
.header {
  height: 100vh;
  max-height: 800px;
  background-image: url("../assets/images/silueta.png");
  background-repeat: no-repeat;
  background-size: 17%;
  background-position: bottom center;
  display: flex;
  align-items: center;
  &__container {
    color: var(--color-dark);
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    &--image {
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }
  &-description {
    display: flex;
    align-items: center;
    color: var(--color-dark);
    margin: 1.5rem 0;
    div {
      height: 2rem;
      width: 0.2rem;
      background-color: var(--color-dark);
      margin-right: 0.5rem;
    }
  }
  @media (max-width: 620px) {
    background-size: 35%;
    &__container {
      grid-template-columns: 1fr;
      text-align: center;
      &--image {
        display: none;
      }
    }
    &-description {
      display: block;
      p {
        text-align: center;
      }
      div {
        display: none;
      }
    }
  }
}
</style>
