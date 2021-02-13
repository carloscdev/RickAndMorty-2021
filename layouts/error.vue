<template>
  <div class="error">
    <img src="../assets/images/404.png" alt="Error 404" />
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.error {
  margin-top: 6rem;
  height: 100vh;
  min-height: 600px;
  background-color: var(--color-dark);
  display: flex;
  align-items: center;
  justify-content: center;
  img {
    width: 300px;
  }
}
</style>
