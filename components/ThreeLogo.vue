<template>
    <div id="threejs-container"></div>
</template>

<script setup>
import { onMounted } from 'vue';
import * as THREE from 'three';

onMounted(() => {
    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
    const renderer = new THREE.WebGLRenderer();
    renderer.setSize(window.innerWidth, window.innerHeight);
    document.getElementById('threejs-container').appendChild(renderer.domElement);

    // Add lighting
    const ambientLight = new THREE.AmbientLight(0x404040); // Soft white light
    scene.add(ambientLight);

    // Add particles
    const particleGeometry = new THREE.BufferGeometry();
    const particleCount = 1200;
    const positions = new Float32Array(particleCount * 13);

    for (let i = 0; i < particleCount; i++) {
        positions[i * 3] = (Math.random() - 0.5) * 2000;
        positions[i * 3 + 1] = (Math.random() - 0.5) * 2000;
        positions[i * 3 + 2] = (Math.random() - 0.5) * 2000;
    }

    particleGeometry.setAttribute('position', new THREE.BufferAttribute(positions, 3));
    const particleMaterial = new THREE.PointsMaterial({ color: 0x34623f, size: 2 });
    const particleSystem = new THREE.Points(particleGeometry, particleMaterial);
    scene.add(particleSystem);

    // Add logo as texture (using uploaded logo PNG)
    const logoTexture = new THREE.TextureLoader().load('/assets/media/Underthehood.png');
    const logoMaterial = new THREE.SpriteMaterial({
        map: logoTexture,
        depthTest: false // Disable depth test to render on top
    });

    const logo = new THREE.Sprite(logoMaterial);

    // Position and scale the logo
    logo.position.set(0, 0, 0); // Center the logo
    logo.scale.set(400, 400, 1); // Adjust size
    logo.renderOrder = 1; // Ensure it's rendered on top
    scene.add(logo);

    // Camera setup
    camera.position.set(0, 0, 1000); // Position camera back a bit to see the logo clearly
    camera.lookAt(0, 0, 0); // Make camera point at the center

    // Animation loop
    const animate = function () {
        requestAnimationFrame(animate);

        // Rotate particle system slightly for motion
        particleSystem.rotation.x += 0.001;
        particleSystem.rotation.y += 0.001;

        renderer.render(scene, camera);
    };

    animate();

    // Handle window resize
    window.addEventListener('resize', () => {
        const width = window.innerWidth;
        const height = window.innerHeight;
        renderer.setSize(width, height);
        camera.aspect = width / height;
        camera.updateProjectionMatrix();
    });
});
</script>


<style scoped>
#threejs-container {
    width: 100%;
    height: 100%;
}
</style>