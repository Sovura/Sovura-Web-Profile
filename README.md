<!doctype html>
<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Ivan Marcellino Wijaya — Cyberpunk Portfolio</title>

  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Inter:wght@300;400;600&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg-dark:#06060a;
      --accent-1:#ff6fb6;
      --accent-2:#7c3aed;
      --neon-cyan:#85f6ff;
      --neon-magenta:#ff79b0;
      --neon-green:#7CFF5A;
      --nav-bg: rgba(9,9,12,0.48);
      --brand-purple: #5b16ff;
      color-scheme: dark;
      font-family: Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    }

    *{box-sizing:border-box}
    html,body{height:100%;margin:0;background:var(--bg-dark);-webkit-font-smoothing:antialiased;color:#fff}
    a{color:inherit;text-decoration:none}

    /* Top sticky nav */
    .top-nav {
      position: fixed;
      top: 12px;
      left: 50%;
      transform: translateX(-50%);
      z-index: 2200;
      display: flex;
      gap: 10px;
      align-items: center;
      background: var(--nav-bg);
      backdrop-filter: blur(8px) saturate(1.05);
      border-radius: 12px;
      padding: 8px;
      border: 1px solid rgba(255,255,255,0.06);
      box-shadow: 0 8px 30px rgba(2,6,23,0.6);
    }
    .top-nav a {
      display:inline-flex;
      align-items:center;
      gap:8px;
      padding:8px 12px;
      border-radius:8px;
      font-weight:700;
      color:rgba(255,255,255,0.92);
      font-size:14px;
      transition: all .14s ease;
      outline: none;
      border: 1px solid transparent;
    }
    .top-nav a:hover,
    .top-nav a:focus { transform: translateY(-2px); background: rgba(255,255,255,0.02); border-color: rgba(255,255,255,0.04); }
    .top-nav a.active {
      background: linear-gradient(90deg, rgba(124,58,237,0.16), rgba(255,111,182,0.08));
      box-shadow: 0 8px 30px rgba(124,58,237,0.06);
      color: #fff;
      border-color: rgba(255,255,255,0.06);
    }

    /* HERO */
    .hero{
      position:relative;
      min-height:66vh;
      display:flex;
      align-items:center;
      justify-content:center;
      overflow:hidden;
      padding-top:36px;
    }
    .hero::before{
      content:"";
      position:absolute;inset:0;
      background-image: url('hero.jpg');
      background-size:cover;
      background-position:center;
      filter:contrast(1.04) saturate(1.06) blur(.8px);
      transform:scale(1.02);
      z-index:0;
    }
    .hero::after{
      content:"";
      position:absolute;inset:0;
      background:linear-gradient(180deg, rgba(6,6,10,0.66) 0%, rgba(6,6,10,0.46) 36%, rgba(6,6,10,0.72) 100%);
      z-index:1;
    }

    .hero-inner{position:relative;z-index:2;display:flex;flex-direction:column;align-items:center;gap:14px;padding:48px 20px;text-align:center;max-width:1200px;width:100%}
    .portrait-wrap{position:relative;width:140px;height:140px;border-radius:18px;display:inline-block;margin-bottom:6px;z-index:6;transform: translateZ(0)}
    /* RGB border ring for avatar */
    .avatar-wrap { position: relative; width: 140px; height: 140px; flex: 0 0 140px; display: inline-block; margin-right: 16px; }
    .avatar { width: 100%; height: 100%; border-radius: 12px; object-fit: cover; display: block; position: relative; z-index: 4; border: 3px solid rgba(0,0,0,0.35); box-shadow: 0 6px 30px rgba(0,0,0,0.5); background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01)); }

    /* neon RGB avatar ring */
    .avatar-wrap::before { content: ""; position: absolute; inset: -8px; border-radius: 16px; background: conic-gradient(red, lime, blue, red); filter: blur(6px) saturate(1.3); z-index: 3; pointer-events: none; -webkit-mask: radial-gradient(farthest-side, transparent calc(100% - 10px), black calc(100% - 10px)); mask: radial-gradient(farthest-side, transparent calc(100% - 10px), black calc(100% - 10px)); animation: rgbRotate 3.6s linear infinite; opacity: 0.95; }
    .avatar-wrap::after  { content: ""; position: absolute; inset: -4px; border-radius: 14px; background: conic-gradient(from 120deg, rgba(255,0,100,0.9), rgba(0,230,180,0.9), rgba(110,80,255,0.9)); z-index: 5; pointer-events: none; -webkit-mask: radial-gradient(farthest-side, transparent calc(100% - 6px), black calc(100% - 6px)); mask: radial-gradient(farthest-side, transparent calc(100% - 6px), black calc(100% - 6px)); animation: rgbRotateRev 2.4s linear infinite; mix-blend-mode: screen; opacity: 0.95; }
    @keyframes rgbRotate { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }
    @keyframes rgbRotateRev { from { transform: rotate(360deg); } to { transform: rotate(0deg); } }

    .portrait{position:relative;width:100%;height:100%;border-radius:12px;object-fit:cover;border:3px solid rgba(0,0,0,0.35);z-index:3;display:block;box-shadow:0 12px 30px rgba(0,0,0,0.6)}
    .brand{font-family:'Orbitron',sans-serif;font-weight:700;font-size:clamp(30px,6.8vw,64px);color:var(--brand-purple)}
    .subtitle{letter-spacing:6px;font-size:12px;color:rgba(255,255,255,0.78)}

    /* helper highlight */
    .highlight-green { color: var(--neon-green); text-shadow: 0 0 6px rgba(124,255,90,0.95), 0 0 14px rgba(124,255,90,0.18); font-weight:600 }

    /* main / layout */
    .main{max-width:1100px;margin:-80px auto 64px;position:relative;z-index:3;padding:24px}
    .profile-card{display:flex;gap:22px;align-items:center;background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));border-radius:14px;padding:18px;border:1px solid rgba(255,255,255,0.04);box-shadow:0 18px 50px rgba(2,6,23,0.65);backdrop-filter:blur(8px) saturate(1.05)}
    .profile-info h2{margin:0;font-family:'Orbitron',sans-serif;font-size:20px;color:var(--brand-purple)}
    .profile-info .handle{margin-top:6px;color:var(--neon-green);font-weight:600;font-size:14px}
    .bio{color:rgba(255,255,255,0.92);margin:10px 0 6px;line-height:1.6}

    /* art */
    .art-section { margin-top:36px; padding:28px; border-radius:12px; background: linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.005)); border: 1px solid rgba(255,255,255,0.04); box-shadow: 0 12px 40px rgba(2,6,23,0.6); }
    .art-header { display:flex; align-items:center; justify-content:space-between; gap:12px; margin-bottom:16px; }
    .art-header h3 { margin:0; font-family:'Orbitron',sans-serif; color:var(--brand-purple); font-size:20px; letter-spacing:1px; }
    .art-grid { display:grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap:14px; }

    .art-card { position:relative; overflow:hidden; border-radius:10px; min-height:120px; display:flex; align-items:flex-end; padding:12px; cursor:pointer; transition: transform .18s ease, box-shadow .18s ease; border:1px solid rgba(255,255,255,0.03); background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(0,0,0,0.06)); }
    .art-thumb { position:absolute; inset:0; background-size:cover; background-position:center; filter: brightness(.85) saturate(1.05); z-index:0; }
    .art-meta { position:relative; z-index:2; color:#fff; font-weight:700; text-shadow:0 2px 10px rgba(0,0,0,0.6); padding:6px 8px; background: linear-gradient(180deg, transparent, rgba(0,0,0,0.45)); width:100% }

    /* lightbox */
    .lightbox { position:fixed; inset:0; display:none; align-items:center; justify-content:center; z-index:1400; background: linear-gradient(180deg, rgba(0,0,0,0.75), rgba(0,0,0,0.85)); padding:20px; }
    .lightbox.show { display:flex; }
    .lightbox-inner { width: min(920px, 96%); max-height: 86%; border-radius:10px; overflow:auto; position:relative; background:#000; box-shadow: 0 30px 120px rgba(0,0,0,0.9); display:flex; gap:18px; padding:18px; }
    .lightbox-img { width:420px; height:auto; object-fit:contain; border-radius:8px; }
    .preview-body { flex:1 1 auto; color:#eafafa; }
    .preview-title { font-family:'Orbitron',sans-serif; font-weight:700; color:var(--brand-purple); margin:0 0 8px; font-size:18px; }
    .preview-desc { color:rgba(235,255,235,0.92); white-space:pre-line; }

    .lightbox-close { position:absolute; right:12px; top:12px; background:rgba(255,255,255,0.06); border:1px solid rgba(255,255,255,0.06); color:#fff; padding:8px 10px; border-radius:8px; cursor:pointer; z-index:1500; }

    /* blog */
    .blog-tabs { display:flex; gap:10px; margin-bottom:12px; }
    .blog-tabs button { padding:8px 12px; border-radius:8px; border:1px solid rgba(255,255,255,0.06); background:transparent; color:#fff; cursor:pointer; }
    .blog-tabs button.active { background: linear-gradient(90deg, rgba(124,58,237,0.16), rgba(255,111,182,0.06)); color:#fff; }

    /* contact */
    .contact-list { display:flex; flex-direction:column; gap:12px; margin-top:12px; }
    .contact-item { display:flex; align-items:center; gap:12px; padding:12px; border-radius:10px; background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(0,0,0,0.03)); border:1px solid rgba(255,255,255,0.04); }
    .contact-link { display:flex; align-items:center; gap:12px; width:100%; text-decoration:none; color:inherit; }
    .contact-icon { width:44px; height:44px; display:flex; align-items:center; justify-content:center; border-radius:8px; background:rgba(0,0,0,0.18); }

    /* cookie */
    .cookie-bar{position:fixed;left:0;right:0;bottom:0;background:rgba(255,255,255,0.03);backdrop-filter: blur(6px);border-top:1px solid rgba(255,255,255,0.04);display:flex;align-items:center;justify-content:space-between;gap:12px;padding:18px 20px;z-index:999}

    @media (max-width:880px){
      .hero{min-height:52vh}
      .portrait-wrap{width:96px;height:96px;border-radius:14px}
      .main{margin-top:-56px}
      .profile-card{flex-direction:column;align-items:flex-start}
      .art-grid{grid-template-columns:repeat(auto-fit,minmax(180px,1fr))}
    }
  </style>
</head>
<body>

  <nav class="top-nav" role="navigation" aria-label="Site sections">
    <a href="#about" data-target="about" id="nav-about">About me</a>
    <a href="#the-art" data-target="the-art" id="nav-art">The Art</a>
    <a href="#blog" data-target="blog" id="nav-blog">Blog</a>
    <a href="#contact" data-target="contact" id="nav-contact">Contact</a>
  </nav>

  <header class="hero" role="banner" aria-label="Hero">
    <div class="hero-inner">
      <div class="portrait-wrap">
        <img class="portrait" src="portrait.jpg" alt="Portrait photo" loading="lazy">
      </div>

      <div class="brand" aria-hidden="false">Ivan Marcellino Wijaya</div>
      <div class="subtitle">Something more important then myself</div>
    </div>
  </header>

  <main class="main" id="about" role="main">
    <section class="profile-card" aria-labelledby="profileTitle">
      <div class="avatar-wrap" aria-hidden="false" aria-label="Profile avatar">
        <img class="avatar" src="portrait.jpg" alt="Ivan Marcellino Wijaya — avatar" loading="lazy">
      </div>

      <div class="profile-info">
        <h2 id="profileTitle">Ivan Marcellino Wijaya</h2>
        <div class="handle">Gamer and friendly</div>

        <p class="bio">
          Perkenalkan sekali lagi, saya <span class="highlight-green">Ivan Marcellino Wijaya</span>, lahir di kota <span class="highlight-green">Malang</span> dan merupakan orang <span class="highlight-green">Indonesia</span>. Tidak terlalu banyak yang bisa saya banggakan kepada kalian semua, tapi setidaknya ada beberapa yang bisa saya berikan jika anda mau berteman atau bekerja sama dengan saya.
          Saya sedang belajar dan menyukai pembuatan ilustrasi, desain kecil untuk channel, dan mencoba berbagai eksperimen visual. Jika anda tertarik bekerja sama atau sekedar bertanya, silakan hubungi saja lewat kontak di bagian bawah.
        </p>

        <div class="strengths" aria-hidden="false" aria-label="Kekuatan" style="display:flex;gap:10px;margin-top:8px">
          <div style="padding:8px 12px;border-radius:10px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,75,110,0.95);font-weight:700">Mudah diajak bekerja sama</div>
          <div style="padding:8px 12px;border-radius:10px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,75,110,0.95);font-weight:700">Cekatan</div>
          <div style="padding:8px 12px;border-radius:10px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,75,110,0.95);font-weight:700">Mengutamakan tujuan</div>
        </div>

        <p class="weakness" style="margin-top:12px;color:rgba(255,255,255,0.86)"><strong>Tetapi untuk kelemahan saya :</strong> Pastikan kalian dapat mengetahui diri sendiri secara dalam-dalam</p>
      </div>
    </section>

    <section id="the-art" class="art-section" aria-labelledby="artTitle">
      <div class="art-header">
        <h3 id="artTitle">The Art</h3>
        <div>
          <button class="btn ghost" id="viewAllBtn">View all</button>
        </div>
      </div>

      <div class="art-grid" id="artGrid" aria-live="polite">
        <div class="art-card" data-title="Chibi project" data-src="art3.jpg"
             data-desc="Chibi Project merupakan style chibi dari saya sendiri yang berasal dari keinginan untuk mengubah logo dari channel youtube saya sendiri yaitu TheNoobBoy31. Penggunaan warnanya sendiri merupakan campuran dari warna favorit dan warna yang biasanya dipakai untuk logo lama.">
          <div class="art-thumb" style="background-image:url('art3.jpg');"></div>
          <div class="art-meta">Chibi project</div>
        </div>

        <div class="art-card" data-title="The First Novel" data-src="art4.jpg"
             data-desc="The First Novel merupakan novel pertama milik saya dimana semua unek-unek saya, saya ceritakan melalui style cerita fantasy. Ahh perlu diperhatikan juga, genre yang saya berikan adalah genre gore dan echi jadi kalau belum cukup umur atau belum siap maka jangan berani-berani untuk membacanya">
          <div class="art-thumb" style="background-image:url('art4.jpg');"></div>
          <div class="art-meta">The First Novel</div>
        </div>

        <div class="art-card" data-title="I See Youuu" data-src="art5.jpg"
             data-desc="I See Youuu berasal dari ide yang ingin saya lakukan untuk foto dan saya berikan di Instagram saya, tapi karena kekurangan outfit dan tempat untuk mengambil foto, jadinya saya lebih memilih bagaimana kalau saya representasikan dari gambaran saya. Dan yahh akhirnya Vualla jadi deh">
          <div class="art-thumb" style="background-image:url('art5.jpg');"></div>
          <div class="art-meta">I See Youuu</div>
        </div>

        <div class="art-card" data-title="First Comic" data-src="art4.png"
             data-desc="First Comic sendiri merupakan ide yang seketika muncul saat saya dan teman saya membicarakan karakter Xiao dari game Genshin Impact. Ide ini muncul saat saya mengatakan bagaimana kalau ultimate dari Xiao ini jadi kayak gini, dan yah akhirnya tanpa pikir panjang saya langsung buat begitu saja. Oh iya, ini juga ada genre Gorenya ya">
          <div class="art-thumb" style="background-image:url('art4.png');"></div>
          <div class="art-meta">First Comic</div>
        </div>

        <div class="art-card" data-title="R.E.P.O" data-src="art5.png"
             data-desc="Thumbnail R.E.P.O ini muncul karena saat saya mencari thumnail yang pas untuk youtube saya di google kebanyakan thumnailnya kurang menarik dan yah akhirnya saya buat sendiri dah thumnailnya. Meskipun masih ada kekurangan tapi setidaknya saya dapat memberikan sesuatu yang original dari saya">
          <div class="art-thumb" style="background-image:url('art5.png');"></div>
          <div class="art-meta">R.E.P.O</div>
        </div>

        <div class="art-card" data-title="Kushika's Scar" data-src="art6.png"
             data-desc="Gambar ini terbuat karena saya ingin menunjukan apa saja yang telah Kushika lalui sampai akhirnya bisa sampai sekarang, meskipun masih banyak kekurangan dari backgroundnya, pewarnaannya dan lainnya, tapi setidaknya saya ingin menyampaikan pesannya. Tentu tidak ada unsur sara atau pornografi saat membuatnya">
          <div class="art-thumb" style="background-image:url('art6.png');"></div>
          <div class="art-meta">Kushika's Scar</div>
        </div>
      </div>
    </section>

    <section id="blog" class="art-section" aria-labelledby="blogTitle">
      <div class="art-header">
        <h3 id="blogTitle">Blog</h3>
      </div>

      <div class="blog-tabs" role="tablist" aria-label="Blog tabs">
        <button id="tab-myreason" class="active" role="tab" aria-selected="true" aria-controls="panel-myreason">My Reason</button>
        <button id="tab-otherpov" role="tab" aria-selected="false" aria-controls="panel-otherpov">Other POV</button>
      </div>

      <div id="panel-myreason" role="tabpanel" aria-labelledby="tab-myreason">
        <article>
          <p>Proses kreatif dan pembelajaran teknologi informasi di masa sekarang ini dapat dipengaruhi secara signifikan oleh kemajuan teknologi, terutama munculnya AI seperti ChatGPT, Gemini, dll. Sayangnya, kebanyakan mahasiswa termasuk saya sendiri berada di kebimbangan antara memanfaatkannya secara efisiensi atau munculnya resiko ketergantungan.</p>

          <h4>🚀 Tantangan dan Peluang Kreativitas</h4>
          <p><strong>Pemanfaatan Teknologi untuk Inovasi:</strong> Teknologi canggih, seperti AI dan IoT, membuka peluang tak terbatas bagi mahasiswa untuk menggabungkan imajinasi dan inovasi. Para mahasiswa ditantang untuk tidak hanya menggunakan teknologi saja, tetapi juga bereksperimen dan menggunakannya sebagai alat untuk menciptakan solusi yang benar-benar baru dan berpengaruh.</p>

          <p><strong>Berpikir Kritis vs Ketergantungan:</strong> AI dapat mempercepat akses informasi dan membantu dalam penyelesaian tugas rutin. Namun, perlu diingat dengan adanya kekhawatiran tentang ketergantungan yang dapat mengikis kemampuan berpikir kritis.</p>

          <p><strong>Strategi Pengembangan Diri:</strong></p>
          <ul>
            <li>Meningkatkan rasa ingin tahu dan keinginan untuk belajar.</li>
            <li>Melatih berpikir kritis dan analitis dalam memfilter informasi.</li>
            <li>Berani mengambil risiko dan belajar dari kegagalan.</li>
          </ul>

          <p>Memastikan bahwa penggunaan teknologi, termasuk AI, tetap didasarkan pada etika dan moral seperti menghormati privasi dan menghindari plagiarisme.</p>

          <h4>📚 TI sebagai Komponen Pembelajaran yang Terintegrasi</h4>
          <p>Refleksi pengalaman mata kuliah menunjukkan bahwa TI tidak lagi sekedar alat bantu, tetapi merupakan komponen yang terintegrasi dalam proses pembelajaran itu sendiri. Mahasiswa belajar cara mengelola kelas virtual, mengembangkan konten e-learning, dan memanfaatkan platform digital interaktif. Hal ini menuntut mereka untuk terus beradaptasi dan mengembangkan literasi digital yang baik.</p>
        </article>
      </div>

      <div id="panel-otherpov" role="tabpanel" aria-labelledby="tab-otherpov" hidden>
        <article>
          <p>Belajar mandiri dalam bidang teknologi informasi dicirikan oleh fleksibilitas, inisiatif tinggi, dan pemanfaatan sumber daya digital secara maksimal. Meskipun tanpa struktur akademik yang formal, prinsip yang memandu pembelajaran mandiri ini sangat mirip dengan tuntutan self-directed learning di era digital.</p>

          <p>Belajar mandiri secara alami didorong untuk mengeksplorasi berbagai aplikasi, platform digital, dan perangkat lunak. Refleksi menunjukkan bahwa pengalaman ini mencakup mempelajari cara membuat konten multimedia, menggunakan platform e-learning, dan memanfaatkan fitur-fitur seperti video conference atau kuis online. Hal ini menunjukkan bahwa praktik langsung dan eksperimentasi menjadi inti dari proses pembelajaran.</p>

          <p><strong>Fleksibilitas dan Sumber Belajar:</strong> Pembelajar mandiri memiliki kendali penuh atas tempo dan materi yang dipelajari. Mereka secara aktif mencari berbagai sumber belajar—artikel, buku, jurnal, diskusi—sebagai penunjang. Misalnya, dalam mempelajari suatu topik, mereka mungkin akan mengaplikasikannya dengan membuat website sederhana menggunakan Google Sites, yang memungkinkan mereka untuk mengeksperis bahan ajar kapan saja dan di mana saja.</p>

          <p><strong>Adaptasi Cepat:</strong> Dalam dunia TI yang berubah cepat, pembelajar mandiri harus memiliki sikap siap dan mampu menyesuaikan diri dengan pembaruan teknologi. Mereka perlu beradaptasi dengan lingkungan, media, dan sistem belajar baru untuk memastikan keterampilan mereka tetap relevan.</p>

          <p>🧠 <strong>Tantangan para pelajar mandiri: Menjaga Integritas dan Kedalaman</strong><br>
          Meskipun belajar mandiri, pelajar mandiri menghadapi tantangan yang sama dengan mahasiswa, terutama dalam hal memilih dan memverifikasi informasi. Karena tidak ada kurikulum terstruktur, kemampuan untuk bertindak bijak dalam menggunakan media pembelajaran dan memiliki keterampilan kritis dalam memfilter informasi sangat penting untuk menjaga integritas pengetahuan yang diperoleh.</p>
        </article>
      </div>
    </section>

    <section id="contact" class="art-section" aria-labelledby="contactTitle" style="margin-top:28px">
      <div class="art-header">
        <h3 id="contactTitle">Contact</h3>
      </div>

      <div class="contact-list" role="list">
        <div class="contact-item" role="listitem">
          <a class="contact-link" href="https://www.instagram.com/_sovura_?igsh=MXR4enM0amY2YmplYg==" target="_blank" rel="noopener" aria-label="Instagram _Sovura_">
            <span class="contact-icon" aria-hidden="true">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><rect x="3" y="3" width="18" height="18" rx="5" stroke="url(#igg)" stroke-width="1.6" fill="none"/><circle cx="12" cy="12" r="3.1" stroke="url(#igg)" stroke-width="1.6" fill="none"/><circle cx="17.2" cy="6.8" r="0.6" fill="url(#igg)"/><defs><linearGradient id="igg" x1="0" x2="1"><stop offset="0" stop-color="#f58529"/><stop offset="0.5" stop-color="#dd2a7b"/><stop offset="1" stop-color="#8134af"/></linearGradient></defs></svg>
            </span>
            <span class="contact-text" style="color:var(--brand-purple);font-weight:700">_Sovura_</span>
          </a>
        </div>

        <div class="contact-item" role="listitem">
          <a class="contact-link" href="https://www.tiktok.com/@thenoobboy31?_r=1&_t=ZS-91t76T2gM6M" target="_blank" rel="noopener" aria-label="TikTok _TNB31_">
            <span class="contact-icon" aria-hidden="true">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M9 9v6.5a3.5 3.5 0 103.5-3.5V7h3" stroke="#fff" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/><circle cx="17" cy="7" r="2" fill="url(#ttt)"/><defs><linearGradient id="ttt" x1="0" x2="1"><stop offset="0" stop-color="#ff3cac"/><stop offset="1" stop-color="#8a2be2"/></linearGradient></defs></svg>
            </span>
            <span class="contact-text" style="font-weight:800; background: linear-gradient(90deg,#8a2be2,#ff3cac); -webkit-background-clip: text; background-clip: text; color: transparent;">_TNB31_</span>
          </a>
        </div>

        <div class="contact-item" role="listitem">
          <a class="contact-link" href="https://youtube.com/@thenoobboy31?si=CEwZ9YvGmG-mnuvd" target="_blank" rel="noopener" aria-label="YouTube TheNoobBoy31">
            <span class="contact-icon" aria-hidden="true">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><rect x="2" y="5" width="20" height="14" rx="4" fill="#000" stroke="rgba(255,255,255,0.06)"/><path d="M10 8l6 4-6 4V8z" fill="var(--neon-green)"/></svg>
            </span>
            <span class="contact-text" style="color:var(--neon-green);font-weight:700">TheNoobBoy31</span>
          </a>
        </div>

        <div class="contact-item" role="listitem">
          <a class="contact-link" href="mailto:Afterupdate31@gmail.com" aria-label="Email Afterupdate31@gmail.com">
            <span class="contact-icon" aria-hidden="true">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><rect x="2" y="4" width="20" height="16" rx="2" fill="rgba(255,255,255,0.03)" stroke="rgba(255,255,255,0.06)"/><path d="M3 6l9 7 9-7" stroke="#ff7b7b" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/></svg>
            </span>
            <span class="contact-text" style="color:#ffb4b4;font-weight:700">Afterupdate31@gmail.com</span>
          </a>
        </div>
      </div>
    </section>
  </main>

  <!-- Lightbox -->
  <div id="lightbox" class="lightbox" aria-hidden="true">
    <div class="lightbox-inner" role="dialog" aria-modal="true" aria-label="Art preview">
      <button class="lightbox-close" id="lightboxClose" aria-label="Close preview">Close</button>
      <img id="lightboxImg" class="lightbox-img" src="" alt="">
      <div class="preview-body">
        <h3 id="previewTitle" class="preview-title"></h3>
        <div id="previewDesc" class="preview-desc"></div>
      </div>
    </div>
  </div>

  <!-- Cookie bar -->
  <div class="cookie-bar" id="cookieBar" role="dialog" aria-live="polite" aria-label="Persetujuan cookie">
    <div class="cookie-info">
      <strong>Privasi Anda penting</strong>
      <div style="opacity:.92;margin-top:6px;font-size:13px">
        Kami menggunakan cookie untuk meningkatkan pengalaman Anda, menganalisis lalu lintas, dan mempersonalisasi konten. Terima semua untuk menyetujui kebijakan Cookie dan Privasi kami.
      </div>
    </div>

    <div class="cookie-actions" role="group" aria-label="Tindakan cookie">
      <button class="btn ghost" id="managePrefs">Kelola preferensi</button>
      <button class="btn ghost" id="rejectAll">Tolak semua</button>
      <button class="btn primary" id="acceptAll">Terima semua</button>
    </div>
  </div>

  <script>
    (function(){
      // Smooth scroll for anchor links (accounts for top nav)
      document.querySelectorAll('.top-nav a').forEach(a=>{
        a.addEventListener('click', (e)=>{
          const href = a.getAttribute('href');
          if(!href || href.indexOf('#') !== 0) return;
          const target = document.querySelector(href);
          if(target){
            e.preventDefault();
            const nav = document.querySelector('.top-nav');
            const navHeight = nav ? nav.getBoundingClientRect().height + 8 : 0;
            const top = target.getBoundingClientRect().top + window.pageYOffset - navHeight - 12;
            window.scrollTo({ top, behavior: 'smooth' });
            target.focus({preventScroll:true});
          }
        });
      });

      // Art grid -> lightbox
      const artGrid = document.getElementById('artGrid');
      const lightbox = document.getElementById('lightbox');
      const lightboxImg = document.getElementById('lightboxImg');
      const lightboxClose = document.getElementById('lightboxClose');
      const previewTitle = document.getElementById('previewTitle');
      const previewDesc = document.getElementById('previewDesc');

      artGrid.querySelectorAll('.art-card').forEach(card=>{
        card.addEventListener('click', ()=> {
          const src = card.dataset.src || '';
          const title = card.dataset.title || '';
          const desc = card.dataset.desc || '';
          if(!src) return;
          lightboxImg.src = src;
          lightboxImg.alt = title;
          previewTitle.textContent = title;
          previewDesc.textContent = desc || 'No description provided.';
          lightbox.classList.add('show');
          lightbox.setAttribute('aria-hidden','false');
          document.body.style.overflow = 'hidden';
        });
        // keyboard activation
        card.setAttribute('tabindex', '0');
        card.addEventListener('keydown', (ev)=>{
          if(ev.key === 'Enter' || ev.key === ' ') { ev.preventDefault(); card.click(); }
        });
      });

      lightboxClose.addEventListener('click', closeLightbox);
      lightbox.addEventListener('click', (ev) => {
        if(ev.target === lightbox) closeLightbox();
      });
      document.addEventListener('keydown', (ev)=>{
        if(ev.key === 'Escape') closeLightbox();
      });
      function closeLightbox(){ lightbox.classList.remove('show'); lightbox.setAttribute('aria-hidden','true'); lightboxImg.src = ''; previewTitle.textContent = ''; previewDesc.textContent = ''; document.body.style.overflow = ''; }

      // Blog tabs
      const tabMy = document.getElementById('tab-myreason');
      const tabOther = document.getElementById('tab-otherpov');
      const panelMy = document.getElementById('panel-myreason');
      const panelOther = document.getElementById('panel-otherpov');
      if(tabMy && tabOther){
        tabMy.addEventListener('click', ()=> { tabMy.classList.add('active'); tabOther.classList.remove('active'); panelMy.hidden = false; panelOther.hidden = true; });
        tabOther.addEventListener('click', ()=> { tabOther.classList.add('active'); tabMy.classList.remove('active'); panelOther.hidden = false; panelMy.hidden = true; });
      }

      // Cookie prefs (simple)
      function setCookiePrefs(obj){ localStorage.setItem('ivan_cookie_prefs', JSON.stringify(obj)); document.getElementById('cookieBar').style.display = 'none'; }
      function getCookiePrefs(){ try{ return JSON.parse(localStorage.getItem('ivan_cookie_prefs')) || null }catch(e){ return null } }
      const prefs = getCookiePrefs(); document.getElementById('cookieBar').style.display = prefs ? 'none' : 'flex';
      document.getElementById('acceptAll')?.addEventListener('click', ()=> setCookiePrefs({essential:true, analytics:true, marketing:true}));
      document.getElementById('rejectAll')?.addEventListener('click', ()=> setCookiePrefs({essential:true, analytics:false, marketing:false}));
      document.getElementById('managePrefs')?.addEventListener('click', ()=> alert('Kelola preferensi cookie (sederhana)'));

      // Active nav highlighting
      const navLinks = Array.from(document.querySelectorAll('.top-nav a'));
      const sections = navLinks.map(l => document.getElementById(l.dataset.target));
      const io = new IntersectionObserver((entries) => {
        let visible = entries.filter(e => e.isIntersecting).sort((a,b) => b.intersectionRatio - a.intersectionRatio)[0];
        if(visible){
          const id = visible.target.id;
          navLinks.forEach(link => {
            if(link.dataset.target === id) link.classList.add('active');
            else link.classList.remove('active');
          });
        }
      }, { threshold: [0.15, 0.35, 0.6] });
      sections.forEach(s => { if(s) io.observe(s); });

    })();
  </script>
</body>
</html>
