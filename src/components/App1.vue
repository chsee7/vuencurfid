<template>
  <div id="app1" :style="divStyle"></div>
</template>

<script>
export default {
  props: {
    backgroundImage: {
      type: String,
      default: ''
    }
  },
  computed: {
    divStyle() {
      return {
        backgroundImage: `url(${this.backgroundImage})`
      };
    }
  }
};
</script>

<style>
#app1 {
  pointer-events: none;
  top: 0px;
  left: 0px;
  z-index: 1000;
  position: fixed; 
  width: 1536px; 
  height: 703px;
  background-repeat: repeat;
  background-position: left top;
}
</style>
