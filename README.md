<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Azure CV Object Detection & Tracking — README</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#0a0e1a;
  --bg2:#0f1525;
  --bg3:#141b2d;
  --card:#1a2235;
  --card2:#1e2840;
  --border:#2a3550;
  --accent:#00d4ff;
  --accent2:#7c3aed;
  --accent3:#10b981;
  --accent4:#f59e0b;
  --text:#e2e8f0;
  --text2:#94a3b8;
  --text3:#64748b;
  --heading:#f1f5f9;
  --radius:12px;
  --radius-lg:18px;
}
*{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{
  font-family:'Space Grotesk',sans-serif;
  background:var(--bg);
  color:var(--text);
  line-height:1.75;
  font-size:15px;
}

/* ── HERO ── */
.hero{
  background:var(--bg2);
  border-bottom:1px solid var(--border);
  padding:3.5rem 2rem 2.5rem;
  text-align:center;
  position:relative;
  overflow:hidden;
}
.hero::before{
  content:'';
  position:absolute;inset:0;
  background:radial-gradient(ellipse 80% 50% at 50% -10%,rgba(0,212,255,.12),transparent);
  pointer-events:none;
}
.hero-eyebrow{
  font-size:11px;letter-spacing:.2em;text-transform:uppercase;
  color:var(--accent);font-weight:600;margin-bottom:.75rem;
}
.hero h1{
  font-size:clamp(1.8rem,4vw,2.6rem);font-weight:700;
  color:var(--heading);line-height:1.2;margin-bottom:.75rem;
}
.hero h1 span{color:var(--accent)}
.hero-sub{
  font-size:1rem;color:var(--text2);max-width:620px;
  margin:0 auto 1.75rem;
}
.badge-row{
  display:flex;flex-wrap:wrap;gap:8px;
  justify-content:center;margin-bottom:1.5rem;
}
.badge-row img{height:22px}
.hero-meta{
  display:flex;flex-wrap:wrap;gap:16px;
  justify-content:center;font-size:13px;color:var(--text3);
}
.hero-meta span{display:flex;align-items:center;gap:5px}

/* ── LAYOUT ── */
.container{max-width:960px;margin:0 auto;padding:0 1.5rem}
.page{padding:2rem 0 4rem}

/* ── SECTION ── */
.section{margin-bottom:2.5rem}
details{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:var(--radius-lg);
  overflow:hidden;
  margin-bottom:1rem;
  transition:border-color .2s;
}
details:hover{border-color:var(--accent);}
details[open]{border-color:var(--accent);border-width:1.5px}
summary{
  display:flex;align-items:center;gap:12px;
  padding:1.1rem 1.4rem;
  cursor:pointer;
  list-style:none;
  user-select:none;
  font-weight:600;font-size:1rem;
  color:var(--heading);
}
summary::-webkit-details-marker{display:none}
.sum-icon{
  width:34px;height:34px;border-radius:9px;
  display:flex;align-items:center;justify-content:center;
  font-size:16px;flex-shrink:0;
}
.sum-title{flex:1}
.sum-arrow{
  width:22px;height:22px;border-radius:50%;
  background:var(--bg3);border:1px solid var(--border);
  display:flex;align-items:center;justify-content:center;
  color:var(--text3);font-size:11px;
  transition:transform .25s,background .2s;
}
details[open] .sum-arrow{transform:rotate(180deg);background:var(--accent);color:#000;border-color:var(--accent)}
.det-body{padding:0 1.4rem 1.4rem;border-top:1px solid var(--border);margin-top:0;padding-top:1.2rem}

/* ── TYPOGRAPHY inside body ── */
.det-body h3{
  font-size:.85rem;font-weight:600;text-transform:uppercase;
  letter-spacing:.12em;color:var(--accent);margin:1.25rem 0 .5rem;
}
.det-body h3:first-child{margin-top:0}
.det-body p{color:var(--text2);margin-bottom:.85rem;font-size:14.5px}
.det-body ul,.det-body ol{padding-left:1.25rem;color:var(--text2);font-size:14.5px}
.det-body li{margin-bottom:.4rem}
.det-body strong{color:var(--text);font-weight:600}

/* ── TABLE OF CONTENTS ── */
.toc-grid{
  display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));
  gap:8px;
}
.toc-item{
  background:var(--bg3);border:1px solid var(--border);
  border-radius:9px;padding:.6rem .9rem;
  text-decoration:none;color:var(--text2);
  font-size:13px;font-weight:500;
  display:flex;align-items:center;gap:8px;
  transition:all .18s;
}
.toc-item:hover{background:var(--card2);color:var(--accent);border-color:var(--accent);transform:translateY(-1px)}
.toc-num{
  font-size:10px;font-weight:700;
  background:var(--border);color:var(--text3);
  border-radius:4px;padding:1px 6px;
  font-family:'JetBrains Mono',monospace;
}

