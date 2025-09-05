<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FocusFuel - Apna Dhyan Badhayein</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #2563eb;
            --primary-dark: #1d4ed8;
            --secondary: #f97316;
            --light: #f3f4f6;
            --dark: #1f2937;
            --success: #10b981;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f8fafc;
            color: #334155;
            line-height: 1.6;
        }
        
        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header */
        header {
            background: linear-gradient(to right, var(--primary), var(--primary-dark));
            color: white;
            padding: 15px 0;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 24px;
            font-weight: 700;
            display: flex;
            align-items: center;
        }
        
        .logo i {
            margin-right: 10px;
        }
        
        /* Sections */
        section {
            padding: 60px 0;
            display: none;
        }
        
        section.active {
            display: block;
        }
        
        /* Landing Page */
        .hero {
            text-align: center;
            padding: 40px 0;
        }
        
        .hero h1 {
            font-size: 2.5rem;
            color: var(--dark);
            margin-bottom: 20px;
            line-height: 1.3;
        }
        
        .hero p {
            font-size: 1.2rem;
            margin-bottom: 30px;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .hero-image {
            max-width: 100%;
            border-radius: 10px;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
            margin: 30px 0;
        }
        
        /* CTA Button */
        .cta-button {
            display: inline-block;
            background: linear-gradient(to right, var(--secondary), #ea580c);
            color: white;
            padding: 15px 40px;
            font-size: 1.2rem;
            font-weight: 600;
            border-radius: 50px;
            text-decoration: none;
            margin: 20px 0;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
        }
        
        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 10px rgba(0, 0, 0, 0.2);
        }
        
        /* Features */
        .features {
            background-color: white;
            border-radius: 10px;
            padding: 30px;
            margin: 40px 0;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
        }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }
        
        .feature-card {
            text-align: center;
            padding: 20px;
            border-radius: 10px;
            background-color: var(--light);
            transition: transform 0.3s ease;
        }
        
        .feature-card:hover {
            transform: translateY(-5px);
        }
        
        .feature-icon {
            font-size: 2.5rem;
            color: var(--primary);
            margin-bottom: 15px;
        }
        
        /* Testimonials */
        .testimonials {
            background-color: #eff6ff;
            padding: 50px 0;
        }
        
        .testimonial-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }
        
        .testimonial-card {
            background-color: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
        }
        
        .testimonial-text {
            font-style: italic;
            margin-bottom: 15px;
        }
        
        .testimonial-author {
            font-weight: 600;
            color: var(--primary);
        }
        
        /* Pricing */
        .pricing {
            text-align: center;
            background-color: white;
            padding: 50px 20px;
            border-radius: 10px;
            margin: 40px 0;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
        }
        
        .pricing-badge {
            position: absolute;
            top: 20px;
            right: -35px;
            background-color: var(--secondary);
            color: white;
            padding: 5px 40px;
            transform: rotate(45deg);
            font-weight: 600;
            font-size: 0.9rem;
        }
        
        .price-old {
            text-decoration: line-through;
            color: #94a3b8;
            font-size: 1.5rem;
        }
        
        .price-new {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--dark);
            margin: 10px 0;
        }
        
        .bonus-section {
            background-color: #fffbeb;
            border-left: 4px solid var(--secondary);
            padding: 20px;
            margin: 30px 0;
            text-align: left;
            border-radius: 0 8px 8px 0;
        }
        
        /* Forms */
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
        }
        
        .form-control {
            width: 100%;
            padding: 15px;
            border: 1px solid #cbd5e1;
            border-radius: 8px;
            font-size: 1rem;
        }
        
        .form-section {
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
            margin: 30px 0;
        }
        
        /* Payment Options */
        .payment-options {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin: 20px 0;
        }
        
        .payment-option {
            flex: 1;
            min-width: 120px;
            border: 1px solid #cbd5e1;
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .payment-option:hover {
            border-color: var(--primary);
            box-shadow: 0 0 0 2px #bfdbfe;
        }
        
        .payment-option i {
            font-size: 2rem;
            margin-bottom: 10px;
            color: var(--primary);
        }
        
        /* Footer */
        footer {
            background-color: var(--dark);
            color: white;
            padding: 40px 0;
            text-align: center;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2rem;
            }
            
            .features-grid, .testimonial-grid {
                grid-template-columns: 1fr;
            }
            
            .header-content {
                flex-direction: column;
                text-align: center;
            }
            
            .logo {
                margin-bottom: 15px;
            }
        }
        
        /* Animation */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .fade-in {
            animation: fadeIn 0.8s ease forwards;
        }
        
        /* Progress Bar */
        .progress-container {
            width: 100%;
            height: 8px;
            background-color: #e2e8f0;
            position: fixed;
            top: 0;
            left: 0;
            z-index: 1000;
        }
        
        .progress-bar {
            height: 100%;
            background: linear-gradient(to right, var(--primary), var(--secondary));
            width: 0%;
            transition: width 0.3s ease;
        }
        
        /* Countdown Timer */
        .countdown {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 20px 0;
        }
        
        .countdown-unit {
            background-color: var(--dark);
            color: white;
            padding: 10px;
            border-radius: 8px;
            min-width: 70px;
            text-align: center;
        }
        
        .countdown-value {
            font-size: 1.8rem;
            font-weight: 700;
        }
        
        .countdown-label {
            font-size: 0.8rem;
            text-transform: uppercase;
        }
    </style>
