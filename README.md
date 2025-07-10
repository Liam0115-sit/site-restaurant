<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Liam Food - Restaurant Pizza & Burger</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=Nunito:wght@300;400;500;600;700;800&family=Poppins:wght@300;400;500;600;700;800&family=Comfortaa:wght@300;400;500;600;700&display=swap');
        @import url('https://fonts.googleapis.com/css2?family=Fredoka+One&display=swap');
        
        body { 
            font-family: 'Inter', sans-serif;
            line-height: 1.6;
        }
        
        .hero-gradient {
            background: linear-gradient(135deg, rgba(0,0,0,0.6) 0%, rgba(0,0,0,0.4) 100%), 
                        url('https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
        }
        
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 0.8s ease-out forwards;
        }
        
        .fade-in.delay-1 { animation-delay: 0.2s; }
        .fade-in.delay-2 { animation-delay: 0.4s; }
        .fade-in.delay-3 { animation-delay: 0.6s; }
        .fade-in.delay-4 { animation-delay: 0.8s; }
        
        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .card-professional {
            background: white;
            border-radius: 16px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
            transition: all 0.3s ease;
            border: 1px solid #f1f5f9;
        }
        
        .card-professional:hover {
            transform: translateY(-8px);
            box-shadow: 0 12px 40px rgba(0,0,0,0.15);
        }
        
        .btn-primary {
            background: linear-gradient(135deg, #1f2937 0%, #374151 100%);
            color: white;
            border: none;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(31, 41, 55, 0.3);
        }
        
        .btn-secondary {
            background: transparent;
            color: #1f2937;
            border: 2px solid #1f2937;
            transition: all 0.3s ease;
        }
        
        .btn-secondary:hover {
            background: #1f2937;
            color: white;
            transform: translateY(-2px);
        }
        
        .accent-gold {
            color: #d97706;
        }
        
        .bg-accent-gold {
            background-color: #d97706;
        }
        
        .page {
            display: none;
            animation: pageSlideIn 0.5s ease-out;
        }
        
        .page.active {
            display: block;
        }
        
        @keyframes pageSlideIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .menu-item-pro {
            background: white;
            border: 1px solid #e2e8f0;
            border-radius: 12px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .menu-item-pro:hover {
            border-color: #d97706;
            transform: translateX(4px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
        }
        
        .price-professional {
            background: #1f2937;
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 8px;
            font-weight: 600;
            font-size: 1.1rem;
        }
        
        .nav-professional {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(0,0,0,0.1);
        }
        
        .section-title {
            position: relative;
            display: inline-block;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 3px;
            background: #d97706;
            border-radius: 2px;
        }
        
        .image-overlay {
            position: relative;
            overflow: hidden;
            border-radius: 12px;
        }
        
        .image-overlay::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, rgba(0,0,0,0.1) 0%, transparent 100%);
            z-index: 1;
        }
        
        .stats-counter {
            font-size: 3rem;
            font-weight: 800;
            color: #1f2937;
        }
        
        .intro-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: linear-gradient(135deg, #1f2937 0%, #374151 50%, #1f2937 100%);
            z-index: 9999;
            display: flex;
            align-items: center;
            justify-content: center;
            animation: hideIntro 4s ease-in-out forwards;
            overflow: hidden;
        }
        
        .logo-reveal {
            position: relative;
            text-align: center;
            animation: logoEntrance 4s ease-out forwards;
        }
        
        .logo-reveal .logo-icon {
            width: 120px;
            height: 120px;
            background: white;
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 2rem;
            font-size: 4rem;
            font-weight: bold;
            color: #1f2937;
            animation: iconSpin 4s ease-out forwards;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }
        
        .logo-reveal .brand-name {
            font-size: 4rem;
            font-weight: 800;
            color: white;
            margin-bottom: 1rem;
            opacity: 0;
            animation: textSlideUp 4s ease-out 0.5s forwards;
            font-family: 'Inter', sans-serif;
            letter-spacing: -2px;
        }
        
        .logo-reveal .brand-tagline {
            font-size: 1.5rem;
            color: #d1d5db;
            opacity: 0;
            animation: textSlideUp 4s ease-out 1s forwards;
            font-weight: 300;
        }
        
        .loading-bar {
            position: absolute;
            bottom: 80px;
            left: 50%;
            transform: translateX(-50%);
            width: 300px;
            height: 3px;
            background: rgba(255,255,255,0.2);
            border-radius: 2px;
            overflow: hidden;
        }
        
        .loading-bar::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, #d97706, transparent);
            animation: loadingProgress 4s ease-out forwards;
        }
        
        @keyframes logoEntrance {
            0% {
                transform: scale(0.3) rotateY(-180deg);
                opacity: 0;
            }
            30% {
                transform: scale(1.1) rotateY(0deg);
                opacity: 1;
            }
            70% {
                transform: scale(1) rotateY(0deg);
                opacity: 1;
            }
            100% {
                transform: scale(1) rotateY(0deg);
                opacity: 0;
            }
        }
        
        @keyframes iconSpin {
            0% {
                transform: rotateY(-180deg) scale(0.3);
                box-shadow: 0 0 0 rgba(0,0,0,0);
            }
            30% {
                transform: rotateY(0deg) scale(1.1);
                box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            }
            70% {
                transform: rotateY(0deg) scale(1);
                box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            }
            100% {
                transform: rotateY(0deg) scale(1);
                box-shadow: 0 0 0 rgba(0,0,0,0);
            }
        }
        
        @keyframes textSlideUp {
            0% {
                opacity: 0;
                transform: translateY(30px);
            }
            30% {
                opacity: 1;
                transform: translateY(0);
            }
            70% {
                opacity: 1;
                transform: translateY(0);
            }
            100% {
                opacity: 0;
                transform: translateY(-20px);
            }
        }
        
        @keyframes loadingProgress {
            0% {
                left: -100%;
            }
            100% {
                left: 100%;
            }
        }
        
        @keyframes hideIntro {
            0% {
                opacity: 1;
                visibility: visible;
            }
            85% {
                opacity: 1;
                visibility: visible;
            }
            100% {
                opacity: 0;
                visibility: hidden;
                pointer-events: none;
            }
        }
    </style>