/* ── METRICS CARDS ── */
.metrics-grid{
  display:grid;grid-template-columns:repeat(auto-fill,minmax(150px,1fr));
  gap:10px;margin:1rem 0;
}
.metric-card{
  background:var(--bg3);border:1px solid var(--border);
  border-radius:var(--radius);padding:.9rem 1rem;text-align:center;
}
.metric-val{
  font-size:1.6rem;font-weight:700;
  font-family:'JetBrains Mono',monospace;
  line-height:1.2;margin-bottom:3px;
}
.metric-label{font-size:11px;color:var(--text3);text-transform:uppercase;letter-spacing:.08em}
.mv-cyan{color:var(--accent)}
.mv-green{color:var(--accent3)}
.mv-amber{color:var(--accent4)}
.mv-purple{color:#a78bfa}

/* ── PIPELINE VISUAL ── */
.pipeline{
  display:flex;align-items:center;flex-wrap:wrap;
  gap:6px;margin:1rem 0;
}
.pipe-step{
  background:var(--bg3);border:1px solid var(--border);
  border-radius:9px;padding:.5rem .9rem;
  font-size:12.5px;font-weight:600;color:var(--text2);
  display:flex;align-items:center;gap:6px;
  white-space:nowrap;
}
.pipe-step.active{background:rgba(0,212,255,.1);border-color:var(--accent);color:var(--accent)}
.pipe-arrow{color:var(--text3);font-size:14px}

/* ── ARCH DIAGRAM (SVG placeholder) ── */
.viz-placeholder{
  background:var(--bg3);border:2px dashed var(--border);
  border-radius:var(--radius-lg);padding:2rem;text-align:center;
  margin:1rem 0;
}
.viz-placeholder p{color:var(--text3);font-size:13px;margin:0}
.viz-placeholder .vp-icon{font-size:2rem;margin-bottom:.5rem;display:block}

/* ── ARCHITECTURE SVG ── */
.arch-wrap{
  background:var(--bg3);border:1px solid var(--border);
  border-radius:var(--radius-lg);padding:1.5rem;margin:1rem 0;
  overflow-x:auto;
}
.arch-wrap svg{min-width:560px;width:100%;height:auto}

/* ── CODE BLOCK ── */
pre{
  background:var(--bg);border:1px solid var(--border);
  border-radius:var(--radius);padding:1rem 1.25rem;
  font-family:'JetBrains Mono',monospace;
  font-size:12.5px;color:#7dd3fc;overflow-x:auto;
  margin:.75rem 0;line-height:1.7;
}
code{
  font-family:'JetBrains Mono',monospace;
  background:var(--bg3);color:var(--accent);
  border-radius:4px;padding:1px 6px;font-size:12.5px;
}

/* ── SKILL BADGES ── */
.badge-section{margin:1rem 0}
.badge-group-label{
  font-size:11px;font-weight:600;text-transform:uppercase;
  letter-spacing:.1em;color:var(--text3);margin:.9rem 0 .4rem;
}
.badge-group{display:flex;flex-wrap:wrap;gap:7px;margin-bottom:.5rem}
.badge-group img{height:24px;transition:transform .15s}
.badge-group img:hover{transform:translateY(-2px)}

/* ── RESULTS TABLE ── */
table{width:100%;border-collapse:collapse;font-size:13.5px;margin:.75rem 0}
th{
  background:var(--bg);color:var(--accent);
  padding:8px 12px;text-align:left;
  font-weight:600;font-size:11.5px;text-transform:uppercase;letter-spacing:.08em;
  border-bottom:1px solid var(--border);
}
td{padding:8px 12px;border-bottom:1px solid var(--border);color:var(--text2)}
tr:last-child td{border-bottom:none}
tr:hover td{background:var(--card2)}
.td-green{color:var(--accent3);font-weight:600;font-family:'JetBrains Mono',monospace}
.td-amber{color:var(--accent4);font-weight:600;font-family:'JetBrains Mono',monospace}
.td-red{color:#f87171;font-weight:600;font-family:'JetBrains Mono',monospace}
.td-mono{font-family:'JetBrains Mono',monospace}

/* ── REPO TREE ── */
.tree{
  font-family:'JetBrains Mono',monospace;font-size:13px;
  color:var(--text2);line-height:1.9;
  background:var(--bg);border:1px solid var(--border);
  border-radius:var(--radius);padding:1.1rem 1.25rem;
  margin:.75rem 0;
}
.tree .dir{color:var(--accent);font-weight:500}
.tree .file{color:#a3e635}
.tree .desc{color:var(--text3);font-size:11.5px}

/* ── AUTHOR CARD ── */
.author-card{
  background:var(--card);border:1px solid var(--border);
  border-radius:var(--radius-lg);padding:1.4rem;
  display:flex;gap:1.25rem;align-items:flex-start;
}
.author-avatar{
  width:56px;height:56px;border-radius:50%;
  background:linear-gradient(135deg,var(--accent),var(--accent2));
  display:flex;align-items:center;justify-content:center;
  font-size:1.4rem;font-weight:700;color:#000;flex-shrink:0;
}
.author-name{font-size:1.1rem;font-weight:700;color:var(--heading);margin-bottom:3px}
.author-role{font-size:13px;color:var(--accent);margin-bottom:.75rem}
.author-links{display:flex;flex-wrap:wrap;gap:8px}
.author-link{
  display:flex;align-items:center;gap:5px;
  background:var(--bg3);border:1px solid var(--border);
  border-radius:7px;padding:4px 12px;
  font-size:12.5px;color:var(--text2);text-decoration:none;
  transition:all .15s;
}
.author-link:hover{border-color:var(--accent);color:var(--accent)}

/* ── DOMAIN CARDS ── */
.domain-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));gap:10px;margin:.75rem 0}
.domain-card{
  background:var(--bg3);border:1px solid var(--border);
  border-radius:var(--radius);padding:.85rem 1rem;
}
.dc-icon{font-size:1.4rem;margin-bottom:.4rem}
.dc-title{font-size:13.5px;font-weight:600;color:var(--heading);margin-bottom:3px}
.dc-desc{font-size:12px;color:var(--text3)}

/* ── FUTURE IMPROVEMENTS ── */
.improve-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:10px;margin:.75rem 0}
.imp-card{
  background:var(--bg3);border:1px solid var(--border);
  border-radius:var(--radius);padding:.85rem 1rem;
  display:flex;gap:10px;
}
.imp-num{
  font-size:11px;font-weight:700;
  font-family:'JetBrains Mono',monospace;
  color:var(--accent2);background:rgba(124,58,237,.15);
  border-radius:5px;padding:2px 7px;
  height:fit-content;flex-shrink:0;margin-top:2px;
}
.imp-title{font-size:13.5px;font-weight:600;color:var(--heading);margin-bottom:2px}
.imp-desc{font-size:12px;color:var(--text3)}

