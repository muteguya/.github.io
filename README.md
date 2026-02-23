<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
  <title>CIUE · dashboard</title>
  <!-- Font Awesome 6 (free) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background: #eef2f7;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 16px;
    }

    /* phone frame */
    .phone {
      max-width: 390px;
      width: 100%;
      background-color: #ffffff;
      border-radius: 40px;
      box-shadow: 0 25px 60px rgba(0, 20, 30, 0.15), 0 8px 20px rgba(0, 40, 60, 0.1);
      overflow: hidden;
      padding: 20px 18px 12px 18px;
      transition: all 0.2s;
    }

    /* header */
    .welcome-section {
      margin-bottom: 28px;
    }

    .hello-tag {
      color: #006064;        /* deep teal – part of new palette */
      font-size: 0.85rem;
      font-weight: 600;
      letter-spacing: 0.8px;
      text-transform: uppercase;
      margin-bottom: 6px;
    }

    .main-headline {
      font-size: 1.9rem;
      font-weight: 700;
      line-height: 1.2;
      color: #0b2b3b;
    }

    .main-headline span {
      display: block;
      font-size: 1rem;
      font-weight: 400;
      color: #3f5e6b;
      margin-top: 6px;
      letter-spacing: -0.2px;
    }

    .divider {
      height: 2px;
      background: linear-gradient(90deg, #00bcd4 0%, #b2ebf2 70%, #e0f7fa 100%);
      width: 70px;
      margin: 18px 0 20px 0;
      border-radius: 4px;
    }

    /* collaboration text */
    .collab-text {
      font-size: 1.2rem;
      font-weight: 500;
      color: #1d4e5f;
      margin-bottom: 24px;
      line-height: 1.3;
    }

    .collab-text i {
      color: #00acc1;
      margin-right: 6px;
    }

    /* TASK HALL section – cards */
    .task-hall-label {
      display: flex;
      align-items: center;
      gap: 10px;
      margin-bottom: 18px;
    }

    .task-hall-label h3 {
      font-size: 1.5rem;
      font-weight: 700;
      color: #003d4d;
      letter-spacing: -0.3px;
    }

    .task-hall-label i {
      font-size: 1.6rem;
      color: #00bcd4;
      background: #e0f7fa;
      padding: 8px;
      border-radius: 18px;
    }

    .teaser-badge {
      background: #00838f;
      color: white;
      padding: 6px 14px;
      border-radius: 100px;
      font-size: 0.8rem;
      font-weight: 600;
      display: inline-block;
      margin-bottom: 12px;
      letter-spacing: 0.3px;
    }

    /* card grid */
    .card-grid {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-bottom: 28px;
    }

    .reward-card {
      background: #f9fbfd;
      border-radius: 28px;
      padding: 16px 22px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border: 1px solid #d6e9ed;
      box-shadow: 0 5px 12px rgba(0, 140, 150, 0.06);
      transition: all 0.2s;
    }

    .reward-card:hover {
      background: #f0fafc;
      border-color: #4dd0e1;
    }

    .card-left {
      display: flex;
      align-items: center;
      gap: 14px;
    }

    .card-icon {
      width: 48px;
      height: 48px;
      background: #d2f1f5;
      border-radius: 30px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #006a7a;
      font-size: 1.5rem;
    }

    .card-title {
      font-weight: 700;
      font-size: 1.2rem;
      color: #144f5c;
    }

    .card-value {
      font-weight: 800;
      font-size: 1.3rem;
      background: linear-gradient(145deg, #006a7a, #00b2c9);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      letter-spacing: 0.5px;
    }

    .card-value small {
      font-size: 0.8rem;
      font-weight: 500;
      color: #3f98a7;
      background: none;
      -webkit-text-fill-color: #3f98a7;
    }

    /* action row (recharge / withdraw / profile) */
    .action-row {
      display: flex;
      align-items: center;
      justify-content: space-around;
      background: #ecf7f9;
      padding: 12px 10px;
      border-radius: 60px;
      margin: 24px 0 20px 0;
    }

    .action-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 6px;
      color: #006b7a;
      font-weight: 500;
      font-size: 0.9rem;
    }

    .action-item i {
      font-size: 1.5rem;
      background: white;
      padding: 10px;
      border-radius: 40px;
      width: 50px;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 4px 10px rgba(0,150,160,0.15);
      color: #006a7a;
      transition: 0.15s;
    }

    .action-item:hover i {
      background: #00bcd4;
      color: white;
    }

    /* company profile line */
    .company-line {
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: white;
      border: 1px solid #cae3e8;
      padding: 12px 18px;
      border-radius: 30px;
      margin-bottom: 22px;
    }

    .company-line span {
      font-weight: 600;
      color: #1b4e5b;
      font-size: 1rem;
    }

    .company-line i {
      color: #00a5b9;
      font-size: 1.3rem;
    }

    /* bottom nav */
    .bottom-nav {
      display: flex;
      align-items: center;
      justify-content: space-around;
      background: #ffffff;
      padding: 8px 0 6px 0;
      border-top: 2px solid #e3f0f3;
      margin-top: 12px;
    }

    .nav-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      color: #597e89;
      font-size: 0.75rem;
      font-weight: 500;
      gap: 4px;
      transition: 0.1s;
    }

    .nav-item i {
      font-size: 1.4rem;
      color: #89b8c5;
    }

    .nav-item.active {
      color: #006a7a;
    }

    .nav-item.active i {
      color: #00b2c9;
      text-shadow: 0 2px 6px #b0e6ee;
    }

    /* small utilities */
    .muted-currency {
      color: #5e8e99;
      font-size: 0.8rem;
      font-weight: 500;
    }
  </style>
