[index.html](https://github.com/user-attachments/files/28574190/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Agent Bio Update Portal — 2 Costa Rica Real Estate</title>
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js"></script>
<script>emailjs.init('-XnAREuDdnot32OAK');</script>
<style>
  :root {
    --forest: #0d505a;
    --forest-mid: #1e4d58;
    --forest-light: #1e4d58;
    --green: #7ab942;
    --green-light: #93cc57;
    --slate: #6f9096;
    --cream: #f6f8f8;
    --warm-white: #ffffff;
    --text-dark: #000000;
    --text-mid: #3a3a3a;
    --text-light: #838383;
    --border: #dde4e5;
    --shadow: rgba(13,80,90,0.10);
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Montserrat', sans-serif;
    background: var(--cream);
    color: var(--text-dark);
    min-height: 100vh;
  }

  /* ─── TOP BAR ─── */
  .topbar {
    background: var(--forest);
    padding: 14px 32px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .topbar-brand {
    display: flex;
    align-items: center;
    gap: 12px;
    color: white;
  }
  .topbar-brand .leaf {
    width: 32px; height: 32px;
    background: var(--green);
    border-radius: 50%;
    flex-shrink: 0;
  }
  .topbar-brand span {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.95rem;
    font-weight: 600;
    letter-spacing: 0.03em;
    line-height: 1.2;
  }
  .topbar-brand small { display: block; font-family: 'Montserrat', sans-serif; font-size: 0.68rem; opacity: 0.65; font-weight: 400; letter-spacing: 0.05em; }
  .topbar-right { color: var(--slate); font-size: 0.8rem; font-weight: 500; }

  /* ─── SCREEN CONTAINER ─── */
  .screen { display: none; min-height: calc(100vh - 66px); }
  .screen.active { display: flex; flex-direction: column; }

  /* ─── LOGIN SCREEN ─── */
  #screen-login {
    align-items: center;
    justify-content: center;
    padding: 40px 20px;
    background: linear-gradient(150deg, var(--forest) 0%, var(--forest-mid) 60%, #0a3840 100%);
  }
  .login-card {
    background: var(--warm-white);
    border-radius: 12px;
    padding: 48px 44px;
    width: 100%;
    max-width: 420px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.2);
  }
  .login-card h1 {
    font-family: 'Montserrat', sans-serif;
    font-size: 1.6rem;
    font-weight: 700;
    color: var(--forest);
    margin-bottom: 6px;
    letter-spacing: -0.01em;
  }
  .login-card p { color: var(--text-light); font-size: 0.85rem; margin-bottom: 32px; }
  .login-card label { display: block; font-size: 0.72rem; font-weight: 600; color: var(--forest); text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: 7px; }
  .login-card input[type=email], .login-card input[type=password] {
    width: 100%; padding: 12px 14px;
    border: 1.5px solid var(--border);
    border-radius: 6px;
    font-size: 0.9rem;
    font-family: 'Montserrat', sans-serif;
    background: var(--cream);
    color: var(--text-dark);
    margin-bottom: 20px;
    transition: border-color 0.2s;
  }
  .login-card input:focus { outline: none; border-color: var(--forest-mid); }
  .btn-primary {
    width: 100%; padding: 13px;
    background: var(--green);
    color: white;
    border: none;
    border-radius: 6px;
    font-size: 0.88rem;
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    cursor: pointer;
    transition: background 0.2s, transform 0.1s;
    letter-spacing: 0.05em;
    text-transform: uppercase;
  }
  .btn-primary:hover { background: var(--green-light); }
  .btn-primary:active { transform: scale(0.99); }
  .btn-primary:disabled { background: #aaa; cursor: not-allowed; }
  .login-error { color: #c0392b; font-size: 0.85rem; margin-top: 12px; text-align: center; display: none; }

  /* ─── MAIN EDITOR SCREEN ─── */
  #screen-editor { padding: 0; background: var(--cream); }

  .editor-layout {
    display: grid;
    grid-template-columns: 320px 1fr;
    min-height: calc(100vh - 66px);
  }

  /* LEFT PANEL */
  .left-panel {
    background: var(--forest);
    color: var(--cream);
    padding: 36px 28px;
    display: flex;
    flex-direction: column;
    gap: 28px;
    position: sticky;
    top: 0;
    height: calc(100vh - 66px);
    overflow-y: auto;
  }
  .agent-profile {
    text-align: center;
    padding-bottom: 24px;
    border-bottom: 1px solid rgba(255,255,255,0.15);
  }
  .agent-avatar {
    width: 96px; height: 96px;
    border-radius: 50%;
    object-fit: cover;
    border: 3px solid var(--green);
    margin: 0 auto 14px;
    display: block;
    background: var(--forest-mid);
  }
  .agent-avatar-placeholder {
    width: 96px; height: 96px;
    border-radius: 50%;
    background: var(--forest-mid);
    border: 3px solid var(--green);
    margin: 0 auto 14px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2rem;
    color: var(--green);
  }
  .agent-name { font-family: 'Montserrat', sans-serif; font-size: 1.05rem; font-weight: 700; margin-bottom: 4px; letter-spacing: -0.01em; }
  .agent-title { font-size: 0.75rem; opacity: 0.6; font-weight: 400; letter-spacing: 0.04em; text-transform: uppercase; }

  .instructions-block h3 {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.72rem;
    font-weight: 700;
    color: var(--slate);
    margin-bottom: 14px;
    text-transform: uppercase;
    letter-spacing: 0.12em;
  }
  .instructions-block ul { list-style: none; display: flex; flex-direction: column; gap: 9px; }
  .instructions-block li {
    font-size: 0.8rem;
    opacity: 0.85;
    padding-left: 14px;
    position: relative;
    line-height: 1.55;
    font-weight: 400;
  }
  .instructions-block li::before {
    content: '';
    position: absolute;
    left: 0;
    top: 7px;
    width: 5px;
    height: 1.5px;
    background: var(--green);
    border-radius: 2px;
  }

  .status-badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 5px 11px;
    border-radius: 4px;
    font-size: 0.7rem;
    font-weight: 600;
    letter-spacing: 0.06em;
    text-transform: uppercase;
  }
  .status-badge.draft { background: rgba(111,144,150,0.2); color: var(--slate); border: 1px solid rgba(111,144,150,0.3); }
  .status-badge.submitted { background: rgba(122,185,66,0.2); color: #7ab942; border: 1px solid rgba(122,185,66,0.35); }
  .status-badge .dot { width: 5px; height: 5px; border-radius: 50%; background: currentColor; }

  .btn-logout {
    background: transparent;
    border: 1px solid rgba(255,255,255,0.2);
    color: var(--cream);
    padding: 8px 16px;
    border-radius: 6px;
    font-size: 0.8rem;
    cursor: pointer;
    font-family: 'DM Sans', sans-serif;
    transition: background 0.2s;
    margin-top: auto;
  }
  .btn-logout:hover { background: rgba(255,255,255,0.1); }

  /* RIGHT PANEL */
  .right-panel {
    padding: 40px 48px;
    display: flex;
    flex-direction: column;
    gap: 32px;
    max-width: 820px;
  }

  .section-header h2 {
    font-family: 'Montserrat', sans-serif;
    font-size: 1.4rem;
    font-weight: 700;
    color: var(--forest);
    margin-bottom: 6px;
    letter-spacing: -0.02em;
  }
  .section-header p { color: var(--text-light); font-size: 0.85rem; }

  .current-bio-box {
    background: white;
    border: 1.5px solid var(--border);
    border-radius: 12px;
    padding: 24px;
  }
  .current-bio-box h4 {
    font-size: 0.75rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: var(--text-light);
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .current-bio-box h4 a { color: var(--forest-light); text-decoration: none; font-size: 0.7rem; }
  .current-bio-box h4 a:hover { text-decoration: underline; }
  .current-bio-text { font-size: 0.88rem; color: var(--text-mid); line-height: 1.7; }
  .bio-loading { color: var(--text-light); font-size: 0.85rem; font-style: italic; }

  .form-section {
    background: white;
    border: 1.5px solid var(--border);
    border-radius: 12px;
    padding: 28px;
    display: flex;
    flex-direction: column;
    gap: 20px;
  }
  .form-section h3 {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.85rem;
    font-weight: 700;
    color: var(--forest);
    padding-bottom: 14px;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    gap: 10px;
    text-transform: uppercase;
    letter-spacing: 0.08em;
  }
  .form-section h3 .icon { font-size: 1rem; }

  .form-group { display: flex; flex-direction: column; gap: 8px; }
  .form-group label {
    font-size: 0.72rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--forest);
  }
  .form-group label span { font-weight: 400; text-transform: none; color: var(--text-light); letter-spacing: 0; }

  textarea {
    width: 100%;
    padding: 13px 15px;
    border: 1.5px solid var(--border);
    border-radius: 6px;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.88rem;
    line-height: 1.7;
    color: var(--text-dark);
    background: var(--cream);
    resize: vertical;
    transition: border-color 0.2s;
  }
  textarea:focus { outline: none; border-color: var(--forest-mid); }
  textarea:disabled { opacity: 0.6; cursor: not-allowed; }

  .char-count { font-size: 0.75rem; color: var(--text-light); text-align: right; }
  .char-count.warn { color: #e67e22; }

  .drive-link-input {
    width: 100%;
    padding: 12px 14px;
    border: 1.5px solid var(--border);
    border-radius: 6px;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.85rem;
    background: var(--cream);
    color: var(--text-dark);
    transition: border-color 0.2s;
  }
  .drive-link-input:focus { outline: none; border-color: var(--forest-mid); }
  .drive-link-input:disabled { opacity: 0.6; cursor: not-allowed; }

  .drive-hint {
    background: rgba(13,80,90,0.04);
    border: 1px solid rgba(13,80,90,0.12);
    border-left: 3px solid var(--green);
    border-radius: 4px;
    padding: 14px 16px;
    font-size: 0.8rem;
    color: var(--text-mid);
    line-height: 1.65;
  }
  .drive-hint strong { color: var(--forest); font-weight: 600; }
  .drive-hint a { color: var(--forest-mid); }

  .drive-warning {
    background: #fff8e1;
    border: 1px solid #f0c040;
    border-left: 3px solid #e6a817;
    border-radius: 4px;
    padding: 12px 16px;
    font-size: 0.8rem;
    color: #7a5800;
    line-height: 1.6;
  }
  .drive-warning strong { color: #5a3f00; }

  .sharing-steps {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin: 16px 0 24px;
    background: var(--cream);
    border-radius: 8px;
    padding: 16px;
  }
  .sharing-step {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    font-size: 0.84rem;
    color: var(--text-mid);
    line-height: 1.5;
  }
  .step-num {
    background: var(--green);
    color: white;
    width: 22px; height: 22px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.7rem;
    font-weight: 700;
    flex-shrink: 0;
    margin-top: 1px;
  }

  .photo-grid-preview {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 8px;
    margin-top: 6px;
  }
  .photo-slot {
    aspect-ratio: 1;
    border: 1.5px dashed var(--border);
    border-radius: 8px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-size: 0.7rem;
    color: var(--text-light);
    gap: 4px;
    background: var(--cream);
  }
  .photo-slot .icon { font-size: 1.4rem; opacity: 0.5; }

  .action-bar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 16px;
    flex-wrap: wrap;
    padding-top: 8px;
  }
  .action-left { display: flex; align-items: center; gap: 12px; }
  .btn-save-draft {
    padding: 10px 20px;
    background: transparent;
    border: 1.5px solid var(--forest);
    color: var(--forest);
    border-radius: 6px;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.78rem;
    font-weight: 700;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    cursor: pointer;
    transition: all 0.2s;
  }
  .btn-save-draft:hover { background: var(--forest); color: white; }
  .btn-save-draft:disabled { opacity: 0.4; cursor: not-allowed; }

  .btn-submit {
    padding: 11px 26px;
    background: var(--green);
    border: none;
    color: white;
    border-radius: 6px;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.82rem;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.2s;
    letter-spacing: 0.06em;
    text-transform: uppercase;
  }
  .btn-submit:hover { background: var(--green-light); }
  .btn-submit:disabled { background: #ccc; color: #888; cursor: not-allowed; }

  .save-indicator { font-size: 0.8rem; color: var(--text-light); display: flex; align-items: center; gap: 6px; }
  .save-indicator.saved { color: #27ae60; }
  .save-indicator.saving { color: var(--gold); }

  /* SUBMITTED STATE */
  .submitted-overlay {
    background: white;
    border: 1.5px solid #c8e6c9;
    border-radius: 8px;
    padding: 36px;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
  }
  .submitted-check { font-size: 3rem; }
  .submitted-overlay h3 { font-family: 'Montserrat', sans-serif; font-weight: 700; color: var(--forest); font-size: 1.2rem; letter-spacing: -0.01em; }
  .submitted-overlay p { color: var(--text-mid); font-size: 0.88rem; max-width: 420px; line-height: 1.6; }

  .modal-backdrop {
    position: fixed; inset: 0;
    background: rgba(0,0,0,0.45);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
    display: none;
  }
  .modal-backdrop.open { display: flex; }
  .modal {
    background: white;
    border-radius: 10px;
    padding: 36px;
    max-width: 460px;
    width: 90%;
    box-shadow: 0 20px 60px rgba(0,0,0,0.18);
  }
  .modal h3 { font-family: 'Montserrat', sans-serif; font-size: 1.1rem; font-weight: 700; color: var(--forest); margin-bottom: 12px; letter-spacing: -0.01em; }
  .modal p { color: var(--text-mid); font-size: 0.88rem; line-height: 1.6; margin-bottom: 24px; }
  .modal-actions { display: flex; gap: 12px; justify-content: flex-end; }
  .btn-cancel {
    padding: 10px 18px;
    background: transparent;
    border: 1.5px solid var(--border);
    border-radius: 6px;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.8rem;
    font-weight: 600;
    cursor: pointer;
    color: var(--text-mid);
  }
  .btn-confirm {
    padding: 10px 22px;
    background: var(--green);
    border: none;
    border-radius: 6px;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.8rem;
    font-weight: 700;
    letter-spacing: 0.04em;
    text-transform: uppercase;
    cursor: pointer;
    color: white;
    transition: background 0.2s;
  }
  .btn-confirm:hover { background: var(--green-light); }
  .btn-confirm:disabled { background: #aaa; cursor: not-allowed; }

  /* TOAST */
  .toast {
    position: fixed;
    bottom: 28px; right: 28px;
    background: var(--forest);
    color: white;
    padding: 13px 20px;
    border-radius: 6px;
    font-size: 0.82rem;
    font-family: 'Montserrat', sans-serif;
    font-weight: 500;
    box-shadow: 0 6px 20px rgba(0,0,0,0.18);
    z-index: 2000;
    transform: translateY(80px);
    opacity: 0;
    transition: all 0.3s ease;
    max-width: 300px;
  }
  .toast.show { transform: translateY(0); opacity: 1; }
  .toast.success { background: var(--forest-mid); }
  .toast.error { background: #c0392b; }

  .progress-bar {
    height: 2px;
    background: var(--border);
    border-radius: 2px;
    overflow: hidden;
    margin-top: 8px;
  }
  .progress-bar-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--forest-mid), var(--green));
    border-radius: 2px;
    transition: width 0.3s;
  }

  /* INTRO MESSAGE */
  .intro-message {
    display: flex;
    gap: 16px;
    background: white;
    border: 1.5px solid var(--border);
    border-left: 4px solid var(--forest);
    border-radius: 8px;
    padding: 22px 20px;
    margin-top: 14px;
  }
  .intro-icon { font-size: 1.6rem; flex-shrink: 0; margin-top: 2px; }
  .intro-text { display: flex; flex-direction: column; gap: 10px; }
  .intro-headline {
    font-size: 0.92rem;
    font-weight: 700;
    color: var(--forest);
    line-height: 1.4;
  }
  .intro-text p {
    font-size: 0.82rem;
    color: var(--text-mid);
    line-height: 1.7;
  }
  .intro-text strong { color: var(--forest); }
  .intro-text em { color: var(--forest-mid); font-style: italic; }

  /* COACHING PROMPTS */
  .coaching-prompts {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }
  .coaching-label {
    font-size: 0.72rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--slate);
  }
  .prompt-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
  }
  .prompt-card {
    display: flex;
    gap: 10px;
    background: var(--cream);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 12px 14px;
    font-size: 0.78rem;
    color: var(--text-mid);
    line-height: 1.55;
    align-items: flex-start;
  }
  .prompt-num {
    font-size: 0.65rem;
    font-weight: 700;
    color: var(--green);
    letter-spacing: 0.05em;
    flex-shrink: 0;
    margin-top: 1px;
  }

  @media (max-width: 600px) {
    .prompt-grid { grid-template-columns: 1fr; }
    .intro-message { flex-direction: column; }
  }

  
    width: 16px; height: 16px;
    border: 2px solid rgba(255,255,255,0.3);
    border-top-color: white;
    border-radius: 50%;
    animation: spin 0.7s linear infinite;
    display: inline-block;
    vertical-align: middle;
  }
  @keyframes spin { to { transform: rotate(360deg); } }

  @media (max-width: 768px) {
    .editor-layout { grid-template-columns: 1fr; }
    .left-panel { position: static; height: auto; }
    .right-panel { padding: 24px 20px; }
    .photo-grid-preview { grid-template-columns: repeat(2, 1fr); }
  }
</style>
</head>
<body>

<!-- TOP BAR -->
<div class="topbar">
  <div class="topbar-brand">
    <div class="leaf"></div>
    <span>2 Costa Rica Real Estate<small>Agent Bio Portal</small></span>
  </div>
  <div class="topbar-right" id="topbar-agent-name"></div>
</div>

<!-- ══════════════════════════════════════ -->
<!-- SCREEN: LOGIN                          -->
<!-- ══════════════════════════════════════ -->
<div id="screen-login" class="screen active">
  <div class="login-card">
    <h1>Welcome Back</h1>
    <p>Sign in to update your biography and lifestyle photos.</p>

    <label for="login-email">Email Address</label>
    <input type="email" id="login-email" placeholder="you@2costaricarealestate.com">

    <label for="login-password">Password</label>
    <input type="password" id="login-password" placeholder="Your password">

    <button class="btn-primary" id="btn-login">Sign In</button>
    <div class="login-error" id="login-error">Incorrect email or password. Please try again.</div>
  </div>
</div>

<!-- ══════════════════════════════════════ -->
<!-- SCREEN: EDITOR                         -->
<!-- ══════════════════════════════════════ -->
<div id="screen-editor" class="screen">
  <div class="editor-layout">

    <!-- LEFT PANEL -->
    <div class="left-panel">
      <div class="agent-profile">
        <div class="agent-avatar-placeholder" id="agent-avatar">👤</div>
        <div class="agent-name" id="agent-name-display">Agent Name</div>
        <div class="agent-title">Real Estate Agent</div>
        <div style="margin-top:12px" id="status-area">
          <span class="status-badge draft"><span class="dot"></span> Draft in progress</span>
        </div>
      </div>

      <div class="instructions-block">
        <h3>Why This Update Matters</h3>
        <p style="font-size:0.78rem;line-height:1.65;opacity:0.85;margin-bottom:10px">Buyers no longer search only on Google. They ask <strong style="color:var(--green)">ChatGPT, Perplexity, and AI assistants</strong> questions like <em>"Who is the best real estate agent in Tamarindo?"</em> — and those systems read your biography word for word to decide who to recommend. A weak bio means you get skipped. A powerful bio means you get cited by name.</p>
      </div>

      <div class="instructions-block">
        <h3>How to Write a Bio That Wins</h3>
        <ul>
          <li>Write in <strong>first person</strong>. Use "I" and "my" — it builds trust instantly.</li>
          <li><strong>Lead with your number:</strong> years of experience, volume closed, or number of clients served. Data stops the scroll.</li>
          <li>Name the <strong>specific areas and neighborhoods</strong> you dominate — Tamarindo, Nosara, Uvita, Escazú. Specificity ranks.</li>
          <li>Describe the <strong>exact type of buyer you serve best</strong> — retirees, investors, families relocating from the US, remote workers seeking beach lifestyle.</li>
          <li>Tell them <strong>what you know that others don't</strong>: permitting, residency programs, HOA red flags, hidden gems in your zone.</li>
          <li>Mention <strong>languages you speak</strong> — English, Spanish, French, German. International buyers filter by this.</li>
          <li>Include one <strong>proof moment</strong>: a client success story, a complex deal you closed, a number that proves your track record.</li>
          <li>End with your <strong>why</strong> — what made you fall in love with Costa Rica and why you chose this career. Authenticity converts.</li>
          <li>Target <strong>250–400 words</strong>. Long enough to rank, short enough to read.</li>
        </ul>
      </div>

      <div class="instructions-block">
        <h3>Power Phrases to Use</h3>
        <ul>
          <li><em>"With over X years specializing in…"</em></li>
          <li><em>"I have helped more than X families and investors…"</em></li>
          <li><em>"My clients close with confidence because I…"</em></li>
          <li><em>"I know this market because I live it every day…"</em></li>
          <li><em>"Whether you are looking for a vacation home, investment property, or your forever home in paradise…"</em></li>
        </ul>
      </div>

      <div class="instructions-block">
        <h3>Lifestyle Photos</h3>
        <ul>
          <li>Upload at least <strong>4 high-quality photos</strong> showing your life in Costa Rica.</li>
          <li>Think: beach, jungle, surfing, local markets, your community, your favorite spot.</li>
          <li>Authentic beats polished — <strong>real moments</strong> connect with buyers more than studio shots.</li>
          <li>Minimum <strong>1200 × 800 px</strong>, JPG or PNG.</li>
          <li>Upload to the shared Drive folder, create a subfolder with your name, then paste the link below.</li>
        </ul>
      </div>

      <button class="btn-logout" id="btn-logout">← Sign Out</button>
    </div>

    <!-- RIGHT PANEL -->
    <div class="right-panel" id="right-panel">

      <div class="section-header">
        <h2>Your Biography Update</h2>
        <div class="intro-message">
          <div class="intro-icon">🌎</div>
          <div class="intro-text">
            <p class="intro-headline">The way buyers find agents has changed — and your bio needs to keep up.</p>
            <p>Today's buyers don't just search Google. They ask <strong>ChatGPT, Perplexity, Gemini, and voice assistants</strong> things like <em>"Who is the best real estate agent in Manuel Antonio?"</em> or <em>"Find me an English-speaking agent who specializes in beachfront properties in Costa Rica."</em></p>
            <p>These AI systems don't show listings — they read agent biographies and <strong>recommend people by name</strong>. If your bio is thin, generic, or outdated, you simply don't exist in those results.</p>
            <p>This update is your opportunity to tell the world exactly who you are, what you've done, and why you are the right agent. <strong>Write it like your next client is an AI deciding between you and a competitor.</strong></p>
          </div>
        </div>
      </div>

      <!-- CURRENT BIO -->
      <div class="current-bio-box">
        <h4>
          YOUR CURRENT BIO
          <a id="agent-profile-link" href="#" target="_blank">View on website ↗</a>
        </h4>
        <div class="current-bio-text" id="current-bio-display">
          <span class="bio-loading">Loading your current biography from the website…</span>
        </div>
      </div>

      <!-- BIO FORM -->
      <div class="form-section" id="bio-form-section">
        <h3><span class="icon">✍️</span> Your New Biography</h3>

        <div class="coaching-prompts">
          <p class="coaching-label">Use these questions to guide your writing:</p>
          <div class="prompt-grid">
            <div class="prompt-card">
              <span class="prompt-num">01</span>
              <span>How many years have you been selling real estate in Costa Rica, and what areas do you know best?</span>
            </div>
            <div class="prompt-card">
              <span class="prompt-num">02</span>
              <span>What type of buyer do you serve best — retirees, investors, families, remote workers?</span>
            </div>
            <div class="prompt-card">
              <span class="prompt-num">03</span>
              <span>Can you share a number? Properties sold, volume closed, satisfied clients, or years of local market knowledge.</span>
            </div>
            <div class="prompt-card">
              <span class="prompt-num">04</span>
              <span>What do you know about Costa Rica real estate that most agents don't? What's your edge?</span>
            </div>
            <div class="prompt-card">
              <span class="prompt-num">05</span>
              <span>What languages do you speak, and what nationalities have you helped buy property here?</span>
            </div>
            <div class="prompt-card">
              <span class="prompt-num">06</span>
              <span>What's your personal story with Costa Rica? Why do you love this market?</span>
            </div>
          </div>
        </div>

        <div class="form-group">
          <label>Write your updated biography <span>(250–400 words recommended)</span></label>
          <textarea id="bio-textarea" rows="16" placeholder="Example opening: 'I have spent the last 12 years helping international buyers navigate one of the most exciting real estate markets in Latin America. From beachfront condos in Tamarindo to coffee farm estates in the Central Valley, I have closed over 200 transactions and built a reputation as one of the most trusted agents on the Pacific Coast…'"></textarea>
          <div class="char-count" id="char-count">0 words</div>
        </div>
      </div>

      <!-- PHOTOS FORM -->
      <div class="form-section" id="photos-form-section">
        <h3><span class="icon">📸</span> Lifestyle Photos</h3>

        <div class="drive-hint">
          <strong>How to upload your photos:</strong><br>
          1. Open the shared folder: <a href="https://drive.google.com/drive/folders/1215ZrAxdFMruBauBjTv8zlLcmXW59BTy?usp=drive_link" target="_blank">Google Drive Folder ↗</a><br>
          2. Create a <strong>subfolder with your name</strong> inside it.<br>
          3. Upload your lifestyle photos (minimum 4, JPG/PNG, 1200×800 px+).<br>
          4. <strong>Share your subfolder:</strong> Right-click → Share → <em>Anyone with the link</em> → Viewer.<br>
          5. Copy the link to your subfolder and paste it below.
        </div>

        <div class="drive-warning">
          ⚠️ <strong>Important:</strong> Your Google Drive folder <strong>must be set to "Anyone with the link can view"</strong> — otherwise the marketing team will not be able to access your photos and your submission may be rejected.
        </div>

        <div class="photo-grid-preview">
          <div class="photo-slot"><span class="icon">🏖️</span><span>Photo 1</span></div>
          <div class="photo-slot"><span class="icon">🌿</span><span>Photo 2</span></div>
          <div class="photo-slot"><span class="icon">🏡</span><span>Photo 3</span></div>
          <div class="photo-slot"><span class="icon">☕</span><span>Photo 4+</span></div>
        </div>

        <div class="form-group">
          <label>Your Google Drive folder link <span>(link to your personal subfolder with photos)</span></label>
          <input type="url" class="drive-link-input" id="drive-link-input" placeholder="https://drive.google.com/drive/folders/your-folder-id">
        </div>
      </div>

      <!-- ACTION BAR -->
      <div class="action-bar" id="action-bar">
        <div class="action-left">
          <button class="btn-save-draft" id="btn-save-draft">💾 Save Draft</button>
          <span class="save-indicator" id="save-indicator"></span>
        </div>
        <button class="btn-submit" id="btn-submit">Submit Biography</button>
      </div>

      <!-- SUBMITTED STATE (hidden until submitted) -->
      <div class="submitted-overlay" id="submitted-overlay" style="display:none">
        <div class="submitted-check">✅</div>
        <h3>Biography Submitted!</h3>
        <p>Your updated biography and photo folder link have been sent to the marketing team at <strong>marketing@2costaricarealestate.com</strong>. Thank you for taking the time to make your profile shine!</p>
        <p style="font-size:0.8rem;color:var(--text-light)">Your submission is now locked. Contact marketing@2costaricarealestate.com if you need to make changes.</p>
      </div>

    </div><!-- /right-panel -->
  </div><!-- /editor-layout -->
</div>

<!-- SHARING REMINDER MODAL -->
<div class="modal-backdrop" id="sharing-reminder-modal">
  <div class="modal">
    <h3>📁 Before you submit — check your Drive folder</h3>
    <p>Please confirm that your Google Drive photo folder is set to <strong>"Anyone with the link can view"</strong>.</p>
    <div class="sharing-steps">
      <div class="sharing-step"><span class="step-num">1</span><span>Open your Google Drive folder</span></div>
      <div class="sharing-step"><span class="step-num">2</span><span>Click the <strong>share icon</strong> (person with +) at the top right</span></div>
      <div class="sharing-step"><span class="step-num">3</span><span>Under "General access" select <strong>"Anyone with the link"</strong></span></div>
      <div class="sharing-step"><span class="step-num">4</span><span>Make sure the role is set to <strong>Viewer</strong></span></div>
      <div class="sharing-step"><span class="step-num">5</span><span>Click <strong>Done</strong> — then come back and confirm below</span></div>
    </div>
    <div class="modal-actions">
      <button class="btn-cancel" id="btn-reminder-back">Go back & check</button>
      <button class="btn-confirm" id="btn-reminder-confirm">Yes, my folder is shared — Continue</button>
    </div>
  </div>
</div>

<!-- SUBMIT CONFIRM MODAL -->
<div class="modal-backdrop" id="submit-modal">
  <div class="modal">
    <h3>Ready to Submit?</h3>
    <p>Once you submit, <strong>you will not be able to edit your biography again</strong>. The marketing team will receive your submission immediately.<br><br>Make sure everything looks perfect before confirming.</p>
    <div class="progress-bar" id="submit-progress" style="display:none"><div class="progress-bar-fill" id="submit-progress-fill" style="width:0%"></div></div>
    <div style="margin-top:12px;font-size:0.82rem;color:var(--text-light);display:none" id="submit-status-text">Sending…</div>
    <div class="modal-actions" style="margin-top:20px">
      <button class="btn-cancel" id="btn-modal-cancel">Go back & review</button>
      <button class="btn-confirm" id="btn-modal-confirm">Yes, submit now</button>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script>
// ═══════════════════════════════════════════
// AGENT DATABASE  (email → { name, slug, password })
// ═══════════════════════════════════════════
const AGENTS = {
  // ── 2CRRE ──────────────────────────────────────────────────────────────────────────────────────────────────────
  "aldo@2costaricarealestate.com":       { name: "Aldo Chirinos",         slug: "aldo-chirinos",         password: "chirinos",   profileUrl: "https://www.2costaricarealestate.com/agents/aldo-chirinos" },
  "alex@2costaricarealestate.com":       { name: "Alex Bejarano",          slug: "alex-bejarano",         password: "bejarano",   profileUrl: "https://www.alexbejarano.com" },
  "alexandra@2costaricarealestate.com":  { name: "Alexandra Vargas",       slug: "alexandra-vargas",      password: "vargas",     profileUrl: "https://www.2costaricarealestate.com/agents/132618-alexandra-vargas" },
  "alejandro@2costaricarealestate.com":  { name: "Alejandro Amador",       slug: "alejandro-amador",      password: "amador",     profileUrl: "https://www.aleavellanas.com/" },
  "alazo@2costaricarealestate.com":      { name: "Alvaro Azofeifa",        slug: "alvaro-azofeifa",       password: "azofeifa",   profileUrl: "https://www.alazocr.com/" },
  "alvaro@2costaricarealestate.com":     { name: "Alvaro Ortiz",           slug: "alvaro-ortiz",          password: "ortiz",      profileUrl: "https://www.alvaroortizcr.com" },
  "alonso@2costaricarealestate.com":     { name: "Alonso Solano",          slug: "alonso-solano",         password: "solano",     profileUrl: "https://www.alonsosolano.com" },
  "ana@2costaricarealestate.com":        { name: "Ana Contreras",          slug: "ana-contreras",         password: "contreras",  profileUrl: "https://www.2costaricarealestate.com/agents/ana-contreras" },
  "andrea@2costaricarealestate.com":     { name: "Andrea Ramirez",         slug: "andrea-ramirez",        password: "ramirez",    profileUrl: "https://www.andrearp.com" },
  "andres@2costaricarealestate.com":     { name: "Andres Murillo",         slug: "andres-murillo",        password: "murillo",    profileUrl: "https://www.andrescr.com" },
  "beau@2costaricarealestate.com":       { name: "Beau Southwell",         slug: "beau-southwell",        password: "southwell",  profileUrl: "https://beaus.com" },
  "chris@2costaricarealestate.com":      { name: "Chris Norris",           slug: "chris-norris",          password: "norris",     profileUrl: "https://www.chrisnorriscr.com" },
  "dopper@2costaricarealestate.com":     { name: "Dopper Huckel",          slug: "dopper-huckel",         password: "huckel",     profileUrl: "https://www.dopperhuckelcr.com" },
  "felipe@2costaricarealestate.com":     { name: "Felipe Pozuelo",         slug: "felipe-pozuelo",        password: "pozuelo",    profileUrl: "https://www.felipepozuelorealestate.com/" },
  "gene@2costaricarealestate.com":       { name: "Gene Harris",            slug: "gene-harris",           password: "harris",     profileUrl: "https://www.geneharriscr.com" },
  "ignacio@2costaricarealestate.com":    { name: "Ignacio de la Hormaza",  slug: "ignacio-de-la-hormaza", password: "hormaza",    profileUrl: "https://www.ignaciodelahormaza.com" },
  "ingrid@2costaricarealestate.com":     { name: "Ingrid Ortiz",           slug: "ingrid-ortiz",          password: "ortiz",      profileUrl: "https://www.ingridortizcr.com" },
  "john@2costaricarealestate.com":       { name: "John Williamson",        slug: "john-williamson",       password: "williamson", profileUrl: "https://www.johnwilliamsoncr.com" },
  "jorge@2costaricarealestate.com":      { name: "Jorge Fernandez",        slug: "jorge-fernandez",       password: "fernandez",  profileUrl: "https://www.jorgefg.com" },
  "katherine@2costaricarealestate.com":  { name: "Katherine Apsey",        slug: "katherine-apsey",       password: "apsey",      profileUrl: "https://www.katherineapsey.com" },
  "lineth@2costaricarealestate.com":     { name: "Lineth Solano",          slug: "lineth-solano",         password: "solano",     profileUrl: "https://www.linethsolano.com/" },
  "maria@2costaricarealestate.com":      { name: "Maria Jimenez Bakit",    slug: "maria-jimenez-bakit",   password: "bakit",      profileUrl: "https://www.mariajimenezbakit.com" },
  "mariel@2costaricarealestate.com":     { name: "Mariel Gracia",          slug: "mariel-gracia",         password: "gracia",     profileUrl: "https://www.marielgraciacr.com" },
  "matt@2costaricarealestate.com":       { name: "Matt Hogan",             slug: "matt-hogan",            password: "hogan",      profileUrl: "https://www.matthogancr.com" },
  "mattc@2costaricarealestate.com":      { name: "Matt Casseday",          slug: "matt-casseday",         password: "casseday",   profileUrl: "https://www.mattcasseday.com" },
  "matthew@2costaricarealestate.com":    { name: "Matthew McPherson",      slug: "matthew-mcpherson",     password: "mcpherson",  profileUrl: "https://www.matthewmcphersoncr.com/" },
  "molly@2costaricarealestate.com":      { name: "Molly Dilworth",         slug: "molly-dilworth",        password: "dilworth",   profileUrl: "https://www.2costaricarealestate.com/agents/96825-molly-dilworth" },
  "nataliya@2costaricarealestate.com":   { name: "Nataliya Bari",          slug: "nataliya-bari",         password: "bari",       profileUrl: "https://www.nataliyabaricr.com/" },
  "pablo@2costaricarealestate.com":      { name: "Pablo Cardoza",          slug: "pablo-cardoza",         password: "cardoza",    profileUrl: "https://www.pablocardoza.com/" },
  "priscilla@2costaricarealestate.com":  { name: "Priscilla Lara",         slug: "priscilla-lara",        password: "lara",       profileUrl: "https://www.priscillalara.com/" },
  "rachel@2costaricarealestate.com":     { name: "Rachel Candib",          slug: "rachel-candib",         password: "candib",     profileUrl: "https://www.rachelcandibcr.com" },
  "roberto@2costaricarealestate.com":    { name: "Roberto Brenes",         slug: "roberto-brenes",        password: "brenes",     profileUrl: "https://www.robertobrenesm.com" },
  "sara@2costaricarealestate.com":       { name: "Sara Gomez",             slug: "sara-gomez",            password: "gomez",      profileUrl: "https://www.saragomezcr.com" },
  "sander@2costaricarealestate.com":     { name: "Sander Werink",          slug: "sander-werink",         password: "werink",     profileUrl: "https://www.sanderarenal.com/" },
  "scott@2costaricarealestate.com":      { name: "Scott Cutter",           slug: "scott-cutter",          password: "cutter",     profileUrl: "https://www.scottcuttercr.com" },
  "cswilliams@2costaricarealestate.com": { name: "Scott Williams",         slug: "scott-williams",        password: "williams",   profileUrl: "https://www.scottwilliamscr.com" },
  "steve@2costaricarealestate.com":      { name: "Steve Hooven",           slug: "steve-hooven",          password: "hooven",     profileUrl: "https://www.stevehooven.com" },
  "todd@2costaricarealestate.com":       { name: "Todd Cutter",            slug: "todd-cutter",           password: "cutter",     profileUrl: "https://www.toddcutter.com" },
    "ea@2costaricarealestate.com":         { name: "Ignacio Velazquez",      slug: "ignacio-velazquez",     password: "velazquez",  profileUrl: "https://www.2costaricarealestate.com/agents" },
  "marketing@2costaricarealestate.com":  { name: "Laura Duran",            slug: "laura-duran",           password: "duran",      profileUrl: "https://www.2costaricarealestate.com/agents" },
  "vitaly@2costaricarealestate.com":     { name: "Vitaly Balasanov",       slug: "vitaly-balasanov",      password: "balasanov",  profileUrl: "https://www.vitalybalasanov.com" },
  // ── 2CRST Santa Teresa ─────────────────────────────────────────────────────────────────────────────────────────
  "andrea@2crsantateresa.com":           { name: "Andrea Bissinger",       slug: "andrea-bissinger",      password: "bissinger",  profileUrl: "https://www.andreabissingercr.com" },
  "dina@2crsantateresa.com":             { name: "Dina Tochluk",           slug: "dina-tochluk",          password: "tochluk",    profileUrl: "https://www.dinatochluk.com/" },
  "jen@2crsantateresa.com":              { name: "Jen Harter",             slug: "jen-harter",            password: "harter",     profileUrl: "https://www.jenharter.com" },
  "josie@2crsantateresa.com":            { name: "Josie Green",            slug: "josie-green",           password: "green",      profileUrl: "https://www.josiegreencostarica.com" },
  "juan@2crsantateresa.com":             { name: "Juan Pinto",             slug: "juan-pinto",            password: "pinto",      profileUrl: "https://www.juanpintocr.com" },
  "reese@2crsantateresa.com":            { name: "Reese Langston",         slug: "reese-langston",        password: "langston",   profileUrl: "https://www.reeselangston.com" },
  "sarah@2crsantateresa.com":            { name: "Sarah Williams",         slug: "sarah-williams",        password: "williams",   profileUrl: "https://www.sarahwilliamscostarica.com" },
  // ── 2CRPA Papagayo ─────────────────────────────────────────────────────────────────────────────────────────────
  "ewen@2crpapagayo.com":                { name: "Ewen Dusch",             slug: "ewen-dusch",            password: "dusch",      profileUrl: "https://www.ewendusch.com/" },
  "kelli@2crpapagayo.com":               { name: "Kelli Ricco",            slug: "kelli-ricco",           password: "ricco",      profileUrl: "https://www.kelliricco.com/" },
  "melsen@2crpapagayo.com":              { name: "Melsen Araya",           slug: "melsen-araya",          password: "araya",      profileUrl: "https://www.melsenaraya.com/" },
  "pourya@2crpapagayo.com":              { name: "Pourya Safari",          slug: "pourya-safari",         password: "safari",     profileUrl: "https://www.2crpapagayo.com/agents/pourya-safari" },
  "theo@2crpapagayo.com":                { name: "Theo Ferreira",          slug: "theo-ferreira",         password: "ferreira",   profileUrl: "https://www.2costaricarealestate.com/agents/114028-theo-ferreira" },
  "german@2crpapagayo.com":              { name: "German Valencia",        slug: "german-valencia",       password: "valencia",   profileUrl: "https://www.2crpapagayo.com/agents/german-valencia" },
  "cynthia@2crpapagayo.com":             { name: "Cynthia Urena",          slug: "cynthia-urena",         password: "urena",      profileUrl: "https://www.cynthiaurena.com/" },
  "juancarlos@2crpapagayo.com":          { name: "Juan Carlos Peralta",    slug: "juan-carlos-peralta",   password: "peralta",    profileUrl: "https://www.2costaricarealestate.com/agents/130118-juan-carlos-peralta" },
};

// ═══════════════════════════════════════════
// SUPABASE — cloud database
// ═══════════════════════════════════════════
const SUPABASE_URL = 'https://ebwvyikrxgjpjpzccbts.supabase.co';
const SUPABASE_KEY = 'sb_publishable_b0KHTa_LCWZk-ICELSAN8A_dSQ_JQ5R';

async function sbGet(email) {
  const res = await fetch(`${SUPABASE_URL}/rest/v1/agent_bios?email=eq.${encodeURIComponent(email)}&select=*`, {
    headers: { 'apikey': SUPABASE_KEY, 'Authorization': `Bearer ${SUPABASE_KEY}` }
  });
  const rows = await res.json();
  return rows.length ? rows[0] : null;
}

async function sbUpsert(data) {
  await fetch(`${SUPABASE_URL}/rest/v1/agent_bios`, {
    method: 'POST',
    headers: {
      'apikey': SUPABASE_KEY,
      'Authorization': `Bearer ${SUPABASE_KEY}`,
      'Content-Type': 'application/json',
      'Prefer': 'resolution=merge-duplicates'
    },
    body: JSON.stringify(data)
  });
}

async function sbGetAll() {
  const res = await fetch(`${SUPABASE_URL}/rest/v1/agent_bios?select=*&order=submitted_at.desc.nullslast`, {
    headers: { 'apikey': SUPABASE_KEY, 'Authorization': `Bearer ${SUPABASE_KEY}` }
  });
  return await res.json();
}

// ═══════════════════════════════════════════
// STATE
// ═══════════════════════════════════════════
let currentAgent = null;
let autoSaveTimer = null;
let agentRecord = null; // current agent's DB record

// ═══════════════════════════════════════════
// TOAST
// ═══════════════════════════════════════════
function showToast(msg, type = '') {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.className = 'toast show ' + type;
  clearTimeout(t._timer);
  t._timer = setTimeout(() => { t.className = 'toast'; }, 3500);
}

// ═══════════════════════════════════════════
// SCREEN SWITCHING
// ═══════════════════════════════════════════
function showScreen(id) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}

// ═══════════════════════════════════════════
// LOGIN
// ═══════════════════════════════════════════
document.getElementById('btn-login').addEventListener('click', doLogin);
document.getElementById('login-password').addEventListener('keydown', e => { if(e.key==='Enter') doLogin(); });

function doLogin() {
  const email = document.getElementById('login-email').value.trim().toLowerCase();
  const pass  = document.getElementById('login-password').value;
  const err   = document.getElementById('login-error');
  const btn   = document.getElementById('btn-login');
  err.style.display = 'none';

  // Admin login
  if (email === ADMIN.email && pass === ADMIN.password) {
    btn.innerHTML = '<span class="spinner"></span>';
    btn.disabled = true;
    setTimeout(() => {
      btn.textContent = 'Sign In';
      btn.disabled = false;
      currentAgent = { email, name: 'Administrator', isAdmin: true };
      openAdmin();
    }, 500);
    return;
  }

  // Agent login
  const agent = AGENTS[email];
  if (!agent || agent.password !== pass) {
    err.style.display = 'block';
    return;
  }

  currentAgent = { email, ...agent };
  btn.innerHTML = '<span class="spinner"></span>';
  btn.disabled = true;
  setTimeout(() => {
    btn.textContent = 'Sign In';
    btn.disabled = false;
    openEditor();
  }, 600);
}

// ═══════════════════════════════════════════
// OPEN EDITOR
// ═══════════════════════════════════════════
async function openEditor() {
  showScreen('screen-editor');
  document.getElementById('topbar-agent-name').textContent = currentAgent.name;
  document.getElementById('agent-name-display').textContent = currentAgent.name;
  document.getElementById('agent-profile-link').href = currentAgent.profileUrl;

  // Show loading state
  document.getElementById('bio-textarea').placeholder = 'Loading your draft…';
  document.getElementById('bio-textarea').disabled = true;

  // Load from Supabase
  try {
    agentRecord = await sbGet(currentAgent.email);
  } catch(e) {
    agentRecord = null;
  }

  document.getElementById('bio-textarea').disabled = false;
  document.getElementById('bio-textarea').placeholder = "Start writing here…";

  if (agentRecord) {
    document.getElementById('bio-textarea').value = agentRecord.bio || '';
    document.getElementById('drive-link-input').value = agentRecord.drive_link || '';
    updateWordCount();
    if (agentRecord.submitted) {
      showSubmittedState();
    } else {
      showEditState();
      fetchCurrentBio(currentAgent.profileUrl);
    }
  } else {
    document.getElementById('bio-textarea').value = '';
    document.getElementById('drive-link-input').value = '';
    updateWordCount();
    showEditState();
    fetchCurrentBio(currentAgent.profileUrl);
  }
}

// ═══════════════════════════════════════════
// AGENT BIOS — loaded from CMS export
// ═══════════════════════════════════════════
const AGENT_BIOS = {
  "kelli@2crpapagayo.com": `Kelli Ricco was born in Philadelphia, PA and graduated from Arcadia University. This is where her passion for fitness and wellness began! Right out of college, Kelli owned her first personal training business in New Jersey for two years. Her curiosity for what made people live naturally their longest, happiest, healthiest lives led her to Australia where she continued her career in fitness and wellness. After discovering that Costa Rica was a "Blue Zone" for centenarians (and where most of the fruit she ate came from anyway), she moved there to study the culture and lifestyle. What was meant to be a six months stay turned into ten years and coming! Kelli has worked at the Four Seasons Resort Costa Rica and now owns her own fitness and wellness company called LONGEV. She feels so lucky to have found this beautiful country that allows her to live a peaceful and pura vida lifestyle with her husband and children. She hopes that she can inspire so many others to find their happiness here in Costa Rica as she has.`,
  "nataliya@2costaricarealestate.com": `Nataliya, a dedicated real estate professional, brings a wealth of experience and a passion for helping clients find their dream homes. Born in one of the coldest corners of Russia, raised in New York City and now residing in the serene beauty of Costa Rica, Nataliya's global perspective and deep understanding of the real estate market have shaped her into a trusted advisor. With over a decade in the industry, Nataliya has successfully represented clients from all walks of life, including celebrities and executives. Her expertise extends to sales, rentals, renovations, home staging, and new construction projects. Notably, she played a pivotal role in revitalizing Brooklyn Heights, selling out a building with record-breaking numbers and contributing to its transformation into a sought-after neighborhood. Nataliya's philosophy is simple: focus on results, not rhetoric. By dedicating her time and energy to understanding her client's needs, she provides personalized guidance and ensures a smooth transaction. As a certified Master Negotiation Expert, Nataliya is your trusted ally in ensuring the choppiest of waters turn into the calmest of seas. Whether you're buying, selling, or building a home, Nataliya's commitment to excellence and her knowledge of the market make her an invaluable partner.`,
  "ana@2costaricarealestate.com": `Ana was born and raised in Costa Rica. As an adult, she lived in various places for seven years, only to discover that nothing compares to the climate, nature, warmth of its people, and quality of life her own country offers. A visionary, loyal, and capable leader, her greatest strength lies in her integrity and willingness to serve others. A professional with a sensitive and empathetic heart, that has guided and supported hundreds of people in their personal and financial transformations for over 20 years through consulting and coaching. Her experience and passion for providing solutions to her clients have led her to incorporate real estate alternatives into her services. This allows her clients to improve their quality of life, maximize their assets, and build stories that transform their lives.`,
  "theo@2crpapagayo.com": `A native of France, Theo moved to Costa Rica in 2015, at the age of 15, and quickly developed a deep attachment to the Guanacaste area where he grew up. With a degree in computer engineering, he nevertheless chose to change his path to get closer to people and nature by embarking on a career in real estate. With his love for the Guanacaste region and his determination to offer quality service, Theo is ready to take on any real estate challenge and help his clients find the property of their dreams in this tropical paradise. Reliable, dedicated and passionate, Theo Ferreira is your trusted partner for real estate projects in Costa Rica's splendid Papagayo area.`,
  "andrea@2costaricarealestate.com": `My name is Andrea, I am Costa Rican, I studied dentistry more than 20 years ago, I am passionate about a country like Costa Rica, its flora and fauna, I love spending family time with my two children and my husband. I like to travel and learn about new cultures and their gastronomy, I like the beach and the mountains, I love road cycling and I have competed in several opportunities in Costa Rica and outside of Costa Rica, I am an animal lover and I like agriculture, that is why I grow avocado in a small farm in Cartago. My interest in real estate is awakened because I see a great opportunity for personal and professional growth and I love to generate solid and lasting friendships and real estate is perfect for that, to generate bonds of trust. For me Costa Rica is a country with an impressive ecotourism and working in a company with so much experience gives you the certainty of providing excellent quality service and trust.`,
  "lineth@2costaricarealestate.com": `Lineth is proudly TICA, with more than 25 years of experience in real estate, and a solid background in hospitality and property management for vacation homes in the Quepos and Manuel Antonio area, where she lived for over 20 years, and more recently in San José where she is from. She has been involved in major real estate developments, where she has gained a deep understanding of the real estate market and a client-centered approach tailored to the unique needs of each customer. A Tourism graduate, Lineth stands out for her personalized approach and her ability to genuinely connect with her clients. Every transaction is, for her, an opportunity to build a lasting relationship based on trust, transforming the buying process into a smooth and satisfying experience. In addition to her professional dedication, Lineth is a mother of two young men, a devoted aunt, and a passionate cyclist, which has led her to organize sporting events and preside over ACONVIVIR, an NGO that promotes safety and peaceful coexistence on the roads.`,
  "ignacio@2costaricarealestate.com": `I was born and raised in San José, Costa Rica, and completed the International Baccalaureate program at the British School of Costa Rica. My father, originally from Spain, transitioned into real estate investing after a long career as a ship captain, which inspired my early passion for real estate. I earned my Bachelor's degree in Civil Engineering from Universidad Latina de Costa Rica and spent nearly eight years working on large-scale mixed-use developments with BILCO Construction. My project portfolio includes Avenida Escazú, Escazú Village, Ciudad AlEste, and Solaris Santa Ana. To complement my technical background, I pursued a Master of Science in Real Estate at the University of Colorado Boulder. I am fully bilingual and well-versed in Costa Rican laws and regulatory processes, which allows me to serve both domestic and international clients at the highest level. Since joining 2CostaRicaRealEstate, I have focused on providing clients with unmatched value through technical knowledge, market insight, and strong relationships with key developers, investors, and decision-makers in Costa Rica.`,
  "beau@2costaricarealestate.com": `My name is Beau Southwell, and I moved to Dominical, Costa Rica as a child with my father and older brother in 1994. I attended public school in the Dominical area of Costa Rica for five years and became an avid surfer. I returned to California in my late teens where I completed high school and eventually attended the University of California at Santa Cruz where I earned my Bachelor's Degree. I obtained my real estate license through the State of California in 2007 and worked for both commercial and residential real estate brokerages. I was also a Police Officer in California for eight years where I worked as a bi-lingual patrol officer and SWAT team member. In my early thirties, I elected to leave the high-stress life of law enforcement in California and returned to the country I had always loved, Costa Rica.`,
  "cynthia@2crpapagayo.com": `Cynthia is Tica (Costarican) born and raised in the picturesque town of San Carlos, Province of Alajuela. Her educational background is a blend of business administration and computer engineering, a unique combination that speaks to her adaptability and problem-solving abilities. Cynthia is an avid outdoor enthusiast who relishes in the beauty of nature, travel and learning about other people and their experiences. She's not only a dedicated mother to her son but also a loving caregiver to her faithful dog. Cynthia's love for challenges and her ability to adapt to different situations have allowed her to thrive in her 10 years of experience in the real estate industry.`,
  "sarah@2crsantateresa.com": `Originally from Toronto, Sarah moved to Santa Teresa in 2011. Sarah has an extensive professional background in communications, marketing, and design from years of working on many large corporate branding campaigns in Canada. Sarah's passion turned to real estate upon moving to Santa Teresa and she has since combined her strong interpersonal skills with her extensive local insight and comprehensive knowledge of Costa Rican real estate. Sarah is a dedicated and hard-working individual that specializes in residential and commercial real estate. She has a warm and friendly approach that centers around the importance of communication, trust, reliability, and follow-through in her client relationships. Sarah loves to surf, read, meet with friends, and travel around the world. She is a loving wife and the devoted mother of two children.`,
  "juan@2crsantateresa.com": `Juan is known to be extremely passionate about wildlife and the environment. He describes himself as a Biologist at heart, an Agronomist by the school, and a hotelier by trade. He studied agriculture and sustainable development at EARTH university and since then has dedicated his time to high-end hospitality projects with sustainability values. During his time in the Osa Peninsula jungle, Juan was the general manager for Lapa Rios Ecolodge, a world-renowned property committed to sustainable development. During his management, the hotel was recognized by Conde Nast, Travel and Leisure and Andrew Harper. He then married his wife Cindy and embarked on a one-year honeymoon around the world. Upon their return, Juan and his wife opened a scuba diving center committed to education, research and conservation in Santa Teresa. He continues to be involved in several hospitality projects in Costa Rica and has recently joined the 2Costa Rica team as a real estate agent.`,
  "alejandro@2costaricarealestate.com": `Alejandro was born in the breathtaking valley of Turrialba, surrounded by the natural beauty of rivers and volcanoes. After finishing high school in New Zealand and completing his degree in industrial engineering in San Jose, Alejandro's entrepreneurial spirit led him to develop a small community of lots in Avellanas, Guanacaste in 2001. In 2009, he joined forces with a reputable developer in Tamarindo, selling condominiums and managing common areas. In 2015 he joined a major real estate franchise, showcasing his expertise in luxury properties and development parcels. Beyond his professional career, Alejandro is happily married to his wife Marcia, a successful interior designer, and they share the blessing of raising two vibrant children while serving their local church Casa Vida.`,
  "sander@2costaricarealestate.com": `Born in the 70's in the Netherlands, from parents that spent a good amount of time in the Caribbean, Sander's desire to live in a tropical location was sparked early. In 2005 the move to Costa Rica was made, and as a life-long waterski and wakeboard fanatic the Lake Arenal region was quickly discovered and called home. Soon Costa Rica's first wakeboard school was started, and he became the distributor for the sport's leading brands. Through his wife's successful lake-area Property Management business, he slowly got involved in real estate, eventually joining the 2Costa Rica family. Free time is mostly spent on the water or other outdoors with his family or friends. Music is another bringer of great joy for Sander, and he has a passion for older, often unreliable, mostly Italian and English cars.`,
  "josie@2crsantateresa.com": `Josie Green is originally from the UK, but has been living in the Santa Teresa area for over 16 years and working in Real Estate for the last 10 years. Josie has a background in banking and finance, having worked for a boutique corporate finance firm in London. As with so many people, Josie fell in love with Santa Teresa whilst on a two-week vacation. She was drawn by the rugged beauty of the beaches, the wonderful waves and the healthy lifestyle. After a number of repeat visits, she decided to pack up her life in London and make a permanent move to Costa Rica in 2009. Over the years she has helped many individuals and families find their perfect home here on the coast, guiding them through the process of purchasing property in Costa Rica.`,
  "priscilla@2costaricarealestate.com": `Priscilla was born and raised in Costa Rica. She spent her childhood years in a Coffee Plantation in Turrialba partly owned by her family. Priscilla went to bilingual schools in Costa Rica and has lived in the United States and Europe, so she is familiar with multi-cultural environments and enjoys interaction with people of different cultures and backgrounds. She pursued her sophomore year in high school and her Master's degree in the US and spent one year in Europe to study French. She enjoys reading, hiking, paddle boarding, going to the beach and the outdoors in general, and she is passionate about providing real estate solutions for both locals and expats.`,
  "mattc@2costaricarealestate.com": `Matt Casseday has resided in Costa Rica since 1990. Originally from West Virginia, he also lived and worked in Ohio, Washington DC, New Orleans, and the US Virgin Islands before settling here. His diverse work background includes numerous years in the bar and restaurant business, as well as seven years as a Travel Consultant, where he planned over one thousand vacations for clients in the US and Canada. He then joined 2Costa Rica Vacation Rentals, working as the Reservations Manager for two years, before transitioning to the Real Estate division. With many years of experience in dealing directly with people and his extensive knowledge of Costa Rica, he is a professional and reliable source for anyone looking to invest in real estate. Matt lives in San Isidro del General with his wife Ana and is the father of four adult children, all born in Costa Rica.`,
  "alex@2costaricarealestate.com": `Alex Bejarano was born in Ft. Lauderdale, Florida. His parents moved back and forth from the U.S. to Bogota, Colombia until eventually settling in Texas, and later San Jose, Costa Rica. Having graduated from Latina University with a degree in Business Administration, he relocated in 2007 to Tamarindo to pursue a career in real estate. Alex has also worked in the non-profit field, overseeing operations for Latin America with Planet Water Foundation and directing a local charity called Costa Rica Makes Me Happy. Throughout his business career, he has always been involved with his local church Iglesia Casa Vida where he currently serves as one of the pastors on staff. Alex is married to his wife Terri Lynn and has had the joy of raising their three children alongside her. He desires to serve his clients through his 15 years of local knowledge and multi-cultural experience.`,
  "john@2costaricarealestate.com": `John Williamson grew up in the Blue Ridge Mountains of Virginia in the USA and moved to Manuel Antonio, Costa Rica in 2000. For two decades he owned a photography and video company which gave him the opportunity to combine his appreciation of the Costa Rican environment while working with a myriad of diverse projects, people and businesses. His specialization in architectural photography has given him a keen eye and an understanding of the nuanced characteristics of each listing. A love of nature and an insatiable curiosity about the natural environment have been the driving force guiding his footsteps. John applies this same passion to finding his clients their dream home or property. John is a family man and appreciates experiencing life with his wife and daughter. They enjoy hiking, diving, traveling and simply appreciating the abundant wildlife in the area.`,
  "scott@2costaricarealestate.com": `Scott Cutter, originally from Birmingham, Alabama, first came to Costa Rica in 1997 after graduating from the University of Colorado at Boulder with a degree in Sociology and a minor in Spanish. He settled in the Manuel Antonio area, spent several years as General Manager of a luxury boutique hotel, and then began a career as a real estate broker — a field in which he has been working full time for the past 15 years. Scott has extensive experience in development, having sold land and negotiated the largest development land and hotel sales in the area. He is now the sales director for Marina Pez Vela, in addition to his ongoing role as lead broker for 2 Costa Rica Real Estate. Scott is married to Gisella Alvarado and is the proud father of Liana Rosalina and Mia Isabella.`,
  "reese@2crsantateresa.com": `Reese has more than two decades of experience in the Costa Rican real estate market, focused on the Nicoya Peninsula. He has worked in Law and International Real Estate Brokerage, focusing on maritime zone properties and project development. Reese specializes in raw land, home appraisals and concession properties. As part owner of Hotel Casa Cecilia, he can answer any questions related to the hospitality industry.`,
  "katherine@2costaricarealestate.com": `Originally from the Chicago area, Katherine moved to New Hampshire to study English Teaching and ride on the equestrian team at the University of NH. She obtained her real estate license as a senior in college. Katherine later moved to the Detroit area where she earned her Masters Degree and worked at a private boarding school. With her children enrolled in college, Katherine moved to Costa Rica to teach at a private international school. After being captivated by the country, she chose to call Costa Rica home and purchased land in Ojochal where she built a yoga and wellness studio. She has been an active real estate agent in Costa Rica for three years, working with clients from all over the world. Katherine currently lives in Ojochal with her two rescue dogs and teaches yoga and Zumba classes that raise money for the local animal rescue center.`,
  "ewen@2crpapagayo.com": `Hailing from the vibrant streets of Paris, Ewen embarked on a life-changing journey that brought him to beautiful Costa Rica. His love affair with this enchanting land began in 2015 when he and his family visited for the first time, and they made it their permanent home in 2017. Ewen earned his real estate license in Costa Rica and in 2018 stepped into the industry as an independent agent. Just two years into his journey, he launched his own luxury-branded real estate office in 2020, specializing in helping foreigners relocate to Costa Rica. In October 2023, Ewen and his team decided to join the 2Costa Rica family, expanding their horizons to provide even more dedicated service to their clients.`,
  "rachel@2costaricarealestate.com": `I was born and raised in Miami Beach, Florida, right on the water on Sunset Island. I have always been an ocean lover spending my weekends sailing, snorkeling, and fishing. I came to Costa Rica for the first time in the summer of 1995 during my graduating year from the University of Arizona. During this trip I fell in love with the country — the beauty of the jungle and all its amazing wildlife took my breath away and I knew I was home. Since that first trip I came every summer until I bought my first piece of property in Manuel Antonio in 2004. I have raised my four daughters here in this beautiful country and couldn't imagine doing it anywhere else. I have been in the real estate industry since my time in Arizona, and bringing my international knowledge to the table in Costa Rica has helped me succeed here. I am beyond grateful to call Costa Rica my home.`,
  "mariel@2costaricarealestate.com": `Young, passionate and driven are three words to describe Mariel. She has lived in India where she volunteered in slums in Delhi, then she learned Portuguese in Lisbon, Portugal. She studied Diplomacy and PR and has a strong background in social media and online marketing. Mariel is fluent in Spanish, English, Portuguese and Italian. She likes to travel to exotic destinations, scotch and wine tasting, and attend polo and philanthropy events in her free time.`,
  "felipe@2costaricarealestate.com": `My journey into real estate is rooted in a desire to connect people with places that inspire them and to create developments that respect both community and environment. With a degree in Industrial Engineering and a Master's in Sustainable Business and Innovation from EADA Business School in Barcelona, I bring a unique blend of analytical skills and forward-thinking vision to the industry. Beyond my education, my life has always been shaped by a deep connection to nature and the ocean. With over 20 years dedicated to surfing, alongside practices like yoga, meditation, and breathwork, I've learned the importance of flow, balance, and resilience — qualities I carry into my professional life. Thanks to surfing I have managed to explore most of Costa Rica's coastline, helping me understand the best locations we have to offer and how surfing has shaped our real estate market and tourism industry.`,
  "aldo@2costaricarealestate.com": `Aldo Chirinos was born in San Jose, Costa Rica and raised in Playa Negra, Guanacaste. Growing up by the beach, he dedicated most of his life to sports. While graduating from CRIA (Costa Rica International Academy) he competed in surfing all over the world until he was 20 years old. He then started studying business administration at Universidad Latina. At the age of 22 he realized there were many opportunities and decided to start working in Real Estate, falling in love with sharing the beauties Guanacaste has to offer and meeting people from different cultures. He also started training Martial Arts at 22, learning Brazilian Jiu Jitsu, Kickboxing, and competing in Mixed Martial Arts, where he became amateur national champion in early 2024.`,
  "roberto@2costaricarealestate.com": `I was born in San Jose 31 years ago in a small town full of nature and farms. I speak 4 languages: Spanish, English, Portuguese and Italian. At the age of 17 I studied abroad on an international exchange program in Brazil. After that year I came to Guanacaste and started a real estate project with my mom — we bought a farm, planted fruit trees and became beekeepers, while also running cabins for rent. I completed my degree in international business with an emphasis in Sustainable Tourism. I am currently living on my nursery property in Playa Garza, Nosara. I started a landscape design and installation company named after local bees and ants, Tamaga and Zompopas, working on master-planning and design for native plants gardens throughout Nosara. Based on this knowledge and contacts built over seven years, I decided to join 2Costa Rica Real Estate to help clients find the properties of their dreams.`,
  "sara@2costaricarealestate.com": `My name is Sara Gomez. I was born in a small town in Colombia called Jardín. When I was 22, I came with my husband to Costa Rica looking for better opportunities — a country I fell in love with, not only because of its rich culture but also because of its people. My daughter Sofia was born here in 2008 and is very proud to be Tica. I graduated with a Bachelor of Business Administration and Finance from a Costa Rican university. In 2003 I started working as a receptionist in a hotel in Manuel Antonio, later became assistant manager and then general manager from 2005 to 2021 — 18 years during which I built friendships around the world. I then joined the administrative area of 2 Costa Rica Real Estate and am now starting an exciting career in sales, where I hope to share my deep knowledge of Costa Rica and its Pura Vida lifestyle with all our clients.`,
  "juancarlos@2crpapagayo.com": `Born in San José, Costa Rica, Juan Carlos has deep roots across the country. His mother is from Liberia, the capital of Guanacaste, where he has spent over four decades living and vacationing. On his father's side, his family hails from Grecia, Alajuela, a top coffee region with a long tradition in coffee production. Juan Carlos worked in the specialty coffee industry as a professional taster, then moved to Playas del Coco as a Property Manager before pursuing an MBA in Madrid, Spain. With more than a decade of experience in real estate development and project management, he has successfully led multiple projects throughout Guanacaste. Today, he guides clients to the right opportunities — whether a luxury home on the Gold Coast, a coffee farm in the Central Valley, or a prime piece of land for residential or commercial development.`,
  "todd@2costaricarealestate.com": `Todd Cutter, originally from Birmingham, Alabama, came to Costa Rica in 1998 after graduating from the University of Colorado Boulder with a degree in Spanish for International Business. He founded an online travel business with niche divisions including surf travel, honeymoon and family travel, which he later sold to dedicate all his time and energy to 2Costa Rica Real Estate. Todd and his brother Scott are the managing brokers of the business. Todd lives in San Jose, managing the central office, and is married to his wife Ana with two children. He specializes in luxury residential real estate, commercial real estate, large development parcels, hotel development, and consulting, and has had the pleasure of working with clients from dozens of countries around the world.`,
  "ingrid@2costaricarealestate.com": `Ingrid is a highly regarded real estate professional known for her clarity, professionalism, and ability to identify exactly the right property for each client. As one client shared: "She guided us through every step of the process with clarity and professionalism, making everything feel smooth and manageable." With deep local knowledge of the Escazú market and surrounding areas, Ingrid provides valuable advice and local insight that go well beyond the transaction. She is known for remaining in close contact with her clients long after closing, supporting them as they establish themselves in Costa Rica.`,
  "alexandra@2costaricarealestate.com": `I grew up in Palmares, Alajuela. I am an attorney and notary public, a profession that has allowed me to build a strong foundation in legal counsel, negotiation, and legal security — essential tools in the world of real estate. I have lived in Jacó since 2018, where I have built my family life with the intention of raising my children close to the ocean. My husband, Vini, and our three children are my driving force and daily inspiration. I am passionate about diving, photography, and everything related to the ocean. My goal is for every person I work with to fall in love with the ocean, the natural surroundings, and everything this paradise has to offer. It is a true privilege to guide individuals and families in finding their home or investment in a region that has so much to give.`,
  "dina@2crsantateresa.com": `Dina is a distinguished real estate professional with over 15 years of experience representing luxury properties across Costa Rica's most coveted coastal destinations, including Manuel Antonio, Papagayo, and now Santa Teresa. As a longtime advisor with 2 Costa Rica Real Estate, she is known for her discretion, integrity, and unwavering commitment to delivering exceptional results. Educated at Costa Rica Academy and later at the Pratt Institute in New York, she began her career in Miami in senior sales and management within a multi-million-dollar international business. Dina returned to Costa Rica in 2007, established a successful property management company in Manuel Antonio, and joined 2 Costa Rica Real Estate in 2010. Today, based in Santa Teresa and currently building her own home in the area, she offers clients not only market expertise but also an authentic, insider perspective on the lifestyle that defines this unique destination.`,
  "alazo@2costaricarealestate.com": `Alvaro Azofeifa is a Costa Rican real estate professional based on the Southern Pacific coast, specializing in high-quality homes, land, and investment properties across Uvita, Ojochal, and Dominical. With over two decades of entrepreneurial and operational experience in the region, Alvaro has developed and invested in residential properties, overseen renovations and new builds, and managed boutique vacation homes and property portfolios. His background includes founding Uvita 360 and Wetfall Surf School, two early tourism ventures in Uvita, giving him a deep understanding of the region's growth and lifestyle appeal. Fluent in American Standard English and experienced in digital marketing and international outreach, Alvaro works closely with buyers from around the world seeking strategic real estate opportunities in Costa Rica.`,
  "pablo@2costaricarealestate.com": `Pablo was born in San José, Costa Rica in 1979. He moved to Guanacaste with his wife Carolina and his son Pablo de Jesús when the pandemic began in April 2020, following their passion for the beach and dream of living in Guanacaste. Pablo is a seasoned pharmacist with extensive experience in sales, marketing, and leadership roles within multinational pharmaceutical companies including AstraZeneca, GSK, and Novartis, working internationally in the UK, Colombia, Guatemala, and the United States. In January 2023, he decided to follow his other passion: the real estate industry. Pablo has invested in real estate assets in Guanacaste since 2005 and has developed luxury spec homes during that period. Known for his analytical approach and results orientation, Pablo excels at building genuine client relationships and delivering exceptional service.`,
  "molly@2costaricarealestate.com": `Molly was born and raised in a small town in Northern California. At the age of 20, she landed an internship with Rip Curl Surf Company, and over the next several years worked with companies like Sanuk, Dragon Alliance, Maaji swimwear, and Hurley International. In addition to her career in the action sports industry, Molly also accomplished a career as a fitness instructor. Over the last five years, Molly has split time between California and Dominical, and has since transitioned to be full time in Costa Rica. Together with her fiancé, a 9-year resident of Costa Rica, they launched a non-profit swim school called Puedo Nadar and own and operate multiple Airbnbs. Molly loves spending time in the mountains of Lake Tahoe, continues to teach fitness classes virtually, and loves running on the beach with her Weimaraner Dakota.`,
  "vitaly@2costaricarealestate.com": `Vitaly Balasanov provides exceptional realty services in Costa Rica. Resourceful and attentive, he is the professional who will get you the results you are looking for. Vitaly was raised in Moscow and moved to the United States to attend college before eventually moving to Costa Rica. He has distinguished himself as a realtor with expertise in condominiums, luxury markets, commercial properties, income-generating properties, investment properties, and serving international home buyers. He has inside knowledge of the San Jose, Escazu, Santa Ana, Heredia, and Central Pacific markets and understands the diverse needs of young professionals, entrepreneurs, and families. Vitaly is also a specialist in helping foreign nationals with mortgages. He is fluent in Russian, English, and Spanish.`,
  "jorge@2costaricarealestate.com": `Jorge Fernández Galimany was born and raised in San José, Costa Rica, with a Master's degree in Business Administration from EAE Business School in Barcelona, Spain and a Bachelor's degree from Universidad Latina de Costa Rica. Jorge has over ten years of experience in commercial, marketing, sales, and customer service sectors. His professional growth opened the door to a career in real estate, where he became part of the strategic team of Costa Rica's most experienced Escrow company and opened a new regional office in Tamarindo. Jorge specializes in the Guanacaste Gold Coast — Tamarindo, Avellanas, Flamingo, Potrero, and Las Catalinas — providing relevant information about real estate investment and relocation to Costa Rica. He enjoys surfing in the morning or at sunset and identifies with values such as ethics, honesty, kindness, empathy, and responsibility.`,
  "cswilliams@2costaricarealestate.com": `Scott Williams is a Costa Rica realtor living on the central/southern Pacific coast. Scott has lived there since 1998, is a resident of Costa Rica, is fully bilingual, and is a member of the Costa Rican Chamber of Realtors (CCCBR) and the National Association of Realtors (NAR). Originally from Virginia, Scott landed in Costa Rica immediately following his graduation from Hampden-Sydney College in 1998. During his first four years in the country, he co-directed the local operation of Outward Bound. Starting in 2002, he did consulting and start-up work on a tourism center and property management company. Having bought, sold, built and remodeled several properties here, his transition into real estate in 2003 came very naturally. Scott also worked closely with the owners of 2 Costa Rica Real Estate in starting the company and specializes in residential, ranches and hotels in the Central Pacific and Southern Zone. He currently lives in Manuel Antonio with his daughter Ylang.`,
  "matthew@2costaricarealestate.com": `Born in Mission Viejo and raised in Tustin, California, Matthew McPherson brings a unique blend of Southern California roots and global experience to the Costa Rica real estate industry. A proud graduate of Pepperdine University with a Bachelor's in Business Administration, Matthew's travels took him across multiple continents — playing professional Water Polo in Australia, living in Bali as a Sports & Activity Specialist, and first visiting Costa Rica in 1998 on a surf exploration trip. Life took a fateful turn during a bachelor party trip to Costa Rica where he met his future wife Dayana, a native of Quepos. They married in 2007 and have two sons, Ethan and Liam. Matthew's passion for real estate is matched only by his love for the ocean. An avid surfer, water polo player, and ocean swimmer, he also enjoys running and capturing the beauty of life through water and aerial photography.`,
  "chris@2costaricarealestate.com": `Chris is a beach boy from California who has always loved the ocean. His dad taught him the art of fishing when he was very little, and when he learned freediving and spearfishing could be combined he was hooked. Chris got seriously into spearfishing while he lived in the Canary Islands, Spain from 1997 to 2013. Costa Rica was always on Chris's radar — since his mom is a tica, he has been visiting the country since he was very young and soon realized that one day he would call it his home. When the opportunity came, Chris sold everything and came to paradise to start a new life. Apart from being a real estate agent, Chris also owns a small successful beach hotel. He has also complemented his love for water sports with the hybrid discipline of triathlons, in which he competes consistently. "Living the dream" is definitely a common motto used to describe Chris's lifestyle in Costa Rica.`,
  "matt@2costaricarealestate.com": `A native Marylander, Matt attended Western State Colorado University where he received a B.A. in Business Administration with an emphasis on Hotel and Resort Management. After owning successful hospitality and design businesses and competing as a professional skier/snowboarder in Colorado, Matt moved to Costa Rica in 2006 and fell in love with the Southern Zone. After finding a rainforest mountain slated for timber harvest, he founded and created Finca Bellavista, the world's first master-planned sustainable treehouse community, which has been flourishing for almost twenty years. With an eye towards responsible development and environmental stewardship, Matt guides his clients with a keen sense for sustainable investments. He brings construction experience, a hospitality background, and a genuine care for the local community to every client relationship.`,
  "gene@2costaricarealestate.com": `Gene grew up on a small island off the coast of South Carolina. His love of surfing and all things ocean-related took him to San Diego, then back to the east coast where he worked in the restaurant industry as General Manager of some of Charleston's finest restaurants. In 1996 Gene and his wife opened a beach store deli that they operated for 8 years. They visited Costa Rica yearly and eventually realized they had to make it their home — as Gene has said, "I had an epiphany standing on a beach watching the waves." They sold their store and moved to Uvita, Costa Rica in 2006. Gene has since worked primarily as a home inspector, having inspected well over one hundred commercial and residential structures in the area, developing a very keen eye for property valuations and looking out for clients' best interests.`,
  "dopper@2costaricarealestate.com": `Born and raised in Key West, Florida, Dopper has a natural affinity for tropical climes and Latin culture. After visiting Costa Rica on spring break in college, his love affair with the country began. After 10 years of visits — some lasting up to 6 months — Dopper made Costa Rica his permanent home in 2003. He met his wife Karla, opened Ambrosia sandwich shop, and worked as a chef at the renowned local restaurant Agua Azul. He then became a partner in Vacation Buggy, a successful local tour company, becoming a well-known local guide. Dopper's many years in tourism, along with his knowledge accumulated through decades of life experience in Costa Rica, made a transition to real estate a natural evolution. He is dedicated to using his in-depth knowledge of Costa Rica's geography, lifestyle and culture to help others realize their dream of ownership in this unique country.`,
  "melsen@2crpapagayo.com": `I was born and raised in Guanacaste, Costa Rica. I moved to San Jose at the age of 20 to learn English at the Instituto Nacional de Aprendizaje, then moved back to Guanacaste. I worked at Reserva Conchal and Cafe Britt for around 4 years, then managed a Coffee and Gallery Shop in Playas del Coco. I graduated in Business Administration from Instituto Tecnológico de Costa Rica and worked with ICE for 8 years in the area of Cañas, Monteverde and Las Juntas. In 2022 I moved back to Playas del Coco and had the opportunity to open a Brazilian Jiu-Jitsu School for kids. I love sports — I work out at the gym, practice Brazilian Jiu Jitsu (7 years of experience), go to the beach, take walks in the mountains, and do MTB rides. I also have the habit of reading self-improvement books, always trying to be better in all areas of life.`,
  "maria@2costaricarealestate.com": `María Jiménez Bákit was born and raised in San José, Costa Rica. What began as a two-week quarantine trip to Jacó in 2020 turned into a life-changing decision — today, María and her family proudly call the Costa Rica Central Pacific Coast home. She holds a Business Degree from the University of Costa Rica and has co-founded multiple ventures, including a shipping company, a gym chain, and various businesses across sectors. With hands-on experience in vacation rentals, construction development, importing and exporting, and retail operations, María brings a solid entrepreneurial foundation to every project. She serves as a mentor with Vital Voices and is a board member of Junior Achievement Costa Rica. María specializes in luxury residential and commercial real estate, development land, and investment-focused opportunities, offering a deep understanding of how to navigate and succeed in Costa Rica's unique business landscape.`,
  "alvaro@2costaricarealestate.com": `Alvaro has been with 2 Costa Rica Real Estate for 4 years and has positioned himself as a very effective agent in the area of development properties in Escazú, Santa Ana and the surroundings of San Jose. He graduated from Texas Wesleyan University (1988–1992) with a Business Administration major emphasizing Marketing, and due to his golf ability was granted a full scholarship during his four years in college. His greatest asset in our business has been his public relations and his ability to connect the most influential developers, business people and decision-makers in Costa Rica with timely real estate opportunities. Well known for his golf career, Alvaro now leverages the relationships and contacts he has forged over decades into successful opportunities for buyers and sellers. Other than golf, his hobbies include aviation, traveling and sports in general.`,
  "andres@2costaricarealestate.com": `Andres Murillo was born and raised in San José, Costa Rica, and graduated from Universidad Latina with a double major in Business Administration and Marketing. At the age of 21, inspired by career opportunities and a significant uptick in ecotourism, Andres relocated to Playa Tamarindo where he began working with one of the region's most prolific developers, Grupo Diria. After working in property acquisitions, strategic development, permitting, and construction, Andres found his passion in Real Estate and has spent the last decade becoming one of the region's most reputable brokers. Specializing in over 100 kilometers of Guanacaste's Gold Coast, Andres has had one key focus: to create long-lasting relationships with his clients. In his personal time, Andres is a global citizen who has traveled the world to learn about cultures and surf some of the best waves in and out of Costa Rica.`,
  "jen@2crsantateresa.com": `Jennifer Harter is one of the most experienced and trusted real estate professionals in Santa Teresa, Costa Rica, known for her deep local knowledge, high ethical standards, and hands-on client representation. With years of on-the-ground experience in Santa Teresa and Mal País, Jennifer specializes in luxury homes, ocean-view properties, investment real estate, and income-producing developments. She works closely with both international and Costa Rican buyers, guiding them through every step of the process — from property selection and due diligence to negotiations and successful closings. What sets Jennifer apart is her professionalism, transparency, and long-term commitment to her clients. As president of the Nicoya Peninsula Waterkeepers and the Nicoya Peninsula Foundation, Jen works on projects that protect the environment, improve infrastructure, and strengthen community ties. Outside of real estate, you'll find her enjoying family life in Santa Teresa with her husband and three kids.`,
  "pourya@2crpapagayo.com": ``,
  "andrea@2crsantateresa.com": ``,
  "german@2crpapagayo.com": ``,
  "alonso@2costaricarealestate.com": ``,
  "mariel@2costaricarealestate.com": `Young, passionate and driven are three words to describe Mariel. She has lived in India where she volunteered in slums in Delhi, then learned Portuguese in Lisbon, Portugal. She studied Diplomacy and PR and has a strong background in social media and online marketing. Mariel is fluent in Spanish, English, Portuguese and Italian. She likes to travel to exotic destinations, scotch and wine tasting, and attend polo and philanthropy events in her free time.`,
};

// ═══════════════════════════════════════════
// LOAD BIO — instant, no API call needed
// ═══════════════════════════════════════════
function fetchCurrentBio(profileUrl) {
  const display = document.getElementById('current-bio-display');
  const bio = AGENT_BIOS[currentAgent.email];
  if (bio && bio.trim().length > 0) {
    display.innerHTML = `<p>${bio.replace(/\n\n/g,'</p><p>').replace(/\n/g,'<br>')}</p>`;
  } else {
    display.innerHTML = `<span class="bio-loading">No biography found in our system yet. <a href="${profileUrl}" target="_blank">Check your profile on the website ↗</a> and use it as your reference.</span>`;
  }
}

// ═══════════════════════════════════════════
// WORD COUNT
// ═══════════════════════════════════════════
function updateWordCount() {
  const text = document.getElementById('bio-textarea').value.trim();
  const words = text ? text.split(/\s+/).length : 0;
  const el = document.getElementById('char-count');
  el.textContent = `${words} word${words !== 1 ? 's' : ''}`;
  el.className = 'char-count' + (words > 500 ? ' warn' : '');
}

document.getElementById('bio-textarea').addEventListener('input', () => {
  updateWordCount();
  scheduleAutoSave();
});
document.getElementById('drive-link-input').addEventListener('input', scheduleAutoSave);

function scheduleAutoSave() {
  const ind = document.getElementById('save-indicator');
  ind.textContent = 'Saving…';
  ind.className = 'save-indicator saving';
  clearTimeout(autoSaveTimer);
  autoSaveTimer = setTimeout(async () => {
    try {
      await sbUpsert({
        email: currentAgent.email,
        name: currentAgent.name,
        bio: document.getElementById('bio-textarea').value,
        drive_link: document.getElementById('drive-link-input').value,
        submitted: false,
        updated_at: new Date().toISOString()
      });
      ind.textContent = '✓ Draft saved';
      ind.className = 'save-indicator saved';
    } catch(e) {
      ind.textContent = 'Save failed';
      ind.className = 'save-indicator';
    }
    setTimeout(() => { ind.textContent = ''; ind.className = 'save-indicator'; }, 2500);
  }, 1200);
}

// ═══════════════════════════════════════════
// MANUAL SAVE DRAFT
// ═══════════════════════════════════════════
document.getElementById('btn-save-draft').addEventListener('click', async () => {
  try {
    await sbUpsert({
      email: currentAgent.email,
      name: currentAgent.name,
      bio: document.getElementById('bio-textarea').value,
      drive_link: document.getElementById('drive-link-input').value,
      submitted: false,
      updated_at: new Date().toISOString()
    });
    showToast('Draft saved! You can come back and continue anytime.', 'success');
  } catch(e) {
    showToast('Could not save draft. Check your connection.', 'error');
  }
});

// ═══════════════════════════════════════════
// SUBMIT FLOW
// ═══════════════════════════════════════════
document.getElementById('btn-submit').addEventListener('click', () => {
  const bio = document.getElementById('bio-textarea').value.trim();
  const drive = document.getElementById('drive-link-input').value.trim();

  if (!bio || bio.split(/\s+/).length < 30) {
    showToast('Please write your biography (at least 30 words) before submitting.', 'error');
    return;
  }
  if (!drive || !drive.startsWith('https://')) {
    showToast('Please paste your Google Drive folder link before submitting.', 'error');
    return;
  }
  if (!drive.includes('drive.google.com')) {
    showToast('The link must be a Google Drive link (drive.google.com).', 'error');
    return;
  }

  // Show sharing reminder modal before submit confirm
  document.getElementById('sharing-reminder-modal').classList.add('open');
});

document.getElementById('btn-modal-cancel').addEventListener('click', () => {
  document.getElementById('submit-modal').classList.remove('open');
});

document.getElementById('btn-reminder-back').addEventListener('click', () => {
  document.getElementById('sharing-reminder-modal').classList.remove('open');
});

document.getElementById('btn-reminder-confirm').addEventListener('click', () => {
  document.getElementById('sharing-reminder-modal').classList.remove('open');
  document.getElementById('submit-modal').classList.add('open');
});

document.getElementById('btn-modal-confirm').addEventListener('click', async () => {
  const btn = document.getElementById('btn-modal-confirm');
  const cancelBtn = document.getElementById('btn-modal-cancel');
  const progress = document.getElementById('submit-progress');
  const progressFill = document.getElementById('submit-progress-fill');
  const statusText = document.getElementById('submit-status-text');

  btn.disabled = true;
  btn.innerHTML = '<span class="spinner"></span> Sending…';
  cancelBtn.style.display = 'none';
  progress.style.display = 'block';
  statusText.style.display = 'block';

  const bio = document.getElementById('bio-textarea').value.trim();
  const drive = document.getElementById('drive-link-input').value.trim();

  let prog = 0;
  const progInterval = setInterval(() => {
    prog = Math.min(prog + 3, 85);
    progressFill.style.width = prog + '%';
  }, 120);

  statusText.textContent = 'Saving to database…';

  try {
    // 1. Save to Supabase
    const submittedAt = new Date().toISOString();
    await sbUpsert({
      email:        currentAgent.email,
      name:         currentAgent.name,
      bio:          bio,
      drive_link:   drive,
      submitted:    true,
      submitted_at: submittedAt,
      updated_at:   submittedAt
    });

    statusText.textContent = 'Sending email notification…';

    // 2. Send email via EmailJS
    await emailjs.send('service_wkcvata', 'template_iuo4wk6', {
      agent_name:      currentAgent.name,
      agent_email:     currentAgent.email,
      submission_date: new Date().toLocaleString('en-US', { dateStyle: 'full', timeStyle: 'short' }),
      bio_text:        bio,
      drive_link:      drive,
      profile_url:     currentAgent.profileUrl,
    });

    clearInterval(progInterval);
    progressFill.style.width = '100%';
    statusText.textContent = 'Submitted successfully!';

    // Update local record
    agentRecord = { email: currentAgent.email, bio, drive_link: drive, submitted: true, submitted_at: new Date().toISOString() };

    setTimeout(() => {
      document.getElementById('submit-modal').classList.remove('open');
      showSubmittedState();
      showToast('Biography submitted! The marketing team has been notified.', 'success');
    }, 900);

  } catch(e) {
    clearInterval(progInterval);
    btn.disabled = false;
    btn.textContent = 'Yes, submit now';
    cancelBtn.style.display = '';
    progress.style.display = 'none';
    statusText.style.display = 'none';
    progressFill.style.width = '0%';
    console.error('EmailJS error:', e);
    showToast('Could not send email. Please try again or contact support.', 'error');
  }
});

// ═══════════════════════════════════════════
// SHOW/HIDE STATES
// ═══════════════════════════════════════════
function showEditState() {
  document.getElementById('bio-form-section').style.display = '';
  document.getElementById('photos-form-section').style.display = '';
  document.getElementById('action-bar').style.display = '';
  document.getElementById('submitted-overlay').style.display = 'none';
  document.getElementById('status-area').innerHTML = '<span class="status-badge draft"><span class="dot"></span> Draft in progress</span>';
}

function showSubmittedState() {
  document.getElementById('bio-form-section').style.display = 'none';
  document.getElementById('photos-form-section').style.display = 'none';
  document.getElementById('action-bar').style.display = 'none';
  document.getElementById('submitted-overlay').style.display = 'flex';
  document.getElementById('status-area').innerHTML = '<span class="status-badge submitted"><span class="dot"></span> Submitted ✓</span>';
  const bio = agentRecord ? agentRecord.bio : '';
  if (bio) {
    document.getElementById('current-bio-display').innerHTML =
      `<p style="font-size:0.82rem;font-weight:700;color:var(--forest);margin-bottom:10px">Your submitted biography:</p>` +
      `<p>${bio.replace(/\n/g,'<br>')}</p>`;
  }
}

// ═══════════════════════════════════════════
// LOGOUT
// ═══════════════════════════════════════════
document.getElementById('btn-logout').addEventListener('click', () => {
  currentAgent = null;
  agentRecord = null;
  document.getElementById('login-email').value = '';
  document.getElementById('login-password').value = '';
  document.getElementById('topbar-agent-name').textContent = '';
  document.getElementById('bio-textarea').value = '';
  document.getElementById('drive-link-input').value = '';
  showScreen('screen-login');
});

// ═══════════════════════════════════════════
// ADMIN PANEL
// ═══════════════════════════════════════════
const ADMIN = { email: 'admin@2costaricarealestate.com', password: 'admin2crre!' };

function openAdmin() {
  showScreen('screen-admin');
  document.getElementById('topbar-agent-name').textContent = 'Admin Dashboard';
  renderAdminDashboard();
}

async function renderAdminDashboard() {
  const tbody = document.getElementById('admin-table-body');
  tbody.innerHTML = '<tr><td colspan="6" style="text-align:center;padding:32px;color:var(--text-light)">Loading data from database…</td></tr>';

  // Load all submissions from Supabase
  let dbRecords = {};
  try {
    const rows = await sbGetAll();
    rows.forEach(r => { dbRecords[r.email] = r; });
  } catch(e) {
    tbody.innerHTML = '<tr><td colspan="6" style="text-align:center;color:#c0392b;padding:24px">Could not connect to database. Check your connection.</td></tr>';
    return;
  }

  const allAgents = Object.entries(AGENTS);
  let submitted = 0, pending = 0;
  let rows = '';

  const sorted = allAgents.sort((a, b) => {
    const aS = dbRecords[a[0]]?.submitted;
    const bS = dbRecords[b[0]]?.submitted;
    if (aS && !bS) return -1;
    if (!aS && bS) return 1;
    return a[1].name.localeCompare(b[1].name);
  });

  sorted.forEach(([email, agent]) => {
    const rec = dbRecords[email];
    const isSubmitted = rec?.submitted === true;
    const bio = rec?.bio || '';
    const drive = rec?.drive_link || '';
    const submittedAt = rec?.submitted_at
      ? new Date(rec.submitted_at).toLocaleString('en-US', { dateStyle: 'medium', timeStyle: 'short' })
      : '';
    const updatedAt = rec?.updated_at
      ? new Date(rec.updated_at).toLocaleString('en-US', { dateStyle: 'medium', timeStyle: 'short' })
      : '';

    if (isSubmitted) submitted++; else pending++;

    const office = email.includes('santateresa') ? 'Santa Teresa'
                 : email.includes('papagayo')    ? 'Papagayo'
                 : '2CRRE';

    const bioEsc = bio.replace(/'/g, "\\'").replace(/\n/g, ' ');

    rows += `<tr class="${isSubmitted ? 'row-submitted' : 'row-pending'}">
      <td><strong>${agent.name}</strong></td>
      <td class="td-office">${office}</td>
      <td style="font-size:0.76rem">${email}</td>
      <td>
        ${isSubmitted
          ? `<span class="badge-submitted">✓ Submitted</span>${submittedAt ? `<div class="sub-date">${submittedAt}</div>` : ''}`
          : rec
            ? `<span class="badge-pending">Draft saved</span><div class="sub-date">Last edit: ${updatedAt}</div>`
            : `<span class="badge-pending">Not started</span>`}
      </td>
      <td>
        ${isSubmitted && bio ? `<button class="btn-view-bio" onclick="viewBio('${email}')">View Bio</button>` : '—'}
      </td>
      <td>
        ${drive ? `<a class="btn-drive" href="${drive}" target="_blank">Open Drive ↗</a>` : '—'}
      </td>
    </tr>`;
  });

  tbody.innerHTML = rows;
  document.getElementById('admin-stat-submitted').textContent = submitted;
  document.getElementById('admin-stat-pending').textContent = pending;
  document.getElementById('admin-stat-total').textContent = allAgents.length;
  const pct = Math.round((submitted / allAgents.length) * 100);
  document.getElementById('admin-progress-fill').style.width = pct + '%';
  document.getElementById('admin-progress-pct').textContent = pct + '%';

  // Store records for viewBio
  window._dbRecords = dbRecords;
}

function viewBio(email) {
  const agent = AGENTS[email];
  const rec = window._dbRecords?.[email] || {};
  const bio = rec.bio || '';
  const drive = rec.drive_link || '';
  const date = rec.submitted_at ? new Date(rec.submitted_at).toLocaleString('en-US', { dateStyle: 'full', timeStyle: 'short' }) : '';
  document.getElementById('bio-modal-title').textContent = agent.name;
  document.getElementById('bio-modal-body').innerHTML =
    `${date ? `<p style="font-size:0.75rem;color:var(--text-light);margin-bottom:16px">Submitted: ${date}</p>` : ''}
     <div class="bio-modal-section"><h4>Biography</h4><p>${bio.replace(/\n/g,'<br>')}</p></div>
     <div class="bio-modal-section"><h4>Google Drive Photos</h4><a href="${drive}" target="_blank" class="drive-modal-link">${drive || 'No link provided'}</a></div>`;
  document.getElementById('bio-detail-modal').classList.add('open');
}

document.getElementById('btn-admin-logout').addEventListener('click', () => {
  currentAgent = null;
  agentRecord = null;
  document.getElementById('login-email').value = '';
  document.getElementById('login-password').value = '';
  document.getElementById('topbar-agent-name').textContent = '';
  showScreen('screen-login');
});

document.getElementById('admin-search').addEventListener('input', function() {
  const q = this.value.toLowerCase();
  document.querySelectorAll('#admin-table-body tr').forEach(row => {
    row.style.display = row.textContent.toLowerCase().includes(q) ? '' : 'none';
  });
});

document.getElementById('btn-export-csv').addEventListener('click', async () => {
  const btn = document.getElementById('btn-export-csv');
  btn.textContent = '⏳ Exporting…';
  btn.disabled = true;
  try {
    const rows = await sbGetAll();
    const dbRecords = {};
    rows.forEach(r => { dbRecords[r.email] = r; });

    const allAgents = Object.entries(AGENTS);
    let csv = 'Name,Email,Office,Status,Submitted Date,Drive Link\n';
    allAgents.forEach(([email, agent]) => {
      const rec = dbRecords[email];
      const isSubmitted = rec?.submitted === true;
      const drive = rec?.drive_link || '';
      const date = rec?.submitted_at
        ? new Date(rec.submitted_at).toLocaleString('en-US', { dateStyle: 'medium', timeStyle: 'short' })
        : '';
      const office = email.includes('santateresa') ? 'Santa Teresa'
                   : email.includes('papagayo')    ? 'Papagayo' : '2CRRE';
      csv += `"${agent.name}","${email}","${office}","${isSubmitted ? 'Submitted' : rec ? 'Draft' : 'Not started'}","${date}","${drive}"\n`;
    });
    const blob = new Blob([csv], { type: 'text/csv' });
    const a = document.createElement('a');
    a.href = URL.createObjectURL(blob);
    a.download = `bio-submissions-${new Date().toISOString().slice(0,10)}.csv`;
    a.click();
  } catch(e) {
    showToast('Could not export. Check connection.', 'error');
  }
  btn.textContent = '⬇ Export CSV';
  btn.disabled = false;
});

document.getElementById('bio-detail-modal').addEventListener('click', (e) => {
  if (e.target.id === 'close-bio-modal' || e.target === e.currentTarget) {
    document.getElementById('bio-detail-modal').classList.remove('open');
  }
});
</script>
<!-- ══════════════════════════════════════ -->
<!-- SCREEN: ADMIN DASHBOARD                -->
<!-- ══════════════════════════════════════ -->
<div id="screen-admin" class="screen">
  <div class="admin-wrap">

    <!-- STATS ROW -->
    <div class="admin-stats">
      <div class="stat-card stat-green">
        <div class="stat-num" id="admin-stat-submitted">0</div>
        <div class="stat-label">Submitted</div>
      </div>
      <div class="stat-card stat-orange">
        <div class="stat-num" id="admin-stat-pending">0</div>
        <div class="stat-label">Pending</div>
      </div>
      <div class="stat-card stat-teal">
        <div class="stat-num" id="admin-stat-total">0</div>
        <div class="stat-label">Total Agents</div>
      </div>
      <div class="stat-card stat-progress-card">
        <div class="stat-label" style="margin-bottom:10px">Overall Progress <span id="admin-progress-pct" style="color:var(--green);font-weight:700">0%</span></div>
        <div class="admin-progress-bar"><div class="admin-progress-fill" id="admin-progress-fill"></div></div>
      </div>
    </div>

    <!-- TOOLBAR -->
    <div class="admin-toolbar">
      <input type="text" id="admin-search" placeholder="Search by name, email or office…" class="admin-search">
      <div class="admin-toolbar-right">
        <button class="btn-export-csv" id="btn-export-csv">⬇ Export CSV</button>
        <button class="btn-admin-logout" id="btn-admin-logout">Sign Out</button>
      </div>
    </div>

    <!-- TABLE -->
    <div class="admin-table-wrap">
      <table class="admin-table">
        <thead>
          <tr>
            <th>Agent Name</th>
            <th>Office</th>
            <th>Email</th>
            <th>Status</th>
            <th>Biography</th>
            <th>Photos</th>
          </tr>
        </thead>
        <tbody id="admin-table-body"></tbody>
      </table>
    </div>

  </div>
</div>

<!-- BIO DETAIL MODAL -->
<div class="modal-backdrop" id="bio-detail-modal">
  <div class="modal" style="max-width:640px;max-height:80vh;overflow-y:auto">
    <h3 id="bio-modal-title"></h3>
    <div id="bio-modal-body"></div>
    <div class="modal-actions" style="margin-top:20px">
      <button class="btn-cancel" id="close-bio-modal">Close</button>
    </div>
  </div>
</div>

<style>
/* ── ADMIN SCREEN ───────────────────────── */
#screen-admin { background: var(--cream); padding: 32px; flex-direction: column; gap: 24px; }
.admin-wrap { max-width: 1100px; margin: 0 auto; width: 100%; display: flex; flex-direction: column; gap: 22px; }

.admin-stats { display: grid; grid-template-columns: repeat(4, 1fr); gap: 16px; }
.stat-card { background: white; border: 1.5px solid var(--border); border-radius: 10px; padding: 20px 22px; display: flex; flex-direction: column; gap: 4px; }
.stat-num { font-size: 2.4rem; font-weight: 700; line-height: 1; }
.stat-label { font-size: 0.72rem; text-transform: uppercase; letter-spacing: 0.08em; color: var(--text-light); font-weight: 600; }
.stat-green .stat-num { color: var(--green); }
.stat-orange .stat-num { color: #e67e22; }
.stat-teal .stat-num { color: var(--forest); }
.stat-progress-card { justify-content: center; }
.admin-progress-bar { height: 8px; background: var(--border); border-radius: 4px; overflow: hidden; }
.admin-progress-fill { height: 100%; background: linear-gradient(90deg, var(--forest-mid), var(--green)); border-radius: 4px; transition: width 0.5s ease; }

.admin-toolbar { display: flex; align-items: center; gap: 12px; justify-content: space-between; }
.admin-search { flex: 1; max-width: 360px; padding: 10px 14px; border: 1.5px solid var(--border); border-radius: 6px; font-family: 'Montserrat', sans-serif; font-size: 0.85rem; background: white; }
.admin-search:focus { outline: none; border-color: var(--forest-mid); }
.admin-toolbar-right { display: flex; gap: 10px; }
.btn-export-csv { padding: 9px 18px; background: var(--forest); color: white; border: none; border-radius: 6px; font-family: 'Montserrat', sans-serif; font-size: 0.78rem; font-weight: 700; cursor: pointer; letter-spacing: 0.04em; transition: background 0.2s; }
.btn-export-csv:hover { background: var(--forest-light); }
.btn-admin-logout { padding: 9px 16px; background: transparent; border: 1.5px solid var(--border); border-radius: 6px; font-family: 'Montserrat', sans-serif; font-size: 0.78rem; font-weight: 600; color: var(--text-mid); cursor: pointer; }

.admin-table-wrap { background: white; border: 1.5px solid var(--border); border-radius: 10px; overflow: hidden; }
.admin-table { width: 100%; border-collapse: collapse; font-size: 0.82rem; }
.admin-table th { background: var(--forest); color: white; padding: 11px 14px; text-align: left; font-size: 0.7rem; text-transform: uppercase; letter-spacing: 0.08em; font-weight: 600; }
.admin-table td { padding: 11px 14px; border-bottom: 1px solid var(--border); vertical-align: middle; }
.admin-table tr:last-child td { border-bottom: none; }
.row-submitted td { background: #f6fdf7; }
.row-pending:hover td { background: #fafafa; }
.td-office { font-size: 0.7rem; text-transform: uppercase; letter-spacing: 0.05em; color: var(--text-light); font-weight: 600; }
.badge-submitted { display: inline-flex; align-items: center; gap: 5px; background: rgba(122,185,66,0.15); color: #4a8a1a; border: 1px solid rgba(122,185,66,0.3); padding: 3px 9px; border-radius: 4px; font-size: 0.7rem; font-weight: 700; text-transform: uppercase; letter-spacing: 0.05em; }
.badge-pending { display: inline-flex; align-items: center; background: rgba(230,126,34,0.12); color: #c0611a; border: 1px solid rgba(230,126,34,0.25); padding: 3px 9px; border-radius: 4px; font-size: 0.7rem; font-weight: 700; text-transform: uppercase; letter-spacing: 0.05em; }
.sub-date { font-size: 0.68rem; color: var(--text-light); margin-top: 3px; }
.btn-view-bio { padding: 5px 12px; background: var(--forest); color: white; border: none; border-radius: 4px; font-family: 'Montserrat', sans-serif; font-size: 0.72rem; font-weight: 600; cursor: pointer; transition: background 0.2s; }
.btn-view-bio:hover { background: var(--forest-light); }
.btn-drive { padding: 5px 12px; background: var(--green); color: white; border-radius: 4px; font-family: 'Montserrat', sans-serif; font-size: 0.72rem; font-weight: 600; text-decoration: none; display: inline-block; transition: background 0.2s; }
.btn-drive:hover { background: var(--green-light); }

.bio-modal-section { margin-bottom: 20px; }
.bio-modal-section h4 { font-size: 0.72rem; font-weight: 700; text-transform: uppercase; letter-spacing: 0.08em; color: var(--forest); margin-bottom: 10px; }
.bio-modal-section p { font-size: 0.85rem; line-height: 1.7; color: var(--text-mid); }
.drive-modal-link { color: var(--forest-light); font-size: 0.85rem; word-break: break-all; }

@media (max-width: 768px) {
  #screen-admin { padding: 16px; }
  .admin-stats { grid-template-columns: repeat(2, 1fr); }
  .admin-table { font-size: 0.75rem; }
  .admin-toolbar { flex-direction: column; align-items: stretch; }
  .admin-search { max-width: 100%; }
}
</style>

</body>
</html>
