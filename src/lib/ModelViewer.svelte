<script>
    import { onMount, onDestroy } from "svelte";
    import * as THREE from "three";
    import { GLTFLoader } from "three/examples/jsm/loaders/GLTFLoader.js";

    let container;
    let scene, camera, renderer, model;
    let frameId;

    onMount(() => {
        // Scene setup
        scene = new THREE.Scene();

        // Camera setup
        const aspect = container.clientWidth / container.clientHeight;
        camera = new THREE.PerspectiveCamera(45, aspect, 0.1, 1000);
        camera.position.z = 5; // Moved back from 4 to 5 to see more of the model

        // Renderer setup
        renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
        renderer.setSize(container.clientWidth, container.clientHeight);
        renderer.setPixelRatio(window.devicePixelRatio);
        container.appendChild(renderer.domElement);

        // Lighting
        const ambientLight = new THREE.AmbientLight(0xffffff, 1.5);
        scene.add(ambientLight);

        const directionalLight = new THREE.DirectionalLight(0xffffff, 2);
        directionalLight.position.set(5, 5, 5);
        scene.add(directionalLight);

        // Load GLB Model
        const loader = new GLTFLoader();
        loader.load(
            "/golo.glb",
            (gltf) => {
                model = gltf.scene;

                // Center the model
                const box = new THREE.Box3().setFromObject(model);
                const center = box.getCenter(new THREE.Vector3());
                model.position.sub(center);

                // Scale the model to fit
                const size = box.getSize(new THREE.Vector3());
                const maxDim = Math.max(size.x, size.y, size.z);
                const scale = 2.25 / maxDim;
                model.scale.set(scale, scale, scale);

                // Recenter after scaling just in case, but usually position is enough.
                // The issue might be the camera position or the model's origin.
                // Let's also adjust the camera z position slightly if needed or just rely on the smaller scale.

                scene.add(model);
            },
            undefined,
            (error) => {
                console.error(
                    "An error happened loading the GLB model:",
                    error,
                );
            },
        );

        // Animation loop
        const animate = () => {
            frameId = requestAnimationFrame(animate);
            if (model) {
                // Slow spin similar to the original cube
                model.rotation.y += 0.005;
                model.rotation.x = -0.18; // Slight tilt like the original animation
            }
            renderer.render(scene, camera);
        };
        animate();

        // Handle resize
        const handleResize = () => {
            if (!container) return;
            const width = container.clientWidth;
            const height = container.clientHeight;
            camera.aspect = width / height;
            camera.updateProjectionMatrix();
            renderer.setSize(width, height);
        };
        window.addEventListener("resize", handleResize);

        return () => {
            window.removeEventListener("resize", handleResize);
        };
    });

    onDestroy(() => {
        if (frameId) cancelAnimationFrame(frameId);
        if (renderer) {
            renderer.dispose();
            if (renderer.domElement && renderer.domElement.parentNode) {
                renderer.domElement.parentNode.removeChild(renderer.domElement);
            }
        }
        if (scene) {
            scene.traverse((object) => {
                if (object.isMesh) {
                    object.geometry.dispose();
                    if (object.material.isMaterial) {
                        cleanMaterial(object.material);
                    } else {
                        for (const material of object.material) {
                            cleanMaterial(material);
                        }
                    }
                }
            });
        }
    });

    function cleanMaterial(material) {
        material.dispose();
        for (const key of Object.keys(material)) {
            const value = material[key];
            if (value && typeof value.dispose === "function") {
                value.dispose();
            }
        }
    }
</script>

<div bind:this={container} class="model-container"></div>

<style>
    .model-container {
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>