</head>
<body>
    <!-- Progress Bar -->
    <div class="progress-container">
        <div class="progress-bar" id="progressBar"></div>
    </div>

    <!-- Header -->
    <header>
        <div class="container header-content">
            <div class="logo">
                <i class="fas fa-bullseye"></i> FocusFuel
            </div>
            <div class="tagline">
                Apna Dhyan Badhayein, Distractions Kam Karein
            </div>
        </div>
    </header>

    <!-- Landing Page -->
    <section id="landing" class="active">
        <div class="container">
            <div class="hero">
                <h1>Dhyan ki kami se pareshan? Ab paaye turant sukoon</h1>
                <p>FocusFuel aapko dega sab kuch jo aapko apne goals par focus karne ke liye chahiye - digital tools se lekar physical products tak!</p>
                <img src="https://images.unsplash.com/photo-1593640495253-23196b27a87f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1200&q=80" alt="FocusFuel Hero Image" class="hero-image">
                <br>
                <button class="cta-button" onclick="showSection('story')">Free Focus Tips Paayein</button>
            </div>

            <div class="features">
                <h2 style="text-align: center; margin-bottom: 30px;">FocusFuel Kya Hai?</h2>
                <div class="features-grid">
                    <div class="feature-card fade-in">
                        <div class="feature-icon">
                            <i class="fas fa-book"></i>
                        </div>
                        <h3>Distraction-blocking eBook</h3>
                        <p>90 pages ki comprehensive guide distractions ko conquer karne ke liye</p>
                    </div>
                    <div class="feature-card fade-in">
                        <div class="feature-icon">
                            <i class="fas fa-headphones"></i>
                        </div>
                        <h3>Guided Audio Sessions</h3>
                        <p>5 professional audio sessions focus badhane ke liye</p>
                    </div>
                    <div class="feature-card fade-in">
                        <div class="feature-icon">
                            <i class="fas fa-mobile-alt"></i>
                        </div>
                        <h3>Phone Wallpapers</h3>
                        <p>12 specially designed wallpapers jo aapko focus karne mein help karenge</p>
                    </div>
                    <div class="feature-card fade-in">
                        <div class="feature-icon">
                            <i class="fas fa-gift"></i>
                        </div>
                        <h3>Physical Focus Kit</h3>
                        <p>Habit cards, timer, aur premium pen - aapke desk ke liye</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Story/Bridge Page -->
    <section id="story">
        <div class="container">
            <h2 style="text-align: center; margin-bottom: 30px;">Kaam Kaise Karta Hai FocusFuel?</h2>
            
            <div style="text-align: center; margin: 40px 0;">
                <div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 10px; box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1);">
                    <img src="https://images.unsplash.com/photo-1593642632823-8f785ba67e45?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1200&q=80" alt="FocusFuel Transformation" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; object-fit: cover;">
                </div>
                <p style="margin-top: 20px; font-style: italic;">FocusFuel ka istemal karte hue ek user ka transformation</p>
            </div>
            
            <div class="features-grid">
                <div class="form-section">
                    <h3>Digital Product Ke Fayde</h3>
                    <ul style="list-style-type: none; margin: 20px 0;">
                        <li style="padding: 10px 0; border-bottom: 1px solid #e2e8f0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Instant access - abhi download karein</li>
                        <li style="padding: 10px 0; border-bottom: 1px solid #e2e8f0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Kahi bhi, kabhi bhi use kar sakte hain</li>
                        <li style="padding: 10px 0; border-bottom: 1px solid #e2e8f0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Phone, tablet, computer par available</li>
                        <li style="padding: 10px 0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Regularly updated content</li>
                    </ul>
                </div>
                
                <div class="form-section">
                    <h3>Physical Product Ke Fayde</h3>
                    <ul style="list-style-type: none; margin: 20px 0;">
                        <li style="padding: 10px 0; border-bottom: 1px solid #e2e8f0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Tangible product jo aap feel kar sakte hain</li>
                        <li style="padding: 10px 0; border-bottom: 1px solid #e2e8f0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Desk par rakhein, daily reminder ke taur par</li>
                        <li style="padding: 10px 0; border-bottom: 1px solid #e2e8f0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> High-quality materials se bana hua</li>
                        <li style="padding: 10px 0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Free delivery all over India</li>
                    </ul>
                </div>
            </div>
            
            <div style="text-align: center; margin: 40px 0;">
                <button class="cta-button" onclick="showSection('offer')">Apna Focus Badhayein</button>
            </div>
            
            <div class="testimonial-grid">
                <div class="testimonial-card">
                    <p class="testimonial-text">"FocusFuel ne meri productivity double kar di! Pehle main 2-3 ghante mein jo kaam karta tha, ab wohi kaam 1 ghante mein ho jata hai."</p>
                    <p class="testimonial-author">- Rahul, IIT Student</p>
                </div>
                <div class="testimonial-card">
                    <p class="testimonial-text">"Is product ne meri life change kar di. Main apne business par focus kar pa raha hoon aur results aa rahe hain."</p>
                    <p class="testimonial-author">- Priya, Entrepreneur</p>
                </div>
                <div class="testimonial-card">
                    <p class="testimonial-text">"Audio sessions bahut effective hain. Subah 15 minute sunne se pure din focus maintain hota hai."</p>
                    <p class="testimonial-author">- Amit, Software Engineer</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Offer Page -->
    <section id="offer">
        <div class="container">
            <div class="pricing">
                <div class="pricing-badge">50% OFF</div>
                <h2>Special Introductory Offer</h2>
                <p>First-time buyers ke liye exclusive discount</p>
                
                <div class="countdown">
                    <div class="countdown-unit">
                        <div class="countdown-value" id="hours">06</div>
                        <div class="countdown-label">Hours</div>
                    </div>
                    <div class="countdown-unit">
                        <div class="countdown-value" id="minutes">45</div>
                        <div class="countdown-label">Minutes</div>
                    </div>
                    <div class="countdown-unit">
                        <div class="countdown-value" id="seconds">30</div>
                        <div class="countdown-label">Seconds</div>
                    </div>
                </div>
                
                <p class="price-old">Original Price: ₹4,999</p>
                <p class="price-new">Today's Price: ₹2,499</p>
                <p>You save: ₹2,500 (50% OFF)</p>
                
                <div class="bonus-section">
                    <h3><i class="fas fa-gift" style="color: var(--secondary);"></i> Limited Time Bonuses</h3>
                    <ul>
                        <li>Free access to Focus Community (Worth ₹1,999)</li>
                        <li>Extra 3 guided audio sessions (Worth ₹999)</li>
                        <li>Priority customer support</li>
                    </ul>
                </div>
                
                <div style="margin: 30px 0;">
                    <button class="cta-button" onclick="showSection('checkout')">Abhi Order Karein</button>
                </div>
                
                <div class="features">
                    <h3>100% Satisfaction Guarantee</h3>
                    <p>30 din tak use karein. Agar aapko koi fayda nahi hua, toh poora paisa wapas milega. No questions asked.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Checkout Page -->
    <section id="checkout">
        <div class="container">
            <div class="form-section">
                <h2 style="text-align: center; margin-bottom: 30px;">Apna Order Complete Karein</h2>
                
                <div style="display: flex; flex-wrap: wrap; gap: 30px;">
                    <div style="flex: 1; min-width: 300px;">
                        <h3>Order Summary</h3>
                        <div style="background-color: var(--light); padding: 20px; border-radius: 8px; margin: 20px 0;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 15px;">
                                <span>FocusFuel Complete Kit</span>
                                <span>₹2,499</span>
                            </div>
                            <div style="display: flex; justify-content: space-between; margin-bottom: 15px;">
                                <span>Bonus Items</span>
                                <span>FREE</span>
                            </div>
                            <div style="display: flex; justify-content: space-between; font-weight: 700; font-size: 1.2rem; border-top: 1px solid #cbd5e1; padding-top: 15px;">
                                <span>Total</span>
                                <span>₹2,499</span>
                            </div>
                        </div>
                        
                        <h3>Payment Method</h3>
                        <div class="payment-options">
                            <div class="payment-option">
                                <i class="fas fa-mobile-alt"></i>
                                <div>UPI</div>
                            </div>
                            <div class="payment-option">
                                <i class="fas fa-credit-card"></i>
                                <div>Card</div>
                            </div>
                            <div class="payment-option">
                                <i class="fas fa-university"></i>
                                <div>Net Banking</div>
                            </div>
                            <div class="payment-option">
                                <i class="fas fa-wallet"></i>
                                <div>Paytm</div>
                            </div>
                        </div>
                    </div>
                    
                    <div style="flex: 1; min-width: 300px;">
                        <h3>Customer Information</h3>
                        <form>
                            <div class="form-group">
                                <label for="name">Full Name</label>
                                <input type="text" id="name" class="form-control" placeholder="Apna naam likhein">
                            </div>
                            <div class="form-group">
                                <label for="email">Email Address</label>
                                <input type="email" id="email" class="form-control" placeholder="apna@email.com">
                            </div>
                            <div class="form-group">
                                <label for="phone">Phone Number</label>
                                <input type="tel" id="phone" class="form-control" placeholder="Apna phone number">
                            </div>
                            <div class="form-group">
                                <label for="address">Shipping Address</label>
                                <textarea id="address" class="form-control" rows="3" placeholder="Apna complete address"></textarea>
                            </div>
                            <div class="form-group">
                                <label for="pincode">Pincode</label>
                                <input type="text" id="pincode" class="form-control" placeholder="Pincode">
                            </div>
                            
                            <button class="cta-button" style="width: 100%;" onclick="showSection('thankyou'); return false;">Payment Complete Karein</button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Thank You Page -->
    <section id="thankyou">
        <div class="container">
            <div style="text-align: center; padding: 60px 20px;">
                <i class="fas fa-check-circle" style="font-size: 5rem; color: var(--success); margin-bottom: 30px;"></i>
                <h2>Shukriya! Aapka Order Confirm Ho Gaya Hai</h2>
                <p>Aapka order number hai: <strong>FF2023#7894</strong></p>
                <p>Hum aapko jald hi confirmation email bhej denge. Digital products ki download link email aur WhatsApp par bhej di gayi hai.</p>
                
                <div class="form-section" style="max-width: 600px; margin: 40px auto;">
                    <h3>Extra Special Offer</h3>
                    <p>Join our monthly focus challenge group with live coaching sessions at 50% discount!</p>
                    <p><strong>Only ₹999/month</strong> (originally ₹1999)</p>
                    
                    <div style="display: flex; gap: 15px; justify-content: center; margin-top: 30px;">
                        <button class="cta-button" style="background: linear-gradient(to right, var(--success), #059669);">Haan, Add Karein</button>
                        <button class="cta-button" style="background: var(--dark);">Nahi, Shukriya</button>
                    </div>
                </div>
                
                <p>Agar aapko koi sawaal hai, toh hamare support team ko email karein: support@focusfuel.in</p>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <p>© 2023 FocusFuel. All rights reserved.</p>
            <p>Email: info@focusfuel.in | Phone: +91 9876543210</p>
        </div>
    </footer>

    <script>
        // Section navigation
        function showSection(sectionId) {
            document.querySelectorAll('section').forEach(section => {
                section.classList.remove('active');
            });
            document.getElementById(sectionId).classList.add('active');
            window.scrollTo(0, 0);
            
            // Update progress bar
            const sections = ['landing', 'story', 'offer', 'checkout', 'thankyou'];
            const currentIndex = sections.indexOf(sectionId);
            const progress = (currentIndex / (sections.length - 1)) * 100;
            document.getElementById('progressBar').style.width = `${progress}%`;
        }
        
        // Countdown timer
        function updateCountdown() {
            let hours = parseInt(document.getElementById('hours').textContent);
            let minutes = parseInt(document.getElementById('minutes').textContent);
            let seconds = parseInt(document.getElementById('seconds').textContent);
            
            seconds--;
            
            if (seconds < 0) {
                seconds = 59;
                minutes--;
                
                if (minutes < 0) {
                    minutes = 59;
                    hours--;
                    
                    if (hours < 0) {
                        hours = 0;
                        minutes = 0;
                        seconds = 0;
                    }
                }
            }
            
            document.getElementById('hours').textContent = hours.toString().padStart(2, '0');
            document.getElementById('minutes').textContent = minutes.toString().padStart(2, '0');
            document.getElementById('seconds').textContent = seconds.toString().padStart(2, '0');
        }
        
        setInterval(updateCountdown, 1000);
        
        // Fade in elements on scroll
        function checkFade() {
            const fadeElements = document.querySelectorAll('.fade-in');
            
            fadeElements.forEach(element => {
                const elementTop = element.getBoundingClientRect().top;
                const elementVisible = 150;
                
                if (elementTop < window.innerHeight - elementVisible) {
                    element.style.opacity = 1;
                }
            });
        }
        
        window.addEventListener('scroll', checkFade);
        window.addEventListener('load', checkFade);
    </script>