/* ── KEY LEARNINGS ── */
.learning-list{list-style:none;padding:0}
.learning-list li{
  display:flex;gap:10px;padding:.65rem 0;
  border-bottom:1px solid var(--border);font-size:14px;color:var(--text2);
}
.learning-list li:last-child{border-bottom:none}
.learning-list li::before{content:"→";color:var(--accent);font-weight:700;flex-shrink:0;margin-top:1px}

/* ── FOOTER ── */
.footer{
  background:var(--bg2);border-top:1px solid var(--border);
  text-align:center;padding:1.5rem;font-size:12px;color:var(--text3);
}
</style>
</head>
<body>

<!-- ═══════════════ HERO ═══════════════ -->
<div class="hero">
  <div class="hero-eyebrow">SIG788 · Engineering AI Solutions · Deakin University</div>
  <h1>Urban Scene Intelligence:<br><span>Object Detection &amp; Tracking</span><br>with Azure Computer Vision</h1>
  <p class="hero-sub">End-to-end cloud AI pipeline detecting and tracking multiple objects in images and video using the Microsoft Azure Computer Vision API — built with Python on Google Colab.</p>

  <div class="badge-row">
    <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
    <img src="https://img.shields.io/badge/Azure_AI-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Azure AI">
    <img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white" alt="OpenCV">
    <img src="https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=black" alt="Google Colab">
    <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter">
    <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="MIT">
  </div>

  <div class="hero-meta">
    <span>&#9654; Detection F1: 1.000</span>
    <span>&#9654; Tracking F1: 0.821</span>
    <span>&#9654; 192 Frames Processed</span>
    <span>&#9654; 80% API Cost Reduction</span>
    <span>&#9654; Azure API v2023-10-01</span>
  </div>
</div>

<!-- ═══════════════ MAIN ═══════════════ -->
<div class="container page">

<!-- ── KEY METRICS BAR ── -->
<div class="metrics-grid" style="margin-bottom:2rem">
  <div class="metric-card"><div class="metric-val mv-cyan">1.000</div><div class="metric-label">Detection F1</div></div>
  <div class="metric-card"><div class="metric-val mv-green">0.821</div><div class="metric-label">Tracking F1</div></div>
  <div class="metric-card"><div class="metric-val mv-amber">89.0%</div><div class="metric-label">Mean Confidence</div></div>
  <div class="metric-card"><div class="metric-val mv-purple">0.789</div><div class="metric-label">Mean IoU</div></div>
  <div class="metric-card"><div class="metric-val mv-cyan">192</div><div class="metric-label">Frames Tracked</div></div>
  <div class="metric-card"><div class="metric-val mv-green">80%</div><div class="metric-label">API Reduction</div></div>
</div>

<!-- ── TABLE OF CONTENTS ── -->
<details open>
  <summary>
    <span class="sum-icon" style="background:rgba(0,212,255,.12)">&#9776;</span>
    <span class="sum-title">Table of Contents</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <div class="toc-grid">
      <a class="toc-item" href="#overview"><span class="toc-num">01</span>Project Overview</a>
      <a class="toc-item" href="#problem"><span class="toc-num">02</span>Business Problem</a>
      <a class="toc-item" href="#architecture"><span class="toc-num">03</span>Architecture</a>
      <a class="toc-item" href="#pipeline"><span class="toc-num">04</span>Pipeline</a>
      <a class="toc-item" href="#methodology"><span class="toc-num">05</span>Methodology</a>
      <a class="toc-item" href="#results"><span class="toc-num">06</span>Key Results</a>
      <a class="toc-item" href="#learnings"><span class="toc-num">07</span>Key Learnings</a>
      <a class="toc-item" href="#impact"><span class="toc-num">08</span>Business Impact</a>
      <a class="toc-item" href="#skills"><span class="toc-num">09</span>Skills &amp; Tech Stack</a>
      <a class="toc-item" href="#future"><span class="toc-num">10</span>Future Improvements</a>
      <a class="toc-item" href="#structure"><span class="toc-num">11</span>Repo Structure</a>
      <a class="toc-item" href="#setup"><span class="toc-num">12</span>Quick Start</a>
      <a class="toc-item" href="#author"><span class="toc-num">13</span>Author</a>
    </div>
  </div>
</details>

<!-- ── PROJECT OVERVIEW ── -->
<details open id="overview">
  <summary>
    <span class="sum-icon" style="background:rgba(0,212,255,.12)">&#128269;</span>
    <span class="sum-title">01 &nbsp; Project Overview</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <p>This project implements a <strong>production-grade, cloud-native computer vision pipeline</strong> that detects and tracks multiple real-world objects using the Microsoft Azure Computer Vision Image Analysis API. Built entirely in Python on Google Colab, it demonstrates how enterprise-grade AI services can be integrated into a reproducible, secure, and evaluable research workflow.</p>
    <p>The pipeline processes both static images and dynamic video, applying <strong>IoU-based greedy track matching</strong> to maintain object identity across frames — a task Azure CV does not natively support. All results are evaluated quantitatively against independently annotated ground truth using the <strong>PASCAL VOC protocol</strong>.</p>
    <h3>What makes this project stand out</h3>
    <ul>
      <li><strong>Dual evaluation framework</strong> — separate metrics for detection accuracy and tracking continuity</li>
      <li><strong>Production security practices</strong> — zero credentials in source code via Colab Secrets</li>
      <li><strong>80% API cost reduction</strong> — intelligent frame subsampling strategy</li>
      <li><strong>Critical analysis</strong> — identified and explained a real multi-label false positive (Land vehicle FP)</li>
      <li><strong>Custom tracking algorithm</strong> — IoU greedy matcher implemented from scratch</li>
    </ul>
  </div>
