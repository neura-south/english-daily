#index.html
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>English Daily</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{--bg:#0f1117;--surface:#1a1d27;--surface2:#222636;--border:#2e3347;--gold:#c9a96e;--gold2:#e8c98a;--text:#e8e6e0;--muted:#8a8fa8;--green:#4ecb8d;--red:#e06b6b;--blue:#6b9fe0}
body{background:var(--bg);color:var(--text);font-family:'DM Sans',sans-serif;min-height:100vh}
.app{max-width:480px;margin:0 auto;min-height:100vh;display:flex;flex-direction:column;padding-bottom:32px}
.header{padding:24px 20px 0;display:flex;justify-content:space-between;align-items:center}
.logo{font-family:'Cormorant Garamond',serif;font-size:22px;font-weight:600;color:var(--gold)}
.logo span{color:var(--text);opacity:.5}
.date-badge{font-size:12px;color:var(--muted);background:var(--surface);padding:4px 10px;border-radius:20px;border:1px solid var(--border)}
.home-hero{padding:28px 20px 16px}
.hero-title{font-family:'Cormorant Garamond',serif;font-size:32px;font-weight:400;line-height:1.2;margin-bottom:6px}
.hero-title em{color:var(--gold);font-style:italic}
.hero-sub{color:var(--muted);font-size:13px;font-weight:300}
.progress-bar{margin:0 20px;height:3px;background:var(--surface2);border-radius:2px;overflow:hidden}
.progress-fill{height:100%;background:linear-gradient(90deg,var(--gold),var(--gold2));border-radius:2px;transition:width .4s ease}
.progress-label{padding:6px 20px 0;font-size:11px;color:var(--muted);font-weight:300}
.section-label{padding:20px 20px 8px;font-size:10px;letter-spacing:2px;color:var(--muted);text-transform:uppercase;font-weight:500}
.phrase-card{margin:0 16px 10px;background:var(--surface);border:1px solid var(--border);border-radius:16px;padding:18px;cursor:pointer;transition:all .2s;position:relative;overflow:hidden}
.phrase-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,var(--gold),transparent)}
.phrase-card:hover{border-color:var(--gold);transform:translateY(-1px)}
.phrase-card.done::before{background:linear-gradient(90deg,var(--green),transparent)}
.phrase-card.done{opacity:.6}
.phrase-main{font-family:'Cormorant Garamond',serif;font-size:21px;margin-bottom:4px}
.phrase-meaning{font-size:12px;color:var(--muted);margin-bottom:10px}
.phrase-meta{display:flex;gap:6px;align-items:center}
.tag{font-size:10px;background:var(--surface2);color:var(--gold);padding:3px 8px;border-radius:10px;border:1px solid var(--border)}
.done-badge{font-size:10px;color:var(--green);margin-left:auto}
.review-btn-wrap{padding:0 16px 10px}
.review-btn{width:100%;background:var(--surface);border:1px solid var(--border);border-radius:14px;padding:16px 18px;cursor:pointer;display:flex;justify-content:space-between;align-items:center;transition:all .2s;color:var(--text)}
.review-btn:hover{border-color:var(--blue)}
.review-btn-label{font-size:14px;font-weight:500;text-align:left}
.review-count{background:var(--blue);color:#fff;font-size:11px;font-weight:600;padding:3px 8px;border-radius:10px;white-space:nowrap}
.stats-box{margin:0 16px;background:var(--surface);border:1px solid var(--border);border-radius:12px;padding:14px 16px;display:flex;justify-content:space-between}
.stat-label{font-size:10px;color:var(--muted);letter-spacing:1.5px;text-transform:uppercase;margin-bottom:6px}
.stat-val{font-size:20px;font-family:'Cormorant Garamond',serif}

/* Practice */
.screen{display:none;flex:1;flex-direction:column;padding:0 20px 20px}
.screen.active{display:flex}
.back-btn{background:none;border:none;color:var(--muted);font-size:13px;cursor:pointer;padding:12px 0;display:flex;align-items:center;gap:6px;font-family:'DM Sans',sans-serif}
.back-btn:hover{color:var(--text)}
.pbar{display:flex;gap:4px;margin-bottom:20px}
.pstep{flex:1;height:3px;background:var(--surface2);border-radius:2px}
.pstep.active{background:var(--gold)}
.pstep.done{background:var(--green)}
.phrase-header{font-family:'Cormorant Garamond',serif;font-size:26px;margin-bottom:4px}
.phrase-header-sub{font-size:12px;color:var(--muted);margin-bottom:20px}
.example-card{background:var(--surface);border:1px solid var(--border);border-radius:14px;padding:20px;margin-bottom:14px}
.example-num{font-size:10px;color:var(--muted);letter-spacing:1px;text-transform:uppercase;margin-bottom:8px}
.example-en{font-family:'Cormorant Garamond',serif;font-size:22px;line-height:1.35;margin-bottom:8px}
.example-kr{font-size:13px;color:var(--muted);line-height:1.5}
.step-label{font-size:11px;letter-spacing:1.5px;text-transform:uppercase;color:var(--gold);margin-bottom:10px;font-weight:500}
textarea{width:100%;background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:14px;color:var(--text);font-family:'DM Sans',sans-serif;font-size:15px;outline:none;transition:border-color .2s;resize:none;line-height:1.5}
textarea:focus{border-color:var(--gold)}
textarea.correct{border-color:var(--green);background:rgba(78,203,141,.05)}
textarea.wrong{border-color:var(--red);background:rgba(224,107,107,.05)}
.btn{border:none;cursor:pointer;font-family:'DM Sans',sans-serif;font-weight:500;border-radius:10px;transition:all .15s}
.btn-primary{background:var(--gold);color:#1a1407;padding:13px 20px;font-size:14px;width:100%;margin-top:8px}
.btn-primary:hover{background:var(--gold2)}
.btn-primary:disabled{opacity:.4;cursor:default}
.btn-secondary{background:var(--surface);border:1px solid var(--border);color:var(--text);padding:12px 20px;font-size:13px;width:100%;margin-top:8px}
.btn-speak{background:var(--surface);border:2px solid var(--border);color:var(--text);padding:14px 20px;font-size:13px;width:100%;margin-bottom:10px;display:flex;align-items:center;justify-content:center;gap:8px;border-radius:10px;cursor:pointer;font-family:'DM Sans',sans-serif;transition:all .2s}
.btn-speak.listening{border-color:var(--red);color:var(--red);animation:pulse 1s infinite}
.btn-speak:hover:not(.listening){border-color:var(--blue);color:var(--blue)}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.6}}
.result-box{background:var(--surface);border-radius:12px;padding:16px;margin-bottom:12px;border:1px solid var(--border)}
.result-score{font-size:24px;font-weight:600}
.result-score.good{color:var(--green)}
.result-score.bad{color:var(--red)}
.result-detail{font-size:12px;color:var(--muted);margin-top:4px}
.result-answer{font-family:'Cormorant Garamond',serif;font-size:18px;margin-top:10px;padding-top:10px;border-top:1px solid var(--border)}
.complete-wrap{flex:1;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:40px 20px;text-align:center}
.complete-icon{font-size:56px;margin-bottom:16px}
.complete-title{font-family:'Cormorant Garamond',serif;font-size:32px;margin-bottom:8px}
.complete-sub{color:var(--muted);font-size:14px;margin-bottom:32px;line-height:1.6}
.info-box{background:var(--surface);border-radius:14px;padding:20px;width:100%;margin-bottom:20px;border:1px solid var(--border);text-align:left}
.review-question{background:var(--surface);border-radius:14px;padding:24px;margin-bottom:16px;border:1px solid var(--border)}
.review-kr{font-size:18px;line-height:1.6;text-align:center}
.review-hint{font-size:12px;color:var(--muted);text-align:center;margin-top:8px}
.btn-row{display:flex;gap:8px;margin-top:8px}
.btn-pass{flex:1;background:rgba(78,203,141,.15);border:1px solid var(--green);color:var(--green);padding:12px;border-radius:10px;font-family:'DM Sans',sans-serif;font-size:13px;cursor:pointer}
.btn-fail{flex:1;background:rgba(224,107,107,.1);border:1px solid var(--red);color:var(--red);padding:12px;border-radius:10px;font-family:'DM Sans',sans-serif;font-size:13px;cursor:pointer}
.pip{display:inline-block;width:7px;height:7px;border-radius:50%;background:var(--surface2);margin-right:2px}
.pip.on{background:var(--gold)}
.method-btns{display:flex;gap:8px;margin-bottom:10px}
.method-btn{flex:1;background:var(--surface);border:1px solid var(--border);color:var(--text);padding:14px;border-radius:10px;cursor:pointer;font-family:'DM Sans',sans-serif;font-size:13px;transition:all .15s}
.method-btn:hover,.method-btn.sel{border-color:var(--gold);color:var(--gold)}
.transcript{font-size:13px;color:var(--muted);margin-bottom:8px;padding:10px;background:var(--surface);border-radius:8px;min-height:40px}
</style>
</head>
<body>
<div class="app" id="app">
  <!-- HOME -->
  <div id="screen-home">
    <div class="header">
      <div class="logo">English <span>/</span> Daily</div>
      <div class="date-badge" id="date-badge"></div>
    </div>
    <div class="home-hero">
      <div class="hero-title">오늘의<br><em>3가지 구문</em></div>
      <div class="hero-sub">각 구문마다 5개의 예문을 학습해요</div>
    </div>
    <div class="progress-bar"><div class="progress-fill" id="progress-fill" style="width:0%"></div></div>
    <div class="progress-label" id="progress-label">0 / 3 완료</div>
    <div class="section-label">오늘의 학습</div>
    <div id="phrase-cards"></div>
    <div class="section-label">복습</div>
    <div class="review-btn-wrap">
      <button class="review-btn" id="review-btn" onclick="startReview()">
        <div>
          <div class="review-btn-label">복습 카드</div>
          <div style="font-size:11px;color:var(--muted);margin-top:2px" id="review-sub">불러오는 중...</div>
        </div>
        <div id="review-count-badge"></div>
      </button>
    </div>
    <div class="stats-box">
      <div><div class="stat-label">학습 중</div><div class="stat-val" id="stat-learning">0</div></div>
      <div style="text-align:right"><div class="stat-label">마스터</div><div class="stat-val" style="color:var(--gold)" id="stat-master">0</div></div>
    </div>
  </div>

  <!-- PRACTICE -->
  <div id="screen-practice" class="screen" style="display:none">
    <button class="back-btn" onclick="goHome()">← 홈으로</button>
    <div class="pbar" id="pbar"></div>
    <div class="phrase-header" id="phr-title"></div>
    <div class="phrase-header-sub" id="phr-sub"></div>
    <div class="example-card" id="example-card">
      <div class="example-num" id="ex-num"></div>
      <div class="example-en" id="ex-en"></div>
      <div class="example-kr" id="ex-kr"></div>
    </div>
    <div id="practice-body"></div>
  </div>

  <!-- COMPLETE -->
  <div id="screen-complete" style="display:none">
    <div class="complete-wrap">
      <div class="complete-icon">✨</div>
      <div class="complete-title">구문 완료!</div>
      <div class="complete-sub" id="complete-sub"></div>
      <div class="info-box">
        <div style="font-size:12px;color:var(--muted);margin-bottom:8px">다음 복습 일정</div>
        <div style="font-family:'Cormorant Garamond',serif;font-size:20px" id="next-review-label"></div>
      </div>
      <button class="btn btn-primary" onclick="goHome()">홈으로 돌아가기</button>
    </div>
  </div>

  <!-- REVIEW -->
  <div id="screen-review" style="display:none;flex-direction:column;padding:0 20px 20px">
    <button class="back-btn" onclick="goHome()">← 홈으로</button>
    <div style="font-family:'Cormorant Garamond',serif;font-size:24px;margin-bottom:4px">복습</div>
    <div style="font-size:12px;color:var(--muted);margin-bottom:20px" id="review-progress-label"></div>
    <div class="pbar" id="rpbar"></div>
    <div class="review-question">
      <div class="review-kr" id="review-kr"></div>
      <div class="review-hint" id="review-hint"></div>
    </div>
    <div id="review-body"></div>
  </div>

  <!-- REVIEW DONE -->
  <div id="screen-reviewdone" style="display:none">
    <div class="complete-wrap">
      <div class="complete-icon">🎯</div>
      <div class="complete-title">복습 완료!</div>
      <div class="complete-sub" id="reviewdone-sub"></div>
      <button class="btn btn-primary" onclick="goHome()">홈으로 돌아가기</button>
    </div>
  </div>