</body>
</html><!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FocusFuel - Apna Dhyan Badhayein</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #2563eb;
            --primary-dark: #1d4ed8;
            --secondary: #f97316;
            --light: #f3f4f6;
            --dark: #1f2937;
            --success: #10b981;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f8fafc;
            color: #334155;
            line-height: 1.6;
        }
        
        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header */
        header {
            background: linear-gradient(to right, var(--primary), var(--primary-dark));
            color: white;
            padding: 15px 0;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 24px;
            font-weight: 700;
            display: flex;
            align-items: center;
        }
        
        .logo i {
            margin-right: 10px;
        }
        
        /* Sections */
        section {
            padding: 60px 0;
            display: none;
        }
        
        section.active {
            display: block;
        }
        
        /* Landing Page */
        .hero {
            text-align: center;
            padding: 40px 0;
        }
        
        .hero h1 {
            font-size: 2.5rem;
            color: var(--dark);
            margin-bottom: 20px;
            line-height: 1.3;
        }
        
        .hero p {
            font-size: 1.2rem;
            margin-bottom: 30px;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .hero-image {
            max-width: 100%;
            border-radius: 10px;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
            margin: 30px 0;
        }
        
        /* CTA Button */
        .cta-button {
            display: inline-block;
            background: linear-gradient(to right, var(--secondary), #ea580c);
            color: white;
            padding: 15px 40px;
            font-size: 1.2rem;
            font-weight: 600;
            border-radius: 50px;
            text-decoration: none;
            margin: 20px 0;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
        }
        
        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 10px rgba(0, 0, 0, 0.2);
        }
        
        /* Features */
        .features {
            background-color: white;
            border-radius: 10px;
            padding: 30px;
            margin: 40px 0;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
        }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }
        
        .feature-card {
            text-align: center;
            padding: 20px;
            border-radius: 10px;
            background-color: var(--light);
            transition: transform 0.3s ease;
        }
        
        .feature-card:hover {
            transform: translateY(-5px);
        }
        
        .feature-icon {
            font-size: 2.5rem;
            color: var(--primary);
            margin-bottom: 15px;
        }
        
        /* Testimonials */
        .testimonials {
            background-color: #eff6ff;
            padding: 50px 0;
        }
        
        .testimonial-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }
        
        .testimonial-card {
            background-color: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
        }
        
        .testimonial-text {
            font-style: italic;
            margin-bottom: 15px;
        }
        
        .testimonial-author {
            font-weight: 600;
            color: var(--primary);
        }
        
        /* Pricing */
        .pricing {
            text-align: center;
            background-color: white;
            padding: 50px 20px;
            border-radius: 10px;
            margin: 40px 0;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
        }
        
        .pricing-badge {
            position: absolute;
            top: 20px;
            right: -35px;
            background-color: var(--secondary);
            color: white;
            padding: 5px 40px;
            transform: rotate(45deg);
            font-weight: 600;
            font-size: 0.9rem;
        }
        
        .price-old {
            text-decoration: line-through;
            color: #94a3b8;
            font-size: 1.5rem;
        }
        
        .price-new {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--dark);
            margin: 10px 0;
        }
        
        .bonus-section {
            background-color: #fffbeb;
            border-left: 4px solid var(--secondary);
            padding: 20px;
            margin: 30px 0;
            text-align: left;
            border-radius: 0 8px 8px 0;
        }
        
        /* Forms */
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
        }
        
        .form-control {
            width: 100%;
            padding: 15px;
            border: 1px solid #cbd5e1;
            border-radius: 8px;
            font-size: 1rem;
        }
        
        .form-section {
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
            margin: 30px 0;
        }
        
        /* Payment Options */
        .payment-options {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin: 20px 0;
        }
        
        .payment-option {
            flex: 1;
            min-width: 120px;
            border: 1px solid #cbd5e1;
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .payment-option:hover {
            border-color: var(--primary);
            box-shadow: 0 0 0 2px #bfdbfe;
        }
        
        .payment-option i {
            font-size: 2rem;
            margin-bottom: 10px;
            color: var(--primary);
        }
        
        /* Footer */
        footer {
            background-color: var(--dark);
            color: white;
            padding: 40px 0;
            text-align: center;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2rem;
            }
            
            .features-grid, .testimonial-grid {
                grid-template-columns: 1fr;
            }
            
            .header-content {
                flex-direction: column;
                text-align: center;
            }
            
            .logo {
                margin-bottom: 15px;
            }
        }
        
        /* Animation */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .fade-in {
            animation: fadeIn 0.8s ease forwards;
        }
        
        /* Progress Bar */
        .progress-container {
            width: 100%;
            height: 8px;
            background-color: #e2e8f0;
            position: fixed;
            top: 0;
            left: 0;
            z-index: 1000;
        }
        
        .progress-bar {
            height: 100%;
            background: linear-gradient(to right, var(--primary), var(--secondary));
            width: 0%;
            transition: width 0.3s ease;
        }
        
        /* Countdown Timer */
        .countdown {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 20px 0;
        }
        
        .countdown-unit {
            background-color: var(--dark);
            color: white;
            padding: 10px;
            border-radius: 8px;
            min-width: 70px;
            text-align: center;
        }
        
        .countdown-value {
            font-size: 1.8rem;
            font-weight: 700;
        }
        
        .countdown-label {
            font-size: 0.8rem;
            text-transform: uppercase;
        }
    </style>
