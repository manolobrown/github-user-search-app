<script setup>
defineProps({
  txt: String,
});
</script>

<template>
  <header>
    <h1>{{ txt }}</h1>
    <button class="btn btn--theme-toggle"></button>
    <audio
      src="../assets/audio/light-on.mp3"
      class="theme-audio--light-on"
      data-attribute="adapted from user 160033 file on freesound.org https://freesound.org/people/160033/sounds/366184/ under CC BY-NC 3.0"
    ></audio>
    <audio
      src="../assets/audio/light-off.mp3"
      class="theme-audio--light-off"
      data-attribute="adapted from user 160033 file on freesound.org https://freesound.org/people/160033/sounds/366184/ under CC BY-NC 3.0"
    ></audio>
  </header>
</template>

<style scoped lang="scss">
@use "../assets/scss/util" as *;
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
    letter-spacing: rem(2.5);
    padding: 0;
    transition: color 0.2s ease;

    &,
    svg {
      color: var(--text2);
      fill: var(--text2);
    }
    svg {
      margin-left: rem(15);
    }

    &:hover,
    &:hover svg {
      color: var(--button);
      fill: var(--button);
    }
  }
}
</style>

<script>
export default {
  methods: {
    getCurrentTheme() {
      let theme = window.matchMedia("(prefers-color-scheme: dark)").matches
        ? "dark"
        : "light";
      localStorage.getItem("devfinder.theme")
        ? (theme = localStorage.getItem("devfinder.theme"))
        : null;
      return theme;
    },
    loadTheme(theme, button) {
      const root = document.querySelector(":root");
      if (theme === "light") {
        button.innerHTML = `Dark <svg width="20" height="20" xmlns="http://www.w3.org/2000/svg"><path d="M19.513 11.397a.701.701 0 00-.588.128 7.496 7.496 0 01-2.276 1.336 7.101 7.101 0 01-2.583.462 7.505 7.505 0 01-5.32-2.209 7.568 7.568 0 01-2.199-5.342c0-.873.154-1.72.41-2.49a6.904 6.904 0 011.227-2.21.657.657 0 00-.102-.924.701.701 0 00-.589-.128C5.32.61 3.427 1.92 2.072 3.666A10.158 10.158 0 000 9.83c0 2.8 1.125 5.342 2.967 7.19a10.025 10.025 0 007.16 2.98c2.353 0 4.527-.822 6.266-2.183a10.13 10.13 0 003.58-5.624.623.623 0 00-.46-.796z"/></svg>`;
      } else {
        button.innerHTML = `Light <svg width="20" height="20" xmlns="http://www.w3.org/2000/svg"><path
          d="M13.545 6.455c-.9-.9-2.17-1.481-3.545-1.481a4.934 4.934 0 00-3.545 1.481c-.9.9-1.481 2.17-1.481 3.545 0 1.376.582 2.646 1.481 3.545.9.9 2.17 1.481 3.545 1.481a4.934 4.934 0 003.545-1.481c.9-.9 1.481-2.17 1.481-3.545a4.934 4.934 0 00-1.481-3.545zM10 3.413a.7.7 0 00.688-.688V.688A.7.7 0 0010 0a.7.7 0 00-.688.688v2.037a.7.7 0 00.688.688zM15.635 5.344l1.455-1.455a.67.67 0 000-.952.67.67 0 00-.952 0l-1.455 1.455a.67.67 0 000 .952c.238.264.66.264.952 0zM19.312 9.312h-2.037a.7.7 0 00-.688.688.7.7 0 00.688.688h2.037A.7.7 0 0020 10a.7.7 0 00-.688-.688zM15.608 14.656a.67.67 0 00-.952 0 .67.67 0 000 .952l1.455 1.455a.67.67 0 00.952 0 .67.67 0 000-.952l-1.455-1.455zM10 16.587a.7.7 0 00-.688.688v2.037A.7.7 0 0010 20a.7.7 0 00.688-.688v-2.037a.7.7 0 00-.688-.688zM4.365 14.656L2.91 16.111a.67.67 0 000 .952.67.67 0 00.952 0l1.455-1.455a.67.67 0 000-.952c-.238-.264-.66-.264-.952 0zM3.413 10a.7.7 0 00-.688-.688H.688A.7.7 0 000 10a.7.7 0 00.688.688h2.037A.7.7 0 003.413 10zM4.365 5.344a.67.67 0 00.952 0 .67.67 0 000-.952L3.862 2.937a.67.67 0 00-.952 0 .67.67 0 000 .952l1.455 1.455z"
        /></svg>`;
      }
      root.setAttribute("color-scheme", `${theme}`);
    },
  },
  mounted() {
    const themeBtn = document.querySelector(".btn--theme-toggle");
    themeBtn.addEventListener("click", () => {
      let theme = this.getCurrentTheme();
      let audio;
      if (theme === "dark") {
        audio = document.querySelector(".theme-audio--light-on");
        theme = "light";
      } else {
        audio = document.querySelector(".theme-audio--light-off");
        theme = "dark";
      }
      audio.currentTime = 0;
      audio.play();
      localStorage.setItem("devfinder.theme", `${theme}`);
      this.loadTheme(theme, themeBtn);
    });

    this.loadTheme(this.getCurrentTheme(), themeBtn);
  },
};
</script>