</div>

<script>
// ── Phrase Database ────────────────────────────────────────────────────────────
const DB = [
  {id:1,phrase:"Can I help you?",cat:"일상/여행",meaning:"도움이 필요하세요? / 뭐 찾으세요?",ex:[
    {en:"Can I help you find something?",kr:"뭔가 찾는 것 도와드릴까요?"},
    {en:"Could I help you carry those bags?",kr:"가방 들어드릴까요?"},
    {en:"I was wondering if I could help you.",kr:"혹시 도움이 필요하신지 해서요."},
    {en:"I will help you whenever you need me.",kr:"필요하실 때 언제든지 도와드릴게요."},
    {en:"I have been helping him every day this week.",kr:"이번 주 매일 그를 도와주고 있어요."}
  ]},
  {id:2,phrase:"Do you mind if...?",cat:"일상/여행",meaning:"~해도 괜찮을까요?",ex:[
    {en:"Do you mind if I sit here?",kr:"여기 앉아도 될까요?"},
    {en:"Would you mind if I opened the window?",kr:"창문 열어도 될까요?"},
    {en:"Did you mind when I borrowed your charger?",kr:"충전기 빌렸을 때 불편하셨나요?"},
    {en:"She won't mind if you use her umbrella.",kr:"그녀의 우산을 써도 신경 안 쓸 거예요."},
    {en:"He has never minded sharing his notes.",kr:"필기를 나눠주는 걸 한 번도 불편해한 적 없어요."}
  ]},
  {id:3,phrase:"I was wondering if...",cat:"일상/여행",meaning:"혹시 ~인지 여쭤봐도 될까요?",ex:[
    {en:"I was wondering if you could help me.",kr:"혹시 도와주실 수 있는지 여쭤봐도 될까요?"},
    {en:"I am wondering if the store is still open.",kr:"가게가 아직 열려 있는지 궁금해요."},
    {en:"I have been wondering if I should change jobs.",kr:"직장을 바꿔야 할지 계속 고민하고 있어요."},
    {en:"She was wondering if she might borrow the car.",kr:"차를 빌릴 수 있을지 물어볼까 했대요."},
    {en:"I will be wondering if everything went well.",kr:"모든 게 잘 됐는지 계속 궁금할 거예요."}
  ]},
  {id:4,phrase:"It depends on...",cat:"일상",meaning:"~에 따라 다르다",ex:[
    {en:"It depends on the weather.",kr:"날씨에 따라 달라요."},
    {en:"It might depend on how much time we have.",kr:"시간이 얼마나 있느냐에 달려 있을 수도 있어요."},
    {en:"Everything depended on her decision.",kr:"모든 것이 그녀의 결정에 달려 있었어요."},
    {en:"The price will depend on the quantity.",kr:"가격은 수량에 따라 달라질 거예요."},
    {en:"It has always depended on the situation.",kr:"항상 상황에 따라 달라져 왔어요."}
  ]},
  {id:5,phrase:"I can't afford to...",cat:"일상/여행",meaning:"~할 여유가 없다",ex:[
    {en:"I can't afford to miss this train.",kr:"이 기차를 놓칠 여유가 없어요."},
    {en:"I couldn't afford to buy a new phone then.",kr:"그때 새 핸드폰을 살 여유가 없었어요."},
    {en:"She won't be able to afford the rent.",kr:"그녀는 집세를 감당하지 못할 거예요."},
    {en:"We can't afford to make any more mistakes.",kr:"더 이상 실수할 여유가 없어요."},
    {en:"I have never been able to afford luxury hotels.",kr:"럭셔리 호텔을 감당한 적이 한 번도 없어요."}
  ]},
  {id:6,phrase:"Would you like to...?",cat:"일상/여행",meaning:"~하시겠어요? (정중한 제안)",ex:[
    {en:"Would you like to try this dish?",kr:"이 음식 드셔보시겠어요?"},
    {en:"Would you like me to call a taxi for you?",kr:"택시를 불러드릴까요?"},
    {en:"Did you want to join us for dinner?",kr:"저희와 저녁 드시고 싶었나요?"},
    {en:"She would have liked to stay longer.",kr:"그녀는 더 머물고 싶었을 거예요."},
    {en:"I will ask if he would like to come.",kr:"그가 오고 싶은지 물어볼게요."}
  ]},
  {id:7,phrase:"Could you tell me where...?",cat:"여행",meaning:"~가 어디인지 알 수 있을까요?",ex:[
    {en:"Could you tell me where the restroom is?",kr:"화장실이 어디 있는지 알 수 있을까요?"},
    {en:"Can you tell me where I should get off?",kr:"어디서 내려야 하는지 알려주실 수 있나요?"},
    {en:"She told me where the nearest hospital was.",kr:"가장 가까운 병원이 어디인지 알려줬어요."},
    {en:"Would you be able to tell me where to exchange money?",kr:"환전할 곳이 어딘지 알 수 있을까요?"},
    {en:"I have been trying to find out where the bus stops.",kr:"버스 정류장이 어딘지 계속 알아보고 있었어요."}
  ]},
  {id:8,phrase:"I'm used to...",cat:"일상",meaning:"~에 익숙하다",ex:[
    {en:"I'm used to waking up early.",kr:"저는 일찍 일어나는 것에 익숙해요."},
    {en:"I wasn't used to eating spicy food at first.",kr:"처음엔 매운 음식 먹는 게 익숙하지 않았어요."},
    {en:"She will get used to living alone.",kr:"그녀는 혼자 사는 것에 익숙해질 거예요."},
    {en:"He must be used to traveling by now.",kr:"이제쯤은 여행에 익숙해졌을 거예요."},
    {en:"I have gotten used to the long commute.",kr:"긴 통근 시간에 익숙해졌어요."}
  ]},
  {id:9,phrase:"Is it possible to...?",cat:"여행/일상",meaning:"~이 가능한가요?",ex:[
    {en:"Is it possible to check in early?",kr:"조기 체크인이 가능한가요?"},
    {en:"Would it be possible to get a refund?",kr:"환불이 가능할까요?"},
    {en:"Was it possible to change the reservation?",kr:"예약 변경이 가능했나요?"},
    {en:"It might be possible to extend your visa.",kr:"비자 연장이 가능할 수도 있어요."},
    {en:"It has never been possible to park here for free.",kr:"여기서 무료 주차가 된 적은 한 번도 없었어요."}
  ]},
  {id:10,phrase:"What do you recommend?",cat:"여행/일상",meaning:"무엇을 추천하시나요?",ex:[
    {en:"What do you recommend from the menu?",kr:"메뉴에서 무엇을 추천하시나요?"},
    {en:"What would you recommend for a beginner?",kr:"초보자에게는 무엇을 추천하시겠어요?"},
    {en:"What did you recommend to her last time?",kr:"지난번에 그녀에게 무엇을 추천했나요?"},
    {en:"What can you recommend near the station?",kr:"역 근처에서 뭘 추천해 주실 수 있나요?"},
    {en:"I have always recommended this place to everyone.",kr:"저는 항상 이곳을 모두에게 추천해 왔어요."}
  ]},
  {id:11,phrase:"I should have...",cat:"일상",meaning:"~했어야 했는데 (후회)",ex:[
    {en:"I should have booked the tickets earlier.",kr:"더 일찍 티켓을 예매했어야 했는데."},
    {en:"I shouldn't have eaten so much.",kr:"그렇게 많이 먹지 말았어야 했는데."},
    {en:"You should have told me sooner.",kr:"더 빨리 말해줬어야 했는데."},
    {en:"She should have brought a jacket.",kr:"그녀는 재킷을 가져왔어야 했어요."},
    {en:"We should have left earlier to avoid the traffic.",kr:"교통 체증을 피하려면 더 일찍 출발했어야 했는데."}
  ]},
  {id:12,phrase:"I'll take care of it.",cat:"일상",meaning:"제가 처리할게요.",ex:[
    {en:"I'll take care of the bill.",kr:"제가 계산할게요."},
    {en:"Don't worry, I will take care of everything.",kr:"걱정 마세요, 제가 다 처리할게요."},
    {en:"I took care of the problem while you were away.",kr:"당신이 없는 동안 제가 문제를 처리했어요."},
    {en:"Could you take care of the luggage?",kr:"짐 좀 맡아봐 주실 수 있어요?"},
    {en:"She has been taking care of the arrangements.",kr:"그녀가 준비를 도맡아 해왔어요."}
  ]},
  {id:13,phrase:"How long does it take?",cat:"여행",meaning:"얼마나 걸리나요?",ex:[
    {en:"How long does it take to get to the airport?",kr:"공항까지 얼마나 걸리나요?"},
    {en:"How long will it take to fix this?",kr:"이걸 고치는 데 얼마나 걸릴까요?"},
    {en:"How long did it take you to learn English?",kr:"영어 배우는 데 얼마나 걸렸나요?"},
    {en:"It shouldn't take more than an hour.",kr:"한 시간 이상 걸리지 않을 거예요."},
    {en:"It has been taking longer than expected.",kr:"예상보다 더 오래 걸리고 있어요."}
  ]},
  {id:14,phrase:"Let me know if...",cat:"일상",meaning:"~하면 알려주세요",ex:[
    {en:"Let me know if you need anything.",kr:"필요한 게 있으면 알려주세요."},
    {en:"Please let me know if you can make it.",kr:"오실 수 있으면 알려주세요."},
    {en:"She asked me to let her know if I changed my mind.",kr:"마음이 바뀌면 알려달라고 했어요."},
    {en:"You should let me know if there's a problem.",kr:"문제가 있으면 꼭 알려주세요."},
    {en:"I will let you know as soon as I hear anything.",kr:"소식이 들리면 바로 알려드릴게요."}
  ]},
  {id:15,phrase:"I'd rather...",cat:"일상",meaning:"~하는 편이 낫겠어요",ex:[
    {en:"I'd rather walk than take a taxi.",kr:"택시보다는 걷는 게 낫겠어요."},
    {en:"I would rather stay in than go out tonight.",kr:"오늘 밤은 집에 있는 게 낫겠어요."},
    {en:"She would rather have taken the earlier flight.",kr:"그녀는 더 이른 비행기를 탔으면 했을 거예요."},
    {en:"I would rather not talk about it right now.",kr:"지금 당장은 그 얘기를 않는 게 낫겠어요."},
    {en:"I have always preferred eating at home.",kr:"저는 항상 집에서 먹는 걸 더 좋아했어요."}
  ]},
  {id:16,phrase:"Do you happen to know...?",cat:"여행/일상",meaning:"혹시 ~을 아시나요?",ex:[
    {en:"Do you happen to know a good restaurant nearby?",kr:"혹시 근처에 좋은 식당 아세요?"},
    {en:"Did you happen to see my passport?",kr:"혹시 제 여권 보셨나요?"},
    {en:"Would you happen to know the bus number?",kr:"혹시 버스 번호를 아실까요?"},
    {en:"She might happen to know someone who can help.",kr:"그녀가 도움이 될 사람을 알 수도 있어요."},
    {en:"I was wondering if you happened to have a map.",kr:"혹시 지도가 있으신지 여쭤보려고요."}
  ]},
  {id:17,phrase:"Is it possible to...?",cat:"여행",meaning:"~이 가능한가요?",ex:[
    {en:"Is it possible to get a window seat?",kr:"창가 좌석이 가능한가요?"},
    {en:"Would it be possible to get a late checkout?",kr:"늦은 체크아웃이 가능할까요?"},
    {en:"It might be possible to upgrade your room.",kr:"방 업그레이드가 가능할 수도 있어요."},
    {en:"Was it possible to cancel without a fee?",kr:"수수료 없이 취소가 가능했나요?"},
    {en:"It has never been possible to enter after midnight.",kr:"자정 이후에 입장이 된 적은 없었어요."}
  ]},
  {id:18,phrase:"How much does it cost?",cat:"여행/일상",meaning:"얼마예요?",ex:[
    {en:"How much does it cost to get in?",kr:"입장료가 얼마예요?"},
    {en:"How much will it cost to fix this?",kr:"이거 고치는 데 얼마나 들까요?"},
    {en:"How much did it cost you to fly there?",kr:"거기까지 비행기 요금이 얼마였나요?"},
    {en:"It shouldn't cost more than twenty dollars.",kr:"20달러 이상은 안 들 거예요."},
    {en:"It has been costing more than I expected.",kr:"예상보다 더 많이 들고 있어요."}
  ]}
];

