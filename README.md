<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AR TREND HUB | Comprehensive Indian Portal</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Chart.js CDN for historical trend visualization -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js@3.7.1/dist/chart.min.js"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f7f9fc;
        }
        /* Custom styles for the hub design */
        .price-card, .tab-content-card {
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.06);
            transition: transform 0.3s ease;
        }
        .price-card:hover { transform: translateY(-2px); }
        .up-trend { color: #059669; }
        .down-trend { color: #dc2626; }
        .table-container { max-width: 100%; overflow-x: auto; -webkit-overflow-scrolling: touch; }
        #calculation-result { min-height: 80px; }
        .header-logo { height: 40px; width: auto; }
        
        /* Style for the active tab */
        .tab-button.active {
            border-bottom: 3px solid #f59e0b; /* Amber-500 */
            color: #1f2937; /* Dark text */
            font-weight: 600;
            background-color: #f3f4f6;
        }
    </style>
</head>
<body>
    <!-- Header and Main Title -->
    <header class="bg-indigo-700 text-white p-4 sm:p-6 shadow-xl">
        <div class="max-w-7xl mx-auto flex flex-col sm:flex-row justify-between items-start sm:items-center">
            <div class="flex items-center">
                <!-- LOGO INTEGRATION (Remember to upload the image!) -->
                <img src="assets/logo.png" 
                     onerror="this.onerror=null; this.src='https://placehold.co/180x40/4f46e5/ffffff?text=AR+TREND+HUB';"
                     alt="AR TREND HUB Logo" 
                     class="header-logo mr-3 hidden sm:block">
                <h1 class="text-2xl sm:text-3xl font-bold tracking-tight">
                    <span class="text-yellow-400">AR TREND</span> HUB
                </h1>
            </div>
            <div id="last-updated" class="text-sm mt-2 sm:mt-0 opacity-80">
                Last Updated: <span id="current-time"></span>
            </div>
        </div>
    </header>

    <!-- Navigation Tabs -->
    <nav class="sticky top-0 z-20 bg-white shadow-md">
        <div class="max-w-7xl mx-auto flex overflow-x-auto">
            <button class="tab-button active p-3 sm:px-6 flex-shrink-0 text-sm sm:text-base text-gray-700 border-b-2 border-transparent hover:bg-gray-100" onclick="showTab('commodities', this)">
                <span class="hidden sm:inline">💰</span> Commodities & Gold
            </button>
            <button class="tab-button p-3 sm:px-6 flex-shrink-0 text-sm sm:text-base text-gray-700 border-b-2 border-transparent hover:bg-gray-100" onclick="showTab('stock-market', this)">
                <span class="hidden sm:inline">📈</span> Stock Market
            </button>
            <button class="tab-button p-3 sm:px-6 flex-shrink-0 text-sm sm:text-base text-gray-700 border-b-2 border-transparent hover:bg-gray-100" onclick="showTab('job-alerts', this)">
                <span class="hidden sm:inline">💼</span> Job Alerts
            </button>
            <button class="tab-button p-3 sm:px-6 flex-shrink-0 text-sm sm:text-base text-gray-700 border-b-2 border-transparent hover:bg-gray-100" onclick="showTab('gov-schemes', this)">
                <span class="hidden sm:inline">🏛️</span> Govt. Schemes
            </button>
            <button class="tab-button p-3 sm:px-6 flex-shrink-0 text-sm sm:text-base text-gray-700 border-b-2 border-transparent hover:bg-gray-100" onclick="showTab('science-tech', this)">
                <span class="hidden sm:inline">🔬</span> Science & Tech
            </button>
        </div>
    </nav>

    <!-- Main Content Area -->
    <main class="max-w-7xl mx-auto p-4 sm:p-6 lg:p-8">

        <!-- 1. COMMODITIES & GOLD Tab Content (Default View) -->
        <div id="commodities" class="tab-content">
            <section class="mb-10">
                <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-4">Today's Indicative Commodity Prices (₹/Gram)</h2>
                <div id="overview-cards" class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    <!-- Price Cards will be rendered here by JS (using mock data for structure) -->
                    <div id="card-24k" class="price-card bg-white p-6 rounded-xl border-t-4 border-yellow-500">
                        <h3 class="text-lg font-semibold text-gray-500 mb-2">24 Karat Gold</h3>
                        <div class="flex items-end justify-between"><p class="text-3xl font-bold text-gray-900">₹<span id="price-24k-1g">0.00</span></p><div class="text-right"><span id="change-24k" class="text-sm font-medium"></span><span class="text-xs text-gray-500 block">per gram</span></div></div>
                        <div class="mt-4 text-sm text-gray-500">10 Gram: ₹<span id="price-24k-10g">0.00</span></div>
                    </div>
                    <div id="card-22k" class="price-card bg-white p-6 rounded-xl border-t-4 border-amber-500">
                        <h3 class="text-lg font-semibold text-gray-500 mb-2">22 Karat Gold</h3>
                        <div class="flex items-end justify-between"><p class="text-3xl font-bold text-gray-900">₹<span id="price-22k-1g">0.00</span></p><div class="text-right"><span id="change-22k" class="text-sm font-medium"></span><span class="text-xs text-gray-500 block">per gram</span></div></div>
                        <div class="mt-4 text-sm text-gray-500">10 Gram: ₹<span id="price-22k-10g">0.00</span></div>
                    </div>
                    <div id="card-silver" class="price-card bg-white p-6 rounded-xl border-t-4 border-gray-400">
                        <h3 class="text-lg font-semibold text-gray-500 mb-2">Silver Price</h3>
                        <div class="flex items-end justify-between"><p class="text-3xl font-bold text-gray-900">₹<span id="price-silver-1g">0.00</span></p><div class="text-right"><span id="change-silver" class="text-sm font-medium"></span><span class="text-xs text-gray-500 block">per gram</span></div></div>
                        <div class="mt-4 text-sm text-gray-500">1 Kg: ₹<span id="price-silver-1kg">0.00</span></div>
                    </div>
                </div>
            </section>
            
            <!-- Price Calculator -->
            <section class="mb-10 p-6 bg-white rounded-xl shadow-lg border-t-4 border-indigo-500">
                <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-6 flex items-center">Gold Price Estimate Calculator</h2>
                <!-- Calculator inputs/results omitted for brevity, logic remains in script -->
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6 items-center">
                    <div><label for="weight-input" class="block text-sm font-medium text-gray-700 mb-2">Enter Weight (in Grams)</label><input type="number" id="weight-input" value="10" min="1" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-yellow-500 focus:border-yellow-500 transition duration-150" placeholder="e.g., 5, 10, 50"></div>
                    <div><label for="carat-select" class="block text-sm font-medium text-gray-700 mb-2">Select Purity (Carat)</label><select id="carat-select" class="w-full p-3 border border-gray-300 rounded-lg bg-white focus:ring-yellow-500 focus:border-yellow-500 transition duration-150"><option value="24">24 Karat (99.9% Pure)</option><option value="22" selected>22 Karat (Jewellery Standard)</option><option value="18">18 Karat</option><option value="14">14 Karat</option></select></div>
                    <div class="self-end pt-2 md:pt-0"><button onclick="calculatePrice()" class="w-full bg-yellow-500 hover:bg-yellow-600 text-indigo-900 font-bold py-3 px-4 rounded-lg shadow-md transition duration-200 ease-in-out"> Calculate Price </button></div>
                </div>
                <div id="calculation-result" class="mt-6 p-4 bg-yellow-50 border-l-4 border-yellow-500 text-gray-800 rounded-lg"><p class="text-sm font-medium">Estimated Price:</p><p class="text-3xl font-extrabold text-indigo-700 mt-1">₹ <span id="final-price">0.00</span></p><p class="text-xs text-gray-500 mt-2">Note: Calculation is based on the live indicative rate displayed above, excluding charges and taxes.</p></div>
            </section>

            <!-- Historical Price Trend Section -->
            <section class="mb-10 p-6 bg-white rounded-xl shadow-lg border-t-4 border-yellow-700">
                <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-6 flex items-center">Historical Price Trend: 24K Gold (30 Days)</h2>
                <div class="h-80 w-full"><canvas id="historicalChart"></canvas></div>
            </section>

            <!-- Market Analysis Section (GEMINI API) -->
            <section class="mb-10 p-6 bg-white rounded-xl shadow-lg border-t-4 border-teal-500">
                <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-6 flex items-center">Current Commodity Market Analysis (Live Insights)</h2>
                <button id="fetch-analysis-btn" onclick="fetchMarketAnalysis('commodity-analysis', 'Act as an expert Indian commodity market analyst. Provide a single-paragraph summary of the current factors and global cues driving gold and silver prices in India today. Focus only on the main economic drivers.', 'What are the major price drivers for gold and silver commodities in India right now?')" class="w-full sm:w-auto bg-teal-500 hover:bg-teal-600 text-white font-bold py-3 px-6 rounded-lg shadow-md transition duration-200 ease-in-out mb-4">
                    Get Latest Price Drivers & Outlook
                </button>
                <div id="commodity-analysis-container" class="analysis-container mt-4 p-4 border border-gray-200 rounded-lg bg-gray-50 min-h-[150px] flex flex-col justify-center items-center">
                    <p id="commodity-analysis-text" class="text-gray-700 text-base leading-relaxed text-center">
                        Click the button to fetch a summary of the current factors driving gold and silver prices.
                    </p>
                    <div id="commodity-analysis-sources" class="mt-4 w-full text-xs text-gray-500"></div>
                    <div id="commodity-analysis-loader" class="loader hidden flex items-center justify-center text-teal-600">
                        <svg class="animate-spin -ml-1 mr-3 h-5 w-5" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"><circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle><path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path></svg>
                        Fetching real-time market insights...
                    </div>
                </div>
            </section>
        </div>

        <!-- 2. STOCK MARKET Tab Content -->
        <div id="stock-market" class="tab-content hidden">
            <h2 class="text-2xl font-semibold text-gray-800 mb-6 flex items-center"><span class="text-green-600 mr-2">📈</span> NSE/BSE Stock Market Data & News</h2>

            <!-- Summary/Top Movers Section -->
            <section class="mb-8 p-6 bg-white rounded-xl shadow-lg border-t-4 border-green-500">
                <h3 class="text-xl font-semibold text-gray-700 mb-4">Nifty 50 & Sensex Overview (Live Summary)</h3>
                
                <button onclick="fetchMarketAnalysis('stock-analysis', 'Act as a professional Indian stock market commentator. Provide a concise, single-paragraph summary of today\'s market performance, including brief commentary on Nifty 50 and Sensex, and mention the general trend (top gainers/losers segments).', 'Summarize today\'s performance of the Indian stock market, including Nifty 50 and Sensex trends.', this)" class="w-full sm:w-auto bg-green-500 hover:bg-green-600 text-white font-bold py-3 px-6 rounded-lg shadow-md transition mb-4">
                    Get Today's Market Summary
                </button>

                <div id="stock-analysis-container" class="analysis-container mt-4 p-4 border border-gray-200 rounded-lg bg-gray-50 min-h-[150px] flex flex-col justify-center items-center">
                    <p id="stock-analysis-text" class="text-gray-700 text-base leading-relaxed text-center">
                        Click the button to get the latest analysis on the Nifty 50 and Sensex performance.
                    </p>
                    <div id="stock-analysis-sources" class="mt-4 w-full text-xs text-gray-500"></div>
                    <div id="stock-analysis-loader" class="loader hidden flex items-center justify-center text-green-600">
                        <svg class="animate-spin -ml-1 mr-3 h-5 w-5" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"><circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle><path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path></svg>
                        Fetching latest stock news...
                    </div>
                </div>
            </section>
        </div>

        <!-- 3. JOB ALERTS Tab Content -->
        <div id="job-alerts" class="tab-content hidden">
            <h2 class="text-2xl font-semibold text-gray-800 mb-6 flex items-center"><span class="text-pink-600 mr-2">💼</span> Free Job Alerts & Notifications (Govt/Private)</h2>
            <section class="mb-8 p-6 bg-white rounded-xl shadow-lg border-t-4 border-pink-500">
                <h3 class="text-xl font-semibold text-gray-700 mb-4">Latest Top Job Notifications in India</h3>
                
                <button onclick="fetchMarketAnalysis('job-analysis', 'Act as a helpful Indian job search guide. Provide a concise, easy-to-read summary listing 3-4 top active Government or major Private Sector job notifications in India currently. For each, mention the organization/department and the last date to apply if possible.', 'List top 4 current job alerts in India for government and private sectors.', this)" class="w-full sm:w-auto bg-pink-500 hover:bg-pink-600 text-white font-bold py-3 px-6 rounded-lg shadow-md transition mb-4">
                    Get Latest Job Alerts
                </button>

                <div id="job-analysis-container" class="analysis-container mt-4 p-4 border border-gray-200 rounded-lg bg-gray-50 min-h-[150px] flex flex-col justify-center items-center">
                    <p id="job-analysis-text" class="text-gray-700 text-base leading-relaxed text-center">
                        Click the button to fetch the latest top government and private job notifications.
                    </p>
                    <div id="job-analysis-sources" class="mt-4 w-full text-xs text-gray-500"></div>
                    <div id="job-analysis-loader" class="loader hidden flex items-center justify-center text-pink-600">
                        <svg class="animate-spin -ml-1 mr-3 h-5 w-5" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"><circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle><path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path></svg>
                        Searching for job notifications...
                    </div>
                </div>
            </section>
        </div>
        
        <!-- 4. GOVERNMENT SCHEMES Tab Content -->
        <div id="gov-schemes" class="tab-content hidden">
            <h2 class="text-2xl font-semibold text-gray-800 mb-6 flex items-center"><span class="text-blue-600 mr-2">🏛️</span> Central & State Government Schemes (Simplified)</h2>
            <section class="mb-8 p-6 bg-white rounded-xl shadow-lg border-t-4 border-blue-500">
                <h3 class="text-xl font-semibold text-gray-700 mb-4">Latest Scheme Information for Citizens</h3>
                
                <button onclick="fetchMarketAnalysis('schemes-analysis', 'Act as a government scheme explainer. Summarize 3 major active Central Government schemes (e.g., related to finance, housing, or welfare) in simple, easy-to-understand points. Focus on who benefits and the main goal.', 'Summarize 3 current central government schemes for the public.', this)" class="w-full sm:w-auto bg-blue-500 hover:bg-blue-600 text-white font-bold py-3 px-6 rounded-lg shadow-md transition mb-4">
                    Get Simplified Scheme Summaries
                </button>

                <div id="schemes-analysis-container" class="analysis-container mt-4 p-4 border border-gray-200 rounded-lg bg-gray-50 min-h-[150px] flex flex-col justify-center items-center">
                    <p id="schemes-analysis-text" class="text-gray-700 text-base leading-relaxed text-center">
                        Click the button to get summaries of current central government schemes.
                    </p>
                    <div id="schemes-analysis-sources" class="mt-4 w-full text-xs text-gray-500"></div>
                    <div id="schemes-analysis-loader" class="loader hidden flex items-center justify-center text-blue-600">
                        <svg class="animate-spin -ml-1 mr-3 h-5 w-5" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"><circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle><path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path></svg>
                        Fetching government scheme details...
                    </div>
                </div>
            </section>
        </div>

        <!-- 5. SCIENCE & TECH Tab Content -->
        <div id="science-tech" class="tab-content hidden">
            <h2 class="text-2xl font-semibold text-gray-800 mb-6 flex items-center"><span class="text-red-600 mr-2">🔬</span> Latest Science & Technology News</h2>
            <section class="mb-8 p-6 bg-white rounded-xl shadow-lg border-t-4 border-red-500">
                <h3 class="text-xl font-semibold text-gray-700 mb-4">Top Articles and Breakthroughs</h3>
                
                <button onclick="fetchMarketAnalysis('science-analysis', 'Act as a science journalist. Summarize 3 recent and significant science and technology news articles or breakthroughs (e.g., in space, AI, or medicine) in India or globally, keeping the summary engaging and concise.', 'Summarize 3 recent significant science and technology news articles.', this)" class="w-full sm:w-auto bg-red-500 hover:bg-red-600 text-white font-bold py-3 px-6 rounded-lg shadow-md transition mb-4">
                    Get Latest S&T News
                </button>

                <div id="science-analysis-container" class="analysis-container mt-4 p-4 border border-gray-200 rounded-lg bg-gray-50 min-h-[150px] flex flex-col justify-center items-center">
                    <p id="science-analysis-text" class="text-gray-700 text-base leading-relaxed text-center">
                        Click the button to get the latest news on science and technology.
                    </p>
                    <div id="science-analysis-sources" class="mt-4 w-full text-xs text-gray-500"></div>
                    <div id="science-analysis-loader" class="loader hidden flex items-center justify-center text-red-600">
                        <svg class="animate-spin -ml-1 mr-3 h-5 w-5" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"><circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle><path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path></svg>
                        Fetching science and tech updates...
                    </div>
                </div>
            </section>
        </div>

    </main>

    <footer class="bg-gray-100 mt-10 p-4 sm:p-6 text-center text-gray-600 text-xs">
        &copy; 2025 AR TREND HUB. Data Simulated for Demonstration Purposes. Live Analysis Powered by Gemini.
    </footer>

    <script>
        // Set the global font for Tailwind
        document.documentElement.style.fontFamily = "'Inter', sans-serif";

        // Global Rates Holder - Used by the calculator
        const currentRates = { '24k_1g': 0, '22k_1g': 0, '18k_1g': 0, '14k_1g': 0 };

        const formatCurrency = (value) => {
            return value.toLocaleString('en-IN', { minimumFractionDigits: 0, maximumFractionDigits: 0 });
        };

        const formatChange = (change) => {
            const isPositive = change >= 0;
            const sign = isPositive ? '▲' : '▼';
            const colorClass = isPositive ? 'up-trend' : 'down-trend';
            return `<span class="${colorClass}">${sign} ${Math.abs(change).toFixed(2)}</span>`;
        };

        // --- MOCK DATA ---
        const MOCK_BASE_PRICE_24K = 65000; // 10 grams 24K 
        const MOCK_BASE_PRICE_22K = 59500; // 10 grams 22K
        const MOCK_BASE_PRICE_SILVER = 92; // 1 gram Silver 
        const MOCK_OVERVIEW_CHANGE = {
            '24k': 0.15, 
            '22k': 0.12,
            'silver': -0.45
        };

        const CARAT_PURITY_MAP = {
            24: 1.00,
            22: 22 / 24, 
            18: 18 / 24, 
            14: 14 / 24 
        };

        const CITY_PRICES = [
            { city: "Mumbai", base: 1.00, change: -0.15 },
            { city: "Delhi", base: 1.001, change: 0.05 },
            { city: "Chennai", base: 1.004, change: 0.22 },
            { city: "Kolkata", base: 0.998, change: -0.10 },
            { city: "Bangalore", base: 1.00, change: 0.15 },
            { city: "Hyderabad", base: 1.002, change: 0.00 },
            { city: "Ahmedabad", base: 1.00, change: 0.18 },
            { city: "Jaipur", base: 1.001, change: -0.05 },
            { city: "Pune", base: 0.999, change: -0.12 },
        ];

        const MOCK_HISTORICAL_DATA = {
            labels: [], 
            prices: [] 
        };

        function generateMockHistoricalData() {
            const days = 30;
            const endDate = new Date();
            const startPrice = MOCK_BASE_PRICE_24K * 0.95;
            let currentPrice = startPrice;

            for (let i = 0; i < days; i++) {
                const date = new Date(endDate);
                date.setDate(endDate.getDate() - (days - 1 - i));
                MOCK_HISTORICAL_DATA.labels.push(date.toLocaleDateString('en-IN', { day: '2-digit', month: 'short' }));
                const fluctuation = (Math.random() - 0.5) * 500; 
                const trend = (MOCK_BASE_PRICE_24K - startPrice) / days * 1.5;
                currentPrice += trend + fluctuation;
                currentPrice = Math.max(currentPrice, MOCK_BASE_PRICE_24K * 0.9);
                MOCK_HISTORICAL_DATA.prices.push(Math.round(currentPrice / 10) * 10);
            }
            MOCK_HISTORICAL_DATA.prices[days - 1] = Math.round(MOCK_BASE_PRICE_24K * (1 + MOCK_OVERVIEW_CHANGE['24k'] / 100) / 10) * 10;
        }
        // --- END MOCK DATA ---

        // --- CORE FUNCTIONS ---

        /**
         * Renders the main commodity overview cards and populates global rates.
         */
        function renderOverview() {
            // 24K Gold Calculations
            const change24kPercent = MOCK_OVERVIEW_CHANGE['24k'];
            const price24k_10g_raw = MOCK_BASE_PRICE_24K * (1 + change24kPercent / 100);
            const price24k_1g_raw = price24k_10g_raw / 10;
            const price24k_1g_change = (price24k_10g_raw - MOCK_BASE_PRICE_24K) / 10;
            currentRates['24k_1g'] = price24k_1g_raw;

            const element24k1g = document.getElementById('price-24k-1g');
            const element24k10g = document.getElementById('price-24k-10g');
            const element24kChange = document.getElementById('change-24k');
            
            if (element24k1g) element24k1g.textContent = formatCurrency(price24k_1g_raw);
            if (element24k10g) element24k10g.textContent = formatCurrency(price24k_10g_raw);
            if (element24kChange) element24kChange.innerHTML = formatChange(price24k_1g_change);

            // 22K Gold Calculations
            const change22kPercent = MOCK_OVERVIEW_CHANGE['22k'];
            const price22k_10g_raw = MOCK_BASE_PRICE_22K * (1 + change22kPercent / 100);
            const price22k_1g_raw = price22k_10g_raw / 10;
            const price22k_1g_change = (price22k_10g_raw - MOCK_BASE_PRICE_22K) / 10;
            currentRates['22k_1g'] = price22k_1g_raw;

            const element22k1g = document.getElementById('price-22k-1g');
            const element22k10g = document.getElementById('price-22k-10g');
            const element22kChange = document.getElementById('change-22k');

            if (element22k1g) element22k1g.textContent = formatCurrency(price22k_1g_raw);
            if (element22k10g) element22k10g.textContent = formatCurrency(price22k_10g_raw);
            if (element22kChange) element22kChange.innerHTML = formatChange(price22k_1g_change);

            // Calculate and store other carat rates
            const p24k = currentRates['24k_1g'];
            currentRates['18k_1g'] = p24k * CARAT_PURITY_MAP[18];
            currentRates['14k_1g'] = p24k * CARAT_PURITY_MAP[14];

            // Silver Calculations
            const changeSilverPercent = MOCK_OVERVIEW_CHANGE['silver'];
            const priceSilver_1g_raw = MOCK_BASE_PRICE_SILVER * (1 + changeSilverPercent / 100);
            const priceSilver_1kg_raw = priceSilver_1g_raw * 1000;
            const priceSilver_1g_change = (priceSilver_1g_raw - MOCK_BASE_PRICE_SILVER);

            const elementSilver1g = document.getElementById('price-silver-1g');
            const elementSilver1kg = document.getElementById('price-silver-1kg');
            const elementSilverChange = document.getElementById('change-silver');

            if (elementSilver1g) elementSilver1g.textContent = formatCurrency(priceSilver_1g_raw);
            if (elementSilver1kg) elementSilver1kg.textContent = formatCurrency(priceSilver_1kg_raw);
            if (elementSilverChange) elementSilverChange.innerHTML = formatChange(priceSilver_1g_change);
        }

        /**
         * Renders the historical price chart using Chart.js.
         */
        function renderHistoricalChart() {
            const chartCanvas = document.getElementById('historicalChart');
            if (!chartCanvas) return; // Only run if the element is present

            generateMockHistoricalData(); // Generate data first
            const ctx = chartCanvas.getContext('2d');
            
            // Check if chart already exists to prevent duplication on tab switch
            if (chartCanvas.chartInstance) {
                chartCanvas.chartInstance.destroy();
            }

            const chartConfig = {
                type: 'line',
                data: {
                    labels: MOCK_HISTORICAL_DATA.labels,
                    datasets: [{
                        label: '24K Gold Rate (₹/10g)',
                        data: MOCK_HISTORICAL_DATA.prices,
                        borderColor: 'rgb(202, 138, 4)', 
                        backgroundColor: 'rgba(251, 191, 36, 0.2)',
                        fill: true,
                        tension: 0.2, 
                        pointRadius: 2,
                        pointBackgroundColor: 'rgb(202, 138, 4)',
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false }, title: { display: false } },
                    scales: {
                        y: { title: { display: true, text: 'Price in INR (₹)', font: { size: 14 } }, beginAtZero: false, grid: { color: 'rgba(0,0,0,0.05)' } },
                        x: { title: { display: true, text: 'Last 30 Days', font: { size: 14 } }, grid: { display: false } }
                    }
                }
            };

            chartCanvas.chartInstance = new Chart(ctx, chartConfig);
        }

        /**
         * Calculates the estimated price based on user inputs.
         */
        function calculatePrice() {
            const weightInput = document.getElementById('weight-input');
            const caratSelect = document.getElementById('carat-select');
            const resultElement = document.getElementById('final-price');

            if (!weightInput || !caratSelect || !resultElement) return;

            const weight = parseFloat(weightInput.value);
            const carat = caratSelect.value;
            if (isNaN(weight) || weight <= 0) {
                resultElement.textContent = 'Invalid Weight';
                resultElement.classList.add('text-red-600');
                return;
            }

            resultElement.classList.remove('text-red-600');

            let ratePerGram = 0;
            const caratFloat = parseFloat(carat);

            if (caratFloat === 24) {
                ratePerGram = currentRates['24k_1g'];
            } else if (caratFloat === 22) {
                ratePerGram = currentRates['22k_1g'];
            } else if (caratFloat === 18) {
                ratePerGram = currentRates['18k_1g'];
            } else if (caratFloat === 14) {
                ratePerGram = currentRates['14k_1g'];
            } else {
                ratePerGram = currentRates['24k_1g'] * (caratFloat / 24);
            }

            if (ratePerGram === 0) {
                resultElement.textContent = 'Data Error';
                resultElement.classList.add('text-red-600');
                console.error("Rate per gram is zero. Check currentRates object.");
                return;
            }

            const totalPrice = weight * ratePerGram;
            resultElement.textContent = formatCurrency(Math.round(totalPrice));
        }

        /**
         * Updates the time display.
         */
        function updateTime() {
            const now = new Date();
            const timeString = now.toLocaleTimeString('en-IN', { hour: '2-digit', minute: '2-digit', second: '2-digit' }) + ' IST';
            const dateString = now.toLocaleDateString('en-IN', { year: 'numeric', month: 'short', day: 'numeric' });
            const timeElement = document.getElementById('current-time');
            if (timeElement) {
                 timeElement.textContent = `${dateString} | ${timeString}`;
            }
        }

        // --- TABBED NAVIGATION LOGIC ---

        function showTab(tabId, button) {
            // Hide all tab contents
            document.querySelectorAll('.tab-content').forEach(content => {
                content.classList.add('hidden');
            });

            // Deactivate all buttons
            document.querySelectorAll('.tab-button').forEach(btn => {
                btn.classList.remove('active');
            });

            // Show the selected tab content
            const selectedContent = document.getElementById(tabId);
            if (selectedContent) {
                selectedContent.classList.remove('hidden');
            }
            
            // Activate the clicked button
            if (button) {
                button.classList.add('active');
            }

            // Specific initialization logic for certain tabs
            if (tabId === 'commodities') {
                // Rerender chart when Commodities tab is opened to handle potential canvas resize issues
                renderHistoricalChart();
            }
        }


        // --- GEMINI API INTEGRATION for all Analysis Sections ---

        /**
         * Displays the generated text and sources in the analysis container.
         * @param {string} containerId - The ID prefix of the container elements (e.g., 'commodity-analysis')
         * @param {Object} data - Contains text and an array of sources.
         */
        function updateAnalysisUI(containerId, data) {
            const analysisTextElement = document.getElementById(`${containerId}-text`);
            const analysisSourcesElement = document.getElementById(`${containerId}-sources`);
            const loader = document.getElementById(`${containerId}-loader`);
            const button = document.querySelector(`#${containerId}-container`).previousElementSibling; // Button is the sibling above the container

            loader.classList.add('hidden');
            if (button) {
                button.disabled = false;
                button.textContent = `Get Latest ${containerId.split('-')[0].charAt(0).toUpperCase() + containerId.split('-')[0].slice(1)} Data`;
            }
            analysisTextElement.classList.remove('text-center', 'italic', 'text-gray-500', 'text-red-600');
            analysisTextElement.classList.add('text-left');

            if (data.error) {
                analysisTextElement.textContent = `Error fetching analysis: ${data.error}. Please try again later.`;
                analysisTextElement.classList.add('text-red-600', 'text-center');
                analysisSourcesElement.innerHTML = '';
                return;
            }

            // Display the generated text
            // Replace markdown-style lists/headings with HTML for better formatting
            let formattedText = data.text;
            formattedText = formattedText.replace(/### (.*)/g, '<h4 class="text-lg font-semibold mt-4 mb-2">$1</h4>');
            formattedText = formattedText.replace(/## (.*)/g, '<h3 class="text-xl font-bold mt-5 mb-3">$1</h3>');
            formattedText = formattedText.replace(/\* (.*)/g, '<li>$1</li>');
            formattedText = formattedText.replace(/\n\s*<li>/g, '<ul><li>').replace(/<\/li>\s*\n/g, '</li></ul>').replace(/<\/ul><ul>/g, '');


            analysisTextElement.innerHTML = formattedText;
            analysisTextElement.classList.remove('text-center');

            // Display the sources if they exist
            if (data.sources && data.sources.length > 0) {
                const sourceList = data.sources.map((source, index) =>
                    `<li class="hover:text-teal-700">
                        <a href="${source.uri}" target="_blank" rel="noopener noreferrer" class="underline">
                            ${source.title || `Source ${index + 1}`}
                        </a>
                    </li>`
                ).join('');

                analysisSourcesElement.innerHTML = `
                    <p class="font-medium text-teal-600 mb-1 mt-4">Sources:</p>
                    <ul class="list-disc list-inside space-y-0.5 ml-2">${sourceList}</ul>
                `;
            } else {
                analysisSourcesElement.innerHTML = '';
            }
        }

        /**
         * Fetches a grounded analysis summary using the Gemini API.
         * @param {string} containerId - The ID prefix of the container elements (e.g., 'commodity-analysis')
         * @param {string} systemPrompt - The system instruction to guide the model's persona.
         * @param {string} userQuery - The specific query for the model.
         * @param {HTMLElement} buttonElement - The button that triggered the function, for dynamic text update.
         */
        async function fetchMarketAnalysis(containerId, systemPrompt, userQuery, buttonElement) {
            const loader = document.getElementById(`${containerId}-loader`);
            const analysisTextElement = document.getElementById(`${containerId}-text`);

            // Reset UI and show loading state
            analysisTextElement.innerHTML = '';
            document.getElementById(`${containerId}-sources`).innerHTML = '';
            loader.classList.remove('hidden');
            buttonElement.disabled = true;
            buttonElement.textContent = 'Analyzing and Fetching Data...';

            // NOTE: The API key is left as an empty string and will be provided by the runtime environment.
            const apiKey = ""; 
            const model = 'gemini-2.5-flash-preview-09-2025';
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/${model}:generateContent?key=${apiKey}`;

            const payload = {
                contents: [{ parts: [{ text: userQuery }] }],
                tools: [{ "google_search": {} }], // Enable Google Search grounding
                systemInstruction: {
                    parts: [{ text: systemPrompt }]
                },
            };

            const maxRetries = 3;
            let result = { text: '', sources: [], error: null };

            for (let attempt = 0; attempt < maxRetries; attempt++) {
                try {
                    const response = await fetch(apiUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });

                    if (!response.ok) {
                        throw new Error(`HTTP error! status: ${response.status}`);
                    }

                    const jsonResult = await response.json();
                    const candidate = jsonResult.candidates?.[0];

                    if (candidate && candidate.content?.parts?.[0]?.text) {
                        result.text = candidate.content.parts[0].text;

                        // Extract grounding sources
                        const groundingMetadata = candidate.groundingMetadata;
                        if (groundingMetadata && groundingMetadata.groundingAttributions) {
                            result.sources = groundingMetadata.groundingAttributions
                                .map(attribution => ({
                                    uri: attribution.web?.uri,
                                    title: attribution.web?.title,
                                }))
                                .filter(source => source.uri && source.title);
                        }
                        // Success, break retry loop
                        break;
                    } else {
                        throw new Error("Invalid response structure from API.");
                    }
                } catch (error) {
                    console.error(`Attempt ${attempt + 1} failed:`, error);
                    result.error = "Could not connect to the analysis service.";
                    if (attempt < maxRetries - 1) {
                        await new Promise(resolve => setTimeout(resolve, Math.pow(2, attempt) * 1000));
                    } else {
                        updateAnalysisUI(containerId, result);
                        return;
                    }
                }
            }
            updateAnalysisUI(containerId, result);
        }


        // --- Initialization ---
        window.onload = function() {
            // Initial setup for the Commodities tab (since it's the default view)
            renderOverview();
            renderHistoricalChart();
            
            // Initial time update and set interval for real-time clock
            updateTime();
            setInterval(updateTime, 1000);

            // Calculate default price on load
            calculatePrice();

            // Attach event listeners for the calculator (only on the commodities tab)
            const weightInput = document.getElementById('weight-input');
            const caratSelect = document.getElementById('carat-select');
            if (weightInput) weightInput.addEventListener('input', calculatePrice);
            if (caratSelect) caratSelect.addEventListener('change', calculatePrice);

            // Ensure the first tab is active on load
            document.querySelector('.tab-button').classList.add('active');
        };
    </script>
</body>
</html>

