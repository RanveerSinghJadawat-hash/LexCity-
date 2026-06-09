<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lexcity - 3D Concept</title>
    <style>
        /* Reset and layout */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow-x: hidden;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #0b0f19; /* Deep executive blue/black */
            color: #ffffff;
        }

        /* The 3D Canvas fixed behind everything */
        #webgl-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1; /* Sits behind text content */
            pointer-events: none; /* Allows user to click through to text links */
        }

        /* Front-end content layer */
        .content-layer {
            position: relative;
            z-index: 2; /* Sits on top of the 3D canvas */
            max-width: 800px;
            margin: 0 auto;
            padding: 100px 20px;
            text-align: center;
        }

        h1 {
            font-size: 3.5rem;
            margin-bottom: 20px;
            letter-spacing: 2px;
            text-shadow: 0 2px 10px rgba(0,0,0,0.5);
        }

        p {
            font-size: 1.2rem;
            line-height: 1.8;
            color: #cbd5e1;
            margin-bottom: 40px;
        }

        .cta-btn {
            background: linear-gradient(135deg, #3b82f6, #1d4ed8);
            color: white;
            border: none;
            padding: 15px 35px;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 30px;
            cursor: pointer;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            box-shadow: 0 4px 15px rgba(59, 130, 246, 0.4);
        }

        .cta-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(59, 130, 246, 0.6);
        }
    </style>
</head>
<body>

    <!-- 3D Container -->
    <canvas id="webgl-background"></canvas>

    <!-- Standard Website Content -->
    <div class="content-layer">
        <h1>LEXCITY</h1>
        <p>Bridging the gap between corporate legal excellence and global bilingual mastery. Explore our premium advisory services, sworn translations, and elite Legal English training modules.</p>
        <button class="cta-btn">Explore Services</button>
    </div>

    <!-- Load Three.js from CDN -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script>
        // 1. Setup Scene, Camera, and Renderer
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ canvas: document.getElementById('webgl-background'), antialias: true, alpha: true });
        
        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

        // 2. Create Geometry - A complex, elegant Torus Knot
        const geometry = new THREE.TorusKnotGeometry(10, 3, 100, 16);
        
        // 3. Create a Particle Material for a modern digital aesthetic
        const material = new THREE.PointsMaterial({
            size: 0.05,
            color: 0x3b82f6, // Bright blue matching the corporate accent
            transparent: true,
            opacity: 0.7
        });

        // 4. Combine into a Points Object instead of a solid mesh
        const particleSystem = new THREE.Points(geometry, material);
        scene.add(particleSystem);

        // Position camera outwards
        camera.position.z = 30;

        // Track mouse movement to add subtle parallax interactivity
        let mouseX = 0;
        let mouseY = 0;
        document.addEventListener('mousemove', (event) => {
            mouseX = (event.clientX - window.innerWidth / 2) * 0.05;
            mouseY = (event.clientY - window.innerHeight / 2) * 0.05;
        });

        // 5. Animation Loop
        const clock = new THREE.Clock();

        function animate() {
            requestAnimationFrame(animate);

            const elapsedTime = clock.getElapsedTime();

            // Constant passive rotation
            particleSystem.rotation.x = elapsedTime * 0.05;
            particleSystem.rotation.y = elapsedTime * 0.1;

            // Subtle mouse tracking interpolation
            camera.position.x += (mouseX - camera.position.x) * 0.05;
            camera.position.y += (-mouseY - camera.position.y) * 0.05;
            camera.lookAt(scene.position);

            renderer.render(scene, camera);
        }

        animate();

        // 6. Handle Window Resizing smoothly
        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });
    </script>
</body>
</html>
