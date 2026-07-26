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
import { DRACOLoader } from 'https://cdn.jsdelivr.net/npm/three@0.161.0/examples/jsm/loaders/DRACOLoader.js';

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

const loadingOverlay = document.createElement('div');
loadingOverlay.className = 'model-canvas-loading';
loadingOverlay.textContent = 'Loading model…';
container.appendChild(loadingOverlay);

const ambient = new THREE.AmbientLight(0xffffff, 0.8);
scene.add(ambient);

const directional = new THREE.DirectionalLight(0xffffff, 0.7);
directional.position.set(5, 10, 7.5);
scene.add(directional);

const dracoLoader = new DRACOLoader();
dracoLoader.setDecoderPath('https://www.gstatic.com/draco/v1/decoders/');
dracoLoader.setDecoderConfig({ type: 'js' });
dracoLoader.preload();

const loader = new GLTFLoader();
loader.setDRACOLoader(dracoLoader);
loader.load(
  '{{ "/assets/models/CoronalHydra3Dmodel-optimized.glb" | relative_url }}',
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

    const maxDim = Math.max(size.x, size.y, size.z, 1);
    const zoomDistance = maxDim * 0.15; // very deep 900% zoom
    camera.position.set(-zoomDistance * 1.1, zoomDistance * 1.35, zoomDistance * 0.2);
    camera.near = Math.max(0.001, maxDim / 200);
    camera.far = maxDim * 20;
    camera.updateProjectionMatrix();
    camera.lookAt(0, 0, 0);

    controls.maxDistance = maxDim * 6;
    controls.minDistance = maxDim * 0.25;
    controls.target.set(0, 0, 0);
    controls.update();

    loadingOverlay.style.display = 'none';
  },
  (xhr) => {
    if (xhr.lengthComputable) {
      const percent = Math.round((xhr.loaded / xhr.total) * 100);
      loadingOverlay.textContent = `Loading model ${percent}%`;
    }
  },
  (error) => {
    loadingOverlay.textContent = 'Failed to load model';
    loadingOverlay.style.opacity = '1';
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
