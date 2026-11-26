<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Arafat AI - Ultra Advanced</title>
<style>
*{margin:0;padding:0;box-sizing:border-box}
body{background:#050510;color:#fff;font-family:Arial;overflow-x:hidden}
.led-bar{height:10px;background:linear-gradient(90deg,#ff0000,#ff7300,#fffb00,#00ff00,#00ffff,#0000ff,#ff00ff,#ff0000);background-size:400% 100%;animation:ledRun 2s linear infinite}
@keyframes ledRun{0%{background-position:0% 50%}100%{background-position:400% 50%}}
.header{text-align:center;padding:25px;background:#0b1020}
.header h1{font-size:38px;background:linear-gradient(90deg,#00ffff,#ff00ff,#00ff00);-webkit-background-clip:text;-webkit-text-fill-color:transparent}
.robot-wrap{display:flex;justify-content:center;margin:30px 0}
.robot{width:200px;height:240px;background:linear-gradient(180deg,#1f2937,#111827);border-radius:35px;position:relative;animation:float 3s ease-in-out infinite;box-shadow:0 0 50px #7c3aed}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-18px)}}
.head{width:130px;height:110px;background:#374151;border-radius:25px;margin:15px auto;position:relative}
.eye{width:20px;height:20px;background:#00ffff;border-radius:50%;position:absolute;top:38px;box-shadow:0 0 25px #00ffff,0 0 50px #00ffff;animation:blink 2s infinite}
.eye.left{left:28px}.eye.right{right:28px}
@keyframes blink{0%,90%,100%{transform:scaleY(1)}95%{transform:scaleY(0.1)}}
.mouth{width:55px;height:9px;background:#00ffff;border-radius:10px;position:absolute;bottom:22px;left:50%;transform:translateX(-50%);box-shadow:0 0 18px #00ffff}
.body{width:150px;height:90px;background:#374151;border-radius:18px;margin:10px auto;position:relative}
.led{width:14px;height:14px;border-radius:50%;position:absolute;animation:ledBlink .8s infinite}
.led1{background:#ff0000;top:18px;left:22px;box-shadow:0 0 18px #ff0000}
.led2{background:#00ff00;top:18px;left:50%;transform:translateX(-50%);box-shadow:0 0 18px #00ff00;animation-delay:.3s}
.led3{background:#0000ff;top:18px;right:22px;box-shadow:0 0 18px #0000ff;animation-delay:.6s}
@keyframes ledBlink{0%,100%{opacity:1}50%{opacity:.2}}
.arm{width:22px;height:80px;background:#374151;border-radius:12px;position:absolute;top:130px}
.arm.left{left:-28px;animation:wave 2s infinite}
.arm.right{right:-28px;animation:wave 2s infinite reverse}
@keyframes wave{0%,100%{transform:rotate(0)}50%{transform:rotate(25deg)}}
.container{max-width:900px;margin:20px auto;padding:20px}
.chat-box{background:#111827;padding:20px;border-radius:20px;border:2px solid #7c3aed;box-shadow:0 0 35px #7c3aed55}
.msg{padding:12px;border-radius:12px;margin:10px 0}
.ai{background:#1f2937;border-left:4px solid #00ffff}
.user{background:#7c3aed;margin-left:20%}
.input-box{display:flex;gap:10px;margin-top:15px}
input{flex:1;padding:15px;border-radius:12px;border:none;background:#1f2937;color:#fff}
button{padding:15px 25px;background:linear-gradient(90deg,#7c3aed,#00ffff);border:none;border-radius:12px;color:#fff;font-weight:bold;cursor:pointer}
.settings{background:#111827;padding:20px;border-radius:20px;margin-top:20px}
select{width:100%;padding:12px;margin:10px 0;border-radius:10px;background:#1f2937;color:#fff;border:none}
.future{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-top:20px}
.future button{background:#2563eb}
</style>
</head>
<body>
<div class="led-bar"></div>
<div class="header">
<h1>🤖 ARAFAT AI ULTRA</h1>
<p>রোবট + LED + ভয়েস + AI - সব একসাথে!</p>
</div>
<div class="robot-wrap">
<div class="robot">
<div class="arm left"></div><div class="arm right"></div>
<div class="head"><div class="eye left"></div><div class="eye right"></div><div class="mouth"></div></div>
<div class="body"><div class="led led1"></div><div class="led led2"></div><div class="led led3"></div></div>
</div>
</div>
<div class="container">
<div class="chat-box">
<div id="chat"><div class="msg ai">🤖 হ্যালো! আমি Arafat AI Ultra রোবট। আমার LED জ্বলছে, চোখ জ্বলছে! বলো, কি করতে চাও?</div></div>
<div class="input-box">
<input id="msgInput" placeholder="রোবটকে বলুন...">
<button onclick="send()">পাঠান</button>
<button onclick="startVoice()">🎤</button>
</div>
</div>
<div class="future">
<button onclick="alert('ইমেজ জেনারেট খুব শীঘ্রই আসছে!')">🖼️ ইমেজ</button>
<button onclick="speak()">🔊 রোবট কথা বলবে</button>
<button onclick="alert('ফাইল আপলোড চালু!')">📁 ফাইল</button>
</div>
<div class="settings">
<h2>⚙️ Advanced Settings</h2>
<label>থিম</label><select><option>Neon LED</option><option>Dark</option><option>Light</option></select>
<label>রোবট মুড</label><select><option>হাসিখুশি</option><option>গম্ভীর</option><option>গান গাইবে</option></select>
<label>LED স্পিড</label><select><option>ধীরে</option><option>মাঝারি</option><option>দ্রুত ⚡</option></select>
</div>
</div>
<div class="led-bar"></div>
<script>
function send(){
 let input=document.getElementById('msgInput');
 let text=input.value.trim();
 if(!text) return;
 let chat=document.getElementById('chat');
 chat.innerHTML+=`<div class="msg user">${text}</div>`;
 input.value="";
 setTimeout(()=>{
   let reply="🤖 রোবট বলছে: '"+text+"' - বুঝেছি! আমার LED আরও জোরে জ্বলছে! 🔥";
   chat.innerHTML+=`<div class="msg ai">${reply}</div>`;
   chat.scrollTop=chat.scrollHeight;
   speakText(reply);
 },800);
}
function startVoice(){
 if('webkitSpeechRecognition' in window){
   let rec=new webkitSpeechRecognition();
   rec.lang='bn-BD'; rec.start();
   rec.onresult=(e)=>{document.getElementById('msgInput').value=e.results[0][0].transcript; send();}
 } else alert('আপনার ব্রাউজার ভয়েস সাপোর্ট করে না');
}
function speakText(t){
 if('speechSynthesis' in window){
   let u=new SpeechSynthesisUtterance(t);
   u.lang='bn-BD'; speechSynthesis.speak(u);
 }
}
function speak(){speakText("হ্যালো, আমি Arafat AI Ultra রোবট, আমি এখন কথা বলছি!");}
</script>
</body>
</html>
