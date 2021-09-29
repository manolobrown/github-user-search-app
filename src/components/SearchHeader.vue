<script setup>
import { ref } from "vue";

defineProps({
  txt: String,
});
</script>

<template>
  <div class="search">
    <img src="../assets/icon-search.svg" alt="" />
    <input type="text" placeholder="Search GitHub username&hellip;" />
    <button class="btn btn--blue">Search</button>
  </div>
</template>

<style scoped lang="scss">
@use "../assets/scss/util" as *;

.search {
  padding: rem(5) rem(5) rem(5) rem(15);
  display: flex;
  align-items: center;
  justify-content: space-between;

  img {
    width: rem(20);
    height: rem(20);
  }
}
.btn--blue {
  font-size: rem(14);
  padding: rem(12);
  border-radius: rem(10);
}

input {
  border: 0;
  background-color: transparent;
  font-size: rem(13);
  flex-basis: 0;
  flex-grow: 1;
  margin: 0 rem(8);
  padding: 0;
  text-overflow: ellipsis;
  overflow: hidden;
}

@include breakpoint(medium) {
  .search {
    padding: rem(10) rem(10) rem(10) rem(32);
    margin-block-end: rem(20);
  }
  input,
  ::placeholder {
    font-size: rem(18);
  }
  input {
    margin: 0 rem(24);
  }
  .btn--blue {
    font-size: rem(16);
    padding: rem(12) rem(24);
  }
}
</style>
