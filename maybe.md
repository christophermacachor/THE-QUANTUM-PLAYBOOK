<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="quantum-playbook:scalar-lock" content="M = (sqrt(5)-1)/2">
<title>Observatory - Scalar-Plasma Cycle - MGDH Complete</title>
<style>
:root{--gold:#c8a04e;--gold-dim:#8a6d2f;--gold-bright:#e8c870;--void:#0a0a0a;--void-light:#111;--ink:#e8e0d0;--ink-dim:#888;--ink-faint:#555;--border:#2a2520;--success:#4ec88a;--danger:#c85a4e;--info:#4e8ac8;--warning:#c8a04e;--red:#a05050;--accent:#d4af37;}
*{margin:0;padding:0;box-sizing:border-box}
body{background:var(--void);color:var(--ink);font-family:'Segoe UI',Arial,sans-serif;line-height:1.5;min-height:100vh}
.phi-nav{position:sticky;top:0;width:100%;background:rgba(10,10,10,0.98);backdrop-filter:blur(12px);border-bottom:1px solid rgba(200,160,78,0.15);z-index:10000;padding:0.5rem 1rem;display:flex;justify-content:center;align-items:center;}
.phi-nav a{color:var(--gold-bright);text-decoration:none;font-family:'Georgia',serif;font-size:1.4rem;letter-spacing:0.12em;padding:0.3rem 1.2rem;border:1px solid rgba(200,160,78,0.25);border-radius:20px;background:rgba(200,160,78,0.04);transition:all 0.3s ease;}
.phi-nav a:hover{border-color:var(--gold);background:rgba(200,160,78,0.1);text-shadow:0 0 10px rgba(200,160,78,0.5);transform:translateY(-1px)}
.section{width:100%;max-width:1400px;margin:0 auto;padding:24px 16px;border-bottom:1px solid var(--border);}
.section-title{color:var(--gold);font-size:1.1rem;letter-spacing:3px;text-transform:uppercase;border-bottom:1px solid var(--gold-dim);padding-bottom:10px;margin-bottom:16px;font-weight:500;}
.sw-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:12px;margin-bottom:16px;}
.sw-card{background:var(--void-light);border:1px solid var(--border);border-radius:6px;padding:16px;text-align:center;position:relative;overflow:hidden;}
.sw-card .sw-label{font-size:0.65rem;text-transform:uppercase;letter-spacing:2px;color:var(--ink-dim);margin-bottom:8px;}
.sw-card .sw-value{font-size:2rem;font-family:'Courier New',monospace;color:var(--gold);font-weight:bold;}
.sw-card .sw-unit{font-size:0.75rem;color:var(--ink-faint);margin-top:4px;}
.sw-card .sw-status{font-size:0.65rem;margin-top:8px;padding:3px 8px;border-radius:3px;display:inline-block;}
.status-quiet{background:rgba(78,200,138,0.15);color:var(--success);border:1px solid rgba(78,200,138,0.3)}
.status-active{background:rgba(200,160,78,0.15);color:var(--warning);border:1px solid rgba(200,160,78,0.3)}
.status-storm{background:rgba(200,90,78,0.15);color:var(--danger);border:1px solid rgba(200,90,78,0.3)}
.plasma-viz{width:100%;height:320px;background:#0d0d12;border:1px solid #2a2a35;border-radius:6px;position:relative;overflow:hidden;margin-bottom:12px;}
#plasma-canvas{display:block;width:100%;height:100%}
.sw-log{background:var(--void-light);border:1px solid var(--border);border-radius:6px;padding:12px;font-family:'Courier New',monospace;font-size:0.75rem;color:var(--ink-dim);max-height:120px;overflow-y:auto;}
.sw-log .log-entry{margin-bottom:4px}
.sw-log .log-time{color:var(--gold-dim);margin-right:8px}
.dual-panel{display:grid;grid-template-columns:1fr 1fr;gap:16px;}
@media(max-width:1100px){.dual-panel{grid-template-columns:1fr}}
.panel-frame{background:var(--void-light);border:1px solid var(--border);border-radius:6px;overflow:hidden;display:flex;flex-direction:column;}
.panel-frame .panel-header{background:rgba(200,160,78,0.08);border-bottom:1px solid var(--border);padding:10px 14px;color:var(--gold);font-size:0.8rem;letter-spacing:2px;text-transform:uppercase;font-weight:500;}
.panel-frame .panel-body{flex:1;padding:12px;overflow:auto;}
.cochlear-wrap{font-family:'Georgia',serif;color:var(--ink);background:var(--void);display:flex;flex-direction:column;align-items:center;padding:1rem;}
.cochlear-wrap h1{font-size:1.3rem;color:var(--gold);text-align:center;margin-bottom:4px;letter-spacing:0.04em}
.cochlear-wrap .subtitle{text-align:center;color:var(--ink-dim);font-size:0.8rem;margin-bottom:16px;font-style:italic}
.cochlear-wrap .controls{display:flex;gap:8px;justify-content:center;margin-bottom:10px;flex-wrap:wrap}
.cochlear-wrap button,.cochlear-wrap select{background:var(--void);color:var(--gold);border:1px solid var(--gold);padding:6px 12px;border-radius:4px;cursor:pointer;font-family:'Georgia',serif;font-size:0.8rem;transition:all 0.2s}
.cochlear-wrap button:hover{background:rgba(200,160,78,0.15)}
.cochlear-wrap button.primary{background:var(--gold);color:var(--void);font-weight:bold;border:none}
.cochlear-wrap button.primary:hover{background:var(--accent)}
.cochlear-wrap select{background:#1a1a20}
.cochlear-wrap .toggles{display:flex;gap:12px;justify-content:center;margin-bottom:12px;flex-wrap:wrap}
.cochlear-wrap .toggles label{display:flex;align-items:center;gap:6px;color:var(--ink-dim);font-size:0.75rem;cursor:pointer}
.cochlear-wrap .toggles input[type="checkbox"]{accent-color:var(--gold);width:14px;height:14px}
.cochlear-wrap #wave-canvas{display:block;border:1px solid #2a2a35;border-radius:6px;background:#0d0d12;max-width:100%;width:100%}
.cochlear-wrap .panels{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:12px;width:100%}
.cochlear-wrap .panel{background:rgba(255,255,255,0.03);border:1px solid rgba(200,160,78,0.15);border-radius:6px;padding:12px}
.cochlear-wrap .panel h3{color:var(--gold);font-size:0.85rem;margin-bottom:6px}
.cochlear-wrap .panel p{margin:0;font-size:0.75rem;color:var(--ink-dim);line-height:1.5}
.cochlear-wrap .panel .highlight{color:var(--accent);font-weight:bold}
.cochlear-wrap .panel .fail{color:var(--red)}
.cochlear-wrap .stage-box{margin-top:12px;width:100%;background:#1a1a20;border-radius:6px;padding:12px;border:1px solid #2a2a35}
.cochlear-wrap .stage-box h3{color:var(--gold);font-size:0.8rem;margin-bottom:8px}
.cochlear-wrap .stages{display:flex;gap:4px;flex-wrap:wrap}
.cochlear-wrap .stage{display:inline-block;padding:4px 8px;border-radius:3px;font-size:0.65rem;transition:all 0.3s;background:#1a1a20;color:#3a3a45;border:1px solid #2a2a35}
.cochlear-wrap .stage.active{background:var(--gold);color:var(--void);border-color:var(--gold)}
.cochlear-wrap .stage.past{background:#2a2a35;color:var(--ink-dim);border-color:#3a3a45}
.cochlear-wrap #stage-desc{margin-top:8px;font-size:0.75rem;color:var(--ink-dim);font-style:italic;min-height:20px}
@media(max-width:600px){.cochlear-wrap .panels{grid-template-columns:1fr}.cochlear-wrap h1{font-size:1.1rem}}
.mesh-wrap{font-family:'Segoe UI',Arial,sans-serif;color:var(--fg);background:var(--bg);line-height:1.5;}
.mesh-wrap h1{color:var(--gold);font-size:1.1rem;letter-spacing:2px;text-transform:uppercase;border-bottom:1px solid var(--gold-dim);padding-bottom:8px;margin-bottom:10px;}
.mesh-wrap h2{color:var(--gold);font-size:0.85rem;letter-spacing:1.5px;text-transform:uppercase;margin:16px 0 8px 0;font-weight:500;}
.mesh-wrap h3{color:var(--ink-dim);font-size:0.75rem;letter-spacing:1.2px;text-transform:uppercase;margin:12px 0 6px 0;font-weight:500;}
.mesh-wrap .meta-row{display:flex;gap:12px;flex-wrap:wrap;font-size:0.7rem;color:var(--ink-dim);margin-bottom:12px;font-family:'Courier New',monospace;}
.mesh-wrap .badge{display:inline-block;padding:2px 6px;border-radius:4px;font-size:0.65rem;font-weight:500;font-family:'Courier New',monospace;}
.mesh-wrap .badge-gov{background:rgba(78,138,200,0.15);color:var(--info);border:1px solid rgba(78,138,200,0.3)}
.mesh-wrap .badge-high{background:rgba(78,200,138,0.15);color:var(--success);border:1px solid rgba(78,200,138,0.3)}
.mesh-wrap .badge-med{background:rgba(200,160,78,0.15);color:var(--warning);border:1px solid rgba(200,160,78,0.3)}
.mesh-wrap .badge-verified{background:rgba(200,160,78,0.15);color:var(--gold);border:1px solid rgba(200,160,78,0.3)}
.mesh-wrap .tabs{display:flex;gap:2px;margin-bottom:12px;border-bottom:1px solid var(--border);overflow-x:auto;}
.mesh-wrap .tab{padding:6px 10px;font-size:0.7rem;cursor:pointer;border-bottom:2px solid transparent;margin-bottom:-1px;color:var(--ink-dim);transition:all 0.15s;white-space:nowrap;letter-spacing:0.5px;text-transform:uppercase;}
.mesh-wrap .tab:hover{color:var(--ink)}
.mesh-wrap .tab.active{color:var(--gold);border-bottom-color:var(--gold)}
.mesh-wrap .tab-content{display:none}
.mesh-wrap .tab-content.active{display:block}
.mesh-wrap .card{background:var(--void-light);border:1px solid var(--border);border-radius:6px;padding:12px;margin-bottom:10px;}
.mesh-wrap .card-label{color:var(--gold);font-size:0.7rem;letter-spacing:1.5px;text-transform:uppercase;margin-bottom:6px;font-weight:bold;}
.mesh-wrap .freq-container{display:flex;align-items:flex-end;gap:6px;height:120px;padding:6px 0;border-bottom:1px solid var(--border);margin-bottom:10px;}
.mesh-wrap .freq-bar{flex:1;display:flex;flex-direction:column;align-items:center;justify-content:flex-end;position:relative;cursor:pointer;transition:opacity 0.2s;}
.mesh-wrap .freq-bar:hover{opacity:0.8}
.mesh-wrap .freq-bar .bar{width:100%;border-radius:4px 4px 0 0;min-height:4px;transition:height 0.5s ease;}
.mesh-wrap .bar-fund{background:linear-gradient(to top,var(--gold-dim),var(--gold))}
.mesh-wrap .bar-harm{background:linear-gradient(to top,rgba(78,138,200,0.6),var(--info))}
.mesh-wrap .bar-null{background:linear-gradient(to top,rgba(85,85,85,0.6),var(--ink-faint))}
.mesh-wrap .freq-bar .label{font-size:0.65rem;margin-top:4px;color:var(--ink);font-weight:500}
.mesh-wrap .freq-bar .hz{font-size:0.7rem;color:var(--gold);margin-top:2px;font-family:'Courier New',monospace}
.mesh-wrap .freq-bar .state{font-size:0.6rem;color:var(--ink-dim);margin-top:2px;font-style:italic}
.mesh-wrap .freq-bar .eeg{font-size:0.55rem;color:var(--ink-faint);margin-top:1px}
.mesh-wrap .omega-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin:10px 0;}
.mesh-wrap .omega-card{padding:10px;border-radius:6px;border:1px solid var(--border);text-align:center;background:var(--void-light);}
.mesh-wrap .omega-card .omega-label{font-size:0.65rem;text-transform:uppercase;letter-spacing:1.5px;margin-bottom:6px;font-weight:bold;}
.mesh-wrap .omega-card .omega-desc{font-size:0.7rem;color:var(--ink-dim);line-height:1.5}
.mesh-wrap .omega-unison{border-color:var(--success)}
.mesh-wrap .omega-unison .omega-label{color:var(--success)}
.mesh-wrap .omega-null{border-color:var(--danger)}
.mesh-wrap .omega-null .omega-label{color:var(--danger)}
.mesh-wrap .omega-harmony{border-color:var(--info)}
.mesh-wrap .omega-harmony .omega-label{color:var(--info)}
.mesh-wrap .cortical-map{display:flex;flex-direction:column;gap:3px;margin:6px 0}
.mesh-wrap .cortical-layer{display:flex;align-items:center;gap:10px;padding:6px 10px;border-radius:4px;font-size:0.7rem;border-left:3px solid transparent;}
.mesh-wrap .cortical-layer .layer-num{font-family:'Courier New',monospace;font-size:0.6rem;color:var(--ink-faint);min-width:28px;}
.mesh-wrap .cortical-layer .layer-freq{font-weight:500;min-width:60px;color:var(--ink)}
.mesh-wrap .cortical-layer .layer-role{color:var(--ink-dim);flex:1}
.mesh-wrap .cortical-layer .layer-sr{font-size:0.6rem;color:var(--gold);font-family:'Courier New',monospace;}
.mesh-wrap .layer-gamma{background:rgba(200,90,78,0.08);border-left-color:rgba(200,90,78,0.5)}
.mesh-wrap .layer-beta{background:rgba(78,138,200,0.08);border-left-color:rgba(78,138,200,0.5)}
.mesh-wrap .layer-alpha{background:rgba(78,200,138,0.08);border-left-color:rgba(78,200,138,0.5)}
.mesh-wrap .layer-theta{background:rgba(200,160,78,0.08);border-left-color:rgba(200,160,78,0.5)}
.mesh-wrap .claims-list{display:flex;flex-direction:column;gap:4px}
.mesh-wrap .claim-row{display:flex;align-items:center;gap:8px;font-size:0.7rem;padding:6px 8px;border-radius:4px;background:var(--void-light);border:1px solid var(--border);}
.mesh-wrap .claim-id{font-family:'Courier New',monospace;font-size:0.6rem;color:var(--ink-faint);min-width:40px;}
.mesh-wrap .claim-text{flex:1}
.mesh-wrap .ref-list{font-size:0.65rem;color:var(--ink-dim)}
.mesh-wrap .ref-item{padding:4px 0;border-bottom:1px solid var(--border);line-height:1.5;}
.mesh-wrap .ref-item:last-child{border-bottom:none}
.mesh-wrap .ref-authors{color:var(--ink-dim)}
.mesh-wrap .ref-year{font-family:'Courier New',monospace;font-size:0.6rem;color:var(--gold)}
.mesh-wrap .ref-journal{font-style:italic;color:var(--ink-faint)}
.mesh-wrap .linkages-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:8px;}
.mesh-wrap .link-card{padding:10px;border-radius:6px;border:1px solid var(--border);background:var(--void-light);}
.mesh-wrap .link-card .pillar-name{font-size:0.7rem;font-weight:500;margin-bottom:4px;color:var(--gold);font-family:'Courier New',monospace;}
.mesh-wrap .link-card .link-desc{font-size:0.65rem;color:var(--ink-dim);line-height:1.5}
.mesh-wrap .phi-chain{font-family:'Courier New',monospace;font-size:0.7rem;color:var(--ink-dim);line-height:1.8;padding:10px;background:var(--void-light);border-radius:6px;border:1px solid var(--border);}
.mesh-wrap .phi-chain .phi-step{display:flex;gap:10px;align-items:baseline}
.mesh-wrap .phi-chain .step-num{color:var(--ink-faint);min-width:50px}
.mesh-wrap .phi-chain .step-val{color:var(--gold)}
.mesh-wrap .phi-chain .step-op{color:var(--ink-faint)}
.mesh-wrap .ratio-arcs{position:relative;height:70px;margin:6px 0;background:var(--void-light);border-radius:6px;border:1px solid var(--border);padding:6px;}
.mesh-wrap .ratio-arcs svg{width:100%;height:100%}
.mesh-wrap .scalar-note{font-size:0.6rem;color:var(--ink-faint);margin-top:4px;font-style:italic;font-family:'Courier New',monospace;}
@media(max-width:640px){.mesh-wrap .omega-grid{grid-template-columns:1fr}.mesh-wrap .freq-container{height:100px}.mesh-wrap .cortical-layer{flex-wrap:wrap}.mesh-wrap .cortical-layer .layer-sr{width:100%;margin-top:4px}}
.nasa-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:12px;}
.nasa-card{background:var(--void-light);border:1px solid var(--border);border-radius:6px;overflow:hidden;}
.nasa-card .nasa-header{background:rgba(200,160,78,0.08);border-bottom:1px solid var(--border);padding:10px 14px;color:var(--gold);font-size:0.75rem;letter-spacing:2px;text-transform:uppercase;font-weight:500;}
.nasa-card .nasa-body{padding:12px}
.nasa-card iframe{width:100%;height:220px;border:none;display:block}
.nasa-card .nasa-desc{font-size:0.7rem;color:var(--ink-dim);margin-top:8px;line-height:1.5;}
.sat-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:12px;}
.sat-card{background:var(--void-light);border:1px solid var(--border);border-radius:6px;overflow:hidden;}
.sat-card .sat-header{background:rgba(200,160,78,0.08);border-bottom:1px solid var(--border);padding:10px 14px;color:var(--gold);font-size:0.75rem;letter-spacing:2px;text-transform:uppercase;font-weight:500;}
.sat-card .sat-body{padding:0}
.sat-card iframe{width:100%;height:280px;border:none;display:block}
.obs-footer{text-align:center;padding:24px 16px;font-size:0.65rem;color:var(--ink-faint);border-top:1px solid var(--border);margin-top:24px;}
</style>
<base target="_blank">
</head>
<body>

<nav class="phi-nav" aria-label="Primary navigation">
  <a href="#" title="Macachor Absolute Scalar Lock">Φ</a>
</nav>

<section class="section" id="space-weather">
  <div class="section-title">Space Weather Station - Scalar-Plasma Cycle v5.1</div>

  <div class="sw-grid" id="sw-metrics">
    <div class="sw-card">
      <div class="sw-label">Kp Index</div>
      <div class="sw-value" id="val-kp">--</div>
      <div class="sw-unit">0-9 Scale</div>
      <div class="sw-status status-quiet" id="status-kp">Loading...</div>
    </div>
    <div class="sw-card">
      <div class="sw-label">AE Index</div>
      <div class="sw-value" id="val-ae">--</div>
      <div class="sw-unit">nT</div>
      <div class="sw-status status-quiet" id="status-ae">Loading...</div>
    </div>
    <div class="sw-card">
      <div class="sw-label">Dst Index</div>
      <div class="sw-value" id="val-dst">--</div>
      <div class="sw-unit">nT</div>
      <div class="sw-status status-quiet" id="status-dst">Loading...</div>
    </div>
    <div class="sw-card">
      <div class="sw-label">Bz (IMF)</div>
      <div class="sw-value" id="val-bz">--</div>
      <div class="sw-unit">nT</div>
      <div class="sw-status status-quiet" id="status-bz">Loading...</div>
    </div>
    <div class="sw-card">
      <div class="sw-label">Solar Wind Speed</div>
      <div class="sw-value" id="val-sw">--</div>
      <div class="sw-unit">km/s</div>
      <div class="sw-status status-quiet" id="status-sw">Loading...</div>
    </div>
    <div class="sw-card">
      <div class="sw-label">Proton Density</div>
      <div class="sw-value" id="val-proton">--</div>
      <div class="sw-unit">p/cm3</div>
      <div class="sw-status status-quiet" id="status-proton">Loading...</div>
    </div>
  </div>

  <div class="plasma-viz">
    <canvas id="plasma-canvas"></canvas>
  </div>

  <div class="sw-log" id="sw-log">
    <div class="log-entry"><span class="log-time">[INIT]</span> Scalar-Plasma Cycle initialized - awaiting NOAA feed...</div>
  </div>
</section>

<section class="section" id="dual-panel">
  <div class="section-title">Scalar Density Architectures</div>
  <div class="dual-panel">

    <div class="panel-frame">
      <div class="panel-header">Cochlear Scalar Density Wave</div>
      <div class="panel-body">
        <div class="cochlear-wrap">
          <p class="subtitle" style="text-align:center;color:var(--ink-dim);font-size:0.8rem;margin-bottom:12px;font-style:italic">
            Cycle-by-Cycle Amplification as Vibrational Unison | Petit &amp; Avan (2025)
          </p>
          <div class="controls">
            <button id="btn-play" class="primary">Play</button>
            <button id="btn-pause">Pause</button>
            <button id="btn-reset">Reset</button>
            <select id="freq-select">
              <option value="1">1 kHz - Basal (low)</option>
              <option value="3">3 kHz - Mid</option>
              <option value="8" selected>8 kHz - High</option>
              <option value="20">20 kHz - Ultrahigh</option>
            </select>
          </div>
          <div class="toggles">
            <label><input type="checkbox" id="show-damping" checked> Show Damping (Vector Model)</label>
            <label><input type="checkbox" id="show-resonance" checked> Show Resonance (Scalar Model)</label>
            <label><input type="checkbox" id="show-phase"> Show Phase Lock</label>
          </div>
          <canvas id="wave-canvas" width="600" height="240"></canvas>
          <div class="panels">
            <div class="panel">
              <h3>Vector Model (Dissipative)</h3>
              <p>Sound = force chain. Hair cells transduce to neurons encode. Friction is the enemy. The RC time constant is a bug to be overcome. Amplification means adding more force. <span class="fail">Fails above the RC cutoff frequency.</span></p>
            </div>
            <div class="panel">
              <h3>Scalar Model (Resonant)</h3>
              <p>Sound = density perturbation. The cochlea enters <strong>unison</strong> with the wave. Friction is irrelevant in resonance. The RC constant is a feature that prevents oscillatory fragmentation. Amplification = phase-locked density restoration. <span class="highlight">Operates to 150+ kHz.</span></p>
            </div>
          </div>
          <div class="stage-box">
            <h3>Amplification Cascade Stage Monitor</h3>
            <div class="stages">
              <span class="stage" id="st-0">1. Stereocilia Deflection</span>
              <span class="stage" id="st-1">2. MET Channel (TMC1)</span>
              <span class="stage" id="st-2">3. Cl- to Prestin</span>
              <span class="stage" id="st-3">4. Conformation Change</span>
              <span class="stage" id="st-4">5. Longitudinal Strain</span>
              <span class="stage" id="st-5">6. Tectorial Coupling</span>
              <span class="stage" id="st-6">7. IHC Excitation</span>
            </div>
            <p id="stage-desc">Click Play to initiate the coherence cycle...</p>
          </div>
        </div>
      </div>
    </div>

    <div class="panel-frame">
      <div class="panel-header">MESH-006 - Stolc-NASA Omega States</div>
      <div class="panel-body">
        <div class="mesh-wrap">
          <div class="meta-row">
            <span><span class="badge badge-gov">GOVERNMENT_AGENCY</span></span>
            <span><span class="badge badge-verified">VERIFIED</span></span>
            <span>Coherence: <strong style="color:var(--success);">0.98</strong></span>
            <span>6 claims - 7 refs - 5 linkages</span>
            <span>Omega(w_Earth, w_brain)</span>
            <span>MGDH-2026-07-28</span>
          </div>

          <div class="tabs">
            <div class="tab active" onclick="meshSwitchTab('frequencies')">Frequencies</div>
            <div class="tab" onclick="meshSwitchTab('conditions')">Omega Conditions</div>
            <div class="tab" onclick="meshSwitchTab('cortical')">Cortical Map</div>
            <div class="tab" onclick="meshSwitchTab('claims')">Claims &amp; Refs</div>
            <div class="tab" onclick="meshSwitchTab('linkages')">Linkages</div>
          </div>

          <div id="mesh-tab-frequencies" class="tab-content active">
            <div class="card">
              <div class="card-label">Schumann Resonance Spectrum</div>
              <div class="freq-container" id="mesh-freqContainer"></div>
              <div class="scalar-note">Fundamental (gold) = SR1 - Harmonics mapped to state (blue) - Unmapped harmonics (gray)</div>
            </div>
            <div class="card">
              <div class="card-label">Harmonic Ratios (relative to SR1 fundamental)</div>
              <div class="ratio-arcs">
                <svg id="mesh-ratioSvg" viewBox="0 0 500 80" preserveAspectRatio="xMidYMid meet"></svg>
              </div>
              <div class="scalar-note">Arcs show frequency multiplication factors from 7.83 Hz baseline - Integer-near ratios enable cross-band phase-locking</div>
            </div>
          </div>

          <div id="mesh-tab-conditions" class="tab-content">
            <h2>Omega Structure Mapping</h2>
            <div class="omega-grid">
              <div class="omega-card omega-unison">
                <div class="omega-label">Unison</div>
                <div class="omega-desc">SR present - HRV elevation, parasympathetic tone, EEG band alignment</div>
              </div>
              <div class="omega-card omega-null">
                <div class="omega-label">Null</div>
                <div class="omega-desc">SR absent (beyond LEO or inside BMSR) - potential stressor, autonomic drift, circadian disruption</div>
              </div>
              <div class="omega-card omega-harmony">
                <div class="omega-label">Harmony</div>
                <div class="omega-desc">SR harmonic series permits cross-band interaction via integer / golden ratios</div>
              </div>
            </div>

            <h2>Phi Scaling Chain</h2>
            <div class="phi-chain">
              <div class="phi-step"><span class="step-num">Step 0</span><span class="step-val">1.855 x 10^43 Hz</span><span class="step-op">- Planck frequency</span></div>
              <div class="phi-step"><span class="step-num">Phi^-72</span><span class="step-val">669 Hz</span><span class="step-op">- golden reduction</span></div>
              <div class="phi-step"><span class="step-num">Phi^-7</span><span class="step-val" style="color:var(--gold);">7.83 Hz</span><span class="step-op">- 669 / Phi^7 = 7.83 - Schumann fundamental</span></div>
            </div>
            <div class="scalar-note" style="margin-top:8px;">Golden ratio reduction bridges Planck scale to geophysical measurement - Macachor Absolute scalar lock</div>

            <h2>Biomarkers</h2>
            <div class="card">
              <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:10px;font-size:0.65rem;">
                <div><strong style="color:var(--success);">Primary</strong><br>HRV - EEG power bands - Melatonin</div>
                <div><strong style="color:var(--info);">Secondary</strong><br>Heart rate - Blood pressure - Parasympathetic tone</div>
                <div><strong style="color:var(--warning);">Mechanistic</strong><br>Ca2+ binding - Microtubule coherence</div>
              </div>
            </div>
          </div>

          <div id="mesh-tab-cortical" class="tab-content">
            <div class="card">
              <div class="card-label">Cortical Layer Oscillation Mapping</div>
              <div style="font-size:0.65rem;color:var(--ink-dim);margin-bottom:8px;">
                Mendoza-Halliday et al. 2024 - Nature Neuroscience 27:547-560 - Universal across 14 cortical areas, 4 mammalian species
              </div>
              <div class="cortical-map">
                <div class="cortical-layer layer-gamma">
                  <span class="layer-num">L1</span>
                  <span class="layer-freq">40-60 Hz</span>
                  <span class="layer-role">External sensory (gamma)</span>
                  <span class="layer-sr">- SR5 (33.8 Hz) gamma threshold</span>
                </div>
                <div class="cortical-layer layer-gamma">
                  <span class="layer-num">L2/3</span>
                  <span class="layer-freq">40-60 Hz</span>
                  <span class="layer-role">External sensory (gamma)</span>
                  <span class="layer-sr">- SR5 (33.8 Hz) gamma threshold</span>
                </div>
                <div class="cortical-layer layer-beta">
                  <span class="layer-num">L4</span>
                  <span class="layer-freq">20-30 Hz</span>
                  <span class="layer-role">Feedforward hub / frequency crossover</span>
                  <span class="layer-sr">- SR3 (20.8 Hz) - SR4 (27.3 Hz)</span>
                </div>
                <div class="cortical-layer layer-alpha">
                  <span class="layer-num">L5</span>
                  <span class="layer-freq">6-16 Hz</span>
                  <span class="layer-role">Internal cognitive (alpha/beta)</span>
                  <span class="layer-sr">- SR2 (14.3 Hz) concentration</span>
                </div>
                <div class="cortical-layer layer-theta">
                  <span class="layer-num">L6</span>
                  <span class="layer-freq">4-8 Hz</span>
                  <span class="layer-role">Deep internal (theta/alpha)</span>
                  <span class="layer-sr">- SR1 (7.83 Hz) relaxation</span>
                </div>
              </div>
              <div class="scalar-note" style="margin-top:8px;padding:6px;border-left:2px solid var(--border);">
                <strong>Key finding:</strong> Superficial layers (L1-L2/3) process external sensory information with fast gamma - aligned to SR5 gamma threshold. Deep layers (L5-L6) maintain internal cognitive states with slow alpha/theta - aligned to SR1-SR2. Layer 4 is the frequency crossover point where feedforward input enters the cortical microcircuit.
              </div>
            </div>
            <div class="card">
              <div class="card-label">Information Flow Architecture</div>
              <div style="font-size:0.65rem;color:var(--ink-dim);line-height:1.7;">
                <div style="margin-bottom:4px;"><strong style="color:var(--info);">Bottom-up (feedforward):</strong> Gamma originates in Layer 4, propagates to superficial (2ms delay) and deep (1ms delay) layers - Bastos et al. PNAS 2014</div>
                <div style="margin-bottom:4px;"><strong style="color:var(--success);">Top-down (feedback):</strong> Alpha propagates from deep layers downward, regulating which sensory information reaches conscious awareness</div>
                <div><strong style="color:var(--warning);">Imbalance pathologies:</strong> Gamma dominance - ADHD (excess sensory gating failure) - Alpha dominance - schizophrenia (insufficient sensory input)</div>
              </div>
            </div>
          </div>

          <div id="mesh-tab-claims" class="tab-content">
            <h2>Validated Claims</h2>
            <div class="claims-list">
              <div class="claim-row"><span class="claim-id">SR-001</span><span class="claim-text">7.83 Hz is Earth fundamental scalar identity frequency</span><span class="badge badge-high">HIGH</span></div>
              <div class="claim-row"><span class="claim-id">SR-002</span><span class="claim-text">Schumann harmonic series maps to primary EEG frequency bands</span><span class="badge badge-high">HIGH</span></div>
              <div class="claim-row"><span class="claim-id">SR-003</span><span class="claim-text">Absence of resonant frequency = decoherence / stressor</span><span class="badge badge-high">HIGH</span></div>
              <div class="claim-row"><span class="claim-id">SR-004</span><span class="claim-text">HRV correlates with scalar substrate power</span><span class="badge badge-high">HIGH</span></div>
              <div class="claim-row"><span class="claim-id">SR-005</span><span class="claim-text">Weak ELF fields modulate neural calcium binding</span><span class="badge badge-med">MEDIUM</span></div>
              <div class="claim-row"><span class="claim-id">SR-006</span><span class="claim-text">Cardiovascular events cluster at SR frequency perturbations</span><span class="badge badge-high">HIGH</span></div>
            </div>

            <h2>References</h2>
            <div class="ref-list">
              <div class="ref-item"><span class="ref-authors">Schlegel, K. &amp; Füllekrug, M.</span> - <span class="ref-year">1999</span> - Schumann resonance parameter changes during high-energy particle precipitation - <span class="ref-journal">J. Geophys. Res.</span> - DOI: 10.1029/1999JA900084</div>
              <div class="ref-item"><span class="ref-authors">Schumann, W.O.</span> - <span class="ref-year">1952</span> - Über die Ausbreitung sehr langer elektrischer Wellen um die Erde - <span class="ref-journal">Nuovo Cim</span></div>
              <div class="ref-item"><span class="ref-authors">Mattoni, M. et al.</span> - <span class="ref-year">2020</span> - Exploring the relationship between geomagnetic activity and human heart rate variability - <span class="ref-journal">Eur J Appl Physiol</span> - DOI: 10.1007/s00421-020-04371-9</div>
              <div class="ref-item"><span class="ref-authors">McCraty, R. et al.</span> - <span class="ref-year">2017</span> - Synchronization of Human Autonomic Nervous System Rhythms with Geomagnetic Activity - <span class="ref-journal">IJERPH</span> - DOI: 10.3390/ijerph14070770</div>
              <div class="ref-item"><span class="ref-authors">Alabdulgader, A. et al.</span> - <span class="ref-year">2018</span> - Long-Term Study of Heart Rate Variability Responses to Changes in the Solar and Geomagnetic Environment - <span class="ref-journal">Sci Rep</span> - DOI: 10.1038/s41598-018-20932-x</div>
              <div class="ref-item"><span class="ref-authors">Fdez-Arroyabe, P. et al.</span> - <span class="ref-year">2020</span> - Schumann resonance and cardiovascular hospital admission in Granada, Spain - <span class="ref-journal">Sci Total Environ</span> - DOI: 10.1016/j.scitotenv.2019.135813</div>
              <div class="ref-item"><span class="ref-authors">Bawin, S.M. &amp; Adey, W.R.</span> - <span class="ref-year">1976</span> - Sensitivity of calcium binding in cerebral tissue to weak environmental electric fields - <span class="ref-journal">PNAS</span> - DOI: 10.1073/pnas.73.6.1999</div>
            </div>
          </div>

          <div id="mesh-tab-linkages" class="tab-content">
            <h2>Cross-Disciplinary Linkages</h2>
            <div class="linkages-grid">
              <div class="link-card"><div class="pillar-name">Oriani-1977</div><div class="link-desc">Crust-mantle density equilibrium to Earth-ionosphere cavity density equilibrium</div></div>
              <div class="link-card"><div class="pillar-name">Fitzpatrick-2006</div><div class="link-desc">EM scalar potential to SR as global scalar potential field</div></div>
              <div class="link-card"><div class="pillar-name">Masood-2013</div><div class="link-desc">Vorticity coherence to atmospheric cavity standing wave coherence</div></div>
              <div class="link-card"><div class="pillar-name">Shah-2019</div><div class="link-desc">Neural phase-locking to EEG-SR frequency band overlap</div></div>
              <div class="link-card"><div class="pillar-name">Denton-2025</div><div class="link-desc">Plasma density equilibrium to magnetosphere-ionosphere coupling to SR</div></div>
            </div>

            <h2>Supplementary Sources</h2>
            <div class="ref-list">
              <div class="ref-item"><span class="ref-authors">Tatum, J.</span> - <span class="ref-year">EM textbook</span> - Chapter 3: Dipole and Quadrupole Moments - University of Victoria - <span class="ref-journal">astro.uvic.ca/~tatum/elmag/em03.pdf</span> - Classical foundation for dipole-toroidal model</div>
              <div class="ref-item"><span class="ref-authors">Mendoza-Halliday, D. et al.</span> - <span class="ref-year">2024</span> - A ubiquitous spectrolaminar motif of local field potential power across the cerebral cortex - <span class="ref-journal">Nature Neuroscience 27:547-560</span> - Cortical layers: gamma (superficial) vs alpha/beta (deep)</div>
              <div class="ref-item"><span class="ref-authors">Stoupel, E.</span> - <span class="ref-year">1999</span> - Effect of geomagnetic activity on cardiovascular parameters - <span class="ref-journal">J Clin Basic Cardiol 2:34-40</span> - High GMA to more MI, higher BP, more CVA</div>
              <div class="ref-item"><span class="ref-authors">PMC9233046</span> - <span class="ref-year">2022</span> - Geomagnetic disturbances reduce heart rate variability - <span class="ref-journal">Environ Health 21:71</span> - Intense GMD: r-MSSD -14.7ms (p=0.0007)</div>
              <div class="ref-item"><span class="ref-authors">Bastos, A.M. et al.</span> - <span class="ref-year">2014</span> - A microcircuit for predictive coding - <span class="ref-journal">PNAS 111:8681-8686</span> - Alpha = top-down feedback, Gamma = bottom-up feedforward</div>
              <div class="ref-item"><span class="ref-authors">Buffalo, E.A. et al.</span> - <span class="ref-year">2011</span> - Laminar differences in gamma and alpha coherence - <span class="ref-journal">J Neurosci 31:11741-11752</span> - Attention enhances superficial gamma, reduces deep alpha</div>
              <div class="ref-item"><span class="ref-authors">Alabdulgader, A. et al.</span> - <span class="ref-year">2018</span> - Long-Term Study of HRV Responses to Changes in the Solar and Geomagnetic Environment - <span class="ref-journal">Sci Rep 8:2663</span> - 5-week longitudinal: HRV positively correlated with sunspot number</div>
            </div>
          </div>

          <div class="scalar-note" style="margin-top:16px;text-align:center;">
            MESH-006 - Stolc-NASA - Omega(w_Earth, w_brain) - M = (sqrt(5)-1)/2 - MGDH-2026-07-28 - Validated by Omega-PRIME Christopher Macachor
          </div>
        </div>
      </div>
    </div>

  </div>
</section>
