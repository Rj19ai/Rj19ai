<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rahul Raj - Digital Product Designer</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #2D3047;
            --secondary: #419D78;
            --accent1: #E0A458;
            --accent2: #C04ABC;
            --accent3: #3066BE;
            --light: #FFFFFF;
            --gradient1: linear-gradient(135deg, #419D78, #3066BE);
            --gradient2: linear-gradient(135deg, #E0A458, #C04ABC);
            --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: var(--primary);
            color: var(--light);
            font-family: 'Poppins', sans-serif;
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Background Shapes */
        .background-shapes {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            overflow: hidden;
        }

        .shape {
            position: absolute;
            opacity: 0.1;
            animation: floatAnimation 20s infinite;
        }

        .shape1 {
            width: 200px;
            height: 200px;
            background: var(--accent1);
            clip-path: polygon(50% 0%, 100% 38%, 82% 100%, 18% 100%, 0% 38%);
            top: 10%;
            left: 10%;
        }

        .shape2 {
            width: 150px;
            height: 150px;
            background: var(--accent2);
            border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
            top: 60%;
            right: 15%;
            animation-delay: -5s;
        }

        .shape3 {
            width: 100px;
            height: 100px;
            background: var(--accent3);
            clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
            bottom: 20%;
            left: 20%;
            animation-delay: -10s;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            padding: 2rem;
            position: relative;
            background: radial-gradient(circle at center, rgba(45, 48, 71, 0.8) 0%, var(--primary) 70%);
        }

        .greeting {
            font-size: 1.5rem;
            opacity: 0;
            animation: slideUp 1s forwards;
            background: var(--gradient1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .name {
            font-size: 4.5rem;
            font-weight: 700;
            margin: 1rem 0;
            opacity: 0;
            animation: slideUp 1s 0.3s forwards;
            background: var(--gradient2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-align: center;
        }

        .title {
            font-size: 1.5rem;
            opacity: 0;
            animation: slideUp 1s 0.6s forwards;
            color: var(--accent1);
        }

        /* Main Content */
        .content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        section {
            margin-bottom: 6rem;
            opacity: 0;
            transform: translateY(50px);
            transition: var(--transition);
        }

        section.visible {
            opacity: 1;
            transform: translateY(0);
        }

        h2 {
            font-size: 2.5rem;
            margin-bottom: 2rem;
            background: var(--gradient1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            display: inline-block;
        }

        /* Skills Section */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
        }

        .skill-card {
            padding: 2rem;
            border-radius: 20px;
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            transition: var(--transition);
            position: relative;
            overflow: hidden;
            animation: float 6s ease-in-out infinite;
        }

        .skill-card:nth-child(2) {
            animation-delay: -2s;
        }

        .skill-card:nth-child(3) {
            animation-delay: -4s;
        }

        .skill-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--gradient1);
            opacity: 0;
            transition: var(--transition);
            z-index: -1;
        }

        .skill-card:hover::before {
            opacity: 0.1;
        }

        /* Projects Section */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .project-card {
            position: relative;
            padding: 2rem;
            border-radius: 20px;
            overflow: hidden;
            transition: var(--transition);
            animation: floatReverse 8s ease-in-out infinite;
        }

        .project-card:nth-child(1) {
            background: var(--gradient1);
            clip-path: polygon(0 0, 100% 0, 100% 85%, 85% 100%, 0 100%);
            animation-delay: -4s;
        }

        .project-card:nth-child(2) {
            background: var(--gradient2);
            clip-path: polygon(15% 0, 100% 0, 100% 100%, 0 100%, 0 15%);
        }

        .project-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        /* Contact Section */
        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
        }

        .contact-item {
            padding: 1.5rem;
            text-align: center;
            border-radius: 15px;
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            transition: var(--transition);
            animation: float 7s ease-in-out infinite;
        }

        .contact-item:nth-child(2) {
            animation-delay: -2.3s;
        }

        .contact-item:nth-child(3) {
            animation-delay: -4.6s;
        }

        .contact-item a {
            color: var(--light);
            text-decoration: none;
            font-size: 1.2rem;
            display: block;
        }

        /* Animations */
        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes float {
            0%, 100% {
                transform: translateY(0) rotate(0deg);
            }
            50% {
                transform: translateY(-20px) rotate(2deg);
            }
        }

        @keyframes floatReverse {
            0%, 100% {
                transform: translateY(0) rotate(0deg);
            }
            50% {
                transform: translateY(-15px) rotate(-2deg);
            }
        }

        @keyframes floatAnimation {
            0%, 100% {
                transform: translate(0, 0) rotate(0deg);
            }
            25% {
                transform: translate(20px, -20px) rotate(90deg);
            }
            50% {
                transform: translate(-20px, 20px) rotate(180deg);
            }
            75% {
                transform: translate(-20px, -20px) rotate(270deg);
            }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .name {
                font-size: 3rem;
            }
            
            .content {
                padding: 1rem;
            }
            
            .shape {
                opacity: 0.05;
            }
        }
    </style>
</head>
<body>
    <!-- Background Shapes -->
    <div class="background-shapes">
        <div class="shape shape1"></div>
        <div class="shape shape2"></div>
        <div class="shape shape3"></div>
    </div>

    <div class="hero">
        <div class="greeting">Hello, I'm</div>
        <h1 class="name">Rahul Raj</h1>
        <div class="title">Digital Product Designer & Manager</div>
    </div>

    <main class="content">
        <section id="about">
            <h2>About Me</h2>
            <p>A passionate Digital Product Designer and Manager with a unique blend of creativity and analytical thinking. I transform complex challenges into elegant, user-centric solutions that drive business growth and user satisfaction.</p>
        </section>

        <section id="skills">
            <h2>Skills & Expertise</h2>
            <div class="skills-grid">
                <div class="skill-card">
                    <h3>Development</h3>
                    <p>Proficient in Python, JavaScript, and MySQL, creating robust and scalable solutions.</p>
                </div>
                <div class="skill-card">
                    <h3>Analytics</h3>
                    <p>Expert in Tableau, Power BI, and data analysis, driving data-informed decisions.</p>
                </div>
                <div class="skill-card">
                    <h3>Design</h3>
                    <p>Specialized in UI/UX, product design, and user research methodologies.</p>
                </div>
            </div>
        </section>

        <section id="projects">
            <h2>Featured Projects</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <h3>UniPrice</h3>
                    <p>A revolutionary price comparison platform that increased user engagement by 25% through innovative design and seamless user experience.</p>
                </div>
                <div class="project-card">
                    <h3>Swiggy Instamart Analysis</h3>
                    <p>Comprehensive market analysis that led to a 20% improvement in delivery efficiency and enhanced customer satisfaction.</p>
                </div>
            </div>
        </section>

        <section id="contact">
            <h2>Let's Connect</h2>
            <div class="contact-grid">
                <div class="contact-item">
                    <a href="mailto:sam9798set@gmail.com">Email</a>
                </div>
                <div class="contact-item">
                    <a href="https://linkedin.com/in/Rahul2001raj" target="_blank">LinkedIn</a>
                </div>
                <div class="contact-item">
                    <a href="tel:+918789730716">Phone</a>
                </div>
            </div>
        </section>
    </main>

    <script>
        // Intersection Observer for scroll animations
        const sections = document.querySelectorAll('section');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, { threshold: 0.1 });

        sections.forEach(section => observer.observe(section));
    </script>
</body>
</html>
