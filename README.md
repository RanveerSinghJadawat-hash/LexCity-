<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LexCity | Civic Justice & Legal Accountability</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Playfair+Display:wght@600;700&display=swap" rel="stylesheet">
    
    <style>
        /* --- DESIGN SYSTEM TOKENS --- */
        :root {
            --primary: #0f172a;       /* Deep Slate/Navy - Trust & Authority */
            --primary-light: #1e293b;
            --accent: #b45309;        /* Muted Amber - Urgent/Action items */
            --accent-hover: #92400e;
            --text-main: #334155;     /* Dark Charcoal for high readability */
            --text-muted: #64748b;    /* Secondary text */
            --bg-light: #f8fafc;      /* Soft off-white to reduce glare */
            --bg-card: #ffffff;
            --border: #e2e8f0;        /* Subtle divider lines */
            --success: #15803d;       /* Professional green for verified states */
            --font-sans: 'Inter', sans-serif;
            --font-serif: 'Playfair Display', serif;
            --shadow: 0 4px 6px -1px rgba(15, 23, 42, 0.05), 0 2px 4px -2px rgba(15, 23, 42, 0.05);
        }

        /* --- BASE STYLES --- */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: var(--font-sans);
            background-color: var(--bg-light);
            color: var(--text-main);
            line-height: 1.7;
            -webkit-font-smoothing: antialiased;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 24px;
        }

        /* --- NAVIGATION --- */
        .navbar {
            background-color: var(--bg-card);
            border-bottom: 1px solid var(--border);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 72px;
        }

        .logo {
            font-family: var(--font-serif);
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary);
            text-decoration: none;
            letter-spacing: -0.01em;
        }

        .nav-links {
            display: flex;
            gap: 32px;
            list-style: none;
            align-items: center;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-muted);
            font-weight: 500;
            font-size: 0.95rem;
            transition: color 0.2s;
        }

        .nav-links a:hover {
            color: var(--primary);
        }

        /* --- BUTTONS --- */
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            padding: 12px 24px;
            border-radius: 6px;
            font-weight: 600;
            font-size: 0.95rem;
            transition: all 0.2s;
            cursor: pointer;
            text-decoration: none;
        }

        .btn-primary {
            background-color: var(--accent);
            color: white;
            border: none;
        }

        .btn-primary:hover {
            background-color: var(--accent-hover);
        }

        .btn-secondary {
            background-color: transparent;
            color: var(--primary);
            border: 1.5px solid var(--primary);
        }

        .btn-secondary:hover {
            background-color: rgba(15, 23, 42, 0.04);
        }

        /* --- HERO SECTION --- */
        .hero {
            background-color: var(--bg-card);
            padding: 96px 0 80px 0;
            border-bottom: 1px solid var(--border);
        }

        .hero-content {
            max-width: 760px;
            margin: 0 auto;
            text-align: center;
        }

        .hero h1 {
            font-family: var(--font-serif);
            font-size: 3rem;
            color: var(--primary);
            line-height: 1.2;
            margin-bottom: 24px;
            letter-spacing: -0.02em;
        }

        .hero p {
            font-size: 1.2rem;
            color: var(--text-muted);
            margin-bottom: 40px;
        }

        .hero-actions {
            display: flex;
            gap: 16px;
            justify-content: center;
        }

        /* --- MAIN DASHBOARD / GRID --- */
        .dashboard {
            padding: 80px 0;
        }

        .section-header {
            margin-bottom: 40px;
            display: flex;
            justify-content: space-between;
            align-items: flex-end;
        }

        .section-header h2 {
            font-family: var(--font-serif);
            font-size: 1.8rem;
            color: var(--primary);
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
            gap: 32px;
        }

        /* --- PROFESSIONAL REPORT CARD --- */
        .card {
            background-color: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 28px;
            box-shadow: var(--shadow);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            transition: transform 0.2s, box-shadow 0.2s;
        }

        .card:hover {
            transform: translateY(-2px);
            box-shadow: 0 12px 16px -4px rgba(15, 23, 42, 0.08);
        }

        .card-tag {
            display: inline-block;
            font-size: 0.75rem;
            text-transform: uppercase;
            font-weight: 700;
            letter-spacing: 0.05em;
            color: var(--accent);
            margin-bottom: 12px;
        }

        .card-title {
            font-size: 1.2rem;
            font-weight: 600;
            color: var(--primary);
            margin-bottom: 12px;
            line-height: 1.4;
        }

        .card-body {
            font-size: 0.95rem;
            color: var(--text-muted);
            margin-bottom: 24px;
        }

        .card-footer {
            border-top: 1px solid var(--border);
            padding-top: 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.85rem;
        }

        .lawyer-badge {
            display: flex;
            align-items: center;
            gap: 6px;
            color: var(--success);
            font-weight: 600;
        }

        .lawyer-badge::before {
            content: "✓";
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 14px;
            height: 14px;
            background-color: rgba(21, 128, 61, 0.1);
            border-radius: 50%;
            font-size: 10px;
        }

        /* --- RESPONSIVE DESIGN --- */
        @media (max-width: 768px) {
            .hero h1 { font-size: 2.2rem; }
            .hero-actions { flex-direction: column; }
            .nav-links { display: none; } /* Simplified for code clarity */
        }
    </style>
