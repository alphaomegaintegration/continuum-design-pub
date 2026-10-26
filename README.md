<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Continuum Design — Business Model</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@200;300;400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
:root{
  /* Alpha Omega green palette — forest/teal hues */
  --bg-deep:      #051912;
  --bg-base:      #08251C;
  --bg-card:      rgba(15, 52, 39, 0.55);
  --bg-card-hi:   rgba(25, 78, 58, 0.65);

  --border-faint: rgba(125, 193, 166, 0.12);
  --border-soft:  rgba(125, 193, 166, 0.26);
  --border-firm:  rgba(125, 193, 166, 0.50);

  --green-900:    #0B2A1F;
  --green-700:    #154835;
  --green-600:    #1F6B4F;
  --green-500:    #2E8B6A;   /* primary brand green */
  --green-400:    #4FA787;
  --green-300:    #7DC1A6;
  --green-200:    #A8D8C0;
  --green-100:    #D2EAD9;

  --text-primary:   #F4FFF8;
  --text-secondary: #BFEED5;
  --text-tertiary:  #78A593;
  --text-muted:     #466657;

  --ease: cubic-bezier(.2,.7,.3,1);

  --font-display: 'IBM Plex Sans', -apple-system, BlinkMacSystemFont, sans-serif;
  --font-mono:    'IBM Plex Mono', ui-monospace, monospace;
}

*{margin:0;padding:0;box-sizing:border-box}
html,body{
  width:100%;height:100%;
  background:#000;
  font-family:var(--font-display);
  overflow:hidden;
  -webkit-font-smoothing:antialiased;
  text-rendering:optimizeLegibility;
}

.stage{
  position:relative;
  width:100vw;height:100vh;
  background:
    radial-gradient(ellipse 80% 60% at 75% 0%, rgba(46,139,106,0.12) 0%, transparent 60%),
    radial-gradient(ellipse 60% 50% at 10% 100%, rgba(46,139,106,0.08) 0%, transparent 55%),
    linear-gradient(180deg, var(--bg-base) 0%, var(--bg-deep) 100%);
  overflow:hidden;
}

.grid-bg{
  position:absolute;inset:0;
  background-image:
    linear-gradient(rgba(125,193,166,0.035) 1px, transparent 1px),
    linear-gradient(90deg, rgba(125,193,166,0.035) 1px, transparent 1px);
  background-size:80px 80px;
  pointer-events:none;
  mask-image: radial-gradient(ellipse 90% 80% at 50% 50%, black 30%, transparent 90%);
}

/* (Brand bar removed per user direction) */

.scene{
  position:absolute;inset:0;
  display:grid;
  grid-template-rows: 130px 1fr 100px;
  padding:0 80px;
  opacity:0;
  transition:opacity 0.5s var(--ease);
  pointer-events:none;
}
.scene.active{opacity:1;pointer-events:auto;}

.scene-header{
  grid-row:1;
  align-self:end;
  padding-bottom:8px;
  display:flex;flex-direction:column;align-items:center;
  text-align:center;
}
.scene-content{
  grid-row:2;
  align-self:center;
  display:flex;flex-direction:column;align-items:center;
  width:100%;
}

.eyebrow{
  font-family:var(--font-mono);
  font-size:12px;letter-spacing:4px;text-transform:uppercase;
  color:var(--green-400);font-weight:500;
  display:flex;align-items:center;gap:14px;
  opacity:0;transform:translateY(-4px);
  transition:opacity .6s .15s var(--ease), transform .6s .15s var(--ease);
}
.scene.active .eyebrow{opacity:1;transform:translateY(0)}
.eyebrow-num{
  display:inline-block;
  border:1px solid var(--border-soft);
  padding:2px 8px;border-radius:3px;
  color:var(--green-300);font-weight:500;
}
.section-title{
  font-size:46px;font-weight:300;color:var(--text-primary);
  letter-spacing:-1.2px;line-height:1.1;
  margin-top:14px;
  opacity:0;transform:translateY(8px);
  transition:opacity .7s .3s var(--ease), transform .7s .3s var(--ease);
}
.scene.active .section-title{opacity:1;transform:translateY(0)}

