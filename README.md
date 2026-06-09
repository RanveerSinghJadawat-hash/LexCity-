<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LexCity - Trusted Legal Partnerships</title>
    <style>
        /* Exact Brand Palette Colors */
        :root {
            --dark-chocolate: #3a2e2b; /* Top and bottom background colors */
            --warm-tan: #d9b480;       /* Main center background color */
            --text-dark: #2c2523;       /* Main heading and text color */
            --text-gold: #d9b480;       /* Logo and nav text color */
            --text-muted: #918179;     /* Copyright text color */
        }

        /* Base Settings */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            min-height: 100vh;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--dark-chocolate);
            display: flex;
            flex-direction: column;
        }

        /* --- 1. NAVBAR HEADER --- */
        header {
            background-color: var(--dark-chocolate);
            padding: 30px 10%;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
        }

        /* Inline SVG Scales of Justice Icon matching your design logo */
        .logo-icon {
            width: 60px;
            height: auto;
            margin-bottom: 5px;
        }

        .logo-icon path {
            fill: var(--text-gold);
        }

        .logo-title {
            color: var(--text-gold);
            font-size: 1.25rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 2px;
            line-height: 1.2;
        }

        .logo-slogan {
            color: var(--text-gold);
            font-size: 0.65rem;
            text-transform: uppercase;
            letter-spacing: 3px;
            opacity: 0.9;
            margin-top: 2px;
        }

        /* Navigation menu settings */
        nav {
            display: flex;
            gap: 25px;
        }

        nav a {
            color: var(--text-gold);
            text-decoration: none;
            font-size: 1.05rem;
            padding-bottom: 6px;
            letter-spacing: 0.5px;
            transition: opacity 0.2s ease;
        }

        nav a.active {
            border-bottom: 2px solid var(--text-gold);
        }

        nav a:hover {
            opacity: 0.8;
        }

        /* --- 2. MAIN CORE SECTION --- */
        main {
            background-color: var(--warm-tan);
            color: var(--text-dark);
            padding: 70px 10% 90px 10%;
            flex-grow: 1;
        }

        .hero-title {
            font-size: 3.4rem;
            font-weight: 700;
            margin: 0 0 12px 0;
            letter-spacing: -0.5px;
        }

        .hero-subtitle {
            font-size: 1.4rem;
            margin: 0 0 50px 0;
            font-weight: 400;
            opacity: 0.9;
        }

        /* 3-Column Desktop Grid layout */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 30px;
            width: 100%;
        }

        .service-card {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
        }

        .image-wrapper {
            width: 100%;
            aspect-ratio: 1.53 / 1; /* Retains widescreen thumbnail proportion */
            border-radius: 6px;
            overflow: hidden;
            margin-bottom: 20px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.15);
        }

        .image-wrapper img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block;
        }

        .card-title {
            font-size: 1.15rem;
            font-weight: 500;
            color: var(--text-dark);
            letter-spacing: 0.2px;
        }

        /* --- 3. FOOTER SECTION --- */
        footer {
            background-color: var(--dark-chocolate);
            padding: 35px 10%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: auto;
        }

        .footer-logo {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .footer-logo .logo-title {
            font-size: 1.1rem;
        }

        .footer-logo .logo-slogan {
            font-size: 0.55rem;
        }

        .copyright-text {
            color: var(--text-muted);
            font-size: 0.95rem;
            letter-spacing: 0.3px;
        }

        /* Social media icon group symbols matching layout positioning */
        .social-container {
            display: flex;
            gap: 25px;
            align-items: center;
        }

        .social-container a {
            color: var(--text-gold);
            text-decoration: none;
            transition: opacity 0.2s ease;
        }

        .social-container a:hover {
            opacity: 0.7;
        }

        .social-icon {
            width: 18px;
            height: 18px;
            fill: var(--text-gold);
        }
    </style>
</head>
<body>

    <header>
        <div class="logo-container">
            <svg class="logo-icon" viewBox="0 0 24 24">
                <path d="M12,2A2,2 0 0,1 14,4C14,4.74 13.6,5.39 13,5.73V7H18.5A2.5,2.5 0 0,1 21,9.5V10H22V12H21V19A3,3 0 0,1 18,22H6A3,3 0 0,1 3,19V12H2V10H3V9.5A2.5,2.5 0 0,1 5.5,7H11V5.73C10.4,5.39 10,4.74 10,4A2,2 0 0,1 12,2M18.5,8.5H13V10H20.47C20.21,9.15 19.43,8.5 18.5,8.5M5.5,8.5C4.57,8.5 3.79,9.15 3.53,10H11V8.5H5.5M5,12V13H11V12H5M19,12H13V13H19V12M5,14.5V15.5H11V14.5H5M19,14.5H13V15.5H19V14.5M5,17V18H11V17H5M19,17H13V18H19V17Z"/>
            </svg>
            <div class="logo-title">LexCity.</div>
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

        <div class="services-grid">
            
            <div class="service-card">
                <div class="image-wrapper">
                    <img src="https://images.unsplash.com/photo-1505664194779-8beaceb93744?auto=format&fit=crop&q=80&w=600" alt="Growth Package - Law Books">
                </div>
                <div class="card-title">Growth Package</div>
            </div>

            <div class="service-card">
                <div class="image-wrapper">
                    <img src="https://images.unsplash.com/photo-1450133064473-71024230f91b?auto=format&fit=crop&q=80&w=600" alt="Estate Planning Suite - Signature">
                </div>
                <div class="card-title">Estate Planning Suite</div>
            </div>

            <div class="service-card">
                <div class="image-wrapper">
                    <img src="https://images.unsplash.com/photo-1589829545856-d10d557cf95f?auto=format&fit=crop&q=80&w=600" alt="Data Privacy Defense - Lady Justice">
                </div>
                <div class="card-title">Data Privacy Defense</div>
            </div>

        </div>
    </main>

    <footer>
        <div class="footer-logo">
            <svg class="logo-icon" style="width:45px; margin-bottom:2px;" viewBox="0 0 24 24">
                <path d="M12,2A2,2 0 0,1 14,4C14,4.74 13.6,5.39 13,5.73V7H18.5A2.5,2.5 0 0,1 21,9.5V10H22V12H21V19A3,3 0 0,1 18,22H6A3,3 0 0,1 3,19V12H2V10H3V9.5A2.5,2.5 0 0,1 5.5,7H11V5.73C10.4,5.39 10,4.74 10,4A2,2 0 0,1 12,2M18.5,8.5H13V10H20.47C20.21,9.15 19.43,8.5 18.5,8.5M5.5,8.5C4.57,8.5 3.79,9.15 3.53,10H11V8.5H5.5M5,12V13H11V12H5M19,12H13V13H19V12M5,14.5V15.5H11V14.5H5M19,14.5H13V15.5H19V14.5M5,17V18H11V17H5M19,17H13V18H19V17Z"/>
            </svg>
            <div class="logo-title">LexCity.</div>
            <div class="logo-slogan">Slogan Here</div>
        </div>
        
        <div class="copyright-text">
            &copy; 2026 by LexCity. All Rights Reserved.
        </div>

        <div class="social-container">
            <a href="#" aria-label="Facebook">
                <svg class="social-icon" viewBox="0 0 24 24"><path d="M9 8H7v3h2v9h3v-9h3l.5-3H12V6c0-.88.72-1 1-1h2V2h-3a4 4 0 0 0-4 4v2z"/></svg>
            </a>
            <a href="#" aria-label="Instagram">
                <svg class="social-icon" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.051.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zM12 16a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm6.406-11.845a1.44 1.44 0 1 0 0 2.881 1.44 1.44 0 0 0 0-2.881z"/></svg>
            </a>
            <a href="#" aria-label="X">
                <svg class="social-icon" viewBox="0 0 24 24"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
            </a>
        </div>
    </footer>

</body>
</html>
