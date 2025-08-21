---
layout: single
title: "뽀모도로 타이머"
permalink: /pomodoro/
author_profile: false
toc: false
---

<div id="pomodoro-timer">
  <div class="timer-container">
    <div class="timer-header">
      <h2 id="timer-mode">작업 시간</h2>
    </div>

    <div class="timer-display">
      <div class="circular-timer">
        <div class="timer-face">

          <!-- 토마토 다이얼 SVG -->
          <svg class="timer-svg tomato" width="320" height="320" viewBox="0 0 320 320" aria-hidden="true">
            <!-- 바닥 그림자 -->
            <ellipse cx="160" cy="250" rx="110" ry="22" fill="rgba(0,0,0,.18)"/>
            <defs>
              <!-- 토마토 표면 하이라이트 -->
              <radialGradient id="gloss" cx="35%" cy="25%" r="60%">
                <stop offset="0%" stop-color="rgba(255,255,255,.9)"/>
                <stop offset="40%" stop-color="rgba(255,255,255,.25)"/>
                <stop offset="100%" stop-color="rgba(255,255,255,0)"/>
              </radialGradient>
              <!-- 토마토 레드 그라데이션 -->
              <radialGradient id="tomatoRed" cx="50%" cy="40%" r="65%">
                <stop offset="0%" stop-color="#ff4343"/>
                <stop offset="70%" stop-color="#e1252f"/>
                <stop offset="100%" stop-color="#b8181f"/>
              </radialGradient>
            </defs>

            <!-- 토마토 본체 -->
            <g>
              <path d="M160,60
                       C220,55 265,85 275,135
                       C285,190 240,235 160,240
                       C80,235 35,190 45,135
                       C55,85 100,55 160,60 Z"
                    fill="url(#tomatoRed)"/>
              <path d="M160,64
                       C216,60 255,87 264,132
                       C272,178 234,219 160,224
                       C86,219 48,178 56,132
                       C65,87 104,60 160,64 Z"
                    fill="url(#gloss)"/>
            </g>

            <!-- 잎사귀 + 포인터 -->
            <g transform="translate(160,66)">
              <g fill="#2e7d32" stroke="#1b5e20" stroke-width="2">
                <path d="M0,0 C20,-10 40,-10 60,0 C20,6 10,14 0,0Z"/>
                <path d="M0,0 C-20,-10 -40,-10 -60,0 C-20,6 -10,14 0,0Z"/>
                <path d="M0,0 C10,-18 8,-36 0,-52 C-6,-28 -8,-14 0,0Z"/>
                <path d="M0,0 C-6,14 -24,22 -44,26 C-18,10 -8,6 0,0Z"/>
                <path d="M0,0 C6,14 24,22 44,26 C18,10 8,6 0,0Z"/>
              </g>
              <polygon points="0,12 -7,28 7,28" fill="#fff"/>
            </g>

            <!-- 바깥 둘레 눈금 -->
            <g transform="translate(160,150)">
              <!-- 1분 눈금 -->
              <g stroke="rgba(255,255,255,.85)">
                <g id="minor"><line x1="0" y1="-122" x2="0" y2="-114" stroke-width="2"/></g>
                <!-- 60개 회전 복제 -->
                <use href="#minor" transform="rotate(0)"/>
                <use href="#minor" transform="rotate(6)"/><use href="#minor" transform="rotate(12)"/>
                <use href="#minor" transform="rotate(18)"/><use href="#minor" transform="rotate(24)"/>
                <use href="#minor" transform="rotate(30)"/><use href="#minor" transform="rotate(36)"/>
                <use href="#minor" transform="rotate(42)"/><use href="#minor" transform="rotate(48)"/>
                <use href="#minor" transform="rotate(54)"/><use href="#minor" transform="rotate(60)"/>
                <use href="#minor" transform="rotate(66)"/><use href="#minor" transform="rotate(72)"/>
                <use href="#minor" transform="rotate(78)"/><use href="#minor" transform="rotate(84)"/>
                <use href="#minor" transform="rotate(90)"/><use href="#minor" transform="rotate(96)"/>
                <use href="#minor" transform="rotate(102)"/><use href="#minor" transform="rotate(108)"/>
                <use href="#minor" transform="rotate(114)"/><use href="#minor" transform="rotate(120)"/>
                <use href="#minor" transform="rotate(126)"/><use href="#minor" transform="rotate(132)"/>
                <use href="#minor" transform="rotate(138)"/><use href="#minor" transform="rotate(144)"/>
                <use href="#minor" transform="rotate(150)"/><use href="#minor" transform="rotate(156)"/>
                <use href="#minor" transform="rotate(162)"/><use href="#minor" transform="rotate(168)"/>
                <use href="#minor" transform="rotate(174)"/><use href="#minor" transform="rotate(180)"/>
                <use href="#minor" transform="rotate(186)"/><use href="#minor" transform="rotate(192)"/>
                <use href="#minor" transform="rotate(198)"/><use href="#minor" transform="rotate(204)"/>
                <use href="#minor" transform="rotate(210)"/><use href="#minor" transform="rotate(216)"/>
                <use href="#minor" transform="rotate(222)"/><use href="#minor" transform="rotate(228)"/>
                <use href="#minor" transform="rotate(234)"/><use href="#minor" transform="rotate(240)"/>
                <use href="#minor" transform="rotate(246)"/><use href="#minor" transform="rotate(252)"/>
                <use href="#minor" transform="rotate(258)"/><use href="#minor" transform="rotate(264)"/>
                <use href="#minor" transform="rotate(270)"/><use href="#minor" transform="rotate(276)"/>
                <use href="#minor" transform="rotate(282)"/><use href="#minor" transform="rotate(288)"/>
                <use href="#minor" transform="rotate(294)"/><use href="#minor" transform="rotate(300)"/>
                <use href="#minor" transform="rotate(306)"/><use href="#minor" transform="rotate(312)"/>
                <use href="#minor" transform="rotate(318)"/><use href="#minor" transform="rotate(324)"/>
                <use href="#minor" transform="rotate(330)"/><use href="#minor" transform="rotate(336)"/>
                <use href="#minor" transform="rotate(342)"/><use href="#minor" transform="rotate(348)"/>
                <use href="#minor" transform="rotate(354)"/>
              </g>
              <!-- 5분 굵은 눈금 -->
              <g stroke="#fff" stroke-width="4">
                <g id="major"><line x1="0" y1="-122" x2="0" y2="-110"/></g>
                <use href="#major" transform="rotate(0)"/>
                <use href="#major" transform="rotate(30)"/>
                <use href="#major" transform="rotate(60)"/>
                <use href="#major" transform="rotate(90)"/>
                <use href="#major" transform="rotate(120)"/>
                <use href="#major" transform="rotate(150)"/>
                <use href="#major" transform="rotate(180)"/>
                <use href="#major" transform="rotate(210)"/>
                <use href="#major" transform="rotate(240)"/>
                <use href="#major" transform="rotate(270)"/>
                <use href="#major" transform="rotate(300)"/>
                <use href="#major" transform="rotate(330)"/>
              </g>
            </g>

            <!-- 진행 아크(하얀 띠) -->
            <circle id="progress-arc"
                    cx="160" cy="150" r="115"
                    fill="none"
                    stroke="#ffffff" stroke-opacity="0.95"
                    stroke-width="18" stroke-linecap="round"
                    stroke-dasharray="722.566" stroke-dashoffset="722.566"
                    transform="rotate(-90 160 150)"/>
          </svg>

          <!-- 중앙 시간 표시 -->
          <div class="timer-center" role="timer" aria-live="polite">
            <div class="center-circle"></div>
            <div id="time-display">25:00</div>
          </div>
        </div>
      </div>
    </div>

    <div class="timer-controls">
      <button id="start-btn" class="btn btn-primary">시작</button>
      <button id="pause-btn" class="btn btn-secondary" disabled>일시정지</button>
      <button id="reset-btn" class="btn btn-secondary">리셋</button>
    </div>

    <div class="timer-modes">
      <button id="work-mode" class="mode-btn active">작업 (25분)</button>
      <button id="short-break-mode" class="mode-btn">짧은 휴식 (5분)</button>
      <button id="long-break-mode" class="mode-btn">긴 휴식 (15분)</button>
    </div>

    <div class="timer-stats">
      <div class="stat">
        <span class="stat-label">완료된 뽀모도로:</span>
        <span id="completed-pomodoros">0</span>
      </div>
    </div>
  </div>