#scene1 .scene-content{justify-content:center}
.title-eyebrow{
  font-family:var(--font-mono);
  font-size:13px;letter-spacing:6px;text-transform:uppercase;
  color:var(--green-400);margin-bottom:28px;
  opacity:0;transform:translateY(8px);
  transition:opacity .7s .2s var(--ease), transform .7s .2s var(--ease);
}
.scene.active .title-eyebrow{opacity:1;transform:translateY(0)}
.title-main{
  font-size:96px;font-weight:200;color:var(--text-primary);
  letter-spacing:-3px;line-height:1.0;text-align:center;
  opacity:0;transform:translateY(14px);
  transition:opacity 1s .5s var(--ease), transform 1s .5s var(--ease);
}
.title-main em{
  font-style:normal;font-weight:300;
  background:linear-gradient(135deg, var(--green-300) 0%, var(--green-500) 100%);
  -webkit-background-clip:text;
  background-clip:text;
  -webkit-text-fill-color:transparent;
}
.scene.active .title-main{opacity:1;transform:translateY(0)}
.title-sub{
  font-size:21px;font-weight:300;color:var(--text-secondary);
  margin-top:32px;letter-spacing:0.1px;text-align:center;max-width:760px;
  line-height:1.45;
  opacity:0;
  transition:opacity .9s 1.1s var(--ease);
}
.scene.active .title-sub{opacity:1}
.title-rule{
  width:60px;height:2px;background:var(--green-500);
  margin-top:44px;
  opacity:0;transform:scaleX(0);transform-origin:left;
  transition:opacity .5s 1.5s var(--ease), transform .8s 1.5s var(--ease);
}
.scene.active .title-rule{opacity:1;transform:scaleX(1)}

.pricing-card{
  background:var(--bg-card);
  border:1px solid var(--border-soft);
  border-radius:16px;
  padding:52px 64px;
  max-width:1080px;width:100%;
  backdrop-filter:blur(12px);
  margin-top:28px;
}
.tier-row{
  display:grid;grid-template-columns:repeat(3,1fr);gap:48px;
}
.tier{
  border-left:2px solid var(--green-500);
  padding-left:22px;
  opacity:0;transform:translateX(-10px);
  transition:opacity .6s var(--ease), transform .6s var(--ease);
}
.scene.active .tier:nth-child(1){transition-delay:.45s}
.scene.active .tier:nth-child(2){transition-delay:.65s}
.scene.active .tier:nth-child(3){transition-delay:.85s}
.scene.active .tier{opacity:1;transform:translateX(0)}
.tier-name{
  font-family:var(--font-mono);
  font-size:11px;letter-spacing:3px;text-transform:uppercase;
  color:var(--green-300);font-weight:500;margin-bottom:12px;
}
.tier-headline{
  font-size:24px;font-weight:300;color:var(--text-primary);
  line-height:1.3;letter-spacing:-0.4px;
}
.tier-meta{
  font-size:13px;color:var(--text-tertiary);margin-top:10px;
  font-weight:400;letter-spacing:0.2px;
}
.pricing-pills{
  display:flex;justify-content:center;gap:12px;flex-wrap:wrap;
  margin-top:40px;padding-top:32px;
  border-top:1px solid var(--border-faint);
}
.pill{
  display:inline-flex;align-items:center;gap:10px;
  padding:9px 18px;
  background:rgba(46,139,106,0.08);
  border:1px solid var(--border-soft);
  border-radius:24px;
  font-size:13px;color:var(--green-200);font-weight:400;
  letter-spacing:0.1px;
  opacity:0;transform:translateY(6px);
  transition:opacity .5s var(--ease), transform .5s var(--ease);
}
.scene.active .pill:nth-child(1){transition-delay:1.1s}
.scene.active .pill:nth-child(2){transition-delay:1.2s}
.scene.active .pill:nth-child(3){transition-delay:1.3s}
.scene.active .pill{opacity:1;transform:translateY(0)}
.pill::before{
  content:"";width:5px;height:5px;border-radius:50%;
  background:var(--green-400);
}