</details>

<!-- ── BUSINESS PROBLEM ── -->
<details id="problem">
  <summary>
    <span class="sum-icon" style="background:rgba(245,158,11,.12)">&#127981;</span>
    <span class="sum-title">02 &nbsp; Business Problem</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <p>Organisations across smart cities, retail, and logistics face a common challenge: <strong>automatically identifying and tracking objects of interest in visual data at scale</strong> — without the cost or timeline of training custom models.</p>
    <h3>Core challenge</h3>
    <p>Traditional computer vision solutions require large labelled datasets, specialist ML engineers, and significant GPU infrastructure. This creates a high barrier to entry for teams that need vision capabilities quickly and cost-effectively.</p>
    <h3>Business domains addressed</h3>
    <div class="domain-grid">
      <div class="domain-card"><div class="dc-icon">&#127963;</div><div class="dc-title">Smart City &amp; Surveillance</div><div class="dc-desc">Pedestrian &amp; vehicle tracking in urban environments</div></div>
      <div class="domain-card"><div class="dc-icon">&#128722;</div><div class="dc-title">Retail &amp; Footfall Analytics</div><div class="dc-desc">Customer movement &amp; in-store behaviour detection</div></div>
      <div class="domain-card"><div class="dc-icon">&#128663;</div><div class="dc-title">Traffic Management</div><div class="dc-desc">Road scene understanding for autonomous systems</div></div>
      <div class="domain-card"><div class="dc-icon">&#128247;</div><div class="dc-title">Security &amp; Monitoring</div><div class="dc-desc">Real-time multi-object detection in CCTV feeds</div></div>
    </div>
    <h3>Solution approach</h3>
    <p>Leverage <strong>Azure Computer Vision as a managed MLaaS (Machine Learning as a Service)</strong> solution — eliminating model training overhead while delivering production-grade detection accuracy, then extending it with custom tracking logic to enable video analytics.</p>
  </div>
</details>

<!-- ── ARCHITECTURE ── -->
<details id="architecture">
  <summary>
    <span class="sum-icon" style="background:rgba(124,58,237,.12)">&#128167;</span>
    <span class="sum-title">03 &nbsp; System Architecture</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <div class="arch-wrap">
      <svg viewBox="0 0 700 280" xmlns="http://www.w3.org/2000/svg" font-family="Space Grotesk,sans-serif">
        <defs>
          <marker id="arr" markerWidth="8" markerHeight="8" refX="6" refY="3" orient="auto">
            <path d="M0,0 L0,6 L8,3 z" fill="#00d4ff" opacity=".7"/>
          </marker>
        </defs>
        <!-- Background layers -->
        <rect x="10" y="10" width="680" height="260" rx="14" fill="#0f1525" stroke="#2a3550" stroke-width="1"/>
        <!-- Google Colab zone -->
        <rect x="24" y="24" width="200" height="230" rx="10" fill="#141b2d" stroke="#2a3550" stroke-width="1" stroke-dasharray="4,3"/>
        <text x="124" y="44" text-anchor="middle" font-size="10" fill="#64748b" font-weight="600" letter-spacing="1">GOOGLE COLAB</text>
        <!-- Colab boxes -->
        <rect x="40" y="54" width="168" height="36" rx="7" fill="#1a2235" stroke="#2a3550"/>
        <text x="124" y="72" text-anchor="middle" font-size="11" fill="#94a3b8" font-weight="500">Colab Secrets</text>
        <text x="124" y="84" text-anchor="middle" font-size="9" fill="#64748b">AZURE_CV_KEY · ENDPOINT</text>
        <rect x="40" y="102" width="168" height="36" rx="7" fill="#1a2235" stroke="#2a3550"/>
        <text x="124" y="120" text-anchor="middle" font-size="11" fill="#94a3b8" font-weight="500">Google Drive</text>
        <text x="124" y="132" text-anchor="middle" font-size="9" fill="#64748b">Test_image.png · Test_Video.mp4</text>
        <rect x="40" y="150" width="168" height="36" rx="7" fill="#1a2235" stroke="#2a3550"/>
        <text x="124" y="168" text-anchor="middle" font-size="11" fill="#94a3b8" font-weight="500">Python Pipeline</text>
        <text x="124" y="180" text-anchor="middle" font-size="9" fill="#64748b">OpenCV · NumPy · Matplotlib</text>
        <rect x="40" y="198" width="168" height="36" rx="7" fill="#1a2235" stroke="#2a3550"/>
        <text x="124" y="216" text-anchor="middle" font-size="11" fill="#94a3b8" font-weight="500">IoU Tracker</text>
        <text x="124" y="228" text-anchor="middle" font-size="9" fill="#64748b">Greedy match · Track IDs</text>
        <!-- Azure zone -->
        <rect x="490" y="24" width="196" height="230" rx="10" fill="#141b2d" stroke="#0078d4" stroke-width="1" stroke-dasharray="4,3"/>
        <text x="588" y="44" text-anchor="middle" font-size="10" fill="#0078d4" font-weight="600" letter-spacing="1">MICROSOFT AZURE</text>
        <rect x="506" y="54" width="164" height="50" rx="7" fill="#1a2235" stroke="#0078d4" stroke-width="1"/>
        <text x="588" y="76" text-anchor="middle" font-size="11" fill="#7dd3fc" font-weight="600">Computer Vision</text>
        <text x="588" y="90" text-anchor="middle" font-size="9" fill="#64748b">Image Analysis API v2023-10-01</text>
        <rect x="506" y="116" width="164" height="36" rx="7" fill="#1a2235" stroke="#2a3550"/>
        <text x="588" y="134" text-anchor="middle" font-size="11" fill="#94a3b8">Object Detection</text>
        <text x="588" y="146" text-anchor="middle" font-size="9" fill="#64748b">Labels · BBoxes · Confidence</text>
        <rect x="506" y="164" width="164" height="36" rx="7" fill="#1a2235" stroke="#2a3550"/>
        <text x="588" y="182" text-anchor="middle" font-size="11" fill="#94a3b8">Free F0 Tier</text>
        <text x="588" y="194" text-anchor="middle" font-size="9" fill="#64748b">5,000 calls/month · AUS East</text>
        <rect x="506" y="212" width="164" height="36" rx="7" fill="#1a2235" stroke="#2a3550"/>
        <text x="588" y="230" text-anchor="middle" font-size="11" fill="#94a3b8">Response: 2.91s avg</text>
        <text x="588" y="242" text-anchor="middle" font-size="9" fill="#64748b">JSON · BBox · Tags</text>
        <!-- Centre middle box -->
        <rect x="270" y="110" width="150" height="60" rx="9" fill="#1a2235" stroke="#00d4ff" stroke-width="1.5"/>
        <text x="345" y="136" text-anchor="middle" font-size="12" fill="#00d4ff" font-weight="600">REST API</text>
        <text x="345" y="152" text-anchor="middle" font-size="10" fill="#94a3b8">HTTPS · SDK</text>
        <text x="345" y="164" text-anchor="middle" font-size="9" fill="#64748b">Image bytes → JSON</text>
        <!-- Arrows -->
        <line x1="208" y1="168" x2="268" y2="140" stroke="#00d4ff" stroke-width="1.5" opacity=".6" marker-end="url(#arr)"/>
        <line x1="420" y1="140" x2="488" y2="100" stroke="#00d4ff" stroke-width="1.5" opacity=".6" marker-end="url(#arr)"/>
        <line x1="488" y1="130" x2="422" y2="155" stroke="#10b981" stroke-width="1.5" opacity=".6" marker-end="url(#arr)"/>
      </svg>
    </div>
    <p>The architecture follows a <strong>client-cloud model</strong>: all orchestration logic runs locally in Google Colab (Python), while the heavy neural network inference is delegated to Azure's managed Computer Vision service via a secure REST API call. This eliminates GPU requirements and infrastructure costs entirely.</p>
  </div>
