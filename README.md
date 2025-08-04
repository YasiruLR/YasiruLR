<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yasiru - Connect With Me</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Noto Sans', Helvetica, Arial, sans-serif;
            background: linear-gradient(135deg, #0d1117 0%, #21262d 100%);
            min-height: 100vh;
            color: #c9d1d9;
            overflow-x: hidden;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 2rem;
            position: relative;
        }

        .background-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .floating-element {
            position: absolute;
            width: 4px;
            height: 4px;
            background: #58a6ff;
            border-radius: 50%;
            animation: float 15s infinite linear;
            opacity: 0.1;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.1;
            }
            90% {
                opacity: 0.1;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }

        .header {
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
        }

        .profile-section {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-bottom: 2rem;
        }

        .avatar {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            background: linear-gradient(45deg, #58a6ff, #7c3aed);
            padding: 3px;
            margin-bottom: 1rem;
            position: relative;
            overflow: hidden;
        }

        .avatar::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, #58a6ff, #7c3aed, #f97316, #ec4899);
            border-radius: 50%;
            animation: rotate 3s linear infinite;
            z-index: -1;
        }

        .avatar-inner {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: #21262d;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.5rem;
            font-weight: bold;
            color: #58a6ff;
            position: relative;
            z-index: 1;
        }

        @keyframes rotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .name {
            font-size: 2.5rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
            background: linear-gradient(45deg, #58a6ff, #7c3aed);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .subtitle {
            font-size: 1.2rem;
            color: #8b949e;
            margin-bottom: 2rem;
        }

        .social-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .social-card {
            background: rgba(33, 38, 45, 0.8);
            border: 1px solid #30363d;
            border-radius: 12px;
            padding: 1.5rem;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(10px);
        }

        .social-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--accent-color), transparent);
            transform: translateX(-100%);
            transition: transform 0.3s ease;
        }

        .social-card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-color);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        .social-card:hover::before {
            transform: translateX(100%);
        }

        .social-link {
            text-decoration: none;
            color: inherit;
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .social-icon {
            width: 50px;
            height: 50px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            color: white;
            flex-shrink: 0;
        }

        .social-info h3 {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
            color: #f0f6fc;
        }

        .social-info p {
            color: #8b949e;
            font-size: 0.9rem;
        }

        /* Platform specific colors */
        .github { --accent-color: #6e7681; }
        .github .social-icon { background: linear-gradient(45deg, #24292f, #6e7681); }

        .linkedin { --accent-color: #0077b5; }
        .linkedin .social-icon { background: linear-gradient(45deg, #0077b5, #00a0dc); }

        .twitter { --accent-color: #1da1f2; }
        .twitter .social-icon { background: linear-gradient(45deg, #1da1f2, #1991db); }

        .instagram { --accent-color: #e4405f; }
        .instagram .social-icon { background: linear-gradient(45deg, #e4405f, #fd1d1d, #fcb045); }

        .youtube { --accent-color: #ff0000; }
        .youtube .social-icon { background: linear-gradient(45deg, #ff0000, #cc0000); }

        .medium { --accent-color: #00ab6c; }
        .medium .social-icon { background: linear-gradient(45deg, #00ab6c, #00d084); }

        .stackoverflow { --accent-color: #f48024; }
        .stackoverflow .social-icon { background: linear-gradient(45deg, #f48024, #fe7a16); }

        .portfolio { --accent-color: #7c3aed; }
        .portfolio .social-icon { background: linear-gradient(45deg, #7c3aed, #a855f7); }

        .footer {
            text-align: center;
            margin-top: 3rem;
            padding-top: 2rem;
            border-top: 1px solid #30363d;
            color: #8b949e;
        }

        .footer p {
            margin-bottom: 0.5rem;
        }

        .tech-stack {
            display: flex;
            justify-content: center;
            gap: 1rem;
            flex-wrap: wrap;
            margin-top: 1rem;
        }

        .tech-item {
            background: rgba(88, 166, 255, 0.1);
            border: 1px solid rgba(88, 166, 255, 0.3);
            padding: 0.5rem 1rem;
            border-radius: 20px;
            font-size: 0.8rem;
            color: #58a6ff;
        }

        /* Mobile responsiveness */
        @media (max-width: 768px) {
            .container {
                padding: 1rem;
            }
            
            .name {
                font-size: 2rem;
            }
            
            .social-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="background-animation" id="backgroundAnimation"></div>
    
    <div class="container">
        <div class="header">
            <div class="profile-section">
                <div class="avatar">
                    <div class="avatar-inner">Y</div>
                </div>
                <h1 class="name">Yasiru Lakshan</h1>
                <p class="subtitle">Software Engineer | Full Stack Developer | Open Source Enthusiast</p>
            </div>
        </div>

        <div class="social-grid">
            <div class="social-card github">
                <a href="https://github.com/yasirulakshan" class="social-link" target="_blank" rel="noopener">
                    <div class="social-icon">
                        <i>📱</i>
                    </div>
                    <div class="social-info">
                        <h3>GitHub</h3>
                        <p>Check out my code repositories and open source contributions</p>
                    </div>
                </a>
            </div>

            <div class="social-card linkedin">
                <a href="https://linkedin.com/in/yasirulakshan" class="social-link" target="_blank" rel="noopener">
                    <div class="social-icon">
                        <i>💼</i>
                    </div>
                    <div class="social-info">
                        <h3>LinkedIn</h3>
                        <p>Connect with me professionally and see my work experience</p>
                    </div>
                </a>
            </div>

            <div class="social-card twitter">
                <a href="https://twitter.com/yasirulakshan" class="social-link" target="_blank" rel="noopener">
                    <div class="social-icon">
                        <i>🐦</i>
                    </div>
                    <div class="social-info">
                        <h3>Twitter</h3>
                        <p>Follow me for tech insights and development updates</p>
                    </div>
                </a>
            </div>

            <div class="social-card instagram">
                <a href="https://instagram.com/yasirulakshan" class="social-link" target="_blank" rel="noopener">
                    <div class="social-icon">
                        <i>📸</i>
                    </div>
                    <div class="social-info">
                        <h3>Instagram</h3>
                        <p>Get a glimpse into my personal life and travel adventures</p>
                    </div>
                </a>
            </div>

            <div class="social-card youtube">
                <a href="https://youtube.com/@yasirulakshan" class="social-link" target="_blank" rel="noopener">
                    <div class="social-icon">
                        <i>🎥</i>
                    </div>
                    <div class="social-info">
                        <h3>YouTube</h3>
                        <p>Watch my coding tutorials and tech content</p>
                    </div>
                </a>
            </div>

            <div class="social-card medium">
                <a href="https://medium.com/@yasirulakshan" class="social-link" target="_blank" rel="noopener">
                    <div class="social-icon">
                        <i>✍️</i>
                    </div>
                    <div class="social-info">
                        <h3>Medium</h3>
                        <p>Read my technical articles and development insights</p>
                    </div>
                </a>
            </div>

            <div class="social-card stackoverflow">
                <a href="https://stackoverflow.com/users/yasirulakshan" class="social-link" target="_blank" rel="noopener">
                    <div class="social-icon">
                        <i>❓</i>
                    </div>
                    <div class="social-info">
                        <h3>Stack Overflow</h3>
                        <p>See my contributions to the developer community</p>
                    </div>
                </a>
            </div>

            <div class="social-card portfolio">
                <a href="https://yasirulr.me" class="social-link" target="_blank" rel="noopener">
                    <div class="social-icon">
                        <i>🌐</i>
                    </div>
                    <div class="social-info">
                        <h3>Portfolio</h3>
                        <p>Explore my complete portfolio and featured projects</p>
                    </div>
                </a>
            </div>
        </div>

        <div class="footer">
            <p>Thanks for connecting! Let's build something amazing together.</p>
            <div class="tech-stack">
                <span class="tech-item">React</span>
                <span class="tech-item">Node.js</span>
                <span class="tech-item">Python</span>
                <span class="tech-item">TypeScript</span>
                <span class="tech-item">AWS</span>
            </div>
            <p style="margin-top: 2rem; font-size: 0.8rem;">© 2025 Yasiru Lakshan. Made with ❤️</p>
        </div>
    </div>

    <script>
        // Create floating background elements
        function createFloatingElements() {
            const container = document.getElementById('backgroundAnimation');
            const numberOfElements = 15;

            for (let i = 0; i < numberOfElements; i++) {
                const element = document.createElement('div');
                element.className = 'floating-element';
                element.style.left = Math.random() * 100 + '%';
                element.style.animationDelay = Math.random() * 15 + 's';
                element.style.animationDuration = (Math.random() * 10 + 10) + 's';
                container.appendChild(element);
            }
        }

        // Add hover effects to social cards
        document.querySelectorAll('.social-card').forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-8px) scale(1.02)';
            });
            
            card.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0) scale(1)';
            });
        });

        // Initialize floating elements
        createFloatingElements();

        // Add some interactive sparkles on click
        document.addEventListener('click', function(e) {
            const sparkle = document.createElement('div');
            sparkle.style.position = 'fixed';
            sparkle.style.left = e.clientX + 'px';
            sparkle.style.top = e.clientY + 'px';
            sparkle.style.width = '10px';
            sparkle.style.height = '10px';
            sparkle.style.background = '#58a6ff';
            sparkle.style.borderRadius = '50%';
            sparkle.style.pointerEvents = 'none';
            sparkle.style.zIndex = '1000';
            sparkle.style.animation = 'sparkle 0.6s ease-out forwards';
            
            document.body.appendChild(sparkle);
            
            setTimeout(() => {
                sparkle.remove();
            }, 600);
        });

        // Add sparkle animation
        const style = document.createElement('style');
        style.textContent = `
            @keyframes sparkle {
                0% {
                    transform: scale(0) rotate(0deg);
                    opacity: 1;
                }
                50% {
                    transform: scale(1) rotate(180deg);
                    opacity: 0.8;
                }
                100% {
                    transform: scale(0) rotate(360deg);
                    opacity: 0;
                }
            }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html>