.deploy-grid{
  display:grid;grid-template-columns:1fr 1fr;gap:28px;
  max-width:1080px;width:100%;margin-top:28px;
}
.deploy-card{
  background:var(--bg-card);
  border:1px solid var(--border-soft);
  border-radius:16px;
  padding:42px 44px;
  position:relative;
  backdrop-filter:blur(12px);
  opacity:0;transform:translateY(14px);
  transition:opacity .7s var(--ease), transform .7s var(--ease);
}
.scene.active .deploy-card:nth-child(1){transition-delay:.45s}
.scene.active .deploy-card:nth-child(2){transition-delay:.7s}
.scene.active .deploy-card{opacity:1;transform:translateY(0)}
.deploy-card.featured{
  border-color:var(--border-firm);
  background:var(--bg-card-hi);
  box-shadow: 0 0 0 1px rgba(125,193,166,0.25), 0 24px 60px -20px rgba(46,139,106,0.35);
}
.deploy-icon{
  width:46px;height:46px;
  border:1px solid var(--border-firm);
  border-radius:10px;
  background:rgba(46,139,106,0.08);
  display:flex;align-items:center;justify-content:center;
  margin-bottom:24px;
}
.deploy-icon svg{width:22px;height:22px;}
.deploy-name{
  font-size:24px;font-weight:400;color:var(--text-primary);
  margin-bottom:10px;letter-spacing:-0.4px;
}
.deploy-desc{
  font-size:15px;color:var(--text-secondary);line-height:1.55;
  font-weight:300;
}
.deploy-badge{
  position:absolute;top:24px;right:24px;
  font-family:var(--font-mono);
  font-size:10px;letter-spacing:2.5px;text-transform:uppercase;
  padding:5px 11px;border-radius:4px;
  background:var(--green-500);color:var(--text-primary);
  font-weight:500;
}

.boundary-wrap{
  width:100%;max-width:1000px;margin-top:32px;
  position:relative;
  padding:24px 0;
}
.boundary{
  position:relative;
  border:1.5px dashed var(--border-firm);
  border-radius:18px;
  background:rgba(46,139,106,0.04);
  padding:56px 64px;
  opacity:0;transform:scale(.97);
  transition:opacity .7s var(--ease), transform .7s var(--ease);
}
.scene.active .boundary{opacity:1;transform:scale(1)}
.boundary-tag{
  position:absolute;top:-12px;left:40px;
  background:var(--bg-deep);
  padding:0 16px;
  font-family:var(--font-mono);
  font-size:11px;letter-spacing:3px;text-transform:uppercase;
  color:var(--green-400);font-weight:500;
  line-height:24px;
}
.boundary-grid{
  display:grid;grid-template-columns:1fr 1fr;gap:28px 56px;
}
.data-item{
  display:flex;align-items:flex-start;gap:16px;
  opacity:0;transform:translateX(-8px);
  transition:opacity .55s var(--ease), transform .55s var(--ease);
}
.scene.active .data-item:nth-child(1){transition-delay:.55s}
.scene.active .data-item:nth-child(2){transition-delay:.75s}
.scene.active .data-item:nth-child(3){transition-delay:.95s}
.scene.active .data-item:nth-child(4){transition-delay:1.15s}
.scene.active .data-item{opacity:1;transform:translateX(0)}
.data-check{
  width:30px;height:30px;border-radius:50%;
  background:rgba(46,139,106,0.18);
  border:1px solid var(--green-500);
  display:flex;align-items:center;justify-content:center;
  flex-shrink:0;margin-top:2px;
}
.data-check svg{width:14px;height:14px;}
.data-text{
  font-size:17px;color:var(--text-primary);font-weight:300;
  line-height:1.4;letter-spacing:-0.1px;
}
.data-text strong{font-weight:500;color:var(--green-200);}

#scene5 .scene-content{justify-content:center}
.close-logo{
  width:380px;height:auto;
  margin-bottom:44px;
  /* mix-blend screen drops the black background, leaves only the white logo + wordmark */
  mix-blend-mode:screen;
  opacity:0;transform:scale(.92);
  transition:opacity .6s var(--ease), transform .8s cubic-bezier(.34,1.4,.64,1);
}
.scene.active .close-logo{opacity:1;transform:scale(1)}
.close-tag{
  font-family:var(--font-mono);
  font-size:11px;letter-spacing:5px;text-transform:uppercase;
  color:var(--green-400);font-weight:500;margin-bottom:32px;
  opacity:0;
  transition:opacity .6s .35s var(--ease);
}
.scene.active .close-tag{opacity:1}
.close-line{
  font-size:38px;font-weight:300;color:var(--text-primary);
  letter-spacing:-0.8px;line-height:1.45;
  text-align:center;max-width:1000px;
}
.close-line span{
  display:inline-block;
  opacity:0;transform:translateY(8px);
  transition:opacity .6s var(--ease), transform .6s var(--ease);
}
.scene.active .close-line span:nth-child(1){transition-delay:.55s}
.scene.active .close-line span:nth-child(2){transition-delay:1.05s}
.scene.active .close-line span:nth-child(3){transition-delay:1.55s}
.scene.active .close-line span{opacity:1;transform:translateY(0)}
.close-divider{
  display:inline-block;width:6px;height:6px;border-radius:50%;
  background:var(--green-500);
  margin:0 18px 8px;
  vertical-align:middle;
}
.close-line .accent{
  background:linear-gradient(135deg, var(--green-300) 0%, var(--green-500) 100%);
  -webkit-background-clip:text;
  background-clip:text;
  -webkit-text-fill-color:transparent;
  font-weight:400;
}

