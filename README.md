<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CopySimplify - Your Message. Simplified.</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            line-height: 1.6;
            color: #1a1a2e;
            background: #fafafa;
        }

        /* Navigation */
        .nav {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(0, 0, 0, 0.1);
            z-index: 1000;
            transition: all 0.3s ease;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 2rem;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            align-items: center;
        }

        .nav-links a {
            text-decoration: none;
            color: #4a5568;
            font-weight: 500;
            transition: color 0.3s ease;
        }

        .nav-links a:hover {
            color: #667eea;
        }

        .nav-cta {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 0.75rem 1.5rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);
        }

        .nav-cta:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.4);
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.05'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E") repeat;
            opacity: 0.1;
        }

        .hero-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
            text-align: center;
            position: relative;
            z-index: 2;
        }

        .hero h1 {
            font-size: 4rem;
            font-weight: 800;
            margin-bottom: 1rem;
            opacity: 0;
            animation: fadeInUp 1s ease forwards;
        }

        .hero p {
            font-size: 1.25rem;
            margin-bottom: 2.5rem;
            opacity: 0.9;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            opacity: 0;
            animation: fadeInUp 1s ease 0.2s forwards;
        }

        .hero-cta {
            background: white;
            color: #667eea;
            padding: 1rem 2.5rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 700;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            display: inline-block;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            opacity: 0;
            animation: fadeInUp 1s ease 0.4s forwards;
        }

        .hero-cta:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.3);
        }

        /* Floating elements */
        .floating-elements {
            position: absolute;
            width: 100%;
            height: 100%;
            overflow: hidden;
            pointer-events: none;
        }

        .floating-element {
            position: absolute;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            animation: float 6s ease-in-out infinite;
        }

        .floating-element:nth-child(1) { width: 80px; height: 80px; top: 20%; left: 10%; animation-delay: 0s; }
        .floating-element:nth-child(2) { width: 120px; height: 120px; top: 60%; right: 10%; animation-delay: 2s; }
        .floating-element:nth-child(3) { width: 60px; height: 60px; bottom: 20%; left: 20%; animation-delay: 4s; }

        /* Value Proposition */
        .value-prop {
            padding: 6rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .value-prop h2 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 1.5rem;
            color: #2d3748;
            text-align: center;
        }

        .value-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
            margin-top: 3rem;
        }

        .value-text p {
            font-size: 1.1rem;
            color: #4a5568;
            margin-bottom: 2rem;
            line-height: 1.7;
        }

        .benefits {
            list-style: none;
            margin-bottom: 2rem;
        }

        .benefits li {
            display: flex;
            align-items: center;
            margin-bottom: 1rem;
            font-weight: 600;
            color: #2d3748;
        }

        .benefits li::before {
            content: '✨';
            margin-right: 1rem;
            font-size: 1.2rem;
        }

        .benefit-label {
            color: #667eea;
            margin-right: 0.5rem;
        }

        .secondary-cta {
            background: transparent;
            color: #667eea;
            border: 2px solid #667eea;
            padding: 0.75rem 1.5rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
            display: inline-block;
        }

        .secondary-cta:hover {
            background: #667eea;
            color: white;
            transform: translateY(-2px);
        }

        .value-visual {
            position: relative;
            height: 400px;
            background: linear-gradient(135deg, #f7fafc 0%, #edf2f7 100%);
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .visual-icon {
            font-size: 8rem;
            color: #667eea;
            opacity: 0.3;
        }

        /* How It Works */
        .how-it-works {
            background: linear-gradient(135deg, #f7fafc 0%, #edf2f7 100%);
            padding: 6rem 2rem;
        }

        .how-container {
            max-width: 1200px;
            margin: 0 auto;
            text-align: center;
        }

        .how-it-works h2 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 3rem;
            color: #2d3748;
        }

        .steps {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 3rem;
            margin-bottom: 3rem;
        }

        .step {
            background: white;
            padding: 2.5rem 1.5rem;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            position: relative;
        }

        .step:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
        }

        .step-number {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 1.5rem;
            margin: 0 auto 1.5rem;
        }

        .step h3 {
            font-size: 1.3rem;
            font-weight: 700;
            margin-bottom: 1rem;
            color: #2d3748;
        }

        .step p {
            color: #4a5568;
            line-height: 1.6;
        }

        .big-cta {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 1rem 2.5rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 700;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            display: inline-block;
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
        }

        .big-cta:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(102, 126, 234, 0.4);
        }

        /* Social Proof */
        .social-proof {
            padding: 6rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
            text-align: center;
        }

        .social-proof h2 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 3rem;
            color: #2d3748;
        }

        .testimonials {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 2rem;
            margin-bottom: 3rem;
        }

        .testimonial {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            text-align: left;
        }

        .testimonial-text {
            font-style: italic;
            margin-bottom: 1rem;
            color: #4a5568;
            line-height: 1.6;
        }

        .testimonial-author {
            font-weight: 600;
            color: #667eea;
        }

        .trust-badge {
            background: linear-gradient(135deg, #f7fafc 0%, #edf2f7 100%);
            padding: 1rem 2rem;
            border-radius: 50px;
            display: inline-block;
            color: #4a5568;
            font-weight: 600;
            margin-top: 2rem;
        }

        /* Pricing */
        .pricing {
            background: linear-gradient(135deg, #f7fafc 0%, #edf2f7 100%);
            padding: 6rem 2rem;
        }

        .pricing-container {
            max-width: 800px;
            margin: 0 auto;
            text-align: center;
        }

        .pricing h2 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 3rem;
            color: #2d3748;
        }

        .pricing-cards {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 2rem;
        }

        .pricing-card {
            background: white;
            padding: 2.5rem;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            position: relative;
        }

        .pricing-card.featured {
            transform: scale(1.05);
            border: 3px solid #667eea;
            box-shadow: 0 15px 40px rgba(102, 126, 234, 0.2);
        }

        .plan-name {
            font-size: 1.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
            color: #2d3748;
        }

        .plan-price {
            font-size: 2.5rem;
            font-weight: 800;
            color: #667eea;
            margin-bottom: 1.5rem;
        }

        .plan-features {
            list-style: none;
            margin-bottom: 2rem;
            text-align: left;
        }

        .plan-features li {
            margin-bottom: 0.5rem;
            color: #4a5568;
            display: flex;
            align-items: center;
        }

        .plan-features li::before {
            content: '✓';
            color: #48bb78;
            font-weight: bold;
            margin-right: 0.5rem;
        }

        .plan-cta {
            width: 100%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 10px;
            font-weight: 700;
            font-size: 1rem;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .plan-cta:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.3);
        }

        /* Final CTA */
        .final-cta {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 2rem;
            text-align: center;
            position: sticky;
            bottom: 0;
            z-index: 999;
        }

        .final-cta-content {
            max-width: 1000px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .final-cta-text {
            font-size: 1.1rem;
            font-weight: 600;
        }

        .final-cta-button {
            background: white;
            color: #667eea;
            padding: 0.75rem 1.5rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 700;
            transition: all 0.3s ease;
        }

        .final-cta-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(255, 255, 255, 0.3);
        }

        /* Animations */
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

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-container {
                padding: 1rem;
            }

            .nav-links {
                display: none;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .value-content {
                grid-template-columns: 1fr;
                gap: 2rem;
            }

            .steps {
                grid-template-columns: 1fr;
            }

            .testimonials {
                grid-template-columns: 1fr;
            }

            .pricing-cards {
                grid-template-columns: 1fr;
            }

            .pricing-card.featured {
                transform: none;
            }

            .final-cta-content {
                flex-direction: column;
                text-align: center;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="nav">
        <div class="nav-container">
            <div class="logo">CopySimplify</div>
            <div class="nav-links">
                <a href="#how-it-works">How It Works</a>
                <a href="#pricing">Pricing</a>
                <a href="#login">Login</a>
                <a href="#cta" class="nav-cta">Simplify My Copy</a>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero">
        <div class="floating-elements">
            <div class="floating-element"></div>
            <div class="floating-element"></div>
            <div class="floating-element"></div>
        </div>
        <div class="hero-container">
            <h1>Your Message. Simplified.</h1>
            <p>Get clear, high‑impact marketing copy in minutes—not hours.</p>
            <a href="#cta" class="hero-cta">Simplify My Copy</a>
        </div>
    </section>

    <!-- Value Proposition -->
    <section class="value-prop">
        <h2>Stop Wasting Time Wrestling with Words.</h2>
        <div class="value-content">
            <div class="value-text">
                <p>Small businesses and creators spend hours trying to make their message clear. We make it effortless. Copysimplify turns messy, unclear copy into concise, high‑performing messaging—instantly.</p>
                <ul class="benefits">
                    <li><span class="benefit-label">Fast:</span> Get optimized copy in seconds.</li>
                    <li><span class="benefit-label">Clear:</span> Eliminate confusing, wordy messaging.</li>
                    <li><span class="benefit-label">Effective:</span> Copy designed to convert.</li>
                </ul>
                <a href="#how-it-works" class="secondary-cta">See How It Works</a>
            </div>
            <div class="value-visual">
                <div class="visual-icon">📝</div>
            </div>
        </div>
    </section>

    <!-- How It Works -->
    <section class="how-it-works" id="how-it-works">
        <div class="how-container">
            <h2>How It Works</h2>
            <div class="steps">
                <div class="step">
                    <div class="step-number">1</div>
                    <h3>Paste Your Copy</h3>
                    <p>Drop in your draft or upload content.</p>
                </div>
                <div class="step">
                    <div class="step-number">2</div>
                    <h3>Pick Your Goal</h3>
                    <p>Sell, engage, or explain.</p>
                </div>
                <div class="step">
                    <div class="step-number">3</div>
                    <h3>Get Instant Results</h3>
                    <p>Clear, polished copy in one click.</p>
                </div>
            </div>
            <a href="#cta" class="big-cta">Try It Free</a>
        </div>
    </section>

    <!-- Social Proof -->
    <section class="social-proof">
        <h2>Creators & Businesses Already Love It</h2>
        <div class="testimonials">
            <div class="testimonial">
                <div class="testimonial-text">"Rewrote my product page in 30 seconds. Conversions went up 18%."</div>
                <div class="testimonial-author">– Alex, eCommerce Owner</div>
            </div>
            <div class="testimonial">
                <div class="testimonial-text">"Cut my website rewrite time from 3 days to 30 minutes."</div>
                <div class="testimonial-author">– Sarah, Freelancer</div>
            </div>
        </div>
        <div class="trust-badge">Trusted by 500+ small businesses</div>
    </section>

    <!-- Pricing -->
    <section class="pricing" id="pricing">
        <div class="pricing-container">
            <h2>Start Free. Upgrade When You're Ready.</h2>
            <div class="pricing-cards">
                <div class="pricing-card">
                    <div class="plan-name">Free Plan</div>
                    <div class="plan-price">$0</div>
                    <ul class="plan-features">
                        <li>3 free copy rewrites</li>
                        <li>Basic tone options</li>
                    </ul>
                    <button class="plan-cta">Get Started Free</button>
                </div>
                <div class="pricing-card featured">
                    <div class="plan-name">Pro Plan</div>
                    <div class="plan-price">$29<span style="font-size: 1rem; font-weight: normal;">/month</span></div>
                    <ul class="plan-features">
                        <li>Unlimited edits</li>
                        <li>Tone & goal presets</li>
                        <li>Priority support</li>
                    </ul>
                    <button class="plan-cta">Get Started Free</button>
                </div>
            </div>
        </div>
    </section>

    <!-- Final CTA -->
    <section class="final-cta" id="cta">
        <div class="final-cta-content">
            <div class="final-cta-text">Your customers won't wait. Why should your copy?</div>
            <a href="#signup" class="final-cta-button">Simplify My Copy</a>
        </div>
    </section>

    <script>
        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Add scroll effect to navigation
        window.addEventListener('scroll', () => {
            const nav = document.querySelector('.nav');
            if (window.scrollY > 50) {
                nav.style.background = 'rgba(255, 255, 255, 0.98)';
                nav.style.boxShadow = '0 2px 20px rgba(0, 0, 0, 0.1)';
            } else {
                nav.style.background = 'rgba(255, 255, 255, 0.95)';
                nav.style.boxShadow = 'none';
            }
        });

        // Add hover effects to cards
        document.querySelectorAll('.step, .pricing-card, .testimonial').forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-5px)';
            });
            
            card.addEventListener('mouseleave', function() {
                if (!this.classList.contains('featured')) {
                    this.style.transform = 'translateY(0)';
                }
            });
        });

        // CTA button interactions
        document.querySelectorAll('.plan-cta, .hero-cta, .big-cta, .final-cta-button').forEach(button => {
            button.addEventListener('click', function(e) {
                e.preventDefault();
                
                // Create ripple effect
                const ripple = document.createElement('span');
                const rect = this.getBoundingClientRect();
                const size = Math.max(rect.height, rect.width);
                const x = e.clientX - rect.left - size / 2;
                const y = e.clientY - rect.top - size / 2;
                
                ripple.style.width = ripple.style.height = size + 'px';
                ripple.style.left = x + 'px';
                ripple.style.top = y + 'px';
                ripple.style.position = 'absolute';
                ripple.style.borderRadius = '50%';
                ripple.style.background = 'rgba(255, 255, 255, 0.6)';
                ripple.style.transform = 'scale(0)';
                ripple.style.animation = 'ripple 0.6s linear';
                ripple.style.pointerEvents = 'none';
                
                this.style.position = 'relative';
                this.style.overflow = 'hidden';
                this.appendChild(ripple);
                
                setTimeout(() => {
                    ripple.remove();
                }, 600);
            });
        });

        // Add CSS for ripple animation
        const style = document.createElement('style');
        style.textContent = `
            @keyframes ripple {
                to {
                    transform: scale(4);
                    opacity: 0;
                }
            }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html># CopySimplify.com
A service focused on simplifying copywriting— offering services or tools for writing, editing, or improving marketing copy, content creation, or messaging clarity.
