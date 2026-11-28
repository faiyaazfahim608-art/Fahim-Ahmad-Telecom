<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#087b4e">
<link rel="manifest" href="./manifest.json">
<link rel="apple-touch-icon" href="./icon-192.png">
<title>FN Telecom</title>

<style>
:root{--g:#087b4e;--d:#063d2b;--mint:#eaf7ef;--ink:#173629;--muted:#718078;--line:#e3eee7}
*{box-sizing:border-box}
body{margin:0;font-family:system-ui,Arial,sans-serif;background:#f3f7f4;color:var(--ink);padding-bottom:85px}
header{background:linear-gradient(120deg,#053b29,#087b4e);color:white;padding:23px 16px;text-align:center;border-radius:0 0 23px 23px}
header h1{margin:0;font-size:25px}
header p{margin:4px 0 0;color:#d6f3e2;font-size:13px}
#installBtn{display:none;background:white;color:#087b4e;margin-top:14px;font-weight:700}
#logoutBtn{margin-top:12px;background:#eaf7ef;color:#063d2b}
main{max-width:680px;margin:auto;padding:15px}
.card{background:white;padding:17px;border:1px solid var(--line);border-radius:17px;margin-bottom:14px;box-shadow:0 8px 24px #073d2810}
h2{font-size:17px;color:var(--d);margin:0 0 13px}
input,select,textarea{width:100%;padding:12px 13px;margin:6px 0;border:1px solid #dce8df;border-radius:11px;font:inherit;background:white;color:var(--ink)}
textarea{min-height:95px;resize:vertical}
button{border:0;padding:11px 15px;border-radius:11px;background:var(--g);color:white;font-weight:700;font:inherit;cursor:pointer}
button.secondary{background:#eaf5ee;color:var(--d)}
button.red{background:#c93636}
button.orange{background:#d97706}
button:disabled{opacity:.55}
.grid{display:grid;grid-template-columns:repeat(2,1fr);gap:9px}
.operator{padding:15px 6px;text-align:center;border:1px solid #d9eee0;border-radius:13px;background:var(--mint);font-weight:750;cursor:pointer}
.offer,.entry{padding:12px 2px;border-bottom:1px solid #edf2ee;font-size:14px;line-height:1.8}
.offer:last-child,.entry:last-child{border:0}
.offer strong{color:var(--g)}
.tag{display:inline-block;padding:3px 9px;border-radius:20px;background:var(--mint);color:var(--g);font-size:12px;font-weight:700}
.tag.processing{background:#fff3d8;color:#996000}
.tag.success{background:#e2f7e9;color:#087b4e}
.tag.cancel{background:#fde8e8;color:#b42323}
nav{position:fixed;bottom:0;left:0;width:100%;display:flex;gap:3px;background:#ffffffed;padding:8px 3px calc(8px + env(safe-area-inset-bottom));box-shadow:0 -5px 20px #0001;z-index:5}
nav button{flex:1;background:transparent;color:#365747;font-size:11px;padding:7px 2px}
.page{display:none}
.page.active{display:block}
.hint{font-size:12px;color:var(--muted)}
.hidden{display:none!important}
.payment-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin:15px 0}
.pay-option{border:2px solid #e5ece7;border-radius:14px;padding:15px 5px;text-align:center;background:white;cursor:pointer;color:var(--ink)}
.pay-option.selected{border-color:var(--g);background:var(--mint)}
.pay-logo{width:53px;height:43px;margin:auto auto 8px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-weight:900;font-size:16px;color:white}
.bkash{background:#d92770}
.nagad{background:#f07824}
.rocket{background:#8a2b91}
.receiver{background:#eaf7ef;padding:14px;border-radius:12px;margin:12px 0;line-height:1.9}
.receiver strong{font-size:20px;color:#087b4e}
.copy-btn{padding:7px 12px;font-size:12px}
.payment-note{background:#fff7e8;border:1px solid #f2dfb8;padding:12px;border-radius:11px;font-size:13px;line-height:1.7;margin:12px 0}

/* Google Login screen */
#authScreen{max-width:500px;margin:25px auto;padding:15px}
#authScreen .card{padding:22px}
#authScreen h2{font-size:20px}
#authMessage{line-height:1.7}
.google-btn{
width:100%;
margin-top:15px;
padding:14px;
background:white;
color:#333;
border:1px solid #ddd;
font-weight:700;
box-shadow:0 2px 6px #0001;
}
.google-btn:active{background:#f5f5f5}

/* Arabic Welcome Splash Screen */
#welcomeSplash{
position:fixed;
inset:0;
z-index:99999;
background:
radial-gradient(circle at center,#147d55 0%,#075238 48%,#032d20 100%);
display:flex;
align-items:center;
justify-content:center;
text-align:center;
color:#fff;
overflow:hidden;
opacity:1;
visibility:visible;
transition:opacity .8s ease,visibility .8s ease;
}

#welcomeSplash::before{
content:"";
position:absolute;
inset:18px;
border:2px solid rgba(231,197,111,.65);
border-radius:22px;
pointer-events:none;
}

#welcomeSplash::after{
content:"✦";
position:absolute;
top:12%;
color:#f4d68b;
font-size:42px;
text-shadow:0 0 20px #f4d68b;
animation:starGlow 1.8s ease-in-out infinite alternate;
}

#welcomeSplash.hide{
opacity:0;
visibility:hidden;
}

.welcomeContent{
position:relative;
z-index:2;
padding:25px 15px;
width:100%;
animation:welcomeIn 1.1s ease;
}

.welcomeLine{
font-family:"Traditional Arabic","Noto Naskh Arabic",serif;
font-size:clamp(39px,10vw,65px);
font-weight:900;
line-height:1.9;
color:#ffe7a6;
text-shadow:
0 3px 2px #553b12,
0 0 12px rgba(255,220,130,.55);
letter-spacing:1px;
}

.welcomeDivider{
width:120px;
height:3px;
margin:8px auto;
border-radius:10px;
background:linear-gradient(90deg,transparent,#f4d68b,transparent);
}

.welcomeSub{
color:#e4f8e9;
font-size:14px;
letter-spacing:3px;
margin-top:20px;
font-weight:600;
}

@keyframes welcomeIn{
from{opacity:0;transform:translateY(30px) scale(.88)}
to{opacity:1;transform:translateY(0) scale(1)}
}

@keyframes starGlow{
from{opacity:.5;transform:scale(.85) rotate(0deg)}
to{opacity:1;transform:scale(1.15) rotate(25deg)}
}
</style>
</head>

<body>

<!-- Arabic Welcome Splash -->
<div id="welcomeSplash">
  <div class="welcomeContent">
    <div class="welcomeLine" dir="rtl">السَّلَامُ عَلَيْكُمْ</div>
    <div class="welcomeDivider"></div>
    <div class="welcomeLine" dir="rtl">أَهْلًا وَسَهْلًا</div>
    <div class="welcomeLine" dir="rtl">مَرْحَبًا</div>
    <div class="welcomeSub">WELCOME TO FN TELECOM</div>
  </div>
</div>

<header>
<h1>🟢 FN Telecom</h1>
<p>আপনার বিশ্বস্ত টেলিকম সেবা</p>
<button id="installBtn" type="button">📲 অ্যাপ ইনস্টল করুন</button>
<br>
<button id="logoutBtn" class="hidden" type="button" onclick="logoutUser()">লগআউট</button>
</header>

<!-- Google Login / Registration -->
<section id="authScreen" class="hidden">
<div class="card">
<h2>🔐 FN Telecom অ্যাকাউন্ট</h2>
<p class="hint">Google অ্যাকাউন্ট দিয়ে লগইন অথবা নতুন অ্যাকাউন্ট তৈরি করুন।</p>

<button id="googleLoginBtn" class="google-btn" onclick="googleLogin()">
🌐 Google দিয়ে লগইন / রেজিস্ট্রেশন
</button>

<p id="authMessage" class="hint"></p>
</div>
</section>

<!-- Authenticated App -->
<div id="appShell" class="hidden">

<main>

<section id="home" class="page active">
<div class="card">
<h2>📱 মোবাইল নম্বর</h2>
<input id="mobile" type="tel" maxlength="11" placeholder="01XXXXXXXXX">
<h2 style="margin-top:13px">📡 অপারেটর নির্বাচন</h2>
<div class="grid">
<div class="operator" onclick="pickOperator('GP')">🟢 GP</div>
<div class="operator" onclick="pickOperator('Banglalink')">🟠 Banglalink</div>
<div class="operator" onclick="pickOperator('Robi')">🔴 Robi</div>
<div class="operator" onclick="pickOperator('Airtel')">🔴 Airtel</div>
<div class="operator" onclick="pickOperator('Teletalk')">🔵 Teletalk</div>
</div>
</div>

<div class="card">
<h2>🔥 জনপ্রিয় অফার</h2>
<div id="homeOffers">অফার লোড হচ্ছে...</div>
</div>

<div class="card">
<h2>📢 নোটিশ</h2>
<div id="notice">FN Telecom-এ আপনাকে স্বাগতম।</div>
</div>
</section>

<section id="offers" class="page">
<div class="card">
<h2>📦 সকল অফার</h2>
<select id="filter" onchange="renderOffers()">
<option value="all">সকল অপারেটর</option>
<option>GP</option>
<option>Banglalink</option>
<option>Robi</option>
<option>Airtel</option>
<option>Teletalk</option>
</select>
<div id="offerList"></div>
</div>
</section>

<section id="orders" class="page">
<div class="card">
<h2>📋 আমার অর্ডার ও পেমেন্টের অবস্থা</h2>
<div id="orderStatus">অর্ডার লোড হচ্ছে...</div>
</div>

<div id="paymentPanel" class="card hidden">
<h2>💳 পেমেন্ট মাধ্যম নির্বাচন করুন</h2>
<div id="selectedOfferInfo"></div>

<div class="payment-grid">
<div class="pay-option" onclick="selectPayment('bKash')">
<div class="pay-logo bkash">bKash</div>বিকাশ
</div>
<div class="pay-option" onclick="selectPayment('Nagad')">
<div class="pay-logo nagad">নগদ</div>নগদ
</div>
<div class="pay-option" onclick="selectPayment('Rocket')">
<div class="pay-logo rocket">Rocket</div>রকেট
</div>
</div>

<div id="paymentDetails" class="hidden">
<div class="receiver">
<div>Send Money করুন এই নম্বরে:</div>
<strong id="receiverNumber"></strong>
<button class="copy-btn secondary" onclick="copyReceiver()">নম্বর কপি</button>
<br>
পেমেন্টের পরিমাণ: <strong id="paymentAmount"></strong>
</div>

<div class="payment-note">
⚠️ অনুগ্রহ করে নির্বাচিত মাধ্যমে উপরের নম্বরে ঠিক পরিমাণ টাকা Send Money করুন। তারপর নিচের তথ্য পূরণ করুন।
</div>

<input id="senderLast4" type="text" inputmode="numeric" maxlength="4" placeholder="টাকা পাঠানো নম্বরের শেষ ৪ সংখ্যা">
<button id="submitPayment" onclick="submitPayment()" style="width:100%">পেমেন্ট তথ্য জমা দিন</button>
</div>
</div>
</section>

<section id="contact" class="page">
<div class="card">
<h2>✉️ FN Telecom-এ মেসেজ পাঠান</h2>
<input id="customerName" placeholder="আপনার নাম">
<input id="customerPhone" type="tel" maxlength="11" placeholder="আপনার মোবাইল নম্বর">
<textarea id="customerMessage" maxlength="2000" placeholder="আপনার মেসেজ লিখুন..."></textarea>
<button onclick="sendCustomerMessage()">মেসেজ পাঠান</button>
<div id="sendStatus" class="hint"></div>
</div>

<div class="card">
<h2>💬 অ্যাডমিনের উত্তর</h2>
<div id="myReplies">আপনার পাঠানো মেসেজের উত্তর এখানে দেখা যাবে।</div>
</div>
</section>

<section id="admin" class="page">
<div class="card">
<h2>🔐 অ্যাডমিন প্যানেল</h2>

<div id="adminGate">
<p class="hint">অ্যাডমিন PIN দিন।</p>
<input id="adminPin" type="password" placeholder="Admin PIN">
<button onclick="unlockAdmin()">প্রবেশ করুন</button>
<p id="pinError" class="hint"></p>
</div>

<div id="adminArea" class="hidden">
<h2>📩 কাস্টমার মেসেজ</h2>
<div id="adminMessages">লোড হচ্ছে...</div>
<hr>

<h2>💳 পেমেন্টসহ কাস্টমার অর্ডার</h2>
<div id="adminOrders">লোড হচ্ছে...</div>
<hr>

<h2>➕ নতুন অফার যোগ করুন</h2>
<select id="newOperator">
<option>GP</option>
<option>Banglalink</option>
<option>Robi</option>
<option>Airtel</option>
<option>Teletalk</option>
</select>
<input id="newOfferName" placeholder="অফারের নাম">
<input id="newOfferPrice" type="number" min="1" placeholder="মূল্য (টাকা)">
<input id="newOfferValidity" placeholder="মেয়াদ">
<button onclick="addOffer()">অফার যোগ করুন</button>

<h2 style="margin-top:18px">📦 অফার পরিচালনা</h2>
<div id="adminOfferList"></div>

<h2 style="margin-top:18px">📢 নোটিশ পরিবর্তন</h2>
<input id="newNotice" placeholder="নতুন নোটিশ">
<button onclick="saveNotice()">নোটিশ প্রকাশ</button>
</div>
</div>
</section>

</main>

<nav>
<button onclick="showPage('home')">🏠<br>হোম</button>
<button onclick="showPage('offers')">📦<br>অফার</button>
<button onclick="showPage('orders')">📋<br>অর্ডার</button>
<button onclick="showPage('contact')">✉️<br>মেসেজ</button>
<button onclick="showPage('admin')">⚙️<br>Admin</button>
</nav>

</div>

<script type="module">
import {initializeApp} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-app.js";

import {
getAuth,
onAuthStateChanged,
GoogleAuthProvider,
signInWithPopup,
signOut,
setPersistence,
browserLocalPersistence
} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-auth.js";

import {
getFirestore,
collection,
addDoc,
query,
orderBy,
onSnapshot,
doc,
setDoc,
updateDoc,
where,
serverTimestamp
} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-firestore.js";

const firebaseConfig={
apiKey:"AIzaSyCxCr4NkVhnFi2cFRcvA9v8Djr1Df9_76Y",
authDomain:"fahim-ahmad-telecom.firebaseapp.com",
projectId:"fahim-ahmad-telecom",
storageBucket:"fahim-ahmad-telecom.firebasestorage.app",
messagingSenderId:"965841120853",
appId:"1:965841120853:web:7fc6a75769a0fdfbd0eedc",
measurementId:"G-N325EFWEXN"
};

const app=initializeApp(firebaseConfig);
const auth=getAuth(app);
const db=getFirestore(app);

const googleProvider=new GoogleAuthProvider();
googleProvider.setCustomParameters({prompt:"select_account"});

const $=id=>document.getElementById(id);

let uid=null;
let offers=[];
let adminUnlocked=false;
let pendingOffer=null;
let pendingPhone="";
let selectedPaymentMethod="";
let unsubs=[];
let appStarted=false;

const ADMIN_PIN="FN2026";

const paymentNumbers={
bKash:"01327335497",
Nagad:"01640592773",
Rocket:"01327335497"
};

const esc=v=>String(v??"").replace(/[&<>"']/g,c=>({
"&":"&amp;",
"<":"&lt;",
">":"&gt;",
'"':"&quot;",
"'":"&#39;"
}[c]));

const money=v=>Number(v||0).toFixed(2);

function watch(ref,cb){
const unsub=onSnapshot(ref,cb,e=>{
console.error(e);
alert("Firebase সমস্যা: "+e.message);
});
unsubs.push(unsub);
}

function statusLabel(status){
const labels={
Pending:"অপেক্ষমাণ",
Processing:"প্রসেসিং হচ্ছে",
Successful:"সম্পন্ন",
Cancelled:"বাতিল"
};
return labels[status]||status||"অপেক্ষমাণ";
}

function statusClass(status){
return status==="Successful"?"success":
status==="Cancelled"?"cancel":
status==="Processing"?"processing":"";
}

/* Google Login and Registration */

window.googleLogin=async()=>{

const btn=$("googleLoginBtn");
const message=$("authMessage");

btn.disabled=true;
btn.innerText="Google দিয়ে প্রবেশ করা হচ্ছে...";
message.innerText="";

try{

const result=await signInWithPopup(auth,googleProvider);
const user=result.user;

await setDoc(doc(db,"users",user.uid),{
name:user.displayName||"",
email:user.email||"",
photoURL:user.photoURL||"",
lastLogin:serverTimestamp()
},{merge:true});

message.innerText="লগইন সফল হয়েছে।";

}catch(e){

console.error(e);

let errorText=e.message;

if(e.code==="auth/popup-closed-by-user"){
errorText="লগইন সম্পন্ন হওয়ার আগেই উইন্ডো বন্ধ হয়েছে। আবার চেষ্টা করুন।";
}else if(e.code==="auth/unauthorized-domain"){
errorText="Firebase Authentication-এ আপনার ওয়েবসাইটের ডোমেইন অনুমোদন করতে হবে।";
}else if(e.code==="auth/popup-blocked"){
errorText="ব্রাউজার পপআপ বন্ধ করেছে। পপআপ অনুমোদন করে আবার চেষ্টা করুন।";
}

message.innerText="Google লগইন করা যায়নি: "+errorText;

btn.disabled=false;
btn.innerText="🌐 Google দিয়ে লগইন / রেজিস্ট্রেশন";

}

};

window.logoutUser=async()=>{

if(!confirm("আপনি কি লগআউট করতে চান?"))return;

try{
await signOut(auth);
location.reload();
}catch(e){
alert("লগআউট করা যায়নি: "+e.message);
}

};

/* Authentication state */

await setPersistence(auth,browserLocalPersistence);

onAuthStateChanged(auth,user=>{

const isGoogleUser=!!user &&
!user.isAnonymous &&
user.providerData.some(p=>p.providerId==="google.com");

if(isGoogleUser){

uid=user.uid;

$("authScreen").classList.add("hidden");
$("appShell").classList.remove("hidden");
$("logoutBtn").classList.remove("hidden");

if(!appStarted){
appStarted=true;
startApp();
}

}else{

uid=null;

$("appShell").classList.add("hidden");
$("authScreen").classList.remove("hidden");
$("logoutBtn").classList.add("hidden");

appStarted=false;

unsubs.forEach(unsub=>unsub());
unsubs=[];

}

});

/* App data */

function startApp(){

watch(collection(db,"offers"),s=>{
offers=s.docs.map(d=>({id:d.id,...d.data()}));
renderOffers();
renderHomeOffers();
renderAdminOffers();
});

watch(doc(db,"settings","notice"),s=>{
$("notice").innerText=s.exists()?s.data().text:"FN Telecom-এ আপনাকে স্বাগতম।";
});

watch(query(collection(db,"orders"),where("sessionId","==",uid)),s=>{
const myOrders=s.docs.map(d=>({id:d.id,...d.data()}));

myOrders.sort((a,b)=>(b.createdAt?.seconds||0)-(a.createdAt?.seconds||0));

$("orderStatus").innerHTML=myOrders.map(x=>`
<div class="entry">
<b>📦 ${esc(x.offer)}</b>
<span class="tag ${statusClass(x.status)}">${esc(statusLabel(x.status))}</span>
<br><span class="hint">অর্ডার আইডি: ${esc(x.id)}</span>
<br>মোবাইল নম্বর: ${esc(x.phone)}
<br>অপারেটর: ${esc(x.operator)}
<br>মূল্য: ৳${money(x.price)}
<br>পেমেন্ট মাধ্যম: ${esc(x.paymentMethod||"-")}
<br>পেমেন্ট নম্বরের শেষ ৪ সংখ্যা: ${esc(x.senderLast4||"-")}
<br>পেমেন্ট যাচাই: ${esc(x.paymentStatus||"যাচাই অপেক্ষমাণ")}
</div>
`).join("")||"এখনো কোনো অর্ডার করা হয়নি।";
});

watch(query(collection(db,"messages"),orderBy("createdAt","desc")),s=>{
const mine=s.docs.filter(d=>d.data().sessionId===uid);

$("myReplies").innerHTML=mine.map(d=>{
const x=d.data();

return `
<div class="entry">
<b>আপনার মেসেজ:</b> ${esc(x.message)}
<br><span class="tag">${esc(x.status||"পাঠানো হয়েছে")}</span>
${x.reply?`<br><b>অ্যাডমিনের উত্তর:</b> ${esc(x.reply)}`:"<br><span class='hint'>উত্তরের অপেক্ষায়...</span>"}
</div>`;
}).join("")||"এখনো কোনো মেসেজ পাঠাননি।";
});

}

window.showPage=id=>{
document.querySelectorAll("#appShell .page").forEach(p=>p.classList.remove("active"));
$(id).classList.add("active");
};

window.pickOperator=op=>{
$("filter").value=op;
showPage("offers");
renderOffers();
};

function offerCard(o){
return `
<div class="offer">
<strong>${esc(o.name)}</strong>
<br>অপারেটর: ${esc(o.operator)}
<br>মেয়াদ: ${esc(o.validity)}
<br>মূল্য: ৳${money(o.price)}
<br><button onclick="placeOrder('${o.id}')">এই অফার অর্ডার করুন</button>
</div>`;
}

window.renderOffers=()=>{
const f=$("filter").value;

$("offerList").innerHTML=offers
.filter(o=>o.active!==false&&(f==="all"||o.operator===f))
.map(offerCard).join("")||"কোনো অফার নেই।";
};

function renderHomeOffers(){
$("homeOffers").innerHTML=offers
.filter(o=>o.active!==false)
.slice(0,3)
.map(offerCard).join("")||"এখনো কোনো অফার যোগ করা হয়নি।";
}

window.placeOrder=id=>{
const o=offers.find(x=>x.id===id&&x.active!==false);
const phone=$("mobile").value.trim();

if(!o){
alert("এই অফারটি বর্তমানে চালু নেই।");
return;
}

if(!/^01[3-9]\d{8}$/.test(phone)){
alert("সঠিক ১১ ডিজিটের মোবাইল নম্বর লিখুন।");
showPage("home");
return;
}

pendingOffer=o;
pendingPhone=phone;
selectedPaymentMethod="";

$("paymentPanel").classList.remove("hidden");
$("paymentDetails").classList.add("hidden");

$("selectedOfferInfo").innerHTML=`
<p><b>অফার:</b> ${esc(o.name)}</p>
<p><b>অপারেটর:</b> ${esc(o.operator)}</p>
<p><b>মোবাইল নম্বর:</b> ${esc(phone)}</p>
<p><b>মোট মূল্য:</b> ৳${money(o.price)}</p>`;

document.querySelectorAll(".pay-option").forEach(x=>x.classList.remove("selected"));

showPage("orders");
};

window.selectPayment=method=>{
if(!pendingOffer)return;

selectedPaymentMethod=method;

document.querySelectorAll(".pay-option").forEach(x=>x.classList.remove("selected"));

const index={bKash:0,Nagad:1,Rocket:2}[method];

document.querySelectorAll(".pay-option")[index].classList.add("selected");

$("receiverNumber").innerText=paymentNumbers[method];
$("paymentAmount").innerText="৳"+money(pendingOffer.price);

$("paymentDetails").classList.remove("hidden");
};

window.copyReceiver=async()=>{
try{
await navigator.clipboard.writeText(paymentNumbers[selectedPaymentMethod]);
alert("পেমেন্ট নম্বর কপি হয়েছে।");
}catch(e){
alert("নম্বরটি হাতে কপি করুন: "+paymentNumbers[selectedPaymentMethod]);
}
};

window.submitPayment=async()=>{

if(!pendingOffer||!selectedPaymentMethod)return;

const last4=$("senderLast4").value.trim();

if(!/^\d{4}$/.test(last4)){
alert("টাকা পাঠানো মোবাইল নম্বরের শেষ ৪টি সংখ্যা লিখুন।");
return;
}

const btn=$("submitPayment");
btn.disabled=true;
btn.innerText="জমা হচ্ছে...";

try{

await addDoc(collection(db,"orders"),{
sessionId:uid,
phone:pendingPhone,
offer:pendingOffer.name,
operator:pendingOffer.operator,
price:Number(pendingOffer.price),
paymentMethod:selectedPaymentMethod,
receiverNumber:paymentNumbers[selectedPaymentMethod],
senderLast4:last4,
paymentStatus:"Verification Pending",
status:"Pending",
createdAt:serverTimestamp()
});

$("paymentPanel").classList.add("hidden");
$("senderLast4").value="";

pendingOffer=null;
selectedPaymentMethod="";

btn.disabled=false;
btn.innerText="পেমেন্ট তথ্য জমা দিন";

alert("আপনার অর্ডার জমা হয়েছে। অর্ডারের অবস্থা এই পেজে স্বয়ংক্রিয়ভাবে দেখা যাবে।");

}catch(e){

alert("অর্ডার জমা হয়নি: "+e.message);

btn.disabled=false;
btn.innerText="পেমেন্ট তথ্য জমা দিন";

}
};

window.sendCustomerMessage=async()=>{

const name=$("customerName").value.trim();
const phone=$("customerPhone").value.trim();
const message=$("customerMessage").value.trim();

if(!name||!/^01[3-9]\d{8}$/.test(phone)||message.length<2){
$("sendStatus").innerText="নাম, সঠিক নম্বর ও মেসেজ লিখুন।";
return;
}

try{

await addDoc(collection(db,"messages"),{
sessionId:uid,
name,
phone,
message,
status:"নতুন",
reply:"",
createdAt:serverTimestamp()
});

$("customerMessage").value="";
$("sendStatus").innerText="আপনার মেসেজ পাঠানো হয়েছে।";

}catch(e){
$("sendStatus").innerText="মেসেজ পাঠানো যায়নি: "+e.message;
}
};

window.unlockAdmin=()=>{
if($("adminPin").value!==ADMIN_PIN){
$("pinError").innerText="PIN সঠিক নয়।";
return;
}

adminUnlocked=true;

$("adminGate").classList.add("hidden");
$("adminArea").classList.remove("hidden");

loadAdmin();
renderAdminOffers();
};

function loadAdmin(){

watch(query(collection(db,"messages"),orderBy("createdAt","desc")),s=>{

$("adminMessages").innerHTML=s.docs.map(d=>{
const x=d.data();

return `
<div class="entry">
<b>${esc(x.name)}</b> · ${esc(x.phone)}
<br>${esc(x.message)}
<br><span class="tag">${esc(x.status||"নতুন")}</span>
${x.reply?`<br><b>আগের উত্তর:</b> ${esc(x.reply)}`:""}
<textarea id="reply_${d.id}" placeholder="কাস্টমারকে উত্তর লিখুন">${esc(x.reply||"")}</textarea>
<button onclick="replyMessage('${d.id}')">উত্তর পাঠান</button>
</div>`;
}).join("")||"কোনো মেসেজ নেই।";

});

watch(query(collection(db,"orders"),orderBy("createdAt","desc")),s=>{

$("adminOrders").innerHTML=s.docs.map(d=>{
const x=d.data();

return `
<div class="entry">
<b>📦 ${esc(x.offer)}</b>
<br>অর্ডার আইডি: ${esc(d.id)}
<br>কাস্টমারের নম্বর: ${esc(x.phone)}
<br>অপারেটর: ${esc(x.operator)}
<br>অফারের মূল্য: ৳${money(x.price)}

<hr>
<b>💳 পেমেন্ট তথ্য</b>
<br>মাধ্যম: ${esc(x.paymentMethod||"পুরোনো অর্ডার")}
<br>পেমেন্ট নম্বরের শেষ ৪ সংখ্যা: <b>${esc(x.senderLast4||"-")}</b>
<br>যে নম্বরে পাঠিয়েছে: ${esc(x.receiverNumber||"-")}
<br>পেমেন্ট যাচাই: ${esc(x.paymentStatus||"-")}
<br>অর্ডারের অবস্থা:
<span class="tag ${statusClass(x.status)}">${esc(statusLabel(x.status))}</span>
<br><br>

<button class="orange" onclick="setOrderStatus('${d.id}','Processing')">⏳ প্রসেসিং</button>
<button onclick="setOrderStatus('${d.id}','Successful')">✅ টাকা যাচাই করে MB পাঠানো হয়েছে</button>
<button class="red" onclick="setOrderStatus('${d.id}','Cancelled')">❌ বাতিল</button>
</div>`;
}).join("")||"কোনো অর্ডার নেই।";

});

}

window.replyMessage=async id=>{

if(!adminUnlocked)return;

const reply=$("reply_"+id).value.trim();

if(!reply)return alert("উত্তর লিখুন।");

try{
await updateDoc(doc(db,"messages",id),{
reply,
status:"উত্তর দেওয়া হয়েছে",
repliedAt:serverTimestamp()
});

alert("উত্তর পাঠানো হয়েছে।");

}catch(e){
alert(e.message);
}

};

window.setOrderStatus=async(id,status)=>{

if(!adminUnlocked)return;

if(status==="Successful"&&!confirm("পেমেন্টের টাকা যাচাই করে MB পাঠানো হয়েছে কি?"))return;

if(status==="Cancelled"&&!confirm("এই অর্ডার বাতিল করবেন?"))return;

try{

const changes={
status,
updatedAt:serverTimestamp()
};

if(status==="Successful"){
changes.paymentStatus="Verified";
changes.completedAt=serverTimestamp();
}

if(status==="Cancelled"){
changes.cancelledAt=serverTimestamp();
}

await updateDoc(doc(db,"orders",id),changes);

alert("অর্ডারের অবস্থা আপডেট হয়েছে।");

}catch(e){
alert(e.message);
}

};

window.addOffer=async()=>{

if(!adminUnlocked)return;

const name=$("newOfferName").value.trim();
const price=Number($("newOfferPrice").value);
const validity=$("newOfferValidity").value.trim();
const operator=$("newOperator").value;

if(!name||price<=0||!validity)return alert("সব তথ্য পূরণ করুন।");

try{

await addDoc(collection(db,"offers"),{
name,
price,
validity,
operator,
active:true,
createdAt:serverTimestamp()
});

$("newOfferName").value="";
$("newOfferPrice").value="";
$("newOfferValidity").value="";

alert("অফার যোগ হয়েছে।");

}catch(e){
alert(e.message);
}

};

function renderAdminOffers(){

if(!adminUnlocked)return;

$("adminOfferList").innerHTML=offers.map(o=>`

<div class="entry">
<b>${esc(o.name)}</b> · ${esc(o.operator)} · ৳${money(o.price)}
<br>মেয়াদ: ${esc(o.validity)}
<br><span class="tag ${o.active===false?"cancel":"success"}">
${o.active===false?"বাতিল / বন্ধ":"চালু আছে"}
</span>
<br><br>

${o.active===false
?`<button onclick="restoreOffer('${o.id}')">♻️ আবার চালু করুন</button>`
:`<button class="red" onclick="removeOffer('${o.id}')">অফার বাতিল করুন</button>`}
</div>

`).join("")||"কোনো অফার নেই।";

}

window.removeOffer=async id=>{

if(!adminUnlocked||!confirm("এই অফারটি গ্রাহকদের তালিকা থেকে বন্ধ করবেন?"))return;

try{
await updateDoc(doc(db,"offers",id),{
active:false,
updatedAt:serverTimestamp()
});

alert("অফারটি বাতিল করা হয়েছে।");

}catch(e){
alert("অফার বন্ধ করা যায়নি: "+e.message);
}

};

window.restoreOffer=async id=>{

if(!adminUnlocked||!confirm("অফারটি আবার চালু করবেন?"))return;

try{
await updateDoc(doc(db,"offers",id),{
active:true,
updatedAt:serverTimestamp()
});

alert("অফারটি আবার চালু হয়েছে।");

}catch(e){
alert("অফার চালু করা যায়নি: "+e.message);
}

};

window.saveNotice=async()=>{

if(!adminUnlocked)return;

const text=$("newNotice").value.trim();

if(!text)return alert("নোটিশ লিখুন।");

try{

await setDoc(doc(db,"settings","notice"),{
text,
updatedAt:serverTimestamp()
});

alert("নোটিশ প্রকাশ হয়েছে।");

}catch(e){
alert(e.message);
}

};

/* PWA: Service Worker registration */

if("serviceWorker" in navigator){
window.addEventListener("load",()=>{
navigator.serviceWorker.register("./service-worker.js")
.catch(error=>console.error("Service Worker registration failed:",error));
});
}

/* PWA: Install prompt */

let deferredPrompt=null;
const installBtn=document.getElementById("installBtn");

window.addEventListener("beforeinstallprompt",event=>{
event.preventDefault();
deferredPrompt=event;

if(installBtn){
installBtn.style.display="inline-block";
}
});

if(installBtn){

installBtn.addEventListener("click",async()=>{

if(!deferredPrompt)return;

deferredPrompt.prompt();
await deferredPrompt.userChoice;

deferredPrompt=null;
installBtn.style.display="none";

});

}

window.addEventListener("appinstalled",()=>{
if(installBtn){
installBtn.style.display="none";
}
});

/* Arabic Welcome Splash: hide after 3 seconds */

const showWelcomeSplash=()=>{
setTimeout(()=>{
const splash=document.getElementById("welcomeSplash");

if(splash){
splash.classList.add("hide");
setTimeout(()=>splash.remove(),850);
}
},3000);
};

if(document.readyState==="complete"){
showWelcomeSplash();
}else{
window.addEventListener("load",showWelcomeSplash,{once:true});
}

</script>
</body>
</html>