.caption-zone{
  grid-row:3;
  display:flex;align-items:end;justify-content:center;
  padding-bottom:30px;
  pointer-events:none;
}
.caption{
  background:rgba(11,42,31,0.85);
  border:1px solid var(--border-soft);
  padding:13px 28px;border-radius:6px;
  font-size:16px;color:var(--text-primary);font-weight:300;
  max-width:1100px;text-align:center;line-height:1.45;
  letter-spacing:0.1px;
  opacity:0;transition:opacity .35s var(--ease);
  backdrop-filter:blur(8px);
}
.caption.visible{opacity:1}

.progress-track{
  position:absolute;bottom:0;left:0;right:0;height:2px;
  background:rgba(125,193,166,0.08);
  z-index:30;
}
.progress-fill{
  height:100%;
  background:linear-gradient(90deg, var(--green-500), var(--green-300));
  width:0%;transition:width .1s linear;
}

.replay-btn{
  position:absolute;top:36px;right:56px;
  background:transparent;
  border:1px solid var(--border-firm);
  color:var(--green-200);
  padding:9px 22px;border-radius:24px;
  font-family:var(--font-mono);
  font-size:11px;letter-spacing:2px;text-transform:uppercase;
  cursor:pointer;font-weight:500;
  z-index:50;display:none;
  transition:background .2s var(--ease), color .2s var(--ease);
}
.replay-btn:hover{background:rgba(46,139,106,0.15);color:var(--text-primary);}
.replay-btn.show{display:block}