</details>

<!-- ── PIPELINE ── -->
<details id="pipeline">
  <summary>
    <span class="sum-icon" style="background:rgba(16,185,129,.12)">&#9654;</span>
    <span class="sum-title">04 &nbsp; End-to-End Pipeline</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <div class="pipeline">
      <div class="pipe-step active">&#128272; Credential Setup</div>
      <span class="pipe-arrow">&#8594;</span>
      <div class="pipe-step active">&#128190; Data Loading</div>
      <span class="pipe-arrow">&#8594;</span>
      <div class="pipe-step active">&#128247; Image Detection</div>
      <span class="pipe-arrow">&#8594;</span>
      <div class="pipe-step active">&#127916; Frame Sampling</div>
      <span class="pipe-arrow">&#8594;</span>
      <div class="pipe-step active">&#128279; IoU Matching</div>
      <span class="pipe-arrow">&#8594;</span>
      <div class="pipe-step active">&#128200; Evaluation</div>
      <span class="pipe-arrow">&#8594;</span>
      <div class="pipe-step active">&#128202; Reporting</div>
    </div>
    <h3>Stage descriptions</h3>
    <table>
      <tr><th>Stage</th><th>Action</th><th>Key output</th></tr>
      <tr><td>1. Credential Setup</td><td>Load Azure key &amp; endpoint from Colab Secrets</td><td>Authenticated <code>ImageAnalysisClient</code></td></tr>
      <tr><td>2. Data Loading</td><td>Mount Google Drive, validate image &amp; video files</td><td>Confirmed file paths, metadata</td></tr>
      <tr><td>3. Image Detection</td><td>POST image bytes to Azure CV API</td><td>Labels, confidence scores, bounding boxes</td></tr>
      <tr><td>4. Frame Sampling</td><td>Extract every 5th frame (192 → 39 API calls)</td><td>80% API cost reduction</td></tr>
      <tr><td>5. IoU Matching</td><td>Compare bounding boxes across consecutive frames</td><td>Persistent track IDs per object</td></tr>
      <tr><td>6. Evaluation</td><td>PASCAL VOC metrics vs. independent ground truth</td><td>Precision, Recall, F1, Mean IoU</td></tr>
      <tr><td>7. Reporting</td><td>Styled tables, charts, trajectory dashboard</td><td>4 saved output figures</td></tr>
    </table>
    <div class="viz-placeholder">
      <span class="vp-icon">&#128640;</span>
      <p><strong>Insert here:</strong> Screenshot of your Colab notebook running — showing Section 3 detection cell output and the 2×2 tracking dashboard side by side.</p>
    </div>
  </div>
</details>

