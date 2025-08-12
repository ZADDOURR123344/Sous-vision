<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sous Vision - Personal Vision Website</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Poppins:wght@300;400;500;600&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #1a2a4a;
            --secondary: #3a506b;
            --accent: #5bc0be;
            --light: #f8f9fa;
            --dark: #121212;
            --gray: #6c757d;
            --transition: all 0.3s ease;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background-color: #fafafa;
            color: var(--dark);
            line-height: 1.6;
            overflow-x: hidden;
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        /* Header Styles */
        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            position: relative;
            overflow: hidden;
        }

        .header-content {
            flex: 1;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 2rem;
            z-index: 2;
        }

        .logo {
            font-family: 'Playfair Display', serif;
            font-size: 4.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
            letter-spacing: 3px;
        }

        .tagline {
            font-size: 1.5rem;
            max-width: 700px;
            margin-bottom: 2rem;
            opacity: 0.9;
        }

        .nav-container {
            width: 100%;
            padding: 1.5rem 0;
            position: absolute;
            top: 0;
            left: 0;
            z-index: 10;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            font-size: 1.1rem;
            transition: var(--transition);
            position: relative;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent);
            transition: var(--transition);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .scroll-down {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            color: white;
            font-size: 2rem;
            animation: bounce 2s infinite;
            z-index: 2;
        }

        /* Section Styles */
        section {
            padding: 6rem 0;
        }

        .section-header {
            text-align: center;
            margin-bottom: 4rem;
        }

        .section-title {
            font-family: 'Playfair Display', serif;
            font-size: 2.5rem;
            color: var(--primary);
            margin-bottom: 1rem;
            position: relative;
            display: inline-block;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 70px;
            height: 3px;
            background: var(--accent);
        }

        .section-subtitle {
            color: var(--gray);
            max-width: 700px;
            margin: 0 auto;
            font-size: 1.1rem;
        }

        .card-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: var(--transition);
        }

        .card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
        }

        .card-img {
            height: 200px;
            overflow: hidden;
        }

        .card-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }

        .card:hover .card-img img {
            transform: scale(1.05);
        }

        .card-content {
            padding: 1.5rem;
        }

        .card-title {
            font-size: 1.3rem;
            margin-bottom: 0.75rem;
            color: var(--primary);
        }

        .card-date {
            color: var(--accent);
            font-size: 0.9rem;
            margin-bottom: 1rem;
            display: block;
        }

        .card-text {
            color: var(--gray);
            margin-bottom: 1.5rem;
        }

        .btn {
            display: inline-block;
            padding: 0.8rem 1.8rem;
            background: var(--accent);
            color: white;
            text-decoration: none;
            border-radius: 30px;
            font-weight: 500;
            transition: var(--transition);
            border: none;
            cursor: pointer;
            font-size: 1rem;
        }

        .btn:hover {
            background: #4aa9a7;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(91, 192, 190, 0.3);
        }

        /* Projects Section */
        .projects-section {
            background: linear-gradient(to bottom, #f8f9fa, #e9ecef);
        }

        .project-card {
            display: flex;
            flex-direction: column;
            height: 100%;
        }

        .project-tags {
            display: flex;
            gap: 0.5rem;
            margin-bottom: 1rem;
            flex-wrap: wrap;
        }

        .project-tag {
            background: rgba(91, 192, 190, 0.15);
            color: var(--accent);
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.85rem;
        }

        /* Connect Section */
        .connect-section {
            background: white;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin-top: 2rem;
        }

        .social-link {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 50px;
            height: 50px;
            background: var(--primary);
            color: white;
            border-radius: 50%;
            font-size: 1.3rem;
            transition: var(--transition);
        }

        .social-link:hover {
            background: var(--accent);
            transform: translateY(-5px);
        }

        .contact-form {
            max-width: 600px;
            margin: 3rem auto 0;
            background: white;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-control {
            width: 100%;
            padding: 0.8rem 1rem;
            border: 1px solid #e0e0e0;
            border-radius: 5px;
            font-family: inherit;
            font-size: 1rem;
            transition: var(--transition);
        }

        .form-control:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 3px rgba(91, 192, 190, 0.2);
        }

        textarea.form-control {
            min-height: 150px;
            resize: vertical;
        }

        /* Footer */
        footer {
            background: var(--primary);
            color: white;
            padding: 4rem 0 2rem;
            text-align: center;
        }

        .footer-logo {
            font-family: 'Playfair Display', serif;
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        .footer-text {
            max-width: 600px;
            margin: 0 auto 2rem;
            opacity: 0.8;
            line-height: 1.8;
        }

        .copyright {
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            font-size: 0.9rem;
            opacity: 0.7;
        }

        /* Animations */
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateY(0) translateX(-50%);
            }
            40% {
                transform: translateY(-20px) translateX(-50%);
            }
            60% {
                transform: translateY(-10px) translateX(-50%);
            }
        }

        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 0.6s ease, transform 0.6s ease;
        }

        .fade-in.appear {
            opacity: 1;
            transform: translateY(0);
        }

        /* Decorative Elements */
        .circle {
            position: absolute;
            border-radius: 50%;
            z-index: 1;
        }

        .circle-1 {
            width: 300px;
            height: 300px;
            background: rgba(91, 192, 190, 0.1);
            top: -150px;
            right: -150px;
        }

        .circle-2 {
            width: 200px;
            height: 200px;
            background: rgba(26, 42, 74, 0.1);
            bottom: -100px;
            left: -100px;
        }

        .circle-3 {
            width: 150px;
            height: 150px;
            background: rgba(91, 192, 190, 0.1);
            bottom: 20%;
            right: 10%;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .logo {
                font-size: 3rem;
            }
            
            .tagline {
                font-size: 1.2rem;
            }
            
            .nav-links {
                display: none;
            }
            
            .section-title {
                font-size: 2rem;
            }
            
            .mobile-menu-btn {
                display: block;
                color: white;
                font-size: 1.5rem;
                background: none;
                border: none;
                cursor: pointer;
            }
        }

        @media (min-width: 769px) {
            .mobile-menu-btn {
                display: none;
            }
        }
    </style>
