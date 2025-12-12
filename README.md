<!doctype html>

<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>AR TREND HUB — Live Gold Rates, Finance Offers & Job Alerts</title>
  <meta name="description" content="AR TREND HUB — Daily gold & silver rates, city-wise prices, credit cards, insurance comparison, bank rates, job alerts and useful financial tools. Updated daily at 10 AM." />
  <meta name="keywords" content="gold rate today, credit cards India, best credit cards, loans, EarnKaro, affiliate links" />
  <style>
    :root{--accent:#0b63d6;--muted:#6b7280;--card:#ffffff;--bg:#f7fafc}
    *{box-sizing:border-box}
    body{font-family:Inter,system-ui,Roboto,Helvetica,Arial;line-height:1.5;margin:0;background:var(--bg);color:#0f172a}
    .container{max-width:1100px;margin:18px auto;padding:0 16px}
    header.site{background:#fff;border-radius:12px;padding:14px 18px;display:flex;align-items:center;gap:12px;box-shadow:0 6px 18px rgba(12,18,25,0.04)}
    .logo{display:flex;align-items:center;gap:12px}
    .logo .mark{width:48px;height:48px;border-radius:8px;background:linear-gradient(135deg,var(--accent),#05a);display:flex;align-items:center;justify-content:center;color:#fff;font-weight:800}
    nav{margin-left:auto}
    nav a{color:var(--muted);text-decoration:none;margin-left:12px;font-weight:600}
    .hero{display:grid;grid-template-columns:1fr 320px;gap:18px;margin-top:18px}
    .card{background:var(--card);border-radius:12px;padding:14px;box-shadow:0 6px 18px rgba(12,18,25,0.04)}
    .gold-today{display:flex;flex-direction:column;gap:8px}
    .gold-row{display:flex;justify-content:space-between;align-items:center;padding:10px 12px;border-radius:8px;background:#fbfdff;border:1px solid rgba(11,99,214,0.06)}
    .city-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-top:10px}
    table{width:100%;border-collapse:collapse}
    table th, table td{padding:8px;border-bottom:1px solid #eef2f7;text-align:left}
    h2{margin:0 0 8px 0}
    .small{font-size:13px;color:var(--muted)}
    .btn{display:inline-block;padding:9px 12px;border-radius:8px;background:var(--accent);color:#fff;text-decoration:none;font-weight:700}
    .two-col{display:grid;grid-template-columns:1fr 320px;gap:18px}
    .list-item{display:flex;justify-content:space-between;padding:10px;border-radius:8px;background:#fff;margin-bottom:8px}
    .tools{display:flex;gap:8px;flex-wrap:wrap}
    .tool-card{background:#fff;padding:12px;border-radius:10px;min-width:160px;flex:1}
    .offer-card{display:flex;justify-content:space-between;align-items:center;padding:12px;border-radius:10px;background:#fff;margin-bottom:10px}
    footer{margin-top:22px;text-align:center;color:var(--muted);padding:18px 0}
    .affiliate{background:#fff;padding:12px;border-radius:10px;box-shadow:0 6px 18px rgba(12,18,25,0.04)}
    .pill{background:#f1f9ff;padding:6px 8px;border-radius:999px;color:var(--accent);font-weight:700}
    @media (max-width:880px){.hero,.two-col{grid-template-columns:1fr}.city-grid{grid-template-columns:repeat(2,1fr)}nav{display:none}}
  </style>
</head>
<body>
  <div class="container">
    <header class="site">
      <div class="logo">
        <div class="mark">AR</div>
        <div>
          <div style="font-weight:800">AR TREND HUB</div>
          <div class="small">Live Gold • Credit Cards • Loans • Deals</div>
        </div>
      </div>
      <nav>
        <a href="#gold">Gold</a>
        <a href="#cards">Cards</a>
        <a href="#loans">Loans</a>
        <a href="#deals">Deals</a>
        <a href="#jobs">Jobs</a>
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
      <a class="btn" href="#cards">Top Cards</a>
      <a class="btn" href="#deals">Today Deals</a>
    </div>

  </section>

  <aside>
    <div class="card">
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

    <div style="margin-top:12px" class="card">
      <h3 style="margin:0 0 8px 0">Top Earning Quick Picks</h3>
      <div class="small">High commission cards & loans you can promote today</div>
      <div style="margin-top:10px">
        <div class="offer-card"><div>Axis Flipkart Credit Card</div><div class="pill">Up to ₹2380</div></div>
        <div class="offer-card"><div>HDFC Millennia / Regalia</div><div class="pill">₹2000+</div></div>
        <div class="offer-card"><div>IDFC First Dual Card</div><div class="pill">Up to ₹2450</div></div>
        <div class="offer-card"><div>HDFC Instant Loan</div><div class="pill">Up to ₹6000</div></div>
      </div>
    </div>
  </aside>
</main>

<!-- CREDIT CARDS SECTION -->
<section style="margin-top:18px" class="card" id="cards">
  <h2>Credit Cards — Top Offers</h2>
  <p class="small">Click Apply to generate the EarnKaro profit link (use the partner page in EarnKaro and copy the link here).</p>

  <!-- Cards list: each row calls openAffiliate(key) where you will paste the EarnKaro profit link in the affiliateMap below -->
  <div style="margin-top:12px">
    <!-- Example Card Row -->
    <div class="offer-card">
      <div>
        <div style="font-weight:700">Axis Flipkart Credit Card</div>
        <div class="small">Best for Flipkart shoppers — eligibility applies</div>
      </div>
      <div style="display:flex;flex-direction:column;gap:8px;align-items:flex-end">
        <a class="btn" href="#" onclick="openAffiliate('AXIS_FLIP')">Apply</a>
        <div class="small">Up to ₹2380</div>
      </div>
    </div>

    <div class="offer-card">
      <div>
        <div style="font-weight:700">Axis Samsung Signature Credit Card</div>
        <div class="small">High benefits for Samsung purchases</div>
      </div>
      <div style="display:flex;flex-direction:column;gap:8px;align-items:flex-end">
        <a class="btn" href="#" onclick="openAffiliate('AXIS_SAMS')">Apply</a>
        <div class="small">₹2380</div>
      </div>
    </div>

    <div class="offer-card">
      <div>
        <div style="font-weight:700">HDFC Millennia / Regalia / Pixel</div>
        <div class="small">Great for online & travel spends</div>
      </div>
      <div style="display:flex;flex-direction:column;gap:8px;align-items:flex-end">
        <a class="btn" href="#" onclick="openAffiliate('HDFC_MILL')">Apply</a>
        <div class="small">₹2000+</div>
      </div>
    </div>

    <div class="offer-card">
      <div>
        <div style="font-weight:700">IDFC First Dual / Power Cards</div>
        <div class="small">Good for rewards & fuel</div>
      </div>
      <div style="display:flex;flex-direction:column;gap:8px;align-items:flex-end">
        <a class="btn" href="#" onclick="openAffiliate('IDFC_POWER')">Apply</a>
        <div class="small">Up to ₹2450</div>
      </div>
    </div>

    <div class="offer-card">
      <div>
        <div style="font-weight:700">IndusInd Eazy / Legend / Platinum</div>
        <div class="small">Multiple variants — list on site</div>
      </div>
      <div style="display:flex;flex-direction:column;gap:8px;align-items:flex-end">
        <a class="btn" href="#" onclick="openAffiliate('INDUSIND_EAZY')">Apply</a>
        <div class="small">₹400–₹1725</div>
      </div>
    </div>

    <div class="offer-card">
      <div>
        <div style="font-weight:700">AU Altura / LIT Credit Card</div>
        <div class="small">Good payouts for new users</div>
      </div>
      <div style="display:flex;flex-direction:column;gap:8px;align-items:flex-end">
        <a class="btn" href="#" onclick="openAffiliate('AU_ALT')">Apply</a>
        <div class="small">₹1540</div>
      </div>
    </div>

    <div class="offer-card">
      <div>
        <div style="font-weight:700">Yes Bank / BOB / RBL Cards</div>
        <div class="small">Good mid-tier payouts</div>
      </div>
      <div style="display:flex;flex-direction:column;gap:8px;align-items:flex-end">
        <a class="btn" href="#" onclick="openAffiliate('YES_RBL_BOB')">Apply</a>
        <div class="small">₹900–₹1500</div>
      </div>
    </div>

  </div>

  <div style="margin-top:14px" class="affiliate">
    <div style="font-weight:700">Pro tip:</div>
    <div class="small">Create separate pages or short videos for each card (e.g., "Axis Flipkart Card — Benefits & Apply") and use the EarnKaro profit link for that specific card. That increases conversions.</div>
  </div>
</section>

<!-- LOANS SECTION -->
<section style="margin-top:18px" class="card" id="loans">
  <h2>Loan Offers — High Commissions</h2>
  <p class="small">Promote instant loans & smart EMI offers — commissions are high but check eligibility rules on partner page.</p>

  <div style="margin-top:12px">
    <div class="offer-card">
      <div>
        <div style="font-weight:700">HDFC Instant Loan</div>
        <div class="small">Up to ₹6000 profit — promote responsibly</div>
      </div>
      <div style="display:flex;flex-direction:column;gap:8px;align-items:flex-end">
        <a class="btn" href="#" onclick="openAffiliate('HDFC_LOAN')">Apply</a>
        <div class="small">Up to ₹6000</div>
      </div>
    </div>

    <div class="offer-card">
      <div>
        <div style="font-weight:700">HDFC Smart EMI</div>
        <div class="small">Good payouts for EMI conversions</div>
      </div>
      <div style="display:flex;flex-direction:column;gap:8px;align-items:flex-end">
        <a class="btn" href="#" onclick="openAffiliate('HDFC_SMART_EMI')">Apply</a>
        <div class="small">Up to ₹6000</div>
      </div>
    </div>

    <div class="offer-card">
      <div>
        <div style="font-weight:700">IDFC Personal Loans</div>
        <div class="small">Multiple products — good mid-high payouts</div>
      </div>
      <div style="display:flex;flex-direction:column;gap:8px;align-items:flex-end">
        <a class="btn" href="#" onclick="openAffiliate('IDFC_LOAN')">Apply</a>
        <div class="small">Up to ₹1400+</div>
      </div>
    </div>
  </div>
</section>

<!-- DEALS / SHOPPING SECTION -->
<section style="margin-top:18px" class="card" id="deals">
  <h2>Shopping Deals & Store Offers</h2>
  <p class="small">Use these on home, product pages, and video descriptions. Always use EarnKaro profit links from the partner page.</p>

  <div style="margin-top:12px;display:grid;grid-template-columns:repeat(2,1fr);gap:10px">
    <div class="card">
      <div style="font-weight:700">Amazon</div>
      <div class="small">Upto 10.2% profit — great for electronics & daily deals</div>
      <div style="margin-top:8px"><a class="btn" href="#" onclick="openAffiliate('AMAZON')">Open</a></div>
    </div>
    <div class="card">
      <div style="font-weight:700">AJIO</div>
      <div class="small">Upto 12.5% — fashion & seasonal offers</div>
      <div style="margin-top:8px"><a class="btn" href="#" onclick="openAffiliate('AJIO')">Open</a></div>
    </div>
    <div class="card">
      <div style="font-weight:700">Myntra</div>
      <div class="small">Upto 8% — fashion & footwear</div>
      <div style="margin-top:8px"><a class="btn" href="#" onclick="openAffiliate('MYNTRA')">Open</a></div>
    </div>
    <div class="card">
      <div style="font-weight:700">MamaEarth / Bewakoof / Nutriburst</div>
      <div class="small">High % profit — include on deals pages</div>
      <div style="margin-top:8px"><a class="btn" href="#" onclick="openAffiliate('HEALTH_BEAUTY')">Open</a></div>
    </div>
  </div>
</section>

<!-- JOBS + BANK RATES -->
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
    // Affiliate map: updated with SBI Cashback Card link with your EarnKaro profit links (exact link from partner page)
    const affiliateMap = {
      'HDFC_LOAN': 'https://bitli.in/prewsE9',
      'AXIS_IOCL': 'https://bitli.in/Hb6GU2a',
      'AXIS_MYZ': 'https://bitli.in/i3MPJlA',
      'SBI_CASH2': 'https://bitli.in/6Ps7pk2',
      'HDFC_SWIGGY': 'https://bitli.in/G9i6ccO',
      'AU_LIT': 'https://bitli.in/KowCF3G',
      'IDFC_POWER_PLUS': 'https://bitli.in/A6G9Kg0',
      'FIRSTCRY': 'https://bitli.in/wYaX1fj',
      'AJIO2': 'https://ajiio.in/Ze2QgWu',
      'TATACLIQ': 'https://bitli.in/sW72PQK',
      'CROMA': 'https://bitli.in/3lfFpUn',
      'RELIANCE_DIGITAL': 'https://bitli.in/c1P8Xa8',
      'HDFC_TATANEU': 'https://bitli.in/Us03b52',
      'RBL_IOCL': 'https://bitli.in/Kuev33G',
      'FLIPKART': 'https://fktr.in/2nwkemX',
      'JIOMART': 'https://bitli.in/1lVbAZs',
      'SBI_CASH': 'https://bitli.in/hy5v74T',
      'AXIS_FLIP': 'https://bitli.in/S7SxLqx',
      'AXIS_SAMS': '#PASTE_AXIS_SAMS_LINK',
      'HDFC_MILL': 'https://bitli.in/2tmngzf',
      'IDFC_POWER': '#PASTE_IDFC_POWER_LINK',
      'INDUSIND_EAZY': '#PASTE_INDUSIND_LINK',
      'AU_ALT': '#PASTE_AU_ALT_LINK',
      'YES_RBL_BOB': '#PASTE_YES_RBL_BOB_LINK',
      'HDFC_LOAN': '#PASTE_HDFC_LOAN_LINK',
      'HDFC_SMART_EMI': '#PASTE_HDFC_SMART_EMI_LINK',
      'IDFC_LOAN': '#PASTE_IDFC_LOAN_LINK',
      'AMAZON': 'https://bitli.in/wUoz4U1',
      'AJIO': '#PASTE_AJIO_LINK',
      'MYNTRA': 'https://myntr.it/5etD0R3',
      'HEALTH_BEAUTY': '#PASTE_HEALTH_BEAUTY_LINK'
    };

    function openAffiliate(key){
      const url = affiliateMap[key] || '#';
      if(url === '#' || url.startsWith('#PASTE')){ alert('Affiliate link not set. Open EarnKaro partner page -> Create Profit Link -> paste here.'); return }
      window.open(url,'_blank');
    }

    // Demo: populate gold fields (replace with real API or manual update routine)
    function populateGoldDemo(){
      const now = new Date();
      document.getElementById('lastUpdate').textContent = now.toLocaleString('en-IN');
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
    populateGoldDemo();

  </script></body>
</html>
