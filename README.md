<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Shaharia Sifat — DevSecOps Engineer</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600;700&display=swap');

  :root {
    --neon: #4AFCB0;
    --blue: #58A6FF;
    --orange: #FF9900;
    --purple: #A78BFA;
    --red: #FF5555;
    --bg: #0D1117;
    --bg2: #161B22;
    --bg3: #1E2A3A;
    --border: #30363D;
    --text: #E6EDF3;
    --muted: #8B949E;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding: 32px 16px;
  }

  .wrap {
    width: 100%;
    max-width: 780px;
  }

  .terminal {
    background: var(--bg);
    border: 1px solid var(--border);
    border-radius: 14px;
    overflow: hidden;
    box-shadow: 0 24px 80px rgba(0,0,0,0.6);
  }

  /* Title bar */
  .tbar {
    background: var(--bg2);
    padding: 12px 18px;
    display: flex;
    align-items: center;
    gap: 8px;
    border-bottom: 1px solid var(--border);
    position: sticky;
    top: 0;
    z-index: 10;
  }
  .tdot { width: 13px; height: 13px; border-radius: 50%; }
  .tlabel { font-size: 12px; color: var(--muted); margin-left: 10px; }
  .tlabel span { color: var(--neon); }

  /* Hero */
  .hero {
    padding: 32px 28px 24px;
    text-align: center;
    border-bottom: 1px solid var(--border);
    background: linear-gradient(180deg, #0D1117 0%, #0D1117 100%);
  }
  .hero-name {
    font-size: 28px;
    font-weight: 700;
    color: var(--neon);
    letter-spacing: .02em;
    min-height: 36px;
  }
  .hero-role {
    margin-top: 8px;
    font-size: 13px;
    color: var(--muted);
  }
  .hero-role span { color: var(--blue); }
  .hero-badges {
    display: flex;
    justify-content: center;
    gap: 10px;
    flex-wrap: wrap;
    margin-top: 16px;
  }
  .badge {
    display: flex;
    align-items: center;
    gap: 6px;
    padding: 6px 14px;
    border-radius: 8px;
    border: 1px solid var(--border);
    font-size: 12px;
    text-decoration: none;
    color: var(--text);
    background: var(--bg2);
    transition: border-color .2s, transform .15s, background .2s;
  }
  .badge:hover { transform: translateY(-2px); background: #1C2430; }
  .badge.li:hover { border-color: #0A66C2; }
  .badge.gh:hover { border-color: var(--blue); }
  .badge.mail:hover { border-color: var(--neon); }
  .badge-dot { width: 8px; height: 8px; border-radius: 50%; }

  .prompt-line {
    margin-top: 16px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    font-size: 12px;
    color: var(--muted);
  }
  .prompt-line .ps { color: var(--neon); }
  .blinking { animation: blink 1s step-end infinite; }
  @keyframes blink { 0%,100%{opacity:1;} 50%{opacity:0;} }

  /* Tabs */
  .tabs {
    display: flex;
    border-bottom: 1px solid var(--border);
    background: var(--bg2);
    overflow-x: auto;
    scrollbar-width: none;
  }
  .tabs::-webkit-scrollbar { display: none; }
  .tab {
    padding: 11px 20px;
    font-size: 12px;
    cursor: pointer;
    color: var(--muted);
    border-bottom: 2px solid transparent;
    white-space: nowrap;
    transition: color .2s, border-color .2s;
    user-select: none;
  }
  .tab:hover { color: var(--text); }
  .tab.active { color: var(--neon); border-bottom-color: var(--neon); }

  /* Panels */
  .panel { display: none; padding: 22px 26px; }
  .panel.active { display: block; }

  .section-title {
    font-size: 10px;
    color: var(--muted);
    letter-spacing: .12em;
    text-transform: uppercase;
    margin-bottom: 12px;
    margin-top: 20px;
  }
  .section-title:first-child { margin-top: 0; }

  /* Skills */
  .skill-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
    gap: 10px;
  }
  .skill {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 9px;
    padding: 11px 13px;
    transition: border-color .2s, transform .15s;
    cursor: default;
  }
  .skill:hover { transform: translateY(-2px); }
  .skill-name { font-size: 12px; font-weight: 600; }
  .skill-level { margin-top: 7px; height: 3px; background: #21262D; border-radius: 2px; overflow: hidden; }
  .skill-bar { height: 100%; border-radius: 2px; transition: width 1s ease; }
  .skill-pct { font-size: 10px; color: var(--muted); margin-top: 4px; }

  /* Projects */
  .proj-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  .proj {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 11px;
    padding: 16px;
    transition: border-color .2s, transform .15s;
    cursor: default;
  }
  .proj:hover { transform: translateY(-3px); }
  .proj-name { font-size: 13px; font-weight: 700; display: flex; align-items: center; gap: 7px; }
  .proj-desc { font-size: 11px; color: var(--muted); margin-top: 7px; line-height: 1.6; }
  .proj-tags { display: flex; flex-wrap: wrap; gap: 5px; margin-top: 12px; }
  .tag { font-size: 10px; padding: 2px 8px; border-radius: 5px; background: #21262D; color: var(--muted); }

  /* Pipeline */
  .pipeline { display: flex; flex-direction: column; gap: 10px; }
  .pipe-stage {
    display: flex;
    align-items: center;
    gap: 12px;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 9px;
    padding: 13px 16px;
    cursor: pointer;
    transition: border-color .2s, background .2s;
  }
  .pipe-stage:hover { border-color: var(--blue); background: #1C2430; }
  .pipe-icon { font-size: 20px; width: 28px; text-align: center; }
  .pipe-info { flex: 1; }
  .pipe-name { font-size: 13px; font-weight: 600; }
  .pipe-hint { font-size: 10px; color: var(--muted); margin-top: 2px; }
  .pipe-status {
    font-size: 10px;
    font-weight: 700;
    padding: 3px 10px;
    border-radius: 5px;
    white-space: nowrap;
  }
  .s-pass { background: #0E4429; color: var(--neon); }
  .s-scan { background: #1C1000; color: var(--orange); }
  .s-gate { background: #1C0000; color: var(--red); }

  .pipe-detail {
    display: none;
    margin-top: 12px;
    background: #0D1117;
    border: 1px solid var(--border);
    border-radius: 9px;
    padding: 16px;
    font-size: 12px;
    color: var(--muted);
    line-height: 1.75;
  }

  /* Certs */
  .cert-row { display: flex; flex-direction: column; gap: 10px; }
  .cert {
    display: flex;
    align-items: center;
    gap: 14px;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 9px;
    padding: 13px 16px;
  }
  .cert-icon { font-size: 24px; }
  .cert-body { flex: 1; }
  .cert-name { font-size: 12px; font-weight: 700; }
  .cert-sub { font-size: 10px; color: var(--muted); margin-top: 2px; }
  .cert-prog { height: 3px; background: #21262D; border-radius: 2px; margin-top: 8px; overflow: hidden; }
  .cert-fill { height: 100%; border-radius: 2px; background: var(--orange); transition: width 1s ease; }
  .cert-pct { font-size: 11px; color: var(--orange); font-weight: 700; white-space: nowrap; }

  /* Threat */
  .stat-row {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 10px;
    margin-bottom: 16px;
  }
  .stat {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 9px;
    padding: 14px;
    text-align: center;
  }
  .stat-val { font-size: 26px; font-weight: 700; }
  .stat-lbl { font-size: 10px; color: var(--muted); margin-top: 4px; }
  .threat-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
  .threat {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 9px;
    padding: 14px;
  }
  .threat-title { font-size: 12px; font-weight: 700; display: flex; align-items: center; gap: 6px; }
  .threat-items { margin-top: 10px; display: flex; flex-direction: column; gap: 5px; }
  .threat-item { font-size: 11px; color: var(--muted); display: flex; align-items: center; gap: 7px; }
  .ti-dot { width: 5px; height: 5px; border-radius: 50%; flex-shrink: 0; }

  /* Connect */
  .connect-section { display: flex; flex-direction: column; gap: 10px; }
  .connect-card {
    display: flex;
    align-items: center;
    gap: 16px;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 9px;
    padding: 16px;
    cursor: pointer;
    text-decoration: none;
    color: var(--text);
    transition: border-color .2s, transform .15s;
  }
  .connect-card:hover { transform: translateX(5px); }
  .cc-icon { font-size: 28px; width: 42px; text-align: center; }
  .cc-label { font-size: 13px; font-weight: 700; }
  .cc-sub { font-size: 11px; color: var(--muted); margin-top: 2px; }
  .cc-arrow { margin-left: auto; font-size: 18px; color: var(--muted); }

  /* Scrollbar */
  ::-webkit-scrollbar { width: 6px; height: 6px; }
  ::-webkit-scrollbar-track { background: transparent; }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 3px; }

  /* Responsive */
  @media (max-width: 560px) {
    .proj-grid { grid-template-columns: 1fr; }
    .stat-row { grid-template-columns: 1fr 1fr; }
    .threat-grid { grid-template-columns: 1fr; }
    .hero-name { font-size: 22px; }
    .panel { padding: 16px; }
  }
</style>
</head>
<body>
<div class="wrap">
<div class="terminal">

  <!-- Title Bar -->
  <div class="tbar">
    <div class="tdot" style="background:#FF5F56"></div>
    <div class="tdot" style="background:#FFBD2E"></div>
    <div class="tdot" style="background:#27C93F"></div>
    <span class="tlabel">sifat@cloudly ~ <span>devsecops-profile</span></span>
  </div>

  <!-- Hero -->
  <div class="hero">
    <div class="hero-name" id="typed-name">&nbsp;</div>
    <div class="hero-role">Senior <span>DevSecOps</span> Engineer · <span>Cloudly DevOps Team</span></div>
    <div class="hero-badges">
      <a class="badge li" href="https://www.linkedin.com/in/shaharia-sifat-9aaab9180/" target="_blank">
        <div class="badge-dot" style="background:#0A66C2"></div>LinkedIn
      </a>
      <a class="badge gh" href="https://github.com/0sifat" target="_blank">
        <div class="badge-dot" style="background:#58A6FF"></div>GitHub / 0sifat
      </a>
      <a class="badge mail" href="mailto:sifat@cloudly.io">
        <div class="badge-dot" style="background:#4AFCB0"></div>sifat@cloudly.io
      </a>
    </div>
    <div class="prompt-line">
      <span class="ps">❯</span>
      <span id="cmd-text" style="font-size:11px;"></span>
      <span class="blinking">▋</span>
    </div>
  </div>

  <!-- Tabs -->
  <div class="tabs" id="tabs">
    <div class="tab active" data-tab="skills">skills.yaml</div>
    <div class="tab" data-tab="projects">projects/</div>
    <div class="tab" data-tab="pipeline">pipeline.sec</div>
    <div class="tab" data-tab="certs">certs.json</div>
    <div class="tab" data-tab="threat">threat.map</div>
    <div class="tab" data-tab="connect">contact.sh</div>
  </div>

  <!-- SKILLS -->
  <div class="panel active" id="panel-skills">
    <div class="section-title">cloud &amp; infrastructure</div>
    <div class="skill-grid" id="sg1"></div>
    <div class="section-title">security &amp; observability</div>
    <div class="skill-grid" id="sg2"></div>
    <div class="section-title">automation &amp; iac</div>
    <div class="skill-grid" id="sg3"></div>
  </div>

  <!-- PROJECTS -->
  <div class="panel" id="panel-projects">
    <div class="proj-grid" id="proj-grid"></div>
  </div>

  <!-- PIPELINE -->
  <div class="panel" id="panel-pipeline">
    <div style="font-size:11px;color:var(--muted);margin-bottom:14px;">→ click any stage to inspect its security controls</div>
    <div class="pipeline" id="pipeline"></div>
    <div class="pipe-detail" id="pipe-detail"></div>
  </div>

  <!-- CERTS -->
  <div class="panel" id="panel-certs">
    <div style="font-size:11px;color:var(--muted);margin-bottom:14px;">active certification tracks</div>
    <div class="cert-row" id="cert-row"></div>
  </div>

  <!-- THREAT MAP -->
  <div class="panel" id="panel-threat">
    <div class="stat-row">
      <div class="stat"><div class="stat-val" style="color:var(--neon)">72</div><div class="stat-lbl">servers monitored</div></div>
      <div class="stat"><div class="stat-val" style="color:var(--orange)">4</div><div class="stat-lbl">active SIEM rulesets</div></div>
      <div class="stat"><div class="stat-val" style="color:var(--red)">0</div><div class="stat-lbl">critical open findings</div></div>
    </div>
    <div class="threat-grid" id="threat-grid"></div>
  </div>

  <!-- CONNECT -->
  <div class="panel" id="panel-connect">
    <div style="font-size:11px;color:var(--muted);margin-bottom:14px;">open to consulting, architecture reviews, and senior engineering roles</div>
    <div class="connect-section" id="connect-section"></div>
  </div>

</div>
</div>

<script>
/* ── DATA ── */
const skills1 = [
  {n:'Kubernetes',   p:90, c:'#326CE5'},
  {n:'AWS EKS',      p:88, c:'#FF9900'},
  {n:'EC2 / VPC',    p:92, c:'#FF9900'},
  {n:'ALB / Route53',p:85, c:'#FF9900'},
  {n:'S3 / IAM',     p:90, c:'#FF9900'},
  {n:'RDS / Aurora', p:82, c:'#FF9900'},
];
const skills2 = [
  {n:'Wazuh SIEM',   p:88, c:'#4AFCB0'},
  {n:'Prometheus',   p:87, c:'#E6522C'},
  {n:'Grafana',      p:90, c:'#F5A800'},
  {n:'Loki/Promtail',p:85, c:'#F5A800'},
  {n:'CloudGuardian',p:80, c:'#4AFCB0'},
  {n:'fail2ban',     p:78, c:'#FF5555'},
];
const skills3 = [
  {n:'Terraform',    p:86, c:'#7B42BC'},
  {n:'Helm',         p:84, c:'#4A90D9'},
  {n:'ArgoCD',       p:80, c:'#EF7B4D'},
  {n:'Docker',       p:94, c:'#2496ED'},
  {n:'GitHub Actions',p:85,c:'#58A6FF'},
  {n:'Bash / Python',p:88, c:'#4EAA25'},
];

const projects = [
  {icon:'🛡️', name:'CloudGuardian Stack',      color:'#F5A800',
   desc:'Full observability — Prometheus · Grafana · Loki · Wazuh on AWS EKS with Go-based Clofix proxy.',
   tags:['Kubernetes','Helm','AWS','Wazuh','Prometheus','Grafana']},
  {icon:'📡', name:'Multi-Server Log Pipeline', color:'#4AFCB0',
   desc:'Promtail log shipping across 72 production servers via jump host automation with consistent label patterns.',
   tags:['Loki','Promtail','Bash','Linux','jump-host']},
  {icon:'🏗️', name:'Terraform K8s Cluster',    color:'#7B42BC',
   desc:'Multi-node Kubernetes cluster: 1 Master (m7i-flex.large) + 2 Workers (t3.micro) provisioned with Terraform IaC.',
   tags:['Terraform','EC2','K8s','gp3','SGs']},
  {icon:'🔐', name:'Wazuh SIEM on AWS',         color:'#58A6FF',
   desc:'Production SIEM on EC2 — full agent fleet, dashboard recovery, 8-issue root-cause chain resolved.',
   tags:['Wazuh','EC2','RHEL','fail2ban','YAML']},
];

const pipeStages = [
  {icon:'📝', name:'Code Commit',       status:'pass', label:'PASSED',
   desc:'Git push triggers pipeline. Pre-commit hooks: gitleaks secret scanning, linting, commit message validation. Branch protection enforced — no direct push to main. All commits signed.'},
  {icon:'🔍', name:'SAST / Secret Scan',status:'pass', label:'CLEAN',
   desc:'Static analysis with Semgrep + Trivy filesystem scan. Detects hardcoded credentials, insecure code patterns, and vulnerable dependencies before any build starts. Zero-tolerance on HIGH/CRITICAL findings.'},
  {icon:'🐳', name:'Container Build',   status:'pass', label:'BUILT',
   desc:'Docker multi-stage build via BuildKit. Minimal attack surface base images pinned by digest. No privileged flags. Build artifacts signed with cosign. SBOM generated per image.'},
  {icon:'🧪', name:'Image Scan (Trivy)',status:'scan', label:'SCANNING',
   desc:'Trivy scans final image for CVEs, misconfigurations, and secret leakage. Results pushed to Defect Dojo. Deployment blocked automatically if CRITICAL CVEs have available fixes.'},
  {icon:'🚨', name:'Security Gate',     status:'gate', label:'GATE',
   desc:'Policy enforcement via OPA/Conftest: no root containers, resource limits required, no latest tags allowed, network policies must be present. Must pass 100% before deploy proceeds — no exceptions.'},
  {icon:'🚀', name:'Deploy to EKS',     status:'pass', label:'DEPLOYED',
   desc:'ArgoCD syncs Helm chart from Git (GitOps). Kyverno admission controller validates manifests at runtime. Rolling update with readiness/liveness checks. Wazuh agent auto-registered on pod startup.'},
  {icon:'📊', name:'Runtime Observability',status:'pass',label:'ACTIVE',
   desc:'Prometheus scrapes metrics. Loki/Promtail ships logs from all 72 servers. Grafana dashboards live. Wazuh SIEM monitors for anomalies, brute-force SSH, and lateral movement across the entire fleet.'},
];

const certs = [
  {icon:'☁️', name:'AWS SAA-C03',           sub:'Solutions Architect Associate', prog:72,  meta:'In progress — Stephane Maarek + Tutorials Dojo'},
  {icon:'⚓',  name:'CKA',                   sub:'Certified Kubernetes Administrator', prog:55, meta:'Hands-on via KodeKloud — active labs, Days 54+'},
  {icon:'🔐', name:'AWS Security Specialty', sub:'Target — post SAA-C03',         prog:15,  meta:'Planned Q4 2025'},
  {icon:'🛡️', name:'CompTIA Security+',     sub:'DevSecOps foundation track',    prog:30,  meta:'Self-study in progress'},
];

const threats = [
  {title:'🔴 Incident Response',   col:'#FF5555',
   items:['Wazuh SIEM on 72-server fleet','Brute-force SSH detection & blocking','Temenos T24 OOM — r5a.2xlarge resize','fail2ban + swap tuning applied']},
  {title:'🛡️ Hardening Applied',  col:'#4AFCB0',
   items:['SSL/TLS cert automation (Certbot)','ModSecurity WAF — duplicate module fix','SSH key-only auth enforced fleet-wide','IAM least-privilege review complete']},
  {title:'📋 Compliance Controls', col:'#58A6FF',
   items:['AWS Secrets Manager — zero plaintext','EBS volumes encrypted at rest','VPC flow logs retained + monitored','CloudWatch audit trail active']},
  {title:'⚡ Proactive Monitoring', col:'#F5A800',
   items:['72 servers via Promtail/Loki','Prometheus alerting rules configured','Grafana dashboards for all stacks','Weekly cost anomaly scanning ($12K/mo)']},
];

const connects = [
  {icon:'💼', label:'LinkedIn',        sub:'Shaharia Sifat — Senior DevSecOps Engineer', href:'https://www.linkedin.com/in/shaharia-sifat-9aaab9180/', col:'#0A66C2'},
  {icon:'🐙', label:'GitHub / 0sifat', sub:'IaC, observability stacks, K8s labs, 100DaysOfDevOps', href:'https://github.com/0sifat', col:'#58A6FF'},
  {icon:'📧', label:'sifat@cloudly.io',sub:'Open to consulting, architecture reviews, senior roles', href:'mailto:sifat@cloudly.io', col:'#4AFCB0'},
];

/* ── RENDER ── */
function renderSkills(id, data) {
  document.getElementById(id).innerHTML = data.map(s => `
    <div class="skill" title="${s.n} — ${s.p}%">
      <div class="skill-name" style="color:${s.c}">${s.n}</div>
      <div class="skill-level"><div class="skill-bar" style="width:0;background:${s.c}" data-w="${s.p}%"></div></div>
      <div class="skill-pct">${s.p}%</div>
    </div>`).join('');
}
renderSkills('sg1', skills1);
renderSkills('sg2', skills2);
renderSkills('sg3', skills3);

document.getElementById('proj-grid').innerHTML = projects.map(p => `
  <div class="proj" style="border-top:2px solid ${p.color}">
    <div class="proj-name"><span>${p.icon}</span><span style="color:${p.color}">${p.name}</span></div>
    <div class="proj-desc">${p.desc}</div>
    <div class="proj-tags">${p.tags.map(t=>`<span class="tag">${t}</span>`).join('')}</div>
  </div>`).join('');

const ppl = document.getElementById('pipeline');
pipeStages.forEach(s => {
  const sc = s.status === 'pass' ? 's-pass' : s.status === 'scan' ? 's-scan' : 's-gate';
  const el = document.createElement('div');
  el.className = 'pipe-stage';
  el.innerHTML = `
    <div class="pipe-icon">${s.icon}</div>
    <div class="pipe-info">
      <div class="pipe-name">${s.name}</div>
      <div class="pipe-hint">click to inspect security controls</div>
    </div>
    <div class="pipe-status ${sc}">${s.label}</div>`;
  el.addEventListener('click', () => {
    const d = document.getElementById('pipe-detail');
    d.style.display = 'block';
    d.innerHTML = `<strong style="color:var(--text)">${s.icon} ${s.name}</strong><br/><br/>${s.desc}`;
    document.querySelectorAll('.pipe-stage').forEach(x => x.style.borderColor = '');
    el.style.borderColor = 'var(--neon)';
    d.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
  });
  ppl.appendChild(el);
});

document.getElementById('cert-row').innerHTML = certs.map(c => `
  <div class="cert">
    <div class="cert-icon">${c.icon}</div>
    <div class="cert-body">
      <div class="cert-name">${c.name} <span style="color:var(--muted);font-weight:400;font-size:10px">— ${c.sub}</span></div>
      <div class="cert-sub">${c.meta}</div>
      <div class="cert-prog"><div class="cert-fill" style="width:0" data-w="${c.prog}%"></div></div>
    </div>
    <div class="cert-pct">${c.prog}%</div>
  </div>`).join('');

document.getElementById('threat-grid').innerHTML = threats.map(t => `
  <div class="threat" style="border-top:2px solid ${t.col}">
    <div class="threat-title" style="color:${t.col}">${t.title}</div>
    <div class="threat-items">${t.items.map(i => `
      <div class="threat-item"><div class="ti-dot" style="background:${t.col}"></div>${i}</div>`).join('')}
    </div>
  </div>`).join('');

document.getElementById('connect-section').innerHTML = connects.map(c => `
  <a class="connect-card" href="${c.href}" target="_blank" style="border-left:3px solid ${c.col}">
    <div class="cc-icon">${c.icon}</div>
    <div>
      <div class="cc-label" style="color:${c.col}">${c.label}</div>
      <div class="cc-sub">${c.sub}</div>
    </div>
    <div class="cc-arrow">→</div>
  </a>`).join('');

/* ── TABS ── */
document.querySelectorAll('.tab').forEach(t => {
  t.addEventListener('click', () => {
    document.querySelectorAll('.tab').forEach(x => x.classList.remove('active'));
    document.querySelectorAll('.panel').forEach(x => x.classList.remove('active'));
    t.classList.add('active');
    document.getElementById('panel-' + t.dataset.tab).classList.add('active');
    animateBars();
  });
});

/* ── ANIMATE BARS ── */
function animateBars() {
  setTimeout(() => {
    document.querySelectorAll('.skill-bar').forEach(b => b.style.width = b.dataset.w);
    document.querySelectorAll('.cert-fill').forEach(b => b.style.width = b.dataset.w);
  }, 80);
}

/* ── TYPING NAME ── */
const nameEl = document.getElementById('typed-name');
const name = 'Shaharia Sifat';
let ni = 0;
(function typeName() {
  if (ni <= name.length) {
    nameEl.textContent = name.slice(0, ni) || '\u00a0';
    ni++;
    setTimeout(typeName, 65);
  }
})();

/* ── CYCLING COMMANDS ── */
const cmds = [
  'cat /etc/profile.d/devsecops',
  'kubectl get nodes --all-namespaces',
  'wazuh-manager status',
  'terraform plan -out=prod.tfplan',
  'helm list -A',
  'docker ps --format "{{.Names}}"',
  'trivy image --severity CRITICAL myapp:latest',
  'kubectl top nodes',
  'aws sts get-caller-identity',
];
let ci = 0, chi = 0;
const cmdEl = document.getElementById('cmd-text');
(function typeCmd() {
  if (chi < cmds[ci].length) {
    cmdEl.textContent = cmds[ci].slice(0, chi + 1);
    chi++;
    setTimeout(typeCmd, 45);
  } else {
    setTimeout(() => {
      chi = 0;
      ci = (ci + 1) % cmds.length;
      cmdEl.textContent = '';
      setTimeout(typeCmd, 300);
    }, 2200);
  }
})();

/* ── INIT BARS ── */
animateBars();
</script>
</body>
</html>
