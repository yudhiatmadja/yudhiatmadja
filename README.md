<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yudhi - Interactive Developer Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            overflow-x: hidden;
        }

        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .star {
            position: absolute;
            background: white;
            border-radius: 50%;
            animation: twinkle 3s infinite alternate;
        }

        @keyframes twinkle {
            0% { opacity: 0.3; transform: scale(0.8); }
            100% { opacity: 1; transform: scale(1.2); }
        }

        .container {
            position: relative;
            z-index: 2;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .hero {
            text-align: center;
            padding: 60px 0;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 20px;
            margin-bottom: 40px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .hero h1 {
            font-size: 3.5em;
            margin-bottom: 20px;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { filter: drop-shadow(0 0 20px rgba(255, 107, 107, 0.5)); }
            to { filter: drop-shadow(0 0 30px rgba(78, 205, 196, 0.8)); }
        }

        .typing-text {
            font-size: 1.5em;
            color: #4ecdc4;
            margin-bottom: 30px;
            min-height: 60px;
        }

        .cursor {
            animation: blink 1s infinite;
        }

        @keyframes blink {
            50% { opacity: 0; }
        }

        .profile-stats {
            display: flex;
            justify-content: center;
            gap: 40px;
            margin-top: 30px;
            flex-wrap: wrap;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .stat-number {
            font-size: 2.5em;
            font-weight: bold;
            color: #ff6b6b;
        }

        .tech-section {
            margin: 60px 0;
        }

        .section-title {
            font-size: 2.5em;
            text-align: center;
            margin-bottom: 40px;
            color: #4ecdc4;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-bottom: 40px;
        }

        .tech-category {
            background: rgba(0, 0, 0, 0.4);
            padding: 30px;
            border-radius: 20px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: transform 0.3s ease;
        }

        .tech-category:hover {
            transform: scale(1.05);
        }

        .tech-category h3 {
            font-size: 1.5em;
            margin-bottom: 20px;
            color: #ff6b6b;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .tech-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }

        .tech-tag {
            background: linear-gradient(45deg, #667eea, #764ba2);
            padding: 8px 16px;
            border-radius: 25px;
            font-size: 0.9em;
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .tech-tag:hover {
            transform: scale(1.1);
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            box-shadow: 0 5px 15px rgba(255, 107, 107, 0.4);
        }

        .pixel-art-section {
            text-align: center;
            margin: 60px 0;
            padding: 40px;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 20px;
        }

        .pixel-gallery {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 30px;
            flex-wrap: wrap;
        }

        .pixel-frame {
            width: 200px;
            height: 200px;
            border: 4px solid #4ecdc4;
            border-radius: 15px;
            overflow: hidden;
            transition: transform 0.3s ease;
            position: relative;
        }

        .pixel-frame:hover {
            transform: scale(1.1) rotate(5deg);
        }

        .pixel-frame::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, transparent 49%, rgba(255, 255, 255, 0.1) 50%, transparent 51%);
            animation: scan 2s linear infinite;
        }

        @keyframes scan {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        .about-section {
            background: rgba(0, 0, 0, 0.4);
            padding: 40px;
            border-radius: 20px;
            margin: 40px 0;
        }

        .about-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }

        .about-item {
            display: flex;
            align-items: center;
            gap: 15px;
            padding: 15px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            transition: transform 0.3s ease;
        }

        .about-item:hover {
            transform: translateX(10px);
        }

        .about-icon {
            font-size: 2em;
            color: #ff6b6b;
        }

        .connect-section {
            text-align: center;
            margin: 60px 0;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 30px;
            flex-wrap: wrap;
        }

        .social-link {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 15px 25px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            transition: all 0.3s ease;
            border: 2px solid transparent;
        }

        .social-link:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            border-color: rgba(255, 255, 255, 0.3);
        }

        .code-section {
            background: rgba(0, 0, 0, 0.6);
            padding: 30px;
            border-radius: 15px;
            margin: 40px 0;
            border-left: 4px solid #4ecdc4;
        }

        .code-block {
            background: #1a1a1a;
            padding: 20px;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            color: #4ecdc4;
            overflow-x: auto;
            position: relative;
        }

        .code-block::before {
            content: '⚡ Fun Fact';
            position: absolute;
            top: -10px;
            left: 20px;
            background: #ff6b6b;
            padding: 5px 15px;
            border-radius: 5px;
            font-size: 0.8em;
            font-family: 'Segoe UI', sans-serif;
        }

        .floating-elements {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .floating-icon {
            position: absolute;
            font-size: 2em;
            opacity: 0.1;
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }

        .interactive-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at var(--x, 50%) var(--y, 50%), rgba(255, 107, 107, 0.1) 0%, transparent 50%);
            pointer-events: none;
            z-index: 0;
        }

        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5em;
            }
            
            .profile-stats {
                gap: 20px;
            }
            
            .tech-grid {
                grid-template-columns: 1fr;
            }
            
            .social-links {
                flex-direction: column;
                align-items: center;
            }
        }
    </style>