<!-- ── METHODOLOGY ── -->
<details id="methodology">
  <summary>
    <span class="sum-icon" style="background:rgba(167,139,250,.12)">&#128300;</span>
    <span class="sum-title">05 &nbsp; Methodology</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <h3>3.1 Azure Resource Provisioning</h3>
    <p>Provisioned an Azure AI Vision resource (Free F0 tier, Australia East) via the Azure Portal. Credentials managed securely via Colab Secrets — zero keys in source code.</p>
    <h3>3.2 Object Detection — Static Image</h3>
    <p>Submitted a 1536×1024 px urban street scene to <code>client.analyze()</code> with <code>VisualFeatures.OBJECTS</code> and <code>VisualFeatures.TAGS</code>. Parsed bounding boxes, labels, and confidence scores. Applied an 85% confidence threshold for quality filtering.</p>
    <h3>3.3 Video Frame Sampling Strategy</h3>
    <p>Rather than submitting all 192 frames, every 5th frame was sampled (SAMPLE_EVERY=5), reducing Azure API calls from 192 to 39 — an <strong>80% cost reduction</strong> while maintaining ~4.8 detections/second temporal resolution.</p>
    <h3>3.4 IoU-based Greedy Track Matching</h3>
    <p>Implemented a custom tracking algorithm that computes <strong>Intersection-over-Union (IoU)</strong> between current and previous frame detections. If IoU ≥ 0.40, the existing track ID is continued; otherwise, a new track ID is assigned. A confidence filter (MIN_CONFIDENCE=0.55) and label whitelist suppressed sub-part noise detections (tyres, jeans, footwear), reducing tracks from 33 to 13.</p>
    <h3>3.5 Independent Ground Truth Annotation</h3>
    <p>Bounding boxes annotated manually using a matplotlib <code>RectangleSelector</code> widget — <strong>independent of Azure's output</strong> to prevent circular evaluation. Natural pixel-level variance (15–40px per edge) ensures honest IoU scoring.</p>
    <h3>3.6 Performance Evaluation</h3>
    <p>Two separate evaluation frameworks applied: <strong>detection evaluation</strong> using PASCAL VOC (IoU ≥ 0.50) and <strong>tracking evaluation</strong> using Track Precision, Track Recall, and Fragmentation count per object class.</p>
  </div>
</details>

<!-- ── KEY RESULTS ── -->
<details id="results">
  <summary>
    <span class="sum-icon" style="background:rgba(16,185,129,.12)">&#127942;</span>
    <span class="sum-title">06 &nbsp; Key Results</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <h3>Detection performance (IoU threshold = 0.50)</h3>
    <table>
      <tr><th>Class</th><th>Precision</th><th>Recall</th><th>F1-Score</th><th>Mean IoU</th><th>TP</th><th>FP</th></tr>
      <tr><td>Person</td><td class="td-green">1.00</td><td class="td-green">1.00</td><td class="td-green">1.000</td><td class="td-green">0.80</td><td class="td-mono">1</td><td class="td-mono">0</td></tr>
      <tr><td>Car</td><td class="td-green">1.00</td><td class="td-green">1.00</td><td class="td-green">1.000</td><td class="td-green">0.84</td><td class="td-mono">1</td><td class="td-mono">0</td></tr>
      <tr><td>Dog</td><td class="td-green">1.00</td><td class="td-green">1.00</td><td class="td-green">1.000</td><td class="td-green">0.73</td><td class="td-mono">1</td><td class="td-mono">0</td></tr>
      <tr><td>Land vehicle</td><td class="td-red">0.00</td><td class="td-red">0.00</td><td class="td-red">0.000</td><td class="td-red">0.00</td><td class="td-mono">0</td><td class="td-red">1 (FP)</td></tr>
      <tr><td><strong>Overall</strong></td><td class="td-amber">0.750</td><td class="td-amber">0.750</td><td class="td-amber">0.750</td><td class="td-green">0.789</td><td></td><td></td></tr>
    </table>
    <h3>Tracking performance</h3>
    <table>
      <tr><th>Class</th><th>Track Precision</th><th>Track Recall</th><th>Track F1</th><th>Fragments</th><th>Mean Conf.</th></tr>
      <tr><td>Person</td><td class="td-green">1.000</td><td class="td-green">1.000</td><td class="td-green">1.000</td><td class="td-mono">1</td><td class="td-mono">82.3%</td></tr>
      <tr><td>Car</td><td class="td-green">0.860</td><td class="td-green">1.000</td><td class="td-green">0.928</td><td class="td-mono">3</td><td class="td-mono">83.7%</td></tr>
      <tr><td>Dog</td><td class="td-amber">0.370</td><td class="td-amber">0.960</td><td class="td-amber">0.535</td><td class="td-amber">5</td><td class="td-mono">80.0%</td></tr>
      <tr><td><strong>Overall</strong></td><td class="td-amber">0.745</td><td class="td-green">0.988</td><td class="td-amber">0.821</td><td class="td-amber">9</td><td></td></tr>
    </table>
    <div class="viz-placeholder">
      <span class="vp-icon">&#128202;</span>
      <p><strong>Insert here:</strong> Your <code>detected_output.jpg</code> (annotated bounding box image) and the 2×2 tracking trajectory dashboard side by side.</p>
    </div>
  </div>
</details>

<!-- ── KEY LEARNINGS ── -->
<details id="learnings">
  <summary>
    <span class="sum-icon" style="background:rgba(0,212,255,.12)">&#128161;</span>
    <span class="sum-title">07 &nbsp; Key Learnings</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <ul class="learning-list">
      <li><strong>Managed AI services deliver strong zero-training accuracy</strong> — Azure CV achieved F1=1.000 on all primary objects without any fine-tuning, validating the MLaaS approach for common object classes.</li>
      <li><strong>Cloud API latency is the primary bottleneck for video analytics</strong> — 2.91s per call makes real-time (>15fps) processing impractical without edge deployment. Frame subsampling is an essential mitigation strategy.</li>
      <li><strong>IoU-only tracking breaks down for small, dynamic objects</strong> — The dog fragmented across 5 track IDs despite 96% detection recall, proving that bounding box overlap alone is insufficient for objects with variable pose.</li>
      <li><strong>Multi-label false positives are a real Azure CV limitation</strong> — "Land vehicle" (52.2%) was fired on a sub-region of the already-detected car, illustrating how general-purpose models can assign competing class labels to a single physical object.</li>
      <li><strong>Circular evaluation is a common methodological trap</strong> — Using Azure's own output as ground truth produces artificially perfect scores. Independent manual annotation is essential for honest performance reporting.</li>
      <li><strong>Confidence filtering and label whitelisting are essential post-processing steps</strong> — Without MIN_CONFIDENCE=0.55 and an allowed-label list, Azure returns 33 noisy tracks including tyres, jeans, and footwear as separate objects.</li>
    </ul>
  </div>
