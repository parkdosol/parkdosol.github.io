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
        <svg class="circular-progress" width="200" height="200">
          <circle
            class="circular-progress-bg"
            cx="100"
            cy="100"
            r="85"
            fill="none"
            stroke="#f0f0f0"
            stroke-width="10"
          />
          <circle
            class="circular-progress-bar"
            cx="100"
            cy="100"
            r="85"
            fill="none"
            stroke="#e74c3c"
            stroke-width="10"
            stroke-linecap="round"
            stroke-dasharray="534.07"
            stroke-dashoffset="534.07"
            transform="rotate(-90 100 100)"
          />
        </svg>
        <div id="time-display">25:00</div>
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
  max-width: 500px;
  margin: 0 auto;
  padding: 2rem;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}

.timer-container {
  background: #fff;
  border-radius: 20px;
  padding: 2rem;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  text-align: center;
}

.timer-header h2 {
  margin: 0 0 1rem 0;
  color: #333;
  font-size: 1.5rem;
  font-weight: 600;
}

.timer-display {
  margin: 2rem 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.circular-timer {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 200px;
  height: 200px;
}

.circular-progress {
  position: absolute;
  top: 0;
  left: 0;
  transform: rotate(0deg);
}

.circular-progress-bg {
  opacity: 0.3;
}

.circular-progress-bar {
  transition: stroke-dashoffset 1s ease-in-out;
}

#time-display {
  font-size: 2.5rem;
  font-weight: bold;
  color: #333;
  font-family: 'Courier New', monospace;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
  position: absolute;
  z-index: 10;
  text-align: center;
}

.timer-controls {
  margin: 2rem 0;
  display: flex;
  justify-content: center;
  gap: 1rem;
}

.btn {
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 25px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  min-width: 100px;
}

.btn-primary {
  background: #27ae60;
  color: white;
}

.btn-primary:hover:not(:disabled) {
  background: #229954;
  transform: translateY(-2px);
}

.btn-secondary {
  background: #95a5a6;
  color: white;
}

.btn-secondary:hover:not(:disabled) {
  background: #7f8c8d;
  transform: translateY(-2px);
}

.btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
  transform: none;
}

.timer-modes {
  margin: 2rem 0;
  display: flex;
  justify-content: center;
  gap: 0.5rem;
  flex-wrap: wrap;
}

.mode-btn {
  padding: 0.5rem 1rem;
  border: 2px solid #ecf0f1;
  border-radius: 20px;
  background: #fff;
  color: #7f8c8d;
  font-size: 0.9rem;
  cursor: pointer;
  transition: all 0.3s ease;
  white-space: nowrap;
}

.mode-btn:hover {
  border-color: #3498db;
  color: #3498db;
}

.mode-btn.active {
  background: #3498db;
  border-color: #3498db;
  color: white;
}

.timer-stats {
  margin-top: 2rem;
  padding-top: 1rem;
  border-top: 1px solid #ecf0f1;
}

.stat {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0.5rem 0;
  color: #7f8c8d;
}

.stat-label {
  font-weight: 500;
}

#completed-pomodoros {
  font-weight: bold;
  color: #e74c3c;
  font-size: 1.2rem;
}

  /* 반응형 디자인 */
@media (max-width: 768px) {
  #pomodoro-timer {
    padding: 1rem;
  }
  
  .timer-container {
    padding: 1.5rem;
  }
  
  .circular-timer {
    width: 150px;
    height: 150px;
  }
  
  .circular-progress {
    width: 150px;
    height: 150px;
  }
  
  #time-display {
    font-size: 2rem;
  }
  
  .timer-controls {
    flex-direction: column;
    align-items: center;
  }
  
  .btn {
    width: 100%;
    max-width: 200px;
  }
  
  .timer-modes {
    flex-direction: column;
    align-items: center;
  }
  
  .mode-btn {
    width: 100%;
    max-width: 200px;
    margin: 0.2rem 0;
  }
}

/* 활성 상태 애니메이션 */
.timer-container.active {
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0% { box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1); }
  50% { box-shadow: 0 10px 30px rgba(231, 76, 60, 0.2); }
  100% { box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1); }
}
</style>