</head>
<body>

    <nav class="navbar">
        <div class="container nav-container">
            <a href="#" class="logo">LexCity</a>
            <ul class="nav-links">
                <li><a href="#feed">Active Issues</a></li>
                <li><a href="#lawyers">For Attorneys</a></li>
                <li><a href="#" class="btn btn-primary" style="padding: 8px 16px; font-size: 0.85rem;">File Report</a></li>
            </ul>
        </div>
    </nav>

    <header class="hero">
        <div class="container hero-content">
            <span class="card-tag">Civic Legal Hub</span>
            <h1>Documenting Injustices. Empowering Communities.</h1>
            <p>LexCity bridges the gap between citizens reporting localized systemic issues and verified legal professionals ready to drive institutional accountability.</p>
            <div class="hero-actions">
                <a href="#" class="btn btn-primary">Report an Issue</a>
                <a href="#" class="btn btn-secondary">Attorney Portal</a>
            </div>
        </div>
    </header>

    <main class="container dashboard" id="feed">
        <div class="section-header">
            <div>
                <h2>Recent Community Reports</h2>
                <p style="color: var(--text-muted); font-size: 0.95rem; margin-top: 4px;">Verified local accounts pending review or legally documented.</p>
            </div>
        </div>

        <div class="grid">
            <div class="card">
                <div>
                    <span class="card-tag">Housing / Zoning</span>
                    <h3 class="card-title">Unlawful Eviction Notices Issued in Ward 4</h3>
                    <p class="card-body">Multiple low-income tenants report receiving identical, backdated eviction notices ignoring the statutory 30-day grace period requirement.</p>
                </div>
                <div class="card-footer">
                    <span style="color: var(--text-muted);">2 hours ago</span>
                    <span class="lawyer-badge">Documented by Attorney</span>
                </div>
            </div>

            <div class="card">
                <div>
                    <span class="card-tag">Labor Rights</span>
                    <h3 class="card-title">Systemic Wage Theft at Metro Logistics Hub</h3>
                    <p class="card-body">Contract workers are reporting uncompensated mandatory overtime hours and structural delays on final payroll processing.</p>
                </div>
                <div class="card-footer">
                    <span style="color: var(--text-muted);">1 day ago</span>
                    <span style="color: var(--accent); font-weight: 500;">Review Pending</span>
                </div>
            </div>

            <div class="card">
                <div>
                    <span class="card-tag">Environmental</span>
                    <h3 class="card-title">Industrial Runoff Violations near District Creek</h3>
                    <p class="card-body">Local residents documented illegal nighttime waste discharges from manufacturing facilities without appropriate permits.</p>
                </div>
                <div class="card-footer">
                    <span style="color: var(--text-muted);">3 days ago</span>
                    <span class="lawyer-badge">Case Opened</span>
                </div>
            </div>
        </div>
    </main>