</div>

<style>
#pomodoro-timer {
  max-width: 520px;
  margin: 0 auto;
  padding: 2rem;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}
.timer-container {
  background: #fff;
  border-radius: 20px;
  padding: 2rem;
  box-shadow: 0 10px 30px rgba(0,0,0,.08);
  text-align: center;
}
.timer-header h2 { margin: 0 0 1rem; color: #333; font-size: 1.5rem; font-weight: 600; }

.timer-display { margin: 1.5rem 0; display: flex; justify-content: center; align-items: center; }
.circular-timer { position: relative; display: flex; justify-content: center; align-items: center; }
.timer-face { position: relative; background: transparent; box-shadow: none; padding: 0; }

.timer-svg.tomato { display:block; width: 280px; height: 280px; }
.timer-center {
  position: absolute; top: 50%; left: 50%; transform: translate(-50%,-50%);
  display: flex; flex-direction: column; align-items: center; justify-content: center;
  pointer-events: none;
}
.center-circle {
  width: 66px; height: 66px; border-radius: 50%;
  background: radial-gradient(circle at 30% 30%, #ffffff 0%, #f8f9fa 55%, #e9ecef 100%);
  box-shadow: inset 2px 2px 6px rgba(0,0,0,.12), inset -2px -2px 6px rgba(255,255,255,.8);
  position: absolute; z-index: 5;
}
#time-display {
  font-size: 1.8rem; font-weight: 800; color: #2c3e50; text-shadow: 0 1px 2px rgba(255,255,255,.6);
  font-variant-numeric: tabular-nums; position: relative; z-index: 10;
}

.timer-controls { margin: 1.75rem 0; display:flex; justify-content:center; gap: 0.8rem; }
.btn {
  padding: 0.75rem 1.5rem; border: none; border-radius: 25px; font-size: 1rem; font-weight: 600;
  cursor: pointer; transition: all .25s ease; min-width: 110px;
}
.btn-primary { background:#e53935; color:#fff; }
.btn-primary:hover:not(:disabled) { background:#c62828; transform: translateY(-2px); }
.btn-secondary { background:#95a5a6; color:#fff; }
.btn-secondary:hover:not(:disabled) { background:#7f8c8d; transform: translateY(-2px); }
.btn:disabled { opacity:.6; cursor:not-allowed; transform:none; }

.timer-modes { margin: 1.5rem 0; display:flex; justify-content:center; gap:.5rem; flex-wrap:wrap; }
.mode-btn {
  padding:.5rem 1rem; border:2px solid #ecf0f1; border-radius: 20px; background:#fff; color:#7f8c8d;
  font-size:.9rem; cursor:pointer; transition:all .25s ease; white-space:nowrap;
}
.mode-btn:hover { border-color:#3498db; color:#3498db; }
.mode-btn.active { background:#2e7d32; border-color:#2e7d32; color:#fff; }

.timer-stats { margin-top:1.2rem; padding-top:1rem; border-top:1px solid #ecf0f1; }
.stat { display:flex; justify-content:space-between; align-items:center; margin:.5rem 0; color:#7f8c8d; }
.stat-label { font-weight:500; }
#completed-pomodoros { font-weight: 800; color:#e74c3c; font-size:1.2rem; }

/* 활성 애니메이션(은은한 호흡) */
.timer-container.active { animation: pulse 2s infinite; }
@keyframes pulse {
  0% { box-shadow: 0 10px 30px rgba(0,0,0,.08); }
  50% { box-shadow: 0 10px 30px rgba(231,76,60,.18); }
  100% { box-shadow: 0 10px 30px rgba(0,0,0,.08); }
}

/* 반응형 */
@media (max-width: 768px) {
  #pomodoro-timer { padding: 1rem; }
  .timer-container { padding: 1.25rem; }
  .timer-svg.tomato { width: 240px; height: 240px; }
  #time-display { font-size: 1.6rem; }
  .timer-controls { flex-direction: column; }
  .btn { width: 100%; max-width: 220px; }
  .timer-modes { flex-direction: column; }
  .mode-btn { width: 100%; max-width: 220px; }
}
</style>

<script>
class PomodoroTimer {
  constructor() {
    // (분)
    this.modes = { work: 25, shortBreak: 5, longBreak: 15 };

    // 상태
    this.currentMode = 'work';
    this.timeLeft = this.modes.work * 60; // 초
    this.isRunning = false;
    this.completedPomodoros = 0;
    this.timer = null;

    // DOM
    this.timeDisplay = document.getElementById('time-display');
    this.timerMode = document.getElementById('timer-mode');
    this.startBtn = document.getElementById('start-btn');
    this.pauseBtn = document.getElementById('pause-btn');
    this.resetBtn = document.getElementById('reset-btn');
    this.workModeBtn = document.getElementById('work-mode');
    this.shortBreakModeBtn = document.getElementById('short-break-mode');
    this.longBreakModeBtn = document.getElementById('long-break-mode');
    this.completedPomodorosDisplay = document.getElementById('completed-pomodoros');
    this.timerContainer = document.querySelector('.timer-container');
    this.progressBar = document.getElementById('progress-arc');

    // 원형 진행바 설정 (SVG r=115)
    this.circleRadius = 115;
    this.circleCircumference = 2 * Math.PI * this.circleRadius; // ≈ 722.566

    this.initEventListeners();
    this.updateDisplay();
    this.loadStats();
  }

  initEventListeners() {
    this.startBtn.addEventListener('click', () => this.startTimer());
    this.pauseBtn.addEventListener('click', () => this.pauseTimer());
    this.resetBtn.addEventListener('click', () => this.resetTimer());

    this.workModeBtn.addEventListener('click', () => this.setMode('work'));
    this.shortBreakModeBtn.addEventListener('click', () => this.setMode('shortBreak'));
    this.longBreakModeBtn.addEventListener('click', () => this.setMode('longBreak'));
  }

  startTimer() {
    if (this.isRunning) return;
    this.isRunning = true;
    this.startBtn.disabled = true;
    this.pauseBtn.disabled = false;
    this.timerContainer.classList.add('active');

    // 알림 권한 미리 확보
    if ('Notification' in window && Notification.permission === 'default') {
      Notification.requestPermission().catch(()=>{});
    }

    this.timer = setInterval(() => {
      this.timeLeft--;
      this.updateDisplay();
      if (this.timeLeft <= 0) this.completeTimer();
    }, 1000);
  }

  pauseTimer() {
    this.isRunning = false;
    this.startBtn.disabled = false;
    this.pauseBtn.disabled = true;
    this.timerContainer.classList.remove('active');
    clearInterval(this.timer);
  }

  resetTimer() {
    this.pauseTimer();
    this.timeLeft = this.modes[this.currentMode] * 60;
    this.updateDisplay();
    this.progressBar.style.strokeDashoffset = this.circleCircumference;
    this.progressBar.style.stroke = '#ffffff';
    this.progressBar.style.strokeOpacity = '0.95';
  }

  completeTimer() {
    this.pauseTimer();
    this.playNotificationSound();

    if (this.currentMode === 'work') {
      this.completedPomodoros++;
      this.saveStats();
      this.updateStatsDisplay();
      // 4회마다 긴 휴식
      if (this.completedPomodoros % 4 === 0) this.setMode('longBreak');
      else this.setMode('shortBreak');
    } else {
      this.setMode('work');
    }
    this.showNotification();
  }

  setMode(mode) {
    if (this.isRunning) return;

    this.currentMode = mode;
    this.timeLeft = this.modes[mode] * 60;

    document.querySelectorAll('.mode-btn').forEach(b => b.classList.remove('active'));
    if (mode === 'work') {
      this.workModeBtn.classList.add('active'); this.timerMode.textContent = '작업 시간';
    } else if (mode === 'shortBreak') {
      this.shortBreakModeBtn.classList.add('active'); this.timerMode.textContent = '짧은 휴식';
    } else {
      this.longBreakModeBtn.classList.add('active'); this.timerMode.textContent = '긴 휴식';
    }
    this.updateDisplay();
  }

  updateDisplay() {
    const minutes = Math.floor(this.timeLeft / 60);
    const seconds = this.timeLeft % 60;
    const timeString = `${String(minutes).padStart(2,'0')}:${String(seconds).padStart(2,'0')}`;
    this.timeDisplay.textContent = timeString;

    // 진행바
    const total = this.modes[this.currentMode] * 60;
    const progress = (total - this.timeLeft) / total;
    const offset = this.circleCircumference - (progress * this.circleCircumference);
    this.progressBar.style.strokeDashoffset = offset;

    document.title = this.isRunning ? `${timeString} - 뽀모도로 타이머` : '뽀모도로 타이머';
  }

  updateStatsDisplay() {
    this.completedPomodorosDisplay.textContent = this.completedPomodoros;
  }

  playNotificationSound() {
    try {
      const audio = new Audio('data:audio/wav;base64,UklGRnoGAABXQVZFZm10IBAAAAABAAEAQB8AAEAfAAABAAgAZGF0YQoGAACBhYqFbF1fdJivrJBhNjVgodDbq2EcBj+a2/LDciUFLIHO8tiJNwgZaLvt559NEAxQp+PwtmMcBjiR1/LMeSwFJHfH8N2QQAoUXrTp66hVFApGn+Dtx2YeCA6FKL');
      audio.play().catch(()=>{});
    } catch(e) {}
  }

  showNotification() {
    if ('Notification' in window && Notification.permission === 'granted') {
      const isWork = this.currentMode === 'work';
      new Notification(isWork ? '휴식 완료!' : '작업 완료!', {
        body: isWork ? '작업을 시작하세요.' : '휴식 시간입니다.',
        icon: '/assets/images/favicon.ico'
      });
    }
  }

  saveStats() {
    localStorage.setItem('pomodoroCompletedCount', String(this.completedPomodoros));
  }
  loadStats() {
    const saved = localStorage.getItem('pomodoroCompletedCount');
    if (saved) this.completedPomodoros = parseInt(saved, 10) || 0;
    this.updateStatsDisplay();
  }
}

document.addEventListener('DOMContentLoaded', () => {
  new PomodoroTimer();
});
</script>
