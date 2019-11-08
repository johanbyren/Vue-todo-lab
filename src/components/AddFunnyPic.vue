<template>
  <div>
    <!-- <fish-button type="primary" v-on:click="isHidden = !isHidden">Show funny picture</fish-button> -->
    <fish-button type="primary" @click="toggle = !toggle">Show Vue Logo</fish-button>
    <img v-show="toggle" :src="require('../assets/logo.png')" />
    <TestButton>Test button component</TestButton>
  </div>
</template>

<script>
import Vue from "vue";
import Button from "@bit/myliang.fish-ui.button";
import "@bit/myliang.fish-ui.styles.button";
import TestButton from "./TestButton";

Vue.component(Button.name, Button);

export default {
  name: "AddFunnyPic",
  components: {
    Button,
    TestButton
  },
  data() {
    return {
      toggle: false
    };
  }
};
</script>

<style scoped>
@import "https://cdn.bootcss.com/font-awesome/4.7.0/css/font-awesome.css";
@import "https://fonts.proxy.ustclug.org/css?family=Lato:400,700,400italic,700italic&subset=latin";

div {
  margin: 10px;
}

img {
  height: 26px;
  width: 26px;
}
</style>