</head>
<body>
    <!-- Header Section -->
    <header>
        <div class="circle circle-1"></div>
        <div class="circle circle-2"></div>
        <div class="circle circle-3"></div>
        
        <div class="nav-container container">
            <nav>
                <div class="logo">Sous Vision</div>
                <div class="nav-links">
                    <a href="#news">Latest News</a>
                    <a href="#reflections">Reflections</a>
                    <a href="#projects">Projects</a>
                    <a href="#connect">Connect</a>
                </div>
                <button class="mobile-menu-btn">
                    <i class="fas fa-bars"></i>
                </button>
            </nav>
        </div>
        
        <div class="header-content">
            <h1 class="logo">Sous Vision</h1>
            <p class="tagline">Your personal gateway to stories, reflections, and everything that matters to me.</p>
            <a href="#news" class="btn">Explore My Vision</a>
        </div>
        
        <div class="scroll-down">
            <i class="fas fa-chevron-down"></i>
        </div>
    </header>

    <!-- Latest News Section -->
    <section id="news" class="news-section">
        <div class="container">
            <div class="section-header fade-in">
                <h2 class="section-title">Latest News</h2>
                <p class="section-subtitle">Stay informed with the latest developments, announcements, and events that shape my journey. I bring you stories that matter, told from my perspective.</p>
            </div>
            
            <div class="card-grid">
                <div class="card fade-in">
                    <div class="card-img">
                        <img src="https://images.unsplash.com/photo-1499750310107-5fef28a66643?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&h=400&q=80" alt="New Journey">
                    </div>
                    <div class="card-content">
                        <span class="card-date">June 15, 2023</span>
                        <h3 class="card-title">Embarking on a New Creative Journey</h3>
                        <p class="card-text">Exciting news! I'm starting a new chapter in my creative journey that will bring fresh perspectives and innovative projects to Sous Vision.</p>
                        <a href="#" class="btn">Read More</a>
                    </div>
                </div>
                
                <div class="card fade-in">
                    <div class="card-img">
                        <img src="https://images.unsplash.com/photo-1463171379579-3fdfb86d6285?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&h=400&q=80" alt="Collaboration">
                    </div>
                    <div class="card-content">
                        <span class="card-date">May 28, 2023</span>
                        <h3 class="card-title">New Collaboration Announcement</h3>
                        <p class="card-text">Thrilled to announce a collaboration with talented artists that will result in an exciting multimedia project launching this fall.</p>
                        <a href="#" class="btn">Read More</a>
                    </div>
                </div>
                
                <div class="card fade-in">
                    <div class="card-img">
                        <img src="https://images.unsplash.com/photo-1497366754035-f200968a6e72?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&h=400&q=80" alt="Workshop">
                    </div>
                    <div class="card-content">
                        <span class="card-date">April 10, 2023</span>
                        <h3 class="card-title">Upcoming Workshop Series</h3>
                        <p class="card-text">Join me for a series of workshops exploring the intersection of storytelling and visual expression. Registration now open!</p>
                        <a href="#" class="btn">Read More</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Reflections Section -->
    <section id="reflections" class="reflections-section" style="background-color: #f8f9fa;">
        <div class="container">
            <div class="section-header fade-in">
                <h2 class="section-title">My Reflections</h2>
                <p class="section-subtitle">This section is dedicated to my thoughts, ideas, and opinions. From deep reflections to spontaneous musings, I write what moves me.</p>
            </div>
            
            <div class="card-grid">
                <div class="card fade-in">
                    <div class="card-content">
                        <span class="card-date">July 3, 2023</span>
                        <h3 class="card-title">The Art of Seeing Differently</h3>
                        <p class="card-text">How shifting perspective can transform ordinary moments into extraordinary insights. A meditation on perception and creativity.</p>
                        <a href="#" class="btn">Read Reflection</a>
                    </div>
                </div>
                
                <div class="card fade-in">
                    <div class="card-content">
                        <span class="card-date">June 18, 2023</span>
                        <h3 class="card-title">Finding Meaning in the Mundane</h3>
                        <p class="card-text">Discovering beauty and significance in everyday routines. How paying attention to small details can enrich our lives.</p>
                        <a href="#" class="btn">Read Reflection</a>
                    </div>
                </div>
                
                <div class="card fade-in">
                    <div class="card-content">
                        <span class="card-date">May 5, 2023</span>
                        <h3 class="card-title">The Courage to Create</h3>
                        <p class="card-text">Exploring the vulnerability of creation and why putting our work into the world requires both courage and humility.</p>
                        <a href="#" class="btn">Read Reflection</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects & Media Section -->
    <section id="projects" class="projects-section">
        <div class="container">
            <div class="section-header fade-in">
                <h2 class="section-title">Projects & Media</h2>
                <p class="section-subtitle">Discover my creative side—photos, videos, designs, and everything I'm working on. Sous Vision is not just about words; it's about vision.</p>
            </div>
            
            <div class="card-grid">
                <div class="card fade-in">
                    <div class="card-img">
                        <img src="https://images.unsplash.com/photo-1503376780353-7e6692767b70?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&h=400&q=80" alt="Automotive Photography">
                    </div>
                    <div class="card-content">
                        <div class="project-tags">
                            <span class="project-tag">Photography</span>
                            <span class="project-tag">Automotive</span>
                        </div>
                        <h3 class="card-title">Automotive Elegance Series</h3>
                        <p class="card-text">A photographic exploration of classic automobiles, capturing their timeless beauty and engineering excellence.</p>
                        <a href="#" class="btn">View Project</a>
                    </div>
                </div>
                
                <div class="card fade-in">
                    <div class="card-img">
                        <img src="https://images.unsplash.com/photo-1516035069371-29a1b244cc32?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&h=400&q=80" alt="Documentary">
                    </div>
                    <div class="card-content">
                        <div class="project-tags">
                            <span class="project-tag">Film</span>
                            <span class="project-tag">Documentary</span>
                        </div>
                        <h3 class="card-title">Urban Rhythms Documentary</h3>
                        <p class="card-text">A short film capturing the heartbeat of the city through the stories of its diverse inhabitants and their daily lives.</p>
                        <a href="#" class="btn">View Project</a>
                    </div>
                </div>
                
                <div class="card fade-in">
                    <div class="card-img">
                        <img src="https://images.unsplash.com/photo-1522542550221-31fd19575a2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&h=400&q=80" alt="Design">
                    </div>
                    <div class="card-content">
                        <div class="project-tags">
                            <span class="project-tag">Design</span>
                            <span class="project-tag">Typography</span>
                        </div>
                        <h3 class="card-title">Typography in Motion</h3>
                        <p class="card-text">An experimental project exploring the relationship between typography, movement, and emotional expression.</p>
                        <a href="#" class="btn">View Project</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Connect Section -->
    <section id="connect" class="connect-section">
        <div class="container">
            <div class="section-header fade-in">
                <h2 class="section-title">Connect With Me</h2>
                <p class="section-subtitle">I believe in sharing and growing together. Feel free to reach out, comment, or follow me on social media. Let's build a community around ideas and inspiration.</p>
            </div>
            
            <div class="social-links fade-in">
                <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
                <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
                <a href="#" class="social-link"><i class="fab fa-linkedin-in"></i></a>
                <a href="#" class="social-link"><i class="fab fa-youtube"></i></a>
                <a href="#" class="social-link"><i class="fab fa-medium-m"></i></a>
            </div>
            
            <div class="contact-form fade-in">
                <div class="form-group">
                    <input type="text" class="form-control" placeholder="Your Name">
                </div>
                <div class="form-group">
                    <input type="email" class="form-control" placeholder="Your Email">
                </div>
                <div class="form-group">
                    <textarea class="form-control" placeholder="Your Message"></textarea>
                </div>
                <button type="submit" class="btn">Send Message</button>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-logo">Sous Vision</div>
            <p class="footer-text">Thank you for visiting Sous Vision. This is more than a website. It's a vision. My vision. And I'm glad you're part of it.</p>
            <div class="social-links">
                <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
                <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
                <a href="#" class="social-link"><i class="fab fa-linkedin-in"></i></a>
            </div>
            <div class="copyright">
                &copy; 2023 Sous Vision. All rights reserved.
            </div>
        </div>
    </footer>

    <script>
        // Simple scroll animation for sections
        document.addEventListener('DOMContentLoaded', function() {
            // Scroll to sections
            document.querySelector('.scroll-down').addEventListener('click', function() {
                document.querySelector('#news').scrollIntoView({ behavior: 'smooth' });
            });
            
            // Fade-in animation for sections
            const fadeElements = document.querySelectorAll('.fade-in');
            
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('appear');
                    }
                });
            }, {
                threshold: 0.1,
                rootMargin: '0px 0px -50px 0px'
            });
            
            fadeElements.forEach(element => {
                observer.observe(element);
            });
            
            // Smooth scrolling for navigation links
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function(e) {
                    e.preventDefault();
                    
                    const target = document.querySelector(this.getAttribute('href'));
                    if (target) {
                        target.scrollIntoView({
                            behavior: 'smooth'
                        });
                    }
                });
            });
        });
    </script>
</body>
</html>
