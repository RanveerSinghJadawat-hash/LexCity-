<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lexcity - Desktop 3D Experience</title>
    <style>
        /* Exact Executive Corporate Color Palette */
        :root {
            --dark-chocolate: #342a22; /* Header and Footer Base */
            --premium-gold: #d4b278;    /* Main Body Panel BG */
            --gold-bevel-light: #edd1a1;
            --gold-bevel-dark: #aa8952;
            --text-dark: #29201a;
            --text-gold: #d4b278;
        }

        /* Desktop Layout Architecture */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100vh;
            font-family: 'Georgia', 'Times New Roman', Times, serif;
            background-color: var(--dark-chocolate);
            color: var(--text-gold);
            display: flex;
            flex-direction: column;
            overflow: hidden; /* Perfect desktop viewport containment */
        }

        /* --- 1. DESKTOP HEADER --- */
        header {
            background-color: var(--dark-chocolate);
            padding: 25px 60px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid var(--text-gold);
            box-shadow: 0 4px 20px rgba(0,0,0,0.4);
            z-index: 10;
        }

        .logo-block {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo-emblem {
            font-size: 2.2rem;
            text-shadow: 0 3px 6px rgba(0,0,0,0.5);
        }

        .logo-text-wrapper {
            display: flex;
            flex-direction: column;
        }

        .logo-main {
            font-size: 1.8rem;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 2px;
            /* 3D Chiseled Metal Effect */
            text-shadow: 1px 1px 0px #4d3d32, 2px 2px 0px #1a1511, 3px 3px 5px rgba(0,0,0,0.6);
        }

        .logo-slogan {
            font-size: 0.75rem;
            letter-spacing: 4px;
            text-transform: uppercase;
            opacity: 0.8;
            margin-top: 2px;
        }

        nav {
            display: flex;
            gap: 35px;
        }

        nav a {
            color: var(--text-gold);
            text-decoration: none;
            font-size: 1.15rem;
            letter-spacing: 1px;
            padding-bottom: 5px;
            position: relative;
            transition: opacity 0.3s ease;
        }

        nav a.active::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 2px;
            background-color: var(--text-gold);
            box-shadow: 0 0 8px var(--gold-bevel-light);
        }

        nav a:hover {
            opacity: 0.7;
        }

        /* --- 2. MAIN 3D DISPLAY PANEL --- */
        main {
            background-color: var(--premium-gold);
            color: var(--text-dark);
            flex-grow: 1;
            padding: 50px 80px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            /* Recessed Bevel Frame Technique */
            box-shadow: 
                inset 0 15px 25px rgba(0,0,0,0.25), 
                inset 0 -15px 25px rgba(0,0,0,0.25);
            border-top: 4px solid var(--gold-bevel-light);
            border-bottom: 4px solid var(--gold-bevel-dark);
            z-index: 5;
        }

        .hero-title {
            font-size: 3.5rem;
            font-weight: bold;
            margin: 0 0 8px 0;
            letter-spacing: 1px;
            /* Dynamic Sculpted 3D Typography Shadowing */
            text-shadow: 
                0 1px 0px #edd8b4,
                1px 2px 0px #cbb082,
                2px 3px 1px #91784f,
                3px 6px 8px rgba(0,0,0,0.3);
        }

        .hero-subtitle {
            font-size: 1.5rem;
            font-style: italic;
            margin: 0 0 45px 0;
            color: #3d3027;
        }

        /* Grid Matrix Optimized for Desktop Views */
        .desktop-showcase-container {
            display: grid;
            grid-template-columns: repeat(3, 1fr); /* Enforces exact 3-column split */
            gap: 50px;
            perspective: 1200px; /* High-depth spatial environment */
        }

        .showcase-card {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-decoration: none;
            color: var(--text-dark);
            transform-style: preserve-3d;
            /* Smooth transitions when restoring position */
            transition: transform 0.2s ease-out, box-shadow 0.2s ease-out;
        }

        .3d-frame {
            width: 100%;
            aspect-ratio: 1.45 / 1;
            border-radius: 6px;
            overflow: hidden;
            background-color: #221a15;
            border: 1px solid rgba(255,255,255,0.25);
            /* Soft physical dropped shadow */
            box-shadow: 0 15px 35px rgba(0,0,0,0.3);
            transform: translateZ(0px);
            transition: transform 0.4s ease;
        }

        .3d-frame img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block;
            filter: grayscale(15%) contrast(105%);
            transition: transform 0.4s ease;
        }

        .card-label {
            margin-top: 20px;
            font-size: 1.3rem;
            font-weight: bold;
            letter-spacing: 0.5px;
            transform: translateZ(20px); /* Forces text to pop forward in spatial layer */
            text-shadow: 0 2px 4px rgba(255,255,255,0.4);
        }

        /* Desktop Interactivity State Handling */
        .showcase-card:hover .3d-frame {
            box-shadow: 0 25px 45px rgba(0,0,0,0.45);
        }
        .showcase-card:hover .3d-frame img {
            transform: scale(1.05);
        }

        /* --- 3. EXECUTIVE FOOTER --- */
        footer {
            background-color: var(--dark-chocolate);
            padding: 25px 60px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-top: 1px solid rgba(214, 178, 120, 0.25);
            font-size: 0.95rem;
            z-index: 10;
        }

        .footer-branding {
            display: flex;
            flex-direction: column;
            opacity: 0.85;
        }

        .fb-main {
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .fb-sub {
            font-size: 0.65rem;
            letter-spacing: 3px;
            text-transform: uppercase;
            margin-top: 2px;
        }

        .footer-copyright {
            color: #9c897c;
        }

        .footer-socials {
            display: flex;
            gap: 25px;
        }

        .footer-socials a {
            color: var(--text-gold);
            text-decoration: none;
            font-weight: bold;
            transition: transform 0.3s ease, opacity 0.3s ease;
        }

        .footer-socials a:hover {
            transform: translateY(-2px);
            opacity: 0.8;
        }
    </style>
</head>
<body>

    <header>
        <div class="logo-block">
            <div class="logo-emblem">⚖</div>
            <div class="logo-text-wrapper">
                <div class="logo-main">LexCity.</div>
                <div class="logo-slogan">Slogan Here</div>
            </div>
        </div>
        <nav>
            <a href="#" class="active">Home</a>
            <a href="#">Contact</a>
        </nav>
    </header>

    <main>
        <h1 class="hero-title">Trusted Legal Partnerships</h1>
        <p class="hero-subtitle">Legal Excellence, Personalized Service</p>

        <div class="desktop-showcase-container">
            
            <a href="#" class="showcase-card">
                <div class="3d-frame">
                    <img src="https://images.unsplash.com/photo-1505664194779-8beaceb93744?auto=format&fit=crop&q=80&w=600" alt="Corporate Books">
                </div>
                <div class="card-label">Growth Package</div>
            </a>

            <a href="#" class="showcase-card">
                <div class="3d-frame">
                    <img src="https://images.unsplash.com/photo-1450133064473-71024230f91b?auto=format&fit=crop&q=80&w=600" alt="Signing Legal Documents">
                </div>
                <div class="card-label">Estate Planning Suite</div>
            </a>

            <a href="#" class="showcase-card">
                <div class="3d-frame">
                    <img src="https://images.unsplash.com/photo-1589829545856-d10d557cf95f?auto=format&fit=crop&q=80&w=600" alt="Lady Justice Emblem">
                </div>
                <div class="card-label">Data Privacy Defense</div>
            </a>

        </div>
    </main>

    <footer>
        <div class="footer-branding">
            <span class="fb-main">LexCity.</span>
            <span class="fb-sub">Slogan Here</span>
        </div>
        <div class="footer-copyright">
            &copy; 2026 by LexCity. All Rights Reserved.
        </div>
        <div class="footer-socials">
            <a href="#">facebook</a>
            <a href="#">instagram</a>
            <a href="#">X</a>
        </div>
    </footer>

    <script>
        const cards = document.querySelectorAll('.showcase-card');

        cards.forEach(card => {
            card.addEventListener('mousemove', (e) => {
                const rect = card.getBoundingClientRect();
                
                // Track where the mouse cursor is relative to the card's center point
                const x = e.clientX - rect.left - (rect.width / 2);
                const y = e.clientY - rect.top - (rect.height / 2);
                
                // Convert coordinates into subtle rotational degrees (Max 12deg tilt angle)
                const rotateX = -(y / (rect.height / 2)) * 12;
                const rotateY = (x / (rect.width / 2)) * 12;
                
                // Inject real-time spatial calculations back into CSS transforms
                card.style.transform = `scale(1.03) rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
            });

            // Return the element to perfect flatness when user cursor steps away
            card.addEventListener('mouseleave', () => {
                card.style.transform = 'scale(1) rotateX(0deg) rotateY(0deg)';
            });
        });
    </script>

</body>
</html>