</head>
<body>
    <div class="stars"></div>
    <div class="floating-elements"></div>
    <div class="interactive-bg"></div>

    <div class="container">
        <div class="hero">
            <h1>👋 Hi there, I'm Yudhi!</h1>
            <div class="typing-text" id="typing-text"></div>
            <div class="profile-stats">
                <div class="stat-card">
                    <div class="stat-number" id="projects-count">0</div>
                    <div>Projects Built</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number" id="tech-count">0</div>
                    <div>Technologies</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number" id="experience-count">0</div>
                    <div>Years Coding</div>
                </div>
            </div>
        </div>

        <div class="tech-section">
            <h2 class="section-title">🚀 Tech Arsenal</h2>
            <div class="tech-grid">
                <div class="tech-category">
                    <h3>💻 Full-Stack Development</h3>
                    <div class="tech-tags">
                        <span class="tech-tag">Laravel</span>
                        <span class="tech-tag">Next.js</span>
                        <span class="tech-tag">Express.js</span>
                        <span class="tech-tag">Node.js</span>
                        <span class="tech-tag">Flutter</span>
                        <span class="tech-tag">Tailwind CSS</span>
                        <span class="tech-tag">Bootstrap</span>
                    </div>
                </div>

                <div class="tech-category">
                    <h3>🎮 Game Development</h3>
                    <div class="tech-tags">
                        <span class="tech-tag">Unity</span>
                        <span class="tech-tag">Unreal Engine</span>
                        <span class="tech-tag">Blender</span>
                        <span class="tech-tag">C#</span>
                        <span class="tech-tag">Game Physics</span>
                        <span class="tech-tag">3D Modeling</span>
                    </div>
                </div>

                <div class="tech-category">
                    <h3>🔥 Backend & Database</h3>
                    <div class="tech-tags">
                        <span class="tech-tag">PHP</span>
                        <span class="tech-tag">MySQL</span>
                        <span class="tech-tag">Firebase</span>
                        <span class="tech-tag">Supabase</span>
                        <span class="tech-tag">Docker</span>
                        <span class="tech-tag">Linux</span>
                    </div>
                </div>

                <div class="tech-category">
                    <h3>📱 Mobile & Languages</h3>
                    <div class="tech-tags">
                        <span class="tech-tag">Kotlin</span>
                        <span class="tech-tag">Dart</span>
                        <span class="tech-tag">Java</span>
                        <span class="tech-tag">JavaScript</span>
                        <span class="tech-tag">Python</span>
                        <span class="tech-tag">HTML5</span>
                        <span class="tech-tag">CSS3</span>
                    </div>
                </div>
            </div>
        </div>

        <div class="pixel-art-section">
            <h2 class="section-title">🎨 Pixel Art & Animation</h2>
            <div class="pixel-gallery">
                <div class="pixel-frame">
                    <img src="https://media.giphy.com/media/QTfX9Ejfra3ZmNxh6B/giphy.gif" alt="Pixel Art 1" style="width: 100%; height: 100%; object-fit: cover;">
                </div>
                <div class="pixel-frame">
                    <img src="https://media.giphy.com/media/kH6CqYiquZawmU1HI6/giphy.gif" alt="Pixel Art 2" style="width: 100%; height: 100%; object-fit: cover;">
                </div>
                <div class="pixel-frame">
                    <img src="https://media.giphy.com/media/l3vR85PnGsBwu1PFK/giphy.gif" alt="Pixel Art 3" style="width: 100%; height: 100%; object-fit: cover;">
                </div>
            </div>
        </div>

        <div class="about-section">
            <h2 class="section-title">✨ About Me</h2>
            <div class="about-grid">
                <div class="about-item">
                    <div class="about-icon">🏗️</div>
                    <div>Full-Stack Developer & Game Developer</div>
                </div>
                <div class="about-item">
                    <div class="about-icon">🚀</div>
                    <div>Exploring AI & Game Physics</div>
                </div>
                <div class="about-item">
                    <div class="about-icon">🎯</div>
                    <div>Building with Modern Tech Stack</div>
                </div>
                <div class="about-item">
                    <div class="about-icon">📚</div>
                    <div>Passionate Lifelong Learner</div>
                </div>
                <div class="about-item">
                    <div class="about-icon">🎨</div>
                    <div>UI Design & Interactive Apps</div>
                </div>
                <div class="about-item">
                    <div class="about-icon">🏆</div>
                    <div>Always Seeking New Challenges</div>
                </div>
            </div>
        </div>

        <div class="connect-section">
            <h2 class="section-title">🌐 Let's Connect!</h2>
            <div class="social-links">
                <a href="https://www.instagram.com/yudhiiatmadja/" target="_blank" class="social-link">
                    <span>📸</span> Instagram
                </a>
                <a href="https://www.linkedin.com/in/yudhiiatmadja/" target="_blank" class="social-link">
                    <span>💼</span> LinkedIn
                </a>
                <a href="https://im-yudhi.vercel.app/" target="_blank" class="social-link">
                    <span>🌐</span> Portfolio
                </a>
                <a href="https://yudhiatmadja.itch.io/" target="_blank" class="social-link">
                    <span>🎮</span> Itch.io
                </a>
            </div>
        </div>

        <div class="code-section">
            <div class="code-block">
                <pre id="code-animation"></pre>
            </div>
        </div>
    </div>

    <script>
        // Typing animation
        const typingText = document.getElementById('typing-text');
        const texts = [
            "Lifelong learner passionate about code 💻",
            "Full-Stack Developer & Game Creator 🎮",
            "Building the future, one line at a time 🚀",
            "Turning ideas into interactive experiences ✨"
        ];
        let currentText = 0;
        let currentChar = 0;
        let isDeleting = false;

        function typeText() {
            const current = texts[currentText];
            
            if (isDeleting) {
                typingText.innerHTML = current.substring(0, currentChar - 1) + '<span class="cursor">|</span>';
                currentChar--;
                
                if (currentChar === 0) {
                    isDeleting = false;
                    currentText = (currentText + 1) % texts.length;
                    setTimeout(typeText, 500);
                } else {
                    setTimeout(typeText, 50);
                }
            } else {
                typingText.innerHTML = current.substring(0, currentChar + 1) + '<span class="cursor">|</span>';
                currentChar++;
                
                if (currentChar === current.length) {
                    isDeleting = true;
                    setTimeout(typeText, 2000);
                } else {
                    setTimeout(typeText, 100);
                }
            }
        }

        typeText();

        // Animated counters
        function animateCounter(element, target, duration = 2000) {
            let start = 0;
            const increment = target / (duration / 16);
            const timer = setInterval(() => {
                start += increment;
                element.textContent = Math.floor(start);
                if (start >= target) {
                    element.textContent = target;
                    clearInterval(timer);
                }
            }, 16);
        }

        // Start counters when page loads
        setTimeout(() => {
            animateCounter(document.getElementById('projects-count'), 42);
            animateCounter(document.getElementById('tech-count'), 20);
            animateCounter(document.getElementById('experience-count'), 5);
        }, 1000);

        // Create floating stars
        function createStars() {
            const starsContainer = document.querySelector('.stars');
            for (let i = 0; i < 100; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.style.width = Math.random() * 3 + 1 + 'px';
                star.style.height = star.style.width;
                star.style.left = Math.random() * 100 + '%';
                star.style.top = Math.random() * 100 + '%';
                star.style.animationDelay = Math.random() * 3 + 's';
                starsContainer.appendChild(star);
            }
        }

        // Create floating tech icons
        function createFloatingIcons() {
            const container = document.querySelector('.floating-elements');
            const icons = ['💻', '🎮', '🚀', '⚡', '🔥', '🎨', '📱', '🛠️'];
            
            for (let i = 0; i < 12; i++) {
                const icon = document.createElement('div');
                icon.className = 'floating-icon';
                icon.textContent = icons[Math.floor(Math.random() * icons.length)];
                icon.style.left = Math.random() * 100 + '%';
                icon.style.top = Math.random() * 100 + '%';
                icon.style.animationDelay = Math.random() * 6 + 's';
                icon.style.animationDuration = (Math.random() * 4 + 4) + 's';
                container.appendChild(icon);
            }
        }

        // Code animation
        const codeLines = [
            "const life = ['Code', 'Game', 'Eat', 'Repeat'];",
            "const passion = ['AI', 'GameDev', 'FullStack'];",
            "const tools = ['Unity', 'Laravel', 'Flutter'];",
            "",
            "while(true) {",
            "  const currentTask = life[Math.floor(Math.random() * life.length)];",
            "  console.log(`Currently: ${currentTask} 🚀`);",
            "  if(currentTask === 'Code') {",
            "    buildAwesomeStuff();",
            "  }",
            "}"
        ];

        function animateCode() {
            const codeElement = document.getElementById('code-animation');
            let lineIndex = 0;
            let charIndex = 0;
            let currentCode = '';

            function typeLine() {
                if (lineIndex < codeLines.length) {
                    if (charIndex < codeLines[lineIndex].length) {
                        currentCode += codeLines[lineIndex][charIndex];
                        codeElement.textContent = currentCode;
                        charIndex++;
                        setTimeout(typeLine, 50);
                    } else {
                        currentCode += '\n';
                        codeElement.textContent = currentCode;
                        lineIndex++;
                        charIndex = 0;
                        setTimeout(typeLine, 200);
                    }
                }
            }

            typeLine();
        }

        // Interactive background
        document.addEventListener('mousemove', (e) => {
            const interactiveBg = document.querySelector('.interactive-bg');
            const x = (e.clientX / window.innerWidth) * 100;
            const y = (e.clientY / window.innerHeight) * 100;
            interactiveBg.style.setProperty('--x', x + '%');
            interactiveBg.style.setProperty('--y', y + '%');
        });

        // Tech tag click effects
        document.querySelectorAll('.tech-tag').forEach(tag => {
            tag.addEventListener('click', () => {
                tag.style.transform = 'scale(1.2)';
                setTimeout(() => {
                    tag.style.transform = 'scale(1)';
                }, 200);
            });
        });

        // Initialize everything
        createStars();
        createFloatingIcons();
        setTimeout(animateCode, 3000);

        // Scroll animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.animation = 'none';
                    entry.target.offsetHeight; // Trigger reflow
                    entry.target.style.animation = 'fadeInUp 0.8s ease forwards';
                }
            });
        }, observerOptions);

        document.querySelectorAll('.tech-category, .about-item, .social-link').forEach(el => {
            observer.observe(el);
        });

        // Add fadeInUp animation
        const style = document.createElement('style');
        style.textContent = `
            @keyframes fadeInUp {
                from {
                    opacity: 0;
                    transform: translateY(30px);
                }
                to {
                    opacity: 1;
                    transform: translateY(0);
                }
            }
        `;
        document.head.appendChild(style);

        // Easter egg - Konami code
        let konamiCode = [];
        const konamiSequence = [38, 38, 40, 40, 37, 39, 37, 39, 66, 65]; // Up Up Down Down Left Right Left Right B A

        document.addEventListener('keydown', (e) => {
            konamiCode.push(e.keyCode);
            if (konamiCode.length > konamiSequence.length) {
                konamiCode.shift();
            }
            
            if (konamiCode.length === konamiSequence.length && 
                konamiCode.every((code, index) => code === konamiSequence[index])) {
                // Easter egg activated!
                document.body.style.animation = 'rainbow 1s linear infinite';
                setTimeout(() => {
                    document.body.style.animation = '';
                }, 5000);
            }
        });

        // Add rainbow animation
        const rainbowStyle = document.createElement('style');
        rainbowStyle.textContent = `
            @keyframes rainbow {
                0% { filter: hue-rotate(0deg); }
                100% { filter: hue-rotate(360deg); }
            }
        `;
        document.head.appendChild(rainbowStyle);
    </script>
</body>
</html>
