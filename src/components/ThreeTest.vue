<template>
  <div id="scene-container" ref="sceneContainer" width="600" height="400"></div>
</template>

<script>
import * as THREE from 'three'
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls'
import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader'


export default {
  name: 'ThreeTest',
  props: {
    
  },
  data () {
    return {
      container: null,
      scene: null,
      camera: null,
      controls: null,
      renderer: null,
    }
  },
  methods: {
    init () {
      
      this.container = this.$refs.sceneContainer;

      const fov = 60; // Field of view
      const aspect = this.container.clientWidth / this.container.clientHeight;
      const near = 0.1; // the near clipping plane
      const far = 30; // the far clipping plane
      const camera = new THREE.PerspectiveCamera(fov, aspect, near, far);
      camera.position.set(0, 5, 10);
      this.camera = camera;

      this.scene = new THREE.Scene();
      this.scene.background = new THREE.Color('skyblue');

      // add lights
      const ambientLight = new THREE.HemisphereLight(
        0xffffff, // bright sky color
        0x222222, // dim ground color
        0 // intensity
      );
      const mainLight = new THREE.DirectionalLight(0xffffff, 4.0);
      const pointLight = new THREE.PointLight(0xffffff, 1, 100);
      const pointLight2 = new THREE.PointLight(0x00ff00, 1, 100);
      const spotLight = new THREE.SpotLight(0x3D85C6);
      spotLight.position.set(0,5,10);
      spotLight.castShadow = true;
      spotLight.shadow.mapSize.width = 600;
      spotLight.shadow.mapSize.height = 400;
      spotLight.shadow.camera.near = near;
      spotLight.shadow.camera.far = far;
      spotLight.shadow.camera.fov = fov;

      

      const spotLight2 = new THREE.SpotLight(0x3D85C6);
      spotLight2.position.set( 100, 1000, 100 );
      spotLight2.castShadow = true;
      spotLight2.shadow.mapSize.width = 600;
      spotLight2.shadow.mapSize.height = 400;
      spotLight2.shadow.camera.near = 500;
      spotLight2.shadow.camera.far = 4000;
      spotLight2.shadow.camera.fov = 30;
      spotLight2.position.set( 100, 1000, 100 );
      spotLight2.castShadow = true;
      this.scene.add(spotLight);
      this.scene.add(spotLight2);
      mainLight.position.set(10, 10, 10);
      this.scene.add(mainLight, ambientLight,pointLight, pointLight2);

      // add controls
      this.controls = new OrbitControls(this.camera, this.container);

      // create renderer
      this.renderer = new THREE.WebGLRenderer({ antialias: true });
      this.renderer.setSize(this.container.clientWidth, this.container.clientHeight);
      this.renderer.setPixelRatio(window.devicePixelRatio);
      this.renderer.gammaFactor = 2.2;
      this.renderer.outputEncoding = THREE.sRGBEncoding;
      this.renderer.physicallyCorrectLights = true;
      this.renderer.shadowMap.enabled = true;
      this.renderer.shadowMap.type = THREE.PCFSoftShadowMap;
      this.container.appendChild(this.renderer.domElement);

      // set aspect ratio to match the new browser window aspect ratio
      this.camera.aspect = this.container.clientWidth / this.container.clientHeight;
      this.camera.updateProjectionMatrix();
      this.renderer.setSize(this.container.clientWidth, this.container.clientHeight);

      const loader = new GLTFLoader()
      loader.load(
        '/three-assets/scene.gltf',
        gltf => {
          this.scene.add(gltf.scene)
        },
        undefined,
        undefined
      );

      this.renderer.setAnimationLoop(() => {
        this.render();
      })
    },
    render () {
      this.renderer.render(this.scene, this.camera);
    }
  },
  mounted () {
    this.init();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#scene-container {
  height: 400px !important;
  width: 600px;
  margin-left: calc(24.3vw);
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
#scene-container {
  height: 100%;
}
</style>
