<template>
  <div class="navbar">
    <nav class="navbar__container container">
      <img src="../assets/images/logo.png" alt="Logo" />
      <ul>
        <li><nuxt-link to="/">Home</nuxt-link></li>
        <li><nuxt-link to="/characters">Characters</nuxt-link></li>
        <li><nuxt-link to="/episodes">Episodes</nuxt-link></li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.navbar {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 0;
    ul {
      display: flex;
      padding: 0;
      li {
        margin-left: 1.5rem;
      }
    }
  }
  img {
    width: 60px;
  }
  .nuxt-link-exact-active {
    background-color: var(--color-dark);
    padding: 1rem;
    color: var(--color-white);
    border-radius: 10px;
  }
}
</style>
