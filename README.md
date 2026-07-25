<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LexCivic | Amplify Your Legal Voice</title>
    <!-- Tailwind CSS for modern utility styling -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Merriweather (Serif) & Inter (Sans) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Merriweather:ital,wght@0,300;0,400;0,700;1,300&display=swap" rel="stylesheet">
    <!-- FontAwesome for Legal & Civic Iconography -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        navy: {
                            DEFAULT: '#0E1A2B',
                            light: '#1A2E4C',
                            dark: '#070D16'
                        },
                        gold: {
                            DEFAULT: '#C9A86A',
                            light: '#DBC392',
                            dark: '#A88544'
                        },
                        slate: {
                            DEFAULT: '#6B7280',
                            light: '#F3F4F6',
                            dark: '#374151'
                        }
                    },
                    fontFamily: {
                        serif: ['Merriweather', 'serif'],
                        sans: ['Inter', 'sans-serif'],
                        mono: ['Courier New', 'monospace']
                    }
                }
            }
        }
    </script>
    <style>
        body { font-family: 'Inter', sans-serif; }
        h1, h2, h3, .font-serif { font-family: 'Merriweather', serif; }
        .focus-ring:focus { outline: 2px solid #C9A86A; outline-offset: 2px; }
        @media (prefers-reduced-motion: reduce) {
            * { animation-duration: 0.01ms !important; animation-iteration-count: 1 !important; transition-duration: 0.01ms !important; scroll-behavior: auto !important; }
        }
    </style>
</head>
<body class="bg-gray-50 text-slate-dark min-h-screen flex flex-col selection:bg-gold selection:text-navy">

    <!-- NAVIGATION BAR -->
    <nav class="bg-navy text-white sticky top-0 z-50 shadow-md border-b border-gold/20">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-20">
                <div class="flex items-center gap-3 cursor-pointer" onclick="switchView('hero-home')">
                    <i class="fa-solid fa-scale-balanced text-2xl text-gold"></i>
                    <span class="text-2xl font-bold font-serif tracking-wide text-white">Lex<span class="text-gold">Civic</span></span>
                </div>
                <!-- Desktop Nav -->
                <div class="hidden md:flex items-center space-x-6">
                    <button onclick="switchView('hub')" class="hover:text-gold transition font-medium text-sm">City Problems</button>
                    <button onclick="switchView('library')" class="hover:text-gold transition font-medium text-sm">Articles</button>
                    <button onclick="switchView('admin')" class="hover:text-gold transition font-medium text-sm">Admin Dashboard</button>
                    <span class="text-gold/30">|</span>
                    <button onclick="switchView('login')" class="text-sm font-medium border border-gold text-gold hover:bg-gold hover:text-navy px-4 py-2 rounded transition">Join as a Lawyer</button>
                </div>
                <!-- Mobile Menu Button -->
                <div class="md:hidden">
                    <button onclick="toggleMobileMenu()" class="text-gray-400 hover:text-white focus:outline-none">
                        <i class="fa-solid fa-bars text-xl"></i>
                    </button>
                </div>
            </div>
        </div>
        <!-- Mobile Dropdown -->
        <div id="mobile-menu" class="hidden md:hidden bg-navy-light border-t border-gold/10 px-4 py-4 space-y-3">
            <button onclick="switchView('hub')" class="block w-full text-left text-white hover:text-gold py-2">City Problems</button>
            <button onclick="switchView('library')" class="block w-full text-left text-white hover:text-gold py-2">Articles</button>
            <button onclick="switchView('admin')" class="block w-full text-left text-white hover:text-gold py-2">Admin Dashboard</button>
            <button onclick="switchView('login')" class="block w-full text-center bg-gold text-navy font-semibold py-2 rounded">Join as a Lawyer</button>
        </div>
    </nav>

    <!-- MAIN APP CONTENT CONTAINERS -->
    <main class="flex-grow">

        <!-- 1. HERO & HOME SECTION -->
        <section id="hero-home" class="view-section dynamic-view">
            <!-- Hero Banner -->
            <div class="bg-gradient-to-br from-navy via-navy-light to-navy-dark text-white py-24 px-4 relative overflow-hidden border-b-4 border-gold">
                <div class="absolute inset-0 opacity-10 bg-[radial-gradient(#C9A86A_1px,transparent_1px)] [background-size:16px_16px]"></div>
                <div class="max-w-4xl mx-auto text-center relative z-10">
                    <div class="inline-flex items-center gap-2 bg-gold/10 border border-gold/30 text-gold px-4 py-1.5 rounded-full text-xs uppercase tracking-wider mb-6 font-semibold">
                        <i class="fa-solid fa-gavel"></i> Civic Justice & Accountability
                    </div>
                    <h1 class="text-4xl sm:text-6xl font-bold tracking-tight mb-6 leading-tight">Amplify Your Legal Voice</h1>
                    <p class="text-lg sm:text-xl text-gray-300 max-w-2xl mx-auto mb-10 font-light">
                        Verified lawyers publishing city issues, structural compliance gaps, and actionable legal insights for community empowerment.
                    </p>
                    <div class="flex flex-col sm:flex-row justify-center gap-4">
                        <button onclick="switchView('login')" class="bg-gold hover:bg-gold-light text-navy font-bold px-8 py-4 rounded shadow-lg transform transition active:scale-95 focus-ring">
                            Join as a Lawyer
                        </button>
                        <button onclick="switchView('hub')" class="bg-transparent border-2 border-white/80 hover:border-white text-white font-semibold px-8 py-4 rounded transition backdrop-blur-sm focus-ring">
                            Explore City Issues
                        </button>
                    </div>
                </div>
            </div>

            <!-- Social Proof / Testimonials -->
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
                <h2 class="text-center text-xs uppercase tracking-widest text-slate font-bold mb-10">Trusted By Attorneys Nationwide</h2>
                <div class="grid md:grid-cols-3 gap-8">
                    <div class="bg-white p-8 rounded-lg shadow-sm border-l-4 border-gold">
                        <p class="text-slate-dark italic mb-6">"LexCivic allowed me to translate structural municipal negligence regarding local tenant rights into actionable administrative appeals. A game-changer for public interest law."</p>
                        <div class="flex items-center gap-3">
                            <div class="w-10 h-10 rounded-full bg-navy text-gold flex items-center justify-center font-bold text-sm">HE</div>
                            <div>
                                <h4 class="font-bold text-sm">Hon. Elena Vance</h4>
                                <p class="text-xs text-slate">Housing Rights Advocate, NY Bar</p>
                            </div>
                        </div>
                    </div>
                    <div class="bg-white p-8 rounded-lg shadow-sm border-l-4 border-gold">
                        <p class="text-slate-dark italic mb-6">"Environmental violations often escape public notice due to legal opacity. Here, we present pure raw facts alongside jurisdictional statutes for maximum impact."</p>
                        <div class="flex items-center gap-3">
                            <div class="w-10 h-10 rounded-full bg-navy text-gold flex items-center justify-center font-bold text-sm">JM</div>
                            <div>
                                <h4 class="font-bold text-sm">Marcus Vance, Esq.</h4>
                                <p class="text-xs text-slate">Environmental Law, CA Bar</p>
                            </div>
                        </div>
                    </div>
                    <div class="bg-white p-8 rounded-lg shadow-sm border-l-4 border-gold">
                        <p class="text-slate-dark italic mb-6">"Infrastructure failure is fundamentally a policy and statutory enforcement failure. This platform bridges that specific gap seamlessly for the public."</p>
                        <div class="flex items-center gap-3">
                            <div class="w-10 h-10 rounded-full bg-navy text-gold flex items-center justify-center font-bold text-sm">DB</div>
                            <div>
                                <h4 class="font-bold text-sm">Dianne Burbank</h4>
                                <p class="text-xs text-slate">Municipal Specialist, TX Bar</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>


        <!-- 2. AUTH & LAWYER VERIFICATION FLOW -->
        <section id="login" class="view-section dynamic-view hidden bg-slate-light py-16 px-4">
            <div class="max-w-2xl mx-auto bg-white rounded-xl shadow-md overflow-hidden border border-gray-200">
                <div class="bg-navy p-6 text-white text-center">
                    <h2 class="text-2xl font-bold font-serif text-gold">Lawyer Onboarding Portal</h2>
                    <p class="text-sm text-gray-300 mt-1">Submit your credentials for secure credentialing and validation</p>
                </div>

                <!-- Wizard Tabs Indicator -->
                <div class="flex border-b border-gray-200 text-xs font-semibold text-center text-gray-500">
                    <div id="tab-step1" class="flex-1 py-3 bg-gray-50 border-b-2 border-gold text-navy">1. Account Creation</div>
                    <div id="tab-step2" class="flex-1 py-3 bg-gray-50">2. Bar Credentials</div>
                    <div id="tab-step3" class="flex-1 py-3 bg-gray-50">3. Status Verification</div>
                </div>

                <!-- Form step 1 -->
                <div id="panel-step1" class="p-8 space-y-6">
                    <div class="space-y-3">
                        <button type="button" class="w-full flex items-center justify-center gap-3 border border-gray-300 rounded px-4 py-2.5 text-sm font-medium hover:bg-gray-50 transition">
                            <i class="fa-brands fa-google text-red-500"></i> Continue with Google Auth
                        </button>
                        <button type="button" class="w-full flex items-center justify-center gap-3 border border-gray-300 rounded px-4 py-2.5 text-sm font-medium hover:bg-gray-50 transition">
                            <i class="fa-brands fa-linkedin text-blue-600"></i> Continue with LinkedIn Pro
                        </button>
                    </div>
                    <div class="relative flex py-2 items-center">
                        <div class="flex-grow border-t border-gray-200"></div>
                        <span class="flex-shrink mx-4 text-gray-400 text-xs uppercase">Or Use Corporate Email</span>
                        <div class="flex-grow border-t border-gray-200"></div>
                    </div>
                    <div>
                        <label class="block text-xs font-bold uppercase text-slate-dark mb-1">Professional Email</label>
                        <input type="email" placeholder="attorney@firm.org" class="w-full p-2.5 border border-gray-300 rounded text-sm focus-ring">
                    </div>
                    <div>
                        <label class="block text-xs font-bold uppercase text-slate-dark mb-1">Password</label>
                        <input type="password" placeholder="••••••••" class="w-full p-2.5 border border-gray-300 rounded text-sm focus-ring">
                    </div>
                    <button onclick="goToVerificationStep(2)" class="w-full bg-navy text-white font-bold py-3 rounded hover:bg-navy-light transition">
                        Next: Verify Professional Credentials
                    </button>
                </div>

                <!-- Form step 2 -->
                <div id="panel-step2" class="p-8 space-y-6 hidden">
                    <div class="grid grid-cols-2 gap-4">
                        <div>
                            <label class="block text-xs font-bold uppercase text-slate-dark mb-1">State Jurisdiction</label>
                            <select class="w-full p-2.5 border border-gray-300 rounded text-sm focus-ring">
                                <option>California (CalBar)</option>
                                <option>New York (NYSBA)</option>
                                <option>Texas (State Bar of Texas)</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-xs font-bold uppercase text-slate-dark mb-1">Bar Registration Number</label>
                            <input type="text" placeholder="######" class="w-full p-2.5 border border-gray-300 rounded text-sm focus-ring">
                        </div>
                    </div>
                    <div>
                        <label class="block text-xs font-bold uppercase text-slate-dark mb-1">Proof of Good Standing (PDF/Image)</label>
                        <div class="border-2 border-dashed border-gray-300 rounded-lg p-6 text-center hover:border-gold transition cursor-pointer">
                            <i class="fa-solid fa-cloud-arrow-up text-3xl text-slate mb-2"></i>
                            <p class="text-xs text-slate-dark font-medium">Drag-and-drop or click to upload current Bar Certificate</p>
                            <p class="text-[10px] text-slate mt-1">Max file size: 10MB (PDF, PNG, JPG)</p>
                        </div>
                    </div>
                    <div class="flex gap-4">
                        <button onclick="goToVerificationStep(1)" class="w-1/3 bg-gray-200 text-slate-dark font-bold py-3 rounded hover:bg-gray-300 transition">Back</button>
                        <button onclick="goToVerificationStep(3)" class="w-2/3 bg-gold text-navy font-bold py-3 rounded hover:bg-gold-light transition">Submit Verification Packet</button>
                    </div>
                </div>

                <!-- Form step 3 -->
                <div id="panel-step3" class="p-8 text-center space-y-6 hidden">
                    <div class="inline-flex items-center justify-center w-16 h-16 rounded-full bg-amber-100 text-amber-600 text-3xl mb-2 animate-pulse">
                        <i class="fa-solid fa-clock-rotate-left"></i>
                    </div>
                    <div>
                        <h3 class="text-xl font-bold text-navy">Application Status: Pending Review</h3>
                        <p class="text-sm text-slate mt-2 max-w-md mx-auto">
                            Our compliance ecosystem is matching your data against state registries. Manual validation usually clears within 12–24 business hours.
                        </p>
                    </div>
                    <div class="bg-slate-light p-4 rounded text-left border border-gray-200 max-w-md mx-auto">
                        <div class="flex justify-between text-xs font-mono text-slate-dark">
                            <span>Submission Reference:</span>
                            <span class="font-bold">#LXC-99281-2026</span>
                        </div>
                        <div class="flex justify-between text-xs font-mono text-slate-dark mt-1">
                            <span>Registry Sync Attempt:</span>
                            <span class="text-green-600 font-bold">SUCCESS (Matched)</span>
                        </div>
                    </div>
                    <div class="pt-4 flex gap-3 justify-center">
                        <button onclick="switchView('publish')" class="bg-navy text-white text-sm px-6 py-2.5 rounded font-medium hover:bg-navy-light transition">Go to Publish Dashboard (Draft Mode)</button>
                    </div>
                </div>
            </div>
        </section>


        <!-- 3. PUBLISH CENTER (Rich Text Editor) -->
        <section id="publish" class="view-section dynamic-view hidden max-w-5xl mx-auto px-4 py-12">
            <div class="flex items-center justify-between border-b border-gray-200 pb-5 mb-8">
                <div>
                    <h1 class="text-3xl font-bold font-serif text-navy">LexCivic Workspace</h1>
                    <p class="text-sm text-slate">Draft and catalog regulatory compliance audits, briefings, or regional updates</p>
                </div>
                <div class="flex items-center gap-3">
                    <button class="text-xs font-bold text-slate hover:text-navy border border-gray-300 bg-white px-3 py-2 rounded">Save Draft</button>
                    <button onclick="alert('Post scheduled or published successfully.')" class="text-xs font-bold bg-gold text-navy hover:bg-gold-light px-4 py-2 rounded shadow-sm">Publish Content</button>
                </div>
            </div>

            <div class="grid lg:grid-cols-3 gap-8">
                <!-- Editor Space -->
                <div class="lg:col-span-2 space-y-6">
                    <div>
                        <input type="text" placeholder="Title: Clear, descriptive legal or structural issue headline..." class="w-full text-2xl font-serif font-bold border-b border-gray-200 pb-2 focus:outline-none focus:border-gold placeholder:text-gray-300">
                    </div>
                    
                    <!-- Formatting Controls Bar -->
                    <div class="bg-white border border-gray-200 p-2 rounded flex items-center gap-1 text-slate text-sm">
                        <button class="w-8 h-8 rounded hover:bg-gray-100 flex items-center justify-center font-bold">B</button>
                        <button class="w-8 h-8 rounded hover:bg-gray-100 flex items-center justify-center italic">I</button>
                        <button class="w-8 h-8 rounded hover:bg-gray-100 flex items-center justify-center font-mono">“</button>
                        <span class="text-gray-300 mx-1">|</span>
                        <button class="w-8 h-8 rounded hover:bg-gray-100 flex items-center justify-center"><i class="fa-solid fa-link text-xs"></i></button>
                        <button class="w-8 h-8 rounded hover:bg-gray-100 flex items-center justify-center"><i class="fa-solid fa-paperclip text-xs"></i></button>
                        <button class="w-8 h-8 rounded hover:bg-gray-100 flex items-center justify-center"><i class="fa-solid fa-location-dot text-xs"></i></button>
                        <span class="text-gray-300 mx-1">|</span>
                        <span class="text-xs text-slate-dark ml-auto bg-gray-100 px-2 py-1 rounded font-mono">Statute Citation Format Enabled</span>
                    </div>

                    <!-- Sandbox Editor Area -->
                    <div>
                        <textarea rows="12" placeholder="Begin analysis here. Use legal citations format (e.g., 42 U.S.C. § 1983) for structural municipal issues..." class="w-full p-4 border border-gray-200 rounded-lg text-sm font-sans leading-relaxed focus-ring focus:border-transparent" style="resize: vertical;"></textarea>
                    </div>
                </div>

                <!-- Content Configuration Meta-Panel -->
                <div class="bg-white p-6 rounded-xl border border-gray-200 shadow-sm space-y-6 h-fit">
                    <h3 class="font-serif font-bold text-navy border-b border-gray-100 pb-2">Classification & Meta</h3>
                    <div>
                        <label class="block text-xs font-bold uppercase tracking-wider text-slate-dark mb-1.5">Post Architecture Type</label>
                        <div class="grid grid-cols-2 gap-2">
                            <label class="border p-3 rounded text-center block cursor-pointer bg-gray-50 border-gold" id="type-prob-lbl">
                                <input type="radio" name="post-type" class="sr-only" checked onclick="document.getElementById('meta-geo').classList.remove('hidden')">
                                <i class="fa-solid fa-triangle-exclamation text-amber-600 block mb-1"></i>
                                <span class="text-xs font-semibold">City Problem</span>
                            </label>
                            <label class="border p-3 rounded text-center block cursor-pointer bg-white" id="type-art-lbl">
                                <input type="radio" name="post-type" class="sr-only" onclick="document.getElementById('meta-geo').classList.add('hidden')">
                                <i class="fa-solid fa-book-bookmark text-blue-600 block mb-1"></i>
                                <span class="text-xs font-semibold">Legal Insight</span>
                            </label>
                        </div>
                    </div>

                    <div id="meta-geo" class="space-y-4">
                        <div>
                            <label class="block text-xs font-bold uppercase tracking-wider text-slate-dark mb-1">Target Municipal Region</label>
                            <input type="text" placeholder="e.g., Los Angeles, CA" class="w-full p-2 border border-gray-300 rounded text-xs focus-ring">
                        </div>
                        <div>
                            <label class="block text-xs font-bold uppercase tracking-wider text-slate-dark mb-1">Systemic Domain Category</label>
                            <select class="w-full p-2 border border-gray-300 rounded text-xs focus-ring">
                                <option>Infrastructure & Public Safety</option>
                                <option>Municipal Housing Discrepancies</option>
                                <option>Environmental Regulatory Breaches</option>
                                <option>Policing & Disciplinary Metrics</option>
                            </select>
                        </div>
                    </div>
                </div>
            </div>
        </section>


        <!-- 4. CITY PROBLEM HUB -->
        <section id="hub" class="view-section dynamic-view hidden max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10">
            <div class="mb-8">
                <h1 class="text-3xl font-bold font-serif text-navy">Municipal Docket & Issues Tracking</h1>
                <p class="text-sm text-slate">Cross-referencing reported municipal vulnerabilities validated by legal counsels.</p>
            </div>

            <!-- Dashboard Filters & Controls -->
            <div class="bg-white p-4 rounded-xl border border-gray-200 shadow-sm flex flex-wrap gap-4 items-center justify-between mb-8">
                <div class="flex flex-wrap items-center gap-3 w-full lg:w-auto">
                    <div class="relative flex-grow sm:flex-grow-0">
                        <i class="fa-solid fa-magnifying-glass absolute left-3 top-3 text-gray-400 text-xs"></i>
                        <input type="text" placeholder="Search by city, case number..." class="pl-9 pr-4 py-2 border border-gray-300 rounded text-xs w-full sm:w-64 focus-ring">
                    </div>
                    <select id="filter-category" onchange="filterIssues()" class="p-2 border border-gray-300 rounded text-xs bg-gray-50 focus-ring">
                        <option value="all">All Domains</option>
                        <option value="infrastructure">Infrastructure</option>
                        <option value="housing">Housing Compliance</option>
                        <option value="environmental">Environmental Violations</option>
                    </select>
                </div>
                <div class="flex items-center gap-2 text-xs">
                    <span class="text-slate font-medium">Export Repository:</span>
                    <button class="border border-gray-300 hover:bg-gray-100 px-3 py-1.5 rounded bg-white text-slate-dark"><i class="fa-solid fa-file-pdf text-red-500 mr-1"></i> PDF</button>
                    <button class="border border-gray-300 hover:bg-gray-100 px-3 py-1.5 rounded bg-white text-slate-dark"><i class="fa-solid fa-file-excel text-green-600 mr-1"></i> Data Sheet</button>
                </div>
            </div>

            <div class="grid lg:grid-cols-3 gap-8">
                <!-- Issues Stream Feed -->
                <div class="lg:col-span-2 space-y-4" id="issues-container">
                    <!-- Case item 1 -->
                    <div class="bg-white p-6 rounded-xl border border-gray-200 shadow-sm hover:shadow-md transition issue-card" data-cat="infrastructure">
                        <div class="flex justify-between items-start gap-4 mb-3">
                            <span class="bg-amber-100 text-amber-800 border border-amber-200 text-[10px] font-bold px-2.5 py-0.5 rounded-full uppercase tracking-wide">
                                Open Status
                            </span>
                            <span class="text-xs font-mono text-slate font-semibold"><i class="fa-solid fa-location-dot text-gold mr-1"></i> Austin, TX</span>
                        </div>
                        <h3 class="text-lg font-bold font-serif text-navy hover:text-gold cursor-pointer transition">Systemic Bridge Structural Maintenance Variance</h3>
                        <p class="text-xs text-slate mt-2 line-clamp-2">
                            Detailed non-compliance metrics tracking structural deflection along the interstate service overpass. Local maintenance budgets have continuously misallocated state hazard mitigation outlays...
                        </p>
                        <div class="flex items-center justify-between border-t border-gray-100 pt-4 mt-4 text-xs">
                            <div class="flex items-center gap-4 text-slate">
                                <button onclick="toggleUpvote(this)" class="hover:text-navy transition flex items-center gap-1.5 font-semibold bg-gray-100 px-3 py-1 rounded">
                                    <i class="fa-solid fa-arrow-up"></i> <span class="vote-count">142</span>
                                </button>
                                <span><i class="fa-solid fa-user-shield text-gold mr-1"></i> Verified Briefing</span>
                            </div>
                            <span class="text-slate font-medium">Domain: Infrastructure</span>
                        </div>
                    </div>

                    <!-- Case item 2 -->
                    <div class="bg-white p-6 rounded-xl border border-gray-200 shadow-sm hover:shadow-md transition issue-card" data-cat="housing">
                        <div class="flex justify-between items-start gap-4 mb-3">
                            <span class="bg-blue-100 text-blue-800 border border-blue-200 text-[10px] font-bold px-2.5 py-0.5 rounded-full uppercase tracking-wide">
                                In Progress
                            </span>
                            <span class="text-xs font-mono text-slate font-semibold"><i class="fa-solid fa-location-dot text-gold mr-1"></i> Los Angeles, CA</span>
                        </div>
                        <h3 class="text-lg font-bold font-serif text-navy hover:text-gold cursor-pointer transition">Unlawful Eviction Notice Enforcement Processing Gaps</h3>
                        <p class="text-xs text-slate mt-2 line-clamp-2">
                            Analysis of systemic errors within municipal housing court notices processed through fast-track administrative pipelines without proper oversight or validation...
                        </p>
                        <div class="flex items-center justify-between border-t border-gray-100 pt-4 mt-4 text-xs">
                            <div class="flex items-center gap-4 text-slate">
                                <button onclick="toggleUpvote(this)" class="hover:text-navy transition flex items-center gap-1.5 font-semibold bg-gray-100 px-3 py-1 rounded">
                                    <i class="fa-solid fa-arrow-up"></i> <span class="vote-count">389</span>
                                </button>
                                <span><i class="fa-solid fa-user-shield text-gold mr-1"></i> Verified Briefing</span>
                            </div>
                            <span class="text-slate font-medium">Domain: Housing Compliance</span>
                        </div>
                    </div>

                    <!-- Case item 3 -->
                    <div class="bg-white p-6 rounded-xl border border-gray-200 shadow-sm hover:shadow-md transition issue-card" data-cat="environmental">
                        <div class="flex justify-between items-start gap-4 mb-3">
                            <span class="bg-green-100 text-green-800 border border-green-200 text-[10px] font-bold px-2.5 py-0.5 rounded-full uppercase tracking-wide">
                                Resolved
                            </span>
                            <span class="text-xs font-mono text-slate font-semibold"><i class="fa-solid fa-location-dot text-gold mr-1"></i> Flint, MI</span>
                        </div>
                        <h3 class="text-lg font-bold font-serif text-navy hover:text-gold cursor-pointer transition">Industrial Effluent Discharge Into Public Stream Feeders</h3>
                        <p class="text-xs text-slate mt-2 line-clamp-2">
                            Independent sampling confirmed chemical values spikes above standard limits. Consent decree tracking parameters established...
                        </p>
                        <div class="flex items-center justify-between border-t border-gray-100 pt-4 mt-4 text-xs">
                            <div class="flex items-center gap-4 text-slate">
                                <button onclick="toggleUpvote(this)" class="hover:text-navy transition flex items-center gap-1.5 font-semibold bg-gray-100 px-3 py-1 rounded">
                                    <i class="fa-solid fa-arrow-up"></i> <span class="vote-count">711</span>
                                </button>
                                <span><i class="fa-solid fa-user-shield text-gold mr-1"></i> Verified Briefing</span>
                            </div>
                            <span class="text-slate font-medium">Domain: Environmental Violations</span>
                        </div>
                    </div>
                </div>

                <!-- Simulation Map Interface -->
                <div class="bg-navy rounded-xl border-2 border-gold shadow-md h-[550px] relative overflow-hidden flex flex-col">
                    <div class="p-4 bg-navy-dark text-white border-b border-gold/20 flex justify-between items-center">
                        <span class="text-xs font-bold tracking-wider uppercase text-gold"><i class="fa-solid fa-map-location-dot mr-1.5"></i> Regional Geofencing Matrix</span>
                        <span class="bg-red-500/20 text-red-400 border border-red-500/40 text-[10px] px-2 py-0.5 rounded font-mono">Live Sync</span>
                    </div>
                    <!-- Mock map elements -->
                    <div class="flex-grow bg-slate-dark relative" style="background-image: radial-gradient(rgba(255,255,255,0.15) 1px, transparent 0); background-size: 24px 24px;">
                        <!-- Map Pin 1 -->
                        <div class="absolute top-1/4 left-1/3 group cursor-pointer">
                            <div class="w-3 h-3 bg-amber-500 rounded-full animate-ping absolute inline-flex"></div>
                            <i class="fa-solid fa-location-pin text-xl text-amber-500 relative z-10"></i>
                            <div class="hidden group-hover:block absolute bg-navy border border-gold text-white text-[10px] p-2 rounded shadow-xl w-32 -top-12 left-4 z-50">
                                <strong>Austin, TX</strong><br>Bridge Infrastructure Gap
                            </div>
                        </div>
                        <!-- Map Pin 2 -->
                        <div class="absolute top-2/3 left-1/4 group cursor-pointer">
                            <div class="w-3 h-3 bg-blue-500 rounded-full animate-ping absolute inline-flex"></div>
                            <i class="fa-solid fa-location-pin text-xl text-blue-500 relative z-10"></i>
                            <div class="hidden group-hover:block absolute bg-navy border border-gold text-white text-[10px] p-2 rounded shadow-xl w-32 -top-12 left-4 z-50">
                                <strong>Los Angeles, CA</strong><br>Housing Notice Audit
                            </div>
                        </div>
                        <!-- Map Pin 3 -->
                        <div class="absolute top-1/2 right-1/4 group cursor-pointer">
                            <i class="fa-solid fa-location-pin text-xl text-green-500 relative z-10"></i>
                            <div class="hidden group-hover:block absolute bg-navy border border-gold text-white text-[10px] p-2 rounded shadow-xl w-32 -top-12 left-4 z-50">
                                <strong>Flint, MI</strong><br>Water Discharge Issue
                            </div>
                        </div>

                        <!-- Map Hud overlay -->
                        <div class="absolute bottom-4 left-4 right-4 bg-navy-dark/95 border border-gold/30 rounded p-3 text-white backdrop-blur-sm">
                            <p class="text-[11px] font-mono leading-normal text-gray-300">
                                <span class="text-gold font-bold">Instruction:</span> Hover or tap clustered localized coordinates nodes to preview active filings briefs.
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </section>


        <!-- 5. ARTICLES LIBRARY -->
        <section id="library" class="view-section dynamic-view hidden max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
            <div class="border-b border-gray-200 pb-6 mb-8 flex flex-col md:flex-row md:items-end justify-between gap-4">
                <div>
                    <h1 class="text-3xl font-bold font-serif text-navy">Legal Insights Library</h1>
                    <p class="text-sm text-slate">Authoritative statutory analyses and accountability publications by legal experts</p>
                </div>
                <div class="flex gap-2">
                    <button class="bg-navy text-white text-xs font-semibold px-4 py-2 rounded">Latest Releases</button>
                    <button class="bg-white border text-slate text-xs font-semibold px-4 py-2 rounded hover:bg-gray-50">Most Consulted</button>
                </div>
            </div>

            <div class="grid md:grid-cols-3 gap-8">
                <!-- Brief Card 1 -->
                <div class="bg-white border border-gray-200 rounded-xl overflow-hidden shadow-sm hover:shadow-md transition flex flex-col">
                    <div class="p-6 flex-grow">
                        <div class="flex items-center gap-2 text-xs font-mono text-slate mb-3">
                            <span class="text-gold font-bold">Constitutional Law</span>
                            <span>•</span>
                            <span>9 min read</span>
                        </div>
                        <h3 class="text-xl font-serif font-bold text-navy mb-3 hover:text-gold cursor-pointer transition">The Scope of Sovereign Immunity in Municipal Infrastructure Torts</h3>
                        <p class="text-xs text-slate line-clamp-3 mb-4">
                            An analytical brief covering structural changes in municipal tort law liability protections when cities neglect critical infrastructure systems after receiving targeted remediation funding allocations.
                        </p>
                        <div class="bg-slate-light p-3 rounded font-mono text-[10px] text-slate-dark border-l-2 border-gold">
                            Primary Ref: 28 U.S.C. § 2674; Monroe v. Pape, 365 U.S. 167
                        </div>
                    </div>
                    <div class="bg-gray-50 px-6 py-4 border-t border-gray-100 flex items-center justify-between">
                        <div class="flex items-center gap-2">
                            <div class="w-7 h-7 rounded-full bg-navy text-white flex items-center justify-center font-bold text-[10px]">TH</div>
                            <span class="text-xs font-medium text-slate-dark">T. Hardinge, Esq.</span>
                        </div>
                        <button class="text-gold hover:text-gold-dark text-xs font-bold flex items-center gap-1">Read Brief <i class="fa-solid fa-chevron-right text-[10px]"></i></button>
                    </div>
                </div>

                <!-- Brief Card 2 -->
                <div class="bg-white border border-gray-200 rounded-xl overflow-hidden shadow-sm hover:shadow-md transition flex flex-col">
                    <div class="p-6 flex-grow">
                        <div class="flex items-center gap-2 text-xs font-mono text-slate mb-3">
                            <span class="text-gold font-bold">Land Use & Housing</span>
                            <span>•</span>
                            <span>14 min read</span>
                        </div>
                        <h3 class="text-xl font-serif font-bold text-navy mb-3 hover:text-gold cursor-pointer transition">Procedural Due Process Challenges in Accelerated Code Enforcement Actions</h3>
                        <p class="text-xs text-slate line-clamp-3 mb-4">
                            Exploring historical precedents where automated municipal fine systems violated constitutional standards regarding notice requirements and opportunity to respond.
                        </p>
                        <div class="bg-slate-light p-3 rounded font-mono text-[10px] text-slate-dark border-l-2 border-gold">
                            Primary Ref: Matthews v. Eldridge, 424 U.S. 319
                        </div>
                    </div>
                    <div class="bg-gray-50 px-6 py-4 border-t border-gray-100 flex items-center justify-between">
                        <div class="flex items-center gap-2">
                            <div class="w-7 h-7 rounded-full bg-navy text-white flex items-center justify-center font-bold text-[10px]">EV</div>
                            <span class="text-xs font-medium text-slate-dark">Hon. E. Vance</span>
                        </div>
                        <button class="text-gold hover:text-gold-dark text-xs font-bold flex items-center gap-1">Read Brief <i class="fa-solid fa-chevron-right text-[10px]"></i></button>
                    </div>
                </div>

                <!-- Brief Card 3 -->
                <div class="bg-white border border-gray-200 rounded-xl overflow-hidden shadow-sm hover:shadow-md transition flex flex-col">
                    <div class="p-6 flex-grow">
                        <div class="flex items-center gap-2 text-xs font-mono text-slate mb-3">
                            <span class="text-gold font-bold">Administrative Law</span>
                            <span>•</span>
                            <span>11 min read</span>
                        </div>
                        <h3 class="text-xl font-serif font-bold text-navy mb-3 hover:text-gold cursor-pointer transition">Ecosystem Standing: Navigating Local Clean Water Compliance</h3>
                        <p class="text-xs text-slate line-clamp-3 mb-4">
                            A clear technical review of modern statutory guidelines determining citizen standing when bringing injunctive claims against heavy industrial pollutant streams.
                        </p>
                        <div class="bg-slate-light p-3 rounded font-mono text-[10px] text-slate-dark border-l-2 border-gold">
                            Primary Ref: 33 U.S.C. § 1365 (Clean Water Act)
                        </div>
                    </div>
                    <div class="bg-gray-50 px-6 py-4 border-t border-gray-100 flex items-center justify-between">
                        <div class="flex items-center gap-2">
                            <div class="w-7 h-7 rounded-full bg-navy text-white flex items-center justify-center font-bold text-[10px]">MV</div>
                            <span class="text-xs font-medium text-slate-dark">M. Vance, Esq.</span>
                        </div>
                        <button class="text-gold hover:text-gold-dark text-xs font-bold flex items-center gap-1">Read Brief <i class="fa-solid fa-chevron-right text-[10px]"></i></button>
                    </div>
                </div>
            </div>
        </section>


        <!-- 6. ADMIN DASHBOARD -->
        <section id="admin" class="view-section dynamic-view hidden max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10">
            <div class="flex items-center justify-between border-b border-gray-200 pb-5 mb-8">
                <div>
                    <h1 class="text-3xl font-bold font-serif text-navy">Central Back-Office Dashboard</h1>
                    <p class="text-sm text-slate">Platform compliance monitoring, verification pipelines, and review queues</p>
                </div>
                <span class="bg-gold/10 text-gold border border-gold/40 text-xs px-3 py-1 rounded-full font-mono font-bold">System Administrator Role</span>
            </div>

            <!-- Operational Metrics Grid -->
            <div class="grid grid-cols-2 lg:grid-cols-4 gap-4 mb-8">
                <div class="bg-white p-5 rounded-lg border border-gray-200 shadow-sm">
                    <span class="text-xs text-slate font-bold uppercase block tracking-wider">Pending Bar Verifications</span>
                    <span class="text-3xl font-bold font-serif text-navy block mt-2">14</span>
                </div>
                <div class="bg-white p-5 rounded-lg border border-gray-200 shadow-sm">
                    <span class="text-xs text-slate font-bold uppercase block tracking-wider">Flagged Content Reviews</span>
                    <span class="text-3xl font-bold font-serif text-amber-600 block mt-2">3</span>
                </div>
                <div class="bg-white p-5 rounded-lg border border-gray-200 shadow-sm">
                    <span class="text-xs text-slate font-bold uppercase block tracking-wider">Active Verified Counsel</span>
                    <span class="text-3xl font-bold font-serif text-navy block mt-2">1,248</span>
                </div>
                <div class="bg-white p-5 rounded-lg border border-gray-200 shadow-sm">
                    <span class="text-xs text-slate font-bold uppercase block tracking-wider">PDF Reports Compiled</span>
                    <span class="text-3xl font-bold font-serif text-green-700 block mt-2">4,812</span>
                </div>
            </div>

            <!-- Action Work Queues -->
            <div class="grid lg:grid-cols-3 gap-8">
                <!-- Verification Processing List -->
                <div class="lg:col-span-2 bg-white rounded-xl border border-gray-200 shadow-sm overflow-hidden">
                    <div class="p-4 bg-navy text-white font-serif font-semibold text-sm flex justify-between items-center">
                        <span>Identity & License Review Queue</span>
                        <span class="text-xs font-mono text-gold bg-gold/10 px-2 py-0.5 rounded">Action Required</span>
                    </div>
                    <div class="divide-y divide-gray-100">
                        <div class="p-4 flex items-center justify-between text-xs hover:bg-gray-50 transition">
                            <div>
                                <h4 class="font-bold text-navy text-sm">Sarah Jenkins, Esq.</h4>
                                <p class="text-slate font-mono mt-0.5">Bar Reference: #IL-8829182 • State Bar of Illinois</p>
                            </div>
                            <div class="flex items-center gap-2">
                                <button onclick="alert('Credential token match verified manually.')" class="bg-emerald-600 hover:bg-emerald-700 text-white font-bold px-3 py-1.5 rounded transition">Approve</button>
                                <button onclick="alert('Deficiency notification dispatched.')" class="bg-rose-600 hover:bg-rose-700 text-white font-bold px-3 py-1.5 rounded transition">Reject</button>
                            </div>
                        </div>
                        <div class="p-4 flex items-center justify-between text-xs hover:bg-gray-50 transition">
                            <div>
                                <h4 class="font-bold text-navy text-sm">David Vance, Jr.</h4>
                                <p class="text-slate font-mono mt-0.5">Bar Reference: #TX-9910294 • State Bar of Texas</p>
                            </div>
                            <div class="flex items-center gap-2">
                                <button onclick="alert('Credential token match verified manually.')" class="bg-emerald-600 hover:bg-emerald-700 text-white font-bold px-3 py-1.5 rounded transition">Approve</button>
                                <button onclick="alert('Deficiency notification dispatched.')" class="bg-rose-600 hover:bg-rose-700 text-white font-bold px-3 py-1.5 rounded transition">Reject</button>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Platform Activity Stream Log -->
                <div class="bg-white rounded-xl border border-gray-200 shadow-sm overflow-hidden">
                    <div class="p-4 bg-gray-50 border-b border-gray-200 font-serif font-bold text-navy text-sm">
                        System Transparency Registry
                    </div>
                    <div class="p-4 font-mono text-[11px] space-y-3 text-slate-dark max-h-[300px] overflow-y-auto">
                        <div class="pb-2 border-b border-gray-100">
                            <span class="text-green-600 font-bold">[SYNC]</span> Automated database validation checked 41 California Bar profiles. All records matching.
                        </div>
                        <div class="pb-2 border-b border-gray-100">
                            <span class="text-amber-600 font-bold">[WARN]</span> Article ID #401 flagged for citation confirmation formatting gaps. Posted to editor review backlog.
                        </div>
                        <div>
                            <span class="text-blue-600 font-bold">[INFO]</span> PDF docket summary package compiled for municipal audit matching regional tag #TX-AUSTIN.
                        </div>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- FOOTER -->
    <footer class="bg-navy text-white border-t-4 border-gold pt-12 pb-6 px-4">
        <div class="max-w-7xl mx-auto grid md:grid-cols-4 gap-8 border-b border-white/10 pb-8 mb-6 text-sm">
            <div class="space-y-3">
                <div class="flex items-center gap-2">
                    <i class="fa-solid fa-scale-balanced text-xl text-gold"></i>
                    <span class="text-xl font-bold font-serif text-white tracking-wide">LexCivic</span>
                </div>
                <p class="text-xs text-gray-400 font-light leading-relaxed">
                    Bridging structural municipal data analysis and constitutional accountability through rigorous legal review.
                </p>
            </div>
            <div>
                <h4 class="font-serif font-bold text-gold mb-3 text-xs uppercase tracking-wider">Framework Features</h4>
                <ul class="space-y-1.5 text-xs text-gray-300">
                    <li><button onclick="switchView('hub')" class="hover:text-gold transition">City Issues Map</button></li>
                    <li><button onclick="switchView('library')" class="hover:text-gold transition">Analyses Library</button></li>
                    <li><button onclick="switchView('login')" class="hover:text-gold transition">Attorney Verification Portal</button></li>
                </ul>
            </div>
            <div>
                <h4 class="font-serif font-bold text-gold mb-3 text-xs uppercase tracking-wider">Governance</h4>
                <ul class="space-y-1.5 text-xs text-gray-300">
                    <li class="hover:text-gold cursor-pointer transition">Editorial Guidelines</li>
                    <li class="hover:text-gold cursor-pointer transition">Transparency Index Logs</li>
                    <li class="hover:text-gold cursor-pointer transition">Regulatory Disclaimers</li>
                </ul>
            </div>
            <div>
                <h4 class="font-serif font-bold text-gold mb-3 text-xs uppercase tracking-wider">System Disclaimer</h4>
                <p class="text-[11px] text-gray-400 font-light leading-normal">
                    LexCivic functions exclusively as an informative public policy analytics mechanism. Submissions do not construct an active attorney-client operational privilege.
                </p>
            </div>
        </div>
        <div class="max-w-7xl mx-auto flex flex-col sm:flex-row items-center justify-between text-xs text-gray-400 font-mono">
            <p>&copy; 2026 LexCivic System Frameworks. All rights reserved.</p>
            <div class="flex gap-4 mt-2 sm:mt-0">
                <span class="hover:text-gold cursor-pointer">Privacy Protocol</span>
                <span>•</span>
                <span class="hover:text-gold cursor-pointer">Terms of Service</span>
            </div>
        </div>
    </footer>

    <!-- INTERACTIVE VIEW CONTROL SCRIPT -->
    <script>
        function switchView(viewId) {
            // Hide all views
            const views = document.querySelectorAll('.dynamic-view');
            views.forEach(view => view.classList.add('hidden'));
            
            // Show requested view
            const target = document.getElementById(viewId);
            if(target) {
                target.classList.remove('hidden');
                window.scrollTo({ top: 0, behavior: 'smooth' });
            }

            // Close mobile menu if open
            document.getElementById('mobile-menu').classList.add('hidden');
        }

        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            menu.classList.toggle('hidden');
        }

        function goToVerificationStep(step) {
            // Hide panels
            document.getElementById('panel-step1').classList.add('hidden');
            document.getElementById('panel-step2').classList.add('hidden');
            document.getElementById('panel-step3').classList.add('hidden');

            // Reset tab styles
            document.getElementById('tab-step1').className = "flex-1 py-3 bg-gray-50";
            document.getElementById('tab-step2').className = "flex-1 py-3 bg-gray-50";
            document.getElementById('tab-step3').className = "flex-1 py-3 bg-gray-50";

            // Activate specific targets
            document.getElementById('panel-step' + step).classList.remove('hidden');
            
            const activeTab = document.getElementById('tab-step' + step);
            activeTab.classList.add('border-b-2', 'border-gold', 'text-navy', 'font-bold');
        }

        function filterIssues() {
            const selectedValue = document.getElementById('filter-category').value;
            const cards = document.querySelectorAll('.issue-card');

            cards.forEach(card => {
                if (selectedValue === 'all' || card.getAttribute('data-cat') === selectedValue) {
                    card.classList.remove('hidden');
                } else {
                    card.classList.add('hidden');
                }
            });
        }

        function toggleUpvote(button) {
            const countSpan = button.querySelector('.vote-count');
            let votes = parseInt(countSpan.textContent);
            
            if(button.classList.contains('text-navy')) {
                button.classList.remove('text-navy', 'bg-gold/30');
                votes--;
            } else {
                button.classList.add('text-navy', 'bg-gold/30');
                votes++;
            }
            countSpan.textContent = votes;
        }
    </script>
</body>
</html>

