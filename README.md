

<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FN Telecom</title>
<style>
:root{--green:#087b4e;--deep:#063d2b;--mint:#eaf7ef;--ink:#173629;--muted:#718078;--line:#e3eee7;--white:#fff;--shadow:0 10px 28px #073d2812}
*{box-sizing:border-box;margin:0;padding:0}body{font-family:system-ui,-apple-system,Arial,sans-serif;background:#f3f7f4;color:var(--ink);line-height:1.5}button,input,select{font:inherit}button{border:0;padding:12px 16px;border-radius:12px;background:var(--green);color:#fff;font-size:14px;font-weight:700;cursor:pointer;transition:.18s}button:active{transform:scale(.98)}button:disabled{opacity:.55;cursor:not-allowed}input,select{width:100%;padding:13px 14px;margin:7px 0;border:1px solid #dce8df;border-radius:12px;font-size:15px;background:#fff;color:var(--ink);outline:none}input:focus,select:focus{border-color:var(--green);box-shadow:0 0 0 3px #087b4e18}label{display:block;font-size:13px;font-weight:650;margin-top:8px;color:#496256}
#authScreen{min-height:100vh;display:flex;align-items:center;justify-content:center;padding:20px;background:radial-gradient(circle at top right,#15965e 0,#0b6844 32%,#042e21 100%)}.auth-card{width:100%;max-width:410px;background:white;padding:30px 24px;border-radius:24px;text-align:center;box-shadow:0 24px 70px #001b1080}.auth-logo{width:66px;height:66px;margin:0 auto 12px;border-radius:20px;background:linear-gradient(135deg,#0c9a5c,#045332);color:white;display:grid;place-items:center;font-size:24px;font-weight:900;box-shadow:0 8px 20px #087b4e35}.auth-card h2{color:var(--deep);font-size:25px;margin:8px}.auth-card>p{color:var(--muted);font-size:13px}.auth-card button{width:100%;margin-top:9px}#registerBtn{background:#eaf5ee;color:var(--deep)}#authMessage{margin-top:13px;color:#c33;overflow-wrap:anywhere;font-size:13px}
#appScreen{display:none;padding-bottom:88px}header{background:linear-gradient(120deg,#053b29,#087b4e);color:white;padding:22px 18px 25px;text-align:center;border-radius:0 0 24px 24px;box-shadow:0 8px 24px #063d2b25}header h1{font-size:25px;letter-spacing:.3px}header p{font-size:13px;color:#d6f3e2;margin-top:3px}.container{max-width:680px;margin:auto;padding:16px}.card{background:var(--white);padding:18px;border:1px solid var(--line);border-radius:18px;margin-bottom:15px;box-shadow:var(--shadow)}.title{font-size:17px;font-weight:800;margin-bottom:13px;color:var(--deep)}.page{display:none}.page.active{display:block}.grid{display:grid;grid-template-columns:repeat(2,1fr);gap:10px}.operator{background:var(--mint);border:1px solid #d9eee0;padding:17px 5px;border-radius:14px;text-align:center;cursor:pointer;font-weight:750;color:var(--deep)}.operator span{display:block;font-size:24px;margin-bottom:6px}.offer{padding:14px;border:1px solid var(--line);border-radius:14px;margin-bottom:11px;background:linear-gradient(120deg,#fff,#fbfefc)}.offer h3{color:var(--green);margin-bottom:6px;font-size:16px}.offer p{font-size:13px;color:#596c61;margin:3px 0}.offer button{margin-top:9px;min-width:125px}.item{padding:13px 2px;border-bottom:1px solid #edf2ee;font-size:13px;line-height:1.8;overflow-wrap:anywhere}.item:last-child{border-bottom:0}.small{font-size:12px;color:var(--muted)}nav{position:fixed;bottom:0;left:0;width:100%;display:flex;justify-content:space-around;gap:2px;background:#ffffffed;backdrop-filter:blur(12px);padding:8px 3px calc(8px + env(safe-area-inset-bottom));box-shadow:0 -5px 22px #00000012;z-index:10;border-top:1px solid var(--line)}nav button{background:transparent;color:#365747;font-size:10px;padding:6px 4px;min-width:0;flex:1;line-height:1.4}nav button:active{background:var(--mint)}.danger{background:#d93636}.blue{background:#0755aa}.logout{background:#d93636;width:100%;margin-top:10px}.status{color:var(--green);font-weight:bold}.balance{font-size:30px;font-weight:850;color:var(--green);margin:8px 0}.muted{color:var(--muted);font-size:12px;line-height:1.6}.payment-options{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin:8px 0}.payment-options span{padding:10px 4px;border-radius:12px;background:#fff4f5;border:1px solid #f6dfe3;text-align:center;font-weight:800;color:#b31f50;font-size:12px}.payment-options span:nth-child(2){background:#fff8ed;border-color:#f6e7cb;color:#a85a00}.payment-options span:nth-child(3){background:#f3efff;border-color:#e4dcff;color:#6338a5}.hero-note{padding:12px;border-radius:12px;background:var(--mint);font-size:12px;color:#365747;margin-top:10px}
@media(min-width:560px){.grid{grid-template-columns:repeat(3,1fr)}}
</style>
</head>
<body>
<div id="authScreen"><div class="auth-card">
<div class="auth-logo">FN</div><h2>FN Telecom</h2><p>আপনার বিশ্বস্ত টেলিকম সেবা</p><br>
<input id="email" type="email" placeholder="আপনার Email" autocomplete="username">
<input id="password" type="password" placeholder="Password" autocomplete="current-password">
<button id="loginBtn">Login করুন</button><button id="registerBtn">নতুন Account খুলুন</button><p id="authMessage"></p>
</div></div>

<div id="appScreen">
<header><h1>🟢 FN Telecom</h1><p>আপনার বিশ্বস্ত টেলিকম সেবা</p></header>
<div class="container">
<section id="home" class="page active">
<div class="card"><div class="title">📱 মোবাইল নম্বর</div><input id="mobile" type="tel" maxlength="11" placeholder="01XXXXXXXXX"></div>
<div class="card"><div class="title">📡 অপারেটর নির্বাচন</div><div class="grid">
<div class="operator" onclick="selectOperator('GP')"><span>🟢</span>GP</div>
<div class="operator" onclick="selectOperator('Banglalink')"><span>🟠</span>Banglalink</div>
<div class="operator" onclick="selectOperator('Robi')"><span>🔴</span>Robi</div>
<div class="operator" onclick="selectOperator('Airtel')"><span>🔴</span>Airtel</div>
<div class="operator" onclick="selectOperator('Teletalk')"><span>🔵</span>Teletalk</div>
</div></div>
<div class="card"><div class="title">🔥 জনপ্রিয় অফার</div><div id="homeOffers"></div></div>
<div class="card"><div class="title">📢 নোটিশ</div><p id="notice">লোড হচ্ছে...</p></div>
</section>

<section id="offers" class="page"><div class="card"><div class="title">📦 সকল অফার</div>
<select id="operatorFilter" onchange="renderOffers()"><option value="all">সকল অপারেটর</option><option>GP</option><option>Banglalink</option><option>Robi</option><option>Airtel</option><option>Teletalk</option></select><div id="offerList"></div></div></section>

<section id="orders" class="page"><div class="card"><div class="title">📋 আমার অর্ডার</div><div id="orderList"></div></div></section>

<section id="balance" class="page">
<div class="card"><div class="title">💰 আমার ব্যালেন্স</div><div class="balance">৳ <span id="balanceAmount">0.00</span></div><p class="muted">ব্যালেন্স যোগ করতে নিচের আবেদন ফর্ম পূরণ করুন। আবেদন অনুমোদনের আগে ব্যালেন্স যোগ হবে না।</p></div>
<div class="card"><div class="title">➕ ব্যালেন্স যোগের আবেদন</div>
<label>কত টাকা যোগ করতে চান?</label><input id="requestAmount" type="number" min="1" max="50000" step="1" placeholder="যেমন ২০০">
<label>পেমেন্ট মাধ্যম</label><div class="payment-options"><span> bKash </span><span> Nagad </span><span> Rocket </span></div><select id="paymentMethod"><option value="bKash">bKash</option><option value="Nagad">Nagad</option><option value="Rocket">Rocket</option></select>
<label>যে নম্বর থেকে পেমেন্ট করেছেন</label><input id="payerPhone" type="tel" maxlength="11" placeholder="01XXXXXXXXX">
<label>Transaction ID</label><input id="trxId" maxlength="80" placeholder="TrxID লিখুন">
<button onclick="submitBalanceRequest()">আবেদন পাঠান</button><p class="hero-note">শুধু পেমেন্ট সম্পন্ন করার পর আবেদন পাঠান। Admin আপনার Transaction ID যাচাই করে অনুমোদন করলে ব্যালেন্স যোগ হবে।</p>
</div>
<div class="card"><div class="title">🧾 আমার ব্যালেন্স আবেদনের অবস্থা</div><div id="myBalanceRequests"></div></div>
<div class="card"><div class="title">📚 লেনদেনের ইতিহাস</div><div id="myTransactions"></div></div>
</section>

<section id="profile" class="page"><div class="card"><div class="title">👤 আমার প্রোফাইল</div>
<input id="userName" placeholder="আপনার নাম"><input id="userPhone" maxlength="11" placeholder="মোবাইল নম্বর"><p id="userEmail" class="small"></p>
<button onclick="saveProfile()">তথ্য সংরক্ষণ</button></div>
<div class="card"><p>FN Telecom</p><p>WhatsApp: 01640592773</p><button onclick="window.open('https://wa.me/8801640592773','_blank')">WhatsApp যোগাযোগ</button><button class="logout" onclick="logoutUser()">Logout</button></div>
</section>

<section id="admin" class="page"><div class="card"><div class="title">⚙️ FN Telecom Admin</div>
<p>মোট অর্ডার: <b id="adminOrders">0</b></p><p>সম্পন্ন অর্ডার: <b id="adminSuccess">0</b></p></div>
<div class="card"><div class="title">💰 ব্যালেন্স আবেদন পরিচালনা</div><div id="adminBalanceRequests"></div></div>
<div class="card"><div class="title">➕ নতুন অফার যোগ করুন</div>
<select id="newOperator"><option>GP</option><option>Banglalink</option><option>Robi</option><option>Airtel</option><option>Teletalk</option></select>
<input id="newOfferName" placeholder="অফারের নাম"><input id="newOfferPrice" type="number" min="1" placeholder="মূল্য"><input id="newOfferValidity" placeholder="মেয়াদ"><button onclick="addOffer()">অফার যোগ করুন</button></div>
<div class="card"><div class="title">📦 অফার পরিচালনা</div><div id="adminOfferList"></div></div>
<div class="card"><div class="title">📋 সকল কাস্টমার অর্ডার</div><div id="adminOrderList"></div></div>
<div class="card"><div class="title">📢 নোটিশ পরিবর্তন</div><input id="newNotice" placeholder="নতুন নোটিশ"><button onclick="updateNotice()">নোটিশ প্রকাশ</button></div>
<button class="logout" onclick="showPage('profile')">প্রোফাইলে ফিরে যান</button>
</section>
</div>
<nav id="mainNav">
<button onclick="showPage('home')">🏠<br>হোম</button><button onclick="showPage('offers')">📦<br>অফার</button>
<button onclick="showPage('orders')">📋<br>অর্ডার</button><button onclick="showPage('balance')">💰<br>ব্যালেন্স</button>
<button onclick="showPage('profile')">👤<br>প্রোফাইল</button><button id="adminMenu" style="display:none" onclick="showPage('admin')">⚙️<br>Admin</button>
</nav>
</div>

<script type="module">
import {initializeApp} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-app.js";
import {getAuth,createUserWithEmailAndPassword,signInWithEmailAndPassword,onAuthStateChanged,signOut,sendEmailVerification} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-auth.js";
import {getFirestore,collection,addDoc,getDocs,query,where,orderBy,onSnapshot,doc,getDoc,setDoc,updateDoc,deleteDoc,serverTimestamp} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-firestore.js";
import {getFunctions,httpsCallable} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-functions.js";

const firebaseConfig={apiKey:"AIzaSyCxCr4NkVhnFi2cFRcvA9v8Djr1Df9_76Y",authDomain:"fahim-ahmad-telecom.firebaseapp.com",projectId:"fahim-ahmad-telecom",storageBucket:"fahim-ahmad-telecom.firebasestorage.app",messagingSenderId:"965841120853",appId:"1:965841120853:web:7fc6a75769a0fdfbd0eedc",measurementId:"G-N325EFWEXN"};
const app=initializeApp(firebaseConfig),auth=getAuth(app),db=getFirestore(app),functions=getFunctions(app,"asia-south1");
const $=id=>document.getElementById(id);
let currentUser=null,isAdmin=false,offers=[],orders=[];
let unsubs=[];
function cleanup(){unsubs.forEach(fn=>{try{fn()}catch(e){}});unsubs=[]}
function esc(v){return String(v??"").replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]))}
function money(v){return Number(v||0).toFixed(2)}
function msg(t){$("authMessage").innerText=t}
$("registerBtn").onclick=async()=>{try{const email=$("email").value.trim(),password=$("password").value;if(!email||password.length<6)return msg("সঠিক Email এবং কমপক্ষে ৬ অক্ষরের Password দিন");const r=await createUserWithEmailAndPassword(auth,email,password);await sendEmailVerification(r.user);msg("অ্যাকাউন্ট তৈরি হয়েছে। ইমেইল যাচাই করে তারপর লগইন করুন।");await signOut(auth)}catch(e){msg(e.message)}};
$("loginBtn").onclick=async()=>{try{await signInWithEmailAndPassword(auth,$("email").value.trim(),$("password").value);msg("")}catch(e){msg(e.message)}};
onAuthStateChanged(auth,async user=>{
 cleanup();
 if(!user){currentUser=null;isAdmin=false;$("authScreen").style.display="flex";$("appScreen").style.display="none";return}
 await user.reload();
 if(!user.emailVerified){alert("আগে আপনার ইমেইল যাচাই করুন। ইমেইলের verification link খুলুন।");await signOut(auth);return}
 currentUser=user;const token=await user.getIdTokenResult(true);isAdmin=token.claims.admin===true;
 $("authScreen").style.display="none";$("appScreen").style.display="block";$("userEmail").innerText=user.email||"";
 $("adminMenu").style.display=isAdmin?"block":"none";loadData();showPage("home");
});
window.logoutUser=()=>signOut(auth);
window.showPage=id=>{if(id==="admin"&&!isAdmin)return alert("Admin অনুমতি নেই");document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));$(id).classList.add("active")};
function loadData(){loadOffers();loadOrders();loadProfile();loadNotice();loadBalance();if(isAdmin){loadAdminOrders();loadAdminBalanceRequests()}}
function loadOffers(){unsubs.push(onSnapshot(collection(db,"offers"),s=>{offers=s.docs.map(d=>({id:d.id,...d.data()}));renderOffers();renderHomeOffers();if(isAdmin)renderAdminOffers()},e=>alert("অফার লোড হয়নি: "+e.message)))}
window.renderOffers=()=>{const f=$("operatorFilter").value;$("offerList").innerHTML=offers.filter(o=>f==="all"||o.operator===f).map(o=>`<div class="offer"><h3>${esc(o.name)}</h3><p>অপারেটর: ${esc(o.operator)}</p><p>মেয়াদ: ${esc(o.validity)}</p><p>মূল্য: ৳${money(o.price)}</p><button onclick="buyOffer('${o.id}')">অর্ডার করুন</button></div>`).join("")||"কোনো অফার নেই।"};
function renderHomeOffers(){$("homeOffers").innerHTML=offers.slice(0,3).map(o=>`<div class="offer"><h3>${esc(o.name)}</h3><p>${esc(o.operator)} · ৳${money(o.price)}</p><button onclick="buyOffer('${o.id}')">অর্ডার করুন</button></div>`).join("")||"কোনো অফার নেই।"}
window.selectOperator=op=>{$("operatorFilter").value=op;showPage("offers");renderOffers()};
window.buyOffer=async id=>{const o=offers.find(x=>x.id===id),phone=$("mobile").value.trim();if(!o)return;if(!/^01[3-9]\d{8}$/.test(phone))return alert("সঠিক ১১ ডিজিটের মোবাইল নম্বর লিখুন");if(!confirm(o.name+" অর্ডার করবেন?"))return;try{await addDoc(collection(db,"orders"),{userId:currentUser.uid,userEmail:currentUser.email,offer:o.name,operator:o.operator,phone,price:Number(o.price),status:"Pending",createdAt:serverTimestamp()});alert("অর্ডার জমা হয়েছে");showPage("orders")}catch(e){alert(e.message)}};
function loadOrders(){const q=query(collection(db,"orders"),where("userId","==",currentUser.uid),orderBy("createdAt","desc"));unsubs.push(onSnapshot(q,s=>{orders=s.docs.map(d=>({id:d.id,...d.data()}));$("orderList").innerHTML=orders.map(o=>`<div class="item"><b>${esc(o.offer)}</b><br>অপারেটর: ${esc(o.operator)}<br>নম্বর: ${esc(o.phone)}<br>মূল্য: ৳${money(o.price)}<br>অবস্থা: <b>${esc(o.status)}</b></div>`).join("")||"এখনো কোনো অর্ডার নেই।"}))}
function loadProfile(){getDoc(doc(db,"users",currentUser.uid)).then(s=>{if(s.exists()){$("userName").value=s.data().name||"";$("userPhone").value=s.data().phone||""}}).catch(e=>console.error(e))}
window.saveProfile=async()=>{const name=$("userName").value.trim(),phone=$("userPhone").value.trim();if(phone&&!/^01[3-9]\d{8}$/.test(phone))return alert("সঠিক ১১ ডিজিটের নম্বর দিন");try{await setDoc(doc(db,"users",currentUser.uid),{name,phone,email:currentUser.email},{merge:true});alert("প্রোফাইল সংরক্ষিত হয়েছে")}catch(e){alert(e.message)}};
function loadNotice(){unsubs.push(onSnapshot(doc(db,"settings","notice"),s=>$("notice").innerText=s.exists()?s.data().text:"FN Telecom-এ আপনাকে স্বাগতম।"))}
window.updateNotice=async()=>{if(!isAdmin)return;const text=$("newNotice").value.trim();if(!text)return alert("নোটিশ লিখুন");try{await setDoc(doc(db,"settings","notice"),{text});alert("নোটিশ প্রকাশ হয়েছে")}catch(e){alert(e.message)}};
function loadBalance(){unsubs.push(onSnapshot(doc(db,"users",currentUser.uid),s=>$("balanceAmount").innerText=money(s.exists()?s.data().balance:0),e=>alert("ব্যালেন্স লোড সমস্যা: "+e.message)));
const rq=query(collection(db,"balanceRequests"),where("userId","==",currentUser.uid),orderBy("createdAt","desc"));unsubs.push(onSnapshot(rq,s=>$("myBalanceRequests").innerHTML=s.docs.map(d=>{const x=d.data();return `<div class="item">৳${money(x.amount)} · ${esc(x.method)}<br>TrxID: ${esc(x.trxId)}<br>অবস্থা: <b>${esc(x.status)}</b></div>`}).join("")||"কোনো আবেদন নেই।"));
const tq=query(collection(db,"transactions"),where("userId","==",currentUser.uid),orderBy("createdAt","desc"));unsubs.push(onSnapshot(tq,s=>$("myTransactions").innerHTML=s.docs.map(d=>{const x=d.data();return `<div class="item">${esc(x.type)} · ৳${money(x.amount)}<br>বিবরণ: ${esc(x.note||"")}<br>আগের ব্যালেন্স: ৳${money(x.previousBalance)} · পরের ব্যালেন্স: ৳${money(x.newBalance)}</div>`}).join("")||"এখনো কোনো লেনদেন নেই।"))}
window.submitBalanceRequest=async()=>{const amount=Number($("requestAmount").value),method=$("paymentMethod").value,phone=$("payerPhone").value.trim(),trxId=$("trxId").value.trim();if(!Number.isInteger(amount)||amount<1||amount>50000)return alert("১ থেকে ৫০,০০০ টাকার মধ্যে পূর্ণ সংখ্যা লিখুন");if(!/^01[3-9]\d{8}$/.test(phone))return alert("সঠিক পেমেন্ট নম্বর দিন");if(trxId.length<6)return alert("সঠিক Transaction ID দিন");try{await addDoc(collection(db,"balanceRequests"),{userId:currentUser.uid,userEmail:currentUser.email,amount,method,payerPhone:phone,trxId,status:"Pending",createdAt:serverTimestamp()});$("requestAmount").value=$("payerPhone").value=$("trxId").value="";alert("আবেদন জমা হয়েছে। Admin যাচাই করার পর ব্যালেন্স যোগ হবে।")}catch(e){alert("আবেদন জমা হয়নি: "+e.message)}};
function loadAdminBalanceRequests(){unsubs.push(onSnapshot(query(collection(db,"balanceRequests"),where("status","==","Pending"),orderBy("createdAt","asc")),s=>{$("adminBalanceRequests").innerHTML=s.docs.map(d=>{const x=d.data();return `<div class="item"><b>৳${money(x.amount)}</b> · ${esc(x.method)}<br>গ্রাহক: ${esc(x.userEmail)}<br>পেমেন্ট নম্বর: ${esc(x.payerPhone)}<br>TrxID: <b>${esc(x.trxId)}</b><br><button onclick="reviewBalanceRequest('${d.id}','approve')">Approve</button><button class="danger" onclick="reviewBalanceRequest('${d.id}','reject')">Reject</button></div>`}).join("")||"Pending আবেদন নেই।"},e=>alert("Admin request error: "+e.message)))}
window.reviewBalanceRequest=async(id,action)=>{if(!isAdmin)return alert("Admin অনুমতি নেই");const note=action==="approve"?"পেমেন্ট যাচাই করে অনুমোদন করছেন?":"আবেদন Reject করবেন?";if(!confirm(note))return;try{const fn=httpsCallable(functions,"reviewBalanceRequest");const result=await fn({requestId:id,action});alert(result.data.message||"সম্পন্ন")}catch(e){alert("কাজটি হয়নি: "+(e.message||e))}};
function loadAdminOrders(){unsubs.push(onSnapshot(query(collection(db,"orders"),orderBy("createdAt","desc")),s=>{const all=s.docs.map(d=>({id:d.id,...d.data()}));$("adminOrders").innerText=all.length;$("adminSuccess").innerText=all.filter(o=>o.status==="Successful").length;$("adminOrderList").innerHTML=all.map(o=>`<div class="item"><b>${esc(o.offer)}</b><br>কাস্টমার: ${esc(o.userEmail)}<br>মোবাইল: ${esc(o.phone)}<br>অপারেটর: ${esc(o.operator)}<br>মূল্য: ৳${money(o.price)}<br>অবস্থা: ${esc(o.status)}<br>${o.status==="Pending"?`<button onclick="changeOrder('${o.id}','Successful')">Successful</button><button class="danger" onclick="changeOrder('${o.id}','Cancelled')">Cancelled</button>`:""}</div>`).join("")||"কোনো অর্ডার নেই।"},e=>alert("Admin Order Error: "+e.message)))}
window.changeOrder=async(id,status)=>{if(!isAdmin)return alert("অনুমতি নেই");try{await updateDoc(doc(db,"orders",id),{status});alert("অর্ডার আপডেট হয়েছে")}catch(e){alert(e.message)}};
window.addOffer=async()=>{if(!isAdmin)return;const name=$("newOfferName").value.trim(),price=Number($("newOfferPrice").value),validity=$("newOfferValidity").value.trim(),operator=$("newOperator").value;if(!name||p
