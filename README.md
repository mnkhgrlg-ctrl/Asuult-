# Asuult-
<!DOCTYPE html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<title>For You ❤️</title>

<style>
*{box-sizing:border-box}
body{
margin:0;
height:100vh;
overflow:hidden;
font-family:-apple-system, BlinkMacSystemFont, sans-serif;
background:radial-gradient(circle at top,#1a0033,#000);
color:white;
}

/* ===== STAR FIELD ===== */
.star{
position:fixed;
width:2px;
height:2px;
background:white;
border-radius:50%;
animation:twinkle linear infinite;
}
@keyframes twinkle{
50%{opacity:.2}
}

/* ===== CENTER ===== */
.center{
position:absolute;
inset:0;
display:flex;
justify-content:center;
align-items:center;
flex-direction:column;
text-align:center;
}

/* ===== GLASS PANEL ===== */
.glass{
background:rgba(255,255,255,.08);
backdrop-filter:blur(12px);
padding:30px 40px;
border-radius:18px;
box-shadow:0 0 40px rgba(255,0,150,.25);
}

/* ===== LOCK ===== */
#lock{
display:flex;
flex-direction:column;
gap:15px;
align-items:center;
animation:fadeIn 1.5s;
}
#lock input{
padding:12px;
font-size:20px;
border:none;
border-radius:10px;
outline:none;
text-align:center;
background:#00000080;
color:white;
letter-spacing:6px;
width:160px;
}
#lock button{
padding:10px 26px;
border:none;
border-radius:12px;
font-size:16px;
cursor:pointer;
background:linear-gradient(45deg,#ff0055,#ff5cab);
color:white;
box-shadow:0 0 20px #ff3b7f;
transition:.3s;
}
#lock button:hover{
transform:scale(1.05);
}

/* ===== GIFT ===== */
#gift{
display:none;
width:190px;
height:130px;
background:#c8002d;
border-radius:14px;
position:relative;
cursor:pointer;
box-shadow:0 25px 60px rgba(255,0,80,.7);
animation:float 2.5s infinite ease-in-out, glow 2s infinite alternate;
}
#gift:before{
content:"";
position:absolute;
width:36px;
height:130px;
background:#ffd1dc;
left:77px;
}
#gift:after{
content:"";
position:absolute;
width:190px;
height:36px;
background:#ffd1dc;
top:47px;
}
#lid{
width:210px;
height:46px;
background:#ff0033;
position:absolute;
top:-46px;
left:-10px;
border-radius:12px;
transition:1s cubic-bezier(.19,1,.22,1);
}

/* ===== MESSAGE ===== */
#msg{
display:none;
font-size:36px;
font-weight:800;
text-shadow:0 0 40px pink;
animation:zoom 1.5s ease;
}

/* ===== PHOTOS ===== */
.photos{
display:flex;
gap:14px;
justify-content:center;
margin-bottom:20px;
}

.photos img{
width:130px;
height:170px;
object-fit:cover;
border-radius:16px;
box-shadow:0 0 25px rgba(255,100,150,.8);
border:2px solid rgba(255,255,255,.4);
animation:float 3s infinite ease-in-out;
}

/* ===== EFFECTS ===== */
@keyframes float{
50%{transform:translateY(-14px)}
}
@keyframes glow{
from{box-shadow:0 0 30px #ff004c}
to{box-shadow:0 0 70px #ff6aa2}
}
@keyframes fadeIn{
from{opacity:0;transform:translateY(20px)}
to{opacity:1}
}
@keyframes zoom{
from{opacity:0;transform:scale(.4)}
to{opacity:1;transform:scale(1)}
}

/* ===== HEART PARTICLES ===== */
.boom{
position:fixed;
font-size:28px;
pointer-events:none;
animation:blast 3s ease-out forwards;
}
@keyframes blast{
to{
transform:translate(
calc(-300px + 600px * var(--x)),
calc(-300px + 600px * var(--y))
) scale(.2);
opacity:0;
}
}

/* ===== MOBILE ===== */
@media(max-width:600px){
#msg{font-size:26px}
.photos img{
width:110px;
height:150px;
}
}
</style>
</head>

<body>

<div class="center">

<!-- LOCK -->
<div id="lock" class="glass">
<div style="font-size:22px">🔐 Зүрхний код оруул</div>
<input id="code" placeholder="****">
<button onclick="unlock()">Нээх ❤️</button>
</div>

<!-- GIFT -->
<div id="gift">
<div id="lid"></div>
</div>

<!-- MESSAGE -->
<div id="msg">

<div class="photos">
<img src="B8E9F02C-A196-408E-9A59-4C21EE737186.jpeg">
<img src="photo2.jpg">
</div>

<span id="type"></span><br><br>
❤️ Forever Yours ❤️

</div>

</div>

<audio id="boom" src="boom.mp3"></audio>
<audio id="music" src="music.mp3" loop></audio>

<script>

/* ===== STAR GENERATOR ===== */
for(let i=0;i<160;i++){
const s=document.createElement("div");
s.className="star";
s.style.left=Math.random()*100+"vw";
s.style.top=Math.random()*100+"vh";
s.style.animationDuration=2+Math.random()*4+"s";
document.body.appendChild(s);
}

/* ===== PASSWORD ===== */
function unlock(){
if(code.value==="0901"){
lock.style.display="none";
gift.style.display="block";
}else{
navigator.vibrate(200);
alert("💔 Буруу код");
}
}

/* ===== GIFT OPEN ===== */
let opened=false;

gift.onclick=()=>{
if(opened) return;
opened=true;

boom.play();
music.volume=.6;
music.play();

lid.style.transform="rotateX(160deg) translateY(-90px)";
gift.style.display="none";

setTimeout(()=>{
msg.style.display="block";
typing();
},800);

for(let i=0;i<70;i++){
explode("❤️");
explode("✨");
}
};

/* ===== PARTICLES ===== */
function explode(t){
const e=document.createElement("div");
e.className="boom";
e.innerHTML=t;
e.style.left=innerWidth/2+"px";
e.style.top=innerHeight/2+"px";
e.style.setProperty("--x",Math.random());
e.style.setProperty("--y",Math.random());
document.body.appendChild(e);
setTimeout(()=>e.remove(),3000);
}

/* ===== TYPING EFFECT ===== */
const text="Suwdaa ❤️\nБи чамд хайртай надтай үерхээч?...";
let i=0;

function typing(){
if(i<text.length){
type.innerHTML+=text[i]=="\n"?"<br>":text[i];
i++;
setTimeout(typing,80);
}
}

</script>

</body>
</html>
