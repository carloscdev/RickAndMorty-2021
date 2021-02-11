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
          SEARCH
        </button>
      </div>
      <div class="header__container--image">
        <img class="floatUp" src="../assets/images/rick.png" alt="Rick" />
        <img class="floatDown" src="../assets/images/morty.png" alt="Rick" />
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.header {
  height: 100vh;
  max-height: 800px;
  /* background-image: url("https://api.thumbr.it/whitenoise-361x370.png?background=f7f7f7ff&noise=171717&density=5&opacity=15"); */
  display: flex;
  align-items: center;
  &__container {
    color: var(--color-dark);
    display: grid;
    grid-template-columns: 0.8fr 1fr;
    &--image {
      position: relative;
      img:first-child {
        position: absolute;
        top: 0;
        left: 0;
      }
      img:last-child {
        position: absolute;
        bottom: 0;
        right: 0;
      }
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
  @media (max-width: 560px) {
    &__container {
      grid-template-columns: 1fr;
      text-align: center;
      &--image {
        position: relative;
        img:first-child {
          top: 2rem;
          left: 0;
          width: 130px;
        }
        img:last-child {
          top: 2rem;
          right: 0;
          width: 130px;
        }
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
