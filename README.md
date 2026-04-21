<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trapped Heat in Panama</title>
    <style>
        /* Global Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            overflow-x: hidden;
        }
        .section {
            min-height: 100vh;
            padding: 80px 20px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
            transition: opacity 0.6s ease-in-out;
        }
        .section.fade-in {
            opacity: 1;
        }
        h1, h2 {
            font-size: clamp(2.5rem, 5vw, 4rem);
            margin-bottom: 1rem;
            background: linear-gradient(135deg, #FF6B35, #F7931E);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        h2 {
            font-size: clamp(2rem, 4vw, 3rem);
            background: linear-gradient(135deg, #00B894, #00A085);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        .subtitle {
            font-size: clamp(1.2rem, 3vw, 1.8rem);
            margin-bottom: 2rem;
            color: #555;
            max-width: 800px;
        }
        .content {
            font-size: 1.2rem;
            max-width: 900px;
            margin: 0 auto 2rem;
            background: rgba(255,255,255,0.9);
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }
        .btn {
            display: inline-block;
            padding: 15px 40px;
            background: linear-gradient(135deg, #FF6B35, #F7931E);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: bold;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(255,107,53,0.4);
        }
        .cool-btn {
            background: linear-gradient(135deg, #00B894, #00A085);
        }
        .cool-btn:hover {
            box-shadow: 0 15px 40px rgba(0,184,148,0.4);
        }
        ul {
            list-style: none;
            max-width: 900px;
            margin: 0 auto;
        }
        li {
            background: rgba(255,255,255,0.9);
            margin: 1rem 0;
            padding: 1.5rem;
            border-radius: 10px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            text-align: left;
            transition: transform 0.3s ease;
        }
        li:hover {
            transform: translateY(-3px);
        }
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin-top: 2rem;
        }
        .comparison {
            display: flex;
            justify-content: space-around;
            max-width: 1200px;
            gap: 2rem;
        }
        .half {
            flex: 1;
            padding: 2rem;
            background: rgba(255,255,255,0.9);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }
        .hot {
            background: linear-gradient(135deg, rgba(255,107,53,0.2), rgba(247,147,30,0.2));
        }
        .cool {
            background: linear-gradient(135deg, rgba(0,184,148,0.2), rgba(0,160,133,0.2));
        }
        /* Background Images */
        .hero {
            background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), url('https://pplx-res.cloudinary.com/image/upload/pplx_search_images/25cd9c525d76d5d6f08f11ba6abb66ce4264135a.jpg') center/cover no-repeat;
            color: white;
        }
        .hero .content {
            background: rgba(0,0,0,0.5);
            color: white;
        }
        .what-is {
            background: linear-gradient(rgba(255,107,53,0.1), rgba(247,147,30,0.1)), url('https://pplx-res.cloudinary.com/image/upload/pplx_search_images/1d77e92a10c2874eb33d3f438cf7802e3a19ec99.jpg') center/cover;
        }
        .why-panama {
            background: linear-gradient(to right, rgba(255,107,53,0.2), rgba(0,184,148,0.1)), url('https://pplx-res.cloudinary.com/image/upload/pplx_search_images/d42ab1c9ebcc999d7a0d956f9f9dcf47d25134b8.jpg') center/cover;
        }
        .science {
            background: linear-gradient(rgba(255,107,53,0.1), rgba(247,147,30,0.1)), url('https://pplx-res.cloudinary.com/image/upload/pplx_search_images/b6e7d8b87c8491fc568f0ba6533286571f0f53ff.jpg') center/cover;
        }
        .impact {
            background: linear-gradient(rgba(255,107,53,0.2), rgba(0,184,148,0.1)), url('https://pplx-res.cloudinary.com/image/upload/pplx_search_images/ec6707b8f72f437d97779027e5b18dddb5fb2632.jpg') bottom/cover;
        }
        .solution {
            background: linear-gradient(rgba(0,184,148,0.2), rgba(0,160,133,0.2)), url('https://pplx-res.cloudinary.com/image/upload/pplx_search_images/d6d7efe50843c06d4259e162ba83700d80f1c87a.jpg') center/cover;
        }
        .financial {
            background: linear-gradient(rgba(255,107,53,0.1), rgba(247,147,30,0.1)), url('https://pplx-res.cloudinary.com/image/upload/pplx_search_images/5b909c20b340dbfc56f9cfd4afb7666fadd09beb.jpg') center/cover;
        }
        .proposal {
            background: linear-gradient(rgba(0,184,148,0.3), rgba(0,160,133,0.3)), url('https://pplx-res.cloudinary.com/image/upload/pplx_search_images/973023f4c743649a2e460fdc8e15f424e6148d5f.jpg') center/cover;
        }
        .comparison-sec {
            background: linear-gradient(rgba(255,107,53,0.1), rgba(0,184,148,0.1)), url('https://pplx-res.cloudinary.com/image/upload/pplx_search_images/07d8470e19c27f5562e160c0fd876c3e7a4bc115.jpg') center/cover;
        }
        .conclusion {
            background: linear-gradient(rgba(0,184,148,0.2), rgba(0,160,133,0.2)), url('https://pplx-res.cloudinary.com/image/upload/pplx_search_images/868976422e1770d0a7abe94e4d00a1701f916f21.jpg') center/cover;
        }
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(255,255,255,0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            padding: 1rem 0;
        }
        nav ul {
            list-style: none;
            display: flex;
            justify-content: center;
            gap: 2rem;
        }
        nav a {
            text-decoration: none;
            color: #333;
            font-weight: bold;
            transition: color 0.3s;
        }
        nav a:hover {
            color: #FF6B35;
        }
        /* Smooth Scrolling */
        html {
            scroll-behavior: smooth;
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
        .content {
            animation: fadeInUp 1s ease-out;
        }
    </style>
</head>
<body>
    <nav>
        <u
        <ul>
            ><a href="#hero">Home</a></l/li>
            ><a href="#what-is">What is Urban Heat?</a></l/li>
            ><a href="#why-panama">Why Panama?</a></l/li>
            ><a href="#science">The Science</a></l/li>
            ><a href="#impact">Impacts</a></l/li>
            ><a href="#solution">Smart Panel</a></l/li>
            ><a href="#financial">Financials</a></l/li>
            ><a href="#proposal">Ecosphere</a></l/li>
            ><a href="#comparison">Comparison</a></l/li>
            ><a href="#conclusion">Conclusion</a></li>
        </ul>
    </nav>

    <section id="hero" class="section hero">
        <h1>Trapped Heat in Panama</h1>
        <p class="subtitle">Understanding why cities are getting hotter and how we can fix it</p>
        <div class="content">
            <p>Panama has always been a tropical country, but in recent years, the heat in cities feels more intense, heavier, and harder to escape. This website explores the causes, impacts, and solutions to urban heat, combining science, real-world problems, and innovative ideas.</p>
        </div>
        <a href="#what-is" class="btn">Learn More</a>
    </section>

    <section id="what-is" class="section what-is">
        <h2>🌡️ What is Urban Heat?</h2>
        <div class="content">
            <p>Urban heat refers to the increase in temperature in cities compared to surrounding rural areas. This happens because cities are built with materials such as asphalt, concrete, and metal that absorb heat during the day and release it slowly at night.</p>
            <p>As a result, heat becomes trapped, making cities feel hotter even after the sun goes down. This phenomenon is known as the urban heat island effect.</p>
        </div>
    </section>

    <section id="why-panama" class="section why-panama">
        <h2>🌴 Why is Panama Getting Hotter?</h2>
        <div class="content">
            <p>Panama has a tropical climate, but human activity is intensifying heat in cities due to urbanization, lack of vegetation, traffic and emissions, heat-retaining materials, and inefficient urban design.</p>
            <p>The problem is not just heat, but heat that gets trapped and accumulates.</p>
        </div>
        [image:2]
    </section>

    <section id="science" class="section science">
        <h2>🌫️ The Science Behind It</h2>
        <div class="content">
            <p>Carbon dioxide (CO₂) is a greenhouse gas that traps heat in the Earth’s atmosphere. When sunlight reaches the Earth, some heat is reflected back, but CO₂ prevents it from escaping into space.</p>
            <p>This causes temperatures to rise. In cities, this effect combines with heat-absorbing materials, making the environment even hotter.</p>
        </div>
        [image:6]
    </section>

    <section id="impact" class="section impact">
        <h2>🌎 Real Impact in Panama</h2>
        <div class="content">
            <ul class="gridid">
                ><strong>Energy:</strong> Higher temperatures increase the use of air conditioning, raising electricity demand and long-term costs.</l/li>
                ><strong>Panama Canal:</strong> Heat increases water evaporation, lowering water levels and reducing the number of ships that can pass, affecting the economy.</l/li>
                ><strong>Infrastructure:</strong> Materials like asphalt and concrete deteriorate faster under heat, increasing maintenance costs.</l/li>
                ><strong>Productivity:</strong> Heat reduces concentration, increases fatigue, and lowers efficiency.</l/li>
                ><strong>Health and Safety:</strong> Workers exposed to heat face higher risks of dehydration and heat stress.</l/li>
                ><strong>Water:</strong> Higher temperatures increase water consumption and evaporation, putting pressure on resources.</li>
            </ul>
        </div>
        [image:3]
    </section>

    <section id="solution" class="section solution">
        <h2>🧪 Our Solution: Smart Cooling Panel</h2>
        <div class="content">
            <p>We propose a smart cooling panel designed to reduce heat in urban environments.</p>
            <p>The panel works by reflecting sunlight, using passive water cooling, capturing CO₂, and collecting rainwater. This system reduces temperature without relying heavily on electricity.</p>
        </div>
        [image:7]
    </section>

    <section id="financial" class="section financial">
        <h2>💰 Why Financial Solutions Matter</h2>
        <div class="content">
            <p>Many solutions to urban heat already exist, but they are not widely implemented due to high costs.</p>
            <p>Cities must decide how to prioritize investments, manage limited resources, and balance cost and impact. This makes financial planning and negotiation essential.</p>
        </div>
        [image:9]
    </section>

    <section id="proposal" class="section proposal">
        <h2>🌱 Our Proposal: Ecosphere Panama</h2>
        <div class="content">
            <p>Ecosphere Panama is a sustainable company focused on implementing cooling solutions in urban areas.</p>
            <p>Its goal is to reduce heat while making solutions accessible and scalable. The company generates revenue through cooling panel installation, partnerships with businesses, sustainable investments, and carbon credits.</p>
            <p>This approach reduces the financial burden on the government.</p>
        </div>
        [image:4]
    </section>

    <section id="comparison" class="section comparison-sec">
        <h2>🏙️ Visual Comparison</h2>
        <div class="content">
            <p>A comparison between a traditional city and a sustainable city shows how design choices affect temperature.</p>
        </div>
        <div class="comparison">
            <div class="half hot">
                <h3>Hot City</h3>
                <p>Dark materials, no trees, heat waves – temperatures rise.</p>
            </div>
            <div class="half cool">
                <h3>Cool City</h3>
                <p>Green areas, light materials, panels – stays comfortable.</p>
            </div>
        </div>
        [image:10]
    </section>

    <section id="conclusion" class="section conclusion">
        <h2>🧠 Conclusion</h2>
        <div class="content">
            <p>Urban heat is not only a natural condition but also a result of human decisions. It affects energy, water, infrastructure, health, and the economy.</p>
            <p>By combining science, sustainable design, and financial planning, cities can become cooler and more livable.</p>
        </div>
        <a href="#hero" class="btn cool-btn">Back to Top</a>
        <div style="margin-top: 2rem; font-size: 1.1rem; font-style: italic;">
            <p>🔥 The goal is not to eliminate heat, but to prevent it from being trapped. Smart design and better decisions can transform cities and improve quality of life.</p>
        </div>
        [image:8]
    </section>

    <script>
        // Smooth scrolling and fade-in
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                target.scrollIntoView({ behavior: 'smooth' });
            });
        });

        // Fade in sections on scroll
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('fade-in');
                }
            });
        });

        document.querySelectorAll('.section').forEach(section => {
            observer.observe(section);
        });
    </script>
</body>
</html>
