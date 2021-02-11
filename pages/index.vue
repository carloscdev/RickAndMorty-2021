<template>
  <div>
    <Navbar />
    <Header />
    <Random />
  </div>
</template>

<script>
import Header from "~/components/Header";
import Navbar from "~/components/Navbar";
import Random from "~/components/Random";
export default {
  components: {
    Header,
    Navbar,
    Random
  }
};
</script>

<style lang="scss">
:root {
  --color-white: #ffffff;
  --color-gray-dark: #3c3e44;
  --color-dark: #24282f;
  --color-main: #ff9800;
  /* --color-main: #02b1c8; */
}
h1 {
  font-size: 5.5rem;
}
h2 {
  font-size: 3rem;
  position: relative;
  &:before {
    content: "";
    background-color: var(--color-white);
    width: 40px;
    height: 10px;
    border-radius: 10px;
    position: absolute;
    bottom: -10px;
    left: 0;
  }
}
h3 {
  font-size: 1.5rem;
  font-weight: bold;
}
@media (max-width: 560px) {
  h1 {
    font-size: 4rem;
  }
}
li {
  list-style: none;
}
a {
  font-size: 1rem;
  text-decoration: none;
  color: inherit;
  box-sizing: border-box;
}

p {
  font-size: 1.1rem;
}
.floatUp {
  animation: floatUp 4s ease-in-out infinite;
}
.floatDown {
  animation: floatDown 4s ease-in-out infinite;
}
@keyframes floatUp {
  0% {
    transform: translatey(0px);
  }
  50% {
    transform: translatey(-20px);
  }
  100% {
    transform: translatey(0px);
  }
}
@keyframes floatDown {
  0% {
    transform: translatey(0px);
  }
  50% {
    transform: translatey(+20px);
  }
  100% {
    transform: translatey(0px);
  }
}
.btn {
  background-color: var(--color-main);
  padding: 1rem 4rem;
  color: var(--color-white);
  border-radius: 10px;
  border: 2px solid var(--color-dark);
  font-size: 1.1rem;
  cursor: pointer;
  &:hover {
    box-shadow: 0px 0px 7px 0px rgba(0, 0, 0, 0.48);
  }
}
.container {
  width: 80%;
  margin: 0 auto;
}
input {
  background-color: white;
  padding: 0.5rem 1rem;
  border-radius: 10px;
  border: 1px solid var(--color-gray-dark);
  width: 60%;
  color: var(--color-gray-dark);
}
input:focus {
  outline: none;
}
</style>
