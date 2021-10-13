<template>
  <form @submit="onSearch" class="search">
    <img src="../assets/icon-search.svg" alt="" />
    <input
      v-model="searchValue"
      type="text"
      name="user"
      placeholder="Search GitHub username&hellip;"
    />
    <div class="no-results"></div>
    <button type="submit" class="btn btn--blue">Search</button>
  </form>
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

.no-results {
  color: #f74646;
  margin-right: rem(10);
  font-size: rem(14);
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

  .no-results {
    margin-right: rem(25);
    font-size: rem(16);
  }
}
</style>

<script>
export default {
  name: "SearchHeader",
  props: {
    value: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      localValue: this.value,
    };
  },
  computed: {
    searchValue: {
      get() {
        return this.isValuePropSet() ? this.value : this.localValue;
      },
      set(value) {
        this.$emit("input", value);
        this.localValue = value;
      },
    },
  },
  methods: {
    onSearch(e) {
      e.preventDefault();

      this.$emit("search", this.searchValue);
    },
    isValuePropSet() {
      return (
        !!this.$options.propsData && this.$options.propsData.value !== undefined
      );
    },
  },
};
</script>
