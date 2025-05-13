# 🎯 JavaScript Event Handling & Interactive Elements Assignment

Welcome to the **ultimate JavaScript playground**! 🎉 This assignment is where we turn boring web pages into dynamic, responsive, *alive* experiences. Get ready to master **event handling**, build **interactive components**, and validate forms like a pro! 💪

## 📁 Assignment Structure

```
📂 js-event-assignment/
├── index.html         # Your playground – where it all comes together
├── style.css          # Keep it cute (optional but encouraged)
└── script.js          # The JavaScript wizardry happens here
```

---

## 🧪 What to Build

Here’s what your interactive bundle of joy should include:

### 1. Event Handling 🎈  
- Button click ✅  
- Hover effects ✅  
- Keypress detection ✅  
- Bonus: A secret action for a *double-click* or *long press* 🤫

### 2. Interactive Elements 🎮  
- A button that changes text or color  
- An image gallery or slideshow  
- Tabs or accordion-style content  
- Bonus: Add some animation using JS or CSS ✨

### 3. Form Validation 📋✅  
- Required field checks  
- Email format validation  
- Password rules (e.g., min 8 characters)  
- Bonus: Real-time feedback while typing

---

## 🧙‍♂️ Pro Tips

- Keep your code clean and commented – your future self will thank you!
- Think about **user experience** – what makes your site more *fun* to use?
- Don’t be afraid to **Google and experiment** – that’s how real developers roll!

---

## 🎉 Now Go Make It Fun!

Remember – this isn't just code. It's your **first step toward creating magical user experiences**. So play around, break stuff (then fix it), and most of all, have FUN! 😄

Happy Coding! 💻✨  









