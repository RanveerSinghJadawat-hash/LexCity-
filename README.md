<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lexcity - Trusted Legal Partnerships</title>
    <style>
        /* Global Variables for Exact Brand Palette */
        :root {
            --dark-chocolate: #382d26;
            --premium-gold: #d7b57c;
            --gold-shadow: #b2935e;
            --text-dark: #221a15;
            --white-glow: rgba(255, 255, 255, 0.15);
        }

        /* Base Configuration */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            font-family: 'Times New Roman', Times, serif; /* Gives the classic legal look */
            background-color: var(--dark-chocolate);
            color: var(--premium-gold);
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }

        /* --- 1. HEADER COMPONENT --- */
        header {
            background-color: var(--dark-chocolate);
            padding: 20px 8%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid var(--premium-gold);
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.4);
        }

        .logo-area {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
        }

        /* 3D Scale Emblem Simulated placeholder */
        .logo-icon {
            font-size: 2rem;
            line-height: 1;
            margin-bottom: 4px;
            text-shadow: 0 2px 4px rgba(0,0,0,0.5);
        }

        .logo-text {
            font-size: 1.6rem;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 2px;
            /* 3D Chiseled Text Effect */
            text-shadow: 1px 1px 0px var(--gold-shadow), 2px 2px 3px rgba(0,0,0,0.6);
        }

        .logo-slogan {
            font-size: 0.75rem;
            letter-spacing: 3px;
            text-transform: uppercase;
            opacity: 0.8;
            margin-top: -2px;
        }

        nav a {
            color: var(--premium-gold);
            text-decoration: none;
            font-size: 1.1rem;
            margin-left: 25px;
            padding-bottom: 4px;
            transition: all 0.3s ease;
            text-shadow: 1px 1px 1px rgba(0,0,0,0.5);
        }

        nav a.active {
            border-bottom: 2px solid var(--premium-gold);
            text-shadow: 0px 0px 8px var(--white-glow);
        }

        nav a:hover {
            opacity: 0.8;
        }

        /* --- 2. MAIN 3D DISPLAY MODULE --- */
        main {
            background-color: var(--premium-gold);
            color: var(--text-dark);
            padding: 60px 8%;
            flex-grow: 1;
            /* Recessed Bevel Frame effect around the golden center core */
            box-shadow: 
                inset 0 10px 20px rgba(0,0,0,0.3), 
                inset 0 -10px 20px rgba(0,0,0,0.3),
                0 10px 30px rgba(0,0,0,0.5);
            border-top: 4px solid #f3dcaf;
            border-bottom: 4px solid #a3814c;
        }

        .hero-title {
            font-size: 3rem;
            font-weight: bold;
            margin: 0 0 10px 0;
            letter-spacing: 1px;
            /* Sculpted dark 3D text styling */
            text-shadow: 
                0 1px 0px #edd8b4,
                1px 2px 0px #cbb082,
                2px 3px 1px #91784f,
                3px 5px 6px rgba(0,0,0,0.4);
        }

        .hero-subtitle {
            font-size: 1.4rem;
            font-style: italic;
            margin: 0 0 50px 0;
            color: #403229;
        }

        /* Grid Configuration for Showcase Cards */
        .showcase-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 40px;
            /* Prepares parent container viewport for proper 3D transformations */
            perspective: 1000px; 
        }

        .showcase-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            /* Enables native 3D interaction parameters */
            transform-style: preserve-3d;
            transition: transform 0.5s cubic-bezier(0.25, 1, 0.5, 1), box-shadow 0.5s ease;
        }

        .image-frame {
            width: 100%;
            aspect-ratio: 1.5 / 1;
            border-radius: 8px;
            overflow: hidden;
            background-color: #221a15;
            /* Box frame depth shadow mapping */
            box-shadow: 
                0 15px 35px rgba(0,0,0,0.35),
                inset 0 0 15px rgba(0,0,0,0.6);
            border: 1px solid rgba(255,255,255,0.2);
            margin-bottom: 20px;
        }

        .image-frame img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block;
            opacity: 0.9;
            transition: transform 0.5s ease;
        }

        .item-label {
            font-size: 1.15rem;
            font-weight: 600;
            color: var(--text-dark);
            letter-spacing: 0.5px;
            text-shadow: 0 1px 1px rgba(255,255,255,0.5);
        }

        /* --- INTERACTIVE 3D EFFECTS ON HOVER --- */
        .showcase-item:hover {
            /* Tilts card upward slightly and lifts off surface space */
            transform: translateY(-10px) rotateX(6deg) scale(1.02);
            box-shadow: 0 25px 40px rgba(0,0,0,0.3);
        }

        .showcase-item:hover .image-frame img {
            transform: scale(1.06); /* Subtle internal zoom */
        }


        /* --- 3. EXECUTIVE FOOTER --- */
        footer {
            background-color: var(--dark-chocolate);
            padding: 30px 8%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-top: 1px solid rgba(215, 181, 124, 0.3);
            font-size: 0.9rem;
        }

        .footer-logo {
            display: flex;
            flex-direction: column;
            opacity: 0.8;
        }

        .footer-logo .f-title {
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1.5px;
        }

        .footer-logo .f-sub {
            font-size: 0.65rem;
            letter-spacing: 2px;
            text-transform: uppercase;
        }

        .copyright {
            color: #a29185;
        }

        .social-links {
            display: flex;
            gap: 20px;
        }

        .social-links a {
            color: var(--premium-gold);
            text-decoration: none;
            font-size: 1.2rem;
            transition: transform 0.3s ease;
        }

        .social-links a:hover {
            transform: scale(1.2);
        }

        /* Responsive Breakpoint layout configurations for Mobile screens */
        @media (max-width: 768px) {
            header, footer {
                flex-direction: column;
                gap: 20px;
                text-align: center;
            }
            .logo-area, .footer-logo {
                align-items: center;
            }
            nav {
                margin-top: 10px;
            }
            nav a {
                margin: 0 10px;
            }
            .hero-title {
                font-size: 2.2rem;
            }
        }
    </style>
