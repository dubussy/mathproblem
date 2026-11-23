<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>소크 선생님과 분수 탐험 (3학년 2학기 수학)</title>
<style>
:root{--main:#4f46e5;--main2:#eef2ff;--bot:#f1f5f9;--txt:#1e293b;--line:#e2e8f0}
*{box-sizing:border-box}
body{margin:0;font-family:"Pretendard","Apple SD Gothic Neo","Malgun Gothic",sans-serif;background:#f8fafc;color:var(--txt)}
.app{max-width:780px;margin:0 auto;height:100vh;height:100dvh;display:flex;flex-direction:column;background:#fff;border-left:1px solid var(--line);border-right:1px solid var(--line)}
header{padding:12px 16px;border-bottom:1px solid var(--line)}
.top{display:flex;justify-content:space-between;align-items:center;gap:8px}
.title{font-weight:800;font-size:17px}
.title small{display:block;font-weight:500;color:#64748b;font-size:12px}
.stat{font-size:13px;color:#475569;text-align:right;line-height:1.5}
.prog{height:8px;background:var(--line);border-radius:4px;margin-top:10px;overflow:hidden}
.prog>div{height:100%;width:0;background:var(--main);transition:width .4s}
#chat{flex:1;overflow-y:auto;padding:16px;display:flex;flex-direction:column;gap:10px}
.row{display:flex;gap:8px;align-items:flex-end}
.row.user{justify-content:flex-end}
.avatar{width:34px;height:34px;border-radius:50%;background:var(--main2);display:flex;align-items:center;justify-content:center;font-size:18px;flex-shrink:0}
.bubble{max-width:80%;padding:10px 14px;border-radius:14px;line-height:1.7;font-size:16px;word-break:keep-all}
.bot .bubble{background:var(--bot);border-bottom-left-radius:4px}
.user .bubble{background:var(--main);color:#fff;border-bottom-right-radius:4px}
.bot .bubble.q{background:#fff;border:2px solid var(--main);font-weight:600}
.bot .bubble.key{background:#fffbeb;border:1px solid #fcd34d}
.divider{align-self:center;font-size:13px;color:#4338ca;background:var(--main2);padding:4px 12px;border-radius:12px;margin:10px 0 2px}
.vis{margin-top:8px;background:#fff;border-radius:10px;padding:8px;border:1px solid var(--line);overflow-x:auto}
.typing span{display:inline-block;width:7px;height:7px;margin:0 2px;background:#94a3b8;border-radius:50%;animation:b 1s infinite}
.typing span:nth-child(2){animation-delay:.15s}
.typing span:nth-child(3){animation-delay:.3s}
@keyframes b{0%,60%,100%{transform:translateY(0);opacity:.5}30%{transform:translateY(-5px);opacity:1}}
footer{border-top:1px solid var(--line);padding:10px 12px;background:#fff}
#quick{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:8px}
#quick:empty{display:none}
.qbtn{border:1.5px solid var(--main);background:#fff;color:var(--main);padding:8px 16px;border-radius:18px;font-size:16px;cursor:pointer;font-family:inherit}
.qbtn:hover{background:var(--main2)}
.qbtn.sub{border-color:#cbd5e1;color:#64748b}
.qbtn.go{background:var(--main);color:#fff}
.inrow{display:flex;gap:8px}
#inp{flex:1;min-width:0;padding:11px 14px;border:1.5px solid var(--line);border-radius:22px;font-size:16px;font-family:inherit;outline:none}
#inp:focus{border-color:var(--main)}
#inp:disabled{background:#f1f5f9}
#send{padding:0 18px;border:none;border-radius:22px;background:var(--main);color:#fff;font-size:15px;font-weight:700;cursor:pointer;font-family:inherit}
#send:disabled{background:#cbd5e1;cursor:default}
.helper{font-size:12px;color:#94a3b8;margin-top:6px}
.fr{display:inline-flex;align-items:center;vertical-align:middle;margin:0 3px}
.fr .w{margin-right:2px;font-weight:700}
.st{display:inline-flex;flex-direction:column;align-items:center;font-size:.82em;line-height:1.15}
.nu{border-bottom:1.6px solid currentColor;padding:0 3px}
.de{padding:0 3px}
#start{position:fixed;inset:0;background:rgba(15,23,42,.55);display:flex;align-items:center;justify-content:center;padding:16px;z-index:10}
.card{background:#fff;border-radius:16px;max-width:470px;width:100%;padding:24px;max-height:95vh;overflow-y:auto}
.card h1{font-size:22px;margin:0 0 6px}
.card p{color:#475569;line-height:1.6;margin:0 0 12px;font-size:15px}
.card label{font-size:14px;font-weight:700;display:block;margin:14px 0 6px}
.card input{width:100%;padding:11px 12px;border:1.5px solid var(--line);border-radius:10px;font-size:16px;font-family:inherit}
.chips{display:flex;flex-wrap:wrap;gap:6px}
.chip{padding:7px 12px;border:1.5px solid var(--line);border-radius:16px;font-size:14px;cursor:pointer;background:#fff;font-family:inherit}
.chip.on{border-color:var(--main);background:var(--main2);color:#3730a3;font-weight:700}
.startbtn{margin-top:18px;width:100%;padding:13px;border:none;border-radius:12px;background:var(--main);color:#fff;font-size:17px;font-weight:800;cursor:pointer;font-family:inherit}
.how{background:#f8fafc;border-radius:10px;padding:10px 12px;font-size:13px;color:#475569;line-height:1.7}
.res table{border-collapse:collapse;width:100%;font-size:14px;margin-top:8px;background:#fff}
.res th,.res td{border:1px solid var(--line);padding:6px 8px;text-align:center}
.res th{background:#f8fafc}
.res td:first-child{text-align:left}
.bignum{font-size:28px;font-weight:800;color:var(--main)}
.rv{margin-top:10px;padding:8px 10px;background:#fff;border:1px solid var(--line);border-radius:8px;font-size:14px}
@media print{footer,#start{display:none}.app{height:auto}#chat{overflow:visible}}
</style>
</head>
<body>
<div class="app">
  <header>
    <div class="top">
      <div class="title">🦉 소크 선생님과 분수 탐험<small>3학년 2학기 수학 · 분수 단원 · 소크라테스 문답법</small></div>
      <div class="stat" id="stat">준비 중</div>
    </div>
    <div class="prog"><div id="bar"></div></div>
  </header>
  <div id="chat"></div>
  <footer>
    <div id="quick"></div>
    <div class="inrow">
      <input id="inp" placeholder="답을 입력하세요" disabled autocomplete="off">
      <button id="send" disabled>보내기</button>
    </div>
    <div class="helper">분수는 3/4 또는 4분의 3, 대분수는 2와 1/3 (또는 2 1/3)처럼 입력해요.</div>
  </footer>
</div>

<div id="start">
  <div class="card">
    <h1>🦉 소크 선생님과 분수 탐험</h1>
    <p>소크 선생님은 정답을 바로 알려 주지 않아요. 대신 <b>질문</b>을 던져서 여러분이 <b>스스로</b> 답을 찾도록 도와줘요.</p>
    <div class="how">✔ 틀려도 괜찮아요. 작은 질문을 따라가며 다시 생각해요.<br>✔ 모를 때는 <b>잘 모르겠어요</b> 버튼을 눌러요.<br>✔ 분수 입력: 3/4 · 대분수 입력: 2와 1/3</div>
    <label for="nm">이름(별명)</label>
    <input id="nm" maxlength="10" placeholder="예) 김분수">
    <label>공부할 범위</label>
    <div class="chips" id="chips"></div>
    <button class="startbtn" id="go">탐험 시작하기</button>
  </div>
</div>

<script>
const U1='분수로 나타내기', U2='분수만큼은 얼마일까', U3='진분수·가분수·대분수', U4='대분수와 가분수 바꾸기', U5='분수의 크기 비교';
const CMP3=['분자가 더 작아요','분자와 분모가 같아요','분자가 더 커요'];

const P=[
/* 1 */ {u:U1,type:'frac',ans:'3/4',q:'사과 12개를 3개씩 묶었어요. 색칠한 사과 9개는 12개의 몇 분의 몇일까요?',visual:{t:'groups',total:12,per:3,hl:9},
 steps:[
  {type:'num',ans:4,q:'먼저 전체부터 볼까요? 사과 12개를 3개씩 묶으면 모두 몇 묶음이 되나요?',hint:'그림의 점선 묶음을 하나씩 세어 보세요. 3+3+3+3=12예요.'},
  {type:'num',ans:3,q:'좋아요. 그럼 색칠한 사과 9개는 몇 묶음인가요?',hint:'9개를 3개씩 나누어 보세요. 3+3+3=9예요.'},
  {type:'choice',opts:['분자','분모'],ans:'분모',q:'전체 묶음 수 4는 분수의 어디에 쓸까요?',hint:'분수의 아래쪽 수는 전체를 똑같이 몇으로 나누었는지를 나타내요.'}
 ],
 key:'전체 묶음 수는 <b>분모</b>, 부분의 묶음 수는 <b>분자</b>예요. 12를 3씩 묶으면 4묶음, 9는 그중 3묶음이니까 [[3/4]]이에요.'},
/* 2 */ {u:U1,type:'frac',ans:'3/5',q:'연필 10자루를 2자루씩 묶었어요. 색칠한 연필 6자루는 10자루의 몇 분의 몇일까요?',visual:{t:'groups',total:10,per:2,hl:6},
 steps:[
  {type:'num',ans:5,q:'연필 10자루를 2자루씩 묶으면 모두 몇 묶음인가요?',hint:'2씩 뛰어 세어 보세요. 2, 4, 6, 8, 10 — 몇 번 셌나요?'},
  {type:'num',ans:3,q:'연필 6자루는 몇 묶음인가요?',hint:'2, 4, 6 — 몇 번 만에 6이 되었나요?'}
 ],
 key:'10을 2씩 묶으면 5묶음, 6은 그중 3묶음이니까 [[3/5]]이에요.'},
/* 3 */ {u:U1,type:'frac',ans:'2/3',q:'사탕 15개를 5개씩 묶었어요. 색칠한 사탕 10개는 15개의 몇 분의 몇일까요?',visual:{t:'groups',total:15,per:5,hl:10},
 steps:[
  {type:'num',ans:3,q:'사탕 15개를 5개씩 묶으면 모두 몇 묶음인가요?',hint:'5, 10, 15 — 5씩 몇 번 뛰어 세었나요?'},
  {type:'num',ans:2,q:'사탕 10개는 몇 묶음인가요?',hint:'5, 10 — 몇 번 만에 10이 되었나요?'}
 ],
 key:'15를 5씩 묶으면 3묶음, 10은 그중 2묶음이니까 [[2/3]]이에요.'},
/* 4 */ {u:U1,type:'frac',ans:'5/7',q:'딸기 14개를 2개씩 묶었어요. 색칠한 딸기 10개는 14개의 몇 분의 몇일까요?',visual:{t:'groups',total:14,per:2,hl:10},
 steps:[
  {type:'num',ans:7,q:'딸기 14개를 2개씩 묶으면 모두 몇 묶음인가요?',hint:'2, 4, 6, 8, 10, 12, 14 — 몇 번 셌나요?'},
  {type:'num',ans:5,q:'딸기 10개는 몇 묶음인가요?',hint:'2, 4, 6, 8, 10 — 몇 번 만에 10이 되었나요?'},
  {type:'choice',opts:['분자','분모'],ans:'분자',q:'부분의 묶음 수 5는 분수의 어디에 쓸까요?',hint:'분수의 위쪽 수는 전체 중 몇 개를 가리키는지 알려 줘요.'}
 ],
 key:'14를 2씩 묶으면 7묶음(분모), 10은 그중 5묶음(분자)이니까 [[5/7]]이에요.'},
/* 5 */ {u:U2,type:'num',ans:4,q:'구슬 12개의 [[1/3]]은 몇 개일까요?',
 steps:[
  {type:'num',ans:3,q:'[[1/3]]은 전체를 똑같이 몇 묶음으로 나눈 것 중의 하나일까요?',hint:'분모를 보세요. 분모는 전체를 똑같이 나눈 수예요.'},
  {type:'num',ans:4,q:'구슬 12개를 똑같이 3묶음으로 나누면 한 묶음에 몇 개씩인가요?',visual:{t:'groups',total:12,per:4,hl:0},hint:'그림처럼 3묶음으로 나누어 세어 보세요. 4+4+4=12예요.'}
 ],
 key:'12의 [[1/3]]은 12를 똑같이 3묶음으로 나눈 것 중 1묶음이므로 <b>4개</b>예요.'},
/* 6 */ {u:U2,type:'num',ans:8,q:'구슬 12개의 [[2/3]]은 몇 개일까요?',
 steps:[
  {type:'num',ans:4,q:'12의 [[1/3]]은 몇 개였나요?',visual:{t:'groups',total:12,per:4,hl:0},hint:'12를 똑같이 3묶음으로 나누면 한 묶음은 몇 개인가요?'},
  {type:'num',ans:2,q:'[[2/3]]은 [[1/3]]이 몇 개 모인 것인가요?',hint:'분자를 보세요. 분자는 몇 묶음을 가리키는지 알려 줘요.'}
 ],
 key:'12의 [[1/3]]은 4개, [[2/3]]은 4개씩 2묶음이므로 <b>8개</b>예요.'},
/* 7 */ {u:U2,type:'num',ans:15,q:'색종이 20장의 [[3/4]]은 몇 장일까요?',
 steps:[
  {type:'num',ans:5,q:'20장을 똑같이 4묶음으로 나누면 한 묶음은 몇 장인가요?',visual:{t:'groups',total:20,per:5,hl:0},hint:'4묶음이 모두 같아야 해요. 5+5+5+5=20이에요.'},
  {type:'num',ans:3,q:'[[3/4]]은 그중 몇 묶음을 말하나요?',hint:'분자를 보세요.'}
 ],
 key:'20의 [[1/4]]은 5장, [[3/4]]은 5장씩 3묶음이므로 <b>15장</b>이에요.'},
/* 8 */ {u:U2,type:'num',ans:12,q:'길이가 30 cm인 색 테이프의 [[2/5]]는 몇 cm일까요?',
 steps:[
  {type:'num',ans:6,q:'30 cm를 똑같이 5부분으로 나누면 한 부분은 몇 cm인가요?',hint:'5부분의 길이가 모두 같아야 해요. 5×6=30이에요.'},
  {type:'num',ans:2,q:'[[2/5]]는 그중 몇 부분인가요?',hint:'분자를 보세요.'}
 ],
 key:'30 cm의 [[1/5]]은 6 cm, [[2/5]]는 6 cm가 2개이므로 <b>12 cm</b>예요.'},
/* 9 */ {u:U2,type:'num',ans:9,q:'사탕 24개 중 [[3/8]]을 먹었어요. 먹은 사탕은 몇 개일까요?',
 steps:[
  {type:'num',ans:3,q:'24개를 똑같이 8묶음으로 나누면 한 묶음에 몇 개씩인가요?',visual:{t:'groups',total:24,per:3,hl:0},hint:'8×3=24예요. 그림의 묶음 하나에 몇 개가 있나요?'},
  {type:'num',ans:3,q:'[[3/8]]은 그중 몇 묶음인가요?',hint:'분자를 보세요.'}
 ],
 key:'24의 [[1/8]]은 3개, [[3/8]]은 3개씩 3묶음이므로 <b>9개</b>예요.'},
/* 10 */ {u:U3,type:'choice',opts:['진분수','가분수','대분수'],ans:'진분수',q:'[[3/5]]는 진분수, 가분수, 대분수 중 무엇일까요?',visual:{t:'bars',items:[{n:3,d:5,label:'3/5'}]},
 steps:[
  {type:'choice',opts:CMP3,ans:'분자가 더 작아요',q:'[[3/5]]에서 분자 3과 분모 5를 비교하면 어떤가요?',hint:'분자는 위의 수, 분모는 아래의 수예요. 3과 5 중 어느 수가 더 작나요?'},
  {type:'choice',opts:['1보다 작아요','1과 같아요','1보다 커요'],ans:'1보다 작아요',q:'그림을 보세요. [[3/5]]는 1(막대 하나 전체)과 비교하면 어떤가요?',hint:'막대 5칸이 모두 색칠되었나요?'}
 ],
 key:'분자가 분모보다 작은 분수를 <b>진분수</b>라고 해요. 진분수는 1보다 작아요.'},
/* 11 */ {u:U3,type:'choice',opts:['진분수','가분수','대분수'],ans:'가분수',q:'[[7/4]]는 진분수, 가분수, 대분수 중 무엇일까요?',visual:{t:'bars',items:[{n:7,d:4,label:'7/4'}]},
 steps:[
  {type:'choice',opts:CMP3,ans:'분자가 더 커요',q:'[[7/4]]에서 분자 7과 분모 4를 비교하면 어떤가요?',hint:'7과 4 중 어느 수가 더 큰가요?'},
  {type:'num',ans:1,q:'[[4/4]]는 자연수 얼마와 같나요?',hint:'4칸 중 4칸을 모두 칠하면 막대 하나가 꽉 차요.'}
 ],
 key:'분자가 분모와 같거나 분모보다 큰 분수를 <b>가분수</b>라고 해요. [[7/4]]는 [[4/4]](=1)보다 크니까 1보다 커요.'},
/* 12 */ {u:U3,type:'choice',opts:['진분수','가분수','대분수'],ans:'대분수',q:'[[2 1/3]]은 진분수, 가분수, 대분수 중 무엇일까요?',
 steps:[
  {type:'frac',ans:'1/3',q:'[[2 1/3]]은 자연수 2와 어떤 분수가 합쳐진 모양인가요?',hint:'2 옆에 붙어 있는 분수를 그대로 써 보세요.'},
  {type:'choice',opts:['진분수','가분수'],ans:'진분수',q:'[[1/3]]은 진분수인가요, 가분수인가요?',hint:'분자 1과 분모 3을 비교해 보세요.'}
 ],
 key:'자연수와 진분수로 이루어진 분수를 <b>대분수</b>라고 해요. [[2 1/3]]은 2와 [[1/3]]이에요.'},
/* 13 */ {u:U3,type:'choice',opts:['진분수','가분수','대분수'],ans:'가분수',q:'[[5/5]]는 진분수, 가분수, 대분수 중 무엇일까요?',visual:{t:'bars',items:[{n:5,d:5,label:'5/5'}]},
 steps:[
  {type:'choice',opts:CMP3,ans:'분자와 분모가 같아요',q:'[[5/5]]에서 분자와 분모를 비교하면 어떤가요?',hint:'위의 수와 아래의 수를 보세요.'},
  {type:'choice',opts:['네, 작아요','아니요, 작지 않아요'],ans:'아니요, 작지 않아요',q:'진분수는 분자가 분모보다 작은 분수예요. [[5/5]]는 분자가 분모보다 작나요?',hint:'5는 5보다 작을까요?'}
 ],
 key:'분자와 분모가 같은 분수도 <b>가분수</b>예요. [[5/5]]는 자연수 1과 같아요.'},
/* 14 */ {u:U3,type:'num',ans:5,q:'분모가 6인 진분수는 모두 몇 개일까요?',
 steps:[
  {type:'choice',opts:['6보다 작아야 해요','6과 같아야 해요','6보다 커야 해요'],ans:'6보다 작아야 해요',q:'분모가 6인 분수가 진분수가 되려면 분자는 어떤 수여야 할까요?',hint:'진분수는 분자가 분모보다 작은 분수였어요.'},
  {type:'num',ans:1,q:'분자가 될 수 있는 가장 작은 자연수는 얼마인가요?',hint:'자연수 중에서 가장 작은 수를 생각해 보세요.'},
  {type:'num',ans:5,q:'분자가 될 수 있는 가장 큰 자연수는 얼마인가요?',hint:'6보다 작은 자연수 중 가장 큰 수예요.'}
 ],
 key:'[[1/6]], [[2/6]], [[3/6]], [[4/6]], [[5/6]] → 분모가 6인 진분수는 <b>5개</b>예요.'},
/* 15 */ {u:U4,type:'frac',ans:'5/3',q:'[[1 2/3]]을 가분수로 나타내 보세요.',visual:{t:'bars',items:[{n:5,d:3,label:'1 2/3'}]},
 steps:[
  {type:'num',ans:3,q:'자연수 1은 [[1/3]]이 몇 개인가요?',hint:'막대 하나를 3칸으로 나누었어요. 꽉 찬 막대는 몇 칸인가요?'},
  {type:'num',ans:2,q:'[[2/3]]은 [[1/3]]이 몇 개인가요?',hint:'분자를 보세요.'},
  {type:'num',ans:5,q:'그럼 [[1 2/3]]은 [[1/3]]이 모두 몇 개인가요?',hint:'3개와 2개를 더해 보세요.'}
 ],
 key:'[[1 2/3]]은 [[1/3]]이 3+2=5개이므로 [[5/3]]이에요. (자연수×분모+분자)를 분자에 써요.'},
/* 16 */ {u:U4,type:'frac',ans:'11/4',q:'[[2 3/4]]을 가분수로 나타내 보세요.',visual:{t:'bars',items:[{n:11,d:4,label:'2 3/4'}]},
 steps:[
  {type:'num',ans:8,q:'자연수 2는 [[1/4]]이 몇 개인가요?',hint:'1은 [[1/4]]이 4개예요. 그럼 2는요?'},
  {type:'num',ans:11,q:'[[3/4]]까지 더하면 [[1/4]]이 모두 몇 개인가요?',hint:'8에 3을 더해 보세요.'}
 ],
 key:'2×4+3=11이므로 [[2 3/4]] = [[11/4]]이에요.'},
/* 17 */ {u:U4,type:'frac',ans:'2 1/3',q:'[[7/3]]을 대분수로 나타내 보세요.',visual:{t:'bars',items:[{n:7,d:3,label:'7/3'}]},
 steps:[
  {type:'num',ans:1,q:'[[3/3]]은 자연수 얼마와 같나요?',hint:'3칸이 모두 칠해진 막대 하나를 보세요.'},
  {type:'num',ans:2,q:'[[7/3]] 안에는 [[3/3]]이 몇 번 들어가나요?',hint:'그림에서 꽉 찬 막대는 몇 개인가요?'},
  {type:'num',ans:1,q:'꽉 찬 막대 2개를 빼면 [[1/3]]이 몇 개 남나요?',hint:'7−3−3=?'}
 ],
 key:'[[7/3]] = [[3/3]] + [[3/3]] + [[1/3]] = [[2 1/3]]이에요.'},
/* 18 */ {u:U4,type:'frac',ans:'2 3/5',q:'[[13/5]]을 대분수로 나타내 보세요.',
 steps:[
  {type:'num',ans:2,q:'[[5/5]]는 1이에요. 13 안에 5가 몇 번 들어가나요?',hint:'5, 10, 15… 13을 넘지 않을 때까지 뛰어 세어 보세요.'},
  {type:'num',ans:3,q:'13에서 5를 2번 빼면 얼마가 남나요?',hint:'13−10=?'}
 ],
 key:'13 안에 5가 2번 들어가고 3이 남으므로 [[13/5]] = [[2 3/5]]이에요.'},
/* 19 */ {u:U5,type:'cmp',ans:'>',q:'[[5/7]] ○ [[3/7]]<br>○ 안에 &gt;, =, &lt; 중 알맞은 것을 골라 보세요.',
 steps:[
  {type:'choice',opts:['같아요','달라요'],ans:'같아요',q:'두 분수의 분모는 같나요?',hint:'아래의 수를 비교해 보세요.'},
  {type:'choice',opts:['분자가 큰 쪽','분자가 작은 쪽'],ans:'분자가 큰 쪽',q:'분모가 같을 때, [[1/7]]이 더 많이 모인 쪽은 분자가 큰 쪽일까요, 작은 쪽일까요?',visual:{t:'bars',items:[{n:5,d:7,label:'5/7'},{n:3,d:7,label:'3/7'}]},hint:'그림에서 색칠한 칸 수를 비교해 보세요.'}
 ],
 key:'분모가 같으면 분자가 클수록 큰 분수예요. 5 &gt; 3이므로 [[5/7]] &gt; [[3/7]]이에요.'},
/* 20 */ {u:U5,type:'cmp',ans:'<',q:'[[19/6]] ○ [[3 2/6]]<br>○ 안에 &gt;, =, &lt; 중 알맞은 것을 골라 보세요.',
 steps:[
  {type:'frac',ans:'20/6',q:'비교하기 쉽게 [[3 2/6]]을 가분수로 바꾸어 볼까요?',hint:'3은 [[1/6]]이 18개예요. 거기에 2개를 더하면요?'},
  {type:'choice',opts:['19/6','20/6'],ans:'20/6',q:'[[19/6]]과 [[20/6]] 중 더 큰 분수는 무엇인가요?',hint:'분모가 같으니 분자를 비교해 보세요.'}
 ],
 key:'[[3 2/6]] = [[20/6]]이고, 19 &lt; 20이므로 [[19/6]] &lt; [[3 2/6]]이에요. 대분수와 가분수는 한쪽 모양으로 바꾸어 비교해요.'}
];

const OK_MAIN=['정답이에요! 👏','훌륭해요! 바로 맞혔어요. 🎯','맞아요! 생각이 아주 또렷하네요. ✨','정확해요! 대단해요. 🌟'];
const OK_SHORT=['맞아요! 👍','좋아요, 바로 그거예요!','정확해요! ✨','잘 생각했어요!'];
const WRONG_MAIN=['음, 그렇게 생각한 이유가 있었을 거예요. 작은 질문부터 하나씩 따라가 볼까요?','아직 정답은 아니지만 괜찮아요. 질문을 따라가며 함께 생각해 봐요.','좋은 시도예요! 그럼 이렇게 생각해 보면 어떨까요?'];

const $=s=>document.querySelector(s);
const chat=$('#chat'), inp=$('#inp'), sendBtn=$('#send'), quick=$('#quick');
let NAME='친구', LIST=[], RESULT={}, stats={first:0,second:0}, resolver=null;

function pick(a){return a[Math.floor(Math.random()*a.length)];}
function sleep(ms){return new Promise(r=>setTimeout(r,ms));}
function esc(s){
  return String(s).replace(/[&<>"']/g,function(c){
    return {'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c];
  });
}
function fracHTML(w,n,d){
  return '<span class="fr">'+(w?'<span class="w">'+w+'</span>':'')+'<span class="st"><span class="nu">'+n+'</span><span class="de">'+d+'</span></span></span>';
}
function fmt(t){
  return t.replace(/\[\[(?:(\d+) )?(\d+)\/(\d+)\]\]/g,function(m,w,n,d){
    return fracHTML(w,n,d);
  });
}

/* ---------- 시각 자료 ---------- */
function svgGroups(v){
  const g=v.total/v.per, r=9, gap=4, pad=6;
  const gw=v.per*(2*r+gap)-gap+pad*2, gh=2*r+pad*2, maxW=360;
  let x=0, y=0, W=0, idx=0, s='';
  for(let k=0;k<g;k++){
    if(x+gw>maxW && x>0){x=0; y+=gh+8;}
    s+='<rect x="'+(x+1)+'" y="'+(y+1)+'" width="'+(gw-2)+'" height="'+(gh-2)+'" rx="10" fill="none" stroke="#94a3b8" stroke-dasharray="4 3"/>';
    for(let j=0;j<v.per;j++){
      const cx=x+pad+r+j*(2*r+gap), cy=y+pad+r, on=idx<(v.hl||0);
      s+='<circle cx="'+cx+'" cy="'+cy+'" r="'+r+'" fill="'+(on?'#f97316':'#cbd5e1')+'"/>';
      idx++;
    }
    x+=gw+8;
    W=Math.max(W,x);
  }
  const H=y+gh+2;
  return '<svg viewBox="0 0 '+W+' '+H+'" width="'+W+'" style="max-width:100%;height:auto">'+s+'</svg>';
}
function svgBars(v){
  const U=170, H=26, LW=60, GAP=10;
  let maxUnits=1;
  v.items.forEach(function(it){
    maxUnits=Math.max(maxUnits,Math.ceil(it.n/it.d));
  });
  const W=LW+maxUnits*(U+GAP), Ht=v.items.length*(H+14)+4;
  let s='';
  v.items.forEach(function(it,r){
    const y=4+r*(H+14), units=Math.max(1,Math.ceil(it.n/it.d)), cw=U/it.d;
    let c=0;
    s+='<text x="0" y="'+(y+H/2+5)+'" font-size="15" fill="#334155">'+it.label+'</text>';
    for(let u=0;u<units;u++){
      const x0=LW+u*(U+GAP);
      for(let k=0;k<it.d;k++){
        const on=c<it.n;
        c++;
        s+='<rect x="'+(x0+k*cw)+'" y="'+y+'" width="'+cw+'" height="'+H+'" fill="'+(on?'#818cf8':'#ffffff')+'" stroke="#475569" stroke-width="1"/>';
      }
    }
  });
  return '<svg viewBox="0 0 '+W+' '+Ht+'" width="'+W+'" style="max-width:100%;height:auto">'+s+'</svg>';
}
function drawVis(v){
  return v.t==='groups'?svgGroups(v):svgBars(v);
}

/* ---------- 채팅 UI ---------- */
function scrollDown(){chat.scrollTop=chat.scrollHeight;}
function addMsg(who,html,cls){
  const row=document.createElement('div');
  row.className='row '+who;
  if(who==='bot'){
    const av=document.createElement('div');
    av.className='avatar';
    av.textContent='🦉';
    row.appendChild(av);
  }
  const b=document.createElement('div');
  b.className='bubble'+(cls?' '+cls:'');
  b.innerHTML=html;
  row.appendChild(b);
  chat.appendChild(row);
  scrollDown();
  return row;
}
function addDivider(t){
  const d=document.createElement('div');
  d.className='divider';
  d.textContent=t;
  chat.appendChild(d);
  scrollDown();
}
async function bot(text,visual,cls){
  const t=addMsg('bot','<span class="typing"><span></span><span></span><span></span></span>');
  await sleep(Math.min(1000,320+text.replace(/<[^>]+>/g,'').length*12));
  t.remove();
  addMsg('bot',fmt(text)+(visual?'<div class="vis">'+drawVis(visual)+'</div>':''),cls);
}
function waitInput(o){
  quick.innerHTML='';
  (o.choices||[]).forEach(function(c){
    const b=document.createElement('button');
    b.className='qbtn'+(o.go?' go':'');
    b.textContent=c;
    b.onclick=function(){submit(c,c);};
    quick.appendChild(b);
  });
  if(o.idk){
    const b=document.createElement('button');
    b.className='qbtn sub';
    b.textContent='🤔 잘 모르겠어요';
    b.onclick=function(){submit('__IDK__','잘 모르겠어요');};
    quick.appendChild(b);
  }
  if(o.skip){
    const b=document.createElement('button');
    b.className='qbtn sub';
    b.textContent='건너뛸래요';
    b.onclick=function(){submit('__SKIP__','건너뛸래요');};
    quick.appendChild(b);
  }
  inp.disabled=!o.text;
  sendBtn.disabled=!o.text;
  inp.placeholder=o.text?(o.ph||'답을 입력하세요'):'위의 버튼을 눌러 답해요';
  if(o.text){inp.focus();}
  scrollDown();
  return new Promise(function(res){resolver=res;});
}
function submit(val,label){
  if(!resolver){return;}
  addMsg('user',esc(label));
  const r=resolver;
  resolver=null;
  quick.innerHTML='';
  inp.value='';
  inp.disabled=true;
  sendBtn.disabled=true;
  r(val);
}
function doSend(){
  const v=inp.value.trim();
  if(!v||inp.disabled){return;}
  submit(v,v);
}
sendBtn.onclick=doSend;
inp.addEventListener('keydown',function(e){
  if(e.key==='Enter'&&!e.isComposing){
    e.preventDefault();
    doSend();
  }
});

/* ---------- 채점 ---------- */
function parseFrac(raw){
  let s=String(raw).trim();
  s=s.replace(/(\d+)\s*분\s*의\s*(\d+)/g,'$2/$1');
  s=s.replace(/[^\d\/와과\s]+/g,' ').replace(/\s+/g,' ').trim();
  let m=s.match(/^(\d+)\s*(?:와|과|\s)\s*(\d+)\s*\/\s*(\d+)$/);
  if(m){return {w:+m[1],n:+m[2],d:+m[3]};}
  m=s.match(/^(\d+)\s*\/\s*(\d+)$/);
  if(m){return {w:0,n:+m[1],d:+m[2]};}
  m=s.match(/^(\d+)$/);
  if(m){return {w:+m[1],n:0,d:1};}
  return null;
}
function judge(v,it){
  if(v==='__IDK__'){return 'idk';}
  if(it.type==='num'){
    const m=String(v).match(/\d+/);
    if(!m){return 'invalid';}
    return (+m[0]===it.ans)?'ok':'no';
  }
  if(it.type==='choice'||it.type==='cmp'){
    return (String(v).trim()===it.ans)?'ok':'no';
  }
  const p=parseFrac(v);
  if(!p||p.d===0){return 'invalid';}
  const a=parseFrac(it.ans);
  if(p.w===a.w&&p.n===a.n&&p.d===a.d){return 'ok';}
  if((p.w*p.d+p.n)*a.d===(a.w*a.d+a.n)*p.d){return 'equiv';}
  if(!p.w&&!a.w&&p.n===a.d&&p.d===a.n){return 'swap';}
  return 'no';
}
function ansText(it){
  if(it.type==='frac'){
    const a=parseFrac(it.ans);
    return a.w?'[['+a.w+' '+a.n+'/'+a.d+']]':'[['+a.n+'/'+a.d+']]';
  }
  return esc(String(it.ans));
}
function optsFor(it){
  if(it.type==='choice'){return {choices:it.opts,idk:true,text:false};}
  if(it.type==='cmp'){return {choices:['>','=','<'],idk:true,text:false};}
  return {text:true,idk:true,ph:it.type==='frac'?'예) 3/4 또는 2와 1/3':'숫자로 답해요'};
}

/* ---------- 문답 진행 ---------- */
async function askItem(it,cls){
  await bot(it.q,it.visual,cls);
  let eq=0;
  while(true){
    const v=await waitInput(optsFor(it));
    const r=judge(v,it);
    if(r==='invalid'){
      await bot(it.type==='frac'?'분수로 답해 볼까요? 예) 3/4, 2와 1/3':'숫자로 답해 볼까요?');
      continue;
    }
    if(r==='equiv'&&eq<2){
      eq++;
      await bot('오, 크기는 같은 수예요! 👀 그런데 질문에서 묻는 모양으로 다시 나타내 볼래요?');
      continue;
    }
    return r==='equiv'?'no':r;
  }
}
async function runStep(s){
  await bot(s.q,s.visual);
  let tries=0, eq=0;
  while(true){
    const v=await waitInput(optsFor(s));
    const r=judge(v,s);
    if(r==='invalid'){
      await bot(s.type==='frac'?'분수로 답해 볼까요? 예) 3/4':'숫자로 답해 볼까요?');
      continue;
    }
    if(r==='equiv'&&eq<2){
      eq++;
      await bot('크기는 같아요! 그런데 질문에서 묻는 모양으로 다시 나타내 볼래요?');
      continue;
    }
    if(r==='ok'){
      await bot(pick(OK_SHORT));
      return true;
    }
    tries++;
    if(tries===1){
      await bot((r==='idk'?'괜찮아요, 힌트를 줄게요. ':'')+'🤔 '+s.hint+'<br>다시 한번 생각해 볼까요?');
    } else {
      await bot('같이 확인해 봐요. 답은 <b>'+ansText(s)+'</b>예요. 다음 질문으로 넘어가 볼게요.');
      return false;
    }
  }
}
function updateStat(k){
  $('#stat').innerHTML='문제 '+Math.min(k+1,LIST.length)+' / '+LIST.length+'<br>⭐ 첫 시도 정답 '+stats.first;
  $('#bar').style.width=(k/LIST.length*100)+'%';
}
async function runProblem(k){
  const i=LIST[k], p=P[i];
  updateStat(k);
  addDivider('문제 '+(i+1)+' · '+p.u);
  let r=await askItem(p,'q');
  if(r==='ok'){
    stats.first++;
    RESULT[i]='first';
    updateStat(k);
    await bot(pick(OK_MAIN));
    await bot('어떻게 그 답을 찾았는지 나만의 말로 설명해 줄래요?');
    const why=await waitInput({text:true,skip:true,ph:'생각한 방법을 적어 보세요'});
    if(why!=='__SKIP__'){
      await bot('자기 생각을 말로 설명할 수 있다니 멋져요! 선생님이 정리한 것과 비교해 보세요.');
    }
    await bot('💡 '+p.key,null,'key');
  } else {
    if(r==='swap'){
      await bot('앗, 분자와 분모가 서로 바뀐 것 같아요. 전체를 나타내는 수는 위에 쓸까요, 아래에 쓸까요? 차근차근 따져 봐요.');
    } else if(r==='idk'){
      await bot('괜찮아요! 모르는 것을 솔직하게 말하는 것이 배움의 시작이에요. 작은 질문부터 같이 해 봐요.');
    } else {
      await bot(pick(WRONG_MAIN));
    }
    for(const s of p.steps){
      await runStep(s);
    }
    await bot('이제 처음 질문으로 돌아가 볼까요? 지금까지 생각한 것을 이용해 보세요.');
    r=await askItem(p,'q');
    if(r==='ok'){
      stats.second++;
      RESULT[i]='second';
      await bot('해냈어요! 질문을 따라가며 스스로 길을 찾아냈네요. 👏');
    } else {
      RESULT[i]='review';
      await bot('정답은 <b>'+ansText(p)+'</b>예요. 괜찮아요, 다음에 다시 만나면 꼭 풀 수 있을 거예요.');
    }
    await bot('💡 '+p.key,null,'key');
  }
  await waitInput({choices:[k<LIST.length-1?'다음 문제로 →':'결과 보기'],go:true,text:false});
}
async function showResult(){
  $('#bar').style.width='100%';
  const n=LIST.length, f=stats.first, s2=stats.second, rv=n-f-s2;
  $('#stat').innerHTML='완료!<br>⭐ 첫 시도 정답 '+f;
  const stars=f/n>=0.8?'⭐⭐⭐':(f/n>=0.5?'⭐⭐':'⭐');
  const units=[U1,U2,U3,U4,U5];
  let rows='';
  units.forEach(function(u){
    const ids=LIST.filter(function(i){return P[i].u===u;});
    if(!ids.length){return;}
    const a=ids.filter(function(i){return RESULT[i]==='first';}).length;
    const b=ids.filter(function(i){return RESULT[i]==='second';}).length;
    rows+='<tr><td>'+u+'</td><td>'+ids.length+'</td><td>'+a+'</td><td>'+b+'</td><td>'+(ids.length-a-b)+'</td></tr>';
  });
  let review='';
  LIST.filter(function(i){return RESULT[i]!=='first';}).forEach(function(i){
    review+='<div class="rv"><b>문제 '+(i+1)+'</b> ('+(RESULT[i]==='second'?'도움 받아 해결':'다시 보기')+') '+P[i].q.split('<br>')[0]+'<br>💡 '+P[i].key+'</div>';
  });
  await bot(esc(NAME)+', 분수 탐험을 모두 마쳤어요! 🎉');
  const html='<div class="res"><div>'+stars+'</div><div><span class="bignum">'+f+'</span> / '+n+' 문제를 처음에 바로 맞혔어요.</div>'+
    '<div>질문을 따라가며 해결: <b>'+s2+'</b>개 · 다시 보면 좋은 문제: <b>'+rv+'</b>개</div>'+
    '<table><tr><th>영역</th><th>문항</th><th>바로 정답</th><th>도움 후 정답</th><th>다시 보기</th></tr>'+rows+'</table>'+
    (review?'<div style="margin-top:12px;font-weight:700">다시 살펴볼 문제</div>'+review:'<div style="margin-top:10px">모든 문제를 처음에 맞혔어요. 완벽해요!</div>')+'</div>';
  addMsg('bot',fmt(html));
  await bot('마지막 질문이에요. 오늘 분수에 대해 새롭게 알게 된 것은 무엇인가요? 한 줄로 적어 보세요.');
  const last=await waitInput({text:true,skip:true,ph:'새롭게 알게 된 점'});
  if(last!=='__SKIP__'){
    await bot('멋진 정리예요! 스스로 질문하고 답을 찾는 습관이 수학을 잘하는 비결이에요. 🦉');
  } else {
    await bot('오늘도 수고 많았어요! 다음 탐험에서 또 만나요. 🦉');
  }
  while(true){
    const c=await waitInput({choices:['처음부터 다시 하기','결과 인쇄하기'],text:false});
    if(c==='결과 인쇄하기'){
      window.print();
    } else {
      location.reload();
      return;
    }
  }
}
async function main(){
  await bot('안녕하세요, '+esc(NAME)+'! 저는 <b>소크 선생님</b>이에요. 🦉');
  await bot('옛날 그리스의 소   라테스는 답을 알려 주는 대신 <b>질문</b>을 해서 사람들이 스스로 깨닫게 했대요. 저도 그렇게 해 볼게요.');
  await bot('오늘은 분수 문제 <b>'+LIST.length+'개</b>를 함께 탐험해요. 준비됐나요?');
  await waitInput({choices:['준비됐어요!'],go:true,text:false});
  for(let k=0;k<LIST.length;k++){
    await runProblem(k);
  }
  await showResult();
}

/* ---------- 시작 화면 ---------- */
(function(){
  const chips=$('#chips');
  const sets=[{label:'전체 ('+P.length+'문항)',u:null}];
  [U1,U2,U3,U4,U5].forEach(function(u){
    sets.push({label:u+' ('+P.filter(function(p){return p.u===u;}).length+')',u:u});
  });
  let sel=0;
  sets.forEach(function(s,idx){
    const b=document.createElement('button');
    b.className='chip'+(idx===0?' on':'');
    b.textContent=s.label;
    b.onclick=function(){
      sel=idx;
      chips.querySelectorAll('.chip').forEach(function(c,j){c.classList.toggle('on',j===idx);});
    };
    chips.appendChild(b);
  });
  $('#go').onclick=function(){
    NAME=$('#nm').value.trim()||'친구';
    const u=sets[sel].u;
    LIST=P.map(function(p,i){return i;}).filter(function(i){return !u||P[i].u===u;});
    $('#start').remove();
    main();
  };
  $('#nm').addEventListener('keydown',function(e){
    if(e.key==='Enter'&&!e.isComposing){$('#go').click();}
  });
})();
</script>
</body>
</html>
