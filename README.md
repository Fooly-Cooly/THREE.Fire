THREE.Fire
=====================

## Description
THREE.Fire is a ray tracing based [real-time procedural volumetric fire](http://dl.acm.org/citation.cfm?id=1230131) object for Three.js.
It extends the THREE.Mesh object that uses a THREE.BoxGeometry to generate fire shapes that are made up of a fire texture and noise.
I have updated it to comply with more modern Three.js implementations and has been tested working on Three.js revision 131

[Demo](https://Fooly-Cooly.github.io/THREE.Fire)

## Preview
<img src="https://raw.githubusercontent.com/Fooly-Cooly/Fooly-Cooly.github.io/master/THREE.Fire/fire.gif" height="350" alt="Example" /><img src="https://raw.githubusercontent.com/Fooly-Cooly/Fooly-Cooly.github.io/master/THREE.Fire/wireframe.gif" height="350" alt="Wireframe" />

## Example

```javascript

import * as THREE from './three.module.js';
import { Fire } from  "./Fire.js";

let canvas = document.querySelector('#viewport');
let renderer = new THREE.WebGLRenderer({ canvas: canvas, antialias: true, alpha: true });
	renderer.setPixelRatio( window.devicePixelRatio );
	renderer.setSize( window.innerWidth, window.innerHeight );

let camera = new THREE.PerspectiveCamera( 35, window.innerWidth / window.innerHeight, 0.1, 500 );
	camera.position.set( 0.00, -0.04, 0.50 );
	camera.rotation.set( 0.00, 0.00, 0.00 );
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

## Sources

- Original implementation - https://github.com/mattatz/THREE.Fire

- Real-Time procedural volumetric fire - http://dl.acm.org/citation.cfm?id=1230131

- webgl-noise - https://github.com/ashima/webgl-noise/blob/master/src/noise3D.glsl

- primitive: blog | object space raymarching - http://i-saint.hatenablog.com/entry/2015/08/24/225254