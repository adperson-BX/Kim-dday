# Kim-dday
김혜영 D-day 운용앱 
<!DOCTYPE html>

<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="theme-color" content="#0a0a0a">
<title>김혜영 D-Day</title>
<link rel="manifest" href="./manifest.json">
<link rel="apple-touch-icon" href="./icon-192.png">
<link rel="apple-touch-icon" sizes="192x192" href="./icon-192.png">
<link rel="apple-touch-icon" sizes="512x512" href="./icon-512.png">
<link rel="icon" type="image/png" sizes="192x192" href="./icon-192.png">
<link rel="icon" type="image/png" sizes="512x512" href="./icon-512.png">
<style>
* { margin: 0; padding: 0; box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
:root {
  --bg: #0a0a0a;
  --surface: #1a1a1a;
  --surface2: #242424;
  --border: #2e2e2e;
  --text: #e8e8e8;
  --text-dim: #888;
  --accent: #f5b942;
  --accent-dim: #8a6627;
  --danger: #ff5252;
  --warn: #ffa726;
  --ok: #66bb6a;
  --info: #5e9eff;
  --done: #4a4a4a;
}
html, body {
  background: var(--bg);
  color: var(--text);
  font-family: -apple-system, BlinkMacSystemFont, 'Pretendard', system-ui, sans-serif;
  font-size: 15px;
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
  overscroll-behavior: none;
}
body {
  padding-bottom: 80px;
  min-height: 100vh;
}

/* Header */
header {
background: var(–surface);
border-bottom: 1px solid var(–border);
padding: 12px 16px;
position: sticky;
top: 0;
z-index: 100;
backdrop-filter: blur(20px);
-webkit-backdrop-filter: blur(20px);
}
.header-row { display: flex; justify-content: space-between; align-items: center; }
.title { font-size: 17px; font-weight: 700; }
.title small { font-weight: 400; color: var(–text-dim); margin-left: 6px; font-size: 12px; }
.now { font-size: 12px; color: var(–accent); font-variant-numeric: tabular-nums; }
.countdown {
font-size: 11px;
color: var(–text-dim);
margin-top: 4px;
font-variant-numeric: tabular-nums;
}

/* Tab bar (bottom) */
nav.tabs {
position: fixed;
bottom: 0; left: 0; right: 0;
background: var(–surface);
border-top: 1px solid var(–border);
display: flex;
z-index: 100;
padding-bottom: env(safe-area-inset-bottom, 0);
overflow-x: auto;
scrollbar-width: none;
}
nav.tabs::-webkit-scrollbar { display: none; }
nav.tabs button {
flex: 1 0 auto;
min-width: 56px;
background: none;
border: none;
color: var(–text-dim);
padding: 8px 4px;
font-size: 10px;
cursor: pointer;
display: flex;
flex-direction: column;
align-items: center;
gap: 2px;
font-family: inherit;
white-space: nowrap;
}
nav.tabs button .ico { font-size: 20px; }
nav.tabs button.active { color: var(–accent); }

/* Main content */
main { padding: 12px 14px 20px; }
section { display: none; }
section.active { display: block; }

/* Cards */
.card {
background: var(–surface);
border: 1px solid var(–border);
border-radius: 12px;
padding: 14px;
margin-bottom: 10px;
}
.card h2 {
font-size: 14px;
font-weight: 600;
margin-bottom: 10px;
color: var(–accent);
display: flex;
align-items: center;
gap: 6px;
}
.card h3 {
font-size: 13px;
font-weight: 600;
margin: 14px 0 6px;
color: var(–text);
}
.card p { color: var(–text-dim); font-size: 13px; }

/* Phase / Time block headers */
.phase {
background: var(–surface2);
border-left: 3px solid var(–accent);
padding: 8px 12px;
margin: 14px -14px 8px;
font-weight: 600;
font-size: 13px;
}
.phase.danger { border-left-color: var(–danger); }
.phase.warn { border-left-color: var(–warn); }
.phase.ok { border-left-color: var(–ok); }
.phase .time {
color: var(–accent);
font-weight: 700;
font-variant-numeric: tabular-nums;
margin-right: 6px;
}
.phase.danger .time { color: var(–danger); }

/* Checkbox items */
.check {
display: flex;
align-items: flex-start;
gap: 10px;
padding: 10px 8px;
border-radius: 8px;
cursor: pointer;
transition: background 0.15s;
user-select: none;
-webkit-user-select: none;
}
.check:active { background: var(–surface2); }
.check input[type=checkbox] {
appearance: none;
-webkit-appearance: none;
width: 22px; height: 22px;
min-width: 22px;
border: 2px solid var(–border);
border-radius: 6px;
background: var(–bg);
cursor: pointer;
position: relative;
margin-top: 1px;
}
.check input[type=checkbox]:checked {
background: var(–accent);
border-color: var(–accent);
}
.check input[type=checkbox]:checked::after {
content: ‘’;
position: absolute;
left: 5px; top: 1px;
width: 6px; height: 11px;
border: solid var(–bg);
border-width: 0 2.5px 2.5px 0;
transform: rotate(45deg);
}
.check label {
flex: 1;
font-size: 14px;
line-height: 1.45;
cursor: pointer;
}
.check input:checked ~ label {
color: var(–done);
text-decoration: line-through;
}
.check.crit label::before {
content: ‘★’;
color: var(–danger);
font-weight: 700;
margin-right: 4px;
}
.check.crit3 label::before {
content: ‘★★★’;
color: var(–danger);
font-weight: 700;
margin-right: 4px;
letter-spacing: -1px;
}
.check.crit2 label::before {
content: ‘★★’;
color: var(–warn);
font-weight: 700;
margin-right: 4px;
letter-spacing: -1px;
}

/* Tables */
.spec {
width: 100%;
border-collapse: collapse;
font-size: 13px;
margin: 8px 0;
}
.spec td {
padding: 8px 6px;
border-bottom: 1px solid var(–border);
vertical-align: top;
}
.spec td:first-child {
color: var(–text-dim);
width: 40%;
font-size: 12px;
}
.spec td:last-child { color: var(–text); font-weight: 500; }
.spec tr:last-child td { border-bottom: none; }
.spec td .h { color: var(–accent); font-weight: 600; }

/* Buttons / actions */
.actions {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 8px;
margin-top: 8px;
}
.actions a, .actions button {
background: var(–surface2);
border: 1px solid var(–border);
color: var(–text);
padding: 12px;
border-radius: 10px;
font-size: 13px;
font-weight: 500;
text-align: center;
text-decoration: none;
display: flex;
flex-direction: column;
gap: 2px;
align-items: center;
font-family: inherit;
cursor: pointer;
}
.actions a:active, .actions button:active { background: var(–border); }
.actions .ico { font-size: 18px; }
.actions a small { color: var(–text-dim); font-size: 11px; }
.btn-call { background: var(–ok); border-color: var(–ok); color: white; }
.btn-call small { color: rgba(255,255,255,0.8); }

/* Pill / badges */
.pill {
display: inline-block;
padding: 2px 8px;
border-radius: 10px;
font-size: 11px;
font-weight: 500;
background: var(–surface2);
color: var(–text-dim);
margin-right: 4px;
}
.pill.danger { background: rgba(255,82,82,0.15); color: var(–danger); }
.pill.warn { background: rgba(255,167,38,0.15); color: var(–warn); }
.pill.ok { background: rgba(102,187,106,0.15); color: var(–ok); }
.pill.info { background: rgba(94,158,255,0.15); color: var(–info); }

/* Now (대시보드) */
.now-hero {
background: linear-gradient(135deg, #2a1f10, #1a1410);
border: 1px solid var(–accent-dim);
border-radius: 14px;
padding: 18px;
margin-bottom: 12px;
}
.now-hero .label { color: var(–accent); font-size: 11px; letter-spacing: 1px; font-weight: 600; }
.now-hero .next-task { font-size: 18px; font-weight: 700; margin-top: 6px; line-height: 1.4; }
.now-hero .next-time { color: var(–text-dim); margin-top: 4px; font-size: 13px; }
.progress-stack { margin-top: 12px; display: flex; flex-direction: column; gap: 8px; }
.progress-row { display: flex; justify-content: space-between; align-items: center; font-size: 12px; }
.progress-row .name { color: var(–text-dim); }
.progress-row .pct { color: var(–accent); font-weight: 600; font-variant-numeric: tabular-nums; }
.progress-bar {
width: 100%;
height: 6px;
background: var(–surface2);
border-radius: 3px;
overflow: hidden;
margin-top: 4px;
}
.progress-bar .fill { height: 100%; background: var(–accent); transition: width 0.3s; }

/* Lighting diagram */
.diagram-wrap {
background: var(–surface2);
border-radius: 10px;
padding: 8px;
overflow: hidden;
margin: 8px 0;
}
.diagram-wrap svg { width: 100%; height: auto; display: block; }

/* Reset button */
.reset-btn {
background: var(–surface2);
border: 1px solid var(–border);
color: var(–danger);
padding: 10px 16px;
border-radius: 8px;
font-size: 12px;
cursor: pointer;
font-family: inherit;
margin-top: 12px;
}

/* Hint */
.hint {
background: rgba(94,158,255,0.08);
border-left: 3px solid var(–info);
padding: 10px 12px;
border-radius: 6px;
margin: 8px 0;
font-size: 12px;
color: var(–text-dim);
line-height: 1.5;
}
.hint.danger { background: rgba(255,82,82,0.08); border-color: var(–danger); }
.hint.warn { background: rgba(255,167,38,0.08); border-color: var(–warn); }

/* Person card */
.person {
background: var(–surface2);
border-radius: 10px;
padding: 14px;
margin-bottom: 10px;
}
.person .name { font-size: 15px; font-weight: 600; }
.person .role { color: var(–text-dim); font-size: 12px; margin-top: 2px; }
.person .actions { margin-top: 10px; }

/* Place card */
.place {
background: var(–surface2);
border-radius: 10px;
padding: 14px;
margin-bottom: 10px;
}
.place .name { font-size: 15px; font-weight: 600; }
.place .addr { color: var(–text-dim); font-size: 12px; margin-top: 4px; }
.place .meta { color: var(–accent); font-size: 11px; margin-top: 4px; }

/* Camera setup highlights */
.cam-card {
background: var(–surface2);
border-radius: 12px;
padding: 14px;
margin-bottom: 10px;
border-left: 3px solid var(–accent);
}
.cam-card.b { border-left-color: var(–info); }
.cam-card.c { border-left-color: var(–ok); }
.cam-card .role { font-size: 11px; letter-spacing: 1px; color: var(–text-dim); }
.cam-card .name { font-size: 16px; font-weight: 700; margin-top: 2px; }

/* Trouble */
.trouble {
background: var(–surface2);
border-radius: 10px;
padding: 12px;
margin-bottom: 10px;
}
.trouble .symptom {
color: var(–danger);
font-weight: 600;
font-size: 14px;
margin-bottom: 6px;
}
.trouble .fix {
color: var(–text);
font-size: 13px;
line-height: 1.55;
}
.trouble .fix strong { color: var(–accent); }

footer-spacer { display: block; height: 40px; }
</style>

</head>
<body>

<header>
  <div class="header-row">
    <div>
      <div class="title">🎬 김혜영 D-Day <small>04.29 수</small></div>
      <div class="countdown" id="countdown">로딩...</div>
    </div>
    <div class="now" id="clock">--:--</div>
  </div>
</header>

<main>

<!-- ============= 🚀 지금 ============= -->

<section id="tab-now" class="active">
  <div class="now-hero">
    <div class="label">NOW · 지금 해야 할 일</div>
    <div class="next-task" id="next-task">로딩 중...</div>
    <div class="next-time" id="next-time"></div>
  </div>

  <div class="card">
    <h2>📊 진행률</h2>
    <div class="progress-stack" id="progress-stack"></div>
  </div>

  <div class="card">
    <h2>🚨 절대 빠뜨리지 말 것</h2>
    <div class="check crit3"><input type="checkbox" id="crit-1" data-key="crit-grey"><label for="crit-1">그레이카드로 두 FX3 동시 WB 설정 (D-Day 11:35)</label></div>
    <div class="check crit3"><input type="checkbox" id="crit-2" data-key="crit-backup"><label for="crit-2">SD → SSD 1차 백업 (D-Day 16:00, 포맷 절대 금지)</label></div>
    <div class="check crit2"><input type="checkbox" id="crit-3" data-key="crit-32bit"><label for="crit-3">Rode 32bit float ON 확인</label></div>
    <div class="check crit2"><input type="checkbox" id="crit-4" data-key="crit-light"><label for="crit-4">자연광 블라인드 100% 차폐</label></div>
    <div class="check crit2"><input type="checkbox" id="crit-5" data-key="crit-rec"><label for="crit-5">두 카메라 REC 동시 시작 (13:15)</label></div>
    <div class="check crit"><input type="checkbox" id="crit-6" data-key="crit-pickup"><label for="crit-6">쿨샷 20:00 마감 전 픽업 완료</label></div>
  </div>

  <div class="card">
    <h2>⚡ 빠른 실행</h2>
    <div class="actions">
      <a href="tel:010-9339-6339" class="btn-call"><span class="ico">📞</span><strong>쿨샷 조창석</strong><small>010-9339-6339</small></a>
      <a href="tel:010-5136-5246"><span class="ico">📞</span><strong>선혜민 PD</strong><small>010-5136-5246</small></a>
      <button onclick="switchTab('camera')"><span class="ico">🎥</span><strong>카메라 설정</strong><small>FX3 / A7IV</small></button>
      <button onclick="switchTab('light')"><span class="ico">💡</span><strong>조명 구조도</strong><small>Key·Rim·NF</small></button>
    </div>
  </div>
</section>

<!-- ============= 📋 D-1 ============= -->

<section id="tab-d1">
  <div class="card">
    <h2>📋 D-1 체크리스트</h2>
    <p style="font-size:12px;">04.28 화 · 광주→대구 출장 + 픽업 + 테스트 촬영</p>
  </div>

  <div class="phase"><span class="time">09:00</span>대외협력팀 (메시지)</div>
  <div class="check crit"><input type="checkbox" data-key="d1-09-1"><label>일정 변경 메시지 카카오워크 발송</label></div>
  <div class="check"><input type="checkbox" data-key="d1-09-2"><label>인터뷰이 도착 13:00 변경 안내</label></div>
  <div class="check"><input type="checkbox" data-key="d1-09-3"><label>하루에, 11:00~12:30 시간 안내</label></div>

  <div class="phase"><span class="time">09:30</span>대구영상미디어센터 (취소)</div>
  <div class="check crit"><input type="checkbox" data-key="d1-0930-1"><label>기존 신청 102,300원 전체 취소</label></div>
  <div class="check"><input type="checkbox" data-key="d1-0930-2"><label>환불 절차 + 환불 계좌 등록</label></div>

  <div class="phase"><span class="time">10:00</span>쿨샷카메라 (조창석 010-9339-6339)</div>
  <div class="check crit"><input type="checkbox" data-key="d1-10-1"><label>35mm GM + 포르자 500 추가 가능 여부</label></div>
  <div class="check crit"><input type="checkbox" data-key="d1-10-2"><label>20:00 픽업 + 다음날 20:00 반납 재확인</label></div>
  <div class="check"><input type="checkbox" data-key="d1-10-3"><label>10품목 재고 재확인</label></div>
  <div class="check"><input type="checkbox" data-key="d1-10-4"><label>보증금 금액 + 결제 방식 (카드 가능?)</label></div>
  <div class="check"><input type="checkbox" data-key="d1-10-5"><label>FX3 예비 배터리 동봉 가능?</label></div>

  <div class="phase"><span class="time">10:30</span>릴리프 스튜디오</div>
  <div class="check crit"><input type="checkbox" data-key="d1-1030-1"><label>영상팀 10:00 별도 입장 가능?</label></div>
  <div class="check"><input type="checkbox" data-key="d1-1030-2"><label>검정천 자체 보유?</label></div>
  <div class="check"><input type="checkbox" data-key="d1-1030-3"><label>콘센트 위치·개수 확인</label></div>
  <div class="check"><input type="checkbox" data-key="d1-1030-4"><label>베이지 라운지 1순위 확정</label></div>

  <div class="phase"><span class="time">11:00</span>하루에, 헤메샵</div>
  <div class="check"><input type="checkbox" data-key="d1-11-1"><label>11:00~12:30 예약 재확인</label></div>
  <div class="check"><input type="checkbox" data-key="d1-11-2"><label>130,000원 결제 (안희영 카카오뱅크 3333-17-4235702)</label></div>
  <div class="check"><input type="checkbox" data-key="d1-11-3"><label>12:30 정확 종료 가능 여부</label></div>

  <div class="phase warn"><span class="time">12:00~15:30</span>보유 장비 점검 + 출장 준비물</div>
  <div class="check"><input type="checkbox" data-key="d1-12-1"><label>FX3 펌웨어 + 배터리 ×3 풀충전</label></div>
  <div class="check"><input type="checkbox" data-key="d1-12-2"><label>A7IV 배터리 ×2 풀충전</label></div>
  <div class="check"><input type="checkbox" data-key="d1-12-3"><label>Rode RX·TX1·TX2 충전 + 페어링 + 32bit float ON</label></div>
  <div class="check"><input type="checkbox" data-key="d1-12-4"><label>SD ×4 카메라 내 포맷</label></div>
  <div class="check"><input type="checkbox" data-key="d1-12-5"><label>1TB SSD 빈 공간 100GB+ 확보</label></div>
  <div class="check crit"><input type="checkbox" data-key="d1-12-6"><label>그레이카드 보유 확인 (없으면 대구 도착 후 구매)</label></div>
  <div class="check crit"><input type="checkbox" data-key="d1-12-7"><label>검정 폼보드 또는 검정 옷·천 확보</label></div>
  <div class="check"><input type="checkbox" data-key="d1-12-8"><label>신분증 ×3 + 사업자등록증</label></div>
  <div class="check"><input type="checkbox" data-key="d1-12-9"><label>보증금 결제 수단 (카드/현금)</label></div>
  <div class="check"><input type="checkbox" data-key="d1-12-10"><label>모든 케이블·어댑터·멀티탭 ×2</label></div>

  <div class="phase"><span class="time">15:30~16:00</span>출발 준비</div>
  <div class="check"><input type="checkbox" data-key="d1-1530-1"><label>차량 적재 (광주 북구 군왕로 51번길 118)</label></div>
  <div class="check"><input type="checkbox" data-key="d1-1530-2"><label>스타리아 주유 + 하이패스 잔액 확인</label></div>
  <div class="check"><input type="checkbox" data-key="d1-1530-3"><label>16:00 정시 출발 (3인)</label></div>

  <div class="phase"><span class="time">16:00~19:30</span>광주 → 대구 이동</div>
  <div class="check"><input type="checkbox" data-key="d1-16-1"><label>17:30~18:00 휴게소 1회 정차</label></div>
  <div class="check"><input type="checkbox" data-key="d1-16-2"><label>17:30 50% 지점 확인</label></div>

  <div class="phase danger"><span class="time">19:30~20:00</span>쿨샷카메라 픽업 ★</div>
  <div class="check crit3"><input type="checkbox" data-key="d1-19-1"><label>20:00 마감 전 도착 (대구 중구 문화동 9-14)</label></div>
  <div class="check crit"><input type="checkbox" data-key="d1-19-2"><label>FX3 바디: 외관·셔터·전원·메뉴</label></div>
  <div class="check crit"><input type="checkbox" data-key="d1-19-3"><label>35mm GM + 85mm GM: 마운트·AF·초점링</label></div>
  <div class="check"><input type="checkbox" data-key="d1-19-4"><label>NANLITE 300B II + 60B II + 포르자 500: 점등·색온도</label></div>
  <div class="check"><input type="checkbox" data-key="d1-19-5"><label>젬볼·C스탠드·맨프로토·ATEM Mini Pro</label></div>
  <div class="check"><input type="checkbox" data-key="d1-19-6"><label>보증금 결제 + 영수증 사진 촬영</label></div>
  <div class="check crit"><input type="checkbox" data-key="d1-19-7"><label>반납 일시 04.29(수) 20:00 재확인</label></div>

  <div class="phase"><span class="time">20:00~20:30</span>숙소 체크인 (동성로 스위트 호텔)</div>
  <div class="check"><input type="checkbox" data-key="d1-20-1"><label>여기어때 회원임 알림 + 신분증</label></div>
  <div class="check"><input type="checkbox" data-key="d1-20-2"><label>디럭스 더블 1 + 스위트 트윈 1 (각 2인 기준)</label></div>
  <div class="check"><input type="checkbox" data-key="d1-20-3"><label>모든 배터리 충전기 연결</label></div>

  <div class="phase ok"><span class="time">20:30~21:30</span>저녁</div>
  <div class="check"><input type="checkbox" data-key="d1-2030-1"><label>가벼운 메뉴 + 카페인 음료 확보</label></div>

  <div class="phase danger"><span class="time">21:30~23:00</span>테스트 촬영 ★ (D-Day 리허설)</div>
  <div class="check crit3"><input type="checkbox" data-key="d1-21-1"><label>그레이카드 두 카메라 동시 WB 설정 절차 익히기</label></div>
  <div class="check crit"><input type="checkbox" data-key="d1-21-2"><label>두 FX3 + GM 렌즈 마운트</label></div>
  <div class="check crit"><input type="checkbox" data-key="d1-21-3"><label>NANLITE 300B II + 60B II + 포르자 500 4000K 통일</label></div>
  <div class="check"><input type="checkbox" data-key="d1-21-4"><label>30초 테스트 클립 ×2 → LCD 비교</label></div>
  <div class="check"><input type="checkbox" data-key="d1-21-5"><label>Rode로 NANLITE 팬 소음 측정</label></div>
  <div class="check"><input type="checkbox" data-key="d1-21-6"><label>35mm + 85mm GM AF 작동 확인</label></div>
  <div class="check"><input type="checkbox" data-key="d1-21-7"><label>테스트 결과 메모 + D-Day 적용 사항 정리</label></div>

  <div class="phase"><span class="time">23:00~23:30</span>취침 준비</div>
  <div class="check"><input type="checkbox" data-key="d1-23-1"><label>모든 배터리 풀충 세팅</label></div>
  <div class="check"><input type="checkbox" data-key="d1-23-2"><label>D-Day 적재 순서 최종 확인</label></div>
  <div class="check"><input type="checkbox" data-key="d1-23-3"><label>23:30 취침 (07:30 기상)</label></div>

<button class="reset-btn" onclick="resetSection('d1')">D-1 체크 전체 초기화</button>

</section>

<!-- ============= 🎬 D-Day ============= -->

<section id="tab-dday">
  <div class="card">
    <h2>🎬 D-Day 체크리스트</h2>
    <p style="font-size:12px;">04.29 수 · 시간순으로 위에서 아래</p>
  </div>

  <div class="phase ok"><span class="time">07:30~09:30</span>아침 준비</div>
  <div class="check"><input type="checkbox" data-key="dd-07-1"><label>07:30 기상 → 08:00~09:00 조식</label></div>
  <div class="check"><input type="checkbox" data-key="dd-07-2"><label>09:00~09:30 체크아웃 + 차량 적재</label></div>
  <div class="check"><input type="checkbox" data-key="dd-07-3"><label>차량 우측: 렌탈 장비 (FX3·GM·NANLITE·맨프로토·C스탠드)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-07-4"><label>차량 좌측: 보유 장비 (FX3·A7IV·24-70·Rode·SmallRig·SD·SSD)</label></div>
  <div class="check crit"><input type="checkbox" data-key="dd-07-5"><label>그레이카드 + 검정 폼보드 별도 챙김 확인</label></div>
  <div class="check"><input type="checkbox" data-key="dd-07-6"><label>모든 배터리 풀충전 상태 확인</label></div>
  <div class="check"><input type="checkbox" data-key="dd-07-7"><label>09:30 숙소 출발</label></div>

  <div class="phase"><span class="time">09:30~10:00</span>스튜디오 이동</div>
  <div class="check"><input type="checkbox" data-key="dd-0930-1"><label>자차 이동 (중구 향촌동 → 달서구 약 30분)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-0930-2"><label>10:00 릴리프 스튜디오 정확 도착</label></div>

  <div class="phase"><span class="time">10:00~10:25</span>페이즈 1 — 입장 + 자연광 차폐</div>
  <div class="check"><input type="checkbox" data-key="dd-p1-1"><label>스튜디오 입장 + 인사 + 화장실·전원 위치</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p1-2"><label>박유리: 차량 → 장비 1차 운반 (조명·삼각대)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p1-3"><label>박유리: 차량 → 장비 2차 운반 (카메라·렌즈·음향)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p1-4"><label>위정재: 블라인드 100% 닫기</label></div>
  <div class="check crit2"><input type="checkbox" data-key="dd-p1-5"><label>검정천 추가 차폐 (창틀·문 틈)</label></div>
  <div class="check crit3"><input type="checkbox" data-key="dd-p1-6"><label>★ 체크포인트 (10:25): 모든 조명 OFF 상태에서 거의 어두움</label></div>

  <div class="phase"><span class="time">10:25~10:55</span>페이즈 2 — 조명 세팅 (4등 체제)</div>
  <div class="check"><input type="checkbox" data-key="dd-p2-1"><label>NANLITE 300B II 좌측 45° 설치 (~2m, Key)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p2-2"><label>젬볼/랜턴 디퓨저 장착</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p2-3"><label>NANLITE 60B II 후방 측면 45° (~1.5m, Rim)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p2-4"><label>NANLITE 포르자 500 (배경 또는 보조)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p2-5"><label>모든 조명 4000K 통일 + 출력 35%/25%/조정</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p2-6"><label>박유리 인터뷰이 자리에 앉혀 시뮬레이션</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p2-7"><label>검정 폼보드 우측 1m 배치 (Negative Fill)</label></div>
  <div class="check crit3"><input type="checkbox" data-key="dd-p2-8"><label>★ 체크포인트 (10:55): 좌측 자연 밝음 + 우측 그림자 + 머리카락 림 라이트</label></div>

  <div class="phase danger"><span class="time">10:55~11:35</span>페이즈 3 — 카메라 세팅 ★ 가장 중요</div>
  <div class="check"><input type="checkbox" data-key="dd-p3-1"><label>CAM A: SmallRig + 보유 FX3 + 35mm GM (좌-정면)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p3-2"><label>CAM B: 맨프로토 504HD + 렌탈 FX3 + 85mm GM (우-정면)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p3-3"><label>두 카메라 아이레벨 (앉은 자세 1.40~1.45m)</label></div>
  <div class="check crit"><input type="checkbox" data-key="dd-p3-4"><label>두 카메라 CineEI 모드 + Base Look S-Log3/S-Gamut3.Cine</label></div>
  <div class="check crit"><input type="checkbox" data-key="dd-p3-5"><label>두 카메라 EI 800 통일</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p3-6"><label>두 카메라 4K 24p XAVC S 100Mbps + 셔터 1/50</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p3-7"><label>모니터 LUT 1 (s709) 통일</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p3-8"><label>SD 카드 ×2 양쪽 카메라 삽입</label></div>
  <div class="check crit3"><input type="checkbox" data-key="dd-p3-9"><label>★★★ 그레이카드로 두 카메라 동시 WB 설정</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p3-10"><label>양쪽 모니터 비교 → 색감 일치 확인</label></div>
  <div class="check crit3"><input type="checkbox" data-key="dd-p3-11"><label>★ 체크포인트 (11:35): 두 카메라 색감 동일 + 화각 정확</label></div>

  <div class="phase"><span class="time">11:35~11:55</span>페이즈 4 — 음향 세팅</div>
  <div class="check"><input type="checkbox" data-key="dd-p4-1"><label>CAM A에 Rode RX 장착 + 페어링</label></div>
  <div class="check crit2"><input type="checkbox" data-key="dd-p4-2"><label>TX1·TX2 32bit float 내부 녹음 ON</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p4-3"><label>TX1·TX2 라벨 테이프 표시</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p4-4"><label>NANLITE 팬 소음 측정 (인터뷰이 위치 < -40dB)</label></div>
  <div class="check crit"><input type="checkbox" data-key="dd-p4-5"><label>★ 체크포인트 (11:55): 페어링 LED 녹색 + 32bit float ON + 팬 소음 OK</label></div>

  <div class="phase warn"><span class="time">11:55~12:30</span>페이즈 5 — 통합 테스트 + 미세 조정</div>
  <div class="check"><input type="checkbox" data-key="dd-p5-1"><label>테스트 클립 1: 박유리 자리 30초 녹화 (A·B·음향)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p5-2"><label>LCD 재생 + 색감·노출·오디오 파형 확인</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p5-3"><label>테스트 클립 2: 다양한 표정·각도</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p5-4"><label>테스트 클립 SSD 백업 워크플로우 검증</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p5-5"><label>인터뷰이 자리 마킹 (테이프)</label></div>
  <div class="check crit"><input type="checkbox" data-key="dd-p5-6"><label>★ 체크포인트 (12:30): 모든 시스템 정상 + 자리 마킹 완료</label></div>

  <div class="phase"><span class="time">12:30~13:00</span>페이즈 6 — 인터뷰이 도착 대기</div>
  <div class="check"><input type="checkbox" data-key="dd-p6-1"><label>CAM C (A7IV) 준비 + S-Cinetone</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p6-2"><label>BTS 동선 익히기 + 인물사진 3공간 답사</label></div>
  <div class="check"><input type="checkbox" data-key="dd-p6-3"><label>모든 카메라 REC 대기 상태</label></div>

  <div class="phase danger"><span class="time">13:00~14:45</span>인터뷰 영상 촬영 ★</div>
  <div class="check"><input type="checkbox" data-key="dd-int-1"><label>13:00 인터뷰이 환영 + 마이크 부착 + 음향 테스트</label></div>
  <div class="check crit3"><input type="checkbox" data-key="dd-int-2"><label>13:15 두 카메라 REC 동시 시작 (점멸 양쪽 확인)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-int-3"><label>A블록 30분 (13:20~13:50, 노하우/스킬)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-int-4"><label>A 종료 → 5분 휴식 + 메모리·배터리 확인</label></div>
  <div class="check"><input type="checkbox" data-key="dd-int-5"><label>B블록 25분 (13:55~14:20, 에피소드/공감)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-int-6"><label>B 종료 → 5분 휴식 + 확인</label></div>
  <div class="check"><input type="checkbox" data-key="dd-int-7"><label>C블록 15분 (14:25~14:40, 추가 질문)</label></div>
  <div class="check"><input type="checkbox" data-key="dd-int-8"><label>태깅표 최종 확인 (A·B·C 커버 여부)</label></div>

  <div class="phase ok"><span class="time">14:45~16:00</span>인물 프로필 사진</div>
  <div class="check"><input type="checkbox" data-key="dd-pic-1"><label>14:45~15:00 백드롭 체인지 + 카메라 재배치</label></div>
  <div class="check"><input type="checkbox" data-key="dd-pic-2"><label>15:00~15:20 책장 (자연 분위기) — 20컷+</label></div>
  <div class="check"><input type="checkbox" data-key="dd-pic-3"><label>15:20~15:40 화이트 룸 — 20컷+</label></div>
  <div class="check"><input type="checkbox" data-key="dd-pic-4"><label>15:40~16:00 베이지 라운지 (EO 톤) — 20컷+</label></div>
  <div class="check"><input type="checkbox" data-key="dd-pic-5"><label>표정·자세 다양화</label></div>

  <div class="phase danger"><span class="time">16:00~17:00</span>데이터 백업 + 철수</div>
  <div class="check crit3"><input type="checkbox" data-key="dd-bk-1"><label>★★★ SD → SSD 1차 백업 (현장 필수)</label></div>
  <div class="check crit"><input type="checkbox" data-key="dd-bk-2"><label>백업 완료 검증 (파일 수 + 용량)</label></div>
  <div class="check crit3"><input type="checkbox" data-key="dd-bk-3"><label>SD 카드 절대 포맷 금지</label></div>
  <div class="check"><input type="checkbox" data-key="dd-bk-4"><label>렌탈 장비 별도 패킹 + 보유 장비 별도 패킹</label></div>
  <div class="check"><input type="checkbox" data-key="dd-bk-5"><label>스튜디오 원상복구 + 검정천 회수</label></div>
  <div class="check"><input type="checkbox" data-key="dd-bk-6"><label>인터뷰이 환송 + 감사 인사</label></div>
  <div class="check"><input type="checkbox" data-key="dd-bk-7"><label>17:00 스튜디오 출발</label></div>

  <div class="phase"><span class="time">17:00~19:00</span>쿨샷카메라 반납</div>
  <div class="check"><input type="checkbox" data-key="dd-rt-1"><label>17:00~18:30 자차 이동 (퇴근시간 35~50분)</label></div>
  <div class="check crit"><input type="checkbox" data-key="dd-rt-2"><label>~19:00 도착 + 장비 검수 + 반납</label></div>
  <div class="check"><input type="checkbox" data-key="dd-rt-3"><label>10품목 누락·파손 없음 확인 + 보증금 환불</label></div>
  <div class="check"><input type="checkbox" data-key="dd-rt-4"><label>20:00 마감 전 반납 완료</label></div>

  <div class="phase ok"><span class="time">19:00~20:00</span>저녁</div>
  <div class="check"><input type="checkbox" data-key="dd-d-1"><label>대구 중구 인근 식당</label></div>
  <div class="check"><input type="checkbox" data-key="dd-d-2"><label>운전자 교대 검토</label></div>

  <div class="phase warn"><span class="time">20:00~23:00</span>광주 복귀</div>
  <div class="check"><input type="checkbox" data-key="dd-rt2-1"><label>20:00 광주 출발</label></div>
  <div class="check"><input type="checkbox" data-key="dd-rt2-2"><label>21:30경 휴게소 1회 정차</label></div>
  <div class="check crit"><input type="checkbox" data-key="dd-rt2-3"><label>운전자 피로도 체크</label></div>
  <div class="check"><input type="checkbox" data-key="dd-rt2-4"><label>~23:00 광주 도착</label></div>
  <div class="check"><input type="checkbox" data-key="dd-rt2-5"><label>D-Day 종료 카카오워크 공지</label></div>

<button class="reset-btn" onclick="resetSection('dd')">D-Day 체크 전체 초기화</button>

</section>

<!-- ============= 🎥 카메라 ============= -->

<section id="tab-camera">
  <div class="card">
    <h2>🎥 카메라별 시네마틱 설정</h2>
    <p style="font-size:12px;">컨셉: EO Korea 톤 (다크·시네마틱)</p>
  </div>

  <div class="card">
    <h2>🎬 공통 베이스 (3대 모두)</h2>
    <table class="spec">
      <tr><td>해상도</td><td><span class="h">4K (3840×2160)</span></td></tr>
      <tr><td>화이트밸런스</td><td><span class="h">★★★ 그레이카드 커스텀 WB</span></td></tr>
      <tr><td>측광</td><td>스폿 (얼굴 기준)</td></tr>
      <tr><td>AF 모드</td><td>AF-C + 얼굴/눈 인식 ON</td></tr>
    </table>
  </div>

  <div class="cam-card">
    <div class="role">CAM A · 메인 인터뷰 ★</div>
    <div class="name">FX3 (보유) + 35mm GM</div>
    <table class="spec">
      <tr><td>모드</td><td><span class="h">CineEI 모드</span></td></tr>
      <tr><td>Base Look</td><td><span class="h">S-Log3 / S-Gamut3.Cine</span></td></tr>
      <tr><td>EI</td><td><span class="h">800 (Base)</span></td></tr>
      <tr><td>모니터 LUT</td><td>LUT 1 (s709)</td></tr>
      <tr><td>조리개</td><td>F2.8 ~ F4.0</td></tr>
      <tr><td>프레임</td><td>24p</td></tr>
      <tr><td>코덱</td><td>XAVC S 4K 100Mbps</td></tr>
      <tr><td>셔터</td><td>1/50 (180°)</td></tr>
      <tr><td>샷 사이즈</td><td>MS (상반신+손)</td></tr>
      <tr><td>위치</td><td>좌-정면 2.5m, 아이레벨</td></tr>
      <tr><td>음원</td><td>Rode RX 장착 (메인)</td></tr>
      <tr><td>제브라</td><td>70±5% (얼굴)</td></tr>
      <tr><td>SteadyShot</td><td>OFF (삼각대)</td></tr>
    </table>
  </div>

  <div class="cam-card b">
    <div class="role">CAM B · 사이드 CU</div>
    <div class="name">FX3 (렌탈) + 85mm GM</div>
    <div class="hint">CAM A와 모드/EI/Base Look/프레임/코덱/셔터/WB 완전 동일. <strong>조리개와 화각만 다름.</strong></div>
    <table class="spec">
      <tr><td>모드</td><td><span class="h">CineEI / S-Log3 / EI 800</span></td></tr>
      <tr><td>조리개</td><td><span class="h">F2.0 ~ F2.8 (한 스톱 더 열기)</span></td></tr>
      <tr><td>샷 사이즈</td><td>CU (얼굴 클로즈업)</td></tr>
      <tr><td>위치</td><td>우-정면 3m, 아이레벨</td></tr>
      <tr><td>음원</td><td>없음 (CAM A로 동기화)</td></tr>
    </table>
  </div>

  <div class="cam-card c">
    <div class="role">CAM C · BTS / 메이킹</div>
    <div class="name">A7IV (보유) + 24-70mm</div>
    <div class="hint warn">A7IV는 FX3와 다른 워크플로우. S-Cinetone + 30p로 분리 운용.</div>
    <table class="spec">
      <tr><td>픽처 프로파일</td><td><span class="h">PP11 (S-Cinetone)</span></td></tr>
      <tr><td>ISO</td><td>Auto ISO (100~6400 제한)</td></tr>
      <tr><td>조리개</td><td>F2.8 ~ F4.0</td></tr>
      <tr><td>해상도</td><td>4K 30p</td></tr>
      <tr><td>셔터</td><td>1/60</td></tr>
      <tr><td>WB</td><td>Auto WB 또는 Daylight</td></tr>
      <tr><td>SteadyShot</td><td><span class="h">Active 모드 ON</span></td></tr>
      <tr><td>운용</td><td>핸드헬드 로밍 (박유리 어시)</td></tr>
    </table>
  </div>

  <div class="card">
    <h2>📊 S-Log3 노출 가이드</h2>
    <table class="spec">
      <tr><td>흰색 (옷·종이)</td><td>약 60~70 IRE</td></tr>
      <tr><td>★ 얼굴 (피부)</td><td><span class="h">약 65~70 IRE</span></td></tr>
      <tr><td>18% 그레이카드</td><td>약 41 IRE</td></tr>
      <tr><td>어두운 배경</td><td>약 30~40 IRE</td></tr>
      <tr><td>그림자 깊은 부분</td><td>약 20~25 IRE</td></tr>
    </table>
    <div class="hint warn">S-Log3는 살짝 오버 노출(+0.3~+0.7 EV) 권장. 후반 그레이딩에서 어두운 부분 끌어올리면 노이즈 증가.</div>
  </div>

  <div class="card">
    <h2>⚠️ 현장 운용 핵심</h2>
    <div class="check crit3"><input type="checkbox" data-key="cam-1"><label>그레이카드 두 카메라 동시 WB</label></div>
    <div class="check crit2"><input type="checkbox" data-key="cam-2"><label>두 FX3 REC 동시 시작 (편집 동기화용)</label></div>
    <div class="check crit2"><input type="checkbox" data-key="cam-3"><label>EI 800 고정 (변경 시 듀얼 매칭 깨짐)</label></div>
    <div class="check crit"><input type="checkbox" data-key="cam-4"><label>모니터 LUT 통일 (둘 다 LUT 1 / s709)</label></div>
    <div class="check"><input type="checkbox" data-key="cam-5"><label>SD 256GB 4K 100Mbps ≈ 5~6시간 / 인터뷰 90분 충분</label></div>
  </div>
</section>

<!-- ============= 💡 조명 ============= -->

<section id="tab-light">
  <div class="card">
    <h2>💡 조명 구조도</h2>
    <p style="font-size:12px;">EO 톤 인터뷰 · 4등 체제 + Negative Fill</p>
  </div>

  <div class="diagram-wrap">
    <svg viewBox="0 0 400 400" xmlns="http://www.w3.org/2000/svg">
      <defs>
        <marker id="arr" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
          <path d="M2 1L9 5L2 9" fill="none" stroke="#f5b942" stroke-width="1.5"/>
        </marker>
      </defs>
      <text x="200" y="20" text-anchor="middle" fill="#f5b942" font-size="13" font-weight="bold">탑다운 평면도</text>
      <rect x="40" y="40" width="320" height="320" fill="none" stroke="#444" stroke-dasharray="4 3"/>
      <rect x="160" y="50" width="80" height="14" fill="#3a2a1a" stroke="#854F0B"/>
      <text x="200" y="60" text-anchor="middle" fill="#888" font-size="9">배경</text>

```
  <ellipse cx="200" cy="200" rx="22" ry="16" fill="#5a3a4a" stroke="#cc6688" stroke-width="1"/>
  <text x="200" y="200" text-anchor="middle" fill="#fff" font-size="9">인터뷰이</text>
  <text x="200" y="212" text-anchor="middle" fill="#aaa" font-size="8">아이레벨</text>

  <rect x="80" y="130" width="36" height="36" rx="4" fill="#3a2810" stroke="#f5b942"/>
  <text x="98" y="150" text-anchor="middle" fill="#f5b942" font-size="9" font-weight="bold">Key</text>
  <text x="98" y="160" text-anchor="middle" fill="#f5b942" font-size="7">300B II</text>
  <text x="98" y="120" text-anchor="middle" fill="#888" font-size="8">좌45° · 2m</text>
  <text x="98" y="180" text-anchor="middle" fill="#888" font-size="8">35% / 4000K</text>
  <line x1="115" y1="166" x2="180" y2="200" stroke="#f5b942" stroke-width="1.5" opacity="0.7" marker-end="url(#arr)"/>

  <rect x="284" y="120" width="32" height="32" rx="4" fill="#0a1f3a" stroke="#5e9eff"/>
  <text x="300" y="138" text-anchor="middle" fill="#5e9eff" font-size="9" font-weight="bold">Rim</text>
  <text x="300" y="148" text-anchor="middle" fill="#5e9eff" font-size="7">60B II</text>
  <text x="300" y="110" text-anchor="middle" fill="#888" font-size="8">후방측 45°</text>
  <text x="300" y="166" text-anchor="middle" fill="#888" font-size="8">25% / 4000K</text>
  <line x1="285" y1="150" x2="222" y2="190" stroke="#5e9eff" stroke-width="1.3" opacity="0.6" marker-end="url(#arr)"/>

  <rect x="290" y="200" width="10" height="40" fill="#444" stroke="#888"/>
  <text x="320" y="216" fill="#aaa" font-size="9">Negative</text>
  <text x="320" y="226" fill="#aaa" font-size="9">Fill (NF)</text>
  <text x="320" y="240" fill="#888" font-size="8">검정 폼보드</text>

  <rect x="80" y="260" width="40" height="40" rx="4" fill="#1a2a1a" stroke="#66bb6a"/>
  <text x="100" y="278" text-anchor="middle" fill="#66bb6a" font-size="9" font-weight="bold">포르자</text>
  <text x="100" y="288" text-anchor="middle" fill="#66bb6a" font-size="9" font-weight="bold">500</text>
  <text x="100" y="316" text-anchor="middle" fill="#888" font-size="8">Background</text>

  <rect x="170" y="320" width="28" height="22" rx="3" fill="#3c2a4a" stroke="#a880ff"/>
  <text x="184" y="334" text-anchor="middle" fill="#a880ff" font-size="8" font-weight="bold">A</text>
  <text x="184" y="354" text-anchor="middle" fill="#aaa" font-size="7">35mm</text>

  <rect x="210" y="320" width="28" height="22" rx="3" fill="#3c2a4a" stroke="#a880ff"/>
  <text x="224" y="334" text-anchor="middle" fill="#a880ff" font-size="8" font-weight="bold">B</text>
  <text x="224" y="354" text-anchor="middle" fill="#aaa" font-size="7">85mm</text>
</svg>
```

  </div>

  <div class="hint danger">⚠️ Fill 라이트 의도적 미사용 — Negative Fill로 우측 그림자 형성이 EO 톤 핵심</div>

  <div class="card">
    <h2>📐 조명별 상세</h2>
    <h3>🟡 Key 라이트 (NANLITE 300B II)</h3>
    <table class="spec">
      <tr><td>위치</td><td>인터뷰이 좌측 45°</td></tr>
      <tr><td>거리</td><td>약 2m</td></tr>
      <tr><td>높이</td><td>머리보다 +15~20cm 위</td></tr>
      <tr><td>출력</td><td>35%</td></tr>
      <tr><td>색온도</td><td>4000K</td></tr>
      <tr><td>모디파이어</td><td>젬볼/랜턴 디퓨저</td></tr>
    </table>

```
<h3>🔵 Rim 라이트 (NANLITE 60B II)</h3>
<table class="spec">
  <tr><td>위치</td><td>후방 측면 45°</td></tr>
  <tr><td>거리</td><td>약 1.5m</td></tr>
  <tr><td>출력</td><td>25%</td></tr>
  <tr><td>색온도</td><td>4000K</td></tr>
  <tr><td>효과</td><td>머리카락·어깨 분리</td></tr>
</table>

<h3>🟢 Background (NANLITE 포르자 500)</h3>
<table class="spec">
  <tr><td>위치</td><td>배경 비추기 또는 보조 Key</td></tr>
  <tr><td>출력</td><td>현장에서 조정 (낮게 시작)</td></tr>
  <tr><td>색온도</td><td>4000K</td></tr>
  <tr><td>주의</td><td>인물에 직접 닿지 않게</td></tr>
</table>

<h3>⚫ Negative Fill</h3>
<table class="spec">
  <tr><td>위치</td><td>인터뷰이 우측 1m</td></tr>
  <tr><td>재료</td><td>검정 폼보드 또는 검정 천</td></tr>
  <tr><td>역할</td><td>우측 그림자 강화 (Fill 미사용 보조)</td></tr>
</table>
```

  </div>

  <div class="card">
    <h2>⚠️ 핵심 원칙</h2>
    <div class="hint">3등 모두 4000K 통일 — 한 등이라도 다르면 후반 매칭 +30분</div>
    <div class="hint">Key 라이트가 머리보다 약간 높아야 그림자가 뺨 아래쪽으로 자연스럽게 떨어짐</div>
    <div class="hint warn">팬 소음 주의 — Rode로 인터뷰이 위치에서 측정, &lt;-40dB 확인</div>
  </div>
</section>

<!-- ============= 📞 연락처 ============= -->

<section id="tab-contact">
  <div class="card">
    <h2>📞 연락처</h2>
    <p style="font-size:12px;">탭하면 바로 전화 / 길게 누르면 복사</p>
  </div>

  <div class="person">
    <div class="name">조창석 · 쿨샷카메라</div>
    <div class="role">D-1 픽업 / D-Day 반납 담당</div>
    <div class="actions">
      <a href="tel:010-9339-6339" class="btn-call"><span class="ico">📞</span><strong>전화</strong><small>010-9339-6339</small></a>
      <a href="sms:010-9339-6339"><span class="ico">💬</span><strong>문자</strong><small>SMS</small></a>
    </div>
  </div>

  <div class="person">
    <div class="name">선혜민 · PD</div>
    <div class="role">인터뷰어 / 현장 연락</div>
    <div class="actions">
      <a href="tel:010-5136-5246" class="btn-call"><span class="ico">📞</span><strong>전화</strong><small>010-5136-5246</small></a>
      <a href="sms:010-5136-5246"><span class="ico">💬</span><strong>문자</strong><small>SMS</small></a>
    </div>
  </div>

  <div class="person">
    <div class="name">쿨샷카메라 (대표번호)</div>
    <div class="role">매장 일반 문의</div>
    <div class="actions">
      <a href="tel:053-257-1012" class="btn-call"><span class="ico">📞</span><strong>전화</strong><small>053-257-1012</small></a>
    </div>
  </div>

  <div class="card">
    <h2>💰 결제 정보</h2>
    <table class="spec">
      <tr><td>쿨샷 입금계좌</td><td><span class="h">하나 103-910023-02905<br>조창석 (쿨샷)</span></td></tr>
      <tr><td>하루에, 헤메 결제</td><td>안희영 카카오뱅크<br><span class="h">3333-17-4235702 (130,000원)</span></td></tr>
    </table>
  </div>

  <div class="card">
    <h2>🏨 숙소 예약</h2>
    <table class="spec">
      <tr><td>이름</td><td>동성로 스위트 호텔</td></tr>
      <tr><td>예약 업체</td><td>여기어때</td></tr>
      <tr><td>예약번호 ①</td><td><span class="h">260428100112BFYE1</span></td></tr>
      <tr><td>예약번호 ②</td><td><span class="h">26042810011A9BYE1</span></td></tr>
      <tr><td>체크인</td><td>04.28(화) 16:00 가능</td></tr>
      <tr><td>체크아웃</td><td>04.29(수) 12:00</td></tr>
    </table>
  </div>
</section>

<!-- ============= 📍 장소 ============= -->

<section id="tab-place">
  <div class="card">
    <h2>📍 주요 장소</h2>
    <p style="font-size:12px;">탭하면 지도 앱으로 이동</p>
  </div>

  <div class="place">
    <div class="name">🏨 동성로 스위트 호텔 (숙소)</div>
    <div class="addr">대구 중구 향촌동 34-1</div>
    <div class="meta">D-1 체크인 · D-Day 09:30 출발</div>
    <div class="actions">
      <a href="https://map.naver.com/p/search/대구%20중구%20향촌동%2034-1" target="_blank"><span class="ico">🗺️</span><strong>네이버 지도</strong><small>길찾기</small></a>
      <a href="https://www.yeogi.com/domestic-accommodations/69489" target="_blank"><span class="ico">🌐</span><strong>여기어때</strong><small>예약 확인</small></a>
    </div>
  </div>

  <div class="place">
    <div class="name">📦 쿨샷카메라</div>
    <div class="addr">대구 중구 문화동 9-14</div>
    <div class="meta">D-1 19:30~20:00 픽업 · D-Day 17:00~19:00 반납<br>숙소에서 도보 약 6분</div>
    <div class="actions">
      <a href="https://map.naver.com/p/search/쿨샷카메라" target="_blank"><span class="ico">🗺️</span><strong>네이버 지도</strong><small>길찾기</small></a>
      <a href="tel:053-257-1012" class="btn-call"><span class="ico">📞</span><strong>전화</strong><small>053-257-1012</small></a>
    </div>
  </div>

  <div class="place">
    <div class="name">💄 하루에, 헤메샵</div>
    <div class="addr">대구 남구 안지랑로 17길 17, 1층</div>
    <div class="meta">D-Day 11:00~12:30 (1시간 30분, 130,000원)</div>
    <div class="actions">
      <a href="http://naver.me/xP8AHX3g" target="_blank"><span class="ico">🗺️</span><strong>네이버 지도</strong><small>길찾기</small></a>
    </div>
  </div>

  <div class="place">
    <div class="name">🎬 릴리프 스튜디오 ★</div>
    <div class="addr">대구 달서구 야외음악당로 50, 4층</div>
    <div class="meta">D-Day 10:00 영상팀 입장 · 13:00~16:00 촬영<br>숙소에서 자차 25~30분</div>
    <div class="actions">
      <a href="http://naver.me/F3TG1xNF" target="_blank"><span class="ico">🗺️</span><strong>네이버 지도</strong><small>길찾기</small></a>
    </div>
  </div>

  <div class="place">
    <div class="name">🏠 광주 출발지</div>
    <div class="addr">광주광역시 북구 군왕로 51번길 118</div>
    <div class="meta">D-1 16:00 출발 · D-Day ~23:00 도착</div>
    <div class="actions">
      <a href="https://map.naver.com/p/search/광주%20북구%20군왕로%2051번길%20118" target="_blank"><span class="ico">🗺️</span><strong>네이버 지도</strong><small>길찾기</small></a>
    </div>
  </div>
</section>

<!-- ============= 🚨 비상 ============= -->

<section id="tab-trouble">
  <div class="card">
    <h2>🚨 트러블슈팅 빠른 참조</h2>
    <p style="font-size:12px;">현장에서 문제 발생 시 즉시 참조</p>
  </div>

  <div class="trouble">
    <div class="symptom">두 FX3 색감이 다르게 보임</div>
    <div class="fix">
      <strong>1.</strong> 두 카메라 모두 CineEI 모드인지 확인<br>
      <strong>2.</strong> Base Look 둘 다 S-Log3 / S-Gamut3.Cine<br>
      <strong>3.</strong> EI 800 통일<br>
      <strong>4.</strong> 모니터 LUT 1 (s709) 통일<br>
      <strong>5.</strong> 그레이카드로 동시 WB 재설정
    </div>
  </div>

  <div class="trouble">
    <div class="symptom">NANLITE 팬 소음이 마이크에 잡힘</div>
    <div class="fix">
      <strong>1.</strong> 조명 거리 +20cm 멀리<br>
      <strong>2.</strong> 출력 살짝 낮춤 (35% → 30%)<br>
      <strong>3.</strong> 후방 흡음재(쿠션·천) 임시 배치<br>
      <strong>4.</strong> Rode로 -40dB 이하 확인<br>
      <strong>5.</strong> 정 안 되면 무음 모드 (출력 50% 이하 시)
    </div>
  </div>

  <div class="trouble">
    <div class="symptom">자연광 빛샘 발생</div>
    <div class="fix">
      <strong>1.</strong> 블라인드 100% 닫혔는지 재확인<br>
      <strong>2.</strong> 창틀·문 틈 검정천 + 마스킹 테이프<br>
      <strong>3.</strong> 그래도 새면 카메라 위치 변경 (빛 반대편)<br>
      <strong>4.</strong> 최후 수단: 시간대 늦춤 (자연광 약해질 때)
    </div>
  </div>

  <div class="trouble">
    <div class="symptom">검정 폼보드 미확보</div>
    <div class="fix">
      <strong>1.</strong> 검정 옷 (재킷·코트) 임시 활용<br>
      <strong>2.</strong> 검정천 (스튜디오 보유분 요청)<br>
      <strong>3.</strong> NANLITE 60B II 위치를 더 측면으로 → 그림자 강화<br>
      <strong>4.</strong> 차량 내 검정 시트 임시 활용
    </div>
  </div>

  <div class="trouble">
    <div class="symptom">Rode 페어링 안 됨</div>
    <div class="fix">
      <strong>1.</strong> RX·TX 모두 전원 OFF → 5초 대기 → ON<br>
      <strong>2.</strong> RX 페어링 모드 진입 (메뉴 → Pair)<br>
      <strong>3.</strong> TX 전원 길게 눌러 페어링 시도<br>
      <strong>4.</strong> 그래도 안 되면 RX 공장 초기화<br>
      <strong>5.</strong> 백업: A7IV 내장 마이크로 임시 녹음
    </div>
  </div>

  <div class="trouble">
    <div class="symptom">SD 카드 용량 부족 / 오류</div>
    <div class="fix">
      <strong>1.</strong> 다른 카드로 즉시 교체<br>
      <strong>2.</strong> 이전 카드를 SSD에 즉시 백업 (인터뷰 중에는 어시 진행)<br>
      <strong>3.</strong> 백업 완료 후에만 카드 포맷 (절대 미백업 카드 포맷 금지)<br>
      <strong>4.</strong> CAM A 우선 → CAM B는 임시 일시정지 가능
    </div>
  </div>

  <div class="trouble">
    <div class="symptom">인터뷰이가 긴장하거나 톤이 안 나옴</div>
    <div class="fix">
      <strong>1.</strong> 5분 휴식 + 물 제공<br>
      <strong>2.</strong> 가벼운 잡담으로 분위기 전환<br>
      <strong>3.</strong> 첫 번째 답변은 워밍업으로 활용 (편집에서 자르기)<br>
      <strong>4.</strong> 카메라 의식 줄이려 PD가 카메라 옆에서 자연스럽게 대화<br>
      <strong>5.</strong> 어려운 질문은 뒤로 미루기
    </div>
  </div>

  <div class="trouble">
    <div class="symptom">시간 지연 (인터뷰가 14:45 넘김)</div>
    <div class="fix">
      <strong>1.</strong> 14:45 시점에 진행 상황 PD와 즉석 협의<br>
      <strong>2.</strong> C블록 우선순위 핵심 질문만 압축<br>
      <strong>3.</strong> 인물 사진 시간 단축 (60분 → 45분, 공간 2개로)<br>
      <strong>4.</strong> 백업·철수 시간은 절대 단축 금지 (1차 백업 필수)<br>
      <strong>5.</strong> 쿨샷 반납 시간 여유 있음 (~19:00 도착 = 마감 1시간 전)
    </div>
  </div>

  <div class="card">
    <h2>📋 비상 절차</h2>
    <div class="hint danger"><strong>장비 파손 발견:</strong> 즉시 사진 촬영 + 쿨샷 조창석(010-9339-6339) 통화 + 상황 설명</div>
    <div class="hint warn"><strong>인터뷰이 컨디션 문제:</strong> 즉시 PD 판단으로 휴식 + 필요 시 일정 조정</div>
    <div class="hint"><strong>차량 문제:</strong> 한국타이어 긴급출동 또는 보험사 연락 + 일정 지연 시 모든 관계자 즉시 통보</div>
  </div>
</section>

</main>

<nav class="tabs">
  <button class="active" data-tab="now"><span class="ico">🚀</span>지금</button>
  <button data-tab="d1"><span class="ico">📋</span>D-1</button>
  <button data-tab="dday"><span class="ico">🎬</span>D-Day</button>
  <button data-tab="camera"><span class="ico">🎥</span>카메라</button>
  <button data-tab="light"><span class="ico">💡</span>조명</button>
  <button data-tab="contact"><span class="ico">📞</span>연락</button>
  <button data-tab="place"><span class="ico">📍</span>장소</button>
  <button data-tab="trouble"><span class="ico">🚨</span>비상</button>
</nav>

<script>
// ===== 시계 + 카운트다운 =====
const DDAY = new Date(2026, 3, 29, 13, 0, 0); // 04.29 13:00 (인터뷰 시작)
function pad(n){return String(n).padStart(2,'0');}
function tick(){
  const now = new Date();
  document.getElementById('clock').textContent =
    `${pad(now.getHours())}:${pad(now.getMinutes())}:${pad(now.getSeconds())}`;
  const diff = DDAY - now;
  const cd = document.getElementById('countdown');
  if(diff > 0){
    const days = Math.floor(diff / 86400000);
    const hours = Math.floor((diff % 86400000) / 3600000);
    const mins = Math.floor((diff % 3600000) / 60000);
    cd.textContent = `인터뷰 시작까지 ${days}일 ${pad(hours)}:${pad(mins)}`;
  } else {
    cd.textContent = '🎬 D-Day 진행 중';
  }
  updateNow();
}

// ===== 탭 전환 =====
function switchTab(name){
  document.querySelectorAll('section').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('nav.tabs button').forEach(b => b.classList.remove('active'));
  document.getElementById('tab-' + name).classList.add('active');
  document.querySelector(`nav.tabs button[data-tab="${name}"]`)?.classList.add('active');
  window.scrollTo({top: 0, behavior: 'smooth'});
  localStorage.setItem('app-last-tab', name);
}
document.querySelectorAll('nav.tabs button[data-tab]').forEach(btn => {
  btn.addEventListener('click', () => switchTab(btn.dataset.tab));
});

// ===== 체크박스 상태 저장/복원 =====
const STORAGE_PREFIX = 'kim-dday-';
function saveCheck(key, checked){
  localStorage.setItem(STORAGE_PREFIX + key, checked ? '1' : '0');
}
function loadCheck(key){
  return localStorage.getItem(STORAGE_PREFIX + key) === '1';
}
function initCheckboxes(){
  document.querySelectorAll('input[type=checkbox][data-key]').forEach(cb => {
    cb.checked = loadCheck(cb.dataset.key);
    cb.addEventListener('change', () => {
      saveCheck(cb.dataset.key, cb.checked);
      updateNow();
    });
  });
}

// ===== 진행률 + Now 다음 작업 계산 =====
const SCHEDULE = [
  // [section, group, label, hour, minute, dataKeys]
  ['d1','D-1 오전 통화', '대외협력팀 메시지', 9, 0, ['d1-09-1','d1-09-2','d1-09-3']],
  ['d1','D-1 오전 통화', '미디어센터 취소', 9, 30, ['d1-0930-1','d1-0930-2']],
  ['d1','D-1 오전 통화', '쿨샷 (35mm GM + 포르자 500 추가)', 10, 0, ['d1-10-1','d1-10-2','d1-10-3','d1-10-4','d1-10-5']],
  ['d1','D-1 오전 통화', '릴리프 스튜디오 확인', 10, 30, ['d1-1030-1','d1-1030-2','d1-1030-3','d1-1030-4']],
  ['d1','D-1 오전 통화', '하루에, 헤메 확인', 11, 0, ['d1-11-1','d1-11-2','d1-11-3']],
  ['d1','D-1 점검', '보유 장비 + 출장 준비물', 12, 0, ['d1-12-1','d1-12-2','d1-12-3','d1-12-4','d1-12-5','d1-12-6','d1-12-7','d1-12-8','d1-12-9','d1-12-10']],
  ['d1','D-1 출장', '광주 출발 + 차량 적재', 15, 30, ['d1-1530-1','d1-1530-2','d1-1530-3']],
  ['d1','D-1 출장', '대구 이동', 16, 0, ['d1-16-1','d1-16-2']],
  ['d1','D-1 픽업', '★ 쿨샷 픽업 (20:00 마감)', 19, 30, ['d1-19-1','d1-19-2','d1-19-3','d1-19-4','d1-19-5','d1-19-6','d1-19-7']],
  ['d1','D-1 픽업', '숙소 체크인', 20, 0, ['d1-20-1','d1-20-2','d1-20-3']],
  ['d1','D-1 저녁', '저녁 식사', 20, 30, ['d1-2030-1']],
  ['d1','D-1 테스트', '★ 테스트 촬영 (D-Day 리허설)', 21, 30, ['d1-21-1','d1-21-2','d1-21-3','d1-21-4','d1-21-5','d1-21-6','d1-21-7']],
  ['d1','D-1 취침', '취침 준비', 23, 0, ['d1-23-1','d1-23-2','d1-23-3']],

  // D-Day (다음날 04.29)
  ['dday','D-Day 아침', '아침 + 차량 적재', 7+24, 30, ['dd-07-1','dd-07-2','dd-07-3','dd-07-4','dd-07-5','dd-07-6','dd-07-7']],
  ['dday','D-Day 이동', '스튜디오 이동', 9+24, 30, ['dd-0930-1','dd-0930-2']],
  ['dday','D-Day 페이즈', '페이즈 1 — 입장 + 차폐', 10+24, 0, ['dd-p1-1','dd-p1-2','dd-p1-3','dd-p1-4','dd-p1-5','dd-p1-6']],
  ['dday','D-Day 페이즈', '페이즈 2 — 조명 (4등 체제)', 10+24, 25, ['dd-p2-1','dd-p2-2','dd-p2-3','dd-p2-4','dd-p2-5','dd-p2-6','dd-p2-7','dd-p2-8']],
  ['dday','D-Day 페이즈', '★ 페이즈 3 — 카메라 (가장 중요)', 10+24, 55, ['dd-p3-1','dd-p3-2','dd-p3-3','dd-p3-4','dd-p3-5','dd-p3-6','dd-p3-7','dd-p3-8','dd-p3-9','dd-p3-10','dd-p3-11']],
  ['dday','D-Day 페이즈', '페이즈 4 — 음향', 11+24, 35, ['dd-p4-1','dd-p4-2','dd-p4-3','dd-p4-4','dd-p4-5']],
  ['dday','D-Day 페이즈', '페이즈 5 — 통합 테스트', 11+24, 55, ['dd-p5-1','dd-p5-2','dd-p5-3','dd-p5-4','dd-p5-5','dd-p5-6']],
  ['dday','D-Day 페이즈', '페이즈 6 — 인터뷰이 도착 대기', 12+24, 30, ['dd-p6-1','dd-p6-2','dd-p6-3']],
  ['dday','D-Day 인터뷰', '★ 인터뷰 영상 촬영', 13+24, 0, ['dd-int-1','dd-int-2','dd-int-3','dd-int-4','dd-int-5','dd-int-6','dd-int-7','dd-int-8']],
  ['dday','D-Day 사진', '인물 프로필 사진', 14+24, 45, ['dd-pic-1','dd-pic-2','dd-pic-3','dd-pic-4','dd-pic-5']],
  ['dday','D-Day 백업', '★ 백업 + 철수', 16+24, 0, ['dd-bk-1','dd-bk-2','dd-bk-3','dd-bk-4','dd-bk-5','dd-bk-6','dd-bk-7']],
  ['dday','D-Day 반납', '쿨샷 반납', 17+24, 0, ['dd-rt-1','dd-rt-2','dd-rt-3','dd-rt-4']],
  ['dday','D-Day 저녁', '저녁', 19+24, 0, ['dd-d-1','dd-d-2']],
  ['dday','D-Day 복귀', '광주 복귀', 20+24, 0, ['dd-rt2-1','dd-rt2-2','dd-rt2-3','dd-rt2-4','dd-rt2-5']],
];

const APP_START = new Date(2026, 3, 28, 0, 0, 0); // 04.28 00:00 기준
function getScheduleTime(s){
  const d = new Date(APP_START);
  d.setHours(s[3], s[4], 0);
  return d;
}
function progressOf(keys){
  const total = keys.length;
  const done = keys.filter(k => loadCheck(k)).length;
  return { total, done, pct: total ? Math.round(done / total * 100) : 0 };
}

function updateNow(){
  const now = new Date();
  // 다음 작업 = 현재 시각 이후 첫 번째 미완료 그룹
  let next = null;
  for(const item of SCHEDULE){
    const t = getScheduleTime(item);
    const p = progressOf(item[5]);
    if(p.pct < 100){
      // 시작 시각이 현재 시각 + 30분 이내면 "지금" 작업
      if(t > now){ next = { item, t, p, status: 'upcoming' }; break; }
      else if(t <= now){ next = { item, t, p, status: 'now' }; }
    }
  }
  const taskEl = document.getElementById('next-task');
  const timeEl = document.getElementById('next-time');
  if(!next){
    taskEl.textContent = '🎉 모든 작업 완료';
    timeEl.textContent = '';
  } else {
    const { item, t, p, status } = next;
    taskEl.textContent = item[2];
    const hh = pad(t.getHours()), mm = pad(t.getMinutes());
    const stat = status === 'now' ? '⚡ 진행 중' : '⏰ 예정';
    timeEl.textContent = `${stat} · ${hh}:${mm} · ${p.done}/${p.total} 완료 (${p.pct}%)`;
  }

  // 진행률 그룹 (6개 큰 그룹으로 묶음)
  const groups = [
    ['D-1 오전 통화', SCHEDULE.filter(s => s[1]==='D-1 오전 통화').flatMap(s => s[5])],
    ['D-1 점검·준비', SCHEDULE.filter(s => s[1].startsWith('D-1 점검') || s[1].startsWith('D-1 출장')).flatMap(s => s[5])],
    ['D-1 픽업·테스트', SCHEDULE.filter(s => ['D-1 픽업','D-1 저녁','D-1 테스트','D-1 취침'].includes(s[1])).flatMap(s => s[5])],
    ['D-Day 세팅 (페이즈 1~6)', SCHEDULE.filter(s => s[1]==='D-Day 페이즈' || s[1]==='D-Day 아침' || s[1]==='D-Day 이동').flatMap(s => s[5])],
    ['D-Day 촬영', SCHEDULE.filter(s => ['D-Day 인터뷰','D-Day 사진'].includes(s[1])).flatMap(s => s[5])],
    ['D-Day 백업·복귀', SCHEDULE.filter(s => ['D-Day 백업','D-Day 반납','D-Day 저녁','D-Day 복귀'].includes(s[1])).flatMap(s => s[5])],
  ];
  const stack = document.getElementById('progress-stack');
  stack.innerHTML = '';
  groups.forEach(([name, keys]) => {
    const p = progressOf(keys);
    const row = document.createElement('div');
    row.innerHTML = `
      <div class="progress-row">
        <span class="name">${name}</span>
        <span class="pct">${p.done}/${p.total} (${p.pct}%)</span>
      </div>
      <div class="progress-bar"><div class="fill" style="width:${p.pct}%"></div></div>
    `;
    stack.appendChild(row);
  });
}

// ===== 섹션별 초기화 =====
function resetSection(prefix){
  if(!confirm(`${prefix === 'd1' ? 'D-1' : 'D-Day'} 체크리스트를 모두 초기화할까요?`)) return;
  document.querySelectorAll(`input[type=checkbox][data-key^="${prefix}-"]`).forEach(cb => {
    cb.checked = false;
    saveCheck(cb.dataset.key, false);
  });
  updateNow();
}

// ===== Service Worker 등록 (PWA 오프라인 동작) =====
if ('serviceWorker' in navigator) {
  window.addEventListener('load', () => {
    navigator.serviceWorker.register('./sw.js')
      .then(reg => console.log('SW registered:', reg.scope))
      .catch(err => console.warn('SW registration failed:', err));
  });
}

// ===== 시작 =====
window.addEventListener('DOMContentLoaded', () => {
  initCheckboxes();
  tick();
  setInterval(tick, 1000);

  // 마지막 탭 복원
  const lastTab = localStorage.getItem('app-last-tab');
  if(lastTab && document.getElementById('tab-' + lastTab)){
    switchTab(lastTab);
  }

  // 페이지 가시성 변경 시 새로고침 (화면 켤 때)
  document.addEventListener('visibilitychange', () => {
    if(!document.hidden) updateNow();
  });
});
</script>

</body>
</html>
