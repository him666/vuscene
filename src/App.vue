<template>
  <div id="app">
    <h1>GLTF Model</h1>
    <three-test />
    <h1>Primitive Model</h1>
    <rotate-box :colour=this.colour :speed=this.speed :texture="this.texture" />
    <div>
      <button v-on:click="this.toggleTexture">Change Texture</button>
      <button v-on:click="this.switchColor">Change Color</button>
      <button v-on:click="this.speedUp">Spin ClockWise</button>
      <button v-on:click="this.speedDown">Spin Counter ClockWise</button>
    </div>
    
  </div>
</template>

<script>

import RotateBox from "./components/RotateBox";
import ThreeTest from "./components/ThreeTest";

export default {
  name: "app",
  components: {
    RotateBox,
    ThreeTest
  },
  data() {
    const texture = null;
    const speed = 0.0;
    const index = 0;
    const colour = 0x00ff00;
    const colours = [
      0XFF9900,
      0XFF0000,
      0X3D85C6,
      0XA7B5B5,
      0X9FC5E8,
      0X0B5394
    ];

    return {
      texture,
      speed,
      index,
      colour,
      colours
    }
  },
  methods: {
    speedUp(){
      this.speed += 0.01;
    },
    speedDown(){
      this.speed -= 0.01;
    },
    switchColor(){
      if(this.index > this.colours.length){
        this.index = 0;
      }
      this.colour = this.colours[this.index];
      this.index++;
    },
    toggleTexture(){
      if(this.texture){
        this.texture = null;
      } else {
        this.texture = '/three-assets/textures/Char_baseColor2.png';
      }
      console.log(this.texture);
    }
  },
  mounted(){
   
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