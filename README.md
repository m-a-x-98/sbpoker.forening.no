<!--
Poker Club - Static single-file website
Place this file (poker-club-site.html) in a GitHub Pages repository (e.g., index.html)
External resources used: Google Fonts, Font Awesome, Unsplash images (hotlinked)
-->
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Riverstone Poker Club</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&family=Playfair+Display:wght@600&display=swap" rel="stylesheet">
  <!-- Font Awesome -->
  <script src="https://kit.fontawesome.com/yourkitid.js" crossorigin="anonymous"></script>
  
  <meta name="description" content="Riverstone Poker Club — weekly Texas Hold'em tournaments, friendly cash games, lessons & membership." />

  <style>
    :root{
      --bg:#0b2b1f; /* deep green felt shadow */
      --felt:#0e5f3a; /* felt green */
      --accent:#d4a017; /* gold chip accent */
      --muted:rgba(255,255,255,0.85);
      --card:#ffffff;
      --glass: rgba(255,255,255,0.06);
      --container:1100px;
      font-family: 'Inter', system-ui, -apple-system, "Segoe UI", Roboto, 'Helvetica Neue', Arial;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      background: radial-gradient(1200px 400px at 10% 20%, rgba(0,0,0,0.2), transparent), linear-gradient(180deg,#042016 0%, var(--bg) 100%);
      color:var(--muted);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      line-height:1.45;
    }

    /* subtle felt texture */
    .felt {
      background:
        linear-gradient(135deg, rgba(255,255,255,0.03) 0%, rgba(255,255,255,0.00) 50% ),
        repeating-linear-gradient(0deg, rgba(255,255,255,0.02) 0 1px, transparent 1px 3px),
        var(--felt);
      box-shadow: 0 20px 60px rgba(2,10,6,0.6) inset;
    }

    .container{max-width:var(--container);margin:0 auto;padding:2rem}

    header{
      position:sticky;top:0;z-index:60;backdrop-filter: blur(6px);
      background: linear-gradient(180deg, rgba(2,8,5,0.6), rgba(2,8,5,0.25));
      border-bottom:1px solid rgba(255,255,255,0.03);
    }
    .nav{display:flex;align-items:center;justify-content:space-between;padding:0.6rem 1rem}
    .brand{display:flex;align-items:center;gap:.8rem}
    .brand .logo{width:46px;height:46px;border-radius:8px;background:linear-gradient(180deg,var(--accent),#b37c09);display:flex;align-items:center;justify-content:center;color:#0b1a0f;font-weight:800;font-family:'Playfair Display';box-shadow:0 6px 18px rgba(0,0,0,0.4)}
    .brand h1{margin:0;font-size:1.05rem}
    nav ul{display:flex;gap:1rem;margin:0;padding:0;list-style:none}
    nav a{color:var(--muted);text-decoration:none;font-weight:600;font-size:.95rem}
    .cta{background:var(--accent);color:#08110b;padding:.45rem .8rem;border-radius:8px;font-weight:700}

    /* hero */
    .hero{display:grid;grid-template-columns:1fr 420px;gap:2rem;align-items:center;padding:4rem 0}
    .hero .left{padding:1rem}
    .headline{font-family:'Playfair Display',serif;font-size:2.4rem;margin:0 0 .6rem;color:#fff}
    .eyebrow{display:inline-block;background:rgba(255,255,255,0.06);padding:.3rem .6rem;border-radius:999px;font-weight:700;font-size:.8rem;margin-bottom:1rem}
    .tagline{font-size:1.05rem;color:rgba(255,255,255,0.88);margin-bottom:1.25rem}
    .features{display:flex;gap:1rem;flex-wrap:wrap}
    .feature{background:var(--glass);padding:.7rem .9rem;border-radius:12px;font-weight:600}

    /* card mock */\    
    .table-card{background:linear-gradient(180deg,#ffffff 0%, #e9e6e6 100%);border-radius:12px;padding:1rem;color:#0b0b0b;box-shadow: 0 10px 30px rgba(3,9,6,0.5)}
    .card-row{display:flex;gap:.6rem;align-items:center}
    .chip{width:44px;height:44px;border-radius:50%;display:inline-grid;place-items:center;font-weight:800;background:conic-gradient(from 90deg,#e9e9e9, #ffffff);box-shadow:0 6px 14px rgba(3,9,6,0.35)}

    .hero .right{padding:1rem}
    .hero-img{border-radius:12px;overflow:hidden;box-shadow:0 20px 60px rgba(2,6,3,0.6)}
    .hero-img img{display:block;width:100%;height:100%;object-fit:cover}

    /* sections */
    section{padding:3rem 0}
    h2{font-family:'Playfair Display';color:#fff;margin:0 0 1rem;font-size:1.4rem}
    p.lead{color:rgba(255,255,255,0.86);max-width:75%}

    /* events grid */
    .grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:1rem}
    .event{background:linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.02));padding:1rem;border-radius:12px;border:1px solid rgba(255,255,255,0.03)}
    .event h3{margin:.3rem 0 .6rem}
    .badge{display:inline-block;padding:.25rem .5rem;border-radius:999px;background:rgba(255,255,255,0.04);font-weight:700}

    /* membership */
    .pricing{display:flex;gap:1rem;flex-wrap:wrap}
    .plan{background:linear-gradient(180deg,#062015, #0b3321);padding:1rem;border-radius:12px;border:1px solid rgba(255,255,255,0.03);flex:1;min-width:220px}
    .plan .price{font-size:1.6rem;font-weight:800;color:var(--accent)}

    /* gallery */
    .gallery{display:grid;grid-template-columns:repeat(4,1fr);gap:8px}
    .gallery img{width:100%;height:140px;object-fit:cover;border-radius:8px}

    /* footer */
    footer{padding:2rem 0;border-top:1px solid rgba(255,255,255,0.03);text-align:center}

    /* responsive */
    @media (max-width:980px){
      .hero{grid-template-columns:1fr;}
      .hero .right{order:-1}
      .gallery{grid-template-columns:repeat(2,1fr)}
      nav ul{display:none}
    }

    @media (max-width:520px){
      .headline{font-size:1.6rem}
      .gallery img{height:100px}
    }

    /* small helpers */
    .muted{color:rgba(255,255,255,0.7)}
    .center{display:flex;align-items:center;justify-content:center}

  </style>
</head>
<body>

  <header>
    <div class="container nav">
      <div class="brand">
        <div class="logo">R</div>
        <div>
          <h1 style="margin:0">Riverstone Poker Club</h1>
          <div style="font-size:.75rem;color:rgba(255,255,255,0.7);margin-top:2px">Stockholm • Weekly Tournaments</div>
        </div>
      </div>

      <nav>
        <ul>
          <li><a href="#about">About</a></li>
          <li><a href="#events">Events</a></li>
          <li><a href="#membership">Membership</a></li>
          <li><a href="#contact">Contact</a></li>
        </ul>
      </nav>

      <div class="center" style="gap:.7rem">
        <a class="cta" href="#join">Join</a>
      </div>
    </div>
  </header>

  <main class="container">
    <section class="hero felt" aria-label="Club hero">
      <div class="left">
        <span class="eyebrow">Texas Hold'em • Friendly • Competitive</span>
        <h2 class="headline">Play your best hand at Riverstone</h2>
        <p class="tagline">Weekly tournaments, cash games, coaching sessions and social nights. New players welcome — we prize etiquette and sportsmanship above all.</p>

        <div class="features" aria-hidden>
          <div class="feature">🏆 Weekly Tournaments</div>
          <div class="feature">💡 Coaching & Workshops</div>
          <div class="feature">🍷 Social Evenings</div>
        </div>

        <div style="margin-top:1.2rem" class="table-card">
          <div class="card-row">
            <div class="chip">100</div>
            <div>
              <div style="font-weight:800">Tonight's Buy-in</div>
              <div class="muted" style="font-size:.9rem">€25 • Rebuys allowed until level 3</div>
            </div>
          </div>

          <div style="margin-top:1rem;font-size:.95rem">Doors open 18:30 — play at 19:00. New players: arrive early for a 15-min primer.</div>
        </div>

      </div>

      <aside class="right">
        <div class="hero-img">
          <img src="https://images.unsplash.com/photo-1548924371-3f6d1e3b0bd2?q=80&w=1200&auto=format&fit=crop&ixlib=rb-4.0.3&s=0f0a2d9b0e0b2f4a9f2b7a3e9f1c8b0c" alt="Poker table with chips and cards">
        </div>
      </aside>
    </section>

    <section id="about">
      <h2>About the Club</h2>
      <p class="lead">Riverstone Poker Club started in 2015 as a group of friends playing for fun. Today we host regular tournaments, beginner classes and charity nights. Our mission: keep poker accessible, honest and welcoming.</p>
    </section>

    <section id="events">
      <h2>Upcoming Events</h2>
      <div class="grid">
        <article class="event">
          <div class="badge">Tournament</div>
          <h3>Friday Night Hold'em</h3>
          <div class="muted">Fri — 19:00</div>
          <p style="margin-top:.6rem">Deep-stack format. €25 buy-in. Prize pool paid to top 15%.</p>
        </article>

        <article class="event">
          <div class="badge">Workshop</div>
          <h3>Beginner's Bootcamp</h3>
          <div class="muted">Sat — 17:00</div>
          <p style="margin-top:.6rem">Learn the rules, basic strategy and table etiquette in a 90-minute session.</p>
        </article>

        <article class="event">
          <div class="badge">Social</div>
          <h3>Charity Poker Night</h3>
          <div class="muted">Monthly • 20:00</div>
          <p style="margin-top:.6rem">Partnership with local charities. Special prizes & raffle.</p>
        </article>

        <article class="event">
          <div class="badge">Cash Game</div>
          <h3>Cash Table Open</h3>
          <div class="muted">Wed — 20:00</div>
          <p style="margin-top:.6rem">€1/€2 NLH cash games, friendly stakes. Bring ID.</p>
        </article>
      </div>
    </section>

    <section id="membership">
      <h2>Membership</h2>
      <p class="muted">Become a member to enjoy reduced buy-ins, priority seating and exclusive workshops.</p>

      <div class="pricing" style="margin-top:1rem">
        <div class="plan">
          <div style="font-weight:800">Social</div>
          <div class="price">€0</div>
          <div class="muted">Free</div>
          <ul style="margin-top:.6rem">
            <li>Event updates</li>
            <li>Priority newsletter</li>
          </ul>
          <div style="margin-top:.8rem"><a class="cta" href="#join">Sign Up</a></div>
        </div>

        <div class="plan">
          <div style="font-weight:800">Club Member</div>
          <div class="price">€45 / year</div>
          <div class="muted">Recommended</div>
          <ul style="margin-top:.6rem">
            <li>Reduced tournament fees</li>
            <li>Members-only sessions</li>
          </ul>
          <div style="margin-top:.8rem"><a class="cta" href="#join">Join</a></div>
        </div>

        <div class="plan">
          <div style="font-weight:800">Pro</div>
          <div class="price">€120 / year</div>
          <div class="muted">Premium</div>
          <ul style="margin-top:.6rem">
            <li>Free entry nights</li>
            <li>Personal coaching credit</li>
          </ul>
          <div style="margin-top:.8rem"><a class="cta" href="#join">Join</a></div>
        </div>
      </div>
    </section>

    <section id="gallery">
      <h2>Gallery</h2>
      <div class="gallery" aria-hidden>
        <img src="https://images.unsplash.com/photo-1511512578047-dfb367046420?q=80&w=800&auto=format&fit=crop" alt="Chips and cards closeup">
        <img src="https://images.unsplash.com/photo-1549893079-0c7a70c2a6f0?q=80&w=800&auto=format&fit=crop" alt="Players at table">
        <img src="https://images.unsplash.com/photo-1518609878373-06d740f60d8b?q=80&w=800&auto=format&fit=crop" alt="Dealer shuffling cards">
        <img src="https://images.unsplash.com/photo-1534253482207-3b5c6d36f3a2?q=80&w=800&auto=format&fit=crop" alt="Tournament night atmosphere">
      </div>
    </section>

    <section id="contact">
      <h2>Contact & Venue</h2>
      <p class="muted">Have questions or want to schedule a private game? Email us — we're happy to help.</p>
      <div style="display:grid;grid-template-columns:1fr 320px;gap:1rem;margin-top:1rem;align-items:start">
        <div>
          <address style="font-style:normal">
            <strong>Riverstone Poker Club</strong><br>
            Gamla Stan 14, Stockholm<br>
            <span class="muted">Opening hours: Wed—Sun, 18:00–01:00</span>
          </address>

          <p style="margin-top:1rem"><strong>Email:</strong> <a href="mailto:info@riverstonepoker.example">info@riverstonepoker.example</a></p>
        </div>

        <div style="background:linear-gradient(180deg, rgba(0,0,0,0.25), rgba(255,255,255,0.02));padding:1rem;border-radius:12px;border:1px solid rgba(255,255,255,0.03)">
          <h3 style="margin:0 0 .6rem">Quick Signup</h3>
          <form action="mailto:info@riverstonepoker.example" method="post" enctype="text/plain">
            <label style="display:block;margin-bottom:.4rem">Name
              <input name="name" required style="width:100%;padding:.5rem;margin-top:.2rem;border-radius:8px;border:1px solid rgba(255,255,255,0.06);background:transparent;color:var(--muted)">
            </label>
            <label style="display:block;margin-bottom:.4rem">Email
              <input name="email" type="email" required style="width:100%;padding:.5rem;margin-top:.2rem;border-radius:8px;border:1px solid rgba(255,255,255,0.06);background:transparent;color:var(--muted)">
            </label>
            <label style="display:block;margin-bottom:.4rem">Message
              <textarea name="message" rows="3" style="width:100%;padding:.5rem;margin-top:.2rem;border-radius:8px;border:1px solid rgba(255,255,255,0.06);background:transparent;color:var(--muted)"></textarea>
            </label>
            <div style="margin-top:.6rem"><button class="cta" type="submit">Send</button></div>
          </form>
        </div>
      </div>
    </section>

  </main>

  <footer>
    <div class="container">
      <div style="display:flex;flex-wrap:wrap;gap:1rem;align-items:center;justify-content:space-between">
        <div class="muted">© Riverstone Poker Club — Established 2015</div>
        <div class="muted">Follow us: <a href="#" style="color:var(--muted);text-decoration:underline">Instagram</a> • <a href="#" style="color:var(--muted);text-decoration:underline">Facebook</a></div>
      </div>
    </div>
  </footer>

  <script>
    // small JS for smooth scroll behavior on hash links
    document.querySelectorAll('a[href^="#"]').forEach(a=>{
      a.addEventListener('click', e=>{
        const target = document.querySelector(a.getAttribute('href'));
        if(target){e.preventDefault();target.scrollIntoView({behavior:'smooth',block:'start'});}
      })
    })
  </script>
</body>
</html>
