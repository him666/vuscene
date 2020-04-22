<template>
  <div id="app">
    <h1>GLTF Model</h1>
    <three-test />
    <div>
      <button v-on:click="this.switchColor">Change Color</button>
      <button v-on:click="this.speedUp">Spin Faster</button>
      <button v-on:click="this.speedDown">Spin Slower</button>
    </div>
    <h1>Primitive Model</h1>
    <rotate-box :colour=this.colour :speed=this.speed />
    <div>
      <button v-on:click="this.switchColor">Change Color</button>
      <button v-on:click="this.speedUp">Spin Faster</button>
      <button v-on:click="this.speedDown">Spin Slower</button>
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
    const speed = 0.0;
    const index = 0;
    const colour = 0x00ff00;
    const colours = [
      0XFF9900,
      0XFF0000,
      0X3D85C6
    ];

    return {
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