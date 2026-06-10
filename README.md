<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lexcity - Civic Legal Hub</title>
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
            display: flex;
            flex-direction: column;
            min-height: 100vh;
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

        /* Main Content Section Wrapper */
        .main-content {
            padding: 60px 80px 80px 80px;
            max-width: 1400px;
            margin: 0 auto;
            width: 100%;
        }

        .hero-header {
            text-align: center;
            margin-bottom: 40px;
        }

        .hero-title {
            font-size: 44px;
            font-weight: 700;
            color: #2b2321;
            margin-bottom: 10px;
        }

        .hero-subtitle {
            font-size: 18px;
            color: #443734;
            font-weight: 400;
        }

        /* --- NEW: Civic Legal Hub Action Section --- */
        .civic-hub-section {
            background-color: #fcfbfa; /* Off-white background matching the image */
            border-radius: 8px;
            padding: 50px 40px;
            text-align: center;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
            margin-bottom: 60px;
            width: 100%;
        }

        .hub-tagline {
            color: #b06330; /* Rust/orange accent color */
            font-size: 13px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 20px;
        }

        .hub-main-statement {
            font-family: 'Georgia', serif; /* Serif font for dramatic emphasis */
            font-size: 32px;
            color: #1a1514;
            font-weight: 500;
            line-height: 1.3;
            max-width: 800px;
            margin: 0 auto 25px auto;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .hub-divider {
            border: 0;
            height: 1px;
            background: #e6e3df;
            max-width: 700px;
            margin: 0 auto 25px auto;
        }

        .hub-description {
            font-size: 16px;
            color: #574c49;
            line-height: 1.6;
            max-width: 750px;
            margin: 0 auto 35px auto;
        }

        .button-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 15px;
        }

        .btn {
            width: 100%;
            max-width: 320px;
            padding: 14px 20px;
            font-size: 14px;
            font-weight: 700;
            letter-spacing: 2px;
            text-transform: uppercase;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .btn-report {
            background-color: #b06330; /* Rust orange fill */
            color: #ffffff;
            border: none;
        }

        .btn-report:hover {
            background-color: #945125;
            box-shadow: 0 4px 12px rgba(176, 99, 48, 0.3);
        }

        .btn-portal {
            background-color: transparent;
            color: #111625; /* Very dark blue/black text */
            border: 2px solid #111625;
        }

        .btn-portal:hover {
            background-color: #111625;
            color: #ffffff;
        }
        /* --- End of Action Section --- */

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
                gap: 40px;
            }
            header, .main-content, footer {
                padding-left: 40px;
                padding-right: 40px;
            }
            .hero-title {
                font-size: 36px;
            }
            .hub-main-statement {
                font-size: 24px;
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
        
        <div class="hero-header">
            <h1 class="hero-title">Trusted Legal Partnerships</h1>
            <p class="hero-subtitle">Legal Excellence, Personalized Service</p>
        </div>

        <section class="civic-hub-section">
            <div class="hub-tagline">Civic Legal Hub</div>
            <h2 class="hub-main-statement">Documenting Injustices. Empowering Communities.</h2>
            <hr class="hub-divider">
            <p class="hub-description">
                LexCity bridges the gap between citizens reporting localized systemic issues and verified legal professionals ready to drive institutional accountability.
            </p>
            <div class="button-container">
                <button class="btn btn-report" onclick="handleReportSubmit()">Report an Issue</button>
                <button class="btn btn-portal" onclick="handlePortalRedirect()">Attorney Portal</button>
            </div>
        </section>

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

    <script>
        function handleReportSubmit() {
            alert("Redirecting you to the Issue Reporting form system...");
            // You can replace this alert with a real link: 
            // window.location.href = "/report-form.html";
        }

        function handlePortalRedirect() {
            alert("Opening Secure Attorney Login Portal...");
            // You can replace this alert with a real link: 
            // window.location.href = "/attorney-login.html";
        }
    </script>

</body>
</html>

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
