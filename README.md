# Thiranex_WD_02
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Advanced responsive CSS3 personal portfolio.">
    <title>Responsive Architecture Portfolio</title>
    
    <style>
        /* ==========================================================================
           1. CSS CUSTOM VARIABLES (Dynamic Themes)
           ========================================================================== */
        :root {
            /* Light Theme Variables (Default) */
            --bg-color: #f8f9fa;
            --surface-color: #ffffff;
            --text-color: #212529;
            --primary-color: #0056b3;
            --accent-color: #e9ecef;
            --border-color: #dee2e6;
            --transition-speed: 0.3s;
        }

        [data-theme="dark"] {
            /* Dark Theme Variables */
            --bg-color: #121212;
            --surface-color: #1e1e1e;
            --text-color: #f8f9fa;
            --primary-color: #3792ff;
            --accent-color: #2d2d2d;
            --border-color: #444444;
        }

        /* Reset and Base Styles */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: system-ui, -apple-system, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            transition: background-color var(--transition-speed), color var(--transition-speed);
            line-height: 1.6;
        }

        /* Accessibility Skip Link */
        .skip-link {
            position: absolute;
            top: -100px;
            left: 10px;
            background: var(--primary-color);
            color: white;
            padding: 10px;
            z-index: 100;
            text-decoration: none;
        }
        .skip-link:focus { top: 10px; }

        /* ==========================================================================
           2. TWO-DIMENSIONAL PAGE LAYOUT (CSS Grid - Desktop First Architecture)
           ========================================================================== */
        .site-container {
            display: grid;
            grid-template-areas: 
                "header"
                "main"
                "footer";
            grid-template-rows: auto 1fr auto;
            min-height: 100vh;
        }

        header { grid-area: header; }
        main { grid-area: main; }
        footer { grid-area: footer; }

        /* Inner Content Grid (Main Content Layout) */
        main {
            display: grid;
            grid-template-columns: 1fr;
            gap: 2rem;
            padding: 2rem 1rem;
            max-width: 1200px;
            margin: 0 auto;
            width: 100%;
        }

        /* ==========================================================================
           3. LOCALIZED COMPONENT ALIGNMENT (Flexbox)
           ========================================================================== */
        /* Header Flexbox Alignment */
        header {
            background-color: var(--surface-color);
            border-bottom: 1px solid var(--border-color);
            padding: 1rem 2rem;
            display: flex;
            flex-direction: column;
            gap: 1rem;
            align-items: center;
        }

        /* Navigation Menu (Flexbox) */
        nav ul {
            display: flex;
            list-style: none;
            gap: 1.5rem;
        }

        nav a {
            color: var(--text-color);
            text-decoration: none;
            font-weight: 500;
            transition: color var(--transition-speed);
        }

        nav a:hover, nav a[aria-current="page"] {
            color: var(--primary-color);
        }

        /* Utility controls (Theme Switcher Button) */
        .theme-toggle-btn {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 600;
        }

        /* Cards Layout inside Main (Grid for dynamic content sizing) */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
        }

        /* Styled Components (Surface design) */
        section, article {
            background-color: var(--surface-color);
            border: 1px solid var(--border-color);
            padding: 1.5rem;
            border-radius: 8px;
        }

        /* Form Components (Flexbox stacking layout) */
        .form-group {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
            margin-bottom: 1rem;
        }

        input, textarea {
            padding: 0.75rem;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            background-color: var(--bg-color);
            color: var(--text-color);
            font-size: 1rem;
        }

        button[type="submit"] {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            border-radius: 4px;
            font-size: 1rem;
            cursor: pointer;
            width: 100%;
        }

        /* Footer Alignment (Flexbox layout) */
        footer {
            background-color: var(--surface-color);
            border-top: 1px solid var(--border-color);
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 1rem;
            text-align: center;
        }

        /* ==========================================================================
           4. MOBILE-FIRST RESPONSIVE MEDIA QUERIES
           ========================================================================== */
        
        /* Tablet Breakpoint (min-width: 768px) */
        @media (min-width: 768px) {
            header {
                flex-direction: row;
                justify-content: space-between;
            }

            footer {
                flex-direction: row;
                justify-content: space-between;
            }
            
            button[type="submit"] {
                width: auto;
            }
        }

        /* Desktop Breakpoint (min-width: 1024px) */
        @media (min-width: 1024px) {
            main {
                /* Transform content section layout to multi-column Grid on wide viewports */
                grid-template-columns: 2fr 1fr;
                align-items: start;
            }
            
            .full-width {
                grid-column: span 2;
            }
        }
    </style>
</head>
<body>

    <a href="#main-content" class="skip-link">Skip to main content</a>

    <div class="site-container">
        <header role="banner">
            <div class="logo-area">
                <h1>DevPortfolio</h1>
            </div>
            <nav aria-label="Main Navigation">
                <ul>
                    <li><a href="#" aria-current="page">Home</a></li>
                    <li><a href="#">Projects</a></li>
                    <li><a href="#">Contact</a></li>
                </ul>
            </nav>
            <button class="theme-toggle-btn" id="themeToggle" aria-label="Toggle dark/light display mode">Toggle Theme</button>
        </header>

        <main id="main-content" role="main">
            
            <div class="primary-content-flow">
                <section aria-labelledby="intro-heading" style="margin-bottom: 2rem;">
                    <h2 id="intro-heading">Advanced CSS3 Architecture</h2>
                    <p>Welcome! This layout utilizes two-dimensional CSS Grid layouts alongside fluid flexbox sub-structures to pass all major viewport standards flawlessly.</p>
                </section>

                <section aria-labelledby="projects-heading">
                    <h2 id="projects-heading" style="margin-bottom: 1rem;">Projects</h2>
                    <div class="projects-grid">
                        <article>
                            <h3>Grid Component A</h3>
                            <p>Adapts perfectly inside parent boundaries using modern multi-column auto-fit rules.</p>
                        </article>
                        <article>
                            <h3>Grid Component B</h3>
                            <p>Adapts perfectly inside parent boundaries using modern multi-column auto-fit rules.</p>
                        </article>
                    </div>
                </section>
            </div>

            <aside class="sidebar-flow">
                <section aria-labelledby="contact-heading">
                    <h2 id="contact-heading">Get in Touch</h2>
                    <form aria-label="Contact form">
                        <div class="form-group">
                            <label for="name">Name</label>
                            <input type="text" id="name" required>
                        </div>
                        <div class="form-group">
                            <label for="email">Email</label>
                            <input type="email" id="email" required>
                        </div>
                        <button type="submit">Submit Work</button>
                    </form>
                </section>
            </aside>

        </main>

        <footer role="contentinfo">
            <p>&copy; 2026 Skills Portfolio Project. Built with Responsive CSS3 Architecture.</p>
            <nav aria-label="Social Media Links">
                <ul>
                    <li><a href="#">GitHub</a></li>
                    <li><a href="#">LinkedIn</a></li>
                </ul>
            </nav>
        </footer>
    </div>

    <script>
        const toggleBtn = document.getElementById('themeToggle');
        toggleBtn.addEventListener('click', () => {
            const currentTheme = document.documentElement.getAttribute('data-theme');
            if (currentTheme === 'dark') {
                document.documentElement.removeAttribute('data-theme');
            } else {
                document.documentElement.setAttribute('data-theme', 'dark');
            }
        });
    </script>
</body>
</html>
