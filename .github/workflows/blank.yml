<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UGC Creator | High-End Cinematic Portfolio & Services</title>
    
    <!-- Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;700&family=Syncopate:wght@700&display=swap" rel="stylesheet">
    
    <!-- GSAP & Vanilla Tilt -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vanilla-tilt/1.8.0/vanilla-tilt.min.js"></script>

    <style>
        :root {
            --bg-void: #050505;
            --text-stark: #F4F4F5;
            --text-muted: #A1A1AA;
            --accent-amber: #F59E0B;
            --font-main: 'Space Grotesk', sans-serif;
            --font-head: 'Syncopate', sans-serif;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            cursor: none; /* Custom cursor everywhere */
        }

        body {
            background-color: var(--bg-void);
            color: var(--text-stark);
            font-family: var(--font-main);
            overflow-x: hidden;
            scroll-behavior: smooth;
        }

        /* Views management */
        .fade-view {
            transition: opacity 0.5s ease-out;
            opacity: 1;
        }
        .fade-view.hidden {
            display: none;
            opacity: 0;
        }

        /* Custom Cursor */
        .cursor {
            position: fixed;
            width: 20px;
            height: 20px;
            border: 2px solid var(--accent-amber);
            border-radius: 50%;
            pointer-events: none;
            transform: translate(-50%, -50%);
            transition: width 0.2s, height 0.2s, background 0.2s;
            z-index: 9999;
        }
        
        .cursor.hovered {
            width: 50px;
            height: 50px;
            background: rgba(245, 158, 11, 0.1);
        }

        /* Loading Screen */
        .loader-wrapper {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: var(--bg-void);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .loader-glow {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            box-shadow: 0 0 30px var(--accent-amber);
            animation: pulse 1.5s infinite alternate;
        }

        @keyframes pulse {
            0% { transform: scale(0.8); opacity: 0.5; }
            100% { transform: scale(1.2); opacity: 1; }
        }

        /* Header */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 20px 5vw;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(to bottom, var(--bg-void), transparent);
            z-index: 900;
            opacity: 0;
            transform: translateY(-20px);
        }

        .logo {
            font-family: var(--font-head);
            font-size: 1.2rem;
            color: var(--accent-amber);
        }

        .admin-link {
            color: var(--text-muted);
            text-decoration: none;
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: color 0.3s;
        }

        .admin-link:hover {
            color: var(--text-stark);
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: relative;
            padding: 0 5vw;
        }

        .hero-text {
            flex: 1;
            max-width: 60%;
        }

        h1 {
            font-family: var(--font-head);
            font-size: clamp(2rem, 5.5vw, 6rem);
            line-height: 1.1;
            text-transform: uppercase;
            letter-spacing: -2px;
            margin-bottom: 20px;
            opacity: 0;
            transform: translateY(50px);
        }

        .subtitle {
            color: var(--text-muted);
            font-size: 1.2rem;
            max-width: 600px;
            margin-bottom: 40px;
            opacity: 0;
        }

        .hero-photo {
            flex: 1;
            height: 80vh;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            overflow: visible;
            opacity: 0;
            transform: translateX(50px);
        }

        .hero-photo img {
            max-height: 100%;
            width: auto;
            object-fit: contain;
            border-radius: 10px;
            z-index: 10;
        }

        .hero-aura {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 500px;
            height: 500px;
            background: radial-gradient(circle, rgba(245,158,11,0.1) 0%, rgba(5,5,5,0) 70%);
            z-index: 0;
        }

        /* Videos Section */
        .videos {
            padding: 100px 5vw;
            min-height: 100vh;
        }

        .section-title {
            font-family: var(--font-head);
            font-size: 3rem;
            margin-bottom: 60px;
            color: var(--text-stark);
            opacity: 0;
            transform: translateY(30px);
        }

        .video-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 40px;
        }

        .video-card {
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 20px;
            transform-style: preserve-3d;
            opacity: 0;
            transform: translateY(50px);
        }

        .video-card iframe {
            width: 100%;
            aspect-ratio: 9/16; /* Mobile format by default */
            border-radius: 10px;
            border: none;
            transform: translateZ(20px);
        }

        /* Service & Pricing Cards */
        .services, .pricing {
            padding: 100px 5vw;
        }

        .card-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
        }

        .glass-card {
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 40px;
            transform-style: preserve-3d;
            opacity: 0;
            transform: translateY(50px);
        }

        .glass-card h3 {
            font-size: 2rem;
            margin-bottom: 20px;
            color: var(--text-stark);
            transform: translateZ(30px);
        }

        .glass-card ul {
            list-style: none;
            transform: translateZ(20px);
        }

        .glass-card ul li {
            color: var(--text-muted);
            margin-bottom: 10px;
            padding-left: 20px;
            position: relative;
        }

        .glass-card ul li::before {
            content: '→';
            position: absolute;
            left: 0;
            color: var(--accent-amber);
        }

        .price-text {
            color: var(--accent-amber);
            font-size: 1.5rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-top: 30px;
            display: block;
            transform: translateZ(40px);
        }

        /* Magnetic Button */
        .magnetic-btn {
            padding: 15px 40px;
            background: transparent;
            color: var(--text-stark);
            border: 1px solid var(--accent-amber);
            border-radius: 30px;
            font-size: 1rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            transition: box-shadow 0.3s;
            opacity: 0;
        }

        .magnetic-btn:hover {
            box-shadow: 0 0 20px rgba(245, 158, 11, 0.4);
            background: rgba(245, 158, 11, 0.1);
        }

        /* Admin Panel Styles */
        aside#admin-view {
            padding: 50px 10vw;
            color: var(--text-stark);
        }

        .admin-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 40px;
        }

        .admin-title {
            font-family: var(--font-head);
            font-size: 2rem;
            color: var(--accent-amber);
        }

        .admin-section {
            margin-bottom: 40px;
            border: 1px solid rgba(255,255,255,0.1);
            padding: 30px;
            border-radius: 15px;
        }

        .admin-section h3 {
            margin-bottom: 20px;
            font-size: 1.2rem;
            color: var(--text-muted);
        }

        .admin-input-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            color: var(--text-muted);
            font-size: 0.9rem;
        }

        input[type="text"], textarea {
            width: 100%;
            padding: 12px;
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 8px;
            color: var(--text-stark);
            font-family: var(--font-main);
        }

        textarea {
            resize: vertical;
            height: 120px;
        }

        .admin-video-list {
            list-style: none;
            margin-bottom: 20px;
        }

        .admin-video-list li {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(255,255,255,0.02);
            padding: 10px;
            margin-bottom: 8px;
            border-radius: 5px;
        }

        .remove-video {
            color: #ef4444;
            cursor: pointer;
            font-size: 0.8rem;
            text-transform: uppercase;
        }

        .admin-save-btn {
            background-color: var(--accent-amber);
            color: #000;
            border: none;
            padding: 15px 30px;
            border-radius: 30px;
            font-weight: 700;
            cursor: pointer;
            text-transform: uppercase;
        }

        .logout-btn {
            background-color: #ef4444;
            color: #fff;
            border: none;
            padding: 10px 20px;
            border-radius: 20px;
            cursor: pointer;
            text-transform: uppercase;
        }

        /* Mobile Optimization */
        @media (max-width: 768px) {
            .hero {
                flex-direction: column-reverse;
                justify-content: center;
                height: auto;
                padding-top: 100px;
                padding-bottom: 50px;
            }
            .hero-text {
                max-width: 100%;
                text-align: center;
            }
            .hero-photo {
                height: 50vh;
                margin-bottom: 40px;
            }
            .video-grid {
                grid-template-columns: 1fr;
            }
            .card-grid {
                grid-template-columns: 1fr;
            }
            .video-card iframe {
                aspect-ratio: 9/16; /* Mobile format enforced */
            }
        }
    </style>