</head>
<body class="bg-gray-50">
    <!-- Animation d'ouverture -->
    <div class="intro-animation">
        <div class="logo-reveal">
            <div class="logo-icon">LF</div>
            <div class="brand-name">Liam Food</div>
            <div class="brand-tagline">Excellence Culinaire</div>
        </div>
        <div class="loading-bar"></div>
    </div>

    <!-- Navigation -->
    <nav class="nav-professional shadow-lg fixed w-full top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-20">
                <div class="flex items-center">
                    <div class="flex items-center space-x-4">
                        <div class="w-12 h-12 bg-gray-900 rounded-lg flex items-center justify-center">
                            <span class="text-white text-xl font-bold">LF</span>
                        </div>
                        <div>
                            <h1 class="text-2xl font-bold text-gray-900">Liam Food</h1>
                            <p class="text-sm text-gray-500 -mt-1">Restaurant • Pizza • Burger • Frites</p>
                        </div>
                    </div>
                </div>
                
                <div class="hidden md:flex items-center space-x-8">
                    <button onclick="showPage('home')" class="text-gray-700 hover:text-gray-900 font-medium transition-colors">
                        Accueil
                    </button>
                    <button onclick="showPage('menu')" class="text-gray-700 hover:text-gray-900 font-medium transition-colors">
                        Menu
                    </button>
                    <button onclick="showPage('about')" class="text-gray-700 hover:text-gray-900 font-medium transition-colors">
                        À propos
                    </button>
                    <button onclick="showPage('contact')" class="text-gray-700 hover:text-gray-900 font-medium transition-colors">
                        Contact
                    </button>
                </div>
                
                <button onclick="showPage('contact')" class="btn-primary px-6 py-3 rounded-lg font-semibold">
                    Commander
                </button>
            </div>
        </div>
    </nav>

    <!-- Page d'Accueil -->
    <div id="home" class="page active">
        <!-- Hero Section -->
        <section class="hero-gradient min-h-screen flex items-center justify-center relative">
            <div class="absolute inset-0 bg-black/40"></div>
            
            <div class="relative z-10 text-center max-w-5xl mx-auto px-6">
                <div class="fade-in bg-white/10 backdrop-blur-md inline-block px-6 py-2 rounded-full mb-8">
                    <span class="text-white font-medium">🍽️ Depuis 2014 • Qualité & Tradition</span>
                </div>
                
                <h1 class="fade-in delay-1 text-6xl md:text-7xl lg:text-8xl font-bold text-white mb-6">
                    Liam Food
                </h1>
                
                <h2 class="fade-in delay-2 text-2xl md:text-3xl lg:text-4xl font-medium text-white/90 mb-8">
                    Restaurant Pizza & Burger
                </h2>
                
                <p class="fade-in delay-3 text-xl text-white/80 mb-12 max-w-3xl mx-auto">
                    Découvrez nos spécialités préparées avec des ingrédients frais et de qualité. 
                    Une cuisine authentique qui respecte les traditions.
                </p>
                
                <div class="fade-in delay-4 flex flex-col sm:flex-row gap-4 justify-center">
                    <button onclick="showPage('menu')" class="btn-primary px-8 py-4 rounded-lg font-semibold text-lg">
                        Découvrir le Menu
                    </button>
                    <button onclick="showPage('contact')" class="btn-secondary px-8 py-4 rounded-lg font-semibold text-lg bg-white text-gray-900 hover:bg-gray-100">
                        Nous Contacter
                    </button>
                </div>
            </div>
        </section>

        <!-- Section Nos Spécialités -->
        <section class="py-20 bg-white">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h2 class="section-title text-4xl md:text-5xl font-bold text-gray-900 mb-6">Nos Spécialités</h2>
                    <p class="text-xl text-gray-600 max-w-3xl mx-auto">
                        Des plats préparés avec passion et savoir-faire
                    </p>
                </div>

                <div class="grid md:grid-cols-3 gap-8">
                    <div class="card-professional p-8 text-center">
                        <div class="image-overlay mb-6 h-48 bg-gray-200 rounded-lg overflow-hidden">
                            <img src="https://images.unsplash.com/photo-1513104890138-7c749659a591?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" 
                                 alt="Pizza" class="w-full h-full object-cover">
                        </div>
                        <h3 class="text-2xl font-bold text-gray-900 mb-4">Pizzas Artisanales</h3>
                        <p class="text-gray-600 mb-6 leading-relaxed">
                            Pâtes fraîches préparées quotidiennement, ingrédients de qualité et cuisson au four traditionnel. 
                            L'authenticité italienne dans chaque bouchée.
                        </p>
                        <div class="price-professional inline-block">À partir de 11,50€</div>
                    </div>

                    <div class="card-professional p-8 text-center">
                        <div class="image-overlay mb-6 h-48 bg-gray-200 rounded-lg overflow-hidden">
                            <img src="https://images.unsplash.com/photo-1568901346375-23c9450c58cd?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" 
                                 alt="Burger" class="w-full h-full object-cover">
                        </div>
                        <h3 class="text-2xl font-bold text-gray-900 mb-4">Burgers Artisanaux</h3>
                        <p class="text-gray-600 mb-6 leading-relaxed">
                            Steaks de qualité, fromages sélectionnés et légumes frais dans nos pains 
                            briochés préparés quotidiennement.
                        </p>
                        <div class="price-professional inline-block">À partir de 12,50€</div>
                    </div>

                    <div class="card-professional p-8 text-center">
                        <div class="image-overlay mb-6 h-48 bg-gray-200 rounded-lg overflow-hidden">
                            <img src="https://images.unsplash.com/photo-1544025162-d76694265947?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" 
                                 alt="Grillades" class="w-full h-full object-cover">
                        </div>
                        <h3 class="text-2xl font-bold text-gray-900 mb-4">Grillades Premium</h3>
                        <p class="text-gray-600 mb-6 leading-relaxed">
                            Viandes grillées à la perfection, accompagnements savoureux et sauces 
                            traditionnelles pour une expérience gustative unique.
                        </p>
                        <div class="price-professional inline-block">À partir de 16,50€</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section Avantages -->
        <section class="py-20 bg-gray-50">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h2 class="section-title text-4xl md:text-5xl font-bold text-gray-900 mb-6">Pourquoi Nous Choisir</h2>
                    <p class="text-xl text-gray-600 max-w-3xl mx-auto">
                        Notre engagement pour votre satisfaction
                    </p>
                </div>

                <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
                    <div class="text-center">
                        <div class="w-16 h-16 bg-gray-900 rounded-full flex items-center justify-center mx-auto mb-6">
                            <span class="text-2xl text-white">⚡</span>
                        </div>
                        <h3 class="text-xl font-bold text-gray-900 mb-3">Service Rapide</h3>
                        <p class="text-gray-600">Préparation soignée en moins de 15 minutes</p>
                    </div>

                    <div class="text-center">
                        <div class="w-16 h-16 bg-gray-900 rounded-full flex items-center justify-center mx-auto mb-6">
                            <span class="text-2xl text-white">🥬</span>
                        </div>
                        <h3 class="text-xl font-bold text-gray-900 mb-3">Ingrédients Frais</h3>
                        <p class="text-gray-600">Produits sélectionnés quotidiennement</p>
                    </div>

                    <div class="text-center">
                        <div class="w-16 h-16 bg-gray-900 rounded-full flex items-center justify-center mx-auto mb-6">
                            <span class="text-2xl text-white">💰</span>
                        </div>
                        <h3 class="text-xl font-bold text-gray-900 mb-3">Prix Justes</h3>
                        <p class="text-gray-600">Qualité premium à prix accessible</p>
                    </div>

                    <div class="text-center">
                        <div class="w-16 h-16 bg-gray-900 rounded-full flex items-center justify-center mx-auto mb-6">
                            <span class="text-2xl text-white">👨‍🍳</span>
                        </div>
                        <h3 class="text-xl font-bold text-gray-900 mb-3">Savoir-Faire</h3>
                        <p class="text-gray-600">10 ans d'expérience et de passion</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section Statistiques -->
        <section class="py-20 bg-gray-900">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="grid md:grid-cols-4 gap-8 text-center text-white">
                    <div>
                        <div class="stats-counter text-white mb-2">10+</div>
                        <div class="text-lg text-gray-300">Années d'Expérience</div>
                    </div>
                    <div>
                        <div class="stats-counter text-white mb-2">5K+</div>
                        <div class="text-lg text-gray-300">Clients Satisfaits</div>
                    </div>
                    <div>
                        <div class="stats-counter text-white mb-2">50+</div>
                        <div class="text-lg text-gray-300">Plats au Menu</div>
                    </div>
                    <div>
                        <div class="stats-counter text-white mb-2">7j/7</div>
                        <div class="text-lg text-gray-300">Service Continu</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section Témoignages Clients -->
        <section class="py-20 bg-gray-50">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h2 class="section-title text-4xl md:text-5xl font-bold text-gray-900 mb-6">Ce Que Disent Nos Clients</h2>
                    <p class="text-xl text-gray-600 max-w-3xl mx-auto">
                        Des avis authentiques qui témoignent de notre excellence
                    </p>
                </div>

                <div class="grid md:grid-cols-3 gap-8 mb-12">
                    <div class="card-professional p-8">
                        <div class="flex items-center mb-6">
                            <div class="w-12 h-12 bg-gray-900 rounded-full flex items-center justify-center mr-4">
                                <span class="text-white font-bold">M</span>
                            </div>
                            <div>
                                <h4 class="font-bold text-gray-900">Marie L.</h4>
                                <div class="flex text-yellow-400">
                                    <span>★★★★★</span>
                                </div>
                            </div>
                        </div>
                        <p class="text-gray-600 italic leading-relaxed">
                            "Excellent restaurant ! Les pizzas sont délicieuses et le service est rapide. 
                            Je recommande vivement, c'est devenu notre adresse préférée."
                        </p>
                    </div>

                    <div class="card-professional p-8">
                        <div class="flex items-center mb-6">
                            <div class="w-12 h-12 bg-gray-900 rounded-full flex items-center justify-center mr-4">
                                <span class="text-white font-bold">J</span>
                            </div>
                            <div>
                                <h4 class="font-bold text-gray-900">Jean-Pierre D.</h4>
                                <div class="flex text-yellow-400">
                                    <span>★★★★★</span>
                                </div>
                            </div>
                        </div>
                        <p class="text-gray-600 italic leading-relaxed">
                            "Les burgers sont exceptionnels ! Ingrédients frais, cuisson parfaite. 
                            L'équipe est accueillante et professionnelle. Une vraie réussite !"
                        </p>
                    </div>

                    <div class="card-professional p-8">
                        <div class="flex items-center mb-6">
                            <div class="w-12 h-12 bg-gray-900 rounded-full flex items-center justify-center mr-4">
                                <span class="text-white font-bold">S</span>
                            </div>
                            <div>
                                <h4 class="font-bold text-gray-900">Sophie M.</h4>
                                <div class="flex text-yellow-400">
                                    <span>★★★★★</span>
                                </div>
                            </div>
                        </div>
                        <p class="text-gray-600 italic leading-relaxed">
                            "Qualité constante depuis des années. Les grillades sont parfaites et 
                            l'ambiance familiale nous fait revenir régulièrement. Bravo !"
                        </p>
                    </div>
                </div>

                <div class="text-center">
                    <button onclick="window.open('https://www.google.com/maps/search/Liam+Food+S%C3%A9n%C3%A9/', '_blank')" 
                            class="btn-secondary px-8 py-4 rounded-lg font-semibold text-lg inline-flex items-center space-x-2">
                        <span>📍</span>
                        <span>Voir Plus d'Avis sur Google</span>
                    </button>
                </div>
            </div>
        </section>

        <!-- Call to Action -->
        <section class="py-20 bg-white">
            <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
                <h2 class="text-4xl md:text-5xl font-bold text-gray-900 mb-6">Prêt à Commander ?</h2>
                <p class="text-xl text-gray-600 mb-10">
                    Découvrez nos spécialités et laissez-vous séduire par nos saveurs authentiques
                </p>
                <div class="flex flex-col sm:flex-row gap-4 justify-center">
                    <button onclick="showPage('menu')" class="btn-primary px-8 py-4 rounded-lg font-semibold text-lg">
                        Voir le Menu
                    </button>
                    <button onclick="showPage('contact')" class="btn-secondary px-8 py-4 rounded-lg font-semibold text-lg">
                        Nous Contacter
                    </button>
                </div>
            </div>
        </section>
    </div>

    <!-- Page Menu -->
    <div id="menu" class="page">
        <section class="pt-32 pb-20 bg-white">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h1 class="section-title text-5xl md:text-6xl font-bold text-gray-900 mb-6">Notre Menu</h1>
                    <p class="text-xl text-gray-600 max-w-3xl mx-auto">
                        Découvrez notre sélection de plats préparés avec passion
                    </p>
                </div>

                <!-- Menu Categories -->
                <div class="grid lg:grid-cols-2 gap-12">
                    <!-- Burgers -->
                    <div class="card-professional overflow-hidden">
                        <div class="image-overlay mb-0 h-48 bg-gray-200 overflow-hidden">
                            <img src="https://images.unsplash.com/photo-1568901346375-23c9450c58cd?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" 
                                 alt="Burgers" class="w-full h-full object-cover object-center">
                        </div>
                        <div class="bg-gray-900 p-8 text-center">
                            <div class="w-20 h-20 bg-white/10 rounded-full flex items-center justify-center mx-auto mb-4">
                                <span class="text-4xl">🍔</span>
                            </div>
                            <h2 class="text-3xl font-bold text-white mb-2">Burgers</h2>
                            <p class="text-gray-300">Nos créations gourmandes</p>
                        </div>
                        <div class="p-8 space-y-6">
                            <div class="menu-item-pro p-6">
                                <div class="flex justify-between items-start mb-3">
                                    <h3 class="text-xl font-bold text-gray-900">Burger Signature</h3>
                                    <span class="price-professional">14,50€</span>
                                </div>
                                <p class="text-gray-600 mb-3">Steak de bœuf 180g, bacon, cheddar, salade, tomates, sauce maison</p>
                                <div class="flex flex-wrap gap-2">
                                    <span class="px-3 py-1 bg-red-100 text-red-800 rounded-full text-sm">Bœuf</span>
                                </div>
                            </div>

                            <div class="menu-item-pro p-6">
                                <div class="flex justify-between items-start mb-3">
                                    <h3 class="text-xl font-bold text-gray-900">Chicken Deluxe</h3>
                                    <span class="price-professional">12,50€</span>
                                </div>
                                <p class="text-gray-600 mb-3">Filet de poulet grillé, avocat, emmental, salade, sauce curry</p>
                                <div class="flex flex-wrap gap-2">
                                    <span class="px-3 py-1 bg-green-100 text-green-800 rounded-full text-sm">Halal</span>
                                </div>
                            </div>

                            <div class="menu-item-pro p-6">
                                <div class="flex justify-between items-start mb-3">
                                    <h3 class="text-xl font-bold text-gray-900">Veggie Burger</h3>
                                    <span class="price-professional">11,00€</span>
                                </div>
                                <p class="text-gray-600 mb-3">Steak végétal, guacamole, légumes grillés, fromage de chèvre</p>
                                <div class="flex flex-wrap gap-2">
                                    <span class="px-3 py-1 bg-green-100 text-green-800 rounded-full text-sm">Végétarien</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Pizzas -->
                    <div class="card-professional overflow-hidden">
                        <div class="image-overlay mb-0 h-48 bg-gray-200 overflow-hidden">
                            <img src="https://images.unsplash.com/photo-1513104890138-7c749659a591?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" 
                                 alt="Pizzas" class="w-full h-full object-cover object-center">
                        </div>
                        <div class="bg-gray-900 p-8 text-center">
                            <div class="w-20 h-20 bg-white/10 rounded-full flex items-center justify-center mx-auto mb-4">
                                <span class="text-4xl">🍕</span>
                            </div>
                            <h2 class="text-3xl font-bold text-white mb-2">Pizzas</h2>
                            <p class="text-gray-300">Nos spécialités italiennes</p>
                        </div>
                        <div class="p-8 space-y-6">
                            <div class="menu-item-pro p-6">
                                <div class="flex justify-between items-start mb-3">
                                    <h3 class="text-xl font-bold text-gray-900">Pizza Margherita</h3>
                                    <span class="price-professional">11,50€</span>
                                </div>
                                <p class="text-gray-600 mb-3">Sauce tomate, mozzarella di bufala, basilic frais, huile d'olive</p>
                                <div class="flex flex-wrap gap-2">
                                    <span class="px-3 py-1 bg-green-100 text-green-800 rounded-full text-sm">Végétarien</span>
                                </div>
                            </div>

                            <div class="menu-item-pro p-6">
                                <div class="flex justify-between items-start mb-3">
                                    <h3 class="text-xl font-bold text-gray-900">Pizza Regina</h3>
                                    <span class="price-professional">14,00€</span>
                                </div>
                                <p class="text-gray-600 mb-3">Sauce tomate, mozzarella, jambon, champignons, olives noires</p>
                                <div class="flex flex-wrap gap-2">
                                    <span class="px-3 py-1 bg-blue-100 text-blue-800 rounded-full text-sm">Populaire</span>
                                </div>
                            </div>

                            <div class="menu-item-pro p-6">
                                <div class="flex justify-between items-start mb-3">
                                    <h3 class="text-xl font-bold text-gray-900">Pizza 4 Fromages</h3>
                                    <span class="price-professional">15,50€</span>
                                </div>
                                <p class="text-gray-600 mb-3">Mozzarella, gorgonzola, parmesan, chèvre, crème fraîche</p>
                                <div class="flex flex-wrap gap-2">
                                    <span class="px-3 py-1 bg-green-100 text-green-800 rounded-full text-sm">Végétarien</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Grillades -->
                    <div class="card-professional overflow-hidden">
                        <div class="image-overlay mb-0 h-48 bg-gray-200 overflow-hidden">
                            <img src="https://images.unsplash.com/photo-1544025162-d76694265947?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" 
                                 alt="Grillades" class="w-full h-full object-cover object-center">
                        </div>
                        <div class="bg-gray-900 p-8 text-center">
                            <div class="w-20 h-20 bg-white/10 rounded-full flex items-center justify-center mx-auto mb-4">
                                <span class="text-4xl">🍖</span>
                            </div>
                            <h2 class="text-3xl font-bold text-white mb-2">Grillades</h2>
                            <p class="text-gray-300">Viandes grillées</p>
                        </div>
                        <div class="p-8 space-y-6">
                            <div class="menu-item-pro p-6">
                                <div class="flex justify-between items-start mb-3">
                                    <h3 class="text-xl font-bold text-gray-900">Brochettes Mixtes</h3>
                                    <span class="price-professional">16,50€</span>
                                </div>
                                <p class="text-gray-600 mb-3">Agneau et bœuf, légumes grillés, riz parfumé, sauce tzatziki</p>
                            </div>

                            <div class="menu-item-pro p-6">
                                <div class="flex justify-between items-start mb-3">
                                    <h3 class="text-xl font-bold text-gray-900">Côte d'Agneau</h3>
                                    <span class="price-professional">19,50€</span>
                                </div>
                                <p class="text-gray-600 mb-3">Côtes d'agneau, purée de patates douces, ratatouille</p>
                            </div>
                        </div>
                    </div>

                    <!-- Accompagnements -->
                    <div class="card-professional overflow-hidden">
                        <div class="image-overlay mb-0 h-48 bg-gray-200 overflow-hidden">
                            <img src="https://images.unsplash.com/photo-1541592106381-b31e9677c0e5?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" 
                                 alt="Accompagnements" class="w-full h-full object-cover object-center">
                        </div>
                        <div class="bg-gray-900 p-8 text-center">
                            <div class="w-20 h-20 bg-white/10 rounded-full flex items-center justify-center mx-auto mb-4">
                                <span class="text-4xl">🍟</span>
                            </div>
                            <h2 class="text-3xl font-bold text-white mb-2">Accompagnements</h2>
                            <p class="text-gray-300">Pour compléter</p>
                        </div>
                        <div class="p-8 space-y-6">
                            <div class="menu-item-pro p-6">
                                <div class="flex justify-between items-start mb-3">
                                    <h3 class="text-xl font-bold text-gray-900">Frites Maison</h3>
                                    <span class="price-professional">4,50€</span>
                                </div>
                                <p class="text-gray-600">Pommes de terre fraîches</p>
                            </div>

                            <div class="menu-item-pro p-6">
                                <div class="flex justify-between items-start mb-3">
                                    <h3 class="text-xl font-bold text-gray-900">Salade Orientale</h3>
                                    <span class="price-professional">6,00€</span>
                                </div>
                                <p class="text-gray-600">Crudités, olives, feta</p>
                            </div>

                            <div class="menu-item-pro p-6">
                                <div class="flex justify-between items-start mb-3">
                                    <h3 class="text-xl font-bold text-gray-900">Boissons</h3>
                                    <span class="price-professional">2,50€</span>
                                </div>
                                <p class="text-gray-600">Sodas, jus, thé à la menthe</p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="text-center mt-16">
                    <button onclick="showPage('contact')" class="btn-primary px-8 py-4 rounded-lg font-semibold text-lg">
                        Commander Maintenant
                    </button>
                </div>
            </div>
        </section>
    </div>

    <!-- Page À Propos -->
    <div id="about" class="page">
        <section class="pt-32 pb-20 bg-white">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h1 class="section-title text-5xl md:text-6xl font-bold text-gray-900 mb-6">Notre Histoire</h1>
                    <p class="text-xl text-gray-600 max-w-3xl mx-auto">
                        Liam Food, une passion familiale depuis 2014
                    </p>
                </div>

                <div class="grid md:grid-cols-2 gap-16 items-center mb-20">
                    <div>
                        <h2 class="text-4xl font-bold text-gray-900 mb-6">Une Tradition Familiale</h2>
                        <p class="text-lg text-gray-600 mb-6 leading-relaxed">
                            Depuis 2014, Liam Food perpétue l'art de la cuisine méditerranéenne authentique. 
                            Notre restaurant familial a su préserver les recettes traditionnelles tout en 
                            s'adaptant aux goûts contemporains.
                        </p>
                        <p class="text-lg text-gray-600 mb-8 leading-relaxed">
                            Chaque plat est préparé avec soin et respect des traditions, utilisant uniquement 
                            des ingrédients frais et de qualité sélectionnés quotidiennement.
                        </p>
                        <div class="grid grid-cols-2 gap-8">
                            <div class="text-center">
                                <div class="text-4xl font-bold accent-gold mb-2">10+</div>
                                <div class="text-gray-600">Années d'Excellence</div>
                            </div>
                            <div class="text-center">
                                <div class="text-4xl font-bold accent-gold mb-2">5000+</div>
                                <div class="text-gray-600">Clients Satisfaits</div>
                            </div>
                        </div>
                    </div>
                    <div class="image-overlay h-96 bg-gray-200 rounded-lg overflow-hidden">
                        <img src="https://images.unsplash.com/photo-1556909114-f6e7ad7d3136?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" 
                             alt="Restaurant" class="w-full h-full object-cover">
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- Page Contact -->
    <div id="contact" class="page">
        <section class="pt-32 pb-20 bg-gray-50">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-16">
                    <h1 class="section-title text-5xl md:text-6xl font-bold text-gray-900 mb-6">Contactez-Nous</h1>
                    <p class="text-xl text-gray-600 max-w-3xl mx-auto">
                        Commandez maintenant ou venez nous rendre visite
                    </p>
                </div>

                <div class="grid md:grid-cols-2 gap-16">
                    <div>
                        <h2 class="text-3xl font-bold text-gray-900 mb-8">Informations</h2>
                        
                        <div class="space-y-8">
                            <div class="flex items-start space-x-4">
                                <div class="w-12 h-12 bg-gray-900 rounded-lg flex items-center justify-center flex-shrink-0">
                                    <span class="text-white text-xl">📍</span>
                                </div>
                                <div>
                                    <h3 class="text-xl font-bold text-gray-900 mb-2">Adresse</h3>
                                    <p class="text-gray-600">Zone Commerciale de Poulfanc<br>56860 Séné, France</p>
                                </div>
                            </div>

                            <div class="flex items-start space-x-4">
                                <div class="w-12 h-12 bg-gray-900 rounded-lg flex items-center justify-center flex-shrink-0">
                                    <span class="text-white text-xl">📞</span>
                                </div>
                                <div>
                                    <h3 class="text-xl font-bold text-gray-900 mb-2">Téléphone</h3>
                                    <p class="text-gray-600">01 42 85 96 73<br>06 12 34 56 78</p>
                                </div>
                            </div>

                            <div class="flex items-start space-x-4">
                                <div class="w-12 h-12 bg-gray-900 rounded-lg flex items-center justify-center flex-shrink-0">
                                    <span class="text-white text-xl">🕒</span>
                                </div>
                                <div>
                                    <h3 class="text-xl font-bold text-gray-900 mb-2">Horaires</h3>
                                    <div class="text-gray-600 space-y-1">
                                        <p><strong>Lun-Jeu:</strong> 11h30-14h30, 18h00-23h30</p>
                                        <p><strong>Ven-Sam:</strong> 11h30-23h30</p>
                                        <p><strong>Dimanche:</strong> 12h00-23h00</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="card-professional p-8">
                        <h2 class="text-3xl font-bold text-gray-900 mb-8">Commander</h2>
                        <div class="space-y-6">
                            <button onclick="showPage('menu')" class="w-full btn-primary py-4 rounded-lg font-semibold text-lg">
                                Voir le Menu Complet
                            </button>
                            
                            <div class="grid grid-cols-2 gap-4">
                                <button class="bg-green-600 hover:bg-green-700 text-white py-3 rounded-lg font-semibold transition-colors">
                                    Appeler
                                </button>
                                <button class="bg-blue-600 hover:bg-blue-700 text-white py-3 rounded-lg font-semibold transition-colors">
                                    WhatsApp
                                </button>
                            </div>

                            <div class="bg-accent-gold p-6 rounded-lg text-center text-white">
                                <h3 class="text-xl font-bold mb-2">🚚 Livraison Gratuite</h3>
                                <p class="text-white/90">Dès 25€ d'achat • Livraison en 30min</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- Footer -->
    <footer class="bg-gray-900 text-white py-16">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center">
                <div class="flex items-center justify-center space-x-4 mb-6">
                    <div class="w-12 h-12 bg-white rounded-lg flex items-center justify-center">
                        <span class="text-gray-900 text-xl font-bold">LF</span>
                    </div>
                    <div>
                        <h3 class="text-2xl font-bold text-white">Liam Food</h3>
                        <p class="text-sm text-gray-400">Restaurant • Pizza • Burger • Frites</p>
                    </div>
                </div>
                <p class="text-lg text-gray-400 mb-8 max-w-2xl mx-auto">
                    Votre restaurant de confiance pour des saveurs authentiques et des moments délicieux.
                </p>
                <div class="flex justify-center space-x-8 mb-8">
                    <button onclick="showPage('home')" class="text-gray-400 hover:text-white transition-colors">Accueil</button>
                    <button onclick="showPage('menu')" class="text-gray-400 hover:text-white transition-colors">Menu</button>
                    <button onclick="showPage('about')" class="text-gray-400 hover:text-white transition-colors">À propos</button>
                    <button onclick="showPage('contact')" class="text-gray-400 hover:text-white transition-colors">Contact</button>
                </div>
                <div class="border-t border-gray-800 pt-8">
                    <p class="text-gray-400">&copy; 2024 Liam Food. Tous droits réservés.</p>
                </div>
            </div>
        </div>
    </footer>

    <script>
        // Navigation entre les pages
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });
            
            document.getElementById(pageId).classList.add('active');
            window.scrollTo({ top: 0, behavior: 'smooth' });
            
            // Messages professionnels
            const messages = {
                'menu': 'Découvrez notre sélection de plats',
                'about': 'Apprenez-en plus sur notre histoire',
                'contact': 'Contactez-nous pour commander',
                'home': 'Bienvenue chez Liam Food'
            };
            
            if (messages[pageId]) {
                showNotification(messages[pageId]);
            }
        }

        // Système de notifications discret
        function showNotification(message) {
            const notification = document.createElement('div');
            notification.className = 'fixed top-24 right-4 bg-gray-900 text-white px-6 py-3 rounded-lg shadow-lg z-50 transform translate-x-full transition-all duration-300 max-w-sm';
            notification.innerHTML = `
                <div class="flex items-center justify-between">
                    <span class="text-sm font-medium">${message}</span>
                    <button onclick="this.parentElement.parentElement.remove()" class="ml-4 text-gray-400 hover:text-white">✕</button>
                </div>
            `;
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.style.transform = 'translateX(0)';
            }, 100);
            
            setTimeout(() => {
                if (notification.parentElement) {
                    notification.style.transform = 'translateX(100%)';
                    setTimeout(() => {
                        if (notification.parentElement) {
                            notification.remove();
                        }
                    }, 300);
                }
            }, 3000);
        }

        // Effets au survol des éléments du menu
        document.addEventListener('click', function(e) {
            if (e.target.closest('.menu-item-pro')) {
                const item = e.target.closest('.menu-item-pro');
                const dishName = item.querySelector('h3').textContent;
                
                item.style.borderColor = '#d97706';
                setTimeout(() => {
                    item.style.borderColor = '#e2e8f0';
                }, 1000);
                
                showNotification(`${dishName} sélectionné`);
            }
        });

        // Effet de navigation
        window.addEventListener('scroll', function() {
            const nav = document.querySelector('nav');
            if (window.scrollY > 50) {
                nav.style.background = 'rgba(255, 255, 255, 0.98)';
            } else {
                nav.style.background = 'rgba(255, 255, 255, 0.95)';
            }
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'95cfeefdc44588f4',t:'MTc1MjE0OTE3MS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>t
