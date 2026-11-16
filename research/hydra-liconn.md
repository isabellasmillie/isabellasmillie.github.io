---
layout: default
title: "Hydra LICONN: Building the full connectome via expansion microscopy"
permalink: /research/hydra-liconn/
neuroglancer_url: 'https://neuroglancer-demo.appspot.com/#!%7B%22dimensions%22:%7B%22z%22:%5B2.998661909009813e-7%2C%22m%22%5D%2C%22y%22:%5B3.014842512598992e-7%2C%22m%22%5D%2C%22x%22:%5B3.0148177288224473e-7%2C%22m%22%5D%7D%2C%22position%22:%5B1448.933837890625%2C5051.203125%2C4424%5D%2C%22crossSectionScale%22:33.11545195869233%2C%22projectionScale%22:16384%2C%22layers%22:%5B%7B%22type%22:%22image%22%2C%22source%22:%7B%22url%22:%22s3://dragonfly-expansion-data/merged_3_12.ome.zarr/%7Czarr2:%22%2C%22transform%22:%7B%22outputDimensions%22:%7B%22t%27%22:%5B0.001%2C%22s%22%5D%2C%22c%27%22:%5B1%2C%22%22%5D%2C%22z%22:%5B2.998661909009813e-7%2C%22m%22%5D%2C%22y%22:%5B3.014842512598992e-7%2C%22m%22%5D%2C%22x%22:%5B3.0148177288224473e-7%2C%22m%22%5D%7D%7D%7D%2C%22localDimensions%22:%7B%22t%27%22:%5B0.001%2C%22s%22%5D%2C%22c%27%22:%5B1%2C%22%22%5D%7D%2C%22localPosition%22:%5B0%2C0%5D%2C%22tab%22:%22rendering%22%2C%22shaderControls%22:%7B%22normalized%22:%7B%22range%22:%5B308%2C0%5D%7D%7D%2C%22name%22:%22merged_3_12.ome.zarr%22%7D%5D%2C%22selectedLayer%22:%7B%22visible%22:true%2C%22layer%22:%22merged_3_12.ome.zarr%22%7D%2C%22layout%22:%224panel-alt%22%2C%22uiControlVisibility%22:%7B%7D%7D'
---

<p class="tab-label tab-label--research">Research</p>
<h1><em>Hydra</em> LICONN: Building the full connectome via expansion microscopy</h1>

<h2 class="liconn-heading">Light-microscopy-based connectomics: 16-fold expansion of <em>Hydra</em> whole-body samples</h2>
<p class="hydra-caption">I optimized <a href="https://www.nature.com/articles/s41586-025-08985-1">Tavakoli et al.</a>'s iterative expansion protocol for <em>Hydra</em>'s whole body. To achieve segmentable data, we use a pan-protein fluorescent label and neuron-specific antibodies.</p>
<div class="hydra-gallery liconn-image-grid liconn-image-grid--protocol">
  <figure><img src="{{ '/assets/images/LICONNProtocol.jpeg' | relative_url }}" alt="Protocol for iterative expansion microscopy"></figure>
  <figure><img src="{{ '/assets/images/HydraTriExpanded.jpeg' | relative_url }}" alt="Expanded Hydra specimen"></figure>
</div>

<h2 class="liconn-heading">Confocal imaging of expanded <em>Hydra</em></h2>
<p class="hydra-caption">After ordering a new Andor Dragonfly spin-disc confocal imaging system, overseeing its installation, and receiving training on its acquisition software, I established an imaging protocol to accurately and efficiently capture an expanded, hydrogel-embedded <em>Hydra</em> volumetrically.</p>
<div class="hydra-gallery liconn-image-grid">
  <figure><img src="{{ '/assets/images/Dragonfly-display.jpg' | relative_url }}" alt="Andor Dragonfly confocal microscope"></figure>
  <figure><img src="{{ '/assets/images/DragonflyImage-display.jpg' | relative_url }}" alt="Confocal image captured using the Dragonfly system"></figure>
</div>

<h2 class="liconn-heading">Alignment of imaged volumes</h2>
<p class="hydra-caption">Due to objective working-distance limits, a blockfacing technique had to be applied during volumetric imaging. I imaged as much gel as possible, then used a vibratome to remove a portion of the previously imaged gel, leaving a small amount to capture an overlap. This overlap is used to computationally align the separate volumes.</p>
<div class="hydra-gallery liconn-image-grid liconn-image-grid--alignment">
  <figure><img src="{{ '/assets/images/Aug_BF_3.jpeg' | relative_url }}" alt="Blockfaced volume section"></figure>
  <figure><img src="{{ '/assets/images/AlignedBlocks.jpeg' | relative_url }}" alt="Aligned volumetric image blocks"></figure>
</div>

<h2 class="liconn-heading">Complete <em>Hydra</em> foot volume</h2>
<p class="hydra-interactive-caption">Hover over a plane, hold shift, and scroll to explore <em>Hydra</em>'s foot. Hold Ctrl and scroll to zoom into individual cells.</p>
{% assign neuroglancer_minimized_url = page.neuroglancer_url | replace: '%22selectedLayer%22:%7B%22visible%22:true', '%22selectedLayer%22:%7B%22visible%22:false' %}
<iframe class="neuroglancer-viewer" src="{{ neuroglancer_minimized_url | escape }}"
  title="Interactive Neuroglancer view of the Hydra LICONN volume"
  allowfullscreen loading="lazy"></iframe>
<p class="neuroglancer-link"><a href="{{ neuroglancer_minimized_url | escape }}" target="_blank" rel="noopener">Open Neuroglancer in a new tab</a></p>

<h2 class="liconn-heading">Segmentation and 3D reconstruction</h2>
<p class="hydra-caption">Using webKnossos segmentation software, my team of undergraduates has begun annotating our volumetric data. For rapid and reliable data access, webKnossos livestreams our Zarr volume from our AWS bucket.</p>
<p class="model-legend"><span class="model-legend__muscles">Muscles</span><span class="model-legend__neurons">Neurons</span><span class="model-legend__unknown">Unknown 'ring' structure</span></p>
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
