<template>
  <div class="characters">
    <div class="characters__container">
      <div
        class="characters__image"
        :style="`background-image: url('${character.image}')`"
      ></div>
      <div class="characters__description">
        <div>
          <h3>{{ character.name }}</h3>
          <div class="statusGender">
            <span class="status" :class="statusColor"></span>
            <span>{{ character.status }} - {{ character.gender }}</span>
          </div>
          <br />
          <span class="gray"> Last known location: <br /> </span>
          <span>
            {{ character.location.name }}
          </span>
          <br />
          <span class="gray">
            Origin:
            <br />
          </span>
          <span>{{ character.origin.name }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    character: { type: Object }
  },
  computed: {
    statusColor() {
      return this.character.status === "Dead"
        ? "color-red"
        : this.character.status === "Alive"
        ? "color-green"
        : "color-white";
    }
  }
};
</script>

<style lang="scss">
.characters {
  &__container {
    height: 210px;
    width: 100%;
    display: grid;
    grid-template-columns: 0.7fr 1fr;
    background-color: var(--color-gray-dark);
    border-radius: 10px;
    overflow: hidden;
    &:hover {
      box-shadow: 0px 0px 7px 0px rgba(0, 0, 0, 0.48);
    }
    @media (max-width: 560px) {
      height: 420px;
      grid-template-columns: 1fr;
    }
  }
  &__image {
    background-position: top center;
    background-size: cover;
    height: 210px;
    background-repeat: no-repeat;
  }
  &__description {
    color: var(--color-white);
    padding: 1rem;
    div:first-child {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
    .status {
      width: 10px;
      height: 10px;
      display: block;
      border-radius: 50%;
      margin-right: 0.5rem;
    }
    .color-red {
      background-color: red;
    }
    .color-green {
      background-color: green;
    }
    .color-white {
      background-color: white;
    }
    .gray {
      opacity: 0.5;
    }
    .statusGender {
      display: flex;
      align-items: center;
    }
  }
}
</style>
