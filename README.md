# vuscene
## Description of the application.
App created using VUE-CLI and THREE.js,
2 separate scenes, first Loading a GLTF Model and the sencond a 3D object Mesh


## Link to the final, hosted application.
https://vuescene.herokuapp.com


For the Cube Model i tried to leverage the rendering process using  VUE.Js' lifecycle methods, trying to create everything the mount or data methods, passing all the important properties from the parent component to the child to keep behaviours easy to change. I also added some lights to give it a better look and according to requirements.
Tried to change textures to the cube but couldnt load the texture fast enough to render it, loading the extra texture from the beggining could be a possible solution. I also added 2 buttons to add movement to the cube.

For the GLTF Scene i couldnt really do this, due to lack of time, but i managed to load the GLTF model and added some lights to it, although they dont seem to render, also added some controls so that the GLTF model can be explored.

## Piece of Code I am proud of.
https://github.com/him666/LolFight/blob/master/app/controllers/guest_controller.rb

## Link to your resume or public profile.
https://him666.github.io/Resume/

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
