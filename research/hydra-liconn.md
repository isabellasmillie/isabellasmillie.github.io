---
layout: default
title: "Hydra LICONN: Building the full connectome via expansion microscopy"
permalink: /research/hydra-liconn/
---

<p class="tab-label tab-label--research">Research</p>
<h1>Hydra LICONN: Building the full connectome via expansion microscopy</h1>

<p class="lede">A short project summary goes here — goals, methods,
and current status.</p>

<div class="model-canvas-wrapper" id="hydra-model-container">
  <div class="model-canvas-helper">Drag to rotate, scroll to zoom</div>
</div>

<script type="importmap">
{
  "imports": {
    "three": "https://cdn.jsdelivr.net/npm/three@0.161.0/build/three.module.js"
  }
}
</script>

<script type="module">
import * as THREE from 'three';
import { OrbitControls } from 'https://cdn.jsdelivr.net/npm/three@0.161.0/examples/jsm/controls/OrbitControls.js';
import { GLTFLoader } from 'https://cdn.jsdelivr.net/npm/three@0.161.0/examples/jsm/loaders/GLTFLoader.js';

const container = document.getElementById('hydra-model-container');
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(45, container.clientWidth / container.clientHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
renderer.outputColorSpace = THREE.SRGBColorSpace;
renderer.setPixelRatio(window.devicePixelRatio);
renderer.setSize(container.clientWidth, container.clientHeight);
container.appendChild(renderer.domElement);

const controls = new OrbitControls(camera, renderer.domElement);
controls.enableDamping = true;
controls.dampingFactor = 0.05;
controls.autoRotate = false;
controls.target.set(0, 0, 0);

const ambient = new THREE.AmbientLight(0xffffff, 0.8);
scene.add(ambient);

const directional = new THREE.DirectionalLight(0xffffff, 0.7);
directional.position.set(5, 10, 7.5);
scene.add(directional);

const loader = new GLTFLoader();
loader.load(
  '{{ "/assets/models/CoronalHydra3Dmodel.glb" | relative_url }}',
  (gltf) => {
    const model = gltf.scene;
    scene.add(model);

    model.traverse((child) => {
      if (child.isMesh) {
        child.castShadow = true;
        child.receiveShadow = true;
        if (child.material) {
          if (child.material.map) {
            child.material.map.encoding = THREE.sRGBEncoding;
          }
          child.material.needsUpdate = true;
        }
      }
    });

    const box = new THREE.Box3().setFromObject(model);
    const size = box.getSize(new THREE.Vector3());
    const center = box.getCenter(new THREE.Vector3());
    model.position.sub(center);

    const maxDim = Math.max(size.x, size.y, size.z);
    const cameraZ = maxDim * 2.2;
    camera.position.set(cameraZ, cameraZ * 0.6, cameraZ);
    camera.lookAt(0, 0, 0);

    controls.update();
  },
  undefined,
  (error) => {
    console.error('Model load error:', error);
  }
);

function resize() {
  const width = container.clientWidth;
  const height = container.clientHeight;
  camera.aspect = width / height;
  camera.updateProjectionMatrix();
  renderer.setSize(width, height);
}

window.addEventListener('resize', resize);
resize();

function animate() {
  requestAnimationFrame(animate);
  controls.update();
  renderer.render(scene, camera);
}
animate();
</script>

<p>Replace this paragraph with the full project description: background,
approach, what LICONN (light microscopy-based connectomics) lets you
resolve at the whole-animal scale, and where the project currently
stands.</p>
