<template>
  <div id="app">
    <three-test />
    <rotate-box />
  </div>
</template>

<script>
import { VRButton } from 'three/examples/jsm/webxr/VRButton.js';
import RotateBox from "./components/RotateBox";
import ThreeTest from "./components/ThreeTest";

export default {
  name: "app",
  components: {
    RotateBox,
    ThreeTest
  },
  mounted(){
    document.body.appendChild( VRButton.createButton( this.renderer ) );
  }
};
  
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>