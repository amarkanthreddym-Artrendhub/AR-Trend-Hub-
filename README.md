    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>AR TREND HUB | Commodity & Analysis</title>
        <script src="https://cdn.tailwindcss.com"></script>
        <!-- Chart.js CDN for historical trend visualization -->
        <script src="https://cdn.jsdelivr.net/npm/chart.js@3.7.1/dist/chart.min.js"></script>
        <style>
            @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');
            body {
                font-family: 'Inter', sans-serif;
                background-color: #f7f9fc; /* Light background */
            }
            .price-card {
                box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.06);
                transition: transform 0.3s ease;
            }
            .price-card:hover {
                transform: translateY(-2px);
            }
            .up-trend {
                color: #059669; /* Emerald Green */
            }
            .down-trend {
                color: #dc2626; /* Red */
            }
            .yt-mock-item:hover {
                box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.1);
            }
            /* Style for the responsive table container */
            .table-container {
                max-width: 100%;
                overflow-x: auto;
                -webkit-overflow-scrolling: touch;
            }
            /* Style for calculator result display */
            #calculation-result {
                min-height: 80px; /* Ensure space for results */
            }
        </style>
    </head>
    <body>

        <!-- Header and Main Title -->
        <header class="bg-indigo-700 text-white p-4 sm:p-6 shadow-lg">
            <div class="max-w-7xl mx-auto flex flex-col sm:flex-row justify-between items-start sm:items-center">
                <h1 class="text-2xl sm:text-3xl font-bold tracking-tight">
                    <span class="text-yellow-400">AR TREND</span> HUB
                </h1>
                <div id="last-updated" class="text-sm mt-2 sm:mt-0 opacity-80">
                    Last Updated: <span id="current-time"></span>
                </div>
            </div>
        </header>

        <!-- Main Content Grid -->
        <main class="max-w-7xl mx-auto p-4 sm:p-6 lg:p-8">

            <!-- Today's Overview Section -->
            <section class="mb-10">
                <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-4">Today's Commodity Prices in India (â‚¹/Gram)</h2>
                <div id="overview-cards" class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    
                    <!-- Card 1: 24K Gold -->
                    <div id="card-24k" class="price-card bg-white p-6 rounded-xl border-t-4 border-yellow-500">
                        <h3 class="text-lg font-semibold text-gray-500 mb-2">24 Karat Gold (99.9% Pure)</h3>
                        <div class="flex items-end justify-between">
                            <p class="text-3xl font-bold text-gray-900">â‚¹<span id="price-24k-1g">0.00</span></p>
                            <div class="text-right">
                                <span id="change-24k" class="text-sm font-medium"></span>
                                <span class="text-xs text-gray-500 block">per gram</span>
                            </div>
                        </div>
                        <div class="mt-4 text-sm text-gray-500">
                            10 Gram: â‚¹<span id="price-24k-10g">0.00</span>
                        </div>
                    </div>

                    <!-- Card 2: 22K Gold -->
                    <div id="card-22k" class="price-card bg-white p-6 rounded-xl border-t-4 border-amber-500">
                        <h3 class="text-lg font-semibold text-gray-500 mb-2">22 Karat Gold (Jewellery)</h3>
                        <div class="flex items-end justify-between">
                            <p class="text-3xl font-bold text-gray-900">â‚¹<span id="price-22k-1g">0.00</span></p>
                            <div class="text-right">
                                <span id="change-22k" class="text-sm font-medium"></span>
                                <span class="text-xs text-gray-500 block">per gram</span>
                            </div>
                        </div>
                        <div class="mt-4 text-sm text-gray-500">
                            10 Gram: â‚¹<span id="price-22k-10g">0.00</span>
                        </div>
                    </div>

                    <!-- Card 3: Silver -->
                    <div id="card-silver" class="price-card bg-white p-6 rounded-xl border-t-4 border-gray-400">
                        <h3 class="text-lg font-semibold text-gray-500 mb-2">Silver Price</h3>
                        <div class="flex items-end justify-between">
                            <p class="text-3xl font-bold text-gray-900">â‚¹<span id="price-silver-1g">0.00</span></p>
                            <div class="text-right">
                                <span id="change-silver" class="text-sm font-medium"></span>
                                <span class="text-xs text-gray-500 block">per gram</span>
                            </div>
                        </div>
                        <div class="mt-4 text-sm text-gray-500">
                            1 Kg: â‚¹<span id="price-silver-1kg">0.00</span>
                        </div>
                    </div>

                </div>
            </section>
            
            <!-- Gold Price Calculator Section -->
            <section class="mb-10 p-6 bg-white rounded-xl shadow-lg border-t-4 border-indigo-500">
                <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-6 flex items-center">
                    <svg class="w-6 h-6 mr-2 text-indigo-600" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 7h6m0 10v-3m-3 3h.01M9 17h.01M12 17h.01M9 14h.01M12 14h.01M15 14h.01M12 10h.01M15 10h.01M12 7h.01M15 7h.01M7 7v10m10-10v10m-3-13h-4a2 2 0 00-2 2v10a2 2 0 002 2h4a2 2 0 002-2V9a2 2 0 00-2-2z"></path></svg>
                    Gold Price Estimate Calculator
                </h2>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-6 items-center">
                    <!-- Input 1: Weight -->
                    <div>
                        <label for="weight-input" class="block text-sm font-medium text-gray-700 mb-2">Enter Weight (in Grams)</label>
                        <input type="number" id="weight-input" value="10" min="1" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-yellow-500 focus:border-yellow-500 transition duration-150" placeholder="e.g., 5, 10, 50">
                    </div>
                    
                    <!-- Input 2: Carat Purity -->
                    <div>
                        <label for="carat-select" class="block text-sm font-medium text-gray-700 mb-2">Select Purity (Carat)</label>
                        <select id="carat-select" class="w-full p-3 border border-gray-300 rounded-lg bg-white focus:ring-yellow-500 focus:border-yellow-500 transition duration-150">
                            <option value="24">24 Karat (99.9% Pure)</option>
                            <option value="22" selected>22 Karat (Jewellery Standard)</option>
                            <option value="18">18 Karat</option>
                            <option value="14">14 Karat</option>
                        </select>
                    </div>
                    
                    <!-- Calculation Button -->
                    <div class="self-end pt-2 md:pt-0">
                        <button onclick="calculatePrice()" class="w-full bg-yellow-500 hover:bg-yellow-600 text-indigo-900 font-bold py-3 px-4 rounded-lg shadow-md transition duration-200 ease-in-out">
                            Calculate Price
                        </button>
                    </div>
                </div>

                <!-- Result Display -->
                <div id="calculation-result" class="mt-6 p-4 bg-yellow-50 border-l-4 border-yellow-500 text-gray-800 rounded-lg">
                    <p class="text-sm font-medium">Estimated Price:</p>
                    <p class="text-3xl font-extrabold text-indigo-700 mt-1">â‚¹ <span id="final-price">0.00</span></p>
                    <p class="text-xs text-gray-500 mt-2">Note: Calculation is based on the live indicative rate displayed above, excluding making charges and taxes (GST/TCS).</p>
                </div>
            </section>

            <!-- Historical Price Trend Section (NEW) -->
            <section class="mb-10 p-6 bg-white rounded-xl shadow-lg border-t-4 border-yellow-700">
                <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-6 flex items-center">
                    <svg class="w-6 h-6 mr-2 text-yellow-700" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6"></path></svg>
                    Historical Price Trend: 24K Gold (30 Days)
                </h2>
                <div class="h-80 w-full">
                    <canvas id="historicalChart"></canvas>
                </div>
            </section>

            <!-- City-Wise Gold Rates Table -->
            <section class="mb-10">
                <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-4">Gold Rate Today in Major Indian Cities (10 Grams)</h2>
                <div class="table-container bg-white rounded-xl shadow overflow-hidden">
                    <table class="min-w-full divide-y divide-gray-200">
                        <thead class="bg-gray-50">
                            <tr>
                                <th class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider sticky left-0 z-10 bg-gray-50">City</th>
                                <th class="px-4 py-3 text-right text-xs font-medium text-gray-500 uppercase tracking-wider">24K (â‚¹)</th>
                                <th class="px-4 py-3 text-right text-xs font-medium text-gray-500 uppercase tracking-wider">Change</th>
                                <th class="px-4 py-3 text-right text-xs font-medium text-gray-500 uppercase tracking-wider">22K (â‚¹)</th>
                                <th class="px-4 py-3 text-right text-xs font-medium text-gray-500 uppercase tracking-wider">Change</th>
                            </tr>
                        </thead>
                        <tbody id="city-prices-body" class="bg-white divide-y divide-gray-200">
                            <!-- City rows will be injected here by JavaScript -->
                        </tbody>
                    </table>
                </div>
                <p class="text-sm text-gray-500 mt-2 p-2">
                    <span class="font-bold">*Note:</span> Prices are indicative and exclude GST, TCS, and making charges.
                </p>
            </section>
            
            <!-- Mock YouTube & Analysis Section -->
            <section class="mt-12 bg-white p-6 rounded-xl shadow-lg">
                <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-6 flex items-center">
                    <svg class="w-6 h-6 mr-2 text-red-600" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM9.555 7.168A1 1 0 008 8v4a1 1 0 001.555.832l3-2a1 1 0 000-1.664l-3-2z" clip-rule="evenodd"></path></svg>
                    Gold Price Analysis & YouTube Updates
                </h2>
                <div id="youtube-mock-grid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
                    <!-- Mock YouTube Videos -->
                </div>
                <div class="text-center mt-6">
                    <a href="#" class="inline-flex items-center justify-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-red-600 hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500 transition duration-150 ease-in-out">
                        View More Video Analysis
                    </a>
                </div>
            </section>

        </main>

        <footer class="bg-gray-100 mt-10 p-4 sm:p-6 text-center text-gray-600 text-xs">
            &copy; 2025 AR TREND HUB. Data Simulated for Demonstration Purposes.
        </footer>

        <script>
            // Set the global font for Tailwind
            document.documentElement.style.fontFamily = "'Inter', sans-serif";

            // Global Rates Holder - Used by the calculator
            const currentRates = {
                '24k_1g': 0,
                '22k_1g': 0,
                '18k_1g': 0,
                '14k_1g': 0
            };

            const formatCurrency = (value) => {
                return value.toLocaleString('en-IN', {
                    minimumFractionDigits: 0,
                    maximumFractionDigits: 0
                });
            };
            
            const formatChange = (change) => {
                const isPositive = change >= 0;
                const sign = isPositive ? 'â–²' : 'â–¼';
                const colorClass = isPositive ? 'up-trend' : 'down-trend';
                return `<span class="${colorClass}">${sign} ${Math.abs(change).toFixed(2)}</span>`;
            };

            // --- MOCK DATA ---
            const MOCK_BASE_PRICE_24K = 125120; // 10 grams 24K (Starting point for today's mock price)
            const MOCK_BASE_PRICE_22K = 114690; // 10 grams 22K
            const MOCK_BASE_PRICE_SILVER = 930; // 10 grams Silver (approx 93000 per kg)

            const MOCK_OVERVIEW_CHANGE = {
                '24k': 0.15, // +0.15% change for 24K
                '22k': 0.12, // +0.12% change for 22K
                'silver': -0.45 // -0.45% change for Silver
            };

            const CARAT_PURITY_MAP = {
                // These are ratios relative to 24K (100% pure)
                24: 1.00,
                22: 22 / 24, // 0.9167
                18: 18 / 24, // 0.75
                14: 14 / 24  // 0.5833
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

            const MOCK_YOUTUBE_VIDEOS = [
                { title: "Gold Price Forecast: Will Yellow Metal hit â‚¹70,000 by Diwali?", channel: "AR TREND HUB", views: "1.2M" },
                { title: "Silver Price Analysis: Is the White Metal a better Buy than Gold Today?", channel: "AR TREND HUB", views: "450K" },
                { title: "How to Invest in Digital Gold vs SGBs (Sovereign Gold Bonds)", channel: "AR TREND HUB", views: "88K" },
                { title: "Global Market Impact on Indian Gold Rates (US Fed Decision Explained)", channel: "AR TREND HUB", views: "600K" },
            ];
            
            const MOCK_HISTORICAL_DATA = {
                labels: [], // Dates for the last 30 days
                prices: []  // Mock 24K Gold Price per 10 grams
            };

            function generateMockHistoricalData() {
                const days = 30;
                const endDate = new Date();
                // Start price 5% lower than current mock price
                const startPrice = MOCK_BASE_PRICE_24K * 0.95; 
                let currentPrice = startPrice;

                for (let i = 0; i < days; i++) {
                    const date = new Date(endDate);
                    // Calculate date for the label
                    date.setDate(endDate.getDate() - (days - 1 - i)); 
                    
                    // Format date as DD MMM
                    MOCK_HISTORICAL_DATA.labels.push(date.toLocaleDateString('en-IN', { day: '2-digit', month: 'short' }));
                    
                    // Simulate general upward trend and random fluctuation
                    const fluctuation = (Math.random() - 0.5) * 1000; // +/- 500
                    const trend = (MOCK_BASE_PRICE_24K - startPrice) / days;
                    
                    currentPrice += trend + fluctuation;
                    currentPrice = Math.max(currentPrice, MOCK_BASE_PRICE_24K * 0.9); // Keep a floor
                    
                    // Round price to nearest 10 for clean display
                    MOCK_HISTORICAL_DATA.prices.push(Math.round(currentPrice / 10) * 10); 
                }
                // Ensure the last price is exactly the current mock price
                MOCK_HISTORICAL_DATA.prices[days - 1] = Math.round(MOCK_BASE_PRICE_24K * (1 + MOCK_OVERVIEW_CHANGE['24k'] / 100) / 10) * 10;
            }
            // --- END MOCK DATA ---

            /**
             * Renders the main commodity overview cards and populates global rates.
             */
            function renderOverview() {
                // 24K Gold Calculations
                const change24kPercent = MOCK_OVERVIEW_CHANGE['24k'];
                const price24k_10g_raw = MOCK_BASE_PRICE_24K * (1 + change24kPercent / 100);
                const price24k_1g_raw = price24k_10g_raw / 10;
                const price24k_1g_change = (price24k_10g_raw - MOCK_BASE_PRICE_24K) / 10;
                
                currentRates['24k_1g'] = price24k_1g_raw; // Store 24K rate

                document.getElementById('price-24k-1g').textContent = formatCurrency(price24k_1g_raw);
                document.getElementById('price-24k-10g').textContent = formatCurrency(price24k_10g_raw);
                document.getElementById('change-24k').innerHTML = formatChange(price24k_1g_change);

                // 22K Gold Calculations
                const change22kPercent = MOCK_OVERVIEW_CHANGE['22k'];
                const price22k_10g_raw = MOCK_BASE_PRICE_22K * (1 + change22kPercent / 100);
                const price22k_1g_raw = price22k_10g_raw / 10;
                const price22k_1g_change = (price22k_10g_raw - MOCK_BASE_PRICE_22K) / 10;

                currentRates['22k_1g'] = price22k_1g_raw; // Store 22K rate

                document.getElementById('price-22k-1g').textContent = formatCurrency(price22k_1g_raw);
                document.getElementById('price-22k-10g').textContent = formatCurrency(price22k_10g_raw);
                document.getElementById('change-22k').innerHTML = formatChange(price22k_1g_change);
                
                // Calculate and store other carat rates based on 24K price
                const p24k = currentRates['24k_1g'];
                currentRates['18k_1g'] = p24k * CARAT_PURITY_MAP[18];
                currentRates['14k_1g'] = p24k * CARAT_PURITY_MAP[14];


                // Silver Calculations (Only for display, not used in gold calculator)
                const changeSilverPercent = MOCK_OVERVIEW_CHANGE['silver'];
                const priceSilver_1g_raw = MOCK_BASE_PRICE_SILVER * (1 + changeSilverPercent / 100);
                const priceSilver_1kg_raw = priceSilver_1g_raw * 1000;
                const priceSilver_1g_change = (priceSilver_1g_raw - MOCK_BASE_PRICE_SILVER);

                document.getElementById('price-silver-1g').textContent = formatCurrency(priceSilver_1g_raw);
                document.getElementById('price-silver-1kg').textContent = formatCurrency(priceSilver_1kg_raw);
                document.getElementById('change-silver').innerHTML = formatChange(priceSilver_1g_change);
            }

            /**
             * Renders the city-wise prices table.
             */
            function renderCityPrices() {
                const tableBody = document.getElementById('city-prices-body');
                tableBody.innerHTML = '';

                CITY_PRICES.forEach(data => {
                    // Calculate city-specific prices based on base gold price and city factor
                    const city_24k_10g = (MOCK_BASE_PRICE_24K * data.base) * (1 + data.change / 100);
                    const city_22k_10g = (MOCK_BASE_PRICE_22K * data.base) * (1 + data.change / 100);

                    // Calculate the daily change value (difference between current city price and city's base price)
                    const change24k = city_24k_10g - (MOCK_BASE_PRICE_24K * data.base);
                    const change22k = city_22k_10g - (MOCK_BASE_PRICE_22K * data.base);
                    
                    const row = `
                        <tr class="hover:bg-gray-50">
                            <td class="px-4 py-3 whitespace-nowrap text-sm font-medium text-indigo-700 sticky left-0 bg-white">${data.city}</td>
                            <td class="px-4 py-3 whitespace-nowrap text-sm text-gray-900 text-right font-medium">${formatCurrency(city_24k_10g)}</td>
                            <td class="px-4 py-3 whitespace-nowrap text-sm text-gray-500 text-right">${formatChange(change24k)}</td>
                            <td class="px-4 py-3 whitespace-nowrap text-sm text-gray-900 text-right font-medium">${formatCurrency(city_22k_10g)}</td>
                            <td class="px-4 py-3 whitespace-nowrap text-sm text-gray-500 text-right">${formatChange(change22k)}</td>
                        </tr>
                    `;
                    tableBody.insertAdjacentHTML('beforeend', row);
                });
            }

            /**
             * Renders the historical price chart using Chart.js.
             */
            function renderHistoricalChart() {
                generateMockHistoricalData(); // Generate data first

                const ctx = document.getElementById('historicalChart').getContext('2d');
                
                const chartConfig = {
                    type: 'line',
                    data: {
                        labels: MOCK_HISTORICAL_DATA.labels,
                        datasets: [{
                            label: '24K Gold Rate (â‚¹/10g)',
                            data: MOCK_HISTORICAL_DATA.prices,
                            borderColor: 'rgb(202, 138, 4)', // Amber-700
                            backgroundColor: 'rgba(251, 191, 36, 0.2)', // Amber-400 transparent fill
                            tension: 0.2, // Smooth line
                            pointRadius: 2,
                            pointBackgroundColor: 'rgb(202, 138, 4)',
                            fill: true
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false, // Important for responsive canvas container
                        plugins: {
                            legend: { display: false },
                            title: { display: false }
                        },
                        scales: {
                            y: {
                                title: {
                                    display: true,
                                    text: 'Price in INR (â‚¹)',
                                    font: { size: 14 }
                                },
                                beginAtZero: false,
                                grid: { color: 'rgba(0,0,0,0.05)' }
                            },
                            x: {
                                title: {
                                    display: true,
                                    text: 'Last 30 Days',
                                    font: { size: 14 }
                                },
                                grid: { display: false }
                            }
                        }
                    }
                };

                new Chart(ctx, chartConfig);
            }

            /**
             * Renders the mock YouTube updates section.
             */
            function renderYoutubeUpdates() {
                const ytGrid = document.getElementById('youtube-mock-grid');
                ytGrid.innerHTML = '';

                MOCK_YOUTUBE_VIDEOS.forEach((video) => {
                    const placeholderText = encodeURIComponent(video.title);
                    const thumbnailUrl = `https://placehold.co/400x225/A020F0/ffffff?text=${placeholderText.substring(0, 30)}...`;

                    const videoHtml = `
                        <a href="#" class="yt-mock-item bg-gray-50 rounded-xl overflow-hidden cursor-pointer transition duration-300 ease-in-out border border-gray-200">
                            <!-- Mock Thumbnail -->
                            <div class="relative w-full h-40 bg-gray-300 flex items-center justify-center overflow-hidden">
                                <img src="${thumbnailUrl}" onerror="this.src='https://placehold.co/400x225/111827/9ca3af?text=Video+Thumbnail';" alt="${video.title}" class="object-cover w-full h-full">
                                <div class="absolute inset-0 bg-black bg-opacity-30 flex items-center justify-center">
                                    <svg class="w-12 h-12 text-white opacity-90" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM9.555 7.168A1 1 0 008 8v4a1 1 0 001.555.832l3-2a1 1 0 000-1.664l-3-2z" clip-rule="evenodd"></path></svg>
                                </div>
                            </div>
                            
                            <div class="p-4">
                                <h4 class="text-base font-semibold text-gray-900 mb-1 leading-snug">${video.title}</h4>
                                <p class="text-sm text-gray-600">${video.channel}</p>
                                <p class="text-xs text-gray-400 mt-1">${video.views} Views â€¢ 2 Days Ago</p>
                            </div>
                        </a>
                    `;
                    ytGrid.insertAdjacentHTML('beforeend', videoHtml);
                });
            }
            
            /**
             * Calculates the estimated price based on user inputs.
             */
            function calculatePrice() {
                const weightInput = document.getElementById('weight-input');
                const caratSelect = document.getElementById('carat-select');
                const resultElement = document.getElementById('final-price');
                
                const weight = parseFloat(weightInput.value);
                const carat = caratSelect.value;

                // Basic input validation
                if (isNaN(weight) || weight <= 0) {
                    resultElement.textContent = 'Invalid Weight';
                    resultElement.classList.add('text-red-600');
                    return;
                }
                
                resultElement.classList.remove('text-red-600');

                let ratePerGram = 0;

                if (carat === '24') {
                    ratePerGram = currentRates['24k_1g'];
                } else if (carat === '22') {
                    ratePerGram = currentRates['22k_1g'];
                } else if (carat === '18') {
                    ratePerGram = currentRates['18k_1g'];
                } else if (carat === '14') {
                    ratePerGram = currentRates['14k_1g'];
                } else {
                    ratePerGram = currentRates['24k_1g'] * (parseFloat(carat) / 24); // Fallback generic calculation
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
                const timeString = now.toLocaleTimeString('en-IN', {
                    hour: '2-digit',
                    minute: '2-digit',
                    second: '2-digit'
                }) + ' IST';
                const dateString = now.toLocaleDateString('en-IN', {
                    year: 'numeric',
                    month: 'short',
                    day: 'numeric'
                });

                document.getElementById('current-time').textContent = `${dateString} | ${timeString}`;
            }

            // --- Initialization ---
            window.onload = function() {
                renderOverview();
                renderCityPrices();
                renderHistoricalChart();
                renderYoutubeUpdates();

                // Initial time update and set interval for real-time clock
                updateTime();
                setInterval(updateTime, 1000);
                
                // Calculate default price on load
                calculatePrice();

                // Attach event listeners to inputs so calculation runs automatically
                document.getElementById('weight-input').addEventListener('input', calculatePrice);
                document.getElementById('carat-select').addEventListener('change', calculatePrice);
            };
        </script>

    </body>
    </html>
    

