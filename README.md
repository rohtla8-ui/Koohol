<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>$VIKING | Crypto Presale - Viking Strength Meets DeFi</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;800&family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --viking-gold: #D4AF37;
            --viking-dark: #0f172a;
            --viking-blue: #1e3a5f;
            --viking-accent: #059669;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background: #0a0f1c;
            color: #fff;
            overflow-x: hidden;
        }
        
        .font-viking {
            font-family: 'Cinzel', serif;
        }
        
        /* Animated Background */
        .bg-mesh {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: 
                radial-gradient(circle at 20% 50%, rgba(30, 58, 95, 0.4) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, rgba(212, 175, 55, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 40% 20%, rgba(5, 150, 105, 0.1) 0%, transparent 50%);
            animation: meshMove 20s ease-in-out infinite;
        }
        
        @keyframes meshMove {
            0%, 100% { transform: translate(0, 0) scale(1); }
            33% { transform: translate(30px, -30px) scale(1.1); }
            66% { transform: translate(-20px, 20px) scale(0.9); }
        }
        
        /* Noise Texture */
        .noise {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
            opacity: 0.03;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E");
        }
        
        /* Viking Helmet Animation */
        .helmet-float {
            animation: float 6s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(2deg); }
        }
        
        /* Glow Effects */
        .glow-gold {
            box-shadow: 0 0 30px rgba(212, 175, 55, 0.3);
        }
        
        .text-glow {
            text-shadow: 0 0 20px rgba(212, 175, 55, 0.5);
        }
        
        /* Progress Bar Animation */
        .progress-fill {
            background: linear-gradient(90deg, #059669, #D4AF37);
            background-size: 200% 100%;
            animation: shimmer 2s infinite;
        }
        
        @keyframes shimmer {
            0% { background-position: 200% 0; }
            100% { background-position: -200% 0; }
        }
        
        /* Card Hover Effects */
        .feature-card {
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .feature-card:hover {
            transform: translateY(-10px);
            border-color: rgba(212, 175, 55, 0.5);
            box-shadow: 0 20px 40px rgba(212, 175, 55, 0.1);
        }
        
        /* Chart Animations */
        .chart-line {
            stroke-dasharray: 1000;
            stroke-dashoffset: 1000;
            animation: drawLine 2s ease-out forwards;
        }
        
        @keyframes drawLine {
            to { stroke-dashoffset: 0; }
        }
        
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        
        ::-webkit-scrollbar-track {
            background: #0f172a;
        }
        
        ::-webkit-scrollbar-thumb {
            background: #D4AF37;
            border-radius: 4px;
        }
        
        /* Button Styles */
        .btn-primary {
            background: linear-gradient(135deg, #059669 0%, #047857 100%);
            position: relative;
            overflow: hidden;
        }
        
        .btn-primary::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: 0.5s;
        }
        
        .btn-primary:hover::before {
            left: 100%;
        }
        
        .btn-gold {
            background: linear-gradient(135deg, #D4AF37 0%, #B8941F 100%);
            color: #0f172a;
        }
        
        /* Glass Effect */
        .glass {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        /* Particle Canvas */
        #particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }
        
        /* Countdown */
        .countdown-box {
            background: rgba(212, 175, 55, 0.1);
            border: 1px solid rgba(212, 175, 55, 0.3);
        }
    </style>
</head>
<body class="antialiased">

    <!-- Background Effects -->
    <div class="bg-mesh"></div>
    <div class="noise"></div>
    <canvas id="particles"></canvas>

    <!-- Navigation -->
    <nav class="fixed w-full z-50 glass transition-all duration-300" id="navbar">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-20">
                <div class="flex items-center space-x-3">
                    <div class="w-10 h-10 bg-gradient-to-br from-yellow-500 to-yellow-700 rounded-full flex items-center justify-center helmet-float">
                        <svg class="w-6 h-6 text-slate-900" fill="currentColor" viewBox="0 0 24 24">
                            <path d="M12 2L2 7v10c0 5.55 3.84 10.74 9 12 5.16-1.26 9-6.45 9-12V7l-10-5z"/>
                        </svg>
                    </div>
                    <span class="font-viking text-2xl font-bold text-yellow-500 tracking-wider">$VIKING</span>
                </div>
                
                <div class="hidden md:flex items-center space-x-8">
                    <a href="#presale" class="text-gray-300 hover:text-yellow-500 transition-colors">Presale</a>
                    <a href="#growth" class="text-gray-300 hover:text-yellow-500 transition-colors">Growth</a>
                    <a href="#protection" class="text-gray-300 hover:text-yellow-500 transition-colors">Protection</a>
                    <a href="#strategy" class="text-gray-300 hover:text-yellow-500 transition-colors">Strategy</a>
                    <button class="btn-gold px-6 py-2 rounded-full font-bold hover:scale-105 transition-transform">
                        Connect Wallet
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="relative min-h-screen flex items-center justify-center pt-20 overflow-hidden">
        <div class="absolute inset-0 z-0">
            <div class="absolute top-20 left-10 w-72 h-72 bg-blue-500 rounded-full mix-blend-multiply filter blur-3xl opacity-20 animate-pulse"></div>
            <div class="absolute bottom-20 right-10 w-96 h-96 bg-yellow-500 rounded-full mix-blend-multiply filter blur-3xl opacity-20 animate-pulse" style="animation-delay: 2s;"></div>
        </div>

        <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
            <div class="helmet-float mb-8 inline-block">
                <svg class="w-32 h-32 mx-auto text-yellow-500 drop-shadow-2xl" viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="2">
                    <path d="M50 10 C30 10 15 25 15 45 L15 60 L25 60 L25 50 C25 35 35 25 50 25 C65 25 75 35 75 50 L75 60 L85 60 L85 45 C85 25 70 10 50 10 Z" fill="url(#helmetGrad)"/>
                    <path d="M20 60 L20 75 Q20 85 35 85 L65 85 Q80 85 80 75 L80 60" stroke="currentColor" fill="rgba(212,175,55,0.3)"/>
                    <path d="M35 25 L25 5 M65 25 L75 5" stroke="currentColor" stroke-width="3"/>
                    <circle cx="35" cy="45" r="3" fill="currentColor"/>
                    <circle cx="65" cy="45" r="3" fill="currentColor"/>
                    <defs>
                        <linearGradient id="helmetGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                            <stop offset="0%" style="stop-color:#D4AF37;stop-opacity:1" />
                            <stop offset="100%" style="stop-color:#B8941F;stop-opacity:1" />
                        </linearGradient>
                    </defs>
                </svg>
            </div>

            <h1 class="font-viking text-5xl md:text-7xl font-bold mb-6 text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 via-yellow-200 to-yellow-400 text-glow">
                KOOHOL VIKING
            </h1>
            
            <p class="text-xl md:text-2xl text-gray-300 mb-4 max-w-3xl mx-auto">
                The Anti-Whale DeFi Revolution
            </p>
            <p class="text-gray-400 mb-12 max-w-2xl mx-auto">
                Fair presale mechanics with maximum buy limits, controlled sell pressure, and sustainable 12-month growth strategy.
            </p>

            <!-- Presale Progress Card -->
            <div class="glass rounded-2xl p-8 max-w-3xl mx-auto glow-gold mb-12" id="presale">
                <div class="flex justify-between items-center mb-6">
                    <div class="text-left">
                        <p class="text-sm text-gray-400 uppercase tracking-wider">Current Price</p>
                        <p class="text-3xl font-bold text-yellow-400">$0.012 USD</p>
                    </div>
                    <div class="text-right">
                        <p class="text-sm text-gray-400 uppercase tracking-wider">Launch Price</p>
                        <p class="text-3xl font-bold text-green-400">$0.050 USD</p>
                    </div>
                </div>

                <div class="relative h-4 bg-gray-700 rounded-full overflow-hidden mb-4">
                    <div class="progress-fill h-full w-0 rounded-full" id="progressBar" style="width: 67%"></div>
                </div>
                
                <div class="flex justify-between text-sm mb-6">
                    <span class="text-gray-400">Raised: <span class="text-white font-bold">$1,670,000</span></span>
                    <span class="text-gray-400">Goal: <span class="text-white font-bold">$2,500,000</span></span>
                </div>

                <div class="grid grid-cols-3 gap-4 mb-8">
                    <div class="countdown-box rounded-lg p-3">
                        <div class="text-2xl font-bold text-yellow-400" id="days">12</div>
                        <div class="text-xs text-gray-400">Days</div>
                    </div>
                    <div class="countdown-box rounded-lg p-3">
                        <div class="text-2xl font-bold text-yellow-400" id="hours">08</div>
                        <div class="text-xs text-gray-400">Hours</div>
                    </div>
                    <div class="countdown-box rounded-lg p-3">
                        <div class="text-2xl font-bold text-yellow-400" id="minutes">45</div>
                        <div class="text-xs text-gray-400">Minutes</div>
                    </div>
                </div>

                <div class="flex flex-col sm:flex-row gap-4">
                    <button class="btn-primary flex-1 py-4 rounded-xl font-bold text-lg hover:scale-105 transition-transform">
                        Buy $VIKING Now
                    </button>
                    <button class="glass flex-1 py-4 rounded-xl font-bold text-lg hover:bg-white/10 transition-colors border border-yellow-500/30">
                        View Whitepaper
                    </button>
                </div>
            </div>

            <!-- Stats Row -->
            <div class="grid grid-cols-2 md:grid-cols-4 gap-6 max-w-4xl mx-auto">
                <div class="glass rounded-xl p-4">
                    <div class="text-2xl font-bold text-green-400">316%</div>
                    <div class="text-sm text-gray-400">Growth Potential</div>
                </div>
                <div class="glass rounded-xl p-4">
                    <div class="text-2xl font-bold text-yellow-400">250K</div>
                    <div class="text-sm text-gray-400">Max Buy Limit</div>
                </div>
                <div class="glass rounded-xl p-4">
                    <div class="text-2xl font-bold text-blue-400">62.5K</div>
                    <div class="text-sm text-gray-400">Max Sell Limit</div>
                </div>
                <div class="glass rounded-xl p-4">
                    <div class="text-2xl font-bold text-purple-400">12 Mo</div>
                    <div class="text-sm text-gray-400">Vesting Period</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Token Growth Section -->
    <section class="py-24 relative" id="growth">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <h2 class="font-viking text-4xl md:text-5xl font-bold mb-4 text-yellow-500">Token Price & Market Cap Growth</h2>
                <p class="text-gray-400 max-w-2xl mx-auto">Sustainable 12-month growth trajectory with stable appreciation and reinvestment mechanisms</p>
            </div>

            <div class="grid lg:grid-cols-2 gap-12 items-center">
                <div class="glass rounded-2xl p-8 relative overflow-hidden">
                    <div class="absolute top-0 right-0 w-32 h-32 bg-green-500/20 rounded-full filter blur-3xl"></div>
                    
                    <h3 class="text-2xl font-bold mb-6 flex items-center gap-2">
                        <span class="w-3 h-3 bg-green-500 rounded-full"></span>
                        12-Month Projection
                    </h3>
                    
                    <div class="space-y-6">
                        <div class="flex justify-between items-center p-4 bg-white/5 rounded-lg">
                            <span class="text-gray-400">Starting Price</span>
                            <span class="text-2xl font-bold text-white">$0.012</span>
                        </div>
                        <div class="flex justify-between items-center p-4 bg-white/5 rounded-lg">
                            <span class="text-gray-400">Month 6 Target</span>
                            <span class="text-2xl font-bold text-green-400">$0.025</span>
                        </div>
                        <div class="flex justify-between items-center p-4 bg-gradient-to-r from-green-500/20 to-yellow-500/20 rounded-lg border border-green-500/30">
                            <span class="text-gray-300">Month 12 Target</span>
                            <span class="text-3xl font-bold text-yellow-400">$0.050</span>
                        </div>
                        
                        <div class="mt-6 pt-6 border-t border-gray-700">
                            <div class="flex justify-between text-sm mb-2">
                                <span class="text-gray-400">Market Cap Growth</span>
                                <span class="text-green-400 font-bold">$600K → $2.5M</span>
                            </div>
                            <div class="w-full bg-gray-700 rounded-full h-2">
                                <div class="bg-gradient-to-r from-green-500 to-yellow-500 h-2 rounded-full" style="width: 100%"></div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="relative">
                    <canvas id="growthChart" class="w-full h-96"></canvas>
                    <div class="absolute -bottom-4 left-0 right-0 flex justify-center gap-4 text-sm">
                        <div class="flex items-center gap-2">
                            <div class="w-3 h-3 bg-green-500 rounded-full"></div>
                            <span class="text-gray-400">Token Price</span>
                        </div>
                        <div class="flex items-center gap-2">
                            <div class="w-3 h-3 bg-blue-500 rounded-full"></div>
                            <span class="text-gray-400">Market Cap</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Anti-Whale Protection -->
    <section class="py-24 bg-gradient-to-b from-slate-900 to-slate-800 relative overflow-hidden" id="protection">
        <div class="absolute inset-0 bg-[url('data:image/svg+xml,%3Csvg width=\'60\' height=\'60\' viewBox=\'0 0 60 60\' xmlns=\'http://www.w3.org/2000/svg\'%3E%3Cg fill=\'none\' fill-rule=\'evenodd\'%3E%3Cg fill=\'%23ffffff\' fill-opacity=\'0.03\'%3E%3Cpath d=\'M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z\'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E')] opacity-20"></div>
        
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <div class="text-center mb-16">
                <h2 class="font-viking text-4xl md:text-5xl font-bold mb-4 text-red-400">Anti-Whale Protection</h2>
                <p class="text-gray-400 max-w-2xl mx-auto">Fair distribution mechanics preventing market manipulation and ensuring sustainable growth</p>
            </div>

            <div class="grid md:grid-cols-2 gap-8 mb-12">
                <div class="feature-card glass rounded-2xl p-8 bg-gradient-to-br from-green-900/20 to-transparent">
                    <div class="flex items-center justify-between mb-6">
                        <h3 class="text-2xl font-bold text-green-400">Maximum Buy Limit</h3>
                        <div class="w-12 h-12 bg-green-500/20 rounded-full flex items-center justify-center">
                            <svg class="w-6 h-6 text-green-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6"/>
                            </svg>
                        </div>
                    </div>
                    <div class="text-5xl font-bold text-white mb-2">250,000</div>
                    <p class="text-gray-400">Tokens per wallet during presale</p>
                    <div class="mt-4 text-sm text-green-400 bg-green-500/10 inline-block px-3 py-1 rounded-full">
                        Prevents Concentration
                    </div>
                </div>

                <div class="feature-card glass rounded-2xl p-8 bg-gradient-to-br from-red-900/20 to-transparent">
                    <div class="flex items-center justify-between mb-6">
                        <h3 class="text-2xl font-bold text-red-400">Maximum Sell at Launch</h3>
                        <div class="w-12 h-12 bg-red-500/20 rounded-full flex items-center justify-center">
                            <svg class="w-6 h-6 text-red-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20 12H4"/>
                            </svg>
                        </div>
                    </div>
                    <div class="text-5xl font-bold text-white mb-2">62,500</div>
                    <p class="text-gray-400">Tokens per investor at launch</p>
                    <div class="mt-4 text-sm text-red-400 bg-red-500/10 inline-block px-3 py-1 rounded-full">
                        Prevents Dumping
                    </div>
                </div>
            </div>

            <!-- Comparison Visualization -->
            <div class="glass rounded-2xl p-8">
                <h3 class="text-xl font-bold mb-8 text-center">Whale Dump vs. Controlled Sell Pressure</h3>
                <div class="relative h-64 flex items-end justify-around gap-4">
                    <div class="flex flex-col items-center gap-4 w-1/3">
                        <div class="w-full bg-red-500/80 rounded-t-lg relative group transition-all duration-500 hover:bg-red-500" style="height: 90%">
                            <div class="absolute -top-12 left-1/2 transform -translate-x-1/2 bg-red-500 text-white px-3 py-1 rounded text-sm font-bold opacity-0 group-hover:opacity-100 transition-opacity">
                                1,000,000+ Tokens
                            </div>
                        </div>
                        <span class="text-red-400 font-bold text-center">Traditional Whale Dump<br><span class="text-sm text-gray-400 font-normal">Market Crash Risk</span></span>
                    </div>
                    
                    <div class="flex items-center justify-center">
                        <div class="text-4xl text-gray-600 font-bold">VS</div>
                    </div>

                    <div class="flex flex-col items-center gap-4 w-1/3">
                        <div class="w-full bg-green-500/80 rounded-t-lg relative group transition-all duration-500 hover:bg-green-500" style="height: 15%">
                            <div class="absolute -top-12 left-1/2 transform -translate-x-1/2 bg-green-500 text-white px-3 py-1 rounded text-sm font-bold opacity-0 group-hover:opacity-100 transition-opacity">
                                62,500 Tokens
                            </div>
                        </div>
                        <span class="text-green-400 font-bold text-center">$VIKING Protection<br><span class="text-sm text-gray-400 font-normal">Stable Growth</span></span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Reinvestment Strategy -->
    <section class="py-24 relative" id="strategy">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <h2 class="font-viking text-4xl md:text-5xl font-bold mb-4 text-blue-400">Reinvesting Strategy</h2>
                <p class="text-gray-400 max-w-2xl mx-auto">Consistent monthly DCA with automated liquidity provision for sustainable ecosystem growth</p>
            </div>

            <div class="grid lg:grid-cols-3 gap-8 mb-16">
                <div class="feature-card glass rounded-2xl p-6 text-center">
                    <div class="w-16 h-16 bg-blue-500/20 rounded-full flex items-center justify-center mx-auto mb-4">
                        <svg class="w-8 h-8 text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path strokeColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/>
                        </svg>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Monthly DCA</h3>
                    <p class="text-gray-400 text-sm">Consistent $1,000 monthly additions to liquidity pools</p>
                </div>

                <div class="feature-card glass rounded-2xl p-6 text-center">
                    <div class="w-16 h-16 bg-purple-500/20 rounded-full flex items-center justify-center mx-auto mb-4">
                        <svg class="w-8 h-8 text-purple-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6"/>
                        </svg>
                    </div>
                    <h3 class="text-xl font-bold mb-2">LP Reinvestment</h3>
                    <p class="text-gray-400 text-sm">Automated yield farming with compound returns</p>
                </div>

                <div class="feature-card glass rounded-2xl p-6 text-center">
                    <div class="w-16 h-16 bg-yellow-500/20 rounded-full flex items-center justify-center mx-auto mb-4">
                        <svg class="w-8 h-8 text-yellow-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/>
                        </svg>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Volatility Suppression</h3>
                    <p class="text-gray-400 text-sm">Deep liquidity buffers against market dips</p>
                </div>
            </div>

            <!-- ROI Projection -->
            <div class="glass rounded-2xl p-8 bg-gradient-to-br from-slate-800 to-slate-900">
                <div class="flex flex-col md:flex-row justify-between items-center mb-8">
                    <div>
                        <h3 class="text-2xl font-bold text-white mb-2">Investor ROI Over 12 Months</h3>
                        <p class="text-green-400 text-lg">Profit Potential: <span class="font-bold text-2xl">+330%</span></p>
                    </div>
                    <div class="mt-4 md:mt-0 text-right">
                        <div class="text-sm text-gray-400">Price Trajectory</div>
                        <div class="text-2xl font-bold text-yellow-400">$0.01 → $0.06 USD</div>
                    </div>
                </div>

                <div class="relative h-80 w-full" id="roiChart">
                    <canvas id="roiCanvas" class="w-full h-full"></canvas>
                </div>

                <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mt-8">
                    <div class="text-center p-4 bg-white/5 rounded-lg">
                        <div class="text-green-400 font-bold text-xl">+20%</div>
                        <div class="text-xs text-gray-400">Month 1</div>
                    </div>
                    <div class="text-center p-4 bg-white/5 rounded-lg">
                        <div class="text-green-400 font-bold text-xl">+83%</div>
                        <div class="text-xs text-gray-400">Month 3</div>
                    </div>
                    <div class="text-center p-4 bg-white/5 rounded-lg">
                        <div class="text-green-400 font-bold text-xl">+200%</div>
                        <div class="text-xs text-gray-400">Month 6</div>
                    </div>
                    <div class="text-center p-4 bg-gradient-to-r from-green-500/20 to-yellow-500/20 rounded-lg border border-green-500/30">
                        <div class="text-yellow-400 font-bold text-xl">+333%</div>
                        <div class="text-xs text-gray-400">Month 12</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Tokenomics -->
    <section class="py-24 bg-gradient-to-b from-slate-800 to-slate-900">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="font-viking text-4xl md:text-5xl font-bold text-center mb-16 text-yellow-500">Tokenomics</h2>
            
            <div class="grid md:grid-cols-2 gap-12 items-center">
                <div class="relative">
                    <canvas id="tokenomicsChart" class="w-full max-w-md mx-auto"></canvas>
                    <div class="absolute inset-0 flex items-center justify-center pointer-events-none">
                        <div class="text-center">
                            <div class="text-3xl font-bold text-white">1B</div>
                            <div class="text-sm text-gray-400">Total Supply</div>
                        </div>
                    </div>
                </div>

                <div class="space-y-4">
                    <div class="flex items-center justify-between p-4 bg-blue-500/10 rounded-lg border-l-4 border-blue-500">
                        <span class="text-gray-300">Presale</span>
                        <span class="text-xl font-bold text-blue-400">40%</span>
                    </div>
                    <div class="flex items-center justify-between p-4 bg-green-500/10 rounded-lg border-l-4 border-green-500">
                        <span class="text-gray-300">Liquidity Pool</span>
                        <span class="text-xl font-bold text-green-400">30%</span>
                    </div>
                    <div class="flex items-center justify-between p-4 bg-purple-500/10 rounded-lg border-l-4 border-purple-500">
                        <span class="text-gray-300">Development</span>
                        <span class="text-xl font-bold text-purple-400">15%</span>
                    </div>
                    <div class="flex items-center justify-between p-4 bg-yellow-500/10 rounded-lg border-l-4 border-yellow-500">
                        <span class="text-gray-300">Marketing</span>
                        <span class="text-xl font-bold text-yellow-400">10%</span>
                    </div>
                    <div class="flex items-center justify-between p-4 bg-red-500/10 rounded-lg border-l-4 border-red-500">
                        <span class="text-gray-300">Team (Vested)</span>
                        <span class="text-xl font-bold text-red-400">5%</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- CTA Section -->
    <section class="py-24 relative overflow-hidden">
        <div class="absolute inset-0 bg-gradient-to-r from-green-600/20 to-yellow-600/20"></div>
        <div class="max-w-4xl mx-auto px-4 text-center relative z-10">
            <h2 class="font-viking text-4xl md:text-6xl font-bold mb-6 text-white">Join the Viking Raid</h2>
            <p class="text-xl text-gray-300 mb-8">Secure your $VIKING tokens before the presale ends. Fair launch, anti-whale protection, sustainable growth.</p>
            
            <div class="flex flex-col sm:flex-row gap-4 justify-center">
                <button class="btn-gold px-8 py-4 rounded-full font-bold text-lg hover:scale-105 transition-transform shadow-2xl shadow-yellow-500/20">
                    Buy $VIKING - $0.012
                </button>
                <button class="glass px-8 py-4 rounded-full font-bold text-lg hover:bg-white/10 transition-colors border border-white/20">
                    Join Community
                </button>
            </div>

            <div class="mt-12 flex justify-center gap-6">
                <a href="#" class="w-12 h-12 glass rounded-full flex items-center justify-center hover:bg-blue-500/20 transition-colors">
                    <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24"><path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/></svg>
                </a>
                <a href="#" class="w-12 h-12 glass rounded-full flex items-center justify-center hover:bg-indigo-500/20 transition-colors">
                    <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/></svg>
                </a>
                <a href="#" class="w-12 h-12 glass rounded-full flex items-center justify-center hover:bg-blue-400/20 transition-colors">
                    <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24"><path d="M20.317 4.37a19.791 19.791 0 00-4.885-1.515.074.074 0 00-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 00-5.487 0 12.64 12.64 0 00-.617-1.25.077.077 0 00-.079-.037A19.736 19.736 0 003.677 4.37a.07.07 0 00-.032.027C.533 9.046-.32 13.58.099 18.057a.082.082 0 00.031.057 19.9 19.9 0 005.993 3.03.078.078 0 00.084-.028 14.09 14.09 0 001.226-1.994.076.076 0 00-.041-.106 13.107 13.107 0 01-1.872-.892.077.077 0 01-.008-.128 10.2 10.2 0 00.372-.292.074.074 0 01.077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 01.078.01c.12.098.246.198.373.292a.077.077 0 01-.006.127 12.299 12.299 0 01-1.873.892.077.077 0 00-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 00.084.028 19.839 19.839 0 006.002-3.03.077.077 0 00.032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 00-.031-.03zM8.02 15.33c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.956 2.418-2.157 2.418zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.955-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.946 2.418-2.157 2.418z"/></svg>
                </a>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="border-t border-gray-800 py-12 bg-slate-900">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid md:grid-cols-4 gap-8 mb-8">
                <div>
                    <div class="flex items-center gap-2 mb-4">
                        <div class="w-8 h-8 bg-yellow-500 rounded-full flex items-center justify-center">
                            <svg class="w-5 h-5 text-slate-900" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M12 2L2 7v10c0 5.55 3.84 10.74 9 12 5.16-1.26 9-6.45 9-12V7l-10-5z"/>
                            </svg>
                        </div>
                        <span class="font-viking text-xl font-bold text-yellow-500">$VIKING</span>
                    </div>
                    <p class="text-gray-400 text-sm">Fair launch DeFi token with anti-whale protection and sustainable growth mechanics.</p>
                </div>
                <div>
                    <h4 class="font-bold text-white mb-4">Quick Links</h4>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li><a href="#" class="hover:text-yellow-500 transition-colors">Whitepaper</a></li>
                        <li><a href="#" class="hover:text-yellow-500 transition-colors">Audit Report</a></li>
                        <li><a href="#" class="hover:text-yellow-500 transition-colors">Token Contract</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="font-bold text-white mb-4">Community</h4>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li><a href="#" class="hover:text-yellow-500 transition-colors">Telegram</a></li>
                        <li><a href="#" class="hover:text-yellow-500 transition-colors">Discord</a></li>
                        <li><a href="#" class="hover:text-yellow-500 transition-colors">Twitter/X</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="font-bold text-white mb-4">Legal</h4>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li><a href="#" class="hover:text-yellow-500 transition-colors">Terms of Service</a></li>
                        <li><a href="#" class="hover:text-yellow-500 transition-colors">Privacy Policy</a></li>
                        <li><a href="#" class="hover:text-yellow-500 transition-colors">Risk Disclaimer</a></li>
                    </ul>
                </div>
            </div>
            <div class="border-t border-gray-800 pt-8 text-center text-sm text-gray-500">
                <p>&copy; 2026 $VIKING Token. All rights reserved. Cryptocurrency may be unregulated in your jurisdiction.</p>
            </div>
        </div>
    </footer>

    <script>
        // Initialize GSAP
        gsap.registerPlugin(ScrollTrigger);

        // Particle System
        const canvas = document.getElementById('particles');
        const ctx = canvas.getContext('2d');
        let particles = [];
        
        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        resizeCanvas();
        window.addEventListener('resize', resizeCanvas);

        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 2;
                this.speedX = Math.random() * 0.5 - 0.25;
                this.speedY = Math.random() * 0.5 - 0.25;
                this.opacity = Math.random() * 0.5;
            }
            
            update() {
                this.x += this.speedX;
                this.y += this.speedY;
                
                if (this.x > canvas.width) this.x = 0;
                if (this.x < 0) this.x = canvas.width;
                if (this.y > canvas.height) this.y = 0;
                if (this.y < 0) this.y = canvas.height;
            }
            
            draw() {
                ctx.fillStyle = `rgba(212, 175, 55, ${this.opacity})`;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        for (let i = 0; i < 50; i++) {
            particles.push(new Particle());
        }

        function animateParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => {
                p.update();
                p.draw();
            });
            requestAnimationFrame(animateParticles);
        }
        animateParticles();

        // Growth Chart (Line Chart)
        const growthCanvas = document.getElementById('growthChart');
        const gCtx = growthCanvas.getContext('2d');
        
        function drawGrowthChart() {
            const width = growthCanvas.width = growthCanvas.offsetWidth;
            const height = growthCanvas.height = growthCanvas.offsetHeight;
            
            const data = [0.012, 0.015, 0.018, 0.022, 0.028, 0.035, 0.042, 0.050];
            const labels = ['0', '2', '4', '6', '8', '10', '12'];
            
            const padding = 40;
            const chartWidth = width - padding * 2;
            const chartHeight = height - padding * 2;
            
            // Clear
            gCtx.clearRect(0, 0, width, height);
            
            // Draw grid
            gCtx.strokeStyle = 'rgba(255,255,255,0.1)';
            gCtx.lineWidth = 1;
            for (let i = 0; i <= 5; i++) {
                const y = padding + (chartHeight / 5) * i;
                gCtx.beginPath();
                gCtx.moveTo(padding, y);
                gCtx.lineTo(width - padding, y);
                gCtx.stroke();
            }
            
            // Draw line
            gCtx.strokeStyle = '#10b981';
            gCtx.lineWidth = 3;
            gCtx.beginPath();
            
            data.forEach((val, i) => {
                const x = padding + (chartWidth / (data.length - 1)) * i;
                const y = padding + chartHeight - (val / 0.06) * chartHeight;
                
                if (i === 0) gCtx.moveTo(x, y);
                else gCtx.lineTo(x, y);
                
                // Draw point
                gCtx.fillStyle = '#10b981';
                gCtx.beginPath();
                gCtx.arc(x, y, 4, 0, Math.PI * 2);
                gCtx.fill();
            });
            gCtx.stroke();
            
            // Fill area
            gCtx.lineTo(padding + chartWidth, padding + chartHeight);
            gCtx.lineTo(padding, padding + chartHeight);
            gCtx.closePath();
            const gradient = gCtx.createLinearGradient(0, padding, 0, height - padding);
            gradient.addColorStop(0, 'rgba(16, 185, 129, 0.3)');
            gradient.addColorStop(1, 'rgba(16, 185, 129, 0)');
            gCtx.fillStyle = gradient;
            gCtx.fill();
            
            // Labels
            gCtx.fillStyle = '#9ca3af';
            gCtx.font = '12px Inter';
            gCtx.textAlign = 'center';
            labels.forEach((label, i) => {
                const x = padding + (chartWidth / (labels.length - 1)) * i;
                gCtx.fillText(label, x, height - 10);
            });
        }
        
        setTimeout(drawGrowthChart, 100);
        window.addEventListener('resize', drawGrowthChart);

        // ROI Chart
        const roiCanvas = document.getElementById('roiCanvas');
        const rCtx = roiCanvas.getContext('2d');
        
        function drawROIChart() {
            const width = roiCanvas.width = roiCanvas.offsetWidth;
            const height = roiCanvas.height = roiCanvas.offsetHeight;
            
            const data = [100, 120, 140, 183, 220, 250, 300, 280, 320, 350, 380, 430, 433];
            const padding = 40;
            const chartWidth = width - padding * 2;
            const chartHeight = height - padding * 2;
            
            rCtx.clearRect(0, 0, width, height);
            
            // Draw bars
            const barWidth = chartWidth / data.length * 0.6;
            const spacing = chartWidth / data.length;
            
            data.forEach((val, i) => {
                const x = padding + spacing * i + spacing * 0.2;
                const barHeight = (val / 500) * chartHeight;
                const y = padding + chartHeight - barHeight;
                
                // Gradient
                const gradient = rCtx.createLinearGradient(0, y, 0, padding + chartHeight);
                if (i === data.length - 1) {
                    gradient.addColorStop(0, '#fbbf24');
                    gradient.addColorStop(1, '#f59e0b');
                } else {
                    gradient.addColorStop(0, '#10b981');
                    gradient.addColorStop(1, '#059669');
                }
                
                rCtx.fillStyle = gradient;
                rCtx.fillRect(x, y, barWidth, barHeight);
                
                // Value label on top
                if (i % 2 === 0 || i === data.length - 1) {
                    rCtx.fillStyle = i === data.length - 1 ? '#fbbf24' : '#10b981';
                    rCtx.font = 'bold 11px Inter';
                    rCtx.textAlign = 'center';
                    rCtx.fillText('+' + (val - 100) + '%', x + barWidth/2, y - 5);
                }
            });
            
            // Line overlay
            rCtx.strokeStyle = 'rgba(255,255,255,0.5)';
            rCtx.lineWidth = 2;
            rCtx.setLineDash([5, 5]);
            rCtx.beginPath();
            data.forEach((val, i) => {
                const x = padding + spacing * i + spacing * 0.2 + barWidth/2;
                const y = padding + chartHeight - (val / 500) * chartHeight;
                if (i === 0) rCtx.moveTo(x, y);
                else rCtx.lineTo(x, y);
            });
            rCtx.stroke();
            rCtx.setLineDash([]);
        }
        
        setTimeout(drawROIChart, 100);
        window.addEventListener('resize', drawROIChart);

        // Tokenomics Donut Chart
        const tokenCanvas = document.getElementById('tokenomicsChart');
        const tCtx = tokenCanvas.getContext('2d');
        
        function drawTokenomics() {
            const size = 300;
            tokenCanvas.width = size;
            tokenCanvas.height = size;
            
            const centerX = size / 2;
            const centerY = size / 2;
            const radius = size * 0.35;
            const thickness = size * 0.15;
            
            const data = [
                { value: 40, color: '#3b82f6', label: 'Presale' },
                { value: 30, color: '#10b981', label: 'Liquidity' },
                { value: 15, color: '#a855f7', label: 'Dev' },
                { value: 10, color: '#fbbf24', label: 'Marketing' },
                { value: 5, color: '#ef4444', label: 'Team' }
            ];
            
            let currentAngle = -Math.PI / 2;
            
            data.forEach(segment => {
                const sliceAngle = (segment.value / 100) * Math.PI * 2;
                
                // Draw segment
                tCtx.beginPath();
                tCtx.arc(centerX, centerY, radius, currentAngle, currentAngle + sliceAngle);
                tCtx.lineWidth = thickness;
                tCtx.strokeStyle = segment.color;
                tCtx.stroke();
                
                // Glow effect
                tCtx.shadowBlur = 10;
                tCtx.shadowColor = segment.color;
                tCtx.stroke();
                tCtx.shadowBlur = 0;
                
                currentAngle += sliceAngle;
            });
        }
        
        setTimeout(drawTokenomics, 100);

        // Countdown Timer
        function updateCountdown() {
            const endDate = new Date();
            endDate.setDate(endDate.getDate() + 12);
            endDate.setHours(endDate.getHours() + 8);
            endDate.setMinutes(endDate.getMinutes() + 45);
            
            function calculate() {
                const now = new Date();
                const diff = endDate - now;
                
                const days = Math.floor(diff / (1000 * 60 * 60 * 24));
                const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
                
                document.getElementById('days').textContent = String(days).padStart(2, '0');
                document.getElementById('hours').textContent = String(hours).padStart(2, '0');
                document.getElementById('minutes').textContent = String(minutes).padStart(2, '0');
            }
            
            calculate();
            setInterval(calculate, 60000);
        }
        updateCountdown();

        // Scroll Animations
        gsap.from(".feature-card", {
            scrollTrigger: {
                trigger: "#protection",
                start: "top 80%",
            },
            y: 50,
            opacity: 0,
            duration: 0.8,
            stagger: 0.2,
            ease: "power3.out"
        });

        gsap.from("#growthChart", {
            scrollTrigger: {
                trigger: "#growth",
                start: "top 70%",
            },
            scale: 0.8,
            opacity: 0,
            duration: 1,
            ease: "power3.out"
        });

        // Navbar scroll effect
        window.addEventListener('scroll', () => {
            const navbar = document.getElementById('navbar');
            if (window.scrollY > 50) {
                navbar.classList.add('bg-slate-900/90');
            } else {
                navbar.classList.remove('bg-slate-900/90');
            }
        });

        // Progress bar animation
        gsap.to("#progressBar", {
            width: "67%",
            duration: 2,
            ease: "power2.out",
            delay: 0.5
        });
    </script>
</body>
</html>
