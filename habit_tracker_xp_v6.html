
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  #app { padding: 1rem 0; font-family: var(--font-sans); }

  .hero { margin-bottom: 1.25rem; }
  .level-badge { display: inline-flex; align-items: center; gap: 6px; background: #2C2C2A; color: #FAC775; padding: 4px 12px; border-radius: 999px; font-size: 12px; font-weight: 500; margin-bottom: 10px; }
  .player-name { font-size: 22px; font-weight: 500; color: var(--color-text-primary); margin-bottom: 4px; }
  .xp-row { display: flex; align-items: center; gap: 10px; margin-bottom: 4px; }
  .xp-bar-wrap { flex: 1; height: 8px; background: var(--color-background-secondary); border-radius: 999px; border: 0.5px solid var(--color-border-tertiary); overflow: hidden; }
  .xp-bar-fill { height: 100%; border-radius: 999px; background: #EF9F27; transition: width 0.5s cubic-bezier(.4,0,.2,1); }
  .xp-label { font-size: 12px; color: var(--color-text-secondary); min-width: 80px; text-align: right; }
  .level-hint { font-size: 13px; color: var(--color-text-secondary); }

  .stats-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; margin-bottom: 1.25rem; }
  .stat-card { background: var(--color-background-secondary); border-radius: var(--border-radius-md); padding: 10px 12px; }
  .stat-label { font-size: 11px; color: var(--color-text-tertiary); margin-bottom: 2px; }
  .stat-val { font-size: 20px; font-weight: 500; color: var(--color-text-primary); }

  .tabs { display: flex; border-bottom: 0.5px solid var(--color-border-tertiary); margin-bottom: 1.25rem; }
  .tab-btn { background: transparent; border: none; border-bottom: 2px solid transparent; padding: 8px 16px; font-size: 13px; font-weight: 500; color: var(--color-text-tertiary); cursor: pointer; font-family: var(--font-sans); transition: color 0.15s, border-color 0.15s; margin-bottom: -0.5px; }
  .tab-btn.active { color: var(--color-text-primary); border-bottom-color: #EF9F27; }
  .tab-btn:hover:not(.active) { color: var(--color-text-secondary); }
  .tab-count { display: inline-flex; align-items: center; justify-content: center; background: #3B6D11; color: #C0DD97; border-radius: 999px; font-size: 10px; font-weight: 500; min-width: 16px; height: 16px; padding: 0 4px; margin-left: 5px; }

  .tab-panel { display: none; }
  .tab-panel.active { display: block; }

  .section-head { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; }
  .section-title { font-size: 13px; font-weight: 500; color: var(--color-text-secondary); }

  .daily-banner { background: var(--color-background-secondary); border-radius: var(--border-radius-lg); padding: 10px 14px; display: flex; align-items: center; gap: 10px; margin-bottom: 12px; border: 0.5px solid var(--color-border-tertiary); }
  .daily-label { font-size: 13px; color: var(--color-text-secondary); flex: 1; }
  .daily-label strong { color: var(--color-text-primary); font-weight: 500; }

  .add-btn { display: flex; align-items: center; gap: 4px; background: transparent; border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); padding: 5px 10px; font-size: 12px; color: var(--color-text-secondary); cursor: pointer; font-family: var(--font-sans); transition: background 0.15s; }
  .add-btn:hover { background: var(--color-background-secondary); }

  .habits-list { display: flex; flex-direction: column; gap: 8px; margin-bottom: 1rem; }

  .habit-card { background: var(--color-background-primary); border: 0.5px solid var(--color-border-tertiary); border-radius: var(--border-radius-lg); padding: 13px 14px; display: flex; align-items: center; gap: 12px; cursor: pointer; transition: border-color 0.15s, background 0.15s; user-select: none; }
  .habit-card:hover { border-color: var(--color-border-secondary); background: var(--color-background-secondary); }
  .habit-card:active { transform: scale(0.99); }
  .habit-card.daily-card { border-left: 2px solid #EF9F27; }

  .completed-card { background: var(--color-background-primary); border: 0.5px solid var(--color-border-tertiary); border-radius: var(--border-radius-lg); padding: 13px 14px; display: flex; align-items: center; gap: 12px; opacity: 0.6; }
  .completed-card.daily-card { border-left: 2px solid #3B6D11; }

  .check-indicator { width: 22px; height: 22px; flex-shrink: 0; border-radius: 50%; border: 1.5px solid var(--color-border-secondary); display: flex; align-items: center; justify-content: center; font-size: 12px; color: transparent; pointer-events: none; }
  .check-done { width: 22px; height: 22px; flex-shrink: 0; border-radius: 50%; background: #3B6D11; border: 1.5px solid #3B6D11; display: flex; align-items: center; justify-content: center; font-size: 12px; color: #C0DD97; }

  .habit-info { flex: 1; min-width: 0; pointer-events: none; }
  .habit-name { font-size: 14px; font-weight: 500; color: var(--color-text-primary); white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
  .habit-name.struck { text-decoration: line-through; color: var(--color-text-tertiary); }
  .habit-meta { font-size: 11px; color: var(--color-text-tertiary); margin-top: 2px; }

  .xp-pill { display: flex; align-items: center; background: var(--color-background-secondary); border-radius: 999px; padding: 3px 8px; font-size: 11px; font-weight: 500; color: #BA7517; white-space: nowrap; pointer-events: none; }
  .xp-pill.daily { background: #FAEEDA; color: #854F0B; }
  .xp-pill.earned { background: #EAF3DE; color: #3B6D11; }

  .delete-btn { background: transparent; border: none; cursor: pointer; color: var(--color-text-tertiary); font-size: 13px; padding: 4px 6px; border-radius: 4px; transition: color 0.15s; font-family: var(--font-sans); line-height: 1; }
  .delete-btn:hover { color: #A32D2D; }

  .add-form { background: var(--color-background-secondary); border: 0.5px solid var(--color-border-tertiary); border-radius: var(--border-radius-lg); padding: 14px; margin-bottom: 1rem; display: none; flex-direction: column; gap: 10px; }
  .add-form.open { display: flex; }
  .form-row { display: flex; gap: 8px; align-items: center; flex-wrap: wrap; }
  .form-row input, .form-row select { flex: 1; min-width: 100px; padding: 7px 10px; font-size: 13px; border-radius: var(--border-radius-md); border: 0.5px solid var(--color-border-secondary); background: var(--color-background-primary); color: var(--color-text-primary); font-family: var(--font-sans); }
  .submit-btn { background: #2C2C2A; color: #FAC775; border: none; border-radius: var(--border-radius-md); padding: 7px 14px; font-size: 13px; font-weight: 500; cursor: pointer; font-family: var(--font-sans); transition: opacity 0.15s; }
  .submit-btn:hover { opacity: 0.85; }
  .cancel-btn { background: transparent; border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); padding: 7px 12px; font-size: 13px; color: var(--color-text-secondary); cursor: pointer; font-family: var(--font-sans); transition: background 0.15s; }
  .cancel-btn:hover { background: var(--color-background-primary); }

  .daily-progress { display: flex; align-items: center; gap: 10px; margin-bottom: 14px; }
  .dp-bar-wrap { flex: 1; height: 6px; background: var(--color-background-secondary); border-radius: 999px; overflow: hidden; }
  .dp-bar-fill { height: 100%; border-radius: 999px; background: #EF9F27; transition: width 0.4s ease; }
  .dp-label { font-size: 12px; color: var(--color-text-secondary); white-space: nowrap; }

  .streak-hint { font-size: 12px; color: var(--color-text-tertiary); margin-bottom: 10px; padding: 8px 12px; background: var(--color-background-secondary); border-radius: var(--border-radius-md); border: 0.5px solid var(--color-border-tertiary); }
  .streak-hint.active { color: #3B6D11; background: #EAF3DE; border-color: #97C459; }

  .empty-state { font-size: 13px; color: var(--color-text-tertiary); padding: 24px 0; text-align: center; }

  .level-up-toast { position: fixed; top: 20px; left: 50%; transform: translateX(-50%) scale(0.9); background: #2C2C2A; color: #FAC775; padding: 10px 20px; border-radius: 999px; font-size: 14px; font-weight: 500; opacity: 0; pointer-events: none; transition: opacity 0.3s, transform 0.3s; z-index: 999; white-space: nowrap; }
  .level-up-toast.show { opacity: 1; transform: translateX(-50%) scale(1); }
</style>

<div id="app">
  <h2 class="sr-only">Habit tracker with daily quests, XP leveling, and completed tab</h2>

  <div class="hero">
    <div class="level-badge"><span id="level-icon">⚔</span> Level <span id="level-num">1</span></div>
    <div class="player-name" id="player-title">Novice Adventurer</div>
    <div class="xp-row">
      <div class="xp-bar-wrap"><div class="xp-bar-fill" id="xp-fill" style="width:0%"></div></div>
      <div class="xp-label"><span id="cur-xp">0</span> / <span id="max-xp">100</span> XP</div>
    </div>
    <div class="level-hint" id="level-hint"></div>
  </div>

  <div class="stats-grid">
    <div class="stat-card"><div class="stat-label">Total XP</div><div class="stat-val" id="total-xp">0</div></div>
    <div class="stat-card"><div class="stat-label">Done today</div><div class="stat-val" id="done-today">0</div></div>
    <div class="stat-card"><div class="stat-label">Streak</div><div class="stat-val" id="best-streak">0</div></div>
  </div>

  <div class="tabs">
    <button class="tab-btn active" onclick="switchTab('quests')">Quests</button>
    <button class="tab-btn" onclick="switchTab('daily')">Daily quests</button>
    <button class="tab-btn" id="completed-tab-btn" onclick="switchTab('completed')">Completed</button>
  </div>

  <!-- QUESTS -->
  <div class="tab-panel active" id="tab-quests">
    <div class="section-head">
      <div class="section-title">My habits</div>
      <button class="add-btn" onclick="openForm('habit')">+ Add habit</button>
    </div>
    <div class="add-form" id="habit-form">
      <div class="form-row">
        <input type="text" id="habit-input" placeholder="Habit name..." maxlength="40" />
        <select id="habit-xp-select">
          <option value="10">10 XP — Easy</option>
          <option value="25" selected>25 XP — Medium</option>
          <option value="50">50 XP — Hard</option>
          <option value="100">100 XP — Epic</option>
        </select>
      </div>
      <div class="form-row" style="justify-content: flex-end;">
        <button class="cancel-btn" onclick="closeForm('habit')">Cancel</button>
        <button class="submit-btn" onclick="submitHabit()">Add quest</button>
      </div>
    </div>
    <div class="habits-list" id="habits-list"></div>
  </div>

  <!-- DAILY QUESTS -->
  <div class="tab-panel" id="tab-daily">
    <div class="daily-banner">
      <div class="daily-label">📅 Complete <strong>all daily quests</strong> to grow your streak and earn a <strong>+50 XP bonus!</strong></div>
    </div>
    <div class="daily-progress">
      <div class="dp-bar-wrap"><div class="dp-bar-fill" id="daily-fill" style="width:0%"></div></div>
      <div class="dp-label" id="daily-progress-label">0 / 0 done</div>
    </div>
    <div id="streak-hint" class="streak-hint">Complete all daily quests to increase your streak.</div>
    <div class="section-head" style="margin-top:10px;">
      <div class="section-title">Today's daily quests</div>
      <button class="add-btn" onclick="openForm('daily')">+ Add daily</button>
    </div>
    <div class="add-form" id="daily-form">
      <div class="form-row">
        <input type="text" id="daily-input" placeholder="Daily quest name..." maxlength="40" />
        <select id="daily-xp-select">
          <option value="15">15 XP — Easy</option>
          <option value="35" selected>35 XP — Medium</option>
          <option value="75">75 XP — Hard</option>
          <option value="150">150 XP — Epic</option>
        </select>
      </div>
      <div class="form-row" style="justify-content: flex-end;">
        <button class="cancel-btn" onclick="closeForm('daily')">Cancel</button>
        <button class="submit-btn" onclick="submitDaily()">Add daily quest</button>
      </div>
    </div>
    <div class="habits-list" id="daily-list"></div>
  </div>

  <!-- COMPLETED -->
  <div class="tab-panel" id="tab-completed">
    <div class="habits-list" id="completed-list"></div>
  </div>
</div>

<div class="level-up-toast" id="toast"></div>

<script>
const LEVELS = [
  {lvl:1,xp:0,title:"Novice Adventurer",icon:"⚔"},
  {lvl:2,xp:100,title:"Apprentice",icon:"🗡"},
  {lvl:3,xp:250,title:"Scout",icon:"🏹"},
  {lvl:4,xp:500,title:"Warrior",icon:"🛡"},
  {lvl:5,xp:900,title:"Champion",icon:"⚡"},
  {lvl:6,xp:1400,title:"Veteran",icon:"🔥"},
  {lvl:7,xp:2000,title:"Hero",icon:"✨"},
  {lvl:8,xp:3000,title:"Legend",icon:"👑"},
  {lvl:9,xp:4500,title:"Mythic",icon:"🌟"},
  {lvl:10,xp:7000,title:"Ascendant",icon:"💎"},
];

let state = {
  totalXp: 0,
  streak: 0,
  streakAwardedToday: false,
  habits: [
    {id:1,name:"Morning workout",xp:50,done:false},
    {id:2,name:"Read for 20 minutes",xp:25,done:false},
    {id:3,name:"Drink 8 glasses of water",xp:10,done:false},
  ],
  dailies: [
    {id:101,name:"Log in and check quests",xp:15,done:false},
    {id:102,name:"Complete 3 habits",xp:75,done:false},
    {id:103,name:"Evening reflection",xp:35,done:false},
  ],
  completed: [],
  nextId: 200,
};

function getLevelData(xp) {
  let cur = LEVELS[0];
  for (let i = LEVELS.length-1; i>=0; i--) { if (xp >= LEVELS[i].xp) { cur = LEVELS[i]; break; } }
  const ni = LEVELS.findIndex(l => l.lvl === cur.lvl) + 1;
  return { current: cur, next: ni < LEVELS.length ? LEVELS[ni] : null };
}

function updateHero() {
  const {current, next} = getLevelData(state.totalXp);
  document.getElementById('level-num').textContent = current.lvl;
  document.getElementById('level-icon').textContent = current.icon;
  document.getElementById('player-title').textContent = current.title;
  if (next) {
    const pct = Math.min(100, Math.round(((state.totalXp - current.xp) / (next.xp - current.xp)) * 100));
    document.getElementById('xp-fill').style.width = pct + '%';
    document.getElementById('cur-xp').textContent = state.totalXp;
    document.getElementById('max-xp').textContent = next.xp;
    document.getElementById('level-hint').textContent = (next.xp - state.totalXp) + ' XP until ' + next.title;
  } else {
    document.getElementById('xp-fill').style.width = '100%';
    document.getElementById('cur-xp').textContent = state.totalXp;
    document.getElementById('max-xp').textContent = state.totalXp;
    document.getElementById('level-hint').textContent = 'Maximum level reached!';
  }
  document.getElementById('total-xp').textContent = state.totalXp.toLocaleString();
  document.getElementById('done-today').textContent = state.completed.filter(c => c.type !== 'bonus').length;
  document.getElementById('best-streak').textContent = state.streak;

  const count = state.completed.filter(c => c.type !== 'bonus').length;
  const btn = document.getElementById('completed-tab-btn');
  btn.innerHTML = 'Completed' + (count > 0 ? ` <span class="tab-count">${count}</span>` : '');
}

function updateDailyProgress() {
  const total = state.dailies.length;
  const done = state.dailies.filter(d => d.done).length;
  const pct = total > 0 ? Math.round((done/total)*100) : 0;
  document.getElementById('daily-fill').style.width = pct + '%';
  document.getElementById('daily-progress-label').textContent = done + ' / ' + total + ' done';

  const hint = document.getElementById('streak-hint');
  const allDone = total > 0 && done === total;
  if (allDone) {
    hint.textContent = '🔥 All daily quests done! Streak: ' + state.streak + ' day' + (state.streak !== 1 ? 's' : '') + '.';
    hint.classList.add('active');
  } else {
    const remaining = total - done;
    hint.textContent = remaining + ' quest' + (remaining !== 1 ? 's' : '') + ' left to grow your streak.';
    hint.classList.remove('active');
  }
}

function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 2800);
}

function completeItem(id, type) {
  const list = type === 'daily' ? state.dailies : state.habits;
  const item = list.find(h => h.id === id);
  if (!item || item.done) return;
  const prevLvl = getLevelData(state.totalXp).current.lvl;
  item.done = true;
  state.totalXp += item.xp;
  state.completed.unshift({id: item.id, name: item.name, xp: item.xp, type, time: new Date()});

  const newLvl = getLevelData(state.totalXp).current.lvl;
  if (newLvl > prevLvl) {
    const lvl = getLevelData(state.totalXp).current;
    setTimeout(() => showToast(lvl.icon + ' Level up! You are now ' + lvl.title), 200);
  }

  if (type === 'daily' && state.dailies.every(d => d.done) && !state.streakAwardedToday) {
    state.streakAwardedToday = true;
    state.streak += 1;
    state.totalXp += 50;
    state.completed.unshift({id: -1, name: 'All daily quests completed! Bonus', xp: 50, type: 'bonus', time: new Date()});
    setTimeout(() => showToast('🔥 Streak is now ' + state.streak + '! +50 bonus XP!'), 400);
  }

  render();
}

function deleteItem(id, type, e) {
  e.stopPropagation();
  if (type === 'daily') state.dailies = state.dailies.filter(h => h.id !== id);
  else state.habits = state.habits.filter(h => h.id !== id);
  render();
}

function renderHabits() {
  const el = document.getElementById('habits-list');
  const pending = state.habits.filter(h => !h.done);
  if (!state.habits.length) { el.innerHTML = '<div class="empty-state">No habits yet — add your first quest!</div>'; return; }
  if (!pending.length) { el.innerHTML = '<div class="empty-state">All habits done! Check the Completed tab.</div>'; return; }
  el.innerHTML = pending.map(h => `
    <div class="habit-card" onclick="completeItem(${h.id},'habit')">
      <div class="check-indicator"></div>
      <div class="habit-info">
        <div class="habit-name">${h.name}</div>
        <div class="habit-meta">Click to complete</div>
      </div>
      <div class="xp-pill">+${h.xp} XP</div>
      <button class="delete-btn" onclick="deleteItem(${h.id},'habit',event)">✕</button>
    </div>`).join('');
}

function renderDailies() {
  const el = document.getElementById('daily-list');
  const pending = state.dailies.filter(d => !d.done);
  if (!state.dailies.length) { el.innerHTML = '<div class="empty-state">No daily quests yet — add one above!</div>'; return; }
  if (!pending.length) { el.innerHTML = ''; return; }
  el.innerHTML = pending.map(d => `
    <div class="habit-card daily-card" onclick="completeItem(${d.id},'daily')">
      <div class="check-indicator"></div>
      <div class="habit-info">
        <div class="habit-name">${d.name}</div>
        <div class="habit-meta">Resets daily</div>
      </div>
      <div class="xp-pill daily">+${d.xp} XP</div>
      <button class="delete-btn" onclick="deleteItem(${d.id},'daily',event)">✕</button>
    </div>`).join('');
  updateDailyProgress();
}

function renderCompleted() {
  const el = document.getElementById('completed-list');
  const items = state.completed.filter(c => c.type !== 'bonus');
  if (!items.length) { el.innerHTML = '<div class="empty-state">Nothing completed yet — click a quest to finish it!</div>'; return; }
  el.innerHTML = items.map(c => `
    <div class="completed-card${c.type==='daily'?' daily-card':''}">
      <div class="check-done">✓</div>
      <div class="habit-info">
        <div class="habit-name struck">${c.name}</div>
        <div class="habit-meta">${c.type==='daily'?'Daily quest':'Habit'}</div>
      </div>
      <div class="xp-pill earned">+${c.xp} XP</div>
    </div>`).join('');
}

function render() {
  updateHero();
  renderHabits();
  renderDailies();
  updateDailyProgress();
  renderCompleted();
}

function switchTab(name) {
  const names = ['quests','daily','completed'];
  document.querySelectorAll('.tab-btn').forEach((b,i) => b.classList.toggle('active', names[i]===name));
  document.querySelectorAll('.tab-panel').forEach(p => p.classList.remove('active'));
  document.getElementById('tab-'+name).classList.add('active');
}

function openForm(type) { document.getElementById(type+'-form').classList.add('open'); document.getElementById(type+'-input').focus(); }
function closeForm(type) { document.getElementById(type+'-form').classList.remove('open'); document.getElementById(type+'-input').value=''; }

function submitHabit() {
  const name = document.getElementById('habit-input').value.trim();
  if (!name) return;
  state.habits.push({id:state.nextId++,name,xp:parseInt(document.getElementById('habit-xp-select').value),done:false});
  closeForm('habit'); render();
}

function submitDaily() {
  const name = document.getElementById('daily-input').value.trim();
  if (!name) return;
  state.dailies.push({id:state.nextId++,name,xp:parseInt(document.getElementById('daily-xp-select').value),done:false});
  closeForm('daily'); render();
}

document.getElementById('habit-input').addEventListener('keydown', e => { if(e.key==='Enter') submitHabit(); });
document.getElementById('daily-input').addEventListener('keydown', e => { if(e.key==='Enter') submitDaily(); });

render();
</script>