// ── Storage (localStorage fallback) ──────────────────────────────────────────
const store = {
  get(k){try{return localStorage.getItem(k)}catch{return null}},
  set(k,v){try{localStorage.setItem(k,v)}catch{}}
};

// ── State ─────────────────────────────────────────────────────────────────────
let progress = {};
let todayPhrases = [];
let reviewQueue = [];

// Practice state
let curPhrase = null;
let exIdx = 0;
let practiceResult = null;

// Review state
let revIdx = 0;
let revResult = null;

// ── Init ──────────────────────────────────────────────────────────────────────
function getDayKey(){
  const d=new Date();
  return `${d.getFullYear()}-${d.getMonth()}-${d.getDate()}`;
}
function getDueDate(level){
  const intervals=[1,3,7,14,30];
  const days=intervals[Math.min(level,4)];
  const d=new Date(); d.setDate(d.getDate()+days);
  return `${d.getFullYear()}-${d.getMonth()}-${d.getDate()}`;
}
function isToday(k){return k===getDayKey()}

function init(){
  const raw=store.get('eng_progress');
  progress=raw?JSON.parse(raw):{};

  const dayKey=getDayKey();
  let assigned=[];
  const rawToday=store.get('eng_today_'+dayKey);
  if(rawToday) assigned=JSON.parse(rawToday);
  if(!assigned.length){
    const available=DB.filter(p=>!progress[p.id]?.mastered);
    const shuffled=[...available].sort(()=>Math.random()-.5);
    assigned=shuffled.slice(0,3).map(p=>p.id);
    store.set('eng_today_'+dayKey,JSON.stringify(assigned));
  }
  todayPhrases=assigned.map(id=>DB.find(p=>p.id===id)).filter(Boolean);

  reviewQueue=DB.filter(p=>{
    const pr=progress[p.id];
    if(!pr||pr.level===0) return false;
    return isToday(pr.nextReview)||pr.nextReview<getDayKey();
  });

  renderHome();
}

