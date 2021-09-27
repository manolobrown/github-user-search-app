<script setup>
defineProps({
  txt: String,
});
</script>

<template>
  <header>
    <h1>{{ txt }}</h1>
    <button class="btn btn--theme-toggle">
      Dark <img src="../assets/icon-moon.svg" alt="" />
    </button>
  </header>
</template>

<style scoped lang="scss">
@use "sass:math";

// Source: https://css-tricks.com/snippets/sass/px-to-em-functions/
@function rem($pixels, $context: 16) {
  @return (math.div($pixels, $context)) * 1rem;
}
header {
  display: flex;
  justify-content: space-between;
  margin-block-end: rem(35);

  h1 {
    margin: 0;
  }

  button {
    width: 100%;
    max-width: rem(78);
    justify-content: space-between;
    text-transform: uppercase;
    color: var(--blue-gray);
    letter-spacing: rem(2.5);
    padding: 0;

    img {
      margin-left: rem(15);
    }
  }
}
</style>
