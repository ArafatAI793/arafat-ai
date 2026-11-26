<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#06111b">
<title>Arafat AI — Premium Dashboard</title>
<style>
:root{--bg:#050c14;--panel:#0b1925;--panel2:#102634;--text:#e9faff;--muted:#91aab6;--cyan:#00e5ff;--green:#00ffa3;--border:#17404d}
body.light{--bg:#edf5f8;--panel:#fff;--panel2:#e4f0f4;--text:#142d39;--muted:#617b87;--border:#c1d9e1}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--text);font-family:Arial,sans-serif;transition:background .2s,color .2s}
button,input,textarea{font:inherit}button{cursor:pointer}
.app{display:flex;min-height:100vh}
.sidebar{width:245px;background:var(--panel);border-right:1px solid var(--border);padding:20px 14px;flex-shrink:0}
.logo{font-size:23px;font-weight:900;color:var(--cyan);margin:8px 7px 30px;text-shadow:0 0 14px #00e5ff66}.logo span{color:var(--green)}
.nav-label{font-size:10px;letter-spacing:2px;color:var(--muted);margin:22px 10px 9px}
.nav button{display:block;width:100%;padding:12px;border:0;border-radius:9px;background:transparent;color:var(--muted);text-align:left;margin:3px 0}
.nav button:hover,.nav button.active{background:var(--panel2);color:var(--cyan)}
.main{flex:1;min-width:0}
.topbar{height:68px;background:var(--panel);border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;padding:0 22px;position:sticky;top:0;z-index:5}
.online{color:var(--green);font-size:12px}
.content{max-width:1200px;margin:auto;padding:22px}
.page{display:none}.page.active{display:block}
.welcome{padding:25px;border-radius:16px;background:linear-gradient(115deg,#063b49,#10213c);border:1px solid #087c8b;margin-bottom:18px}
.welcome h1{margin:0 0 9px;font-size:25px}.welcome p{color:#c1e8ee;margin:0}
.cards{display:grid;grid-template-columns:repeat(4,1fr);gap:13px;margin:17px 0}
.card,.panel{background:var(--panel);border:1px solid var(--border);border-radius:14px;padding:17px}
.card small,.muted{color:var(--muted)}.number{font-size:22px;color:var(--cyan);margin-top:9px}
h2.section-title{font-size:20px;margin:22px 0 14px}
.tool-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
.tool{background:var(--panel2);color:var(--text);border:1px solid var(--border);border-radius:12px;padding:17px;text-align:left}
.tool b{display:block;color:var(--cyan);margin-bottom:8px}.tool p{font-size:12px;color:var(--muted);margin:0}
button.primary{background:linear-gradient(120deg,#00d9bd,#087bff);color:#00151b;border:0;border-radius:9px;padding:11px 16px;font-weight:bold}
button.secondary{background:var(--panel2);color:var(--cyan);border:1px solid var(--border);border-radius:9px;padding:10px 13px}
input,textarea{width:100%;background:var(--bg);color:var(--text);border:1px solid var(--border);border-radius:9px;padding:12px;outline:none}
textarea{min-height:110px;resize:vertical}
.messages{height:350px;overflow-y:auto;padding:10px;background:var(--bg);border-radius:10px}
.msg{max-width:85%;padding:11px 13px;margin:9px 0;border-radius:12px;font-size:14px;line-height:1.5;white-space:pre-wrap;overflow-wrap:anywhere}
.msg.bot{background:var(--panel2);border-left:3px solid var(--cyan)}
.msg.user{background:#075044;color:white;margin-left:auto;border-right:3px solid var(--green)}
.chat-input{display:flex;gap:8px;margin-top:12px}.chat-input input{flex:1;min-width:0}
.row{display:flex;gap:9px;align-items:center;flex-wrap:wrap}
.note-item{padding:12px;background:var(--panel2);border-radius:9px;margin:9px 0;white-space:pre-wrap;overflow-wrap:anywhere}
.note-item button{float:right;margin-left:8px}
.avatar-wrap{height:300px;display:grid;place-items:center;position:relative;overflow:hidden;border-radius:14px;background:radial-gradient(ellipse,#073443,#07121d 68%)}
.ring{position:absolute;width:225px;height:225px;border:2px solid transparent;border-top-color:var(--cyan);border-bottom-color:var(--green);border-radius:50%;animation:rotate 35s linear infinite}
.ring.inner{width:190px;height:190px;animation-duration:48s;animation-direction:reverse}
@keyframes rotate{to{transform:rotate(360deg)}}
.avatar{width:112px;height:150px;position:relative;border-radius:48% 48% 42% 42%;background:radial-gradient(ellipse at 50% 30%,#d6a58c,#573b42 70%,#172735);border:2px solid #5cecff;box-shadow:0 0 22px #00cfff77;z-index:1}
.avatar:before{content:"";position:absolute;top:-8px;left:-8px;width:122px;height:76px;border-radius:60% 60% 25% 25%;background:linear-gradient(100deg,#10121d,#382b39,#090d18)}
.eyes{position:absolute;top:65px;left:22px;width:65px;display:flex;justify-content:space-between;z-index:2}
.eyes i{width:17px;height:5px;background:#b9ffff;border-radius:50%;box-shadow:0 0 8px #00eaff;animation:blink 9s infinite}
@keyframes blink{0%,46%,50%,100%{transform:scaleY(1)}48%{transform:scaleY(.1)}}
.smile{position:absolute;z-index:2;top:99px;left:42px;width:27px;height:10px;border-bottom:2px solid #ffb4c4;border-radius:50%}
.avatar-label{position:absolute;bottom:14px;color:var(--cyan);letter-spacing:4px;font-size:11px}
.history-item{padding:12px;border-bottom:1px solid var(--border);display:flex;justify-content:space-between;gap:10px}
.footer{text-align:center;color:var(--muted);font-size:11px;padding:24px}
.mobile-menu{display:none}
@media(max-width:850px){.sidebar{width:205px}.cards{grid-template-columns:repeat(2,1fr)}}
@media(max-width:600px){.app{display:block}.sidebar{display:none;width:100%;border:0}.sidebar.show{display:block}.mobile-menu{display:inline-block}.content{padding:13px}.topbar{padding:0 13px}.tool-grid{grid-template-columns:repeat(2,1fr)}.messages{height:310px}.welcome h1{font-size:21px}}
@media(prefers-reduced-motion:reduce){*,*::before,*::after{animation:none!important;transition:none!important}}
</style>
</head>
<body>
<div class="app">
<aside class="sidebar" id="sidebar">
 <div class="logo">ARAFAT <span>AI</span></div>
 <div class="nav-label">MAIN MENU</div>
 <div class="nav">
  <button class="active" data-page="home">⌂ Dashboard</button>
  <button data-page="chat">✦ AI Chat</button>
  <button data-page="avatar">◉ AI Avatar</button>
 </div>
 <div class="nav-label">WORKSPACE</div>
 <div class="nav">
  <button data-page="tools">⚙ AI Tools</button>
  <button data-page="notes">▤ My Notes</button>
  <button data-page="calculator">＋ Calculator</button>
  <button data-page="history">◷ Chat History</button>
 </div>
 <div class="nav-label">PREFERENCES</div>
 <div class="nav"><button data-page="settings">⚙ Settings</button></div>
 <div class="panel" style="margin-top:25px"><small>AI SYSTEM</small><p class="online">● DEMO MODE ONLINE</p></div>
</aside>

<section class="main">
<header class="topbar">
 <div class="row"><button class="secondary mobile-menu" id="menuBtn">☰</button><b id="pageTitle">Dashboard</b></div>
 <div class="row"><span class="online">● ONLINE</span><button class="secondary" id="themeBtn">☼ Theme</button></div>
</header>

<div class="content">
<section class="page active" id="home">
 <div class="welcome"><h1>Welcome to Arafat AI ✦</h1><p>Your Future. Your AI. — Beyond Intelligence.</p></div>
 <div class="cards">
  <div class="card"><small>AI SYSTEM</small><div class="number">ONLINE</div></div>
  <div class="card"><small>CHAT MODE</small><div class="number">DEMO</div></div>
  <div class="card"><small>FEATURES</small><div class="number">08</div></div>
  <div class="card"><small>VERSION</small><div class="number">1.0</div></div>
 </div>
 <h2 class="section-title">Quick Access</h2>
 <div class="tool-grid">
  <button class="tool" data-open="chat"><b>✦ AI Chat</b><p>চ্যাট শুরু করো</p></button>
  <button class="tool" data-open="notes"><b>▤ Notes</b><p>নিজের নোট রাখো</p></button>
  <button class="tool" data-open="tools"><b>⚙ AI Tools</b><p>টুল ব্যবহার করো</p></button>
 </div>
</section>

<section class="page" id="chat">
 <h2 class="section-title">✦ Arafat AI Chat</h2>
 <div class="panel">
  <div class="messages" id="messages"><div class="msg bot">আসসালামু আলাইকুম! আমি Arafat AI Demo। কী জানতে চাও?</div></div>
  <div class="chat-input">
   <input id="chatInput" placeholder="তোমার প্রশ্ন লেখো...">
   <button class="secondary" id="voiceBtn" title="Voice input">🎙</button>
   <button class="primary" id="sendBtn">Send</button>
  </div>
  <p class="muted" style="font-size:12px">Demo Mode: এখানে নমুনা উত্তর দেওয়া হয়; এটি এখনো আসল AI নয়।</p>
 </div>
</section>

<section class="page" id="avatar">
 <h2 class="section-title">◉ AI Avatar</h2>
 <div class="panel">
  <div class="avatar-wrap"><div class="ring"></div><div class="ring inner"></div><div class="avatar"><div class="eyes"><i></i><i></i></div><div class="smile"></div></div><div class="avatar-label">ARAFAT AI</div></div>
  <p class="muted" style="text-align:center">Calm Premium Avatar • Soft Motion</p>
 </div>
</section>

<section class="page" id="tools">
 <h2 class="section-title">⚙ AI Tools</h2>
 <div class="tool-grid">
  <div class="tool"><b>🎙 Voice Input</b><p>Chat-এ মাইক্রোফোন দিয়ে কথা লিখে পাঠাও।</p></div>
  <div class="tool"><b>🔊 Voice Output</b><p>উত্তর সাপোর্ট থাকলে পড়ে শোনাও।</p></div>
  <div class="tool"><b>🧮 Calculator</b><p>সাধারণ হিসাব করো।</p></div>
  <div class="tool"><b>📝 Notes</b><p>নোট লিখে ব্রাউজারে রাখো।</p></div>
  <div class="tool"><b>🌙 Theme</b><p>Dark ও Light Mode বদলাও।</p></div>
  <div class="tool"><b>💬 Chat History</b><p>এই ব্রাউজারে আগের কথোপকথন দেখো।</p></div>
 </div>
</section>

<section class="page" id="notes">
 <h2 class="section-title">▤ My Notes</h2>
 <div class="panel">
  <textarea id="noteInput" placeholder="তোমার নোট লেখো..."></textarea><br><br>
  <div class="row"><button class="primary" id="saveNoteBtn">Save Note</button><button class="secondary" id="clearNoteBtn">Clear</button></div>
 </div>
 <div class="panel"><h3>Saved Notes</h3><div id="noteList"></div></div>
</section>

<section class="page" id="calculator">
 <h2 class="section-title">＋ Calculator</h2>
 <div class="panel">
  <input id="calcInput" inputmode="decimal" placeholder="যেমন: (25*4)+10">
  <br><br><div class="row"><button class="primary" id="calcBtn">Calculate</button><button class="secondary" id="calcClearBtn">Clear</button></div>
  <h2 id="calcResult">Result: —</h2>
  <small class="muted">শুধু সাধারণ সংখ্যা ও + − × ÷ % এবং বন্ধনী ব্যবহার করো।</small>
 </div>
</section>

<section class="page" id="history">
 <h2 class="section-title">◷ Chat History</h2>
 <div class="panel"><div id="historyList"></div><button class="secondary" id="clearHistoryBtn">Clear History</button></div>
</section>

<section class="page" id="settings">
 <h2 class="section-title">⚙ Settings</h2>
 <div class="panel"><h3>Appearance</h3><button class="secondary" id="settingsThemeBtn">Change Theme</button></div>
 <div class="panel"><h3>Voice</h3><button class="secondary" id="testVoiceBtn">Test Voice</button></div>
 <div class="panel"><h3>About Arafat AI</h3><p>Version 1.0 • Premium Demo Dashboard</p><p class="muted">তোমার নিজস্ব AI Dashboard Project।</p></div>
</section>
</div>
<footer class="footer">ARAFAT AI © 2026 • BEYOND INTELLIGENCE</footer>
</section>
</div>

<script>
"use strict";

const titles={home:"Dashboard",chat:"AI Chat",avatar:"AI Avatar",tools:"AI Tools",notes:"My Notes",calculator:"Calculator",history:"Chat History",settings:"Settings"};
const $=id=>document.getElementById(id);
let chatHistory=load("arai_history",[]);

function load(key,fallback){
 try{const value=localStorage.getItem(key);return value===null?fallback:JSON.parse(value)}
 catch{return fallback}
}
function save(key,value){
 try{localStorage.setItem(key,JSON.stringify(value))}
 catch{alert("ব্রাউজারে সংরক্ষণ করা যায়নি।")}
}
function showPage(id){
 document.querySelectorAll(".page").forEach(p=>p.classList.toggle("active",p.id===id));
 document.querySelectorAll("[data-page]").forEach(b=>b.classList.toggle("active",b.dataset.page===id));
 $("pageTitle").textContent=titles[id]||"Arafat AI";
 $("sidebar").classList.remove("show");
 if(id==="notes")renderNotes();
 if(id==="history")renderHistory();
}
document.querySelectorAll("[data-page]").forEach(b=>b.addEventListener("click",()=>showPage(b.dataset.page)));
document.querySelectorAll("[data-open]").forEach(b=>b.addEventListener("click",()=>showPage(b.dataset.open)));
$("menuBtn").addEventListener("click",()=>$("sidebar").classList.toggle("show"));

function toggleTheme(){
 document.body.classList.toggle("light");
 try{localStorage.setItem("arai_theme",document.body.classList.contains("light")?"light":"dark")}catch{}
}
$("themeBtn").addEventListener("click",toggleTheme);
$("settingsThemeBtn").addEventListener("click",toggleTheme);
if(load("arai_theme","dark")==="light")document.body.classList.add("light");

function addMessage(text,type){
 const el=document.createElement("div");
 el.className="msg "+type;
 el.textContent=text;
 $("messages").appendChild(el);
 $("messages").scrollTop=$("messages").scrollHeight;
}
function demoAnswer(q){
 const s=q.toLowerCase();
 if(s.includes("হ্যালো")||s.includes("hello"))return "হ্যালো! আমি Arafat AI Demo। কীভাবে সাহায্য করতে পারি?";
 if(s.includes("তোমার নাম")||s.includes("নাম কি"))return "আমার নাম Arafat AI।";
 if(s.includes("কে বানিয়েছে")||s.includes("কে তৈরি"))return "এটি Arafat AI-এর একটি Demo Dashboard Project।";
 if(s.includes("কেমন আছ"))return "আমি প্রস্তুত আছি! তোমার প্রশ্ন লিখে পাঠাও।";
 if(s.includes("সময়")||s.includes("সময়"))return "তোমার ডিভাইসের ঘড়িতে বর্তমান সময় দেখতে পারো।";
 if(s.includes("ধন্যবাদ"))return "স্বাগতম! আর কিছু জানতে চাইলে লিখো।";
 return "তোমার প্রশ্নটি পেয়েছি: “"+q+"”। আমি এখন Demo Mode-এ আছি, তাই নির্ভরযোগ্য AI উত্তর দিতে হলে পরে একটি নিরাপদ AI Backend সংযুক্ত করতে হবে।";
}
function sendChat(){
 const input=$("chatInput"),q=input.value.trim();
 if(!q)return;
 input.value="";
 addMessage(q,"user");
 chatHistory.push({role:"user",text:q,time:new Date().toLocaleString()});
 addMessage("Arafat AI উত্তর তৈরি করছে...","bot");
 const placeholder=$("messages").lastElementChild;
 setTimeout(()=>{
  const answer=demoAnswer(q);
  placeholder.textContent=answer;
  chatHistory.push({role:"assistant",text:answer,time:new Date().toLocaleString()});
  save("arai_history",chatHistory);
 },500);
}
$("sendBtn").addEventListener("click",sendChat);
$("chatInput").addEventListener("keydown",e=>{if(e.key==="Enter")sendChat()});

function voiceInput(){
 const Recognition=window.SpeechRecognition||window.webkitSpeechRecognition;
 if(!Recognition){alert("এই ব্রাউজারে Voice Input নেই। Chrome-এ চেষ্টা করো।");return}
 const recognition=new Recognition();
 recognition.lang="bn-BD";
 recognition.onresult=e=>{$("chatInput").value=e.results[0][0].transcript;sendChat()};
 recognition.onerror=()=>alert("Voice Input কাজ করেনি। মাইক্রোফোনের অনুমতি পরীক্ষা করো।");
 recognition.start();
}
$("voiceBtn").addEventListener("click",voiceInput);

function speak(text){
 if(!("speechSynthesis" in window)){alert("Voice Output সাপোর্ট নেই।");return}
 speechSynthesis.cancel();
 const u=new SpeechSynthesisUtterance(text);u.lang="bn-BD";speechSynthesis.speak(u);
}
$("testVoiceBtn").addEventListener("click",()=>speak("আসসালামু আলাইকুম। আমি Arafat AI Demo।"));

function renderNotes(){
 const notes=load("arai_notes",[]);
 const list=$("noteList");list.replaceChildren();
 if(!notes.length){list.textContent="এখনো কোনো নোট নেই।";return}
 notes.forEach((note,index)=>{
  const item=document.createElement("div");item.className="note-item";
  const text=document.createElement("span");text.textContent=note;
  const del=document.createElement("button");del.className="secondary";del.textContent="Delete";
  del.addEventListener("click",()=>{const updated=load("arai_notes",[]);updated.splice(index,1);save("arai_notes",updated);renderNotes()});
  item.append(del,text);list.append(item);
 });
}
$("saveNoteBtn").addEventListener("click",()=>{
 const value=$("noteInput").value.trim();if(!value){alert("আগে একটি নোট লেখো।");return}
 const notes=load("arai_notes",[]);notes.unshift(value);save("arai_notes",notes);$("noteInput").value="";renderNotes();
});
$("clearNoteBtn").addEventListener("click",()=>$("noteInput").value="");

function calculate(){
 const expr=$("calcInput").value.trim();
 if(!expr){$("calcResult").textContent="Result: —";return}
 if(!/^[0-9+\-*/().%\s]+$/.test(expr)){ $("calcResult").textContent="শুধু সাধারণ গণিতের চিহ্ন ব্যবহার করো।";return}
 try{
  const result=Function('"use strict";return ('+expr+')')();
  if(typeof result!=="number"||!Number.isFinite(result))throw Error();
  $("calcResult").textContent="Result: "+result;
 }catch{$("calcResult").textContent="হিসাবটি সঠিক নয়।"}
}
$("calcBtn").addEventListener("click",calculate);
$("calcInput").addEventListener("keydown",e=>{if(e.key==="Enter")calculate()});
$("calcClearBtn").addEventListener("click",()=>{$("calcInput").value="";$("calcResult").textContent="Result: —"});

function renderHistory(){
 const list=$("historyList");list.replaceChildren();
 if(!chatHistory.length){list.textContent="এখনো কোনো Chat History নেই।";return}
 chatHistory.slice().reverse().forEach(item=>{
  const row=document.createElement("div");row.className="history-item";
  const content=document.createElement("div");
  const role=document.createElement("b");role.textContent=item.role==="user"?"তুমি":"Arafat AI";
  const message=document.createElement("p");message.textContent=item.text;
  const time=document.createElement("small");time.className="muted";time.textContent=item.time||"";
  content.append(role,message,time);row.append(content);list.append(row);
 });
}
$("clearHistoryBtn").addEventListener("click",()=>{
 if(confirm("সব Chat History মুছে ফেলবে?")){chatHistory=[];save("arai_history",chatHistory);renderHistory()}
});
renderNotes();
</script>
</body>
</html>