<script>
class PomodoroTimer {
  constructor() {
    // 타이머 설정 (분)
    this.modes = {
      work: 25,
      shortBreak: 5,
      longBreak: 15
    };
    
    // 현재 상태
    this.currentMode = 'work';
    this.timeLeft = this.modes.work * 60; // 초 단위
    this.isRunning = false;
    this.completedPomodoros = 0;
    this.timer = null;
    
    // DOM 요소
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
    this.progressBar = document.querySelector('.circular-progress-bar');
    
    // 원형 진행바 설정
    this.circleRadius = 85;
    this.circleCircumference = 2 * Math.PI * this.circleRadius;
    
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
    this.isRunning = true;
    this.startBtn.disabled = true;
    this.pauseBtn.disabled = false;
    this.timerContainer.classList.add('active');
    
    this.timer = setInterval(() => {
      this.timeLeft--;
      this.updateDisplay();
      
      if (this.timeLeft <= 0) {
        this.completeTimer();
      }
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
    // 진행바도 리셋
    this.progressBar.style.strokeDashoffset = this.circleCircumference;
    this.progressBar.style.stroke = '#e74c3c';
  }
  
  completeTimer() {
    this.pauseTimer();
    
    // 알림음 (가능한 경우)
    this.playNotificationSound();
    
    // 작업 완료 시 뽀모도로 카운트 증가
    if (this.currentMode === 'work') {
      this.completedPomodoros++;
      this.saveStats();
      this.updateStatsDisplay();
      
      // 자동으로 휴식 모드로 전환
      if (this.completedPomodoros % 4 === 0) {
        this.setMode('longBreak');
      } else {
        this.setMode('shortBreak');
      }
    } else {
      // 휴식 완료 시 작업 모드로 전환
      this.setMode('work');
    }
    
    // 완료 알림
    this.showNotification();
  }
  
  setMode(mode) {
    if (this.isRunning) return;
    
    this.currentMode = mode;
    this.timeLeft = this.modes[mode] * 60;
    
    // 모드 버튼 활성화 상태 업데이트
    document.querySelectorAll('.mode-btn').forEach(btn => btn.classList.remove('active'));
    
    if (mode === 'work') {
      this.workModeBtn.classList.add('active');
      this.timerMode.textContent = '작업 시간';
    } else if (mode === 'shortBreak') {
      this.shortBreakModeBtn.classList.add('active');
      this.timerMode.textContent = '짧은 휴식';
    } else if (mode === 'longBreak') {
      this.longBreakModeBtn.classList.add('active');
      this.timerMode.textContent = '긴 휴식';
    }
    
    this.updateDisplay();
  }
  
  updateDisplay() {
    const minutes = Math.floor(this.timeLeft / 60);
    const seconds = this.timeLeft % 60;
    const timeString = `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
    this.timeDisplay.textContent = timeString;
    
    // 원형 진행바 업데이트
    this.updateProgress();
    
    // 브라우저 탭 제목 업데이트
    if (this.isRunning) {
      document.title = `${timeString} - 뽀모도로 타이머`;
    } else {
      document.title = '뽀모도로 타이머';
    }
  }
  
  updateProgress() {
    const totalTime = this.modes[this.currentMode] * 60;
    const progress = (totalTime - this.timeLeft) / totalTime;
    const offset = this.circleCircumference - (progress * this.circleCircumference);
    
    this.progressBar.style.strokeDashoffset = offset;
    
    // 시간이 지날수록 더 진한 빨간색으로 변경
    const intensity = Math.min(progress * 1.5, 1); // 1.5배로 더 빠르게 진해짐
    const red = Math.floor(231 * (0.6 + 0.4 * intensity)); // 기본 빨간색에서 더 진해짐
    const green = Math.floor(76 * (1 - intensity * 0.7)); // 초록색 성분 감소
    const blue = Math.floor(60 * (1 - intensity * 0.8)); // 파란색 성분 감소
    
    this.progressBar.style.stroke = `rgb(${red}, ${green}, ${blue})`;
  }
  
  updateStatsDisplay() {
    this.completedPomodorosDisplay.textContent = this.completedPomodoros;
  }
  
  playNotificationSound() {
    // 가능한 경우 알림음 재생
    try {
      const audio = new Audio('data:audio/wav;base64,UklGRnoGAABXQVZFZm10IBAAAAABAAEAQB8AAEAfAAABAAgAZGF0YQoGAACBhYqFbF1fdJivrJBhNjVgodDbq2EcBj+a2/LDciUFLIHO8tiJNwgZaLvt559NEAxQp+PwtmMcBjiR1/LMeSwFJHfH8N2QQAoUXrTp66hVFApGn+Dtx2YeCA6FKL');
      audio.play().catch(() => {
        // 알림음 재생 실패 시 무시
      });
    } catch (e) {
      // 알림음 재생 불가 시 무시
    }
  }
  
  showNotification() {
    if ('Notification' in window && Notification.permission === 'granted') {
      const title = this.currentMode === 'work' ? '작업 완료!' : '휴식 완료!';
      const body = this.currentMode === 'work' ? '휴식 시간입니다.' : '작업을 시작하세요.';
      
      new Notification(title, {
        body: body,
        icon: '/assets/images/favicon.ico'
      });
    } else if ('Notification' in window && Notification.permission !== 'denied') {
      Notification.requestPermission().then(permission => {
        if (permission === 'granted') {
          this.showNotification();
        }
      });
    }
  }
  
  saveStats() {
    localStorage.setItem('pomodoroCompletedCount', this.completedPomodoros.toString());
  }
  
  loadStats() {
    const saved = localStorage.getItem('pomodoroCompletedCount');
    if (saved) {
      this.completedPomodoros = parseInt(saved, 10) || 0;
    }
    this.updateStatsDisplay();
  }
}

// 페이지 로드 시 타이머 초기화
document.addEventListener('DOMContentLoaded', () => {
  new PomodoroTimer();
});
</script> 