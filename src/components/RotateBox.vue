<template>
  <canvas id="canvas" width="600" height="400"></canvas>
</template>

<script>
import * as THREE from "three";
export default {
  name: "RotateBox",
  props: {
    speed: {
      required: false,
      type: Number,
      default: 0.02
    },
    color: {
      required: false,
      type: Number,
      default: 0x00ff00
    }
  },
  data() {
    const scene = new THREE.Scene();
    const renderer = null;
    const camera = new THREE.PerspectiveCamera(75, 600 / 400, 0.1, 1000);
    //const light = new THREE.DirectionalLight(0xffffff);
    const hemisphereLight = new THREE.HemisphereLight( 0xffffbb, 0x080820, 1 );
    const pointLight = new THREE.PointLight(0xffffff, 1, 100);
    const pointLight2 = new THREE.PointLight(0x00ff00, 1, 100);
    const spotLight = new THREE.SpotLight(0xffffff);
    const spotLight2 = new THREE.SpotLight(0xffffff);
    const geometry = new THREE.BoxGeometry(1, 1, 1);
    const material = new THREE.MeshLambertMaterial( { color: this.color } );
    const cube = new THREE.Mesh(geometry, material);
    return { 
      scene, 
      renderer, 
      camera, 
      hemisphereLight, 
      pointLight, 
      pointLight2, 
      spotLight, 
      spotLight2, 
      geometry, 
      material, 
      cube
    };
  },
  mounted() {
    const $canvas = document.getElementById("canvas");
    this.renderer = new THREE.WebGLRenderer({
      antialias: true,
      canvas: $canvas
    });
    
    this.pointLight.position.set(0, 0, 2);
    this.pointLight2.position.set(0, 0, 10);
    this.spotLight.position.set(100, 1000, 100);
    this.spotLight2.position.set(100, 1000, 100);
    this.camera.position.set(0, 0, 2);
    //this.light.position.set(0, 0, 10);
    this.scene.add(this.cube);
    //this.scene.add(this.light);
    this.scene.add(this.hemisphereLight);
    this.scene.add(this.spotlight);
    this.scene.add(this.spotlight2);
    this.scene.add(this.pointLight);
    this.scene.add(this.pointLight2);

    this.animate();
  },
  methods: {
    animate() {
      requestAnimationFrame(this.animate);

      this.cube.rotation.x += this.speed;
      this.cube.rotation.y += this.speed;

      this.renderer.render(this.scene, this.camera);
    }
  }
};
</script>

<style></style>