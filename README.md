<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>AETHERNET PRO - Advanced Multi-Vector Security Audit Tool</title>
  <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;700&family=Orbitron:wght@400;500;700;900&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />
  <style>
    /* === CSS Variables === */
    :root {
      --bg: #0a0a0f;
      --bg-card: #0f1019;
      --bg-card-hover: #141520;
      --fg: #e0e0e8;
      --fg-muted: #6b6b80;
      --accent: #00ff88;
      --accent-dim: rgba(0, 255, 136, 0.12);
      --accent-glow: rgba(0, 255, 136, 0.35);
      --cyan: #00d4ff;
      --red: #ff3355;
      --red-dim: rgba(255, 51, 85, 0.1);
      --border: #1a1a2e;
      --border-accent: rgba(0, 255, 136, 0.2);
      --radius: 10px;
      --font-display: 'Orbitron', sans-serif;
      --font-mono: 'JetBrains Mono', monospace;
    }

    /* === Reset & Base === */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      font-family: var(--font-mono);
      background: var(--bg);
      color: var(--fg);
      line-height: 1.7;
      overflow-x: hidden;
      position: relative;
    }

    /* === Animated Background === */
    body::before {
      content: '';
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background:
        radial-gradient(ellipse 600px 400px at 20% 10%, rgba(0, 255, 136, 0.04) 0%, transparent 70%),
        radial-gradient(ellipse 500px 500px at 80% 80%, rgba(0, 212, 255, 0.03) 0%, transparent 70%),
        radial-gradient(ellipse 300px 300px at 50% 50%, rgba(255, 51, 85, 0.02) 0%, transparent 70%);
      pointer-events: none;
      z-index: 0;
    }

    /* Grid pattern overlay */
    body::after {
      content: '';
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background-image:
        linear-gradient(rgba(0, 255, 136, 0.015) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0, 255, 136, 0.015) 1px, transparent 1px);
      background-size: 60px 60px;
      pointer-events: none;
      z-index: 0;
    }

    /* === Scanline animation === */
    @keyframes scanline {
      0% { transform: translateY(-100vh); }
      100% { transform: translateY(100vh); }
    }

    .scanline {
      position: fixed;
      top: 0; left: 0; right: 0;
      height: 3px;
      background: linear-gradient(90deg, transparent, var(--accent-glow), transparent);
      animation: scanline 6s linear infinite;
      pointer-events: none;
      z-index: 1;
      opacity: 0.4;
    }

    /* === Layout === */
    .container {
      max-width: 900px;
      margin: 0 auto;
      padding: 0 24px;
      position: relative;
      z-index: 2;
    }

    /* === Hero Section === */
    .hero {
      text-align: center;
      padding: 60px 0 40px;
      position: relative;
    }

    .badges {
      display: flex;
      justify-content: center;
      gap: 12px;
      flex-wrap: wrap;
      margin-bottom: 28px;
    }

    .badge {
      display: inline-flex;
      align-items: center;
      gap: 7px;
      padding: 7px 16px;
      border-radius: 6px;
      font-size: 12px;
      font-weight: 500;
      letter-spacing: 0.5px;
      text-transform: uppercase;
      border: 1px solid var(--border);
      background: var(--bg-card);
      transition: all 0.3s ease;
    }

    .badge:hover {
      border-color: var(--border-accent);
      background: var(--accent-dim);
    }

    .badge.blue { color: #4da6ff; border-color: rgba(77, 166, 255, 0.2); }
    .badge.dark { color: #aaa; }
    .badge.green { color: var(--accent); border-color: var(--border-accent); }
    .badge.red { color: var(--red); border-color: rgba(255, 51, 85, 0.25); background: var(--red-dim); }

    .badge i { font-size: 13px; }

    .hero-title {
      font-family: var(--font-display);
      font-size: clamp(36px, 7vw, 64px);
      font-weight: 900;
      letter-spacing: 4px;
      margin-bottom: 16px;
      position: relative;
      display: inline-block;
    }

    .hero-title .lightning {
      color: var(--accent);
      text-shadow: 0 0 30px var(--accent-glow), 0 0 60px rgba(0, 255, 136, 0.15);
      animation: pulse-glow 3s ease-in-out infinite;
    }

    @keyframes pulse-glow {
      0%, 100% { text-shadow: 0 0 30px var(--accent-glow), 0 0 60px rgba(0, 255, 136, 0.15); }
      50% { text-shadow: 0 0 40px var(--accent-glow), 0 0 80px rgba(0, 255, 136, 0.25); }
    }

    .hero-subtitle {
      font-size: 16px;
      font-weight: 500;
      color: var(--fg);
      margin-bottom: 6px;
    }

    .hero-desc {
      font-size: 13px;
      color: var(--fg-muted);
      font-style: italic;
    }

    /* === Divider === */
    .divider {
      border: none;
      height: 1px;
      background: linear-gradient(90deg, transparent, var(--border-accent), var(--border), var(--border-accent), transparent);
      margin: 40px 0;
    }

    /* === Section Headers === */
    .section-header {
      margin-bottom: 24px;
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .section-header .icon-wrap {
      width: 38px;
      height: 38px;
      border-radius: 8px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
      flex-shrink: 0;
    }

    .section-header h2 {
      font-family: var(--font-display);
      font-size: clamp(18px, 3.5vw, 24px);
      font-weight: 700;
      letter-spacing: 1.5px;
    }

    .icon-green { background: var(--accent-dim); color: var(--accent); border: 1px solid var(--border-accent); }
    .icon-cyan { background: rgba(0, 212, 255, 0.1); color: var(--cyan); border: 1px solid rgba(0, 212, 255, 0.2); }
    .icon-red { background: var(--red-dim); color: var(--red); border: 1px solid rgba(255, 51, 85, 0.2); }
    .icon-gold { background: rgba(255, 200, 50, 0.1); color: #ffc832; border: 1px solid rgba(255, 200, 50, 0.2); }

    /* === Text Content === */
    .text-block {
      margin-bottom: 20px;
      font-size: 13.5px;
      color: #b0b0c0;
    }

    .text-block b, .text-block strong {
      color: var(--fg);
      font-weight: 600;
    }

    /* === Feature Lists === */
    .feature-list {
      list-style: none;
      margin-bottom: 28px;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .feature-list li {
      position: relative;
      padding: 12px 16px 12px 44px;
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      font-size: 13px;
      color: #b0b0c0;
      transition: all 0.3s ease;
      line-height: 1.6;
    }

    .feature-list li:hover {
      border-color: var(--border-accent);
      background: var(--bg-card-hover);
      transform: translateX(4px);
    }

    .feature-list li::before {
      content: '';
      position: absolute;
      left: 16px;
      top: 50%;
      transform: translateY(-50%);
      width: 8px;
      height: 8px;
      border-radius: 2px;
      background: var(--accent);
      box-shadow: 0 0 8px var(--accent-glow);
    }

    .feature-list li b, .feature-list li strong {
      color: var(--fg);
    }

    /* === Sub-section headers === */
    .sub-header {
      font-family: var(--font-display);
      font-size: 14px;
      font-weight: 500;
      letter-spacing: 1px;
      margin: 28px 0 14px;
      padding-left: 12px;
      border-left: 3px solid var(--accent);
      color: var(--accent);
    }

    /* === Hardware Tables === */
    .hw-section {
      margin-bottom: 36px;
    }

    .hw-section-title {
      font-family: var(--font-display);
      font-size: 13px;
      font-weight: 500;
      letter-spacing: 1px;
      color: var(--cyan);
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .hw-section-title i {
      font-size: 12px;
      opacity: 0.7;
    }

    .hw-table {
      width: 100%;
      border-collapse: collapse;
      border-radius: var(--radius);
      overflow: hidden;
      border: 1px solid var(--border);
      margin-bottom: 8px;
    }

    .hw-table thead th {
      background: rgba(0, 212, 255, 0.06);
      padding: 10px 16px;
      font-size: 11px;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 1px;
      color: var(--cyan);
      text-align: left;
      border-bottom: 1px solid var(--border);
    }

    .hw-table thead th:nth-child(2) { text-align: center; }

    .hw-table tbody td {
      padding: 9px 16px;
      font-size: 12.5px;
      border-bottom: 1px solid rgba(255,255,255,0.03);
      color: #a0a0b4;
    }

    .hw-table tbody td:nth-child(2) {
      text-align: center;
    }

    .hw-table tbody tr {
      transition: background 0.2s ease;
    }

    .hw-table tbody tr:hover {
      background: rgba(0, 255, 136, 0.02);
    }

    .hw-table tbody tr:last-child td {
      border-bottom: none;
    }

    .pin-code {
      display: inline-block;
      background: var(--accent-dim);
      color: var(--accent);
      font-weight: 700;
      padding: 2px 10px;
      border-radius: 4px;
      font-size: 12px;
      border: 1px solid var(--border-accent);
    }

    .hw-note {
      font-size: 11.5px;
      color: var(--fg-muted);
      font-style: italic;
      margin-bottom: 20px;
      padding-left: 4px;
    }

    .hw-note b { color: var(--red); font-style: normal; }

    /* === Warning Box === */
    .warning-box {
      background: var(--red-dim);
      border-left: 4px solid var(--red);
      padding: 20px 24px;
      border-radius: 0 var(--radius) var(--radius) 0;
      margin: 28px 0;
    }

    .warning-box h3 {
      font-family: var(--font-display);
      font-size: 15px;
      color: var(--red);
      margin-bottom: 10px;
      letter-spacing: 1px;
    }

    .warning-box p {
      font-size: 13px;
      color: #cc8899;
      line-height: 1.8;
    }

    .warning-box b, .warning-box strong {
      color: var(--red);
    }

    /* === Premium CTA Section === */
    .premium-section {
      text-align: center;
      padding: 48px 24px;
      margin: 20px 0;
      background: linear-gradient(135deg, rgba(0,255,136,0.03) 0%, rgba(0,212,255,0.03) 50%, rgba(255,200,50,0.03) 100%);
      border: 1px solid var(--border);
      border-radius: 16px;
      position: relative;
      overflow: hidden;
    }

    .premium-section::before {
      content: '';
      position: absolute;
      top: -1px; left: -1px; right: -1px; bottom: -1px;
      border-radius: 16px;
      background: linear-gradient(135deg, var(--accent), var(--cyan), #ffc832, var(--accent));
      background-size: 300% 300%;
      animation: border-shift 6s ease infinite;
      z-index: -1;
      opacity: 0.15;
    }

    @keyframes border-shift {
      0%, 100% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
    }

    .premium-section h2 {
      font-family: var(--font-display);
      font-size: clamp(18px, 4vw, 26px);
      font-weight: 700;
      letter-spacing: 2px;
      margin-bottom: 12px;
      background: linear-gradient(90deg, var(--accent), var(--cyan));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .premium-section .premium-desc {
      font-size: 13px;
      color: var(--fg-muted);
      margin-bottom: 20px;
    }

    .premium-benefits {
      text-align: left;
      display: inline-block;
      margin-bottom: 28px;
    }

    .premium-benefits p {
      font-size: 13px;
      color: #b0b0c0;
      padding: 4px 0;
    }

    .premium-benefits .check {
      color: var(--accent);
      margin-right: 6px;
    }

    .price-tag {
      font-family: var(--font-display);
      font-size: clamp(22px, 5vw, 32px);
      font-weight: 900;
      color: var(--fg);
      margin-bottom: 24px;
      letter-spacing: 2px;
    }

    .price-tag span { color: var(--accent); }

    .cta-btn {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      padding: 14px 36px;
      border-radius: 8px;
      font-family: var(--font-display);
      font-size: 13px;
      font-weight: 700;
      letter-spacing: 1.5px;
      text-transform: uppercase;
      text-decoration: none;
      color: #000;
      background: linear-gradient(135deg, var(--accent), #00cc6a);
      border: none;
      cursor: pointer;
      transition: all 0.3s ease;
      box-shadow: 0 4px 24px rgba(0, 255, 136, 0.25);
      position: relative;
      overflow: hidden;
    }

    .cta-btn::after {
      content: '';
      position: absolute;
      top: -50%; left: -50%;
      width: 200%; height: 200%;
      background: linear-gradient(45deg, transparent 30%, rgba(255,255,255,0.15) 50%, transparent 70%);
      transform: translateX(-100%);
      transition: transform 0.6s ease;
    }

    .cta-btn:hover::after {
      transform: translateX(100%);
    }

    .cta-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 32px rgba(0, 255, 136, 0.35);
    }

    .cta-btn:active {
      transform: translateY(0);
    }

    .cta-note {
      font-size: 11.5px;
      color: var(--fg-muted);
      margin-top: 16px;
      font-style: italic;
    }

    /* === Preview Section === */
    .preview-block {
      margin-bottom: 28px;
    }

    .preview-label {
      font-size: 13px;
      font-weight: 600;
      color: var(--fg);
      margin-bottom: 12px;
    }

    .preview-placeholder {
      width: 100%;
      aspect-ratio: 16/9;
      border-radius: var(--radius);
      border: 1px solid var(--border);
      background: var(--bg-card);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 12px;
      color: var(--fg-muted);
      font-size: 12px;
      overflow: hidden;
      position: relative;
    }

    .preview-placeholder i {
      font-size: 36px;
      opacity: 0.3;
    }

    .preview-placeholder .fake-screen {
      position: absolute;
      top: 0; left: 0; right: 0; bottom: 0;
      opacity: 0.04;
      background:
        repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,255,136,0.3) 2px, rgba(0,255,136,0.3) 4px);
    }

    /* === Footer === */
    footer {
      text-align: center;
      padding: 40px 0;
      font-size: 12px;
      color: var(--fg-muted);
    }

    footer span { color: var(--red); }

    /* === Floating particles === */
    .particle {
      position: fixed;
      width: 2px;
      height: 2px;
      background: var(--accent);
      border-radius: 50%;
      pointer-events: none;
      z-index: 1;
      opacity: 0;
      animation: float-up linear infinite;
    }

    @keyframes float-up {
      0% { opacity: 0; transform: translateY(0) scale(1); }
      10% { opacity: 0.6; }
      90% { opacity: 0.1; }
      100% { opacity: 0; transform: translateY(-100vh) scale(0.3); }
    }

    /* === Highlight block for "DO NOT" warnings === */
    .do-not {
      color: var(--red);
      font-weight: 700;
    }

    /* === Important callout === */
    .important-callout {
      background: rgba(255, 200, 50, 0.06);
      border: 1px solid rgba(255, 200, 50, 0.15);
      border-radius: var(--radius);
      padding: 14px 18px;
      margin: 12px 0 20px;
      font-size: 12.5px;
      color: #c0b070;
      display: flex;
      gap: 10px;
      align-items: flex-start;
    }

    .important-callout i {
      color: #ffc832;
      margin-top: 3px;
      flex-shrink: 0;
    }

    .important-callout b { color: #ffc832; }

    /* === Scroll reveal === */
    .reveal {
      opacity: 0;
      transform: translateY(20px);
      transition: opacity 0.6s ease, transform 0.6s ease;
    }

    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* === Responsive === */
    @media (max-width: 640px) {
      .container { padding: 0 16px; }
      .hero { padding: 40px 0 28px; }
      .badges { gap: 8px; }
      .badge { padding: 5px 10px; font-size: 10px; }
      .feature-list li { padding-left: 36px; font-size: 12px; }
      .feature-list li::before { left: 12px; width: 6px; height: 6px; }
      .hw-table thead th, .hw-table tbody td { padding: 7px 10px; font-size: 11px; }
      .pin-code { font-size: 10.5px; padding: 2px 7px; }
      .premium-section { padding: 32px 16px; }
    }

    /* === Reduced motion === */
    @media (prefers-reduced-motion: reduce) {
      .scanline, .particle { animation: none !important; display: none; }
      .reveal { opacity: 1; transform: none; transition: none; }
      .cta-btn::after { transition: none; }
      .premium-section::before { animation: none; }
      .hero-title .lightning { animation: none; }
    }
  </style>
</head>
<body>

  <!-- Scanline effect -->
  <div class="scanline" aria-hidden="true"></div>

  <!-- ==================== HERO ==================== -->
  <header class="hero">
    <div class="container">
      <div class="badges">
        <span class="badge blue"><i class="fa-solid fa-microchip"></i> Version 1.0</span>
        <span class="badge dark"><i class="fa-solid fa-cube"></i> ESP32 + BW16</span>
        <span class="badge green"><i class="fa-solid fa-shield-halved"></i> PREMIUM</span>
      </div>
      <div style="margin-bottom:20px;">
        <span class="badge red"><i class="fa-solid fa-triangle-exclamation"></i> Educational Purpose Only</span>
      </div>
      <h1 class="hero-title">
        <span class="lightning">AETHERNET</span> PRO
      </h1>
      <p class="hero-subtitle">Advanced Multi-Vector WiFi & Bluetooth Security Audit Tool</p>
      <p class="hero-desc">A single module to stress-test the resilience of 2.4GHz, 5GHz, and Bluetooth networks.</p>
    </div>
  </header>

  <div class="container">

    <hr class="divider" />

    <!-- ==================== WHY DIFFERENT ==================== -->
    <section class="reveal">
      <div class="section-header">
        <div class="icon-wrap icon-green"><i class="fa-solid fa-star"></i></div>
        <h2>WHY AETHERNET PRO IS DIFFERENT</h2>
      </div>
      <p class="text-block">
        Most tools rely solely on the ESP32, which causes bottlenecks during heavy attacks. AETHERNET PRO utilizes a <strong>Distributed Attack System</strong>, combining the power of 3 distinct microcontrollers simultaneously:
      </p>
      <ul class="feature-list">
        <li><strong>ESP32:</strong> Acts as the Master Controller, Web Server, and Password Capture engine.</li>
        <li><strong>BW16:</strong> Dedicated solely to handling Deauthentication attacks, providing extreme stability for both 2.4GHz & 5GHz networks.</li>
        <li><strong>Dual NRF24L01:</strong> Runs Continuous Wave Jamming to test Bluetooth frequencies without consuming the main CPU's resources.</li>
      </ul>
      <p class="text-block"><strong>The result?</strong> Attacks run smoothly, the UI remains highly responsive, and the success rate of credential capture is significantly higher.</p>
    </section>

    <hr class="divider" />

    <!-- ==================== KEY FEATURES ==================== -->
    <section class="reveal">
      <div class="section-header">
        <div class="icon-wrap icon-cyan"><i class="fa-solid fa-crosshairs"></i></div>
        <h2>KEY FEATURES</h2>
      </div>

      <h3 class="sub-header">WiFi Attacks (2.4GHz & 5GHz)</h3>
      <ul class="feature-list">
        <li><strong>Smart Deauth Attack:</strong> Selectively disconnects targets using the BW16, forcing devices to automatically connect to our fake network (Evil Twin).</li>
        <li><strong>Evil Twin & Captive Portal:</strong> 100% identical network cloning (Including SSID & Channel). Supports Custom HTML for highly realistic phishing pages.</li>
        <li><strong>Rogue AP:</strong> Creates a standalone fake Access Point with login pages (Google/Facebook style) to capture credentials.</li>
        <li><strong>Beacon Spam:</strong> Floods the area with hundreds of fake SSIDs (Customizable up to 50 different names).</li>
        <li><strong>Password Auto-Verify:</strong> When a victim enters a password on the phishing page, the ESP32 automatically verifies its correctness against the real router in real-time.</li>
      </ul>

      <h3 class="sub-header">Bluetooth Attacks</h3>
      <ul class="feature-list">
        <li><strong>Dual Channel BT Jammer:</strong> Uses 2x NRF24L01 (HSPI & VSPI) to perform Continuous Wave Jamming on BT frequencies, testing the vulnerability of Bluetooth IoT devices.</li>
      </ul>

      <h3 class="sub-header">Interface & Control</h3>
      <ul class="feature-list">
        <li><strong>Dark Web Dashboard:</strong> Futuristic web interface, mobile-responsive, equipped with a color theme system.</li>
        <li><strong>3D OLED Menu:</strong> Physical navigation using 4 buttons with a 3D Scroll style menu and custom icons.</li>
        <li><strong>File Manager:</strong> Upload/Edit phishing HTML templates directly from the browser.</li>
        <li><strong>BW16 Auto-Link:</strong> Automatically detects and synchronizes with the BW16 module via Serial.</li>
      </ul>
    </section>

    <hr class="divider" />

    <!-- ==================== HARDWARE PINOUT ==================== -->
    <section class="reveal">
      <div class="section-header">
        <div class="icon-wrap icon-gold"><i class="fa-solid fa-screwdriver-wrench"></i></div>
        <h2>HARDWARE & PINOUT SPECIFICATIONS</h2>
      </div>

      <div class="warning-box">
        <p><strong>STRICT WARNING:</strong> This firmware is hard-coded specifically for the pinout below. Using different pins will cause immediate malfunction or permanent hardware damage. Ensure strict adherence to this wiring diagram.</p>
      </div>

      <!-- OLED -->
      <div class="hw-section">
        <div class="hw-section-title"><i class="fa-solid fa-display"></i> 1. OLED Display (SSD1306 128x64 - I2C)</div>
        <table class="hw-table">
          <thead><tr><th>OLED Pin</th><th>ESP32 Pin</th><th>Notes</th></tr></thead>
          <tbody>
            <tr><td>SDA</td><td><span class="pin-code">GPIO 4</span></td><td>Data Line</td></tr>
            <tr><td>SCL</td><td><span class="pin-code">GPIO 5</span></td><td>Clock Line</td></tr>
            <tr><td>VCC</td><td><span class="pin-code">3.3V</span></td><td class="do-not">DO NOT use 5V</td></tr>
            <tr><td>GND</td><td><span class="pin-code">GND</span></td><td>Common Ground</td></tr>
          </tbody>
        </table>
        <p class="hw-note">* I2C Address must be set to <b>0x3C</b>.</p>
      </div>

      <!-- BW16 -->
      <div class="hw-section">
        <div class="hw-section-title"><i class="fa-solid fa-satellite-dish"></i> 2. BW16 Deauther Module (RTL8720DN - UART1)</div>
        <table class="hw-table">
          <thead><tr><th>BW16 Pin</th><th>ESP32 Pin</th><th>Notes</th></tr></thead>
          <tbody>
            <tr><td>PB1 (RX)</td><td><span class="pin-code">GPIO 25</span></td><td>ESP32 TX → BW16 RX</td></tr>
            <tr><td>PB2 (TX)</td><td><span class="pin-code">GPIO 26</span></td><td>ESP32 RX ← BW16 TX</td></tr>
            <tr><td>GND</td><td><span class="pin-code">GND</span></td><td>Common Ground (CRITICAL)</td></tr>
          </tbody>
        </table>
        <p class="hw-note">* BW16 requires its own separate Deauther firmware to function. Only connect TX to RX and RX to TX.</p>
      </div>

      <!-- NRF24L01 #1 -->
      <div class="hw-section">
        <div class="hw-section-title"><i class="fa-solid fa-tower-broadcast"></i> 3. NRF24L01 #1 - Bluetooth Jammer (HSPI Bus)</div>
        <table class="hw-table">
          <thead><tr><th>NRF24L01 Pin</th><th>ESP32 Pin</th><th>Notes</th></tr></thead>
          <tbody>
            <tr><td>CE</td><td><span class="pin-code">GPIO 16</span></td><td>Chip Enable</td></tr>
            <tr><td>CSN</td><td><span class="pin-code">GPIO 15</span></td><td>Chip Select</td></tr>
            <tr><td>MOSI</td><td><span class="pin-code">GPIO 13</span></td><td>HSPI Default</td></tr>
            <tr><td>MISO</td><td><span class="pin-code">GPIO 12</span></td><td>HSPI Default</td></tr>
            <tr><td>SCK</td><td><span class="pin-code">GPIO 14</span></td><td>HSPI Default</td></tr>
            <tr><td>VCC</td><td><span class="pin-code">3.3V</span></td><td class="do-not">DO NOT use 5V</td></tr>
            <tr><td>GND</td><td><span class="pin-code">GND</span></td><td>Common Ground</td></tr>
          </tbody>
        </table>
      </div>

      <!-- NRF24L01 #2 -->
      <div class="hw-section">
        <div class="hw-section-title"><i class="fa-solid fa-tower-broadcast"></i> 4. NRF24L01 #2 - Bluetooth Jammer (VSPI Bus)</div>
        <table class="hw-table">
          <thead><tr><th>NRF24L01 Pin</th><th>ESP32 Pin</th><th>Notes</th></tr></thead>
          <tbody>
            <tr><td>CE</td><td><span class="pin-code">GPIO 22</span></td><td>Chip Enable</td></tr>
            <tr><td>CSN</td><td><span class="pin-code">GPIO 21</span></td><td>Chip Select</td></tr>
            <tr><td>MOSI</td><td><span class="pin-code">GPIO 23</span></td><td>VSPI Default</td></tr>
            <tr><td>MISO</td><td><span class="pin-code">GPIO 19</span></td><td>VSPI Default</td></tr>
            <tr><td>SCK</td><td><span class="pin-code">GPIO 18</span></td><td>VSPI Default</td></tr>
            <tr><td>VCC</td><td><span class="pin-code">3.3V</span></td><td class="do-not">DO NOT use 5V</td></tr>
            <tr><td>GND</td><td><span class="pin-code">GND</span></td><td>Common Ground</td></tr>
          </tbody>
        </table>

        <div class="important-callout">
          <i class="fa-solid fa-circle-exclamation"></i>
          <div>Solder a <b>10uF Capacitor</b> directly between the VCC and GND pins on <b>BOTH</b> NRF24L01 modules to prevent voltage drops and crashes during transmission.</div>
        </div>
      </div>

      <!-- Buttons -->
      <div class="hw-section">
        <div class="hw-section-title"><i class="fa-solid fa-hand-pointer"></i> 5. Physical Control Buttons</div>
        <table class="hw-table">
          <thead><tr><th>Function</th><th>ESP32 Pin</th><th>Connection</th></tr></thead>
          <tbody>
            <tr><td>UP</td><td><span class="pin-code">GPIO 17</span></td><td>Button → GND (Uses Internal Pull-Up)</td></tr>
            <tr><td>DOWN</td><td><span class="pin-code">GPIO 33</span></td><td>Button → GND (Uses Internal Pull-Up)</td></tr>
            <tr><td>SELECT</td><td><span class="pin-code">GPIO 27</span></td><td>Button → GND (Uses Internal Pull-Up)</td></tr>
            <tr><td>BACK</td><td><span class="pin-code">GPIO 32</span></td><td>Button → GND (Uses Internal Pull-Up)</td></tr>
          </tbody>
        </table>
      </div>

      <!-- On-board -->
      <div class="hw-section">
        <div class="hw-section-title"><i class="fa-solid fa-lightbulb"></i> 6. On-Board Components</div>
        <table class="hw-table">
          <thead><tr><th>Component</th><th>Pin</th><th>Notes</th></tr></thead>
          <tbody>
            <tr><td>Built-in LED</td><td><span class="pin-code">GPIO 2</span></td><td>Used for Status Indicators</td></tr>
          </tbody>
        </table>
      </div>
    </section>

    <hr class="divider" />

    <!-- ==================== PREMIUM CTA ==================== -->
    <section class="reveal">
      <div class="premium-section">
        <h2>GET THE FULL / PREMIUM VERSION</h2>
        <p class="premium-desc">The file available in this repository is a <strong>Trial Version</strong>, strictly limited to initial demonstration.</p>
        <p class="premium-desc" style="margin-top:-12px;"><strong>Benefits of purchasing the Premium Version:</strong></p>
        <div class="premium-benefits">
          <p><span class="check"><i class="fa-solid fa-check"></i></span> No Time Limits (Trial is only 1 minute, Premium is Unlimited).</p>
          <p><span class="check"><i class="fa-solid fa-check"></i></span> No EEPROM Locks (Can be upgraded to future versions).</p>
          <p><span class="check"><i class="fa-solid fa-check"></i></span> Lifetime Updates (New features like Auto-Attack Sequence are in development).</p>
          <p><span class="check"><i class="fa-solid fa-check"></i></span> Technical Support via Telegram (Troubleshooting and custom wiring assistance).</p>
        </div>
        <div class="price-tag">RP <span>50.000</span></div>
        <a href="https://t.me/AtherNet29" class="cta-btn" target="_blank" rel="noopener noreferrer">
          <i class="fa-brands fa-telegram"></i> BUY NOW VIA TELEGRAM
        </a>
        <p class="cta-note">Click the button above to chat directly with the developer on Telegram.</p>
      </div>
    </section>

    <hr class="divider" />

    <!-- ==================== PREVIEW ==================== -->
    <section class="reveal">
      <div class="section-header">
        <div class="icon-wrap icon-cyan"><i class="fa-solid fa-camera"></i></div>
        <h2>PREVIEW & DOCUMENTATION</h2>
      </div>

      <div class="preview-block">
        <p class="preview-label">Web Dashboard Interface:</p>
        <div class="preview-placeholder">
          <div class="fake-screen" aria-hidden="true"></div>
          <i class="fa-solid fa-desktop"></i>
          <span>preview.jpg — Screenshot will appear here</span>
        </div>
      </div>

      <div class="preview-block">
        <p class="preview-label">Module Wiring Diagram:</p>
        <div class="preview-placeholder">
          <div class="fake-screen" aria-hidden="true"></div>
          <i class="fa-solid fa-diagram-project"></i>
          <span>wiring.jpg — Diagram will appear here</span>
        </div>
      </div>
    </section>

    <hr class="divider" />

    <!-- ==================== DISCLAIMER ==================== -->
    <section class="reveal">
      <div class="warning-box">
        <h3><i class="fa-solid fa-scale-balanced"></i> Legal Disclaimer</h3>
        <p>
          <strong>STRICT WARNING:</strong> This tool is created purely for <em>Penetration Testing</em> and <em>Educational Purposes</em> within the scope of network security. It is strictly forbidden to use this tool to attack, steal data, or disrupt networks that are NOT your property. Any form of abuse that violates your country's laws is <strong>NOT</strong> the responsibility of the Developer. By purchasing this firmware, you agree to these terms and conditions.
        </p>
      </div>
    </section>

  </div>

  <!-- ==================== FOOTER ==================== -->
  <footer>
    <div class="container">
      Built with <span>&#10084;</span> by AETHERNET Developer Team
    </div>
  </footer>

  <script>
    /* === Scroll Reveal with IntersectionObserver === */
    document.addEventListener('DOMContentLoaded', () => {
      const revealEls = document.querySelectorAll('.reveal');

      const observer = new IntersectionObserver((entries) => {
        entries.forEach((entry, idx) => {
          if (entry.isIntersecting) {
            // Stagger animation slightly based on index
            setTimeout(() => {
              entry.target.classList.add('visible');
            }, idx * 80);
            observer.unobserve(entry.target);
          }
        });
      }, {
        threshold: 0.08,
        rootMargin: '0px 0px -40px 0px'
      });

      revealEls.forEach(el => observer.observe(el));

      /* === Floating Particles === */
      const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
      if (!prefersReducedMotion) {
        const particleCount = 18;
        for (let i = 0; i < particleCount; i++) {
          createParticle();
        }
      }

      function createParticle() {
        const p = document.createElement('div');
        p.classList.add('particle');
        // Random horizontal position
        p.style.left = Math.random() * 100 + 'vw';
        // Random starting Y below viewport
        p.style.top = (60 + Math.random() * 40) + 'vh';
        // Random size
        const size = 1 + Math.random() * 2;
        p.style.width = size + 'px';
        p.style.height = size + 'px';
        // Random duration
        const dur = 8 + Math.random() * 12;
        p.style.animationDuration = dur + 's';
        // Random delay
        p.style.animationDelay = (Math.random() * dur) + 's';
        // Slight color variation
        if (Math.random() > 0.7) {
          p.style.background = 'var(--cyan)';
        }
        document.body.appendChild(p);
      }

      /* === Subtle parallax on hero === */
      if (!prefersReducedMotion) {
        const hero = document.querySelector('.hero');
        const heroTitle = document.querySelector('.hero-title');

        window.addEventListener('mousemove', (e) => {
          const cx = (e.clientX / window.innerWidth - 0.5) * 2;
          const cy = (e.clientY / window.innerHeight - 0.5) * 2;
          if (heroTitle) {
            heroTitle.style.transform = `translate(${cx * 4}px, ${cy * 3}px)`;
          }
        });
      }
    });
  </script>
</body>
</html>