</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LexCity</title>
    <style>
        /* --- DESIGN SYSTEM TOKENS --- */
        :root {
            --primary: #0f172a;       /* Deep Slate */
            --primary-light: #1e293b;
            --accent: #b45309;        /* Muted Amber */
            --accent-hover: #92400e;
            --text-main: #334155;     /* Dark Gray */
            --text-muted: #64748b;    /* Secondary Gray */
            --bg-light: #f8fafc;      /* Soft Off-White */
            --bg-card: #ffffff;
            --border: #e2e8f0;        /* Subtle Border */
            --success: #15803d;       /* Professional Green */
            --font-sans: 'Inter', sans-serif;
            --font-serif: 'Playfair Display', serif;
            --shadow: 0 4px 6px -1px rgba(15, 23, 42, 0.1);
        }

        /* --- BASE STYLES --- */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: var(--font-sans);
            background-color: var(--bg-light);
            color: var(--text-main);
            line-height: 1.7;
            -webkit-font-smoothing: antialiased;
        }

        /* --- SIGN UP SCREEN OVERLAY --- */
        #auth-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: var(--bg-light);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999; /* Keeps it on top of everything */
            padding: 20px;
            transition: opacity 0.4s ease, visibility 0.4s ease;
        }

        .auth-card {
            background-color: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 2.5rem;
            width: 100%;
            max-width: 420px;
            box-shadow: var(--shadow);
        }

        .auth-title {
            font-family: var(--font-serif);
            color: var(--primary);
            font-size: 1.75rem;
            margin-bottom: 0.5rem;
            text-align: center;
        }

        .auth-subtitle {
            color: var(--text-muted);
            font-size: 0.875rem;
            margin-bottom: 2rem;
            text-align: center;
        }

        /* --- FORM ELEMENTS --- */
        .form-group {
            margin-bottom: 1.25rem;
        }

        .form-label {
            display: block;
            font-size: 0.875rem;
            font-weight: 500;
            color: var(--primary);
            margin-bottom: 0.5rem;
        }

        .form-input {
            width: 100%;
            padding: 0.75rem 1rem;
            font-family: var(--font-sans);
            font-size: 0.95rem;
            border: 1px solid var(--border);
            border-radius: 6px;
            background-color: #ffffff;
            color: var(--text-main);
            transition: border-color 0.2s ease, box-shadow 0.2s ease;
        }

        .form-input:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 3px rgba(180, 83, 9, 0.15);
        }

        /* --- BUTTONS & LINKS --- */
        .btn-submit {
            width: 100%;
            padding: 0.75rem;
            background-color: var(--accent);
            color: #ffffff;
            border: none;
            border-radius: 6px;
            font-family: var(--font-sans);
            font-size: 1rem;
            font-weight: 500;
            cursor: pointer;
            transition: background-color 0.2s ease;
            margin-top: 0.5rem;
        }

        .btn-submit:hover {
            background-color: var(--accent-hover);
        }

        .auth-footer {
            text-align: center;
            margin-top: 1.5rem;
            font-size: 0.875rem;
            color: var(--text-muted);
        }

        .auth-link {
            color: var(--accent);
            text-decoration: none;
            font-weight: 500;
        }

        /* --- MAIN WEBSITE CONTENT --- */
        .main-website {
            padding: 40px;
            max-width: 800px;
            margin: 0 auto;
        }
        
        .welcome-title {
            font-family: var(--font-serif);
            color: var(--primary);
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }
    </style>
</head>
<body>

    <div id="auth-overlay">
        <div class="auth-card">
            <h2 class="auth-title">Create an Account</h2>
            <p class="auth-subtitle">Join LexCity to get started</p>
            
            <form id="signup-form" onsubmit="unlockWebsite(event)">
                <div class="form-group">
                    <label for="fullname" class="form-label">Full Name</label>
                    <input type="text" id="fullname" class="form-input" placeholder="John Doe" required>
                </div>
                
                <div class="form-group">
                    <label for="email" class="form-label">Email Address</label>
                    <input type="email" id="email" class="form-input" placeholder="you@example.com" required>
                </div>
                
                <div class="form-group">
                    <label for="password" class="form-label">Password</label>
                    <input type="password" id="password" class="form-input" placeholder="••••••••" required>
                </div>
                
                <button type="submit" class="btn-submit">Sign Up</button>
            </form>
            
            <div class="auth-footer">
                Already have an account? <a href="#" class="auth-link">Log in</a>
            </div>
        </div>
    </div>

    <div class="main-website">
        <h1 class="welcome-title">Welcome to LexCity!</h1>
        <p>This is your main dashboard or landing page content. It only reveals itself after a user successfully submits the sign-up form above.</p>
    </div>

    <script>
        function unlockWebsite(event) {
            // Prevent the page from reloading instantly
            event.preventDefault(); 
            
            // Hide the sign-up screen smoothly
            const overlay = document.getElementById('auth-overlay');
            overlay.style.opacity = '0';
            overlay.style.visibility = 'hidden';
            
            alert("Account created successfully! Welcome to the site.");
        }
    </script>

</body>
</html>
/* --- THE FIX FOR HORIZONTAL STRETCHING --- */
.main-website {
    width: 100%;
    max-width: 650px;       /* Keeps the text from stretching too wide */
    margin: 0 auto;         /* Perfectly centers the content on the screen */
    padding: 40px 20px;     /* Adds breathing room on the sides for mobile */
    display: flex;
    flex-direction: column; /* Stacks everything neatly from top to bottom */
    gap: 20px;              /* Adds clean spacing between elements */
}

/* This forces extra vertical space so you can actually test the scrolling */
.scroll-space {
    margin-top: 40px;
    padding: 30px;
    background-color: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: 8px;
    box-shadow: var(--shadow);
}
