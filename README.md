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
/* Container for your "Recent Community Reports" articles */
.report-cards-container {
    display: flex;
    flex-direction: column; /* Force articles to stack BELOW each other */
    gap: 1.25rem;           /* Clean spacing between stacked articles */
    width: 100%;
}

.auth-card, .report-card {
    width: 100%;            /* Keeps them perfectly slim to fit mobile screens */
    max-width: 100%;
    box-sizing: border-box; /* Prevents padding from forcing horizontal stretch */
}
display: flex;
flex-direction: column; /* This will force them to stack down instead of going sideways */
width: 100%;
gap: 1.5rem;            /* Puts clean spacing between the stacked cards */
<div class="about-container">
    <div class="about-card">
        <div class="founder-badge">Founder & CEO</div>
        <h2 class="about-title">About the Creator</h2>
        <p class="about-text">
            As the Founder and CEO of LexCity, my goal is to reshape how our communities handle institutional and systemic issues. LexCity was born out of a necessity to empower individuals and give them a voice where they are often left unheard.
        </p>

        <h2 class="about-title" style="margin-top: 1.5rem;">Our Motive</h2>
        <p class="about-text">
            The fundamental motive of LexCity is to bridge the gap between citizens reporting localized systemic injustices and verified legal professionals. We exist to transform raw community reports into legally documented evidence, providing a transparent, secure channel that holds power accountable and drives real institutional change.
        </p>
    </div>
</div>

