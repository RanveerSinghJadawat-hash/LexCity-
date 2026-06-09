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
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lexcity - Professional 3D Concept</title>
    <style>
        /* Reset and layout */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #0b0f19; 
            color: #ffffff;
            scroll-behavior: smooth; /* Enables elegant cinematic scrolling */
        }

        /* Fixed 3D Canvas Background */
        #webgl-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1; 
            pointer-events: none; 
        }

        /* Main Wrapper to allow scrolling over fixed background */
        .page-wrapper {
            position: relative;
            z-index: 2;
            width: 100%;
        }

        /* Hero / Landing Section */
        .hero-section {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 0 20px;
            text-align: center;
            box-sizing: border-box;
        }

        /* Advanced 3D Extrusion Effect for Header */
        h1.three-d-text {
            font-size: 3.5rem;
            font-weight: 800;
            color: #ffffff;
            letter-spacing: 4px;
            margin-bottom: 20px;
            text-transform: uppercase;
            text-shadow: 
                0 1px 0 #cccccc,
                0 2px 0 #c5c5c5,
                0 3px 0 #bbbbbb,
                0 4px 0 #b5b5b5,
                0 5px 0 #aaaaaa,
                0 6px 1px rgba(0,0,0,.1),
                0 0 5px rgba(0,0,0,.1),
                0 1px 3px rgba(0,0,0,.3),
                0 3px 5px rgba(0,0,0,.2),
                0 5px 10px rgba(0,0,0,.25),
                0 10px 10px rgba(0,0,0,.2),
                0 20px 20px rgba(0,0,0,.15);
        }

        p.hero-description {
            font-size: 1.2rem;
            line-height: 1.8;
            color: #cbd5e1;
            max-width: 700px;
            margin-bottom: 40px;
        }

        /* Premium Call To Action Button */
        .cta-btn {
            background: linear-gradient(135deg, #3b82f6, #1d4ed8);
            color: white;
            border: none;
            padding: 16px 40px;
            font-size: 1.1rem;
            font-weight: bold;
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 4px 20px rgba(59, 130, 246, 0.4);
            text-decoration: none;
            display: inline-block;
        }

        .cta-btn:hover {
            transform: translateY(-3px) scale(1.03);
            box-shadow: 0 8px 25px rgba(59, 130, 246, 0.7);
        }

        /* Dynamic Services Section Target */
        .services-section {
            min-height: 100vh;
            padding: 100px 20px;
            background: rgba(11, 15, 25, 0.85); /* Frosty transparent overlay */
            backdrop-filter: blur(10px); /* Blurs out the 3D shapes slightly when viewing items */
            -webkit-backdrop-filter: blur(10px);
            box-sizing: border-box;
            display: flex;
            flex-direction: column
