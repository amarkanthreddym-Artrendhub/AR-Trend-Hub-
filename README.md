<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>AR TREND HUB | Commodity & Analysis</title>

  <!-- Tailwind CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Chart.js CDN -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js@3.7.1/dist/chart.min.js"></script>

  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');
    :root { --bg:#f7f9fc; --indigo:#4f46e5; }
    body {
      font-family: 'Inter', sans-serif;
      background-color: var(--bg);
    }
    .price-card {
      box-shadow: 0 4px 6px -1px rgba(0,0,0,0.08), 0 2px 4px -2px rgba(0,0,0,0.06);
      transition: transform 0.25s ease;
    }
    .price-card:hover { transform: translateY(-4px); }
    .up-trend { color: #059669; } /* green */
    .down-trend { color: #dc2626; } /* red */
    .yt-mock-item:hover {
      box-shadow: 0 10px 15px -3px rgba(0,0,0,0.08), 0 4px 6px -4px rgba(0,0,0,0.06);
    }
    .table-container { max-width:100%; overflow-x:auto; -webkit-overflow-scrolling:touch; }
    /* Sticky first column in table */
    .sticky-col { position: sticky; left: 0; z-index: 10; background: white; }
    #calculation-result { min-height: 80px; }
  </style>
</head>
<body>
  <header class="bg-indigo-700 text-white p-4 sm:p-6 shadow-lg">
    <div class="max-w-7xl mx-auto flex flex-col sm:flex-row justify-between items-start sm:items-center">
      <h1 class="text-2xl sm:text-3xl font-bold tracking-tight">
        <span class="text-yellow-400">AR TREND</span> HUB
      </h1>
      <div id="last-updated" class="text-sm mt-2 sm:mt-0 opacity-80">
        Last Updated: <span id="current-time">--</span>
      </div>
    </div>
  </header>

  <main class="max-w-7xl mx-auto p-4 sm:p-6 lg:p-8">
    <!-- Overview -->
    <section class="mb-10">
      <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-4">Today's Commodity Prices in India (₹/Gram)</h2>
      <div id="overview-cards" class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <!-- 24K -->
        <div id="card-24k" class="price-card bg-white p-6 rounded-xl border-t-4 border-yellow-500">
          <h3 class="text-lg font-semibold text-gray-500 mb-2">24 Karat Gold (99.9% Pure)</h3>
          <div class="flex items-end justify-between">
            <p class="text-3xl font-bold text-gray-900">₹<span id="price-24k-1g">0</span></p>
            <div class="text-right">
              <span id="change-24k" class="text-sm font-medium"></span>
              <span class="text-xs text-gray-500 block">per gram</span>
            </div>
          </div>
          <div class="mt-4 text-sm text-gray-500">10 Gram: ₹<span id="price-24k-10g">0</span></div>
        </div>

        <!-- 22K -->
        <div id="card-22k" class="price-card bg-white p-6 rounded-xl border-t-4 border-amber-500">
          <h3 class="text-lg font-semibold text-gray-500 mb-2">22 Karat Gold (Jewellery)</h3>
          <div class="flex items-end justify-between">
            <p class="text-3xl font-bold text-gray-900">₹<span id="price-22k-1g">0</span></p>
            <div class="text-right">
              <span id="change-22k" class="text-sm font-medium"></span>
              <span class="text-xs text-gray-500 block">per gram</span>
            </div>
          </div>
          <div class="mt-4 text-sm text-gray-500">10 Gram: ₹<span id="price-22k-10g">0</span></div>
        </div>

        <!-- Silver -->
        <div id="card-silver" class="price-card bg-white p-6 rounded-xl border-t-4 border-gray-400">
          <h3 class="text-lg font-semibold text-gray-500 mb-2">Silver Price</h3>
          <div class="flex items-end justify-between">
            <p class="text-3xl font-bold text-gray-900">₹<span id="price-silver-1g">0</span></p>
            <div class="text-right">
              <span id="change-silver" class="text-sm font-medium"></span>
              <span class="text-xs text-gray-500 block">per gram</span>
            </div>
          </div>
          <div class="mt-4 text-sm text-gray-500">1 Kg: ₹<span id="price-silver-1kg">0</span></div>
        </div>
      </div>
    </section>

    <!-- Calculator -->
    <section class="mb-10 p-6 bg-white rounded-xl shadow-lg border-t-4 border-indigo-500">
      <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-6 flex items-center">
        <svg class="w-6 h-6 mr-2 text-indigo-600" fill="none" stroke="currentColor" viewBox="0 0 24 24"
             xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
             d="M9 7h6m0 10v-3m-3 3h.01M9 17h.01M12 17h.01M9 14h.01M12 14h.01M15 14h.01M12 10h.01M15 10h.01M12 7h.01M15 7h.01M7 7v10m10-10v10m-3-13h-4a2 2 0 00-2 2v10a2 2 0 002 2h4a2 2 0 002-2V9a2 2 0 00-2-2z"></path></svg>
        Gold Price Estimate Calculator
      </h2>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-6 items-center">
        <div>
          <label for="weight-input" class="block text-sm font-medium text-gray-700 mb-2">Enter Weight (in Grams)</label>
          <input type="number" id="weight-input" value="10" min="0.01" step="0.01"
                 class="w-full p-3 border border-gray-300 rounded-lg focus:ring-yellow-500 focus:border-yellow-500 transition duration-150"
                 placeholder="e.g., 5, 10, 50">
        </div>

        <div>
          <label for="carat-select" class="block text-sm font-medium text-gray-700 mb-2">Select Purity (Carat)</label>
          <select id="carat-select" class="w-full p-3 border border-gray-300 rounded-lg bg-white focus:ring-yellow-500 focus:border-yellow-500 transition duration-150">
            <option value="24">24 Karat (99.9% Pure)</option>
            <option value="22" selected>22 Karat (Jewellery Standard)</option>
            <option value="18">18 Karat</option>
            <option value="14">14 Karat</option>
          </select>
        </div>

        <div class="self-end pt-2 md:pt-0">
          <button id="calc-btn" class="w-full bg-yellow-500 hover:bg-yellow-600 text-indigo-900 font-bold py-3 px-4 rounded-lg shadow-md transition duration-200 ease-in-out">
            Calculate Price
          </button>
        </div>
      </div>

      <div id="calculation-result" class="mt-6 p-4 bg-yellow-50 border-l-4 border-yellow-500 text-gray-800 rounded-lg">
        <p class="text-sm font-medium">Estimated Price:</p>
        <p class="text-3xl font-extrabold text-indigo-700 mt-1">₹ <span id="final-price">0</span></p>
        <p class="text-xs text-gray-500 mt-2">Note: Calculation is based on the indicative rate displayed above, excluding making charges and taxes (GST/TCS).</p>
      </div>
    </section>

    <!-- Historical Chart -->
    <section class="mb-10 p-6 bg-white rounded-xl shadow-lg border-t-4 border-yellow-700">
      <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-6 flex items-center">
        <svg class="w-6 h-6 mr-2 text-yellow-700" fill="none" stroke="currentColor" viewBox="0 0 24 24"
             xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
             d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6"></path></svg>
        Historical Price Trend: 24K Gold (30 Days)
      </h2>
      <div class="h-80 w-full">
        <canvas id="historicalChart"></canvas>
      </div>
    </section>

    <!-- City-Wise Table -->
    <section class="mb-10">
      <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-4">Gold Rate Today in Major Indian Cities (10 Grams)</h2>
      <div class="table-container bg-white rounded-xl shadow overflow-hidden">
        <table class="min-w-full divide-y divide-gray-200">
          <thead class="bg-gray-50">
            <tr>
              <th class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider sticky left-0 z-10 bg-gray-50">City</th>
              <th class="px-4 py-3 text-right text-xs font-medium text-gray-500 uppercase tracking-wider">24K (₹)</th>
              <th class="px-4 py-3 text-right text-xs font-medium text-gray-500 uppercase tracking-wider">Change</th>
              <th class="px-4 py-3 text-right text-xs font-medium text-gray-500 uppercase tracking-wider">22K (₹)</th>
              <th class="px-4 py-3 text-right text-xs font-medium text-gray-500 uppercase tracking-wider">Change</th>
            </tr>
          </thead>
          <tbody id="city-prices-body" class="bg-white divide-y divide-gray-200"></tbody>
        </table>
      </div>
      <p class="text-sm text-gray-500 mt-2 p-2">
        <span class="font-bold">*Note:</span> Prices are indicative and exclude GST, TCS, and making charges.
      </p>
    </section>

    <!-- Mock YouTube -->
    <section class="mt-12 bg-white p-6 rounded-xl shadow-lg">
      <h2 class="text-xl sm:text-2xl font-semibold text-gray-800 mb-6 flex items-center">
        <svg class="w-6 h-6 mr-2 text-red-600" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM9.555 7.168A1 1 0 008 8v4a1 1 0 001.555.832l3-2a1 1 0 000-1.664l-3-2z" clip-rule="evenodd"></path></svg>
        Gold Price Analysis & YouTube Updates
      </h2>

      <div id="youtube-mock-grid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6"></div>

      <div class="text-center mt-6">
        <a href="#" class="inline-flex items-center justify-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-red-600 hover:bg-red-700 transition duration-150">
          View More Video Analysis
        </a>
      </div>
    </section>

  </main>

  <footer class="bg-gray-100 mt-10 p-4 sm:p-6 text-center text-gray-600 text-xs">
    &copy; 2025 AR TREND HUB. Data Simulated for Demonstration Purposes.
  </footer>

  <script>
    // Global rates holder (per gram)
    const currentRates = {
      '24k_1g': 0,
      '22k_1g': 0,
      '18k_1g': 0,
      '14k_1g': 0
    };

    // Mock base prices (per 10g) - you can replace these with API values later
    const MOCK_BASE_PRICE_24K = 125120; // per 10g
    const MOCK_BASE_PRICE_22K = 114690; // per 10g
    const MOCK_BASE_PRICE_SILVER = 930; // per 10g => ~93,000 per kg

    // Mock percentage changes (for display, not real)
    const MOCK_OVERVIEW_CHANGE = {
      '24k': 0.15, // percent for 24K
      '22k': 0.12,
      'silver': -0.45
    };

    const CARAT_PURITY_MAP = { 24:1.00, 22:22/24, 18:18/24, 14:14/24 };

    const CITY_PRICES = [
      { city: "Mumbai", base: 1.00, change: -0.15 },
      { city: "Delhi", base: 1.001, change: 0.05 },
      { city: "Chennai", base: 1.004, change: 0.22 },
      { city: "Kolkata", base: 0.998, change: -0.10 },
      { city: "Bangalore", base: 1.00, change: 0.15 },
      { city: "Hyderabad", base: 1.002, change: 0.00 },
      { city: "Ahmedabad", base: 1.00, change: 0.18 },
      { city: "Jaipur", base: 1.001, change: -0.05 },
      { city: "Pune", base: 0.999, change: -0.12 }
    ];

    const MOCK_YOUTUBE_VIDEOS = [
      { title: "Gold Price Forecast: Will Yellow Metal hit ₹70,000 by Diwali?", channel: "AR TREND HUB", views: "1.2M" },
      { title: "Silver Price Analysis: Is the White Metal a better Buy than Gold Today?", channel: "AR TREND HUB", views: "450K" },
      { title: "How to Invest in Digital Gold vs SGBs (Sovereign Gold Bonds)", channel: "AR TREND HUB", views: "88K" },
      { title: "Global Market Impact on Indian Gold Rates (US Fed Decision Explained)", channel: "AR TREND HUB", views: "600K" }
    ];

    // Historical data buffer
    const MOCK_HISTORICAL_DATA = { labels: [], prices: [] };

    // Utility: format numbers for INR without currency symbol (we add symbol in HTML)
    const formatCurrency = (value) => {
      if (value === null || isNaN(value)) return '0';
      return Number(value).toLocaleString('en-IN', { minimumFractionDigits: 0, maximumFractionDigits: 0 });
    };

    // Format change: absolute and color arrow; show two decimals
    const formatChange = (changeValue, showPercent=false, baseValue=null) => {
      const isPositive = changeValue >= 0;
      const arrow = isPositive ? '▲' : '▼';
      const cls = isPositive ? 'up-trend' : 'down-trend';
      const absVal = Math.abs(changeValue);
      if (showPercent && baseValue) {
        const pct = (absVal / baseValue) * 100;
        return `<span class="${cls}">${arrow} ${absVal.toFixed(2)} (${pct.toFixed(2)}%)</span>`;
      }
      return `<span class="${cls}">${arrow} ${absVal.toFixed(2)}</span>`;
    };

    // Generate mock historical 30-day series for 24K per 10g
    function generateMockHistoricalData() {
      MOCK_HISTORICAL_DATA.labels = [];
      MOCK_HISTORICAL_DATA.prices = [];
      const days = 30;
      const endDate = new Date();
      // Start price: a bit lower than today's mock base
      const startPrice = MOCK_BASE_PRICE_24K * 0.95;
      let price = startPrice;

      // daily trend to reach near base over period
      const dailyTrend = (MOCK_BASE_PRICE_24K - startPrice) / days;

      for (let i = 0; i < days; i++) {
        const d = new Date(endDate);
        d.setDate(endDate.getDate() - (days - 1 - i));
        MOCK_HISTORICAL_DATA.labels.push(d.toLocaleDateString('en-IN', { day: '2-digit', month: 'short' }));

        // random fluctuation ±250
        const fluct = (Math.random() - 0.5) * 500;
        price = Math.max(price + dailyTrend + fluct, MOCK_BASE_PRICE_24K * 0.9);
        MOCK_HISTORICAL_DATA.prices.push(Math.round(price / 10) * 10);
      }

      // align last price with overview (apply change)
      const lastPrice = Math.round(MOCK_BASE_PRICE_24K * (1 + (MOCK_OVERVIEW_CHANGE['24k'] / 100)) / 10) * 10;
      MOCK_HISTORICAL_DATA.prices[MOCK_HISTORICAL_DATA.prices.length - 1] = lastPrice;
    }

    // Render Overview cards and set currentRates (per gram)
    function renderOverview() {
      // 24K
      const change24kPct = MOCK_OVERVIEW_CHANGE['24k'];
      const price24k_10g_raw = MOCK_BASE_PRICE_24K * (1 + change24kPct / 100);
      const price24k_1g_raw = price24k_10g_raw / 10;
      const price24k_1g_change = (price24k_10g_raw - MOCK_BASE_PRICE_24K) / 10;

      currentRates['24k_1g'] = price24k_1g_raw;
      document.getElementById('price-24k-1g').textContent = formatCurrency(price24k_1g_raw);
      document.getElementById('price-24k-10g').textContent = formatCurrency(price24k_10g_raw);
      document.getElementById('change-24k').innerHTML = formatChange(price24k_1g_change, true, price24k_1g_raw);

      // 22K
      const change22kPct = MOCK_OVERVIEW_CHANGE['22k'];
      const price22k_10g_raw = MOCK_BASE_PRICE_22K * (1 + change22kPct / 100);
      const price22k_1g_raw = price22k_10g_raw / 10;
      const price22k_1g_change = (price22k_10g_raw - MOCK_BASE_PRICE_22K) / 10;

      currentRates['22k_1g'] = price22k_1g_raw;
      document.getElementById('price-22k-1g').textContent = formatCurrency(price22k_1g_raw);
      document.getElementById('price-22k-10g').textContent = formatCurrency(price22k_10g_raw);
      document.getElementById('change-22k').innerHTML = formatChange(price22k_1g_change, true, price22k_1g_raw);

      // other carat calculations derived from 24K per gram
      const p24 = currentRates['24k_1g'];
      currentRates['18k_1g'] = p24 * CARAT_PURITY_MAP[18];
      currentRates['14k_1g'] = p24 * CARAT_PURITY_MAP[14];

      // Silver
      const changeSilverPct = MOCK_OVERVIEW_CHANGE['silver'];
      const priceSilver_1g_raw = MOCK_BASE_PRICE_SILVER * (1 + changeSilverPct / 100);
      const priceSilver_1kg_raw = priceSilver_1g_raw * 1000;
      const priceSilver_1g_change = (priceSilver_1g_raw - MOCK_BASE_PRICE_SILVER);

      document.getElementById('price-silver-1g').textContent = formatCurrency(priceSilver_1g_raw);
      document.getElementById('price-silver-1kg').textContent = formatCurrency(priceSilver_1kg_raw);
      document.getElementById('change-silver').innerHTML = formatChange(priceSilver_1g_change, true, priceSilver_1g_raw);
    }

    // Render city-wise table
    function renderCityPrices() {
      const tbody = document.getElementById('city-prices-body');
      tbody.innerHTML = '';

      CITY_PRICES.forEach(data => {
        const city_24k_10g = (MOCK_BASE_PRICE_24K * data.base) * (1 + data.change / 100);
        const city_22k_10g = (MOCK_BASE_PRICE_22K * data.base) * (1 + data.change / 100);

        const change24k = city_24k_10g - (MOCK_BASE_PRICE_24K * data.base);
        const change22k = city_22k_10g - (MOCK_BASE_PRICE_22K * data.base);

        const row = `
          <tr class="hover:bg-gray-50">
            <td class="px-4 py-3 whitespace-nowrap text-sm font-medium text-indigo-700 sticky-col">${data.city}</td>
            <td class="px-4 py-3 whitespace-nowrap text-sm text-gray-900 text-right font-medium">₹${formatCurrency(city_24k_10g)}</td>
            <td class="px-4 py-3 whitespace-nowrap text-sm text-gray-500 text-right">${formatChange(change24k, true, (MOCK_BASE_PRICE_24K * data.base))}</td>
            <td class="px-4 py-3 whitespace-nowrap text-sm text-gray-900 text-right font-medium">₹${formatCurrency(city_22k_10g)}</td>
            <td class="px-4 py-3 whitespace-nowrap text-sm text-gray-500 text-right">${formatChange(change22k, true, (MOCK_BASE_PRICE_22K * data.base))}</td>
          </tr>
        `;
        tbody.insertAdjacentHTML('beforeend', row);
      });
    }

    // Render historical chart using Chart.js
    function renderHistoricalChart() {
      generateMockHistoricalData();
      const ctx = document.getElementById('historicalChart').getContext('2d');

      // Destroy previous chart if exists to avoid duplicates
      if (window._historicalChart) window._historicalChart.destroy();

      window._historicalChart = new Chart(ctx, {
        type: 'line',
        data: {
          labels: MOCK_HISTORICAL_DATA.labels,
          datasets: [{
            label: '24K Gold Rate (₹/10g)',
            data: MOCK_HISTORICAL_DATA.prices,
            borderColor: 'rgb(202,138,4)',
            backgroundColor: 'rgba(251,191,36,0.18)',
            tension: 0.25,
            pointRadius: 2,
            fill: true
          }]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          plugins: { legend: { display: false }, title: { display: false } },
          scales: {
            y: {
              title: { display: true, text: 'Price in INR (₹)', font: { size: 14 } },
              beginAtZero: false,
              grid: { color: 'rgba(0,0,0,0.05)' }
            },
            x: {
              title: { display: true, text: 'Last 30 Days', font: { size: 14 } },
              grid: { display: false }
            }
          }
        }
      });
    }

    // Render mock YouTube grid
    function renderYoutubeUpdates() {
      const ytGrid = document.getElementById('youtube-mock-grid');
      ytGrid.innerHTML = '';
      MOCK_YOUTUBE_VIDEOS.forEach(video => {
        const placeholderText = encodeURIComponent(video.title);
        const thumbnailUrl = `https://placehold.co/400x225/A020F0/ffffff?text=${placeholderText.substring(0, 30)}...`;
        const html = `
          <a href="#" class="yt-mock-item bg-gray-50 rounded-xl overflow-hidden cursor-pointer transition duration-300 ease-in-out border border-gray-200">
            <div class="relative w-full h-40 bg-gray-300 flex items-center justify-center overflow-hidden">
              <img src="${thumbnailUrl}" onerror="this.src='https://placehold.co/400x225/111827/9ca3af?text=Video+Thumbnail';" alt="${video.title}" class="object-cover w-full h-full">
              <div class="absolute inset-0 bg-black bg-opacity-30 flex items-center justify-center">
                <svg class="w-12 h-12 text-white opacity-90" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM9.555 7.168A1 1 0 008 8v4a1 1 0 001.555.832l3-2a1 1 0 000-1.664l-3-2z" clip-rule="evenodd"></path></svg>
              </div>
            </div>
            <div class="p-4">
              <h4 class="text-base font-semibold text-gray-900 mb-1 leading-snug">${video.title}</h4>
              <p class="text-sm text-gray-600">${video.channel}</p>
              <p class="text-xs text-gray-400 mt-1">${video.views} Views • 2 Days Ago</p>
            </div>
          </a>`;
        ytGrid.insertAdjacentHTML('beforeend', html);
      });
    }

    // Calculator
    function calculatePrice() {
      const weightInput = document.getElementById('weight-input');
      const caratSelect = document.getElementById('carat-select');
      const resultElement = document.getElementById('final-price');

      const weight = parseFloat(weightInput.value);
      const carat = caratSelect.value;

      if (isNaN(weight) || weight <= 0) {
        resultElement.textContent = 'Invalid';
        resultElement.classList.add('text-red-600');
        return;
      }
      resultElement.classList.remove('text-red-600');

      let ratePerGram = 0;
      if (carat === '24') ratePerGram = currentRates['24k_1g'];
      else if (carat === '22') ratePerGram = currentRates['22k_1g'];
      else if (carat === '18') ratePerGram = currentRates['18k_1g'];
      else if (carat === '14') ratePerGram = currentRates['14k_1g'];
      else ratePerGram = currentRates['24k_1g'] * (parseFloat(carat) / 24);

      if (!ratePerGram || isNaN(ratePerGram)) {
        resultElement.textContent = 'Data Error';
        resultElement.classList.add('text-red-600');
        console.error('Rate per gram invalid:', ratePerGram);
        return;
      }

      const totalPrice = weight * ratePerGram;
      resultElement.textContent = formatCurrency(Math.round(totalPrice));
    }

    // Update clock/time display (India timezone assumption)
    function updateTime() {
      const now = new Date();
      const timeString = now.toLocaleTimeString('en-IN', { hour: '2-digit', minute: '2-digit', second: '2-digit' }) + ' IST';
      const dateString = now.toLocaleDateString('en-IN', { year: 'numeric', month: 'short', day: 'numeric' });
      document.getElementById('current-time').textContent = `${dateString} | ${timeString}`;
    }

    // Initialization on DOM ready
    document.addEventListener('DOMContentLoaded', () => {
      renderOverview();
      renderCityPrices();
      renderHistoricalChart();
      renderYoutubeUpdates();

      updateTime();
      setInterval(updateTime, 1000);

      // default calculation
      calculatePrice();

      // event bindings
      document.getElementById('weight-input').addEventListener('input', calculatePrice);
      document.getElementById('carat-select').addEventListener('change', calculatePrice);
      document.getElementById('calc-btn').addEventListener('click', calculatePrice);
    });
  </script>
</body>
</html>