.icon-stroke{stroke:var(--green-400);stroke-width:1.6;fill:none;stroke-linecap:round;stroke-linejoin:round;}
.deploy-card.featured .icon-stroke{stroke:var(--green-300);}
.data-check .icon-stroke{stroke:var(--green-300);stroke-width:2;}
</style>
</head>
<body>
<div class="stage" id="stage">
  <div class="grid-bg"></div>

  <button class="replay-btn" id="replay">▶ Replay</button>

  <div class="scene" id="scene1">
    <div class="scene-header"></div>
    <div class="scene-content">
      <div class="title-eyebrow">Business Model</div>
      <div class="title-main">Procurement-ready.<br><em>Mission-aligned.</em></div>
      <div class="title-sub">Built for federal appropriation cycles, not commercial SaaS budgets.</div>
      <div class="title-rule"></div>
    </div>
    <div class="caption-zone"></div>
  </div>

  <div class="scene" id="scene2">
    <div class="scene-header">
      <div class="eyebrow">
        <span class="eyebrow-num">01</span>
        <span>Pricing</span>
      </div>
      <h2 class="section-title">Predictable subscription, scaled to mission</h2>
    </div>
    <div class="scene-content">
      <div class="pricing-card">
        <div class="tier-row">
          <div class="tier">
            <div class="tier-name">Squad</div>
            <div class="tier-headline">Mission teams<br>&amp; pilots</div>
            <div class="tier-meta">Per-named-user · Annual</div>
          </div>
          <div class="tier">
            <div class="tier-name">Program</div>
            <div class="tier-headline">Program-office<br>deployments</div>
            <div class="tier-meta">Multi-year · Tiered discounts</div>
          </div>
          <div class="tier">
            <div class="tier-name">Enterprise</div>
            <div class="tier-headline">Agency-wide<br>rollout</div>
            <div class="tier-meta">Volume pricing · Predictable</div>
          </div>
        </div>
        <div class="pricing-pills">
          <div class="pill">Per-named-user licensing</div>
          <div class="pill">Annual or multi-year</div>
          <div class="pill">Scales with adoption, not consumption</div>
        </div>
      </div>
    </div>
    <div class="caption-zone">
      <div class="caption" data-scene="2"></div>
    </div>
  </div>

  <div class="scene" id="scene3">
    <div class="scene-header">
      <div class="eyebrow">
        <span class="eyebrow-num">02</span>
        <span>Deployment</span>
      </div>
      <h2 class="section-title">Inside your boundary, on your terms</h2>
    </div>
    <div class="scene-content">
      <div class="deploy-grid">
        <div class="deploy-card">
          <div class="deploy-icon">
            <svg viewBox="0 0 24 24"><path class="icon-stroke" d="M3 12a9 9 0 0 1 18 0M3 12a9 9 0 0 0 18 0M3 12h18M12 3a14 14 0 0 1 0 18M12 3a14 14 0 0 0 0 18"/></svg>
          </div>
          <div class="deploy-name">Customer-hosted</div>
          <div class="deploy-desc">GovCloud · On-premises · Disconnected enclave</div>
        </div>
        <div class="deploy-card featured">
          <div class="deploy-badge">Recommended</div>
          <div class="deploy-icon">
            <svg viewBox="0 0 24 24"><path class="icon-stroke" d="M4 7h16M4 12h16M4 17h10M16 14l4 3-4 3"/></svg>
          </div>
          <div class="deploy-name">Continuum AF Bundle</div>
          <div class="deploy-desc">Platform + Alpha Omega design &amp; DevSecOps services</div>
        </div>
      </div>
    </div>
    <div class="caption-zone">
      <div class="caption" data-scene="3"></div>
    </div>
  </div>

  <div class="scene" id="scene4">
    <div class="scene-header">
      <div class="eyebrow">
        <span class="eyebrow-num">03</span>
        <span>Data &amp; IP Posture</span>
      </div>
      <h2 class="section-title">Government data stays government data</h2>
    </div>
    <div class="scene-content">
      <div class="boundary-wrap">
        <div class="boundary">
          <div class="boundary-tag">Customer Accreditation Boundary</div>
          <div class="boundary-grid">
            <div class="data-item">
              <div class="data-check">
                <svg viewBox="0 0 24 24"><path class="icon-stroke" d="M5 12l5 5L20 7"/></svg>
              </div>
              <div class="data-text"><strong>Customer data</strong> stays in customer boundary</div>
            </div>
            <div class="data-item">
              <div class="data-check">
                <svg viewBox="0 0 24 24"><path class="icon-stroke" d="M5 12l5 5L20 7"/></svg>
              </div>
              <div class="data-text"><strong>Customer-owned</strong> generated artifacts</div>
            </div>
            <div class="data-item">
              <div class="data-check">
                <svg viewBox="0 0 24 24"><path class="icon-stroke" d="M5 12l5 5L20 7"/></svg>
              </div>
              <div class="data-text"><strong>BYO approved LLM</strong> via Model Context Protocol</div>
            </div>
            <div class="data-item">
              <div class="data-check">
                <svg viewBox="0 0 24 24"><path class="icon-stroke" d="M5 12l5 5L20 7"/></svg>
              </div>
              <div class="data-text"><strong>No model training</strong> on customer data unless required</div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="caption-zone">
      <div class="caption" data-scene="4"></div>
    </div>
  </div>

  <div class="scene" id="scene5">
    <div class="scene-header"></div>
    <div class="scene-content">
      <img class="close-logo" src="data:image/jpeg;base64,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" alt="Alpha Omega">
      <div class="close-tag">Continuum Design / Business Model</div>
      <div class="close-line">
        <span>Predictable subscription pricing.</span>
        <span class="close-divider"></span>
        <span>Multiple acquisition paths.</span>
        <br>
        <span class="accent">Deploys inside your accreditation boundary.</span>
      </div>
    </div>
    <div class="caption-zone"></div>
  </div>

  <div class="progress-track"><div class="progress-fill" id="progress"></div></div>
</div>