<style>
    /* --- ABOUT & MOTIVE MOBILE-FIRST STYLES --- */
    .about-container {
        width: 100%;
        margin: 3rem 0 2rem 0;
        padding: 0 10px; /* Prevents text from touching phone screen edges */
        box-sizing: border-box;
    }

    .about-card {
        background-color: var(--bg-card, #ffffff);
        border: 1px solid var(--border, #e2e8f0);
        border-radius: 8px;
        padding: 2rem 1.5rem;
        box-shadow: var(--shadow, 0 4px 6px -1px rgba(15, 23, 42, 0.1));
        position: relative;
    }

    .founder-badge {
        display: inline-block;
        background-color: var(--accent, #b45309);
        color: #ffffff;
        font-family: var(--font-sans), sans-serif;
        font-size: 0.75rem;
        font-weight: 700;
        text-transform: uppercase;
        padding: 4px 10px;
        border-radius: 4px;
        margin-bottom: 0.75rem;
        letter-spacing: 0.05em;
    }

    .about-title {
        font-family: var(--font-serif), serif;
        color: var(--primary, #0f172a);
        font-size: 1.4rem;
        margin-bottom: 0.75rem;
    }

    .about-text {
        color: var(--text-main, #334155);
        font-family: var(--font-sans), sans-serif;
        font-size: 0.95rem;
        line-height: 1.6;
        margin-bottom: 1rem;
    }

    .about-text:last-child {
        margin-bottom: 0;
    }
</style>
<div id="report-modal" class="modal-overlay">
    <div class="modal-card">
        <button class="modal-close" onclick="closeReportModal()">&times;</button>
        <h2 class="modal-title">Submit a Community Report</h2>
        <p class="modal-subtitle">Provide details regarding the localized systemic issue.</p>
        
        <form id="issue-form" onsubmit="handleFormSubmit(event)">
            <div class="form-group">
                <label class="form-label" for="issue-category">Category</label>
                <select id="issue-category" class="form-input" required>
                    <option value="HOUSING / ZONING">Housing / Zoning</option>
                    <option value="LABOR RIGHTS">Labor Rights</option>
                    <option value="ENVIRONMENTAL">Environmental</option>
                    <option value="CIVIL RIGHTS">Civil Rights</option>
                </select>
            </div>
            
            <div class="form-group">
                <label class="form-label" for="issue-title">Issue Title</label>
                <input type="text" id="issue-title" class="form-input" placeholder="e.g., Unlawful Eviction Notices Issued in Ward 4" required>
            </div>
            
            <div class="form-group">
                <label class="form-label" for="issue-description">Description</label>
                <textarea id="issue-description" class="form-input" rows="4" placeholder="Describe the systemic issue and its impact on the community..." required></textarea>
            </div>
            
            <button type="submit" class="btn-submit-report">Submit Report</button>
        </form>
    </div>
</div>

<style>
    /* Modal Background Overlay */
    .modal-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(15, 23, 42, 0.6); /* Translucent dark slate */
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 10000;
        padding: 20px;
        box-sizing: border-box;
        opacity: 0;
        visibility: hidden;
        transition: opacity 0.3s ease, visibility 0.3s ease;
    }

    /* Active class to show modal */
    .modal-overlay.active {
        opacity: 1;
        visibility: visible;
    }

    .modal-card {
        background-color: var(--bg-card, #ffffff);
        border: 1px solid var(--border, #e2e8f0);
        border-radius: 8px;
        padding: 2rem 1.5rem;
        width: 100%;
        max-width: 450px;
        box-shadow: var(--shadow);
        position: relative;
    }

    .modal-close {
        position: absolute;
        top: 1rem;
        right: 1.25rem;
        background: none;
        border: none;
        font-size: 1.75rem;
        color: var(--text-muted, #64748b);
        cursor: pointer;
    }

    .modal-title {
        font-family: var(--font-serif), serif;
        color: var(--primary, #0f172a);
        font-size: 1.5rem;
        margin-bottom: 0.25rem;
    }

    .modal-subtitle {
        color: var(--text-muted, #64748b);
        font-size: 0.875rem;
        margin-bottom: 1.5rem;
    }

    .btn-submit-report {
        width: 100%;
        padding: 0.75rem;
        background-color: var(--accent, #b45309);
        color: #ffffff;
        border: none;
        border-radius: 6px;
        font-family: var(--font-sans), sans-serif;
        font-size: 1rem;
        font-weight: 500;
        cursor: pointer;
        transition: background-color 0.2s ease;
    }

    .btn-submit-report:hover {
        background-color: var(--accent-hover, #92400e);
    }
</style>

<script>
    // 1. Hook up your existing "Report an Issue" button
    document.addEventListener("DOMContentLoaded", function() {
        // Find the button that contains the text "Report an Issue"
        const reportBtn = Array.from(document.querySelectorAll('button, a')).find(el => el.textContent.trim() === 'Report an Issue');
        
        if(reportBtn) {
            // Overwrite its action to open our modal popup
            reportBtn.addEventListener('click', function(e) {
                e.preventDefault();
                document.getElementById('report-modal').classList.add('active');
            });
        }
    });

    // 2. Functions to control modal closure
    function closeReportModal() {
        document.getElementById('report-modal').classList.remove('active');
        document.getElementById('issue-form').reset();
    }

    // 3. Handle when a user submits their new issue
    function handleFormSubmit(event) {
        event.preventDefault();
        
        const category = document.getElementById('issue-category').value;
        const title = document.getElementById('issue-title').value;
        const description = document.getElementById('issue-description').value;
        
        // Find your existing container where the other cards sit
        // We'll look for standard container names or inject it near the top
        const reportsContainer = document.querySelector('.report-cards-container') || document.querySelector('[class*="card"]').parentElement;
        
        if (reportsContainer) {
            // Build a matching card element HTML structure
            const newCardHtml = `
                <div class="report-card" style="background: var(--bg-card, #fff); border: 1px solid var(--border, #e2e8f0); border-radius: 8px; padding: 1.5rem; margin-bottom: 1.25rem; box-shadow: var(--shadow);">
                    <span style="font-size: 0.75rem; font-weight: 700; color: var(--accent, #b45309); text-transform: uppercase; letter-spacing: 0.05em;">${category}</span>
                    <h3 style="font-family: var(--font-serif), serif; color: var(--primary, #0f172a); font-size: 1.2rem; margin: 0.5rem 0;">${title}</h3>
                    <p style="color: var(--text-main, #334155); font-size: 0.9rem; line-height: 1.5; margin-bottom: 1rem;">${description}</p>
                    <div style="display: flex; justify-content: space-between; font-size: 0.8rem; color: var(--text-muted, #64748b);">
                        <span>Just now</span>
                        <span style="color: var(--success, #15803d); font-weight: 500;">✓ Review Pending</span>
                    </div>
                </div>
            `;
            
            // Insert it at the very top of your list
            reportsContainer.insertAdjacentHTML('afterbegin', newCardHtml);
        }
        
        // Close modal and alert success
        closeReportModal();
        alert("Thank you! Your report has been submitted for review.");
    }
</script>
<!-- --- LOGIN & GUEST ACCESS POPUP MODAL --- -->
<div id="login-modal" class="modal-overlay">
    <div class="modal-card">
        <button class="modal-close" onclick="closeLoginModal()">&times;</button>
        <h2 class="modal-title">Welcome Back</h2>
        <p class="modal-subtitle">Log in to your LexCity account or browse anonymously.</p>
        
        <form id="login-form" onsubmit="handleLoginSubmit(event)">
            <div class="form-group">
                <label class="form-label" for="login-email">Email Address</label>
                <input type="email" id="login-email" class="form-input" placeholder="you@example.com" required>
            </div>
            
            <div class="form-group">
                <label class="form-label" for="login-password">Password</label>
                <input type="password" id="login-password" class="form-input" placeholder="••••••••" required>
            </div>
            
            <button type="submit" class="btn-submit-login">Log In</button>
        </form>

        <!-- The Guest Access Divider & Button -->
        <div class="guest-divider"><span>OR</span></div>
        
        <button type="button" class="btn-guest-login" onclick="handleGuestLogin()">
            Continue as Guest
        </button>
    </div>
</div>

<!-- --- STYLING & FUNCTIONALITY --- -->
<style>
    /* Reuses overlay setup, ensures styling matches your system tokens */
    .guest-divider {
        display: flex;
        align-items: center;
        text-align: center;
        margin: 1.5rem 0;
        color: var(--text-muted, #64748b);
        font-size: 0.8rem;
        font-weight: 600;
        letter-spacing: 0.05em;
    }

    .guest-divider::before, .guest-divider::after {
        content: '';
        flex: 1;
        border-bottom: 1px solid var(--border, #e2e8f0);
    }

    .guest-divider:not(:empty)::before { margin-right: .75em; }
    .guest-divider:not(:empty)::after { margin-left: .75em; }

    .btn-submit-login {
        width: 100%;
        padding: 0.75rem;
        background-color: var(--primary, #0f172a); /* Deep slate login button */
        color: #ffffff;
        border: none;
        border-radius: 6px;
        font-family: var(--font-sans), sans-serif;
        font-size: 1rem;
        font-weight: 500;
        cursor: pointer;
        transition: background-color 0.2s ease;
    }

    .btn-submit-login:hover {
        background-color: var(--primary-light, #1e293b);
    }

    .btn-guest-login {
        width: 100%;
        padding: 0.75rem;
        background-color: transparent;
        color: var(--text-main, #334155);
        border: 1px solid var(--border, #e2e8f0);
        border-radius: 6px;
        font-family: var(--font-sans), sans-serif;
        font-size: 1rem;
        font-weight: 500;
        cursor: pointer;
        transition: background-color 0.2s ease, color 0.2s ease;
    }

    .btn-guest-login:hover {
        background-color: var(--bg-light, #f8fafc);
        color: var(--primary, #0f172a);
    }
</style>

<script>
    // 1. Hook up all your existing "Log in" text links dynamically
    document.addEventListener("DOMContentLoaded", function() {
        // Find links that say "Log in"
        const loginLinks = Array.from(document.querySelectorAll('.auth-link, a')).filter(el => el.textContent.trim().toLowerCase() === 'log in');
        
        loginLinks.forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                document.getElementById('login-modal').classList.add('active');
            });
        });
    });

    // 2. Control Login Modal close
    function closeLoginModal() {
        document.getElementById('login-modal').classList.remove('active');
        document.getElementById('login-form').reset();
    }

    // 3. Handle Standard Login Submit
    function handleLoginSubmit(event) {
        event.preventDefault();
        closeLoginModal();
        
        // If your initial sign-up screen is still covering the main page, dismiss it too
        const mainOverlay = document.getElementById('auth-overlay');
        if (mainOverlay) {
            mainOverlay.style.opacity = '0';
            mainOverlay.style.visibility = 'hidden';
        }
        
        alert("Logged in successfully!");
    }

    // 4. Handle Guest Login (Bypasses verification fields)
    function handleGuestLogin() {
        closeLoginModal();
        
        // Instantly clear out your splash screen/sign-up screen if it is active
        const mainOverlay = document.getElementById('auth-overlay');
        if (mainOverlay) {
            mainOverlay.style.opacity = '0';
            mainOverlay.style.visibility = 'hidden';
        }
        
        alert("Entering LexCity as a Guest. Some direct case tracking features may require a profile.");
    }
</script>
<div class="guest-divider"><span>OR</span></div>

<button type="button" class="btn-guest-login" onclick="handleGuestLogin()">
    Continue as Guest
</button>
/* --- GUEST DIVIDER & BUTTON FOR SIGN UP --- */
.guest-divider {
    display: flex;
    align-items: center;
    text-align: center;
    margin: 1.5rem 0;
    color: var(--text-muted, #64748b);
    font-size: 0.8rem;
    font-weight: 600;
    letter-spacing: 0.05em;
}

.guest-divider::before, .guest-divider::after {
    content: '';
    flex: 1;
    border-bottom: 1px solid var(--border, #e2e8f0);
}

.guest-divider:not(:empty)::before { margin-right: .75em; }
.guest-divider:not(:empty)::after { margin-left: .75em; }

.btn-guest-login {
    width: 100%;
    padding: 0.75rem;
    background-color: transparent;
    color: var(--text-main, #334155);
    border: 1px solid var(--border, #e2e8f0);
    border-radius: 6px;
    font-family: var(--font-sans), sans-serif;
    font-size: 1rem;
    font-weight: 500;
    cursor: pointer;
    transition: background-color 0.2s ease, color 0.2s ease;
}

.btn-guest-login:hover {
    background-color: var(--bg-light, #f8fafc);
    color: var(--primary, #0f172a);
}
<script>
    function handleGuestLogin() {
        // Find your main signup screen container/overlay ID
        // If it's called 'auth-overlay', this will hide it smoothly:
        const mainOverlay = document.getElementById('auth-overlay') || document.querySelector('.auth-container');
        
        if (mainOverlay) {
            mainOverlay.style.display = 'none';
        }
        
        alert("Entering LexCity as a Guest!");
    }
</script>
<div class="app-container">
  <button class="settings-btn" aria-label="Settings">
    <i class="fas fa-cog"></i> </button>

  <h1>Welcome to the App</h1>
</div>
.app-container {
  position: relative; /* Establishes a positioning context */
  width: 100%;
  height: 100vh;
  padding: 20px;
}

.settings-btn {
  position: absolute;
  top: 20px;
  right: 20px;
  background: none;
  border: none;
  font-size: 24px;
  cursor: pointer;
  color: #333;
  transition: transform 0.3s ease;
}

/* Subtle spin effect on hover */
.settings-btn:hover {
  transform: rotate(45deg);
  color: #007bff;
}
import React, { useState } from 'react';
import { Settings } from 'lucide-react'; // Clean icon library

export default function AppLayout() {
  const [isOpen, setIsOpen] = useState(false);

  return (
    <div className="relative min-h-screen w-full bg-gray-50 p-6">
      
      {/* Top Right Settings Button */}
      <button 
        onClick={() => setIsOpen(!isOpen)}
        className="absolute top-6 right-6 p-2 rounded-full text-gray-600 hover:bg-gray-200 hover:text-gray-900 transition-all duration-200"
        aria-label="Open settings"
      >
        <Settings className="w-6 h-6 animate-hover:spin" />
      </button>

      {/* Simple Dropdown Menu Menu */}
      {isOpen && (
        <div className="absolute top-16 right-6 w-48 bg-white border border-gray-200 rounded-lg shadow-lg py-2 z-50">
          <button className="w-full text-left px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Account</button>
          <button className="w-full text-left px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Preferences</button>
          <hr className="my-1 border-gray-200" />
          <button className="w-full text-left px-4 py-2 text-sm text-red-600 hover:bg-gray-100">Logout</button>
        </div>
      )}

      <main>
        <h1 className="text-2xl font-bold">Main Content Area</h1>
      </main>
    </div>
  );
}
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>App with Settings</title>
  
  <!-- FontAwesome for the Gear Icon -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-font-awesome/6.4.0/css/all.min.css">

  <style>
    /* Basic Page Setup */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background-color: #f4f7f6;
      color: #333;
      transition: background 0.3s, color 0.3s;
      padding: 40px;
    }

    /* Dark Mode Styles */
    body.dark-theme {
      background-color: #1e1e24;
      color: #fff;
    }
    body.dark-theme .settings-menu {
      background-color: #2a2a35;
      border-color: #444;
      color: #fff;
    }
    body.dark-theme .menu-item {
      color: #eee;
    }
    body.dark-theme .menu-item:hover {
      background-color: #3a3a4a;
    }

    /* --- Settings Container (Top Right) --- */
    .settings-container {
      position: fixed;
      top: 20px;
      right: 20px;
      z-index: 1000;
    }

    /* The Gear Button */
    .settings-btn {
      background: none;
      border: none;
      font-size: 24px;
      cursor: pointer;
      color: inherit;
      padding: 10px;
      border-radius: 50px;
      transition: transform 0.4s ease, background-color 0.2s;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .settings-btn:hover {
      background-color: rgba(0, 0, 0, 0.05);
      transform: rotate(45deg);
    }
    
    body.dark-theme .settings-btn:hover {
      background-color: rgba(255, 255, 255, 0.1);
    }

    /* The Dropdown Menu */
    .settings-menu {
      position: absolute;
      top: 50px;
      right: 0;
      width: 220px;
      background-color: white;
      border: 1px solid #e0e0e0;
      border-radius: 8px;
      shadow: 0 4px 12px rgba(0,0,0,0.1);
      box-shadow: 0 4px 15px rgba(0,0,0,0.1);
      padding: 8px 0;
      display: none; /* Hidden by default */
      flex-direction: column;
    }

    /* Show class triggered by JS */
    .settings-menu.show {
      display: flex;
    }

    /* Menu Items */
    .menu-item {
      padding: 10px 20px;
      width: 100%;
      text-align: left;
      background: none;
      border: none;
      font-size: 14px;
      color: #444;
      cursor: pointer;
      display: flex;
      justify-content: space-between;
      align-items: center;
      transition: background 0.2s;
    }

    .menu-item:hover {
      background-color: #f5f5f5;
    }

    .menu-divider {
      border-top: 1px solid #eee;
      margin: 6px 0;
    }

    /* Toggle Switch Styles */
    .switch {
      position: relative;
      display: inline-block;
      width: 34px;
      height: 20px;
    }

    .switch input { 
      opacity: 0;
      width: 0;
      height: 0;
    }

    .slider {
      position: absolute;
      cursor: pointer;
      top: 0; left: 0; right: 0; bottom: 0;
      background-color: #ccc;
      transition: .3s;
      border-radius: 20px;
    }

    .slider:before {
      position: absolute;
      content: "";
      height: 14px;
      width: 14px;
      left: 3px;
      bottom: 3px;
      background-color: white;
      transition: .3s;
      border-radius: 50%;
    }

    input:checked + .slider {
      background-color: #2196F3;
    }

    input:checked + .slider:before {
      transform: translateX(14px);
    }
  </style>
</head>
<body>

  <!-- SETTINGS COMPONENT -->
  <div class="settings-container">
    <button class="settings-btn" id="settingsBtn" aria-label="Settings">
      <i class="fa-solid fa-gear"></i>
    </button>
    
    <div class="settings-menu" id="settingsMenu">
      <div class="menu-item">
        <span>Dark Mode</span>
        <label class="switch">
          <input type="checkbox" id="darkModeToggle">
          <span class="slider"></span>
        </label>
      </div>
      <button class="menu-item" onclick="alert('Account settings clicked!')">Account Details</button>
      <button class="menu-item" onclick="alert('Notifications clicked!')">Notifications</button>
      <div class="menu-divider"></div>
      <button class="menu-item" style="color: #e53e3e;" onclick="alert('Logged out!')">Log Out</button>
    </div>
  </div>

  <!-- MAIN PAGE CONTENT -->
  <main>
    <h1>My Awesome App</h1>
    <p>Click the gear icon in the top right corner to customize your preferences.</p>
  </main>

  <!-- JAVASCRIPT FOR INTERACTION -->
  <script>
    const settingsBtn = document.getElementById('settingsBtn');
    const settingsMenu = document.getElementById('settingsMenu');
    const darkModeToggle = document.getElementById('darkModeToggle');

    // 1. Toggle Menu Visibility
    settingsBtn.addEventListener('click', (e) => {
      e.stopPropagation(); // Prevents immediate closing
      settingsMenu.classList.toggle('show');
    });

    // 2. Close Menu if clicking anywhere else on screen
    document.addEventListener('click', (e) => {
      if (!settingsMenu.contains(e.target) && e.target !== settingsBtn) {
        settingsMenu.classList.remove('show');
      }
    });

    // 3. Dark Mode Toggle Logic
    darkModeToggle.addEventListener('change', () => {
      document.body.classList.toggle('dark-theme');
    });
  </script>

</body>
</html>
<button class="settings-btn" id="settingsBtn" aria-label="Settings">
  ⚙️
</button>