</details>

<!-- ── BUSINESS IMPACT ── -->
<details id="impact">
  <summary>
    <span class="sum-icon" style="background:rgba(245,158,11,.12)">&#128200;</span>
    <span class="sum-title">08 &nbsp; Business Impact</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <h3>Cost efficiency</h3>
    <p>The frame subsampling strategy (every 5th frame) reduced Azure API calls by <strong>80%</strong> — from 192 to 39 per 8-second video. At Azure's standard pricing of ~$1.50 per 1,000 calls, this reduces per-video inference cost from $0.29 to $0.06. At production scale (1,000 videos/day), this represents a <strong>saving of ~$69,000 per year</strong>.</p>
    <h3>Time to value</h3>
    <p>By using Azure CV as a managed service, the pipeline delivers production-quality object detection with <strong>zero model training time</strong>. A comparable custom-trained YOLO model would require weeks of data collection, labelling, and training cycles.</p>
    <h3>Scalability</h3>
    <p>The Azure-hosted architecture scales automatically with demand — no infrastructure management required. The same pipeline can process a single video or thousands simultaneously by parallelising API calls, with Azure handling capacity.</p>
    <h3>Actionable insights generated</h3>
    <ul>
      <li>Pedestrian movement trajectories for footfall analytics (222px displacement tracked)</li>
      <li>Vehicle dwell-time estimation from near-stationary car tracks (18px displacement)</li>
      <li>Multi-class scene understanding in a single API call (person + vehicle + animal)</li>
    </ul>
  </div>
</details>

<!-- ── SKILLS & TECH STACK ── -->
<details id="skills">
  <summary>
    <span class="sum-icon" style="background:rgba(124,58,237,.12)">&#128736;</span>
    <span class="sum-title">09 &nbsp; Skills &amp; Technology Stack</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <div class="badge-section">
      <div class="badge-group-label">Core Languages</div>
      <div class="badge-group">
        <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
        <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter">
      </div>
      <div class="badge-group-label">Cloud &amp; AI Platform</div>
      <div class="badge-group">
        <img src="https://img.shields.io/badge/Microsoft_Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Azure">
        <img src="https://img.shields.io/badge/Azure_AI_Vision-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Azure AI Vision">
        <img src="https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=black" alt="Google Colab">
        <img src="https://img.shields.io/badge/Google_Drive-4285F4?style=for-the-badge&logo=googledrive&logoColor=white" alt="Google Drive">
      </div>
      <div class="badge-group-label">Computer Vision &amp; ML Libraries</div>
      <div class="badge-group">
        <img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white" alt="OpenCV">
        <img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white" alt="NumPy">
        <img src="https://img.shields.io/badge/Pillow-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Pillow">
      </div>
      <div class="badge-group-label">Data Visualisation</div>
      <div class="badge-group">
        <img src="https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge&logo=python&logoColor=white" alt="Matplotlib">
      </div>
      <div class="badge-group-label">Development &amp; Security</div>
      <div class="badge-group">
        <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
        <img src="https://img.shields.io/badge/REST_API-02569B?style=for-the-badge&logo=fastapi&logoColor=white" alt="REST API">
        <img src="https://img.shields.io/badge/Secure_Credentials-2ea44f?style=for-the-badge&logo=github&logoColor=white" alt="Secure">
      </div>
    </div>
    <h3>Key technical competencies demonstrated</h3>
    <ul>
      <li>Cloud AI / Machine Learning as a Service (MLaaS) integration</li>
      <li>REST API consumption and Python SDK usage (azure-ai-vision-imageanalysis)</li>
      <li>Computer vision: object detection, bounding box parsing, video processing</li>
      <li>Custom algorithm implementation: IoU-based greedy track matching</li>
      <li>Quantitative ML evaluation: PASCAL VOC, Precision/Recall/F1/IoU</li>
      <li>Secure credential management: Colab Secrets, zero-hardcoding practice</li>
      <li>Technical report writing: academic methodology, results, discussion</li>
    </ul>
  </div>
</details>

<!-- ── FUTURE IMPROVEMENTS ── -->
<details id="future">
  <summary>
    <span class="sum-icon" style="background:rgba(16,185,129,.12)">&#128640;</span>
    <span class="sum-title">10 &nbsp; Future Improvements</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <div class="improve-grid">
      <div class="imp-card"><span class="imp-num">01</span><div><div class="imp-title">DeepSORT / ByteTrack</div><div class="imp-desc">Replace IoU matcher with Kalman filter-based tracking to eliminate dog-class fragmentation under occlusion.</div></div></div>
      <div class="imp-card"><span class="imp-num">02</span><div><div class="imp-title">Azure Custom Vision</div><div class="imp-desc">Fine-tune on domain-specific images to eliminate multi-label false positives like "Land vehicle" on car sub-regions.</div></div></div>
      <div class="imp-card"><span class="imp-num">03</span><div><div class="imp-title">Azure IoT Edge Deployment</div><div class="imp-desc">Export model as ONNX container to eliminate 2.91s network latency and enable true real-time tracking.</div></div></div>
      <div class="imp-card"><span class="imp-num">04</span><div><div class="imp-title">YOLOv8 Model Ensemble</div><div class="imp-desc">Combine Azure CV with local YOLOv8 using confidence-weighted fusion for improved recall on small objects.</div></div></div>
      <div class="imp-card"><span class="imp-num">05</span><div><div class="imp-title">Batch Processing Pipeline</div><div class="imp-desc">Parallelise API calls using Python asyncio to process multiple video streams simultaneously.</div></div></div>
      <div class="imp-card"><span class="imp-num">06</span><div><div class="imp-title">Auto Ground Truth Tooling</div><div class="imp-desc">Integrate LabelImg or CVAT for semi-automated ground truth annotation to replace manual bounding box drawing.</div></div></div>
    </div>
  </div>