<script>
(function(){
  const timeline = [
    {scene:'scene1', start:0,     end:3000,  caption:''},
    {scene:'scene2', start:3000,  end:5500,  caption:'Continuum Design is offered as a subscription licensed by user…'},
    {scene:'scene2', start:5500,  end:9500,  caption:'…with tiered pricing for program offices, mission squads, and enterprise-wide deployments.'},
    {scene:'scene2', start:9500,  end:12500, caption:'Pricing scales with adoption, not consumption — predictable for federal appropriation cycles.'},
    {scene:'scene3', start:12500, end:16500, caption:'We deliver procurement-ready paths: customer-hosted in your GovCloud or on-premises enclave…'},
    {scene:'scene3', start:16500, end:22000, caption:'…or bundled as a Continuum AF engagement combining the platform with Alpha Omega\'s design and DevSecOps services.'},
    {scene:'scene4', start:22000, end:27500, caption:'Government data, prompts, and generated artifacts remain inside the customer accreditation boundary.'},
    {scene:'scene4', start:27500, end:30000, caption:''},
    {scene:'scene5', start:30000, end:35000, caption:''}
  ];
  const totalDuration = 35000;
  const sceneIds = ['scene1','scene2','scene3','scene4','scene5'];
  const progressEl = document.getElementById('progress');
  const replayBtn = document.getElementById('replay');

  let startTime = null;
  let rafId = null;
  let currentScene = null;

  function setActiveScene(id){
    if(currentScene === id) return;
    currentScene = id;
    sceneIds.forEach(s=>{
      const el = document.getElementById(s);
      if(s === id) el.classList.add('active');
      else el.classList.remove('active');
    });
  }

  function setCaption(sceneId, text){
    document.querySelectorAll('.caption').forEach(c=>{
      if(c.dataset.scene === sceneId.replace('scene','')){
        if(text){
          if(c.textContent !== text) c.textContent = text;
          c.classList.add('visible');
        } else {
          c.classList.remove('visible');
        }
      } else {
        c.classList.remove('visible');
      }
    });
  }

  function tick(ts){
    if(!startTime) startTime = ts;
    const elapsed = ts - startTime;
    progressEl.style.width = Math.min(100, (elapsed / totalDuration) * 100) + '%';

    const current = timeline.find(t => elapsed >= t.start && elapsed < t.end);
    if(current){
      setActiveScene(current.scene);
      setCaption(current.scene, current.caption);
    }

    if(elapsed < totalDuration){
      rafId = requestAnimationFrame(tick);
    } else {
      setActiveScene('scene5');
      setCaption('scene5','');
      replayBtn.classList.add('show');
    }
  }

  function start(){
    replayBtn.classList.remove('show');
    document.querySelectorAll('.caption').forEach(c=>{c.classList.remove('visible');c.textContent='';});
    startTime = null;
    if(rafId) cancelAnimationFrame(rafId);
    progressEl.style.width = '0%';
    sceneIds.forEach(s=>document.getElementById(s).classList.remove('active'));
    currentScene = null;
    setTimeout(()=>{
      setActiveScene('scene1');
      rafId = requestAnimationFrame(tick);
    }, 80);
  }

  replayBtn.addEventListener('click', start);
  window.addEventListener('load', () => setTimeout(start, 300));

  document.addEventListener('keydown', e=>{
    if(e.key === 'f' || e.key === 'F'){
      if(!document.fullscreenElement){ document.documentElement.requestFullscreen(); }
      else { document.exitFullscreen(); }
    } else if(e.key === 'r' || e.key === 'R'){
      start();
    }
  });
})();
</script>
</body>
</html>

## Architecture and code map

**Architecture diagram.** The diagram shows the single static page: a timer-driven player that steps through five scenes and their captions, styled by inline CSS and one web-font stylesheet.
- Source: [`docs/architecture/architecture.json`](docs/architecture/architecture.json) (an [archify](https://github.com/tt-a1i/archify) spec).
- Rendered view: the `architecture` workflow builds it on every change and uploads `architecture-diagram` (open the latest run under Actions → architecture, download the artifact, open `architecture.html`).
- Locally: `node <archify>/bin/archify.mjs deliver architecture docs/architecture/architecture.json docs/architecture/architecture.html --quality showcase --open` (or ask Claude Code to use the archify skill). The HTML is gitignored.

**Knowledge graph (graphify).** `graphify-out/GRAPH_REPORT.md` (key concepts and connections) and `graphify-out/graph.html` (clickable graph) are committed ([report](graphify-out/GRAPH_REPORT.md), [graph](graphify-out/graph.html)); `graph.json` is gitignored and rebuilt with [`graphify`](https://github.com/safishamsi/graphify). Rebuild with `graphify update . && graphify cluster-only . --no-label` (code only, no LLM, nothing leaves the machine). The Graphify Labs GitHub App also runs on every push and PR in the org.
