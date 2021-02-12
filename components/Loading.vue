<template>
  <div class="loading">
    <div>
      <img src="../assets/images/load.png" alt="Loading" />
    </div>
    <h3>Loading ...</h3>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.loading {
  padding-top: 5rem;
  text-align: center;
  width: 100%;
  color: var(--color-white);
  img {
    width: 100px;
    animation: 3s rotate linear infinite;
  }
}
@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>