</head>
<body>

    <header>
        <div class="logo-area">
            <div class="logo-icon">⚖</div>
            <div class="logo-text">LexCity.</div>
            <div class="logo-slogan">Slogan Here</div>
        </div>
        <nav>
            <a href="#" class="active">Home</a>
            <a href="#">Contact</a>
        </nav>
    </header>

    <main>
        <h1 class="hero-title">Trusted Legal Partnerships</h1>
        <p class="hero-subtitle">Legal Excellence, Personalized Service</p>

        <div class="showcase-grid">
            
            <div class="showcase-item">
                <div class="image-frame">
                    <img src="https://images.unsplash.com/photo-1505664194779-8beaceb93744?auto=format&fit=crop&q=80&w=600" alt="Law Bookshelf">
                </div>
                <div class="item-label">Growth Package</div>
            </div>

            <div class="showcase-item">
                <div class="image-frame">
                    <img src="https://images.unsplash.com/photo-1450133064473-71024230f91b?auto=format&fit=crop&q=80&w=600" alt="Signing Contract Documents">
                </div>
                <div class="item-label">Estate Planning Suite</div>
            </div>

            <div class="showcase-item">
                <div class="image-frame">
                    <img src="https://images.unsplash.com/photo-1589829545856-d10d557cf95f?auto=format&fit=crop&q=80&w=600" alt="Lady Justice Statue">
                </div>
                <div class="item-label">Data Privacy Defense</div>
            </div>

        </div>
    </main>

    <footer>
        <div class="footer-logo">
            <span class="f-title">LexCity.</span>
            <span class="f-sub">Slogan Here</span>
        </div>
        <div class="copyright">
            &copy; 2026 by LexCity. All Rights Reserved.
        </div>
        <div class="social-links">
            <a href="#" title="Facebook">facebook</a>
            <a href="#" title="Instagram">instagram</a>
            <a href="#" title="X">X</a>
        </div>
    </footer>

</body>
</html>
