<!doctype html>

<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>AR TREND HUB — Live Gold Rates, Finance Updates & Job Alerts</title>
  <meta name="description" content="AR TREND HUB — Daily gold & silver rates, city-wise prices, credit cards, insurance comparison, bank rates, job alerts and useful financial tools. Updated daily at 10 AM." />
  <meta name="keywords" content="gold rate today, 22k gold rate, 24k gold rate, credit cards India, health insurance, job alerts, bank rates" />
  <style>
    :root{--accent:#0b63d6;--muted:#6b7280;--card:#ffffff;--bg:#f7fafc}
    *{box-sizing:border-box}
    body{font-family:Inter,ui-sans-serif,system-ui,-apple-system,Segoe UI,Roboto,Helvetica,Arial;line-height:1.5;margin:0;background:var(--bg);color:#0f172a}
    .container{max-width:1100px;margin:24px auto;padding:0 16px}
    header.site{background:#fff;border-radius:12px;padding:18px 20px;display:flex;align-items:center;gap:16px;box-shadow:0 6px 18px rgba(12,18,25,0.06)}
    .logo{display:flex;align-items:center;gap:12px}
    .logo .mark{width:56px;height:56px;border-radius:8px;background:linear-gradient(135deg,var(--accent),#05a);display:flex;align-items:center;justify-content:center;color:#fff;font-weight:700}
    nav{margin-left:auto}
    nav a{color:var(--muted);text-decoration:none;margin-left:12px;font-weight:600}
    .hero{display:grid;grid-template-columns:1fr 320px;gap:18px;margin-top:18px}
    .card{background:var(--card);border-radius:12px;padding:16px;box-shadow:0 6px 18px rgba(12,18,25,0.04)}
    .gold-today{display:flex;flex-direction:column;gap:8px}
    .gold-row{display:flex;justify-content:space-between;align-items:center;padding:10px 12px;border-radius:8px;background:#fbfdff;border:1px solid rgba(11,99,214,0.06)}
    .city-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-top:10px}
    table{width:100%;border-collapse:collapse}
    table th, table td{padding:8px;border-bottom:1px solid #eef2f7;text-align:left}
    h2{margin:0 0 8px 0}
    .small{font-size:13px;color:var(--muted)}
    .btn{display:inline-block;padding:9px 14px;border-radius:8px;background:var(--accent);color:#fff;text-decoration:none;font-weight:700}
    .two-col{display:grid;grid-template-columns:1fr 320px;gap:18px}
    .list-item{display:flex;justify-content:space-between;padding:10px;border-radius:8px;background:#fff;margin-bottom:8px}
    .tools{display:flex;gap:8px;flex-wrap:wrap}
    .tool-card{background:#fff;padding:12px;border-radius:10px;min-width:160px;flex:1}
    footer{margin-top:22px;text-align:center;color:var(--muted);padding:22px 0}
    .affiliate{background:#fff;padding:12px;border-radius:10px;box-shadow:0 6px 18px rgba(12,18,25,0.04)}
    @media (max-width:880px){.hero,.two-col{grid-template-columns:1fr} .city-grid{grid-template-columns:repeat(2,1fr)}}
  </style>
</head>
<body>
  <div class="container">
    <header class="site">
      <div class="logo">
        <div class="mark">AR</div>
        <div>
          <div style="font-weight:800">AR TREND HUB</div>
          <div class="small">Live Gold Rates • Jobs • Credit Cards • Insurance</div>
        </div>
      </div>
      <nav>
        <a href="#gold">Gold</a>
        <a href="#jobs">Jobs</a>
        <a href="#cards">Credit Cards</a>
        <a href="#insurance">Insurance</a>
        <a href="#banks">Bank Rates</a>
        <a href="#tools">Tools</a>
      </nav>
    </header><main class="hero">
  <section class="card gold-today" id="gold">
    <div style="display:flex;justify-content:space-between;align-items:center">
      <div>
        <h2>Today Gold Rate (Updated at 10:00 AM)</h2>
        <div class="small">Daily 22K & 24K gold price — city-wise comparison</div>
      </div>
      <div style="text-align:right">
        <div class="small">Last update:</div>
        <div id="lastUpdate" style="font-weight:700">--</div>
      </div>
    </div>

    <div class="gold-row" style="margin-top:12px">
      <div>
        <div class="small">22K Gold</div>
        <div id="gold22" style="font-size:20px;font-weight:800">₹ -- / gm</div>
      </div>
      <div>
        <div class="small">24K Gold</div>
        <div id="gold24" style="font-size:20px;font-weight:800">₹ -- / gm</div>
      </div>
      <div>
        <div class="small">Silver</div>
        <div id="silver" style="font-size:20px;font-weight:800">₹ -- / kg</div>
      </div>
    </div>

    <div style="margin-top:12px">
      <div class="small">City-wise Prices</div>
      <div class="city-grid" id="cityGrid">
        <div class="card" style="background:#fff;padding:10px">
          <div style="font-weight:700">Hyderabad</div>
          <div class="small">22K: <span id="hyd22">--</span> | 24K: <span id="hyd24">--</span></div>
        </div>
        <div class="card" style="background:#fff;padding:10px">
          <div style="font-weight:700">Mumbai</div>
          <div class="small">22K: <span id="mum22">--</span> | 24K: <span id="mum24">--</span></div>
        </div>
        <div class="card" style="background:#fff;padding:10px">
          <div style="font-weight:700">Delhi</div>
          <div class="small">22K: <span id="del22">--</span> | 24K: <span id="del24">--</span></div>
        </div>
        <div class="card" style="background:#fff;padding:10px">
          <div style="font-weight:700">Chennai</div>
          <div class="small">22K: <span id="che22">--</span> | 24K: <span id="che24">--</span></div>
        </div>
        <div class="card" style="background:#fff;padding:10px">
          <div style="font-weight:700">Bangalore</div>
          <div class="small">22K: <span id="ban22">--</span> | 24K: <span id="ban24">--</span></div>
        </div>
      </div>
    </div>

    <div style="margin-top:12px;display:flex;gap:8px;align-items:center">
      <a class="btn" href="#goldTable">View Full Table</a>
      <a class="btn" href="#" onclick="alert('Use EarnKaro profit link here')">Buy Gold Savings Plan</a>
    </div>

    <div style="margin-top:14px" class="affiliate">
      <div style="font-weight:700">10-Day Gold Price History</div>
      <table id="historyTable" style="margin-top:8px">
        <thead><tr><th>Date</th><th>22K</th><th>24K</th></tr></thead>
        <tbody>
          <tr><td>2025-12-12</td><td>₹5,250</td><td>₹5,700</td></tr>
          <tr><td>2025-12-11</td><td>₹5,240</td><td>₹5,690</td></tr>
          <tr><td>2025-12-10</td><td>₹5,260</td><td>₹5,710</td></tr>
          <tr><td>2025-12-09</td><td>₹5,230</td><td>₹5,680</td></tr>
          <tr><td>2025-12-08</td><td>₹5,210</td><td>₹5,660</td></tr>
        </tbody>
      </table>
    </div>
  </section>

  <aside>
    <div class="card">
      <h3 style="margin:0 0 8px 0">Top Credit Cards (Apply)</h3>
      <div class="list-item">
        <div>
          <div style="font-weight:700">Amazon Pay ICICI</div>
          <div class="small">Lifetime free • Best for shopping</div>
        </div>
        <div style="display:flex;flex-direction:column;gap:8px;align-items:flex-end">
          <a class="btn" href="#" onclick="openAffiliate('AMAZON_ICICI')">Apply</a>
          <div class="small">₹200–₹1200 per approval</div>
        </div>
      </div>

      <div class="list-item">
        <div>
          <div style="font-weight:700">SBI Cashback Card</div>
          <div class="small">Good for online spends</div>
        </div>
        <div style="display:flex;flex-direction:column;gap:8px;align-items:flex-end">
          <a class="btn" href="#" onclick="openAffiliate('SBI_CASH')">Apply</a>
          <div class="small">Simple cashback</div>
        </div>
      </div>

      <div class="list-item">
        <div>
          <div style="font-weight:700">HDFC Millennia</div>
          <div class="small">High rewards on shopping</div>
        </div>
        <div style="display:flex;flex-direction:column;gap:8px;align-items:flex-end">
          <a class="btn" href="#" onclick="openAffiliate('HDFC_MILL')">Apply</a>
          <div class="small">Great for online buyers</div>
        </div>
      </div>

    </div>

    <div style="margin-top:12px" class="card">
      <h3 style="margin:0 0 8px 0">Quick Tools</h3>
      <div class="tools">
        <div class="tool-card">
          <div style="font-weight:700">EMI Calculator</div>
          <div class="small">Find monthly EMI instantly</div>
          <div style="margin-top:8px"><a class="btn" href="#tools">Open</a></div>
        </div>
        <div class="tool-card">
          <div style="font-weight:700">SIP Calculator</div>
          <div class="small">Plan your SIP goals</div>
          <div style="margin-top:8px"><a class="btn" href="#tools">Open</a></div>
        </div>
      </div>
    </div>
  </aside>
</main>

<section style="margin-top:18px" class="two-col">
  <div class="card" id="cards">
    <h2>Credit Cards — Compare & Apply</h2>
    <p class="small">Choose a credit card based on your spending style. All apply links are affiliate links (EarnKaro / partner).</p>

    <div style="margin-top:12px">
      <div style="font-weight:700">Amazon Pay ICICI Credit Card</div>
      <div class="small">No annual fee, best for online shopping. Apply via EarnKaro link below.</div>
      <div style="margin-top:8px"><a class="btn" href="#" onclick="openAffiliate('AMAZON_ICICI')">Apply via EarnKaro</a></div>
    </div>

    <hr style="margin:12px 0;border:none;border-top:1px solid #eef2f7">

    <div>
      <div style="font-weight:700">SBI Cashback Card</div>
      <div class="small">Simple cashback on online spends.</div>
      <div style="margin-top:8px"><a class="btn" href="#" onclick="openAffiliate('SBI_CASH')">Apply via EarnKaro</a></div>
    </div>

    <hr style="margin:12px 0;border:none;border-top:1px solid #eef2f7">

    <div>
      <div style="font-weight:700">HDFC Millennia</div>
      <div class="small">Rewards on e-commerce & digital spends.</div>
      <div style="margin-top:8px"><a class="btn" href="#" onclick="openAffiliate('HDFC_MILL')">Apply via EarnKaro</a></div>
    </div>

  </div>

  <aside class="card" id="insurance">
    <h2>Insurance — Quick Compare</h2>
    <p class="small">Insurance protects you and your family. Always read policy documents before buying.</p>

    <div style="margin-top:10px">
      <div style="font-weight:700">Health Insurance (Family Floater)</div>
      <div class="small">Cashless hospitals, wide network. Compare plans and get quotes.</div>
      <div style="margin-top:8px"><a class="btn" href="#" onclick="openAffiliate('HEALTH_INS')">Compare Plans</a></div>
    </div>

    <div style="margin-top:12px">
      <div style="font-weight:700">Term Life Insurance</div>
      <div class="small">Low premium, high coverage. Good for income protection.</div>
      <div style="margin-top:8px"><a class="btn" href="#" onclick="openAffiliate('TERM_LIFE')">Check Premiums</a></div>
    </div>

  </aside>
</section>

<section style="margin-top:18px" class="card" id="jobs">
  <h2>Latest Job Notifications</h2>
  <div class="small">We update job notifications daily. Click the job to view full details and official apply link.</div>
  <div style="margin-top:12px">
    <div class="list-item">
      <div>
        <div style="font-weight:700">XYZ Bank PO Recruitment</div>
        <div class="small">Qualification: Graduate • Age: 21–30 • Last Date: 2026-01-15</div>
      </div>
      <div><a class="btn" href="#">View</a></div>
    </div>

    <div class="list-item">
      <div>
        <div style="font-weight:700">State Govt — Teacher Vacancy</div>
        <div class="small">Qualification: B.Ed • Age: 18–40 • Last Date: 2026-01-07</div>
      </div>
      <div><a class="btn" href="#">Apply</a></div>
    </div>
  </div>
</section>

<section style="margin-top:18px" class="card" id="banks">
  <h2>Latest Bank Interest Rates</h2>
  <p class="small">Updated weekly — compare FD, RD and savings rates from top banks.</p>
  <table style="margin-top:8px">
    <thead><tr><th>Bank</th><th>FD (1 Yr)</th><th>RD (1 Yr)</th><th>Savings</th></tr></thead>
    <tbody>
      <tr><td>SBI</td><td>6.80%</td><td>6.50%</td><td>2.70%</td></tr>
      <tr><td>HDFC</td><td>7.00%</td><td>6.75%</td><td>3.00%</td></tr>
      <tr><td>ICICI</td><td>6.95%</td><td>6.70%</td><td>3.00%</td></tr>
    </tbody>
  </table>
</section>

<section style="margin-top:18px" class="card" id="tools">
  <h2>Tools</h2>
  <div class="small">Free calculators to help your visitors — these pages bring consistent organic traffic.</div>
  <div style="margin-top:12px;display:grid;grid-template-columns:repeat(3,1fr);gap:12px">
    <div class="card">
      <div style="font-weight:700">EMI Calculator</div>
      <div class="small">Find monthly EMI for loans.</div>
      <div style="margin-top:8px"><a class="btn" href="#">Open</a></div>
    </div>
    <div class="card">
      <div style="font-weight:700">SIP Calculator</div>
      <div class="small">Plan SIP growth over time.</div>
      <div style="margin-top:8px"><a class="btn" href="#">Open</a></div>
    </div>
    <div class="card">
      <div style="font-weight:700">Gold Price Calculator</div>
      <div class="small">Calculate value for weight & purity.</div>
      <div style="margin-top:8px"><a class="btn" href="#">Open</a></div>
    </div>
  </div>
</section>

<footer>
  <div class="small">© 2025 AR TREND HUB — Daily gold rates, finance updates & job alerts</div>
  <div class="small" style="margin-top:8px">Disclaimer: This site contains affiliate links (EarnKaro). We may earn a commission if you apply through our links. Always read terms before applying.</div>
</footer>

  </div>  <script>
    // Replace these with your real EarnKaro links mapping
    const affiliateMap = {
      'AMAZON_ICICI': 'https://earnkaro.example/amazon_icici',
      'SBI_CASH': 'https://bitli.in/1dt8etW/sbi_cashback',
      'HDFC_MILL': 'https://earnkaro.example/hdfc_mill',
      'HEALTH_INS': 'https://earnkaro.example/health_ins',
      'TERM_LIFE': 'https://earnkaro.example/term_life'
    };

    function openAffiliate(key){
      const url = affiliateMap[key] || '#';
      if(url === '#'){ alert('Affiliate link not set yet.'); return }
      // open in new tab
      window.open(url,'_blank');
    }

    // Demo: populate gold fields (replace with real API or manual update routine)
    function populateGoldDemo(){
      const now = new Date();
      document.getElementById('lastUpdate').textContent = now.toLocaleString('en-IN');
      // example values (you will update these daily)
      const data = {
        gold22: '₹5,250', gold24: '₹5,700', silver: '₹65,000',
        hyd22: '₹5,250', hyd24: '₹5,700',
        mum22: '₹5,270', mum24: '₹5,720',
        del22: '₹5,240', del24: '₹5,690',
        che22: '₹5,260', che24: '₹5,710',
        ban22: '₹5,255', ban24: '₹5,705'
      };
      document.getElementById('gold22').textContent = data.gold22;
      document.getElementById('gold24').textContent = data.gold24;
      document.getElementById('silver').textContent = data.silver;
      ['hyd22','hyd24','mum22','mum24','del22','del24','che22','che24','ban22','ban24'].forEach(id=>{
        if(document.getElementById(id)) document.getElementById(id).textContent = data[id] || '--';
      })
    }

    // Call demo populate on load
    populateGoldDemo();

    // Helper: copy template to clipboard (for content editors)
    function copySectionText(selector){
      const el = document.querySelector(selector);
      if(!el) return; navigator.clipboard.writeText(el.innerText || el.textContent).then(()=>alert('Copied'));
    }
  </script></body>
</html>