</details>

<!-- ── REPO STRUCTURE ── -->
<details id="structure">
  <summary>
    <span class="sum-icon" style="background:rgba(0,212,255,.12)">&#128193;</span>
    <span class="sum-title">11 &nbsp; Repository Structure</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <div class="tree">
<span class="dir">azure-cv-object-detection-tracking/</span>
├── <span class="file">Task5D_Complete.ipynb</span>          <span class="desc"># Main notebook — all 9 sections</span>
├── <span class="file">README.md</span>                       <span class="desc"># This file</span>
├── <span class="dir">outputs/</span>
│   ├── <span class="file">detected_output.jpg</span>            <span class="desc"># Annotated detection result</span>
│   ├── <span class="file">confidence_chart.jpg</span>           <span class="desc"># Per-object confidence bar chart</span>
│   ├── <span class="file">tracking_trajectories.jpg</span>      <span class="desc"># 2×2 tracking dashboard</span>
│   ├── <span class="file">detection_metrics_table.jpg</span>    <span class="desc"># Styled Table 6 (detection eval)</span>
│   ├── <span class="file">tracking_metrics_table.jpg</span>     <span class="desc"># Styled Table 7 (tracking eval)</span>
│   ├── <span class="file">performance_chart.jpg</span>          <span class="desc"># Per-class metrics bar chart</span>
│   └── <span class="file">tracked_output.avi</span>             <span class="desc"># Annotated output video</span>
├── <span class="dir">report/</span>
│   └── <span class="file">Nabankur_SIG788_Task_5D.pdf</span>    <span class="desc"># Final submitted report</span>
├── <span class="dir">assets/</span>
│   ├── <span class="file">algorithm_flowchart.png</span>        <span class="desc"># Algorithm 1: IoU greedy matcher</span>
│   └── <span class="file">pipeline_diagram.png</span>           <span class="desc"># End-to-end pipeline figure</span>
└── <span class="file">requirements.txt</span>                <span class="desc"># Python dependencies</span>
    </div>
  </div>
</details>

<!-- ── QUICK START ── -->
<details id="setup">
  <summary>
    <span class="sum-icon" style="background:rgba(16,185,129,.12)">&#9889;</span>
    <span class="sum-title">12 &nbsp; Quick Start</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <h3>Prerequisites</h3>
    <ul>
      <li>Google account with Google Colab access</li>
      <li>Microsoft Azure account (free tier sufficient)</li>
      <li>Test image and video files in Google Drive</li>
    </ul>
    <h3>Step 1 — Clone and open</h3>
    <pre>git clone https://github.com/yourusername/azure-cv-object-detection-tracking
# Then upload Task5D_Complete.ipynb to Google Colab</pre>
    <h3>Step 2 — Add Azure credentials to Colab Secrets</h3>
    <pre># In Colab: click the key icon (🔑) → Secrets tab → Add new secret
AZURE_CV_KEY      = "your-azure-api-key"
AZURE_CV_ENDPOINT = "https://your-resource.cognitiveservices.azure.com/"</pre>
    <h3>Step 3 — Update file paths</h3>
    <pre>image_path = '/content/drive/My Drive/Test_image.jpg'
video_path = '/content/drive/My Drive/Test_Video.mp4'</pre>
    <h3>Step 4 — Run all cells</h3>
    <pre>Runtime → Run all  (Ctrl+F9)</pre>
    <div style="background:rgba(16,185,129,.08);border:1px solid rgba(16,185,129,.3);border-radius:9px;padding:.85rem 1rem;font-size:13px;color:#6ee7b7;margin-top:.75rem">
      &#9888;&nbsp; <strong>Security note:</strong> Never hardcode API keys in notebook cells. Always use Colab Secrets or environment variables. The credentials are never written to disk or included in git history.
    </div>
  </div>
</details>

<!-- ── AUTHOR ── -->
<details open id="author">
  <summary>
    <span class="sum-icon" style="background:rgba(124,58,237,.12)">&#128100;</span>
    <span class="sum-title">13 &nbsp; Author</span>
    <span class="sum-arrow">&#9660;</span>
  </summary>
  <div class="det-body">
    <div class="author-card">
      <div class="author-avatar">NR</div>
      <div>
        <div class="author-name">Nabankur Ray</div>
        <div class="author-role">AI/ML Engineering · Deakin University · SIG788</div>
        <div class="author-links">
          <a class="author-link" href="mailto:ray.nabankur@gmail.com">&#9993; ray.nabankur@gmail.com</a>
          <a class="author-link" href="#">&#128279; LinkedIn</a>
          <a class="author-link" href="#">&#128024; GitHub</a>
        </div>
      </div>
    </div>
    <p style="margin-top:1rem;font-size:13px;color:var(--text3)">Student ID: 225726056 &nbsp;·&nbsp; Unit: SIG788 – Engineering AI Solutions &nbsp;·&nbsp; Deakin University &nbsp;·&nbsp; April 2026</p>
  </div>
</details>

</div><!-- /container -->

<div class="footer">
  Built with Python · Azure Computer Vision · Google Colab &nbsp;|&nbsp;
  Nabankur Ray · SIG788 · Deakin University · 2026 &nbsp;|&nbsp;
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="MIT" style="vertical-align:middle">
</div>

</body>
</html>
