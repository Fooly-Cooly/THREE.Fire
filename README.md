THREE.Fire
=====================

Ray tracing based [real-time procedural volumetric fire](http://dl.acm.org/citation.cfm?id=1230131) object for Three.js.

![fire](https://raw.githubusercontent.com/Fooly-Cooly/Fooly-Cooly.github.io/master/THREE.Fire/fire.gif)


## Example

```javascript

import * as THREE from './three.module.js';
import { Fire } from  "./Fire.js";

let canvas = document.querySelector('#viewport');
let renderer = new THREE.WebGLRenderer({ canvas: canvas, antialias: true, alpha: true });
	renderer.setPixelRatio( window.devicePixelRatio );
	renderer.setSize( window.innerWidth, window.innerHeight );

let camera = new THREE.PerspectiveCamera( 35, window.innerWidth / window.innerHeight, 0.1, 500 ); // Parameters: (fov, aspect, near, far)
	camera.position.set( 0.00, -0.04, 0.50 ); // ( x, y, z )
	camera.rotation.set( 0.00, 0.00, 0.00 ); // ( x, y, z )
	camera.fov = 60;

let scene = new THREE.Scene();
let fire = new Fire();
	fire.scale.set( 0.15, 0.30, 0.15 );
	fire.position.set( 0.00, 0.00, 0.00 );
	fire.name = "Fire1";
scene.add( fire );

function animate() {
	requestAnimationFrame( animate );

	fire.update(performance.now() / 1000);
	renderer.render( scene, camera );
}
animate();

```

## Description

THREE.Fire is an extended THREE.Mesh object that uses a THREE.BoxGeometry.
It generates fire shapes that are made up of noise and a fire texture.
I have updated it to comply with more modern Three.js implementations.
It's been tested working on Three.js revision 131

![wireframe](https://raw.githubusercontent.com/Fooly-Cooly/Fooly-Cooly.github.io/master/THREE.Fire/wireframe.gif "Visualized wireframe of THREE.Fire's geometry")

You must pass a fire texture argument to THREE.Fire like this.
![firetex](https://raw.githubusercontent.com/Fooly-Cooly/Fooly-Cooly.github.io/master/THREE.Fire/Fire.png "Fire texture")

[for more details.](http://dl.acm.org/citation.cfm?id=1230131)

## Demo

[Demo](https://Fooly-Cooly.github.io/THREE.Fire)

## Sources

- Original implementation - https://github.com/mattatz/THREE.Fire

- Real-Time procedural volumetric fire - http://dl.acm.org/citation.cfm?id=1230131

- webgl-noise - https://github.com/ashima/webgl-noise/blob/master/src/noise3D.glsl

- primitive: blog | object space raymarching - http://i-saint.hatenablog.com/entry/2015/08/24/225254

