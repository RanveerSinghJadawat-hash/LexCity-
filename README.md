<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lexcity - Trusted Legal Partnerships</title>
    <style>
        /* Reset and Base Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
        }

        body {
            background-color: #d1b48c; /* Warm tan/gold color */
            color: #2b2321; /* Dark brown for text */
        }

        /* Header Styles */
        header {
            background-color: #2b2321; /* Deep chocolate brown */
            padding: 20px 80px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo-container {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
        }

        .logo-icon {
            color: #d1b48c;
            font-size: 24px;
            margin-bottom: 4px;
        }

        .brand-name {
            color: #d1b48c;
            font-size: 20px;
            font-weight: bold;
            letter-spacing: 2px;
            text-transform: uppercase;
        }

        .slogan {
            color: #a89275;
            font-size: 10px;
            letter-spacing: 3px;
            text-transform: uppercase;
            margin-top: 2px;
        }

        nav a {
            color: #ffffff;
            text-decoration: none;
            margin-left: 30px;
            font-size: 16px;
            transition: color 0.3s ease;
        }

        nav a:hover, nav a.active {
            color: #d1b48c;
            border-bottom: 2px solid #d1b48c;
            padding-bottom: 4px;
        }

        /* Main Hero & Content Section */
        .main-content {
            padding: 80px 80px 100px 80px;
            max-width: 1400px;
            margin: 0 auto;
        }

        .hero-title {
            font-size: 48px;
            font-weight: 700;
            color: #2b2321;
            margin-bottom: 15px;
        }

        .hero-subtitle {
            font-size: 20px;
            color: #443734;
            margin-bottom: 60px;
            font-weight: 400;
        }

        /* Grid / Cards Section */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 40px;
        }

        .card {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .card-image-wrapper {
            width: 100%;
            height: 250px;
            overflow: hidden;
            border-radius: 4px;
            margin-bottom: 20px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.15);
        }

        .card-image-wrapper img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.3s ease;
        }

        .card-image-wrapper img:hover {
            transform: scale(1.03);
        }

        .card-title {
            font-size: 18px;
            color: #2b2321;
            font-weight: 500;
            text-align: center;
        }

        /* Footer Styles */
        footer {
            background-color: #2b2321;
            padding: 40px 80px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: auto;
        }

        .footer-copyright {
            color: #a89275;
            font-size: 14px;
        }

        .social-links a {
            color: #a89275;
            text-decoration: none;
            margin-left: 20px;
            font-size: 16px;
            transition: color 0.3s ease;
        }

        .social-links a:hover {
            color: #ffffff;
        }

        /* Responsive Design */
        @media (max-width: 992px) {
            .services-grid {
                grid-template-columns: 1fr;
                gap: 50px;
            }
            header, .main-content, footer {
                padding-left: 40px;
                padding-right: 40px;
            }
            .hero-title {
                font-size: 36px;
            }
        }
    </style>
</head>
<body>

    <header>
        <div class="logo-container">
            <div class="logo-icon">⚖</div>
            <div class="brand-name">Lexcity.</div>
            <div class="slogan">Slogan Here</div>
        </div>
        <nav>
            <a href="#" class="active">Home</a>
            <a href="#">Contact</a>
        </nav>
    </header>

    <main class="main-content">
        <h1 class="hero-title">Trusted Legal Partnerships</h1>
        <p class="hero-subtitle">Legal Excellence, Personalized Service</p>

        <div class="services-grid">
            <div class="card">
                <div class="card-image-wrapper">
                    <img src="https://images.unsplash.com/photo-1505664194779-8beaceb93744?auto=format&fit=crop&w=600&q=80" alt="Law books on shelf">
                </div>
                <h3 class="card-title">Growth Package</h3>
            </div>

            <div class="card">
                <div class="card-image-wrapper">
                    <img src="https://images.unsplash.com/photo-1450133064473-71024230f91b?auto=format&fit=crop&w=600&q=80" alt="Signing legal documents">
                </div>
                <h3 class="card-title">Estate Planning Suite</h3>
            </div>

            <div class="card">
                <div class="card-image-wrapper">
                    <img src="https://images.unsplash.com/photo-1589829545856-d10d557cf95f?auto=format&fit=crop&w=600&q=80" alt="Lady Justice Statue">
                </div>
                <h3 class="card-title">Data Privacy Defense</h3>
            </div>
        </div>
    </main>

    <footer>
        <div class="logo-container">
            <div class="brand-name" style="font-size: 16px;">Lexcity.</div>
            <div class="slogan" style="font-size: 8px;">Slogan Here</div>
        </div>
        <div class="footer-copyright">
            &copy; 2026 by Lexcity. All Rights Reserved.
        </div>
        <div class="social-links">
            <a href="#" aria-label="Facebook">f</a>
            <a href="#" aria-label="Instagram">i</a>
            <a href="#" aria-label="X">X</a>
        </div>
    </footer>

</body>
</html>
