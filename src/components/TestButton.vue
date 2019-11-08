<template>
  <div class="button" @click="clickHandler">
    <slot />
  </div>
</template>

<script>
export default {
  name: "test-button",
  methods: {
    clickHandler(evt) {
      this.$emit("click", evt);
    }
  }
};
</script>

<style scoped>
.button {
  background-color: green;
  border-radius: 2px;
  line-height: 1em;
  min-height: 1em;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  cursor: pointer;
  font-size: 1rem;
  font-weight: 700;
  padding: 0.75em 1em;
  outline: none;
  vertical-align: baseline;
  zoom: 1;
  color: white;
}
.button:hover {
  background-color: rgb(0, 88, 0);
}
</style>