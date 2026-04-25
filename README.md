<html><head><style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  #app {
    padding: 1rem 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    background: #0a0a0a;
    color: #e8e8e8;
    min-height: 100vh;
    border-radius: 12px;
  }

  .hero { margin-bottom: 1.25rem; }
  .level-badge { display: inline-flex; align-items: center; gap: 6px; background: #1a1a1a; color: #FAC775; padding: 4px 12px; border-radius: 999px; font-size: 12px; font-weight: 500; margin-bottom: 10px; border: 1px solid #2a2a2a; }
  .player-name { font-size: 22px; font-weight: 500; color: #f0f0f0; margin-bottom: 4px; }
  .xp-row { display: flex; align-items: center; gap: 10px; margin-bottom: 4px; }
  .xp-bar-wrap { flex: 1; height: 8px; background: #1a1a1a; border-radius: 999px; border: 1px solid #2a2a2a; overflow: hidden; }
  .xp-bar-fill { height: 100%; border-radius: 999px; background: #EF9F27; transition: width 0.5s cubic-bezier(.4,0,.2,1); }
  .xp-label { font-size: 12px; color: #888; min-width: 90px; text-align: right; }
  .level-hint { font-size: 13px; color: #666; }

  .stats-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; margin-bottom: 1.25rem; }
  .stat-card { background: #111; border: 1px solid #222; border-radius: 10px; padding: 10px 12px; }
  .stat-label { font-size: 11px; color: #555; margin-bottom: 2px; }
  .stat-val { font-size: 20px; font-weight: 500; color: #f0f0f0; }

  .tabs { display: flex; border-bottom: 1px solid #222; margin-bottom: 1.25rem; }
  .tab-btn { background: transparent; border: none; border-bottom: 2px solid transparent; padding: 8px 14px; font-size: 13px; font-weight: 500; color: #555; cursor: pointer; font-family: inherit; transition: color 0.15s, border-color 0.15s; margin-bottom: -1px; }
  .tab-btn.active { color: #f0f0f0; border-bottom-color: #EF9F27; }
  .tab-btn:hover:not(.active) { color: #aaa; }
  .tab-count { display: inline-flex; align-items: center; justify-content: center; background: #1e3a0f; color: #7ec845; border-radius: 999px; font-size: 10px; font-weight: 500; min-width: 16px; height: 16px; padding: 0 4px; margin-left: 5px; }

  .tab-panel { display: none; }
  .tab-panel.active { display: block; }

  .section-head { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; }
  .section-title { font-size: 13px; font-weight: 500; color: #666; }

  .daily-banner { background: #111; border-radius: 10px; padding: 10px 14px; display: flex; align-items: center; gap: 10px; margin-bottom: 12px; border: 1px solid #222; }
  .daily-label { font-size: 13px; color: #888; flex: 1; }
  .daily-label strong { color: #e0e0e0; font-weight: 500; }

  .add-btn { display: flex; align-items: center; gap: 4px; background: transparent; border: 1px solid #2a2a2a; border-radius: 8px; padding: 5px 10px; font-size: 12px; color: #888; cursor: pointer; font-family: inherit; transition: background 0.15s, color 0.15s; }
  .add-btn:hover { background: #1a1a1a; color: #ccc; }

  .habits-list { display: flex; flex-direction: column; gap: 8px; margin-bottom: 1rem; }

  .habit-card { background: #111; border: 1px solid #222; border-radius: 12px; padding: 13px 14px; display: flex; align-items: center; gap: 12px; cursor: pointer; transition: border-color 0.15s, background 0.15s; user-select: none; }
  .habit-card:hover { border-color: #333; background: #161616; }
  .habit-card:active { transform: scale(0.99); }
  .habit-card.daily-card { border-left: 2px solid #EF9F27; }
  .habit-card.special-card { border: 1px solid #5a3a00; background: #110d00; position: relative; overflow: hidden; }
  .habit-card.special-card::before { content: ''; position: absolute; inset: 0; background: linear-gradient(135deg, rgba(250,199,117,0.04) 0%, transparent 60%); pointer-events: none; }
  .habit-card.special-card:hover { border-color: #7a5200; background: #160f00; }

  .completed-card { background: #0e0e0e; border: 1px solid #1a1a1a; border-radius: 12px; padding: 13px 14px; display: flex; align-items: center; gap: 12px; opacity: 0.55; }
  .completed-card.daily-card { border-left: 2px solid #2a5010; }
  .completed-card.special-done { border: 1px solid #3a2500; }
  .locked-card { background: #0d0d0d; border: 1px solid #1a1a1a; border-radius: 12px; padding: 13px 14px; display: flex; align-items: center; gap: 12px; opacity: 0.45; cursor: not-allowed; }

  .check-indicator { width: 22px; height: 22px; flex-shrink: 0; border-radius: 50%; border: 1.5px solid #333; display: flex; align-items: center; justify-content: center; font-size: 12px; color: transparent; pointer-events: none; }
  .special-card .check-indicator { border-color: #5a3a00; }
  .check-done { width: 22px; height: 22px; flex-shrink: 0; border-radius: 50%; background: #2a5010; border: 1.5px solid #3a6a18; display: flex; align-items: center; justify-content: center; font-size: 12px; color: #7ec845; }
  .check-done.special { background: #5a3a00; border-color: #8a5a00; color: #FAC775; }
  .lock-icon { width: 22px; height: 22px; flex-shrink: 0; display: flex; align-items: center; justify-content: center; font-size: 14px; }

  .habit-info { flex: 1; min-width: 0; pointer-events: none; }
  .habit-name { font-size: 14px; font-weight: 500; color: #e8e8e8; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
  .habit-name.special { color: #FAC775; }
  .habit-name.struck { text-decoration: line-through; color: #444; }
  .habit-meta { font-size: 11px; color: #555; margin-top: 2px; }
  .habit-meta.special { color: #8a6020; }
  .habit-meta.locked { color: #333; }

  .xp-pill { display: flex; align-items: center; background: #1a1400; border: 1px solid #2a2000; border-radius: 999px; padding: 3px 8px; font-size: 11px; font-weight: 500; color: #c88a10; white-space: nowrap; pointer-events: none; }
  .xp-pill.daily { background: #1a1000; border-color: #2a1800; color: #d4891a; }
  .xp-pill.earned { background: #0e1a08; border-color: #1a2e10; color: #5ea830; }
  .xp-pill.special { background: #2a1800; border-color: #5a3a00; color: #FAC775; font-weight: 600; }
  .xp-pill.locked-pill { background: #111; border-color: #1a1a1a; color: #333; }

  .delete-btn { background: transparent; border: none; cursor: pointer; color: #444; font-size: 13px; padding: 4px 6px; border-radius: 4px; transition: color 0.15s; font-family: inherit; line-height: 1; }
  .delete-btn:hover { color: #c0392b; }

  .add-form { background: #111; border: 1px solid #222; border-radius: 12px; padding: 14px; margin-bottom: 1rem; display: none; flex-direction: column; gap: 10px; }
  .add-form.open { display: flex; }
  .form-row { display: flex; gap: 8px; align-items: center; flex-wrap: wrap; }
  .form-row input, .form-row select { flex: 1; min-width: 100px; padding: 7px 10px; font-size: 13px; border-radius: 8px; border: 1px solid #2a2a2a; background: #0a0a0a; color: #e8e8e8; font-family: inherit; }
  .form-row input::placeholder { color: #444; }
  .form-row select option { background: #111; color: #e8e8e8; }
  .submit-btn { background: #FAC775; color: #1a0e00; border: none; border-radius: 8px; padding: 7px 14px; font-size: 13px; font-weight: 600; cursor: pointer; font-family: inherit; transition: opacity 0.15s; }
  .submit-btn:hover { opacity: 0.85; }
  .cancel-btn { background: transparent; border: 1px solid #2a2a2a; border-radius: 8px; padding: 7px 12px; font-size: 13px; color: #888; cursor: pointer; font-family: inherit; transition: background 0.15s; }
  .cancel-btn:hover { background: #1a1a1a; }

  .daily-progress { display: flex; align-items: center; gap: 10px; margin-bottom: 10px; }
  .dp-bar-wrap { flex: 1; height: 6px; background: #1a1a1a; border-radius: 999px; overflow: hidden; }
  .dp-bar-fill { height: 100%; border-radius: 999px; background: #EF9F27; transition: width 0.4s ease; }
  .dp-label { font-size: 12px; color: #666; white-space: nowrap; }

  .streak-hint { font-size: 12px; color: #555; margin-bottom: 10px; padding: 8px 12px; background: #111; border-radius: 8px; border: 1px solid #1e1e1e; }
  .streak-hint.active { color: #7ec845; background: #0d1a08; border-color: #1e3a10; }

  .milestone-banner { background: linear-gradient(135deg, #1a0f00 0%, #110a00 100%); border: 1px solid #5a3a00; border-radius: 10px; padding: 10px 14px; margin-bottom: 14px; display: flex; align-items: center; gap: 10px; }
  .milestone-banner .mb-icon { font-size: 18px; }
  .milestone-banner .mb-text { font-size: 13px; color: #c88a10; flex: 1; }
  .milestone-banner .mb-text strong { color: #FAC775; }

  .subsection-label { font-size: 11px; color: #444; font-weight: 500; text-transform: uppercase; letter-spacing: 0.05em; margin: 14px 0 8px; }

  .empty-state { font-size: 13px; color: #444; padding: 24px 0; text-align: center; }

  /* ── SYSTEM NOTIFICATION ── */
  .notif-stack {
    position: fixed; top: 16px; right: 16px;
    display: flex; flex-direction: column; gap: 10px;
    z-index: 9999; pointer-events: none;
    width: 300px;
  }
  .notif {
    background: #1c1c1e;
    border: 1px solid #3a3a3c;
    border-radius: 14px;
    padding: 12px 14px;
    display: flex; align-items: flex-start; gap: 10px;
    box-shadow: 0 8px 32px rgba(0,0,0,0.7), 0 0 0 0.5px rgba(255,255,255,0.05);
    pointer-events: all;
    opacity: 0;
    transform: translateX(calc(100% + 20px));
    transition: opacity 0.35s cubic-bezier(.4,0,.2,1), transform 0.35s cubic-bezier(.4,0,.2,1);
    cursor: pointer;
    position: relative;
    overflow: hidden;
  }
  .notif::before {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(250,199,117,0.07) 0%, transparent 55%);
    pointer-events: none;
  }
  .notif.show {
    opacity: 1;
    transform: translateX(0);
  }
  .notif.hide {
    opacity: 0;
    transform: translateX(calc(100% + 20px));
  }
  .notif-progress {
    position: absolute; bottom: 0; left: 0; height: 2px;
    background: #EF9F27; border-radius: 0 0 0 14px;
    transition: width linear;
  }
  .notif-icon-wrap {
    width: 36px; height: 36px; flex-shrink: 0;
    background: #2a1800; border: 1px solid #5a3a00;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 18px;
  }
  .notif-icon-wrap.levelup {
    background: #1a1400; border-color: #4a3800;
  }
  .notif-body { flex: 1; min-width: 0; }
  .notif-app { font-size: 10px; color: #666; font-weight: 500; text-transform: uppercase; letter-spacing: 0.06em; margin-bottom: 2px; }
  .notif-title { font-size: 13px; font-weight: 600; color: #FAC775; margin-bottom: 2px; line-height: 1.3; }
  .notif-title.levelup { color: #f0f0f0; }
  .notif-desc { font-size: 12px; color: #888; line-height: 1.4; }
  .notif-xp { display: inline-block; background: #2a1800; border: 1px solid #5a3a00; border-radius: 999px; padding: 1px 7px; font-size: 11px; font-weight: 600; color: #FAC775; margin-top: 4px; }
  .notif-xp.levelup { background: #1a1400; border-color: #4a3800; color: #EF9F27; }

  /* simple bottom toast for streak/bonus */
  .toast-simple { position: fixed; bottom: 24px; left: 50%; transform: translateX(-50%) translateY(10px); background: #1c1c1e; border: 1px solid #333; color: #e8e8e8; padding: 9px 18px; border-radius: 999px; font-size: 13px; font-weight: 500; opacity: 0; pointer-events: none; transition: opacity 0.25s, transform 0.25s; z-index: 9998; white-space: nowrap; box-shadow: 0 4px 20px rgba(0,0,0,0.5); }
  .toast-simple.show { opacity: 1; transform: translateX(-50%) translateY(0); }
</style>

</head><body><div id="app">
  <div style="padding: 0 1rem;">
  <div class="hero">
    <div class="level-badge"><span id="level-icon">⚔</span> Level <span id="level-num">1</span></div>
    <div class="player-name" id="player-title">Novice Adventurer</div>
    <div class="xp-row">
      <div class="xp-bar-wrap"><div class="xp-bar-fill" id="xp-fill" style="width: 12%;"></div></div>
      <div class="xp-label"><span id="cur-xp">60</span> / <span id="max-xp">500</span> XP</div>
    </div>
    <div class="level-hint" id="level-hint">440 XP until Apprentice</div>
  </div>

  <div class="stats-grid">
    <div class="stat-card"><div class="stat-label">Total XP</div><div class="stat-val" id="total-xp">60</div></div>
    <div class="stat-card"><div class="stat-label">Done today</div><div class="stat-val" id="done-today">6</div></div>
    <div class="stat-card"><div class="stat-label">Streak</div><div class="stat-val" id="streak-stat">1 🔥</div></div>
  </div>

  <div class="tabs">
    <button class="tab-btn active" onclick="switchTab('quests')">Quests</button>
    <button class="tab-btn" onclick="switchTab('daily')">Daily</button>
    <button class="tab-btn" onclick="switchTab('special')">Special ✨</button>
    <button class="tab-btn" id="completed-tab-btn" onclick="switchTab('completed')">Completed <span class="tab-count">6</span></button>
  </div>

  <div class="tab-panel active" id="tab-quests">
    <div class="section-head">
      <div class="section-title">My habits</div>
      <button class="add-btn" onclick="openForm('habit')">+ Add habit</button>
    </div>
    <div class="add-form" id="habit-form">
      <div class="form-row">
        <input type="text" id="habit-input" placeholder="Habit name..." maxlength="40">
        <select id="habit-xp-select">
          <option value="3">3 XP — Easy</option>
          <option value="5" selected="">5 XP — Medium</option>
          <option value="10">10 XP — Hard</option>
          <option value="20">20 XP — Epic</option>
        </select>
      </div>
      <div class="form-row" style="justify-content: flex-end;">
        <button class="cancel-btn" onclick="closeForm('habit')">Cancel</button>
        <button class="submit-btn" onclick="submitHabit()">Add quest</button>
      </div>
    </div>
    <div class="habits-list" id="habits-list"><div class="empty-state">All habits done! Check the Completed tab.</div></div>
  </div>

  <div class="tab-panel" id="tab-daily">
    <div class="daily-banner">
      <div class="daily-label">📅 Complete <strong>all daily quests</strong> to grow your streak and earn a <strong>+20 XP bonus!</strong></div>
    </div>
    <div class="daily-progress">
      <div class="dp-bar-wrap"><div class="dp-bar-fill" id="daily-fill" style="width: 100%;"></div></div>
      <div class="dp-label" id="daily-progress-label">3 / 3 done</div>
    </div>
    <div id="streak-hint" class="streak-hint active">🔥 All daily quests done! Streak: 1 day.</div>
    <div class="section-head" style="margin-top:10px;">
      <div class="section-title">Today's daily quests</div>
      <button class="add-btn" onclick="openForm('daily')">+ Add daily</button>
    </div>
    <div class="add-form" id="daily-form">
      <div class="form-row">
        <input type="text" id="daily-input" placeholder="Daily quest name..." maxlength="40">
        <select id="daily-xp-select">
          <option value="3">3 XP — Easy</option>
          <option value="7" selected="">7 XP — Medium</option>
          <option value="12">12 XP — Hard</option>
          <option value="20">20 XP — Epic</option>
        </select>
      </div>
      <div class="form-row" style="justify-content: flex-end;">
        <button class="cancel-btn" onclick="closeForm('daily')">Cancel</button>
        <button class="submit-btn" onclick="submitDaily()">Add daily quest</button>
      </div>
    </div>
    <div class="habits-list" id="daily-list"></div>
  </div>

  <div class="tab-panel" id="tab-special">
    <div id="special-milestone-banner"><div class="milestone-banner"><span class="mb-icon">🔒</span><div class="mb-text">Reach <strong>Level 2</strong> to unlock <strong>Iron Will</strong></div></div></div>
    <div class="habits-list" id="special-list"><div class="habit-card special-card" onclick="completeSpecial('s1')">
      <div style="font-size:20px;flex-shrink:0;">🌅</div>
      <div class="habit-info">
        <div class="habit-name special">Dawn of a Hero</div>
        <div class="habit-meta special">Complete your first habit streak of 3 days</div>
      </div>
      <div class="xp-pill special">+150 XP</div>
    </div><div class="subsection-label">Locked quests</div><div class="locked-card"><div class="lock-icon">🔒</div><div class="habit-info"><div class="habit-name" style="color:#333;">Iron Will</div><div class="habit-meta locked">Unlocks at Level 2</div></div><div class="xp-pill locked-pill">+400 XP</div></div><div class="locked-card"><div class="lock-icon">🔒</div><div class="habit-info"><div class="habit-name" style="color:#333;">The Consistent One</div><div class="habit-meta locked">Unlocks at Level 3</div></div><div class="xp-pill locked-pill">+800 XP</div></div><div class="locked-card"><div class="lock-icon">🔒</div><div class="habit-info"><div class="habit-name" style="color:#333;">Warrior's Oath</div><div class="habit-meta locked">Unlocks at Level 4</div></div><div class="xp-pill locked-pill">+500 XP</div></div><div class="locked-card"><div class="lock-icon">🔒</div><div class="habit-info"><div class="habit-name" style="color:#333;">Champion's Trial</div><div class="habit-meta locked">Unlocks at Level 5</div></div><div class="xp-pill locked-pill">+1,000 XP</div></div><div class="locked-card"><div class="lock-icon">🔒</div><div class="habit-info"><div class="habit-name" style="color:#333;">The Veteran's Code</div><div class="habit-meta locked">Unlocks at Level 6</div></div><div class="xp-pill locked-pill">+2,000 XP</div></div><div class="locked-card"><div class="lock-icon">🔒</div><div class="habit-info"><div class="habit-name" style="color:#333;">Hero's Journey</div><div class="habit-meta locked">Unlocks at Level 7</div></div><div class="xp-pill locked-pill">+3,000 XP</div></div><div class="locked-card"><div class="lock-icon">🔒</div><div class="habit-info"><div class="habit-name" style="color:#333;">Legend's Mantle</div><div class="habit-meta locked">Unlocks at Level 8</div></div><div class="xp-pill locked-pill">+5,000 XP</div></div><div class="locked-card"><div class="lock-icon">🔒</div><div class="habit-info"><div class="habit-name" style="color:#333;">Mythic Discipline</div><div class="habit-meta locked">Unlocks at Level 9</div></div><div class="xp-pill locked-pill">+8,000 XP</div></div><div class="locked-card"><div class="lock-icon">🔒</div><div class="habit-info"><div class="habit-name" style="color:#333;">Ascendant</div><div class="habit-meta locked">Unlocks at Level 10</div></div><div class="xp-pill locked-pill">+10,000 XP</div></div></div>
  </div>

  <div class="tab-panel" id="tab-completed">
    <div class="habits-list" id="completed-list">
    <div class="completed-card daily-card">
      <div class="check-done">✓</div>
      <div class="habit-info"><div class="habit-name struck">Evening reflection</div><div class="habit-meta">Daily quest</div></div>
      <div class="xp-pill earned">+7 XP</div>
    </div>
    <div class="completed-card daily-card">
      <div class="check-done">✓</div>
      <div class="habit-info"><div class="habit-name struck">Complete 3 habits</div><div class="habit-meta">Daily quest</div></div>
      <div class="xp-pill earned">+12 XP</div>
    </div>
    <div class="completed-card daily-card">
      <div class="check-done">✓</div>
      <div class="habit-info"><div class="habit-name struck">Log in and check quests</div><div class="habit-meta">Daily quest</div></div>
      <div class="xp-pill earned">+3 XP</div>
    </div>
    <div class="completed-card">
      <div class="check-done">✓</div>
      <div class="habit-info"><div class="habit-name struck">Drink 8 glasses of water</div><div class="habit-meta">Habit</div></div>
      <div class="xp-pill earned">+3 XP</div>
    </div>
    <div class="completed-card">
      <div class="check-done">✓</div>
      <div class="habit-info"><div class="habit-name struck">Read for 20 minutes</div><div class="habit-meta">Habit</div></div>
      <div class="xp-pill earned">+5 XP</div>
    </div>
    <div class="completed-card">
      <div class="check-done">✓</div>
      <div class="habit-info"><div class="habit-name struck">Morning workout</div><div class="habit-meta">Habit</div></div>
      <div class="xp-pill earned">+10 XP</div>
    </div></div>
  </div>
  </div>
</div>

<div class="notif-stack" id="notif-stack"></div>
<div class="toast-simple" id="toast-simple">🔥 Streak is now 1! +20 bonus XP!</div>

<script>
const LEVELS = [
  {lvl:1,  xp:0,     title:"Novice Adventurer", icon:"⚔"},
  {lvl:2,  xp:500,   title:"Apprentice",         icon:"🗡"},
  {lvl:3,  xp:1200,  title:"Scout",              icon:"🏹"},
  {lvl:4,  xp:2500,  title:"Warrior",            icon:"🛡"},
  {lvl:5,  xp:4500,  title:"Champion",           icon:"⚡"},
  {lvl:6,  xp:7500,  title:"Veteran",            icon:"🔥"},
  {lvl:7,  xp:12000, title:"Hero",               icon:"✨"},
  {lvl:8,  xp:18000, title:"Legend",             icon:"👑"},
  {lvl:9,  xp:27000, title:"Mythic",             icon:"🌟"},
  {lvl:10, xp:40000, title:"Ascendant",          icon:"💎"},
];

const SPECIAL_QUESTS = [
  {id:'s1', name:'Dawn of a Hero',       desc:'Complete your first habit streak of 3 days',  xp:150,  unlockLvl:1,  icon:'🌅'},
  {id:'s2', name:'Iron Will',            desc:'Complete every habit for 7 days in a row',     xp:400,  unlockLvl:2,  icon:'🏋️'},
  {id:'s3', name:'The Consistent One',   desc:'Log in and complete dailies 14 days straight', xp:800,  unlockLvl:3,  icon:'📅'},
  {id:'s4', name:"Warrior's Oath",       desc:'Earn 1,000 total XP',                          xp:500,  unlockLvl:4,  icon:'⚔️', xpGoal:1000},
  {id:'s5', name:"Champion's Trial",     desc:'Complete 50 total tasks',                      xp:1000, unlockLvl:5,  icon:'🏆', taskGoal:50},
  {id:'s6', name:"The Veteran's Code",   desc:'Reach a 30-day streak',                        xp:2000, unlockLvl:6,  icon:'🔥', streakGoal:30},
  {id:'s7', name:"Hero's Journey",       desc:'Earn 5,000 total XP',                          xp:3000, unlockLvl:7,  icon:'✨', xpGoal:5000},
  {id:'s8', name:"Legend's Mantle",      desc:'Complete 200 total tasks',                     xp:5000, unlockLvl:8,  icon:'👑', taskGoal:200},
  {id:'s9', name:'Mythic Discipline',    desc:'Reach a 100-day streak',                       xp:8000, unlockLvl:9,  icon:'🌟', streakGoal:100},
  {id:'s10',name:'Ascendant',            desc:'Reach level 10 — you have mastered yourself',  xp:10000,unlockLvl:10, icon:'💎'},
];

let state = {
  totalXp:0, streak:0, streakAwardedToday:false, totalTasksDone:0,
  habits:[
    {id:1,name:"Morning workout",xp:10,done:false},
    {id:2,name:"Read for 20 minutes",xp:5,done:false},
    {id:3,name:"Drink 8 glasses of water",xp:3,done:false},
  ],
  dailies:[
    {id:101,name:"Log in and check quests",xp:3,done:false},
    {id:102,name:"Complete 3 habits",xp:12,done:false},
    {id:103,name:"Evening reflection",xp:7,done:false},
  ],
  specials: JSON.parse(JSON.stringify(SPECIAL_QUESTS)),
  completed:[], nextId:200,
};

/* ── Notification system ── */
let notifQueue = [];
let notifShowing = false;

function pushNotif(data) {
  notifQueue.push(data);
  if (!notifShowing) drainNotifQueue();
}

function drainNotifQueue() {
  if (!notifQueue.length) { notifShowing = false; return; }
  notifShowing = true;
  const data = notifQueue.shift();
  showNotif(data, () => setTimeout(drainNotifQueue, 200));
}

function showNotif(data, onDone) {
  const stack = document.getElementById('notif-stack');
  const el = document.createElement('div');
  el.className = 'notif';
  const duration = data.duration || 4000;
  const isLevel = data.type === 'level';

  el.innerHTML = `
    <div class="notif-icon-wrap${isLevel?' levelup':''}">${data.icon}</div>
    <div class="notif-body">
      <div class="notif-app">Quest Tracker</div>
      <div class="notif-title${isLevel?' levelup':''}">${data.title}</div>
      <div class="notif-desc">${data.desc}</div>
      ${data.xp ? `<div class="notif-xp${isLevel?' levelup':''}">+${data.xp.toLocaleString()} XP</div>` : ''}
    </div>
    <div class="notif-progress" id="np-${Date.now()}"></div>
  `;
  stack.appendChild(el);

  // Animate in
  requestAnimationFrame(() => {
    requestAnimationFrame(() => { el.classList.add('show'); });
  });

  // Progress bar
  const bar = el.querySelector('.notif-progress');
  bar.style.width = '100%';
  bar.style.transitionDuration = '0ms';
  setTimeout(() => {
    bar.style.transitionDuration = duration + 'ms';
    bar.style.width = '0%';
  }, 50);

  // Dismiss on click
  el.addEventListener('click', () => dismiss());

  const timer = setTimeout(() => dismiss(), duration);

  function dismiss() {
    clearTimeout(timer);
    el.classList.remove('show');
    el.classList.add('hide');
    setTimeout(() => { el.remove(); onDone && onDone(); }, 400);
  }
}

function showSimpleToast(msg) {
  const t = document.getElementById('toast-simple');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 2500);
}

/* ── Level / XP helpers ── */
function getLevelData(xp) {
  let cur = LEVELS[0];
  for (let i = LEVELS.length-1; i>=0; i--) { if (xp >= LEVELS[i].xp) { cur = LEVELS[i]; break; } }
  const ni = LEVELS.findIndex(l => l.lvl === cur.lvl) + 1;
  return { current: cur, next: ni < LEVELS.length ? LEVELS[ni] : null };
}

function checkSpecialAutoComplete() {
  const lvl = getLevelData(state.totalXp).current.lvl;
  state.specials.forEach(sq => {
    if (sq.done) return;
    let triggered = false;
    if (sq.xpGoal && state.totalXp >= sq.xpGoal) triggered = true;
    if (sq.taskGoal && state.totalTasksDone >= sq.taskGoal) triggered = true;
    if (sq.streakGoal && state.streak >= sq.streakGoal) triggered = true;
    if (sq.id === 's10' && lvl >= 10) triggered = true;
    if (triggered) {
      sq.done = true;
      state.totalXp += sq.xp;
      state.completed.unshift({name: sq.icon+' '+sq.name, xp: sq.xp, type:'special', time:new Date()});
      pushNotif({
        type: 'special',
        icon: sq.icon,
        title: 'Special Quest Complete!',
        desc: sq.name,
        xp: sq.xp,
        duration: 5000,
      });
    }
  });
}

function updateHero() {
  const {current, next} = getLevelData(state.totalXp);
  document.getElementById('level-num').textContent = current.lvl;
  document.getElementById('level-icon').textContent = current.icon;
  document.getElementById('player-title').textContent = current.title;
  if (next) {
    const pct = Math.min(100, Math.round(((state.totalXp - current.xp) / (next.xp - current.xp)) * 100));
    document.getElementById('xp-fill').style.width = pct + '%';
    document.getElementById('cur-xp').textContent = state.totalXp.toLocaleString();
    document.getElementById('max-xp').textContent = next.xp.toLocaleString();
    document.getElementById('level-hint').textContent = (next.xp - state.totalXp).toLocaleString() + ' XP until ' + next.title;
  } else {
    document.getElementById('xp-fill').style.width = '100%';
    document.getElementById('cur-xp').textContent = state.totalXp.toLocaleString();
    document.getElementById('max-xp').textContent = state.totalXp.toLocaleString();
    document.getElementById('level-hint').textContent = 'Maximum level reached!';
  }
  document.getElementById('total-xp').textContent = state.totalXp.toLocaleString();
  document.getElementById('done-today').textContent = state.completed.filter(c => c.type !== 'bonus').length;
  document.getElementById('streak-stat').textContent = state.streak + ' 🔥';
  const count = state.completed.filter(c => c.type !== 'bonus').length;
  const btn = document.getElementById('completed-tab-btn');
  btn.innerHTML = 'Completed' + (count > 0 ? ` <span class="tab-count">${count}</span>` : '');
}

function updateDailyProgress() {
  const total = state.dailies.length, done = state.dailies.filter(d=>d.done).length;
  const pct = total > 0 ? Math.round((done/total)*100) : 0;
  document.getElementById('daily-fill').style.width = pct + '%';
  document.getElementById('daily-progress-label').textContent = done + ' / ' + total + ' done';
  const hint = document.getElementById('streak-hint');
  if (total > 0 && done === total) {
    hint.textContent = '🔥 All daily quests done! Streak: '+state.streak+' day'+(state.streak!==1?'s':'')+'.';
    hint.classList.add('active');
  } else {
    hint.textContent = (total-done)+' quest'+((total-done)!==1?'s':'')+' left to grow your streak.';
    hint.classList.remove('active');
  }
}

function completeItem(id, type) {
  const list = type==='daily' ? state.dailies : state.habits;
  const item = list.find(h=>h.id===id);
  if (!item||item.done) return;
  const prevLvl = getLevelData(state.totalXp).current.lvl;
  item.done = true;
  state.totalXp += item.xp;
  state.totalTasksDone++;
  state.completed.unshift({id:item.id, name:item.name, xp:item.xp, type, time:new Date()});
  const newLvl = getLevelData(state.totalXp).current.lvl;
  if (newLvl > prevLvl) {
    const lvl = getLevelData(state.totalXp).current;
    setTimeout(() => pushNotif({
      type:'level', icon: lvl.icon,
      title: 'Level Up! You are now Level ' + lvl.lvl,
      desc: lvl.title,
      xp: null,
      duration: 5000,
    }), 300);
  }
  if (type==='daily' && state.dailies.every(d=>d.done) && !state.streakAwardedToday) {
    state.streakAwardedToday = true;
    state.streak += 1;
    state.totalXp += 20;
    state.completed.unshift({name:'All daily quests completed! Bonus', xp:20, type:'bonus', time:new Date()});
    setTimeout(() => showSimpleToast('🔥 Streak is now '+state.streak+'! +20 bonus XP!'), 200);
  }
  checkSpecialAutoComplete();
  render();
}

function completeSpecial(id) {
  const sq = state.specials.find(s=>s.id===id);
  const lvl = getLevelData(state.totalXp).current.lvl;
  if (!sq||sq.done||lvl<sq.unlockLvl) return;
  sq.done = true;
  state.totalXp += sq.xp;
  state.completed.unshift({name:sq.icon+' '+sq.name, xp:sq.xp, type:'special', time:new Date()});
  pushNotif({
    type:'special', icon: sq.icon,
    title: 'Special Quest Complete!',
    desc: sq.name,
    xp: sq.xp,
    duration: 5000,
  });
  render();
}

function deleteItem(id, type, e) {
  e.stopPropagation();
  if (type==='daily') state.dailies = state.dailies.filter(h=>h.id!==id);
  else state.habits = state.habits.filter(h=>h.id!==id);
  render();
}

function renderHabits() {
  const el = document.getElementById('habits-list');
  const pending = state.habits.filter(h=>!h.done);
  if (!state.habits.length) { el.innerHTML='<div class="empty-state">No habits yet — add your first quest!</div>'; return; }
  if (!pending.length) { el.innerHTML='<div class="empty-state">All habits done! Check the Completed tab.</div>'; return; }
  el.innerHTML = pending.map(h=>`
    <div class="habit-card" onclick="completeItem(${h.id},'habit')">
      <div class="check-indicator"></div>
      <div class="habit-info"><div class="habit-name">${h.name}</div><div class="habit-meta">Click to complete</div></div>
      <div class="xp-pill">+${h.xp} XP</div>
      <button class="delete-btn" onclick="deleteItem(${h.id},'habit',event)">✕</button>
    </div>`).join('');
}

function renderDailies() {
  const el = document.getElementById('daily-list');
  const pending = state.dailies.filter(d=>!d.done);
  if (!state.dailies.length) { el.innerHTML='<div class="empty-state">No daily quests yet — add one above!</div>'; return; }
  if (!pending.length) { el.innerHTML=''; return; }
  el.innerHTML = pending.map(d=>`
    <div class="habit-card daily-card" onclick="completeItem(${d.id},'daily')">
      <div class="check-indicator"></div>
      <div class="habit-info"><div class="habit-name">${d.name}</div><div class="habit-meta">Resets daily</div></div>
      <div class="xp-pill daily">+${d.xp} XP</div>
      <button class="delete-btn" onclick="deleteItem(${d.id},'daily',event)">✕</button>
    </div>`).join('');
}

function renderSpecials() {
  const lvl = getLevelData(state.totalXp).current.lvl;
  const bannerEl = document.getElementById('special-milestone-banner');
  const el = document.getElementById('special-list');
  const nextLocked = state.specials.find(s=>!s.done && lvl<s.unlockLvl);
  bannerEl.innerHTML = nextLocked
    ? `<div class="milestone-banner"><span class="mb-icon">🔒</span><div class="mb-text">Reach <strong>Level ${nextLocked.unlockLvl}</strong> to unlock <strong>${nextLocked.name}</strong></div></div>`
    : '';
  const available = state.specials.filter(s=>!s.done && lvl>=s.unlockLvl);
  const locked    = state.specials.filter(s=>!s.done && lvl<s.unlockLvl);
  const done      = state.specials.filter(s=>s.done);
  let html = '';
  available.forEach(sq => {
    let progress = '';
    if (sq.xpGoal) progress = `${Math.min(state.totalXp,sq.xpGoal).toLocaleString()} / ${sq.xpGoal.toLocaleString()} XP`;
    if (sq.taskGoal) progress = `${Math.min(state.totalTasksDone,sq.taskGoal)} / ${sq.taskGoal} tasks`;
    if (sq.streakGoal) progress = `${Math.min(state.streak,sq.streakGoal)} / ${sq.streakGoal} days`;
    html += `<div class="habit-card special-card" onclick="completeSpecial('${sq.id}')">
      <div style="font-size:20px;flex-shrink:0;">${sq.icon}</div>
      <div class="habit-info">
        <div class="habit-name special">${sq.name}</div>
        <div class="habit-meta special">${sq.desc}${progress?' · '+progress:''}</div>
      </div>
      <div class="xp-pill special">+${sq.xp.toLocaleString()} XP</div>
    </div>`;
  });
  if (locked.length) {
    html += `<div class="subsection-label">Locked quests</div>`;
    locked.forEach(sq => { html += `<div class="locked-card"><div class="lock-icon">🔒</div><div class="habit-info"><div class="habit-name" style="color:#333;">${sq.name}</div><div class="habit-meta locked">Unlocks at Level ${sq.unlockLvl}</div></div><div class="xp-pill locked-pill">+${sq.xp.toLocaleString()} XP</div></div>`; });
  }
  if (done.length) {
    html += `<div class="subsection-label">Completed</div>`;
    done.forEach(sq => { html += `<div class="completed-card special-done"><div class="check-done special">✓</div><div class="habit-info"><div class="habit-name struck">${sq.icon} ${sq.name}</div><div class="habit-meta">${sq.desc}</div></div><div class="xp-pill earned">+${sq.xp.toLocaleString()} XP</div></div>`; });
  }
  if (!available.length && !locked.length && !done.length) html = '<div class="empty-state">No special quests available.</div>';
  el.innerHTML = html;
}

function renderCompleted() {
  const el = document.getElementById('completed-list');
  const items = state.completed.filter(c=>c.type!=='bonus');
  if (!items.length) { el.innerHTML='<div class="empty-state">Nothing completed yet — click a quest to finish it!</div>'; return; }
  el.innerHTML = items.map(c=>`
    <div class="completed-card${c.type==='daily'?' daily-card':c.type==='special'?' special-done':''}">
      <div class="check-done${c.type==='special'?' special':''}">✓</div>
      <div class="habit-info"><div class="habit-name struck">${c.name}</div><div class="habit-meta">${c.type==='daily'?'Daily quest':c.type==='special'?'Special quest':'Habit'}</div></div>
      <div class="xp-pill earned">+${c.xp.toLocaleString()} XP</div>
    </div>`).join('');
}

function render() { updateHero(); renderHabits(); renderDailies(); updateDailyProgress(); renderSpecials(); renderCompleted(); }

function switchTab(name) {
  const names=['quests','daily','special','completed'];
  document.querySelectorAll('.tab-btn').forEach((b,i)=>b.classList.toggle('active',names[i]===name));
  document.querySelectorAll('.tab-panel').forEach(p=>p.classList.remove('active'));
  document.getElementById('tab-'+name).classList.add('active');
}
function openForm(t) { document.getElementById(t+'-form').classList.add('open'); document.getElementById(t+'-input').focus(); }
function closeForm(t) { document.getElementById(t+'-form').classList.remove('open'); document.getElementById(t+'-input').value=''; }
function submitHabit() {
  const name=document.getElementById('habit-input').value.trim();
  if(!name)return;
  state.habits.push({id:state.nextId++,name,xp:parseInt(document.getElementById('habit-xp-select').value),done:false});
  closeForm('habit'); render();
}
function submitDaily() {
  const name=document.getElementById('daily-input').value.trim();
  if(!name)return;
  state.dailies.push({id:state.nextId++,name,xp:parseInt(document.getElementById('daily-xp-select').value),done:false});
  closeForm('daily'); render();
}
document.getElementById('habit-input').addEventListener('keydown',e=>{if(e.key==='Enter')submitHabit();});
document.getElementById('daily-input').addEventListener('keydown',e=>{if(e.key==='Enter')submitDaily();});
render();
</script>
</body></html>