function saveProgress(){
  store.set('eng_progress',JSON.stringify(progress));
}

// ── Home ─────────────────────────────────────────────────────────────────────
function renderHome(){
  const d=new Date();
  document.getElementById('date-badge').textContent=
    d.toLocaleDateString('ko-KR',{month:'long',day:'numeric',weekday:'short'});

  const done=todayPhrases.filter(p=>progress[p.id]?.level>0).length;
  document.getElementById('progress-fill').style.width=(done/3*100)+'%';
  document.getElementById('progress-label').textContent=done+' / 3 완료';

  const cardsEl=document.getElementById('phrase-cards');
  cardsEl.innerHTML='';
  todayPhrases.forEach(p=>{
    const isDone=progress[p.id]?.level>0;
    const lvl=progress[p.id]?.level||0;
    const pips=[0,1,2,3,4].map(i=>`<span class="pip${i<lvl?' on':''}"></span>`).join('');
    const card=document.createElement('div');
    card.className='phrase-card'+(isDone?' done':'');
    card.innerHTML=`
      <div class="phrase-main">"${p.phrase}"</div>
      <div class="phrase-meaning">${p.meaning}</div>
      <div class="phrase-meta">
        <span class="tag">${p.cat}</span>
        ${isDone
          ? `<span class="done-badge" style="margin-left:auto">✓ 완료 &nbsp;${pips}</span>`
          : `<span style="margin-left:auto;font-size:11px;color:var(--muted)">탭하여 시작 →</span>`}
      </div>`;
    card.onclick=()=>startPractice(p);
    cardsEl.appendChild(card);
  });

  const rcount=reviewQueue.length;
  document.getElementById('review-sub').textContent=
    rcount>0?'망각하기 전에 복습하세요':'오늘 복습할 항목이 없어요';
  const badge=document.getElementById('review-count-badge');
  badge.innerHTML=rcount>0
    ?`<div class="review-count">${rcount}</div>`
    :`<div style="font-size:12px;color:var(--muted)">✓</div>`;

  document.getElementById('stat-learning').textContent=Object.keys(progress).length;
  document.getElementById('stat-master').textContent=Object.values(progress).filter(p=>p.mastered).length;
}