<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pet Adoption Quiz</title>
    <style>
        /* === GENERAL STYLES === */
        :root {
            --primary: #4e54c8;
            --primary-light: #8f94fb;
            --secondary: #ff7e5f;
            --secondary-light: #feb47b;
            --success: #27ae60;
            --error: #e74c3c;
            --gray-light: #f5f7fa;
            --gray: #dcdde1;
            --dark: #2d3436;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: var(--dark);
            background-color: var(--gray-light);
            padding: 20px;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            position: relative;
        }
        
        header {
            background: linear-gradient(135deg, var(--primary), var(--primary-light));
            color: white;
            padding: 20px;
            text-align: center;
            position: relative;
        }
        
        header h1 {
            margin-bottom: 10px;
            font-size: 28px;
        }
        
        .paw-print {
            position: absolute;
            top: 15px;
            right: 15px;
            font-size: 24px;
            opacity: 0.7;
            cursor: pointer;
            transition: transform 0.3s ease, opacity 0.3s ease;
        }
        
        .paw-print:hover {
            opacity: 1;
            transform: scale(1.2);
        }
        
        /* === TABS STYLES === */
        .tabs {
            display: flex;
            background-color: var(--gray);
        }
        
        .tab {
            padding: 10px 20px;
            cursor: pointer;
            flex-grow: 1;
            text-align: center;
            transition: background-color 0.3s ease;
            border: none;
            background-color: transparent;
            font-family: inherit;
            font-size: 16px;
        }
        
        .tab:hover {
            background-color: rgba(255, 255, 255, 0.3);
        }
        
        .tab.active {
            background-color: white;
            font-weight: bold;
            border-bottom: 3px solid var(--secondary);
        }
        
        /* === TAB CONTENT STYLES === */
        .tab-content {
            display: none;
            padding: 30px;
            animation: fadeIn 0.5s ease;
        }
        
        .tab-content.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* === SLIDESHOW STYLES === */
        .slideshow {
            position: relative;
            margin: 20px 0;
            height: 250px;
            overflow: hidden;
            border-radius: 8px;
        }
        
        .slide {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0;
            transition: opacity 0.5s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            background: var(--gray-light);
        }
        
        .slide.active {
            opacity: 1;
        }
        
        .slide img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
        }
        
        .slide-caption {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.5);
            color: white;
            padding: 10px;
            text-align: center;
        }
        
        .prev-btn, .next-btn {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(0, 0, 0, 0.3);
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            font-size: 18px;
            cursor: pointer;
            z-index: 10;
            transition: background 0.3s ease;
        }
        
        .prev-btn:hover, .next-btn:hover {
            background: rgba(0, 0, 0, 0.6);
        }
        
        .prev-btn {
            left: 10px;
        }
        
        .next-btn {
            right: 10px;
        }
        
        /* === FORM STYLES === */
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 6px;
            font-weight: bold;
        }
        
        input, select, textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--gray);
            border-radius: 4px;
            font-family: inherit;
            font-size: 16px;
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
        }
        
        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(78, 84, 200, 0.1);
        }
        
        .validation-message {
            margin-top: 6px;
            font-size: 14px;
            color: var(--error);
            height: 20px;
            transition: opacity 0.3s ease;
        }
        
        .valid-feedback {
            color: var(--success);
        }
        
        button {
            background: linear-gradient(135deg, var(--secondary), var(--secondary-light));
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        button:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }
        
        button:active {
            transform: translateY(0);
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        
        /* === RESULTS STYLES === */
        .result-container {
            text-align: center;
            padding: 20px;
        }
        
        .result-image {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            object-fit: cover;
            margin: 0 auto 20px;
            border: 5px solid var(--primary-light);
        }
        
        .result-title {
            font-size: 24px;
            margin-bottom: 10px;
            color: var(--primary);
        }
        
        .result-description {
            margin-bottom: 20px;
        }
        
        /* === SECRET FEATURE === */
        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background-color: var(--secondary);
            opacity: 0;
            pointer-events: none;
        }
        
        @keyframes confettiFall {
            0% {
                opacity: 1;
                transform: translateY(-20px) rotate(0deg);
            }
            100% {
                opacity: 0;
                transform: translateY(100vh) rotate(720deg);
            }
        }
        
        .theme-toggle {
            position: absolute;
            top: 15px;
            left: 15px;
            font-size: 20px;
            opacity: 0.7;
            cursor: pointer;
            transition: transform 0.3s ease, opacity 0.3s ease;
        }
        
        .theme-toggle:hover {
            opacity: 1;
            transform: scale(1.2);
        }
        
        /* Dark theme */
        body.dark-theme {
            background-color: #2d3436;
            color: white;
        }
        
        body.dark-theme .container {
            background-color: #353b48;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
        }
        
        body.dark-theme .tab.active {
            background-color: #353b48;
            color: white;
        }
        
        body.dark-theme input, 
        body.dark-theme select, 
        body.dark-theme textarea {
            background-color: #4a5568;
            color: white;
            border-color: #2d3436;
        }
        
        body.dark-theme .slide {
            background-color: #4a5568;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="theme-toggle">🌓</div>
            <h1>Pet Adoption Quiz</h1>
            <p>Find your perfect furry friend!</p>
            <div class="paw-print">🐾</div>
        </header>
        
        <div class="tabs">
            <button class="tab active" data-tab="quiz">Quiz</button>
            <button class="tab" data-tab="gallery">Pet Gallery</button>
            <button class="tab" data-tab="about">About</button>
        </div>
        
        <div class="tab-content active" id="quiz">
            <h2>Take The Quiz</h2>
            <p>Answer a few questions to find out what type of pet would be perfect for you!</p>
            
            <form id="pet-quiz-form">
                <div class="form-group">
                    <label for="name">Your Name *</label>
                    <input type="text" id="name" name="name" required>
                    <div class="validation-message" id="name-validation"></div>
                </div>
                
                <div class="form-group">
                    <label for="email">Email Address *</label>
                    <input type="email" id="email" name="email" required>
                    <div class="validation-message" id="email-validation"></div>
                </div>
                
                <div class="form-group">
                    <label for="password">Create a Password *</label>
                    <input type="password" id="password" name="password" required>
                    <div class="validation-message" id="password-validation"></div>
                </div>
                
                <div class="form-group">
                    <label for="lifestyle">Your Lifestyle</label>
                    <select id="lifestyle" name="lifestyle">
                        <option value="">-- Select an option --</option>
                        <option value="active">Very Active</option>
                        <option value="moderate">Moderately Active</option>
                        <option value="relaxed">Relaxed</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="home">Your Living Situation</label>
                    <select id="home" name="home">
                        <option value="">-- Select an option --</option>
                        <option value="house">House with yard</option>
                        <option value="apartment">Apartment</option>
                        <option value="condo">Condo</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="time">Hours at home per day</label>
                    <select id="time" name="time">
                        <option value="">-- Select an option --</option>
                        <option value="few">Less than 4 hours</option>
                        <option value="half">4-8 hours</option>
                        <option value="most">More than 8 hours</option>
                    </select>
                </div>
                
                <button type="submit" id="submit-btn">Find My Perfect Pet!</button>
            </form>
            
            <div class="result-container" id="result" style="display: none;">
                <img src="/api/placeholder/200/200" alt="Pet match" class="result-image" id="result-image">
                <h3 class="result-title" id="result-title">Your perfect match is...</h3>
                <p class="result-description" id="result-description"></p>
                <button id="restart-btn">Take Quiz Again</button>
            </div>
        </div>
        
        <div class="tab-content" id="gallery">
            <h2>Pet Gallery</h2>
            <p>Browse through our adorable animals looking for forever homes!</p>
            
            <div class="slideshow">
                <div class="slide active">
                    <img src="/api/placeholder/400/200" alt="Golden Retriever">
                    <div class="slide-caption">Meet Buddy, a friendly Golden Retriever</div>
                </div>
                <div class="slide">
                    <img src="/api/placeholder/400/200" alt="Tabby Cat">
                    <div class="slide-caption">This is Whiskers, a playful Tabby Cat</div>
                </div>
                <div class="slide">
                    <img src="/api/placeholder/400/200" alt="Rabbit">
                    <div class="slide-caption">Say hello to Hoppy, an adorable Lop Rabbit</div>
                </div>
                <div class="slide">
                    <img src="/api/placeholder/400/200" alt="Parrot">
                    <div class="slide-caption">Meet Polly, a talkative Amazon Parrot</div>
                </div>
                <button class="prev-btn">←</button>
                <button class="next-btn">→</button>
            </div>
        </div>
        
        <div class="tab-content" id="about">
            <h2>About Our Pet Adoption Quiz</h2>
            <p>Welcome to our Pet Adoption Quiz! We've designed this interactive tool to help match you with the perfect furry (or feathery) companion based on your lifestyle and preferences.</p>
            <br>
            <p>Our quiz considers factors like:</p>
            <ul>
                <li>Your daily activity level</li>
                <li>Your living situation</li>
                <li>How much time you spend at home</li>
            </ul>
            <br>
            <p>After analyzing your responses, we'll suggest the type of pet that would be most compatible with your lifestyle.</p>
            <br>
            <p><strong>Note:</strong> This is just for fun! Always research thoroughly and consult with shelter staff before adopting a pet.</p>
            <br>
            <p><em>Double-click the paw print in the header for a special surprise! 🐾</em></p>
        </div>
    </div>

    <script>
        // ====== TAB FUNCTIONALITY ======
        document.querySelectorAll('.tab').forEach(tab => {
            tab.addEventListener('click', () => {
                // Remove active class from all tabs and tab contents
                document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
                document.querySelectorAll('.tab-content').forEach(content => content.classList.remove('active'));
                
                // Add active class to clicked tab
                tab.classList.add('active');
                
                // Show corresponding tab content
                const tabId = tab.getAttribute('data-tab');
                document.getElementById(tabId).classList.add('active');
            });
        });
        
        // ====== SLIDESHOW FUNCTIONALITY ======
        const slides = document.querySelectorAll('.slide');
        const prevBtn = document.querySelector('.prev-btn');
        const nextBtn = document.querySelector('.next-btn');
        let currentSlide = 0;
        
        function showSlide(index) {
            // Remove active class from all slides
            slides.forEach(slide => slide.classList.remove('active'));
            
            // Handle wraparound
            if (index < 0) {
                currentSlide = slides.length - 1;
            } else if (index >= slides.length) {
                currentSlide = 0;
            } else {
                currentSlide = index;
            }
            
            // Add active class to current slide
            slides[currentSlide].classList.add('active');
        }
        
        // Event listeners for slideshow buttons
        prevBtn.addEventListener('click', () => showSlide(currentSlide - 1));
        nextBtn.addEventListener('click', () => showSlide(currentSlide + 1));
        
        // Auto advance slideshow every 5 seconds
        setInterval(() => {
            showSlide(currentSlide + 1);
        }, 5000);
        
        // ====== FORM VALIDATION ======
        const form = document.getElementById('pet-quiz-form');
        const nameInput = document.getElementById('name');
        const emailInput = document.getElementById('email');
        const passwordInput = document.getElementById('password');
        const lifestyleSelect = document.getElementById('lifestyle');
        const homeSelect = document.getElementById('home');
        const timeSelect = document.getElementById('time');
        
        const nameValidation = document.getElementById('name-validation');
        const emailValidation = document.getElementById('email-validation');
        const passwordValidation = document.getElementById('password-validation');
        
        // Validate name on input
        nameInput.addEventListener('input', validateName);
        
        function validateName() {
            if (!nameInput.value.trim()) {
                nameValidation.textContent = 'Name is required';
                nameValidation.classList.remove('valid-feedback');
                return false;
            } else if (nameInput.value.trim().length < 2) {
                nameValidation.textContent = 'Name must be at least 2 characters';
                nameValidation.classList.remove('valid-feedback');
                return false;
            } else {
                nameValidation.textContent = 'Looks good!';
                nameValidation.classList.add('valid-feedback');
                return true;
            }
        }
        
        // Validate email on input
        emailInput.addEventListener('input', validateEmail);
        
        function validateEmail() {
            const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            
            if (!emailInput.value.trim()) {
                emailValidation.textContent = 'Email is required';
                emailValidation.classList.remove('valid-feedback');
                return false;
            } else if (!emailRegex.test(emailInput.value)) {
                emailValidation.textContent = 'Please enter a valid email address';
                emailValidation.classList.remove('valid-feedback');
                return false;
            } else {
                emailValidation.textContent = 'Valid email!';
                emailValidation.classList.add('valid-feedback');
                return true;
            }
        }
        
        // Validate password on input
        passwordInput.addEventListener('input', validatePassword);
        
        function validatePassword() {
            if (!passwordInput.value) {
                passwordValidation.textContent = 'Password is required';
                passwordValidation.classList.remove('valid-feedback');
                return false;
            } else if (passwordInput.value.length < 8) {
                passwordValidation.textContent = 'Password must be at least 8 characters';
                passwordValidation.classList.remove('valid-feedback');
                return false;
            } else if (!/[A-Z]/.test(passwordInput.value)) {
                passwordValidation.textContent = 'Password must include at least one uppercase letter';
                passwordValidation.classList.remove('valid-feedback');
                return false;
            } else if (!/[0-9]/.test(passwordInput.value)) {
                passwordValidation.textContent = 'Password must include at least one number';
                passwordValidation.classList.remove('valid-feedback');
                return false;
            } else {
                passwordValidation.textContent = 'Strong password!';
                passwordValidation.classList.add('valid-feedback');
                return true;
            }
        }
        
        // Form submission
        form.addEventListener('submit', (e) => {
            e.preventDefault();
            
            // Validate all fields
            const isNameValid = validateName();
            const isEmailValid = validateEmail();
            const isPasswordValid = validatePassword();
            
            if (isNameValid && isEmailValid && isPasswordValid) {
                // Determine pet match based on selections
                const result = determinePetMatch();
                
                // Hide form and show result
                form.style.display = 'none';
                const resultContainer = document.getElementById('result');
                const resultTitle = document.getElementById('result-title');
                const resultDescription = document.getElementById('result-description');
                
                resultTitle.textContent = `Your perfect match is a ${result.pet}!`;
                resultDescription.textContent = result.description;
                resultContainer.style.display = 'block';
            }
        });
        
        // Restart button
        document.getElementById('restart-btn').addEventListener('click', () => {
            document.getElementById('result').style.display = 'none';
            form.reset();
            form.style.display = 'block';
        });
        
        // Determine pet match based on form selections
        function determinePetMatch() {
            const lifestyle = lifestyleSelect.value;
            const home = homeSelect.value;
            const time = timeSelect.value;
            
            // Simple matching logic
            if (lifestyle === 'active' && (home === 'house' || home === 'condo')) {
                return {
                    pet: 'Dog',
                    description: 'Dogs are perfect for active people with enough space. They provide companionship, encourage exercise, and offer unconditional love!'
                };
            } else if ((lifestyle === 'moderate' || lifestyle === 'relaxed') && time === 'most') {
                return {
                    pet: 'Cat',
                    description: 'Cats are ideal for those with a relaxed lifestyle who spend a lot of time at home. They\'re independent yet affectionate companions.'
                };
            } else if (lifestyle === 'relaxed' && (home === 'apartment' || home === 'condo')) {
                return {
                    pet: 'Fish',
                    description: 'Fish are perfect for apartment dwellers with a relaxed lifestyle. They require minimal space and provide a peaceful, calming presence.'
                };
            } else if (time === 'few') {
                return {
                    pet: 'Turtle',
                    description: 'Turtles are excellent pets for busy people who aren\'t home often. They\'re low-maintenance and have fascinating personalities!'
                };
            } else {
                return {
                    pet: 'Rabbit',
                    description: 'Rabbits make wonderful pets for various lifestyles. They\'re social, can be litter-trained, and have moderate exercise needs.'
                };
            }
        }
        
        // ====== KEYBOARD EVENTS ======
        document.addEventListener('keydown', (e) => {
            // Navigate slideshow with arrow keys when on gallery tab
            if (document.getElementById('gallery').classList.contains('active')) {
                if (e.key === 'ArrowLeft') {
                    showSlide(currentSlide - 1);
                } else if (e.key === 'ArrowRight') {
                    showSlide(currentSlide + 1);
                }
            }
            
            // Easter egg - press 'P' to go to pet gallery
            if (e.key === 'p' || e.key === 'P') {
                document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
                document.querySelectorAll('.tab-content').forEach(content => content.classList.remove('active'));
                
                document.querySelector('[data-tab="gallery"]').classList.add('active');
                document.getElementById('gallery').classList.add('active');
            }
        });
        
        // ====== SECRET FEATURE - CONFETTI EFFECT ======
        const pawPrint = document.querySelector('.paw-print');
        let clickCount = 0;
        let lastClickTime = 0;
        
        pawPrint.addEventListener('click', (e) => {
            const currentTime = new Date().getTime();
            
            // Check for double click (within 300ms)
            if (currentTime - lastClickTime < 300) {
                createConfetti();
            }
            
            lastClickTime = currentTime;
        });
        
        // Double-click detection
        pawPrint.addEventListener('dblclick', (e) => {
            e.preventDefault(); // Prevent text selection
            createConfetti();
        });
        
        // Long press detection
        let pressTimer;
        
        pawPrint.addEventListener('mousedown', (e) => {
            pressTimer = setTimeout(() => {
                createConfetti();
            }, 800); // Long press after 800ms
        });
        
        pawPrint.addEventListener('mouseup', () => {
            clearTimeout(pressTimer);
        });
        
        pawPrint.addEventListener('mouseleave', () => {
            clearTimeout(pressTimer);
        });
        
        function createConfetti() {
            // Create 50 confetti pieces
            for (let i = 0; i < 50; i++) {
                createConfettiPiece();
            }
        }
        
        function createConfettiPiece() {
            const confetti = document.createElement('div');
            confetti.className = 'confetti';
            
            // Random position, color, and size
            const x = Math.random() * window.innerWidth;
            const colors = ['#ff7e5f', '#feb47b', '#4e54c8', '#8f94fb', '#27ae60', '#e74c3c'];
            const color = colors[Math.floor(Math.random() * colors.length)];
            const size = Math.floor(Math.random() * 10) + 5;
            
            confetti.style.left = `${x}px`;
            confetti.style.backgroundColor = color;
            confetti.style.width = `${size}px`;
            confetti.style.height = `${size}px`;
            confetti.style.borderRadius = Math.random() > 0.5 ? '50%' : '0';
            
            document.body.appendChild(confetti);
            
            // Animate falling
            confetti.style.animation = `confettiFall ${Math.random() * 3 + 2}s ease forwards`;
            
            // Remove after animation
            setTimeout(() => {
                confetti.remove();
            }, 5000);
        }
        
        // ====== THEME TOGGLE ======
        const themeToggle = document.querySelector('.theme-toggle');
        
        themeToggle.addEventListener('click', () => {
            document.body.classList.toggle('dark-theme');
            themeToggle.textContent = document.body.classList.contains('dark-theme') ? '☀️' : '🌓';
        });
        
        // Hover effect for buttons (can't be done in CSS due to dynamic states)
        document.querySelectorAll('button').forEach(button => {
            button.addEventListener('mouseover', () => {
                button.style.transform = 'translateY(-2px)';
                button.style.boxShadow = '0 4px 10px rgba(0, 0, 0, 0.1)';
            });
            
            button.addEventListener('mouseout', () => {
                button.style.transform = '';
                button.style.boxShadow = '';
            });
        });
    </script>
</body>
</html>
