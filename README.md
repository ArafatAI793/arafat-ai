

<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#090d1c">
<title>Arafat AI | Personal Assistant</title>

<style>
*{box-sizing:border-box}
:root{
 --bg:#080c19;
 --panel:#111a30;
 --panel2:#172441;
 --text:#f5f7ff;
 --muted:#91a2c5;
 --border:#293c63;
 --accent:#7957ff;
 --cyan:#18d5f5;
}
body{
 margin:0;background:
 radial-gradient(circle at 75% 10%,#25215b 0,transparent 35%),
 var(--bg);
 color:var(--text);
 font-family:Arial,sans-serif;
 min-height:100vh;
}
button,input{font:inherit}
button{cursor:pointer;color:inherit}
.layout{display:flex;min-height:100vh}
.sidebar{
 width:245px;background:#0d1426;
 border-right:1px solid var(--border);
 padding:22px 16px;
 display:flex;flex-direction:column;
}
.brand{display:flex;align-items:center;gap:11px;margin-bottom:30px}
.logo{
 width:43px;height:43px;border-radius:14px;
 display:grid;place-items:center;font-size:23px;
 background:linear-gradient(135deg,var(--cyan),var(--accent));
 box-shadow:0 0 22px #7957ff55;
}
.brand h2{font-size:19px;margin:0}
.brand small{color:var(--muted);font-size:11px}
.newchat,.navbtn{
 width:100%;padding:13px;border-radius:12px;
 border:1px solid var(--border);
 background:var(--panel);text-align:left;
 margin-bottom:12px;
}
.newchat{
 background:linear-gradient(120deg,#3156bd,#7746d8);
 border:0;text-align:center;
}
.section{font-size:11px;color:var(--muted);margin:20px 8px 10px}
.navbtn{background:transparent;border-color:transparent;color:#c8d5f1}
.navbtn:hover,.navbtn.active{background:var(--panel2);border-color:var(--border)}
.sidebar-bottom{margin-top:auto}
.profile{
 padding:12px;background:var(--panel);
 border:1px solid var(--border);border-radius:13px;
 display:flex;align-items:center;gap:10px;
}
.avatar{
 width:35px;height:35px;border-radius:50%;
 background:linear-gradient(135deg,#12c9ef,#8852ff);
 display:grid;place-items:center;
}
.profile small{color:var(--muted)}
.main{flex:1;min-width:0;padding:22px 30px}
.topbar{display:flex;justify-content:space-between;align-items:center}
.topbar h2{font-size:19px;margin:0}
.actions{display:flex;gap:9px}
.action{
 background:var(--panel);border:1px solid var(--border);
 border-radius:11px;padding:10px 13px;
}
.status{color:#53e8ae;font-size:12px}
.hero{text-align:center;margin:25px auto 20px}
.robot{
 width:112px;height:112px;margin:auto;
 border-radius:34px;
 display:grid;place-items:center;
 background:linear-gradient(145deg,#9b61ff,#14cafa);
 box-shadow:0 0 45px #7957ff55;
 animation:float 3s ease-in-out infinite;
}
.face{
 width:78px;height:59px;border-radius:23px;
 background:#10172d;
 display:flex;align-items:center;
 justify-content:center;gap:18px;
}
.eye{
 width:11px;height:17px;border-radius:50%;
 background:#36eaff;box-shadow:0 0 12px #36eaff;
}
@keyframes float{
 50%{transform:translateY(-9px)}
}
.hero h1{font-size:30px;margin:17px 0 7px}
.gradient{
 background:linear-gradient(90deg,#26d9ff,#a37aff);
 background-clip:text;color:transparent;
}
.hero p{color:var(--muted);font-size:14px}
.screen{
 max-width:850px;height:330px;
 overflow-y:auto;margin:20px auto;
 padding:18px;
 border:1px solid var(--border);
 border-radius:18px;background:#0c1324;
}
.msg{
 padding:12px 15px;border-radius:14px;
 margin:10px 0;max-width:85%;
 font-size:14px;line-height:1.7;
 white-space:pre-wrap;overflow-wrap:anywhere;
}
.bot{background:#1a2949;color:#e2ebff}
.user{background:#6044bd;margin-left:auto}
.quick{
 max-width:850px;margin:auto;
 display:flex;flex-wrap:wrap;gap:9px;
}
.quick button{
 background:var(--panel2);border:1px solid var(--border);
 border-radius:20px;padding:10px 13px;
 font-size:12px;color:#d5e2ff;
}
.input-area{max-width:850px;margin:18px auto}
.inputrow{
 display:flex;gap:9px;padding:8px;
 background:var(--panel);border:1px solid var(--border);
 border-radius:16px;
}
.inputrow input{
 flex:1;min-width:0;background:transparent;
 color:white;border:0;outline:0;padding:12px;
}
.send,.mic{
 border:0;border-radius:12px;padding:0 17px;
 background:linear-gradient(135deg,#16c9e9,#8151ff);
}
footer{text-align:center;color:#7185ad;font-size:11px;margin-top:20px}
.mobile-menu{display:none}
@media(max-width:700px){
 .sidebar{display:none}
 .main{padding:16px 12px}
 .mobile-menu{display:inline-block}
 .hero h1{font-size:25px}
 .screen{height:300px}
 .quick button{font-size:11px}
}
body.light{
 --bg:#edf2ff;--panel:#fff;--panel2:#e5eaff;
 --text:#17213c;--muted:#667596;--border:#cbd5ed;
}
body.light .sidebar{background:#e3eaff}
body.light .screen{background:#fff}
body.light .bot{background:#e5eaff;color:#17213c}
body.light .inputrow input{color:#17213c}
body.light .profile{background:white}
</style>
</head>

<body>
<div class="layout">

<aside class="sidebar">
 <div class="brand">
  <div class="logo">🤖</div>
  <div>
   <h2>Arafat AI</h2>
   <small>Personal AI Assistant</small>
  </div>
 </div>

 <button class="newchat" onclick="newChat()">＋ New Chat</button>

 <div class="section">WORKSPACE</div>
 <button class="navbtn active" onclick="showHome()">💬 AI Assistant</button>
 <button class="navbtn" onclick="showHistory()">🕘 Chat History</button>
 <button class="navbtn" onclick="toggleTheme()">🎨 Appearance</button>

 <div class="section">MORE</div>
 <button class="navbtn" onclick="showAbout()">✨ About Arafat AI</button>
 <button class="navbtn" onclick="showSettings()">⚙️ Settings</button>

 <div class="sidebar-bottom">
  <div class="profile">
   <div class="avatar">👤</div>
   <div>
    <b>Arafat</b><br>
    <small>Personal Workspace</small>
   </div>
  </div>
 </div>
</aside>

<main class="main">
 <div class="topbar">
  <div>
   <button class="action mobile-menu" onclick="alert('মোবাইল মেনু: New Chat, History, Settings')">☰</button>
   <h2 style="display:inline">AI Workspace</h2>
  </div>
  <div class="actions">
   <span class="status">● Online</span>
   <button class="action" onclick="toggleTheme()">☀️</button>
  </div>
 </div>

 <section class="hero">
  <div class="robot">
   <div class="face">
    <div class="eye"></div>
    <div class="eye"></div>
   </div>
  </div>
  <h1>Welcome to <span class="gradient">Arafat AI</span></h1>
  <p>হ্যালো! আমি তোমার Personal AI Assistant। কীভাবে সাহায্য করতে পারি?</p>
 </section>

 <div class="screen" id="screen">
  <div class="msg bot">
   আসসালামু আলাইকুম! ❤️
   আমি Arafat AI। আমাকে যেকোনো প্রশ্ন করতে পারো!
  </div>
 </div>

 <div class="quick">
  <button onclick="ask('তোমার নাম কী?')">🤖 তোমার নাম কী?</button>
  <button onclick="ask('তুমি কী করতে পারো?')">✨ তুমি কী পারো?</button>
  <button onclick="ask('একটি জোক বলো')">😂 একটি জোক বলো</button>
  <button onclick="ask('আমাকে একটি গল্প বলো')">📖 গল্প বলো</button>
 </div>

 <div class="input-area">
  <div class="inputrow">
   <input id="question" placeholder="Arafat AI-কে কিছু জিজ্ঞেস করো...">
   <button class="mic" onclick="voiceInput()" title="Voice Input">🎙️</button>
   <button class="send" onclick="send()">➤</button>
  </div>
  <footer>Made with ❤️ by Arafat | Arafat AI 2.0</footer>
 </div>
</main>
</div>

<script>
const screen=document.getElementById('screen');
const input=document.getElementById('question');

function add(text,type){
 const div=document.createElement('div');
 div.className='msg '+type;
 div.textContent=text;
 screen.appendChild(div);
 screen.scrollTop=screen.scrollHeight;
}

function ask(text){
 input.value=text;
 send();
}

function send(){
 const q=input.value.trim();
 if(!q)return;
 add(q,'user');
 input.value='';

 setTimeout(()=>{
  let answer='ধন্যবাদ! ❤️ তোমার কথাটি বুঝেছি।';
  const s=q.toLowerCase();

  if(s.includes('নাম'))
   answer='আমার নাম Arafat AI। আমি তোমার ব্যক্তিগত সহকারী! 🤖';
  else if(s.includes('পারো'))
   answer='আমি প্রশ্নের উত্তর, লেখা, আইডিয়া এবং বিভিন্ন কাজে সাহায্য করতে পারি।';
  else if(s.includes('জোক'))
   answer='শিক্ষক: বিদ্যুৎ কোথায় থাকে? ছাত্র: বিলের কাগজে! 😂';
  else if(s.includes('হাই')||s.includes('হ্যালো'))
   answer='হ্যালো! ❤️ কেমন আছো?';
  else if(s.includes('গল্প'))
   answer='এক ছিল ছোট্ট রোবট। সে প্রতিদিন নতুন কিছু শিখত। তার স্বপ্ন ছিল মানুষের কাজে সাহায্য করা। 🤖';
  else
   answer='তোমার প্রশ্ন পেয়েছি! আমি এখন Demo Mode-এ আছি। আসল AI উত্তর পেতে নিরাপদ Backend ও AI API সংযোগ করতে হবে।';

  add(answer,'bot');
 },400);
}

function newChat(){
 screen.innerHTML='';
 add('নতুন চ্যাট শুরু হয়েছে! ❤️ কী জানতে চাও?','bot');
}

function toggleTheme(){
 document.body.classList.toggle('light');
}

function showHome(){
 alert('তুমি AI Assistant পেজে আছো।');
}
function showHistory(){
 alert('Chat History ফিচারটি পরবর্তী সংস্করণে Backend-এর মাধ্যমে যুক্ত হবে।');
}
function showSettings(){
 alert('Arafat AI Settings পরবর্তী সংস্করণে যুক্ত হবে।');
}
function showAbout(){
 alert('Arafat AI — My Personal AI Assistant Website. Made with ❤️ by Arafat.');
}

function voiceInput(){
 const Speech=window.SpeechRecognition||window.webkitSpeechRecognition;
 if(!Speech){
  alert('তোমার ব্রাউজারে Voice Input সাপোর্ট নেই।');
  return;
 }
 const recognition=new Speech();
 recognition.lang='bn-BD';
 recognition.onresult=e=>{
  input.value=e.results[0][0].transcript;
 };
 recognition.start();
}

input.addEventListener('keydown',e=>{
 if(e.key==='Enter')send();
});
</script>
</body>
</html>
