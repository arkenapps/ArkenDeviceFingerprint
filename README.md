<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Arken Windows Device Fingerprint Utility</title>
  <style>
    :root{
      --bg:#0b1220;
      --panel:rgba(255,255,255,.07);
      --panel2:rgba(255,255,255,.09);
      --line:rgba(255,255,255,.14);
      --text:#eaf0ff;
      --muted:rgba(234,240,255,.72);
      --accent:#46F3C7;
      --accent2:#867DFE;
      --warn:#fbbf24;
      --good:#22c55e;
      --shadow: 0 20px 60px rgba(0,0,0,.45);
      --radius:22px;
    }

    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: ui-sans-serif, system-ui, Segoe UI, Arial;
      color:var(--text);
      background:
        radial-gradient(900px 500px at 15% 10%, rgba(70,243,199,.18), transparent 60%),
        radial-gradient(900px 500px at 85% 20%, rgba(134,125,254,.18), transparent 60%),
        linear-gradient(180deg, #070b14, var(--bg));
      min-height:100vh;
    }

    .wrap{
      max-width:1100px;
      margin:0 auto;
      padding:26px 18px 40px;
    }

    .topbar{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:14px;
      padding:16px 18px;
      border:1px solid var(--line);
      background:linear-gradient(135deg, rgba(255,255,255,.08), rgba(255,255,255,.05));
      border-radius:var(--radius);
      box-shadow: var(--shadow);
      backdrop-filter: blur(10px);
    }

    .brand{
      display:flex;
      align-items:center;
      gap:12px;
      min-width:0;
    }

    .logo{
      width:46px;
      height:46px;
      border-radius:14px;
      display:grid;
      place-items:center;
      background:rgba(70,243,199,.16);
      border:1px solid rgba(70,243,199,.35);
      box-shadow: 0 10px 30px rgba(70,243,199,.12);
      font-size:22px;
    }

    .title{
      line-height:1.15;
      min-width:0;
    }
    .title h1{
      margin:0;
      font-size:18px;
      letter-spacing:.2px;
      white-space:nowrap;
      overflow:hidden;
      text-overflow:ellipsis;
    }
    .title p{
      margin:4px 0 0;
      color:var(--muted);
      font-size:12.5px;
      white-space:nowrap;
      overflow:hidden;
      text-overflow:ellipsis;
    }

    .links{
      display:flex;
      align-items:center;
      gap:10px;
      flex-wrap:wrap;
      justify-content:flex-end;
    }

    .btn{
      text-decoration:none;
      color:var(--text);
      font-weight:700;
      font-size:13px;
      padding:10px 14px;
      border-radius:999px;
      border:1px solid var(--line);
      background:rgba(255,255,255,.06);
      transition:.15s ease;
      display:inline-flex;
      align-items:center;
      gap:8px;
    }
    .btn:hover{ transform: translateY(-1px); background: rgba(255,255,255,.09); }
    .btn.primary{
      border-color: rgba(70,243,199,.35);
      background: linear-gradient(135deg, rgba(70,243,199,.18), rgba(134,125,254,.16));
    }

    .hero{
      margin-top:18px;
      display:grid;
      grid-template-columns: 1.1fr .9fr;
      gap:16px;
      align-items:stretch;
    }
    @media (max-width: 980px){
      .hero{ grid-template-columns:1fr; }
    }

    .card{
      border:1px solid var(--line);
      border-radius:var(--radius);
      background:rgba(255,255,255,.06);
      box-shadow: var(--shadow);
      backdrop-filter: blur(10px);
      padding:18px;
    }

    .hero h2{
      margin:0 0 10px;
      font-size:28px;
      letter-spacing:.2px;
    }
    .hero p{
      margin:0 0 14px;
      color:var(--muted);
      line-height:1.55;
      font-size:14.5px;
    }

    .badges{
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      margin-top:10px;
    }
    .badge{
      font-size:12px;
      font-weight:700;
      padding:7px 11px;
      border-radius:999px;
      border:1px solid var(--line);
      background:rgba(255,255,255,.06);
      color:var(--muted);
    }
    .badge.good{ color:#d7ffe9; border-color: rgba(34,197,94,.35); background: rgba(34,197,94,.12); }
    .badge.accent{ color:#dbfff6; border-color: rgba(70,243,199,.38); background: rgba(70,243,199,.12); }

    .screen{
      padding:14px;
      display:flex;
      flex-direction:column;
      gap:12px;
    }

    .shot{
      border-radius:18px;
      border:1px solid rgba(255,255,255,.16);
      background:linear-gradient(135deg, rgba(255,255,255,.06), rgba(255,255,255,.03));
      overflow:hidden;
    }
    .shot img{
      width:100%;
      display:block;
      aspect-ratio: 16/10;
      object-fit: cover;
    }
    .shot .ph{
      aspect-ratio: 16/10;
      display:grid;
      place-items:center;
      color:rgba(234,240,255,.55);
      font-weight:800;
      letter-spacing:.4px;
      font-size:13px;
      padding:24px;
      text-align:center;
    }

    .grid{
      margin-top:16px;
      display:grid;
      grid-template-columns: repeat(3, 1fr);
      gap:14px;
    }
    @media (max-width: 980px){ .grid{ grid-template-columns:1fr; } }

    .feature{
      padding:16px;
      border:1px solid var(--line);
      border-radius:20px;
      background:rgba(255,255,255,.06);
    }
    .feature h3{
      margin:0 0 8px;
      font-size:15px;
    }
    .feature p{
      margin:0;
      color:var(--muted);
      font-size:13.5px;
      line-height:1.55;
    }

    .section{
      margin-top:16px;
    }
    .section h2{
      margin:0 0 10px;
      font-size:18px;
      letter-spacing:.2px;
    }

    .list{
      margin:0;
      padding-left:18px;
      color:var(--muted);
      line-height:1.8;
      font-size:14px;
    }

    .code{
      margin-top:10px;
      border-radius:18px;
      border:1px solid rgba(255,255,255,.14);
      background:rgba(0,0,0,.28);
      padding:14px;
      overflow:auto;
      font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
      font-size:12.5px;
      color:rgba(234,240,255,.9);
      white-space:pre;
    }

    .note{
      margin-top:10px;
      padding:12px 14px;
      border-radius:18px;
      border:1px solid rgba(251,191,36,.28);
      background: rgba(251,191,36,.12);
      color: rgba(255,239,206,.95);
      font-size:13px;
      line-height:1.55;
    }

    .foot{
      margin-top:18px;
      padding:14px 12px;
      text-align:center;
      color:rgba(234,240,255,.55);
      font-size:12px;
    }
    .foot a{ color:rgba(234,240,255,.78); text-decoration:none; border-bottom:1px dashed rgba(234,240,255,.25); }
    .foot a:hover{ color:var(--text); border-bottom-color: rgba(234,240,255,.5); }
  </style>
</head>

<body>
  <div class="wrap">

    <!-- TOP BAR -->
    <header class="topbar">
      <div class="brand">
        <div class="logo">🔐</div>
        <div class="title">
          <h1>Arken Windows Device Fingerprint Utility</h1>
          <p>Offline • x64 & ARM64 • SHA-256 Device ID • Desktop output</p>
        </div>
      </div>
      <div class="links">
        <a class="btn primary" href="#" onclick="alert('Add your GitHub Releases link here'); return false;">⬇ Download</a>
        <a class="btn" href="https://www.arkenapps.com" target="_blank" rel="noreferrer">🌐 ArkenApps</a>
        <a class="btn" href="https://www.globalitsoft.com" target="_blank" rel="noreferrer">🌍 GlobalITSoft</a>
      </div>
    </header>

    <!-- HERO -->
    <section class="hero">
      <div class="card">
        <h2>Small tool. Big clarity.</h2>
        <p>
          A lightweight, offline Windows utility that generates a unique device fingerprint using system-level
          identifiers. Built for IT teams, developers, and support professionals who need a reliable way to identify
          and register Windows devices — fast and without dependencies.
        </p>

        <div class="badges">
          <span class="badge accent">Offline-first</span>
          <span class="badge good">x64 + ARM64</span>
          <span class="badge">No install</span>
          <span class="badge">Copy-friendly</span>
          <span class="badge">SHA-256</span>
        </div>

        <div class="section" style="margin-top:14px">
          <h2>Key features</h2>
          <ul class="list">
            <li>Works on <b>Windows x64 and ARM64</b></li>
            <li>Fully <b>offline</b> (no internet required)</li>
            <li>No installation or dependencies</li>
            <li>Generates a stable <b>SHA-256 Device ID</b></li>
            <li>Shows <b>manufacturer, model, device type</b></li>
            <li>Saves results automatically to the <b>Desktop</b></li>
          </ul>
        </div>
      </div>

      <div class="card screen">
        <h2 style="font-size:18px;margin:0">Screenshot</h2>
        <div class="shot">
          <!-- Replace screenshot.png with your image -->
          <!-- If you don't have a screenshot yet, keep placeholder block below -->
          <!-- <img src="screenshot.png" alt="Console Output Screenshot" /> -->
          <div class="ph">
            Place your screenshot here.<br/><br/>
            Save an image as <b>screenshot.png</b> in the same folder<br/>
            and uncomment the &lt;img&gt; tag.
          </div>
        </div>

        <div class="note">
          ✅ Tip: After you upload to GitHub, you can reference the screenshot from the repo and it will render on this page too.
        </div>
      </div>
    </section>

    <!-- FEATURE GRID -->
    <section class="grid">
      <div class="feature">
        <h3>🔒 Privacy-first</h3>
        <p>No personal data is collected. Nothing is transmitted outside the device. Outputs stay local.</p>
      </div>
      <div class="feature">
        <h3>⚙ Reliable identifiers</h3>
        <p>Uses BIOS Serial, System UUID, and Machine GUID, plus vendor/model context for clarity.</p>
      </div>
      <div class="feature">
        <h3>🚀 Fast & portable</h3>
        <p>Runs instantly. No runtime. No setup. Perfect for support, inventory, and licensing workflows.</p>
      </div>
    </section>

    <!-- DETAILS -->
    <section class="card section">
      <h2>What information does it collect?</h2>
      <ul class="list">
        <li><b>BIOS Serial Number</b></li>
        <li><b>System UUID</b></li>
        <li><b>Windows Machine GUID</b></li>
        <li><b>System Manufacturer</b> (Dell, HP, Lenovo, etc.)</li>
        <li><b>System Model</b> (Latitude, ThinkPad, Surface, etc.)</li>
        <li><b>Device Type</b> (Laptop, Desktop, Virtual Machine)</li>
      </ul>

      <div class="note">
        <b>No personal data is collected.</b> This tool is intended for device identification and support workflows.
      </div>
    </section>

    <section class="card section">
      <h2>Device ID explained</h2>
      <p style="margin:0;color:var(--muted);line-height:1.65">
        The Device ID is a <b>SHA-256</b> hash generated from multiple system identifiers. This provides high uniqueness,
        reasonable stability, and safe sharing (raw identifiers are not exposed in the Device ID itself).
      </p>

      <div class="section" style="margin-top:12px">
        <h2>Typical output</h2>
        <div class="code">🔐 Arken Windows Device Fingerprint Utility
===========================================
Manufacturer : Dell Inc.
Model        : Latitude 5420
Device Type  : Laptop
-------------------------------------------
BIOS Serial  : 35XPNJ3
System UUID  : 4C4C4544-0035-5810-8050-B3C04F4E4A33
Machine GUID : bce57c64-4cbb-4360-ae8b-b3f125fe1372
Device ID    : 7598d8de22505a946eb6858198736cbd2a84be451008939486bbba303d7ef9a9

Saved to: C:\Users\...\Desktop\device_fingerprint.txt</div>
      </div>
    </section>

    <section class="card section">
      <h2>Usage notice</h2>
      <p style="margin:0;color:var(--muted);line-height:1.65">
        This utility is intended for use on systems you own or are authorized to access. Use should comply with
        applicable laws, organizational policies, and permissions. ArkenApps assumes no responsibility for misuse.
      </p>
    </section>

    <footer class="foot">
      Developed by <b>ArkenStone</b> •
      <a href="https://www.arkenapps.com" target="_blank" rel="noreferrer">arkenapps.com</a> •
      <a href="https://www.globalitsoft.com" target="_blank" rel="noreferrer">globalitsoft.com</a> •
      © 2026 ArkenApps
    </footer>

  </div>
</body>
</html>