</head>
<body>
  <div class="phone">
    <!-- header with CIUE and new opportunity text -->
    <div class="welcome-section">
      <div class="hello-tag"><i class="far fa-hand-peace" style="margin-right: 6px;"></i> CIUE · FRESH</div>
      <div class="main-headline">
        NEW OPPORTUNITIES <span>and challenges work together to create a better future</span>
      </div>
      <div class="divider"></div>
    </div>

    <!-- Collaboration belief line (exactly like original but fresh) -->
    <div class="collab-text">
      <i class="fas fa-handshake"></i> Collaboration. We believe that every employee can:
    </div>

    <!-- Task Hall area with teaser / VAF / Out of Ideas -->
    <div class="task-hall-label">
      <i class="fas fa-clipboard-list"></i>
      <h3>Task Hall</h3>
    </div>
    <span class="teaser-badge">✨ TEASER · fresh tasks</span>

    <div class="card-grid">
      <!-- TEASER card -->
      <div class="reward-card">
        <div class="card-left">
          <div class="card-icon"><i class="fas fa-bolt"></i></div>
          <span class="card-title">TEASER</span>
        </div>
        <div class="card-value">+1,200 <small>UGX</small></div>
      </div>
      <!-- VAF card -->
      <div class="reward-card">
        <div class="card-left">
          <div class="card-icon"><i class="fas fa-chart-line"></i></div>
          <span class="card-title">VAF</span>
        </div>
        <div class="card-value">+1,200 <small>UGX</small></div>
      </div>
      <!-- Out of Ideas card -->
      <div class="reward-card">
        <div class="card-left">
          <div class="card-icon"><i class="fas fa-lightbulb"></i></div>
          <span class="card-title">Out of Ideas</span>
        </div>
        <div class="card-value">+1,200 <small>UGX</small></div>
      </div>
    </div>

    <!-- Recharge · Withdraw · Company Profile (original structure) -->
    <div class="action-row">
      <div class="action-item">
        <i class="fas fa-wallet"></i>
        <span>Recharge</span>
      </div>
      <div class="action-item">
        <i class="fas fa-hand-holding-usd"></i>
        <span>Withdraw</span>
      </div>
      <div class="action-item">
        <i class="fas fa-building"></i>
        <span>Company</span>
      </div>
    </div>

    <!-- subtle extra: Company Profile line (exactly as in screenshot) -->
    <div class="company-line">
      <span><i class="far fa-id-card" style="margin-right: 10px; color: #00838f;"></i> Company Profile</span>
      <i class="fas fa-chevron-right"></i>
    </div>

    <!-- bottom nav: Home | Task | Level | Income | Me (original) -->
    <div class="bottom-nav">
      <div class="nav-item active">
        <i class="fas fa-home"></i>
        <span>Home</span>
      </div>
      <div class="nav-item">
        <i class="fas fa-tasks"></i>
        <span>Task</span>
      </div>
      <div class="nav-item">
        <i class="fas fa-chart-simple"></i>
        <span>Level</span>
      </div>
      <div class="nav-item">
        <i class="fas fa-coins"></i>
        <span>Income</span>
      </div>
      <div class="nav-item">
        <i class="fas fa-user"></i>
        <span>Me</span>
      </div>
    </div>

    <!-- tiny footnote (just for style) -->
    <div style="text-align: center; margin: 18px 0 8px 0; color: #97b7c0; font-size: 0.65rem;">
      <i class="fas fa-circle" style="font-size: 0.2rem; vertical-align: middle;"></i> CIUE · fresh opportunities
    </div>
  </div>

  <!-- publish hint (discreet) -->
  <div style="max-width:390px; margin:24px auto 0; text-align: center; font-size:0.8rem; background: #fff4e6; padding: 12px 14px; border-radius: 60px; color:#3a5e69;">
    <i class="fas fa-globe" style="margin-right: 8px;"></i> 
    <strong>How to publish (make it live):</strong> Upload these 3 files (HTML, and optional CSS/icon libs are CDN) to any web host — Netlify, Vercel, GitHub Pages, or even a basic FTP. Just drag and drop.
  </div>
</body>
</html>