function showScreen(id){
  ['home','practice','complete','review','reviewdone'].forEach(s=>{
    const el=document.getElementById('screen-'+s);
    if(el) el.style.display='none';
  });
  const target=document.getElementById('screen-'+id);
  if(target) target.style.display=(id==='practice'||id==='review')?'flex':'block';
}

function goHome(){
  showScreen('home');
  renderHome();
}

// ── Practice ──────────────────────────────────────────────────────────────────
function startPractice(phrase){
  curPhrase=phrase;
  exIdx=0;
  practiceResult=null;
  showScreen('practice');
  renderPractice();
}

function renderPractice(){
  const ex=curPhrase.ex[exIdx];
  // progress bar
  const pbar=document.getElementById('pbar');
  pbar.innerHTML=curPhrase.ex.map((_,i)=>
    `<div class="pstep${i<exIdx?' done':i===exIdx?' active':''}"></div>`
  ).join('');
  document.getElementById('phr-title').textContent='"'+curPhrase.phrase+'"';
  document.getElementById('phr-sub').textContent=curPhrase.meaning+' · 예문 '+(exIdx+1)+' / 5';
  document.getElementById('ex-num').textContent='예문 '+(exIdx+1);
  document.getElementById('ex-en').textContent=ex.en;
  document.getElementById('ex-kr').textContent=ex.kr;

  const body=document.getElementById('practice-body');
  body.innerHTML=`
    <div class="step-label">방법 선택</div>
    <div class="method-btns">
      <button class="method-btn" onclick="showTyping()">⌨️ 타이핑</button>
      <button class="method-btn" onclick="showSpeaking()">🎤 발음</button>
    </div>
    <div id="input-area"></div>`;
}

