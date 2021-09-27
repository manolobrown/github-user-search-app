<script setup>
import { ref } from "vue";

defineProps({
  txt: String,
});

import SearchHeader from "./SearchHeader.vue";
</script>

<template>
  <SearchHeader />
  <div class="user">
    <header>
      <img src="../assets/icon-octocat.svg" alt="" />
      <div class="user__info">
        <h2>The Octocat</h2>
        <a href="#">@octocat</a>
        <div class="date">Joined 25 Jan 2011</div>
      </div>
    </header>

    <main>
      <p>
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Id porro
        mollitia fugit delectus consectetur vel ipsa laboriosam, error
        voluptatibus? Debitis?
      </p>

      <div class="user__meta">
        <div class="repos">
          <h3>Repos</h3>
          <div class="number">8</div>
        </div>
        <div class="followers">
          <h3>Followers</h3>
          <div class="number">3938</div>
        </div>
        <div class="following">
          <h3>Following</h3>
          <div class="number">9</div>
        </div>
      </div>
    </main>

    <footer>
      <div class="user__links">
        <ul>
          <li>
            <span>
              <img src="../assets/icon-location.svg" alt="" />
            </span>
            <a href="#">San Franscisco</a>
          </li>
          <li>
            <span>
              <img src="../assets/icon-website.svg" alt="" />
            </span>
            <a href="#">https://github.blog</a>
          </li>
          <li>
            <span>
              <img src="../assets/icon-twitter.svg" alt="" />
            </span>
            <a href="#">Not Available</a>
          </li>
          <li>
            <span>
              <img src="../assets/icon-company.svg" alt="" />
            </span>
            <a href="#">@github</a>
          </li>
        </ul>
      </div>
    </footer>
  </div>
</template>

<style scoped lang="scss">
@use "sass:math";

// Source: https://css-tricks.com/snippets/sass/px-to-em-functions/
@function rem($pixels, $context: 16) {
  @return (math.div($pixels, $context)) * 1rem;
}
.user {
  padding: rem(32) rem(24);

  p,
  .date,
  &__meta h3 {
    color: var(--gray);
  }
  p {
    line-height: rem(25);
    margin-block-end: rem(30);
  }

  &__meta {
    background-color: var(--white-gray);
    border-radius: rem(10);
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: rem(17);
    margin-block-end: rem(30);

    > div {
      flex: 0 0 33.333%;
      max-width: 33.333%;
    }

    h3 {
      font-size: rem(11);
    }
    .number {
      font-size: rem(16);
      font-weight: 700;
    }
  }

  &__links {
    ul {
      list-style: none;
      padding: 0;
      margin: 0;
    }

    li {
      display: flex;
      align-items: center;
      margin-block-end: rem(15);
    }
    li span {
      width: rem(20);
      margin-right: rem(15);
    }
    li,
    li a {
      color: var(--blue-gray);
      font-size: rem(13);
    }
  }
}
header {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  margin-block-end: rem(30);

  img {
    width: rem(70);
    height: rem(70);
    margin-right: rem(18);
  }

  h2 {
    margin-block-end: 0;
    font-size: rem(16);
    line-height: 1;
  }
  h3,
  a,
  .date {
    font-size: rem(13);
    line-height: 1;
    margin-top: rem(6);
  }
}
</style>
