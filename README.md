<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#087b4e">
<title>FN Telecom</title>
<style>
:root{--g:#087b4e;--d:#063d2b;--mint:#eaf7ef;--ink:#173629;--muted:#718078;--line:#e3eee7}
*{box-sizing:border-box}body{margin:0;font-family:system-ui,Arial,sans-serif;background:#f3f7f4;color:var(--ink);padding-bottom:78px}
header{background:linear-gradient(120deg,#053b29,#087b4e);color:white;padding:23px 16px;text-align:center;border-radius:0 0 23px 23px}
header h1{margin:0;font-size:25px}header p{margin:4px 0 0;color:#d6f3e2;font-size:13px}
main{max-width:680px;margin:auto;padding:15px}.card{background:white;padding:17px;border:1px solid var(--line);border-radius:17px;margin-bottom:14px;box-shadow:0 8px 24px #073d2810}
h2{font-size:17px;color:var(--d);margin:0 0 13px}input,select,textarea{width:100%;padding:12px 13px;margin:6px 0;border:1px solid #dce8df;border-radius:11px;font:inherit;background:white;color:var(--ink)}
textarea{min-height:95px;resize:vertical}button{border:0;padding:11px 15px;border-radius:11px;background:var(--g);color:white;font-weight:700;font:inherit;cursor:pointer}button.secondary{background:#eaf5ee;color:var(--d)}button.red{background:#c93636}button:disabled{opacity:.55}
.grid{display:grid;grid-template-columns:repeat(2,1fr);gap:9px}.operator{padding:15px 6px;text-align:center;border:1px solid #d9eee0;border-radius:13px;background:var(--mint);font-weight:750;cursor:pointer}
.offer,.entry{padding:12px 2px;border-bottom:1px solid #edf2ee;font-size:14px;line-height:1.7}.offer:last-child,.entry:last-child{border:0}.offer strong{color:var(--g)}.tag{display:inline-block;padding:2px 8px;border-radius:20px;background:var(--mint);color:var(--g);font-size:12px;font-weight:700}
nav{position:fixed;bottom:0;left:0;width:100%;display:flex;gap:3px;background:#ffffffed;padding:8px 3px calc(8px + env(safe-area-inset-bottom));box-shadow:0 -5px 20px #0001;z-index:5}
nav button{flex:1;background:transparent;color:#365747;font-size:11px;padding:7px 2px}
.page{display:none}.page.active{display:block}.hint{font-size:12px;color:var(--muted)}.hidden{display:none!important}
</style>
</head>
<body>
<header><h1>🟢 FN Telecom</h1><p>আপনার বিশ্বস্ত টেলিকম সেবা</p></header>
<main>
<section id="home" class="page active">
 <div class="card"><h2>📱 মোবাইল নম্বর</h2><input id="mobile" type="tel" maxlength="11" placeholder="01XXXXXXXXX">
 <h2 style="margin-top:13px">📡 অপারেটর নির্বাচন</h2><div class="grid">
 <div class="operator" onclick="pickOperator('GP')">🟢 GP</div><div class="operator" onclick="pickOperator('Banglalink')">🟠 Banglalink</div>
 <div class="operator" onclick="pickOperator('Robi')">🔴 Robi</div><div class="operator" onclick="pickOperator('Airtel')">🔴 Airtel</div>
 <div class="operator" onclick="pickOperator('Teletalk')">🔵 Teletalk</div></div></div>
 <div class="card"><h2>🔥 জনপ্রিয় অফার</h2><div id="homeOffers">অফার লোড হচ্ছে...</div></div>
 <div class="card"><h2>📢 নোটিশ</h2><div id="notice">FN Telecom-এ আপনাকে স্বাগতম।</div></div>
</section>
<section id="offers" class="page"><div class="card"><h2>📦 সকল অফার</h2><select id="filter" onchange="renderOffers()"><option value="all">সকল অপারেটর</option><option>GP</option><option>Banglalink</option><option>Robi</option><option>Airtel</option><option>Teletalk</option></select><div id="offerList"></div></div></section>
<section id="orders" class="page"><div class="card"><h2>📋 অর্ডার করুন</h2><p class="hint">নম্বর লিখে অফার নির্বাচন করুন। আপনার অর্ডার অ্যাডমিন প্যানেলে দেখা যাবে।</p><div id="orderStatus"></div></div></section>
<section id="contact" class="page"><div class="card"><h2>✉️ FN Telecom-এ মেসেজ পাঠান</h2>
<input id="customerName" placeholder="আপনার নাম"><input id="customerPhone" type="tel" maxlength="11" placeholder="আপনার মোবাইল নম্বর">
<textarea id="customerMessage" maxlength="2000" placeholder="আপনার মেসেজ লিখুন..."></textarea>
<button onclick="sendCustomerMessage()">মেসেজ পাঠান</button><div id="sendStatus" class="hint"></div></div>
<div class="card"><h2>💬 অ্যাডমিনের উত্তর</h2><div id="myReplies">আপনার পাঠানো মেসেজের উত্তর এখানে দেখা যাবে।</div></div></section>
<section id="admin" class="page"><div class="card"><h2>🔐 অ্যাডমিন প্যানেল</h2><div id="adminGate"><p class="hint">অ্যাডমিন PIN দিন।</p><input id="adminPin" type="password" placeholder="Admin PIN"><button onclick="unlockAdmin()">প্রবেশ করুন</button><p id="pinError" class="hint"></p></div>
<div id="adminArea" class="hidden">
<h2>📩 কাস্টমার মেসেজ</h2><div id="adminMessages">লোড হচ্ছে...</div>
<hr style="border:0;border-top:1px solid #eee;margin:15px 0">
<h2>📋 কাস্টমার অর্ডার</h2><div id="adminOrders">লোড হচ্ছে...</div>
<hr style="border:0;border-top:1px solid #eee;margin:15px 0">
<h2>➕ নতুন অফার যোগ করুন</h2><select id="newOperator"><option>GP</option><option>Banglalink</option><option>Robi</option><option>Airtel</option><option>Teletalk</option></select>
<input id="newOfferName" placeholder="অফারের নাম"><input id="newOfferPrice" type="number" min="1" placeholder="মূল্য (টাকা)"><input id="newOfferValidity" placeholder="মেয়াদ"><button onclick="addOffer()">অফার যোগ করুন</button>
<h2 style="margin-top:18px">📦 অফার পরিচালনা</h2><div id="adminOfferList"></div>
<h2 style="margin-top:18px">📢 নোটিশ পরিবর্তন</h2><input id="newNotice" placeholder="নতুন নোটিশ"><button onclick="saveNotice()">নোটিশ প্রকাশ</button>
</div></div></section>
</main>
<nav>
<button onclick="showPage('home')">🏠<br>হোম</button><button onclick="showPage('offers')">📦<br>অফার</button><button onclick="showPage('orders')">📋<br>অর্ডার</button><button onclick="showPage('contact')">✉️<br>মেসেজ</button><button onclick="showPage('admin')">⚙️<br>Admin</button>
</nav>
<script type="module">
import {initializeApp} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-app.js";
import {getAuth,signInAnonymously,onAuthStateChanged} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-auth.js";
import {getFirestore,collection,addDoc,query,orderBy,onSnapshot,doc,setDoc,updateDoc,deleteDoc,serverTimestamp} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-firestore.js";

const firebaseConfig={
 apiKey:"AIzaSyCxCr4NkVhnFi2cFRcvA9v8Djr1Df9_76Y",
 authDomain:"fahim-ahmad-telecom.firebaseapp.com",
 projectId:"fahim-ahmad-telecom",
 storageBucket:"fahim-ahmad-telecom.firebasestorage.app",
 messagingSenderId:"965841120853",
 appId:"1:965841120853:web:7fc6a75769a0fdfbd0eedc",
 measurementId:"G-N325EFWEXN"
};
const app=initializeApp(firebaseConfig),auth=getAuth(app),db=getFirestore(app);
const $=id=>document.getElementById(id);
let uid=null,selectedOperator="all",offers=[],adminUnlocked=false,unsubs=[];
const ADMIN_PIN="FN2026"; // প্রকাশের আগে নিজের পছন্দমতো PIN বদলান
const esc=v=>String(v??"").replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
const money=v=>Number(v||0).toFixed(2);
function watch(ref,cb,err){unsubs.push(onSnapshot(ref,cb,e=>{console.error(e);if(err)err(e)}))}
onAuthStateChanged(auth,async user=>{
 if(user){uid=user.uid;startApp()}
 else {try{await signInAnonymously(auth)}catch(e){alert("Firebase Anonymous Authentication চালু করুন: "+e.message)}}
});
function startApp(){
 watch(collection(db,"offers"),s=>{offers=s.docs.map(d=>({id:d.id,...d.data()}));renderOffers();renderHomeOffers();renderAdminOffers()});
 watch(doc(db,"settings","notice"),s=>$("notice").innerText=s.exists()?s.data().text:"FN Telecom-এ আপনাকে স্বাগতম।");
 watch(query(collection(db,"messages"),orderBy("createdAt","desc")),s=>{
  const mine=s.docs.filter(d=>d.data().sessionId===uid);
  $("myReplies").innerHTML=mine.map(d=>{const x=d.data();return `<div class="entry"><b>আপনার মেসেজ:</b> ${esc(x.message)}<br><span class="tag">${esc(x.status||"পাঠানো হয়েছে")}</span>${x.reply?`<br><b>অ্যাডমিনের উত্তর:</b> ${esc(x.reply)}`:"<br><span class='hint'>উত্তরের অপেক্ষায়...</span>"}</div>`}).join("")||"এখনো কোনো মেসেজ পাঠাননি।";
 });
}
window.showPage=id=>{document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));$(id).classList.add("active")};
window.pickOperator=op=>{$("filter").value=op;showPage("offers");renderOffers()};
function offerCard(o){return `<div class="offer"><strong>${esc(o.name)}</strong><br>অপারেটর: ${esc(o.operator)}<br>মেয়াদ: ${esc(o.validity)}<br>মূল্য: ৳${money(o.price)}<br><button onclick="placeOrder('${o.id}')">এই অফার অর্ডার করুন</button></div>`}
window.renderOffers=()=>{const f=$("filter").value;$("offerList").innerHTML=offers.filter(o=>f==="all"||o.operator===f).map(offerCard).join("")||"কোনো অফার নেই।"};
function renderHomeOffers(){$("homeOffers").innerHTML=offers.slice(0,3).map(offerCard).join("")||"এখনো কোনো অফার যোগ করা হয়নি।"}
window.placeOrder=async id=>{
 const o=offers.find(x=>x.id===id),phone=$("mobile").value.trim();
 if(!o)return;if(!/^01[3-9]\d{8}$/.test(phone)){alert("সঠিক ১১ ডিজিটের মোবাইল নম্বর লিখুন।");showPage("home");return}
 try{await addDoc(collection(db,"orders"),{sessionId:uid,phone,offer:o.name,operator:o.operator,price:Number(o.price),status:"Pending",createdAt:serverTimestamp()});$("orderStatus").innerHTML=`<p class="tag">অর্ডার জমা হয়েছে</p><p>অফার: ${esc(o.name)}<br>নম্বর: ${esc(phone)}<br>অবস্থা: Pending</p>`;showPage("orders")}
 catch(e){alert("অর্ডার জমা হয়নি: "+e.message)}
};
window.sendCustomerMessage=async()=>{
 const name=$("customerName").value.trim(),phone=$("customerPhone").value.trim(),message=$("customerMessage").value.trim();
 if(!name||!/^01[3-9]\d{8}$/.test(phone)||message.length<2){$("sendStatus").innerText="নাম, সঠিক ১১ ডিজিটের নম্বর ও মেসেজ লিখুন।";return}
 try{await addDoc(collection(db,"messages"),{sessionId:uid,name,phone,message,status:"নতুন",reply:"",createdAt:serverTimestamp()});$("customerMessage").value="";$("sendStatus").innerText="আপনার মেসেজ পাঠানো হয়েছে।";}catch(e){$("sendStatus").innerText="মেসেজ পাঠানো যায়নি: "+e.message}
};
window.unlockAdmin=()=>{
 if($("adminPin").value!==ADMIN_PIN){$("pinError").innerText="PIN সঠিক নয়।";return}
 adminUnlocked=true;$("adminGate").classList.add("hidden");$("adminArea").classList.remove("hidden");loadAdmin();
};
function loadAdmin(){
 watch(query(collection(db,"messages"),orderBy("createdAt","desc")),s=>{
  $("adminMessages").innerHTML=s.docs.map(d=>{const x=d.data();return `<div class="entry"><b>${esc(x.name)}</b> · ${esc(x.phone)}<br>${esc(x.message)}<br><span class="tag">${esc(x.status||"নতুন")}</span>${x.reply?`<br><b>আগের উত্তর:</b> ${esc(x.reply)}`:""}<textarea id="reply_${d.id}" placeholder="কাস্টমারকে উত্তর লিখুন">${esc(x.reply||"")}</textarea><button onclick="replyMessage('${d.id}')">উত্তর পাঠান</button></div>`}).join("")||"কোনো মেসেজ নেই।";
 });
 watch(query(collection(db,"orders"),orderBy("createdAt","desc")),s=>{
  $("adminOrders").innerHTML=s.docs.map(d=>{const x=d.data();return `<div class="entry"><b>${esc(x.offer)}</b><br>নম্বর: ${esc(x.phone)} · ${esc(x.operator)}<br>মূল্য: ৳${money(x.price)}<br>অবস্থা: ${esc(x.status)}<br><button onclick="setOrderStatus('${d.id}','Successful')">সম্পন্ন</button> <button class="red" onclick="setOrderStatus('${d.id}','Cancelled')">বাতিল</button></div>`}).join("")||"কোনো অর্ডার নেই।";
 });
}
window.replyMessage=async id=>{if(!adminUnlocked)return;const reply=$("reply_"+id).value.trim();if(!reply)return alert("উত্তর লিখুন।");try{await updateDoc(doc(db,"messages",id),{reply,status:"উত্তর দেওয়া হয়েছে",repliedAt:serverTimestamp()});alert("উত্তর পাঠানো হয়েছে।")}catch(e){alert(e.message)}};
window.setOrderStatus=async(id,status)=>{if(!adminUnlocked)return;try{await updateDoc(doc(db,"orders",id),{status});}catch(e){alert(e.message)}};
window.addOffer=async()=>{if(!adminUnlocked)return;const name=$("newOfferName").value.trim(),price=Number($("newOfferPrice").value),validity=$("newOfferValidity").value.trim(),operator=$("newOperator").value;if(!name||price<=0||!validity)return alert("সব তথ্য পূরণ করুন।");try{await addDoc(collection(db,"offers"),{name,price,validity,operator,createdAt:serverTimestamp()});$("newOfferName").value=$("newOfferPrice").value=$("newOfferValidity").value="";alert("অফার যোগ হয়েছে।")}catch(e){alert(e.message)}};
function renderAdminOffers(){if(!adminUnlocked)return;$("adminOfferList").innerHTML=offers.map(o=>`<div class="entry">${esc(o.name)} · ${esc(o.operator)} · ৳${money(o.price)}<br><button class="red" onclick="removeOffer('${o.id}')">ডিলিট</button></div>`).join("")||"কোনো অফার নেই।"}
window.removeOffer=async id=>{if(!adminUnlocked||!confirm("অফারটি মুছবেন?"))return;try{await deleteDoc(doc(db,"offers",id))}catch(e){alert(e.message)}};
window.saveNotice=async()=>{if(!adminUnlocked)return;const text=$("newNotice").value.trim();if(!text)return alert("নোটিশ লিখুন।");try{await setDoc(doc(db,"settings","notice"),{text,updatedAt:serverTimestamp()});alert("নোটিশ প্রকাশ হয়েছে।")}catch(e){alert(e.message)}};
</script>
</body></html>