</head>
<body class="dark-void">

    <!-- Custom Cursor -->
    <div class="cursor"></div>

    <!-- Cinematic Loader -->
    <div class="loader-wrapper">
        <div class="loader-glow"></div>
    </div>

    <!-- MAIN PORTFOLIO VIEW -->
    <main id="portfolio-view" class="fade-view">
        <header>
            <div class="logo hover-target">UGC_CREATOR</div>
            <a href="#" id="login-admin" class="admin-link hover-target">Admin Portal</a>
        </header>

        <!-- Hero Section -->
        <section class="hero">
            <div class="hero-text">
                <h1>Crafting Authentic Stories<br>Through UGC.</h1>
                <p class="subtitle">ELEVATE YOUR BRAND WITH CREATIVE USER GENERATED CONTENT THAT DRIVES ENGAGEMENT & TRUST.</p>
                <button class="magnetic-btn hover-target">Let's Collaborate</button>
            </div>
            <div class="hero-photo">
                <img src="image_28.png" alt="Professional Portfolio Photo of UGC Creator" class="hover-target">
                <div class="hero-aura"></div>
            </div>
        </section>

        <!-- UGC Videos Section -->
        <section id="videos" class="videos">
            <h2 class="section-title hover-target">Video Engineering</h2>
            <div id="portfolio-video-grid" class="video-grid">
                <!-- Video cards will be dynamically rendered from JSON here -->
            </div>
        </section>

        <!-- UGC Services Section -->
        <section id="services" class="services">
            <div class="card-grid">
                <div class="glass-card hover-target" data-tilt data-tilt-max="5">
                    <h3>UGC Benefits</h3>
                    <ul id="ugc-benefits-list">
                        <!-- Content rendered from JSON -->
                    </ul>
                </div>
                <div class="glass-card hover-target" data-tilt data-tilt-max="5">
                    <h3>UGC Investment</h3>
                    <span id="ugc-pricing-text" class="price-text">$XXX / Video</span>
                </div>
            </div>
        </section>

        <!-- Website Services Section -->
        <section id="pricing" class="pricing">
            <div class="card-grid">
                <div class="glass-card hover-target" data-tilt data-tilt-max="5">
                    <h3>Website Benefits</h3>
                    <ul id="website-benefits-list">
                        <!-- Content rendered from JSON -->
                    </ul>
                </div>
                <div class="glass-card hover-target" data-tilt data-tilt-max="5">
                    <h3>Website Investment</h3>
                    <span id="website-pricing-text" class="price-text">$XXX / Project</span>
                </div>
            </div>
        </section>
    </main>

    <!-- ADMIN PANEL VIEW (Hidden by default) -->
    <aside id="admin-view" class="fade-view hidden">
        <div class="admin-header">
            <div class="admin-title">Admin Dashboard</div>
            <button id="logout-admin" class="logout-btn hover-target">Logout</button>
        </div>

        <!-- Video Manager -->
        <div class="admin-section">
            <h3>Manage UGC Videos</h3>
            <ul id="admin-video-list" class="admin-video-list">
                <!-- Manage list with remove button -->
            </ul>
            <div class="admin-input-group">
                <label>Add New Video URL (Embed Link):</label>
                <input type="text" id="new-video-url" placeholder="https://www.youtube.com/embed/XXXXXXX">
            </div>
            <button id="add-video-btn" class="admin-save-btn hover-target">Add Video</button>
        </div>

        <!-- Content Editor -->
        <div class="admin-section">
            <h3>Edit Services & Pricing</h3>
            <div class="admin-input-group">
                <label>UGC Benefits (separate benefits with new lines):</label>
                <textarea id="ugc-benefits-editor"></textarea>
            </div>
            <div class="admin-input-group">
                <label>UGC Price:</label>
                <input type="text" id="ugc-price-editor">
            </div>
            <div class="admin-input-group">
                <label>Website Benefits (separate benefits with new lines):</label>
                <textarea id="website-benefits-editor"></textarea>
            </div>
            <div class="admin-input-group">
                <label>Website Price:</label>
                <input type="text" id="website-price-editor">
            </div>
            <button id="save-content-btn" class="admin-save-btn hover-target">Save All Content</button>
        </div>
    </aside>

    <script>
        gsap.registerPlugin(ScrollTrigger);

        // DATA MANAGEMENT (Mock JSON with localStorage for persistent state)
        const defaultData = {
            videos: [
                "https://www.youtube.com/embed/A37ZlyI8VjM?si=m5l6pZcQ5JzC8WJ4&showinfo=0", // Standard video formats in grid
                "https://www.youtube.com/embed/M7lc1UVf-VE?showinfo=0", 
                "https://www.youtube.com/embed/vH7mS9S0tXg?showinfo=0"
            ],
            ugc_benefits: ["AUTHENTIC BRAND INTEGRATION", "INCREASED ENGAGEMENT RATES", "ELEVATED CONSUMER TRUST", "RESONATES WITH GEN Z & MILLENNIALS"],
            ugc_pricing: "$500 / Video",
            website_benefits: ["CUSTOM CINEMATIC DESIGN", "WEBGL INTERACTIVE VISUALS", "GSAP SMOOTH SCROLLING", "MOBILE OPTIMIZED EXPERIENCE"],
            website_pricing: "$2500 / Project"
        };

        let appData = JSON.parse(localStorage.getItem('appData')) || defaultData;

        // Render Functions
        const renderPortfolio = () => {
            // Render videos grid
            const grid = document.getElementById('portfolio-video-grid');
            grid.innerHTML = '';
            appData.videos.forEach(url => {
                grid.innerHTML += `
                    <div class="video-card glass-card hover-target" data-tilt data-tilt-max="5" data-tilt-speed="400" data-tilt-glare="true" data-tilt-max-glare="0.1">
                        <iframe src="${url}" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                    </div>
                `;
            });

            // Render UGC content
            const ugcList = document.getElementById('ugc-benefits-list');
            ugcList.innerHTML = '';
            appData.ugc_benefits.forEach(item => { ugcList.innerHTML += `<li>${item}</li>`; });
            document.getElementById('ugc-pricing-text').innerText = appData.ugc_pricing;

            // Render Website content
            const webList = document.getElementById('website-benefits-list');
            webList.innerHTML = '';
            appData.website_benefits.forEach(item => { webList.innerHTML += `<li>${item}</li>`; });
            document.getElementById('website-pricing-text').innerText = appData.website_pricing;

            // Re-apply tilt effects after rendering
            VanillaTilt.init(document.querySelectorAll(".glass-card"), {
                max: 5,
                speed: 400,
                glare: true,
                "max-glare": 0.1,
                scale: 1.02
            });
            ScrollTrigger.refresh(); // Important for smooth scrolling
        };

        const renderAdmin = () => {
            // Render video list manager
            const adminList = document.getElementById('admin-video-list');
            adminList.innerHTML = '';
            appData.videos.forEach((url, index) => {
                adminList.innerHTML += `
                    <li>
                        <span>${url.substring(0, 40)}...</span>
                        <span class="remove-video remove-button-target" data-index="${index}">Remove</span>
                    </li>
                `;
            });

            // Fill editors
            document.getElementById('ugc-benefits-editor').value = appData.ugc_benefits.join('\n');
            document.getElementById('ugc-price-editor').value = appData.ugc_pricing;
            document.getElementById('website-benefits-editor').value = appData.website_benefits.join('\n');
            document.getElementById('website-price-editor').value = appData.website_pricing;
        };

        // ADMIN PANEL LOGIC (Persistence)
        const saveAppData = () => {
            localStorage.setItem('appData', JSON.stringify(appData));
            renderPortfolio();
        };

        const toggleViews = (showPortfolio) => {
            document.getElementById('portfolio-view').classList.toggle('hidden', !showPortfolio);
            document.getElementById('admin-view').classList.toggle('hidden', showPortfolio);
            window.scrollTo(0, 0);
            renderPortfolio();
            renderAdmin();
        };

        // Custom Cursor Logic
        const cursor = document.querySelector('.cursor');
        document.addEventListener('mousemove', (e) => {
            cursor.style.left = e.clientX + 'px';
            cursor.style.top = e.clientY + 'px';
        });

        const updateCursorHover = () => {
            const targets = document.querySelectorAll('.hover-target, .video-card, iframe');
            targets.forEach(target => {
                target.addEventListener('mouseenter', () => cursor.classList.add('hovered'));
                target.addEventListener('mouseleave', () => cursor.classList.remove('hovered'));
            });
        };

        // Video Manager Events
        document.getElementById('add-video-btn').addEventListener('click', () => {
            const url = document.getElementById('new-video-url').value;
            if (url) {
                appData.videos.push(url);
                document.getElementById('new-video-url').value = '';
                saveAppData();
                renderAdmin();
                updateCursorHover();
            }
        });

        document.getElementById('admin-video-list').addEventListener('click', (e) => {
            if (e.target.classList.contains('remove-video')) {
                const index = e.target.getAttribute('data-index');
                appData.videos.splice(index, 1);
                saveAppData();
                renderAdmin();
            }
        });

        // Content Save Event
        document.getElementById('save-content-btn').addEventListener('click', () => {
            appData.ugc_benefits = document.getElementById('ugc-benefits-editor').value.split('\n').filter(item => item.trim() !== '');
            appData.ugc_pricing = document.getElementById('ugc-price-editor').value;
            appData.website_benefits = document.getElementById('website-benefits-editor').value.split('\n').filter(item => item.trim() !== '');
            appData.website_pricing = document.getElementById('website-price-editor').value;
            saveAppData();
        });

        // View Toggles
        document.getElementById('login-admin').addEventListener('click', (e) => { e.preventDefault(); toggleViews(false); });
        document.getElementById('logout-admin').addEventListener('click', () => toggleViews(true));

        // INTERACTION & ANIMATION LOGIC

        // Cinematic Loading Sequence
        const tlLoad = gsap.timeline();
        tlLoad.to(".loader-glow", { scale: 0, duration: 0.8, ease: "power2.inOut", delay: 1 })
              .to(".loader-wrapper", { opacity: 0, display: "none", duration: 0.5 })
              .to("header", { opacity: 1, y: 0, duration: 1 }, "-=0.2")
              .to(".hero-photo", { opacity: 1, x: 0, duration: 1.2, ease: "power4.out" }, "-=0.8")
              .to("h1", { y: 0, opacity: 1, duration: 1.2, ease: "power4.out" }, "-=1.5")
              .to(".subtitle", { opacity: 1, duration: 1 }, "-=1")
              .to(".magnetic-btn", { opacity: 1, duration: 1 }, "-=0.8");

        // Magnetic Button Logic
        const magBtn = document.querySelector('.magnetic-btn');
        magBtn.addEventListener('mousemove', (e) => {
            const rect = magBtn.getBoundingClientRect();
            const x = (e.clientX - rect.left - rect.width / 2) * 0.3;
            const y = (e.clientY - rect.top - rect.height / 2) * 0.3;
            gsap.to(magBtn, { x: x, y: y, duration: 0.3 });
        });
        magBtn.addEventListener('mouseleave', () => {
            gsap.to(magBtn, { x: 0, y: 0, duration: 0.7, ease: "elastic.out(1, 0.3)" });
        });

        // Smooth Scrolling Animations (Apply to newly rendered elements)
        const applyScrollAnimations = () => {
            gsap.to(".section-title", {
                scrollTrigger: { trigger: ".section-title", start: "top 90%", toggleActions: "play none none reverse" },
                opacity: 1, y: 0, duration: 0.8, ease: "power3.out"
            });

            gsap.utils.toArray('.video-card, .glass-card').forEach((card, i) => {
                gsap.to(card, {
                    scrollTrigger: { trigger: card, start: "top 85%", toggleActions: "play none none reverse" },
                    y: 0, opacity: 1, duration: 0.8, delay: i * 0.1, ease: "power3.out"
                });
            });
        };

        // Initial Initialization
        renderPortfolio();
        applyScrollAnimations();
        updateCursorHover();

        // Ensure tilt effects work on initial load
        VanillaTilt.init(document.querySelectorAll(".glass-card, .video-card"), {
            max: 5,
            speed: 400,
            glare: true,
            "max-glare": 0.1,
            scale: 1.02
        });

    </script>
</body>
</html>