function normalize(s){return s.toLowerCase().replace(/[^a-z0-9 ']/g,'').trim()}
function similarity(a,b){
  const na=normalize(a),nb=normalize(b);
  if(na===nb) return 1;
  const wa=na.split(' '),wb=nb.split(' ');
  let m=0; wa.forEach(w=>{if(wb.includes(w))m++});
  return m/Math.max(wa.length,wb.length);
}

function showTyping(){
  const area=document.getElementById('input-area');
  area.innerHTML=`
    <div class="step-label">⌨️ 위 예문을 입력하세요</div>
    <textarea id="type-input" rows="3" placeholder="여기에 입력..."></textarea>
    <button class="btn btn-primary" id="type-submit" onclick="submitTyping()" disabled>확인</button>`;
  const inp=document.getElementById('type-input');
  inp.addEventListener('input',()=>{
    document.getElementById('type-submit').disabled=!inp.value.trim();
  });
  inp.addEventListener('keydown',e=>{
    if(e.key==='Enter'&&!e.shiftKey&&inp.value.trim()){e.preventDefault();submitTyping();}
  });
  inp.focus();
}

function submitTyping(){
  const inp=document.getElementById('type-input');
  const ex=curPhrase.ex[exIdx];
  const score=similarity(inp.value,ex.en);
  const correct=score>=0.8;
  inp.className=correct?'correct':'wrong';
  inp.disabled=true;
  document.getElementById('type-submit').style.display='none';
  showResult({score,correct,type:'type',answer:ex.en});
}

// ── Microphone Permission (한 번만 요청) ──────────────────────────────────────
let micStream=null;   // 권한 획득 후 stream 유지 → 재요청 없음
let micGranted=false;

async function ensureMicPermission(){
  if(micGranted) return true;
  // 이미 허용됐는지 먼저 조용히 확인
  try{
    const perm=await navigator.permissions.query({name:'microphone'});
    if(perm.state==='granted'){micGranted=true; return true;}
    if(perm.state==='denied') return false;
  }catch(e){}
  // 허용 안 됐으면 딱 한 번 요청
  try{
    micStream=await navigator.mediaDevices.getUserMedia({audio:true});
    micGranted=true;
    return true;
  }catch(e){
    micGranted=false;
    return false;
  }
}

// 앱 로드 시 조용히 권한 상태 확인 (팝업 없이)
(async()=>{
  try{
    const perm=await navigator.permissions.query({name:'microphone'});
    if(perm.state==='granted') micGranted=true;
  }catch(e){}
})();

function showSpeaking(){
  const area=document.getElementById('input-area');
  const hasSTT=!!(window.SpeechRecognition||window.webkitSpeechRecognition);
  if(!hasSTT){
    area.innerHTML=`
      <div style="color:var(--muted);font-size:13px;padding:12px;background:var(--surface);border-radius:10px;text-align:center">
        이 브라우저는 음성 인식을 지원하지 않아요.<br>Chrome 브라우저를 사용해 보세요.
      </div>
      <button class="btn btn-secondary" onclick="showTyping()" style="margin-top:8px">타이핑으로 전환</button>`;
    return;
  }
  area.innerHTML=`
    <div class="step-label">🎤 말하기 연습</div>
    <button class="btn btn-speak" id="speak-btn" onclick="toggleSpeech()">🎤 탭하여 말하기</button>
    <div class="transcript" id="transcript">인식된 내용이 여기에 표시됩니다...</div>`;
}

let recognition=null;
async function toggleSpeech(){
  const btn=document.getElementById('speak-btn');
  if(recognition){
    recognition.stop(); recognition=null;
    btn.className='btn btn-speak'; btn.textContent='🎤 탭하여 말하기';
    return;
  }
  // 권한이 없으면 딱 한 번 요청, 이후엔 바로 실행
  if(!micGranted){
    btn.textContent='⏳ 마이크 권한 확인 중...';
    btn.disabled=true;
    const ok=await ensureMicPermission();
    btn.disabled=false;
    if(!ok){
      document.getElementById('transcript').textContent='마이크 권한이 거부됐어요. 브라우저 주소창 옆 🔒 아이콘에서 허용해 주세요.';
      btn.textContent='🎤 탭하여 말하기';
      return;
    }
  }
  const SR=window.SpeechRecognition||window.webkitSpeechRecognition;
  recognition=new SR();
  recognition.lang='en-US'; recognition.interimResults=false;
  recognition.onstart=()=>{
    btn.className='btn btn-speak listening';
    btn.textContent='🔴 듣는 중... (탭하여 중지)';
  };
  recognition.onresult=e=>{
    const text=e.results[0][0].transcript;
    document.getElementById('transcript').textContent='"'+text+'"';
    const ex=curPhrase.ex[exIdx];
    const score=similarity(text,ex.en);
    const correct=score>=0.7;
    recognition=null;
    btn.disabled=true;
    showResult({score,correct,type:'speak',spoken:text,answer:ex.en});
  };
  recognition.onerror=recognition.onend=()=>{
    if(recognition){recognition=null;}
    if(btn){btn.className='btn btn-speak';btn.textContent='🎤 탭하여 말하기';}
  };
  recognition.start();
}

function showResult({score,correct,type,answer,spoken}){
  const area=document.getElementById('input-area');
  const existing=area.innerHTML;
  const resultHtml=`
    <div class="result-box" style="margin-top:10px">
      <div class="result-score ${correct?'good':'bad'}">${correct?'훌륭해요! ✓':'조금 더 연습해요'}</div>
      <div class="result-detail">정확도: ${Math.round(score*100)}%${type==='speak'&&spoken?' · 인식: "'+spoken+'"':''}</div>
      <div class="result-answer">${answer}</div>
    </div>
    <button class="btn btn-primary" onclick="nextExample()">${exIdx<4?'다음 예문 →':'이 구문 완료! ✓'}</button>
    ${!correct?`<button class="btn btn-secondary" onclick="retryExample()">다시 시도</button>`:''}`;
  area.innerHTML=existing+resultHtml;
}

function retryExample(){
  practiceResult=null;
  renderPractice();
  showTyping();
}

async function nextExample(){
  if(exIdx<curPhrase.ex.length-1){
    exIdx++;
    renderPractice();
  } else {
    // Completed
    const existing=progress[curPhrase.id]||{level:0};
    const newLevel=Math.min(existing.level+1,4);
    progress[curPhrase.id]={
      level:newLevel,
      nextReview:getDueDate(newLevel),
      mastered:newLevel>=4
    };
    saveProgress();
    const intervals=['1일 후','3일 후','7일 후','14일 후','30일 후'];
    document.getElementById('complete-sub').innerHTML=
      `"${curPhrase.phrase}"<br>모든 예문을 학습했어요`;
    document.getElementById('next-review-label').textContent=intervals[Math.min(newLevel-1,4)];
    showScreen('complete');
  }
}

// ── Review ────────────────────────────────────────────────────────────────────
function startReview(){
  if(!reviewQueue.length) return;
  revIdx=0; revResult=null;
  showScreen('review');
  renderReview();
}

function renderReview(){
  const cur=reviewQueue[revIdx];
  document.getElementById('review-progress-label').textContent=
    (revIdx+1)+' / '+reviewQueue.length+' · 한국어를 보고 영어로 답해보세요';
  const rpbar=document.getElementById('rpbar');
  rpbar.innerHTML=reviewQueue.map((_,i)=>
    `<div class="pstep${i<revIdx?' done':i===revIdx?' active':''}"></div>`
  ).join('');
  document.getElementById('review-kr').textContent=cur.meaning;
  document.getElementById('review-hint').textContent='카테고리: '+cur.cat;

  const body=document.getElementById('review-body');
  body.innerHTML=`
    <div class="step-label">영어로 입력하세요</div>
    <textarea id="rev-input" rows="2" placeholder='"${cur.phrase.split(' ')[0]}..."'></textarea>
    <button class="btn btn-primary" id="rev-submit" onclick="submitReview()" disabled>확인</button>`;
  const inp=document.getElementById('rev-input');
  inp.addEventListener('input',()=>{
    document.getElementById('rev-submit').disabled=!inp.value.trim();
  });
  inp.addEventListener('keydown',e=>{
    if(e.key==='Enter'&&!e.shiftKey&&inp.value.trim()){e.preventDefault();submitReview();}
  });
  inp.focus();
}

function submitReview(){
  const cur=reviewQueue[revIdx];
  const inp=document.getElementById('rev-input');
  const score=similarity(inp.value,cur.phrase);
  const correct=score>=0.7;
  revResult={score,correct};
  inp.className=correct?'correct':'wrong';
  inp.disabled=true;
  document.getElementById('rev-submit').style.display='none';
  const body=document.getElementById('review-body');
  body.innerHTML+=`
    <div class="result-box" style="margin-top:10px">
      <div class="result-score ${correct?'good':'bad'}">${correct?'정답! ✓':'아쉬워요'}</div>
      <div class="result-answer">${cur.phrase}</div>
      <div style="font-size:12px;color:var(--muted);margin-top:6px">${cur.meaning}</div>
    </div>
    <div class="btn-row">
      <button class="btn-pass" onclick="nextReview(true)">✓ 알았어요</button>
      <button class="btn-fail" onclick="nextReview(false)">✗ 다시 복습</button>
    </div>`;
}

function nextReview(passed){
  const cur=reviewQueue[revIdx];
  const existing=progress[cur.id]||{level:1};
  const newLevel=passed?Math.min(existing.level+1,4):Math.max(existing.level-1,1);
  progress[cur.id]={...existing,level:newLevel,nextReview:getDueDate(newLevel),mastered:newLevel>=4};
  saveProgress();
  if(revIdx<reviewQueue.length-1){
    revIdx++; revResult=null;
    renderReview();
  } else {
    document.getElementById('reviewdone-sub').textContent=
      reviewQueue.length+'개의 구문을 복습했어요\n꾸준히 하면 반드시 늘어요';
    showScreen('reviewdone');
  }
}

// Start
init();
</script>
</body>
</html>
