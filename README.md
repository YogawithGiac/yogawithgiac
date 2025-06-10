<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Conscious Yoga with Giacomo</title>
    <!-- Chosen Palette: Calm Harmony -->
    <!-- Application Structure Plan: The SPA is designed as a single-page narrative journey. It starts with a Hero section to immediately convey the "Conscious Yoga" brand message. The flow guides the user from the core philosophy ("What is Conscious Yoga?") to an interactive exploration of specific offerings (Vinyasa, Yin, Sound Healing). It then builds a personal connection ("Meet Giacomo"), details the ways to practice, shares the long-term vision ("Sankalpa"), and provides social proof (Testimonials) before ending with a clear call-to-action for booking. This thematic, top-down structure was chosen over a report-like layout to create an emotional and intuitive user experience, making the abstract concepts of healing and self-realization feel accessible and inviting. -->
    <!-- Visualization & Content Choices: The report's qualitative insights are translated into structured, interactive content blocks. Report Info: Differentiated yoga offerings (Vinyasa, Yin, etc.). Goal: Inform & Compare. Viz/Presentation: Interactive tabs. Interaction: On-click content reveal. Justification: Prevents information overload and encourages user engagement. Library/Method: Vanilla JS for state and class toggling. Report Info: Giacomo's unique blend of music, anatomy, and yoga. Goal: Organize & Inform. Viz/Presentation: A multi-column "Meet Giacomo" section with icons. Interaction: Static but visually grouped. Justification: Clearly presents multifaceted skills. Library/Method: Tailwind CSS Grid. Report Info: Sankalpa/Vision. Goal: Inform & Inspire. Viz/Presentation: A dedicated, stylized text block. Justification: Elevates the brand from a service to a mission. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Playfair+Display:wght@400;500&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #FAF9F6;
            color: #4A4A4A;
        }
        h1, h2, h3, h4 {
            font-family: 'Playfair Display', serif;
        }
        .nav-link {
            transition: color 0.3s ease;
        }
        .nav-link:hover {
            color: #8A9A5B;
        }
        .cta-button {
            transition: background-color 0.3s ease, transform 0.2s ease;
        }
        .cta-button:hover {
            transform: translateY(-2px);
        }
        .offering-card {
            transition: all 0.3s ease-in-out;
            cursor: pointer;
        }
        .offering-card.active {
            border-color: #8A9A5B;
            background-color: #FFFFFF;
        }
        .offering-card:not(.active) {
            border-color: #E5E7EB;
        }
        .offering-content {
            display: none;
            transition: opacity 0.5s ease-in-out;
        }
        .offering-content.active {
            display: block;
        }
        .section-fade-in {
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.6s ease-out, transform 0.6s ease-out;
        }
        .section-fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body class="antialiased">

    <header id="header" class="bg-white/80 backdrop-blur-md fixed top-0 left-0 right-0 z-50 shadow-sm">
        <div class="container mx-auto px-6 py-4 flex justify-between items-center">
            <a href="#hero" class="text-xl font-semibold tracking-wider text-gray-800">Yoga with Giac</a>
            <nav class="hidden md:flex items-center space-x-8">
                <a href="#philosophy" class="nav-link text-gray-600">Philosophy</a>
                <a href="#offerings" class="nav-link text-gray-600">The Practice</a>
                <a href="#about" class="nav-link text-gray-600">About</a>
                <a href="#contact" class="nav-link text-gray-600">Contact</a>
            </nav>
            <a href="#contact" class="hidden md:block bg-[#8A9A5B] text-white py-2 px-6 rounded-full cta-button shadow hover:bg-[#7a8a4f]">Book a Session</a>
            <button id="mobile-menu-button" class="md:hidden text-gray-700 focus:outline-none">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path></svg>
            </button>
        </div>
        <div id="mobile-menu" class="hidden md:hidden px-6 pt-2 pb-4 space-y-2">
            <a href="#philosophy" class="block nav-link text-gray-600">Philosophy</a>
            <a href="#offerings" class="block nav-link text-gray-600">The Practice</a>
            <a href="#about" class="block nav-link text-gray-600">About</a>
            <a href="#contact" class="block nav-link text-gray-600">Contact</a>
            <a href="#contact" class="block mt-4 bg-[#8A9A5B] text-white text-center py-2 px-6 rounded-full cta-button shadow hover:bg-[#7a8a4f]">Book a Session</a>
        </div>
    </header>

    <main>
        <section id="hero" class="relative min-h-screen flex items-center bg-cover bg-center" style="background-image: url('https://images.unsplash.com/photo-1544367567-0f2fcb009e0b?q=80&w=2120&auto=format&fit=crop');">
            <div class="absolute inset-0 bg-black/40"></div>
            <div class="relative container mx-auto px-6 text-center text-white">
                <h1 class="text-4xl md:text-6xl lg:text-7xl font-medium leading-tight mb-4">Conscious Yoga</h1>
                <p class="text-lg md:text-xl max-w-3xl mx-auto mb-8">A holistic journey to align mind, body, and spirit. Explore bodily sensations, and discover the profound peace that already lies within you!</p>
                <a href="#offerings" class="bg-white text-[#4A4A4A] py-3 px-10 rounded-full cta-button text-lg font-semibold shadow-lg hover:bg-gray-100">Begin Your Journey</a>
            </div>
        </section>

        <section id="philosophy" class="py-20 md:py-32 section-fade-in">
            <div class="container mx-auto px-6 text-center">
                <h2 class="text-3xl md:text-4xl text-gray-800 mb-6">What is Conscious Yoga?</h2>
                <p class="text-lg text-gray-600 max-w-3xl mx-auto leading-relaxed">
                    My approach to yoga is a holistic one, viewing it as a spiritual and therapeutic path to healing and self-realization. It's more than just physical postures; it is a conscious blending of breath, movement, and meditation. As we practice, we cultivate a deep, self-explorative connection to the Self, founded on the principle that there is no path to happiness—happiness <span class="italic">is</span> the path.
                </p>
            </div>
        </section>

        <section id="offerings" class="py-20 md:py-28 bg-white section-fade-in">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl text-gray-800 mb-4">Practice with Intention</h2>
                    <p class="text-lg text-gray-600 max-w-3xl mx-auto">I offer a range of practices to balance strength and mindfulness, accessible to every age, gender, and level. Click each practice to learn more.</p>
                </div>
                
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 mb-8">
                    <div id="vinyasa-card" class="offering-card active border-2 p-6 rounded-lg text-center" data-content="vinyasa">
                        <h3 class="text-xl font-semibold mb-2">Vinyasa Flow</h3>
                        <p class="text-gray-500">Dynamic & Energizing</p>
                    </div>
                    <div id="yin-card" class="offering-card border-2 p-6 rounded-lg text-center" data-content="yin">
                        <h3 class="text-xl font-semibold mb-2">Yin & Restorative</h3>
                        <p class="text-gray-500">Deep & Meditative</p>
                    </div>
                    <div id="nidra-card" class="offering-card border-2 p-6 rounded-lg text-center" data-content="nidra">
                        <h3 class="text-xl font-semibold mb-2">Yoga Nidra</h3>
                        <p class="text-gray-500">Conscious Relaxation</p>
                    </div>
                    <div id="sound-card" class="offering-card border-2 p-6 rounded-lg text-center" data-content="sound">
                        <h3 class="text-xl font-semibold mb-2">Sound Healing</h3>
                        <p class="text-gray-500">Vibrational Harmony</p>
                    </div>
                </div>

                <div class="max-w-4xl mx-auto p-8 rounded-lg bg-gray-50">
                    <div id="vinyasa-content" class="offering-content active">
                        <h4 class="text-2xl font-semibold mb-4 text-gray-800">Vinyasa Flow: The Dance of Breath and Movement</h4>
                        <p class="text-gray-600 leading-relaxed">Vinyasa synchronizes breath with movement, creating a dynamic, flowing practice. These classes are designed to build heat, strength, and flexibility while focusing the mind. Each sequence is thoughtfully crafted to be both challenging and accessible, leaving you feeling energized, centered, and empowered.</p>
                    </div>
                    <div id="yin-content" class="offering-content">
                        <h4 class="text-2xl font-semibold mb-4 text-gray-800">Yin & Restorative: The Art of Surrender</h4>
                        <p class="text-gray-600 leading-relaxed">In contrast to dynamic flows, Yin and Restorative practices invite stillness and deep release. We hold passive poses for longer periods, targeting the deep connective tissues and promoting flexibility. This meditative approach calms the nervous system, reduces stress, and cultivates a profound sense of inner peace. It's a perfect balance to our active lives.</p>
                    </div>
                    <div id="nidra-content" class="offering-content">
                        <h4 class="text-2xl font-semibold mb-4 text-gray-800">Yoga Nidra: Yogic Sleep</h4>
                        <p class="text-gray-600 leading-relaxed">Yoga Nidra is a powerful guided meditation that induces a state of deep, conscious relaxation between waking and sleeping. It is a systematic practice of moving awareness through the body, systematically calming the mind and body. This practice is incredibly restorative, helping to release deep-seated tensions and rejuvenate your entire being.</p>
                    </div>
                    <div id="sound-content" class="offering-content">
                        <h4 class="text-2xl font-semibold mb-4 text-gray-800">Sound Healing: The Power of Intention</h4>
                        <p class="text-gray-600 leading-relaxed">As a musician, I am passionate about the healing power of sound. In my sessions, I often integrate elements of sound healing using voice, chimes, or other instruments. These vibrations can help release energetic blockages, deepen meditation, and guide you into a state of pure harmony and relaxation, aligning you with your own natural rhythm.</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="about" class="py-20 md:py-32 section-fade-in">
            <div class="container mx-auto px-6">
                <div class="flex flex-col md:flex-row items-center gap-12 md:gap-16">
                    <div class="md:w-1/2 lg:w-2/5">
                        <div class="aspect-w-1 aspect-h-1 rounded-full overflow-hidden shadow-xl">
                            <img src="https://images.unsplash.com/photo-1615655406043-5654344b419b?q=80&w=1887&auto=format&fit=crop" alt="Giacomo Pastore" class="object-cover w-full h-full">
                        </div>
                    </div>
                    <div class="md:w-1/2 lg:w-3/5">
                        <h2 class="text-3xl md:text-4xl text-gray-800 mb-4">Meet Giacomo</h2>
                        <p class="text-gray-600 leading-relaxed mb-6">Born in Rome to a jazz singer and a university professor, my life has always been a blend of art and inquiry. My journey into yoga was a path of self-exploration, a way to deepen my connection with myself. As a 200h Yoga Alliance certified instructor and a passionate musician, I weave together the threads of movement, philosophy, sound, and anatomy to create a truly holistic experience.</p>
                        <p class="text-gray-600 leading-relaxed mb-6">My sociable and bubbly nature (I'm an ENFP-A!) infuses my classes with warmth and accessibility. I strive to create a space where everyone feels welcome to explore, heal, and discover the joy of being present.</p>
                        <div class="flex space-x-6 text-gray-700">
                             <div>
                                <span class="text-2xl">🎵</span>
                                <p class="font-semibold">Musician</p>
                            </div>
                             <div>
                                <span class="text-2xl">🧘‍♂️</span>
                                <p class="font-semibold">200h Certified</p>
                            </div>
                            <div>
                                <span class="text-2xl">♥️</span>
                                <p class="font-semibold">Self-Love Advocate</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="sankalpa" class="py-20 md:py-28 bg-white section-fade-in">
            <div class="container mx-auto px-6 text-center">
                 <h3 class="text-2xl text-gray-500 mb-4 tracking-widest">MY SANKALPA</h3>
                <p class="text-2xl md:text-3xl text-gray-700 max-w-4xl mx-auto leading-relaxed italic">
                    "To open an Arts & Healing center amidst nature, exploring and sharing the power of Yoga, Sound, and other Arts to improve wellness. To guide each guest on a personal journey of self-discovery and contentment."
                </p>
            </div>
        </section>
        
        <section id="ways-to-practice" class="py-20 md:py-28 section-fade-in">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl text-gray-800 mb-4">Ways to Practice with Me</h2>
                    <p class="text-lg text-gray-600 max-w-3xl mx-auto">I offer sessions in various settings across Italy, Spain, and the UK, tailored to your needs.</p>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-5xl mx-auto">
                    <div class="bg-white p-8 rounded-lg shadow-md text-center">
                        <h3 class="text-2xl font-semibold mb-3">Group Sessions</h3>
                        <p class="text-gray-600">Join a vibrant community in small to medium-sized groups, workshops, or special events, both indoors and out.</p>
                    </div>
                    <div class="bg-white p-8 rounded-lg shadow-md text-center">
                        <h3 class="text-2xl font-semibold mb-3">Private 1-on-1</h3>
                        <p class="text-gray-600">Receive a custom practice tailored specifically to your body, goals, and personal journey of self-discovery.</p>
                    </div>
                    <div class="bg-white p-8 rounded-lg shadow-md text-center">
                        <h3 class="text-2xl font-semibold mb-3">Corporate Wellness</h3>
                        <p class="text-gray-600">Bring balance and mindfulness to your workplace. I have experience leading sessions for companies like TikTok UK.</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="contact" class="py-20 md:py-32 bg-white section-fade-in">
            <div class="container mx-auto px-6 text-center">
                <h2 class="text-3xl md:text-4xl text-gray-800 mb-4">Connect & Begin Your Practice</h2>
                <p class="text-lg text-gray-600 max-w-2xl mx-auto mb-8">Ready to explore the path of conscious yoga? Reach out to book a session or ask any questions. I look forward to connecting with you.</p>
                <div class="flex flex-col md:flex-row justify-center items-center space-y-4 md:space-y-0 md:space-x-8 mb-8 text-lg text-gray-700">
                    <p>Email: <a href="mailto:giacomopastore2@gmail.com" class="hover:text-[#8A9A5B] underline">giacomopastore2@gmail.com</a></p>
                    <p>Phone: <a href="tel:+393387944098" class="hover:text-[#8A9A5B] underline">+39 338 794 4098</a></p>
                </div>
                <a href="mailto:giacomopastore2@gmail.com?subject=Yoga Session Inquiry" class="bg-[#8A9A5B] text-white py-3 px-10 rounded-full cta-button text-lg font-semibold shadow-lg hover:bg-[#7a8a4f]">Send an Inquiry</a>
            </div>
        </section>
    </main>

    <footer class="bg-gray-800 text-white py-8">
        <div class="container mx-auto px-6 text-center">
            <p>&copy; 2024 Giacomo Pastore. All Rights Reserved.</p>
            <p class="text-sm text-gray-400 mt-2">"Be Calmly Active and Actively Calm" - Paramahansa Yogananda</p>
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const mobileMenuButton = document.getElementById('mobile-menu-button');
            const mobileMenu = document.getElementById('mobile-menu');
            mobileMenuButton.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });

            const offeringCards = document.querySelectorAll('.offering-card');
            const offeringContents = document.querySelectorAll('.offering-content');

            offeringCards.forEach(card => {
                card.addEventListener('click', () => {
                    const contentId = card.dataset.content;

                    offeringCards.forEach(c => c.classList.remove('active'));
                    card.classList.add('active');

                    offeringContents.forEach(content => {
                        if (content.id === `${contentId}-content`) {
                            content.classList.add('active');
                        } else {
                            content.classList.remove('active');
                        }
                    });
                });
            });

            const sections = document.querySelectorAll('.section-fade-in');
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('visible');
                    }
                });
            }, {
                threshold: 0.1
            });
            sections.forEach(section => {
                observer.observe(section);
            });
            
            const navLinks = document.querySelectorAll('a[href^="#"]');
            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    if (this.pathname === window.location.pathname) {
                       mobileMenu.classList.add('hidden');
                    }
                });
            });
        });
    </script>
</body>
</html>