</head>
<body>
    <!-- Progress Bar -->
    <div class="progress-container">
        <div class="progress-bar" id="progressBar"></div>
    </div>

    <!-- Header -->
    <header>
        <div class="container header-content">
            <div class="logo">
                <i class="fas fa-bullseye"></i> FocusFuel
            </div>
            <div class="tagline">
                Apna Dhyan Badhayein, Distractions Kam Karein
            </div>
        </div>
    </header>

    <!-- Landing Page -->
    <section id="landing" class="active">
        <div class="container">
            <div class="hero">
                <h1>Dhyan ki kami se pareshan? Ab paaye turant sukoon</h1>
                <p>FocusFuel aapko dega sab kuch jo aapko apne goals par focus karne ke liye chahiye - digital tools se lekar physical products tak!</p>
                <img src="https://images.unsplash.com/photo-1593640495253-23196b27a87f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1200&q=80" alt="FocusFuel Hero Image" class="hero-image">
                <br>
                <button class="cta-button" onclick="showSection('story')">Free Focus Tips Paayein</button>
            </div>

            <div class="features">
                <h2 style="text-align: center; margin-bottom: 30px;">FocusFuel Kya Hai?</h2>
                <div class="features-grid">
                    <div class="feature-card fade-in">
                        <div class="feature-icon">
                            <i class="fas fa-book"></i>
                        </div>
                        <h3>Distraction-blocking eBook</h3>
                        <p>90 pages ki comprehensive guide distractions ko conquer karne ke liye</p>
                    </div>
                    <div class="feature-card fade-in">
                        <div class="feature-icon">
                            <i class="fas fa-headphones"></i>
                        </div>
                        <h3>Guided Audio Sessions</h3>
                        <p>5 professional audio sessions focus badhane ke liye</p>
                    </div>
                    <div class="feature-card fade-in">
                        <div class="feature-icon">
                            <i class="fas fa-mobile-alt"></i>
                        </div>
                        <h3>Phone Wallpapers</h3>
                        <p>12 specially designed wallpapers jo aapko focus karne mein help karenge</p>
                    </div>
                    <div class="feature-card fade-in">
                        <div class="feature-icon">
                            <i class="fas fa-gift"></i>
                        </div>
                        <h3>Physical Focus Kit</h3>
                        <p>Habit cards, timer, aur premium pen - aapke desk ke liye</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Story/Bridge Page -->
    <section id="story">
        <div class="container">
            <h2 style="text-align: center; margin-bottom: 30px;">Kaam Kaise Karta Hai FocusFuel?</h2>
            
            <div style="text-align: center; margin: 40px 0;">
                <div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 10px; box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1);">
                    <img src="https://images.unsplash.com/photo-1593642632823-8f785ba67e45?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1200&q=80" alt="FocusFuel Transformation" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; object-fit: cover;">
                </div>
                <p style="margin-top: 20px; font-style: italic;">FocusFuel ka istemal karte hue ek user ka transformation</p>
            </div>
            
            <div class="features-grid">
                <div class="form-section">
                    <h3>Digital Product Ke Fayde</h3>
                    <ul style="list-style-type: none; margin: 20px 0;">
                        <li style="padding: 10px 0; border-bottom: 1px solid #e2e8f0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Instant access - abhi download karein</li>
                        <li style="padding: 10px 0; border-bottom: 1px solid #e2e8f0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Kahi bhi, kabhi bhi use kar sakte hain</li>
                        <li style="padding: 10px 0; border-bottom: 1px solid #e2e8f0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Phone, tablet, computer par available</li>
                        <li style="padding: 10px 0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Regularly updated content</li>
                    </ul>
                </div>
                
                <div class="form-section">
                    <h3>Physical Product Ke Fayde</h3>
                    <ul style="list-style-type: none; margin: 20px 0;">
                        <li style="padding: 10px 0; border-bottom: 1px solid #e2e8f0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Tangible product jo aap feel kar sakte hain</li>
                        <li style="padding: 10px 0; border-bottom: 1px solid #e2e8f0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Desk par rakhein, daily reminder ke taur par</li>
                        <li style="padding: 10px 0; border-bottom: 1px solid #e2e8f0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> High-quality materials se bana hua</li>
                        <li style="padding: 10px 0;"><i class="fas fa-check-circle" style="color: var(--success); margin-right: 10px;"></i> Free delivery all over India</li>
                    </ul>
                </div>
            </div>
            
            <div style="text-align: center; margin: 40px 0;">
                <button class="cta-button" onclick="showSection('offer')">Apna Focus Badhayein</button>
            </div>
            
            <div class="testimonial-grid">
                <div class="testimonial-card">
                    <p class="testimonial-text">"FocusFuel ne meri productivity double kar di! Pehle main 2-3 ghante mein jo kaam karta tha, ab wohi kaam 1 ghante mein ho jata hai."</p>
                    <p class="testimonial-author">- Rahul, IIT Student</p>
                </div>
                <div class="testimonial-card">
                    <p class="testimonial-text">"Is product ne meri life change kar di. Main apne business par focus kar pa raha hoon aur results aa rahe hain."</p>
                    <p class="testimonial-author">- Priya, Entrepreneur</p>
                </div>
                <div class="testimonial-card">
                    <p class="testimonial-text">"Audio sessions bahut effective hain. Subah 15 minute sunne se pure din focus maintain hota hai."</p>
                    <p class="testimonial-author">- Amit, Software Engineer</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Offer Page -->
    <section id="offer">
        <div class="container">
            <div class="pricing">
                <div class="pricing-badge">50% OFF</div>
                <h2>Special Introductory Offer</h2>
                <p>First-time buyers ke liye exclusive discount</p>
                
                <div class="countdown">
                    <div class="countdown-unit">
                        <div class="countdown-value" id="hours">06</div>
                        <div class="countdown-label">Hours</div>
                    </div>
                    <div class="countdown-unit">
                        <div class="countdown-value" id="minutes">45</div>
                        <div class="countdown-label">Minutes</div>
                    </div>
                    <div class="countdown-unit">
                        <div class="countdown-value" id="seconds">30</div>
                        <div class="countdown-label">Seconds</div>
                    </div>
                </div>
                
                <p class="price-old">Original Price: ₹4,999</p>
                <p class="price-new">Today's Price: ₹2,499</p>
                <p>You save: ₹2,500 (50% OFF)</p>
                
                <div class="bonus-section">
                    <h3><i class="fas fa-gift" style="color: var(--secondary);"></i> Limited Time Bonuses</h3>
                    <ul>
                        <li>Free access to Focus Community (Worth ₹1,999)</li>
                        <li>Extra 3 guided audio sessions (Worth ₹999)</li>
                        <li>Priority customer support</li>
                    </ul>
                </div>
                
                <div style="margin: 30px 0;">
                    <button class="cta-button" onclick="showSection('checkout')">Abhi Order Karein</button>
                </div>
                
                <div class="features">
                    <h3>100% Satisfaction Guarantee</h3>
                    <p>30 din tak use karein. Agar aapko koi fayda nahi hua, toh poora paisa wapas milega. No questions asked.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Checkout Page -->
    <section id="checkout">
        <div class="container">
            <div class="form-section">
                <h2 style="text-align: center; margin-bottom: 30px;">Apna Order Complete Karein</h2>
                
                <div style="display: flex; flex-wrap: wrap; gap: 30px;">
                    <div style="flex: 1; min-width: 300px;">
                        <h3>Order Summary</h3>
                        <div style="background-color: var(--light); padding: 20px; border-radius: 8px; margin: 20px 0;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 15px;">
                                <span>FocusFuel Complete Kit</span>
                                <span>₹2,499</span>
                            </div>
                            <div style="display: flex; justify-content: space-between; margin-bottom: 15px;">
                                <span>Bonus Items</span>
                                <span>FREE</span>
                            </div>
                            <div style="display: flex; justify-content: space-between; font-weight: 700; font-size: 1.2rem; border-top: 1px solid #cbd5e1; padding-top: 15px;">
                                <span>Total</span>
                                <span>₹2,499</span>
                            </div>
                        </div>
                        
                        <h3>Payment Method</h3>
                        <div class="payment-options">
                            <div class="payment-option">
                                <i class="fas fa-mobile-alt"></i>
                                <div>UPI</div>
                            </div>
                            <div class="payment-option">
                                <i class="fas fa-credit-card"></i>
                                <div>Card</div>
                            </div>
                            <div class="payment-option">
                                <i class="fas fa-university"></i>
                                <div>Net Banking</div>
                            </div>
                            <div class="payment-option">
                                <i class="fas fa-wallet"></i>
                                <div>Paytm</div>
                            </div>
                        </div>
                    </div>
                    
                    <div style="flex: 1; min-width: 300px;">
                        <h3>Customer Information</h3>
                        <form>
                            <div class="form-group">
                                <label for="name">Full Name</label>
                                <input type="text" id="name" class="form-control" placeholder="Apna naam likhein">
                            </div>
                            <div class="form-group">
                                <label for="email">Email Address</label>
                                <input type="email" id="email" class="form-control" placeholder="apna@email.com">
                            </div>
                            <div class="form-group">
                                <label for="phone">Phone Number</label>
                                <input type="tel" id="phone" class="form-control" placeholder="Apna phone number">
                            </div>
                            <div class="form-group">
                                <label for="address">Shipping Address</label>
                                <textarea id="address" class="form-control" rows="3" placeholder="Apna complete address"></textarea>
                            </div>
                            <div class="form-group">
                                <label for="pincode">Pincode</label>
                                <input type="text" id="pincode" class="form-control" placeholder="Pincode">
                            </div>
                            
                            <button class="cta-button" style="width: 100%;" onclick="showSection('thankyou'); return false;">Payment Complete Karein</button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Thank You Page -->
    <section id="thankyou">
        <div class="container">
            <div style="text-align: center; padding: 60px 20px;">
                <i class="fas fa-check-circle" style="font-size: 5rem; color: var(--success); margin-bottom: 30px;"></i>
                <h2>Shukriya! Aapka Order Confirm Ho Gaya Hai</h2>
                <p>Aapka order number hai: <strong>FF2023#7894</strong></p>
                <p>Hum aapko jald hi confirmation email bhej denge. Digital products ki download link email aur WhatsApp par bhej di gayi hai.</p>
                
                <div class="form-section" style="max-width: 600px; margin: 40px auto;">
                    <h3>Extra Special Offer</h3>
                    <p>Join our monthly focus challenge group with live coaching sessions at 50% discount!</p>
                    <p><strong>Only ₹999/month</strong> (originally ₹1999)</p>
                    
                    <div style="display: flex; gap: 15px; justify-content: center; margin-top: 30px;">
                        <button class="cta-button" style="background: linear-gradient(to right, var(--success), #059669);">Haan, Add Karein</button>
                        <button class="cta-button" style="background: var(--dark);">Nahi, Shukriya</button>
                    </div>
                </div>
                
                <p>Agar aapko koi sawaal hai, toh hamare support team ko email karein: support@focusfuel.in</p>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <p>© 2023 FocusFuel. All rights reserved.</p>
            <p>Email: info@focusfuel.in | Phone: +91 8793334496</p>
        </div>
    </footer>

    <script>
        // Section navigation
        function showSection(sectionId) {
            document.querySelectorAll('section').forEach(section => {
                section.classList.remove('active');
            });
            document.getElementById(sectionId).classList.add('active');
            window.scrollTo(0, 0);
            
            // Update progress bar
            const sections = ['landing', 'story', 'offer', 'checkout', 'thankyou'];
            const currentIndex = sections.indexOf(sectionId);
            const progress = (currentIndex / (sections.length - 1)) * 100;
            document.getElementById('progressBar').style.width = `${progress}%`;
        }
        
        // Countdown timer
        function updateCountdown() {
            let hours = parseInt(document.getElementById('hours').textContent);
            let minutes = parseInt(document.getElementById('minutes').textContent);
            let seconds = parseInt(document.getElementById('seconds').textContent);
            
            seconds--;
            
            if (seconds < 0) {
                seconds = 59;
                minutes--;
                
                if (minutes < 0) {
                    minutes = 59;
                    hours--;
                    
                    if (hours < 0) {
                        hours = 0;
                        minutes = 0;
                        seconds = 0;
                    }
                }
            }
            
            document.getElementById('hours').textContent = hours.toString().padStart(2, '0');
            document.getElementById('minutes').textContent = minutes.toString().padStart(2, '0');
            document.getElementById('seconds').textContent = seconds.toString().padStart(2, '0');
        }
        
        setInterval(updateCountdown, 1000);
        
        // Fade in elements on scroll
        function checkFade() {
            const fadeElements = document.querySelectorAll('.fade-in');
            
            fadeElements.forEach(element => {
                const elementTop = element.getBoundingClientRect().top;
                const elementVisible = 150;
                
                if (elementTop < window.innerHeight - elementVisible) {
                    element.style.opacity = 1;
                }
            });
        }
        
        window.addEventListener('scroll', checkFade);
        window.addEventListener('load', checkFade);
    </script>
</body>
</html>
