<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FN Telecom</title>

<style>
*{margin:0;padding:0;box-sizing:border-box}
body{
font-family:Arial,sans-serif;
background:#f1f5f3;
color:#172b24;
}
header{
background:#073e2d;
color:white;
padding:20px;
text-align:center;
}
header h1{font-size:26px}
header p{font-size:13px;margin-top:5px}

.container{
max-width:650px;
margin:auto;
padding:15px;
}

.card{
background:white;
padding:18px;
border-radius:15px;
margin-bottom:15px;
box-shadow:0 3px 12px #00000010;
}

.balance{
background:linear-gradient(135deg,#087b4e,#043d2c);
color:white;
padding:25px;
border-radius:17px;
margin-bottom:15px;
}

.balance h2{font-size:16px}
.balance h1{font-size:32px;margin:12px 0}

button{
border:none;
padding:12px 16px;
border-radius:9px;
background:#07864e;
color:white;
font-size:14px;
cursor:pointer;
margin:4px 0;
}

button:hover{opacity:.85}

input,select{
width:100%;
padding:13px;
border:1px solid #ddd;
border-radius:9px;
margin:8px 0;
font-size:15px;
}

.grid{
display:grid;
grid-template-columns:repeat(2,1fr);
gap:12px;
}

.operator{
background:#f5f9f6;
padding:18px 8px;
border-radius:12px;
text-align:center;
cursor:pointer;
border:1px solid #e4eee8;
font-weight:bold;
}

.operator span{
font-size:27px;
display:block;
margin-bottom:8px;
}

.title{
font-size:18px;
font-weight:bold;
margin-bottom:15px;
}

.offer{
border:1px solid #e4eee8;
padding:15px;
border-radius:12px;
margin-bottom:12px;
}

.offer h3{color:#087b4e;margin-bottom:7px}
.offer p{font-size:14px;margin:5px 0}

nav{
position:fixed;
bottom:0;
left:0;
width:100%;
background:white;
display:flex;
justify-content:space-around;
padding:12px 2px;
box-shadow:0 -2px 10px #00000012;
z-index:10;
}

nav button{
background:transparent;
color:#174c37;
font-size:11px;
padding:5px;
}

.page{display:none;padding-bottom:85px}
.page.active{display:block}

.hidden{display:none}

.item{
padding:12px;
border-bottom:1px solid #eee;
font-size:14px;
}

.green{color:green}
.red{color:red}

footer{
text-align:center;
padding:20px;
font-size:12px;
color:#777;
}

.admin{
background:#172b24;
color:white;
}

.small{font-size:12px;color:#777}
</style>
</head>

<body>

<header>
<h1>🟢 FN Telecom</h1>
<p>আপনার বিশ্বস্ত টেলিকম সেবা</p>
</header>

<div class="container">

<!-- HOME -->
<div id="home" class="page active">

<div class="balance">
<h2>💰 আপনার বর্তমান ব্যালেন্স</h2>
<h1 id="balance">৳ 0.00</h1>
<button onclick="showPage('addmoney')">
+ ব্যালেন্স যোগ করুন
</button>
</div>

<div class="card">
<div class="title">📱 মোবাইল রিচার্জ ও অফার</div>

<input id="mobile" type="tel"
placeholder="মোবাইল নম্বর লিখুন"
maxlength="11">

<button onclick="findOperator()">নম্বর যাচাই করুন</button>
<p id="operatorResult"></p>
</div>

<div class="card">
<div class="title">📡 অপারেটর নির্বাচন</div>

<div class="grid">

<div class="operator" onclick="selectOperator('GP')">
<span>🟢</span>Grameenphone
</div>

<div class="operator" onclick="selectOperator('Banglalink')">
<span>🟠</span>Banglalink
</div>

<div class="operator" onclick="selectOperator('Robi')">
<span>🔴</span>Robi
</div>

<div class="operator" onclick="selectOperator('Airtel')">
<span>🔴</span>Airtel
</div>

<div class="operator" onclick="selectOperator('Teletalk')">
<span>🔵</span>Teletalk
</div>

</div>
</div>

<div class="card">
<div class="title">🔥 জনপ্রিয় অফার</div>
<div id="homeOffers"></div>
</div>

<div class="card">
<div class="title">📢 নোটিশ বোর্ড</div>
<p id="notice">FN Telecom-এ আপনাকে স্বাগতম।</p>
</div>

</div>

<!-- OFFERS -->
<div id="offers" class="page">
<div class="card">
<div class="title">📦 সকল অফার</div>

<select id="operatorFilter" onchange="renderOffers()">
<option value="all">সকল অপারেটর</option>
<option>GP</option>
<option>Banglalink</option>
<option>Robi</option>
<option>Airtel</option>
<option>Teletalk</option>
</select>

<div id="offerList"></div>
</div>
</div>

<!-- ADD MONEY -->
<div id="addmoney" class="page">
<div class="card">
<div class="title">💰 ব্যালেন্স যোগ করুন</div>

<p>পেমেন্ট মাধ্যম নির্বাচন করুন</p>

<select id="paymentMethod">
<option value="বিকাশ">বিকাশ</option>
<option value="নগদ">নগদ</option>
</select>

<input type="number" id="amount"
placeholder="টাকার পরিমাণ">

<input id="transaction"
placeholder="ট্রানজেকশন আইডি">

<button onclick="addMoneyRequest()">
পেমেন্ট আবেদন করুন
</button>

<p class="small">
আপনার আবেদন অ্যাডমিন যাচাই করার পর ব্যালেন্স যোগ হবে।
</p>
</div>
</div>

<!-- ORDERS -->
<div id="orders" class="page">
<div class="card">
<div class="title">📋 আমার অর্ডার</div>
<div id="orderList"></div>
</div>
</div>

<!-- PROFILE -->
<div id="profile" class="page">
<div class="card">
<div class="title">👤 আমার প্রোফাইল</div>

<input id="userName" placeholder="আপনার নাম">

<input id="userPhone" placeholder="মোবাইল নম্বর">

<button onclick="saveProfile()">তথ্য সংরক্ষণ করুন</button>

<hr style="margin:15px 0">

<p>মোট অর্ডার: <b id="totalOrders">0</b></p>
<p>বর্তমান ব্যালেন্স: <b id="profileBalance">৳ 0</b></p>
</div>

<div class="card">
<div class="title">📞 যোগাযোগ</div>
<p>FN Telecom</p>
<p>WhatsApp: 01640592773</p>
<button onclick="window.open('https://wa.me/8801640592773')">
WhatsApp যোগাযোগ
</button>
</div>

<div class="card">
<button onclick="showPage('adminLogin')">
⚙️ অ্যাডমিন প্যানেল
</button>
</div>
</div>

<!-- ADMIN LOGIN -->
<div id="adminLogin" class="page">
<div class="card">
<div class="title">🔐 Admin Login</div>

<input type="password" id="adminPin"
placeholder="অ্যাডমিন পিন">

<button onclick="adminLogin()">লগইন</button>

<p class="small">
ডেমো পিন: 1234
</p>
</div>
</div>

<!-- ADMIN PANEL -->
<div id="admin" class="page">

<div class="balance">
<h2>⚙️ FN Telecom Admin</h2>
<h1>Dashboard</h1>
<button onclick="adminLogout()">Logout</button>
</div>

<div class="grid">

<div class="card">
মোট অর্ডার
<h2 id="adminOrders">0</h2>
</div>

<div class="card">
মোট বিক্রি
<h2 id="adminSales">৳0</h2>
</div>

<div class="card">
মোট গ্রাহক
<h2 id="adminCustomers">1</h2>
</div>

<div class="card">
ব্যালেন্স আবেদন
<h2 id="adminRequests">0</h2>
</div>

</div>

<div class="card">
<div class="title">➕ নতুন অফার যোগ করুন</div>

<select id="newOperator">
<option>GP</option>
<option>Banglalink</option>
<option>Robi</option>
<option>Airtel</option>
<option>Teletalk</option>
</select>

<input id="newOfferName" placeholder="অফারের নাম">
<input id="newOfferPrice" type="number" placeholder="বিক্রয় মূল্য">
<input id="newOfferValidity" placeholder="মেয়াদ">
<select id="newOfferType">
<option>ইন্টারনেট</option>
<option>মিনিট</option>
<option>বান্ডেল</option>
<option>অন্যান্য</option>
</select>

<button onclick="addOffer()">অফার যোগ করুন</button>
</div>

<div class="card">
<div class="title">📦 অফার পরিচালনা</div>
<div id="adminOfferList"></div>
</div>

<div class="card">
<div class="title">💳 ব্যালেন্স আবেদন পরিচালনা</div>
<div id="requestList"></div>
</div>

<div class="card">
<div class="title">📋 সকল অর্ডার</div>
<div id="adminOrderList"></div>
</div>

<div class="card">
<div class="title">💰 গ্রাহকের ব্যালেন্স পরিচালনা</div>
<input id="customerPhone" placeholder="গ্রাহকের নম্বর">
<input id="customerAmount" type="number" placeholder="টাকার পরিমাণ">
<button onclick="adminAddBalance()">ব্যালেন্স যোগ করুন</button>
</div>

<div class="card">
<div class="title">📢 নোটিশ পরিবর্তন</div>
<input id="newNotice" placeholder="নতুন নোটিশ লিখুন">
<button onclick="updateNotice()">নোটিশ প্রকাশ করুন</button>
</div>

</div>

</div>

<nav>
<button onclick="showPage('home')">🏠<br>হোম</button>
<button onclick="showPage('offers')">📦<br>অফার</button>
<button onclick="showPage('addmoney')">💰<br>ব্যালেন্স</button>
<button onclick="showPage('orders')">📋<br>অর্ডার</button>
<button onclick="showPage('profile')">👤<br>প্রোফাইল</button>
</nav>

<footer>
FN Telecom © 2026
<br>সকল স্বত্ব সংরক্ষিত
</footer>

<script>

// DATA STORAGE

let balance = Number(localStorage.getItem('balance') || 0);

let offers = JSON.parse(localStorage.getItem('offers') || '[]');

let orders = JSON.parse(localStorage.getItem('orders') || '[]');

let requests = JSON.parse(localStorage.getItem('requests') || '[]');

let notice = localStorage.getItem('notice') ||
'FN Telecom-এ আপনাকে স্বাগতম।';

let profile = JSON.parse(localStorage.getItem('profile') ||
'{"name":"","phone":""}');

let admin = false;

function save(){
localStorage.setItem('balance',balance);
localStorage.setItem('offers',JSON.stringify(offers));
localStorage.setItem('orders',JSON.stringify(orders));
localStorage.setItem('requests',JSON.stringify(requests));
localStorage.setItem('notice',notice);
localStorage.setItem('profile',JSON.stringify(profile));
}

function showPage(id){

document.querySelectorAll('.page').forEach(p=>{
p.classList.remove('active');
});

document.getElementById(id).classList.add('active');

renderAll();
}

// BALANCE

function updateBalance(){

document.getElementById('balance').innerText=
'৳ '+balance.toFixed(2);

document.getElementById('profileBalance').innerText=
'৳ '+balance.toFixed(2);

}

// OPERATORS

function selectOperator(op){

document.getElementById('operatorFilter').value=op;

showPage('offers');

}

function findOperator(){

let number=document.getElementById('mobile').value;

if(!/^01[3-9]\d{8}$/.test(number)){
alert('সঠিক ১১ সংখ্যার বাংলাদেশি মোবাইল নম্বর লিখুন');
return;
}

let prefix=number.substring(0,3);

let map={
'013':'GP','017':'GP',
'014':'Banglalink','019':'Banglalink',
'018':'Robi','016':'Airtel',
'015':'Teletalk'
};

let op=map[prefix] || 'অজানা';

document.getElementById('operatorResult').innerText=
'সম্ভাব্য অপারেটর: '+op+
' | নম্বর: '+number+
' | প্রয়োজনে অপারেটর নিশ্চিত করুন।';

}

// OFFERS

function addOffer(){

let name=document.getElementById('newOfferName').value;

let price=Number(document.getElementById('newOfferPrice').value);

let validity=document.getElementById('newOfferValidity').value;

if(!name || price<=0 || !validity){
alert('সব তথ্য পূরণ করুন');
return;
}

offers.push({
id:Date.now(),
operator:document.getElementById('newOperator').value,
name:name,
price:price,
validity:validity,
type:document.getElementById('newOfferType').value
});

save();
renderAll();

alert('অফার যোগ হয়েছে');

}

function renderOffers(){

let filter=document.getElementById('operatorFilter').value;

let html='';

offers.filter(o=>filter==='all'||o.operator===filter)
.forEach(o=>{

html+=`
<div class="offer">
<h3>${escapeHTML(o.operator)} - ${escapeHTML(o.name)}</h3>
<p>ধরন: ${escapeHTML(o.type)}</p>
<p>মেয়াদ: ${escapeHTML(o.validity)}</p>
<p>মূল্য: ৳${o.price}</p>
<button onclick="buyOffer(${o.id})">অর্ডার করুন</button>
</div>
`;

});

document.getElementById('offerList').innerHTML=
html || 'এখনো কোনো অফার যোগ করা হয়নি।';

}

function renderHome(){

document.getElementById('homeOffers').innerHTML=
offers.slice(0,3).map(o=>`
<div class="offer">
<h3>${escapeHTML(o.name)}</h3>
<p>${escapeHTML(o.operator)} | ৳${o.price}</p>
</div>
`).join('') || 'কোনো অফার নেই।';

}

// ORDER

function buyOffer(id){

let offer=offers.find(o=>o.id===id);

if(!offer)return;

let phone=document.getElementById('mobile').value;

if(!/^01[3-9]\d{8}$/.test(phone)){
alert('প্রথমে সঠিক মোবাইল নম্বর লিখুন');
showPage('home');
return;
}

if(balance<offer.price){
alert('আপনার ব্যালেন্স পর্যাপ্ত নয়।');
showPage('addmoney');
return;
}

if(!confirm('৳'+offer.price+' দিয়ে অর্ডার করবেন?'))return;

balance-=offer.price;

orders.push({
id:Date.now(),
offer:offer.name,
phone:phone,
price:offer.price,
status:'Pending',
date:new Date().toLocaleString('bn-BD')
});

save();
renderAll();

alert('অর্ডার তৈরি হয়েছে। অ্যাডমিনের অনুমোদনের অপেক্ষায় আছে।');

}

function renderOrders(){

document.getElementById('orderList').innerHTML=
orders.map(o=>`
<div class="item">
<b>${escapeHTML(o.offer)}</b><br>
নম্বর: ${escapeHTML(o.phone)}<br>
মূল্য: ৳${o.price}<br>
অবস্থা: ${escapeHTML(o.status)}<br>
${escapeHTML(o.date)}
</div>
`).join('') || 'কোনো অর্ডার নেই।';

}

// ADD MONEY

function addMoneyRequest(){

let amount=Number(document.getElementById('amount').value);

let trx=document.getElementById('transaction').value;

if(amount<=0 || !trx){
alert('সঠিক তথ্য দিন');
return;
}

requests.push({
id:Date.now(),
amount:amount,
method:document.getElementById('paymentMethod').value,
trx:trx,
status:'Pending'
});

save();
renderAll();

alert('আপনার আবেদন জমা হয়েছে। যাচাইয়ের পর ব্যালেন্স যোগ হবে।');

}

// ADMIN

function adminLogin(){

let pin=document.getElementById('adminPin').value;

if(pin==='1234'){

admin=true;
showPage('admin');

}else{

alert('ভুল পিন');

}

}

function adminLogout(){

admin=false;
showPage('home');

}

function adminAddBalance(){

if(!admin)return;

let phone=document.getElementById('customerPhone').value;

let amount=Number(document.getElementById('customerAmount').value);

if(!phone || amount<=0){
alert('সঠিক তথ্য দিন');
return;
}

if(phone!==profile.phone){
alert('এই ডেমোতে শুধু বর্তমান প্রোফাইলের ব্যালেন্স পরিবর্তন করা যাবে।');
return;
}

balance+=amount;

save();
renderAll();

alert('ব্যালেন্স আপডেট হয়েছে');

}

function approveRequest(id){

let r=requests.find(x=>x.id===id);

if(!r || r.status!=='Pending')return;

r.status='Approved';

balance+=r.amount;

save();
renderAll();

}

function rejectRequest(id){

let r=requests.find(x=>x.id===id);

if(!r || r.status!=='Pending')return;

r.status='Rejected';

save();
renderAll();

}

function changeOrder(id,status){

let o=orders.find(x=>x.id===id);

if(!o)return;

o.status=status;

save();
renderAll();

}

// ADMIN OFFER LIST

function renderAdminOffers(){

document.getElementById('adminOfferList').innerHTML=
offers.map(o=>`
<div class="item">
<b>${escapeHTML(o.name)}</b> - ৳${o.price}
<br>${escapeHTML(o.operator)}
<br>
<button onclick="deleteOffer(${o.id})">ডিলিট</button>
</div>
`).join('') || 'কোনো অফার নেই';

}

function deleteOffer(id){

if(!confirm('অফার মুছে ফেলবেন?'))return;

offers=offers.filter(o=>o.id!==id);

save();
renderAll();

}

// REQUEST LIST

function renderRequests(){

document.getElementById('requestList').innerHTML=
requests.map(r=>`
<div class="item">
পদ্ধতি: ${escapeHTML(r.method)}<br>
পরিমাণ: ৳${r.amount}<br>
ট্রানজেকশন: ${escapeHTML(r.trx)}<br>
অবস্থা: ${escapeHTML(r.status)}
<br>
${r.status==='Pending'?`
<button onclick="approveRequest(${r.id})">অনুমোদন</button>
<button onclick="rejectRequest(${r.id})">বাতিল</button>
`:''}
</div>
`).join('') || 'কোনো আবেদন নেই';

}

// ADMIN ORDERS

function renderAdminOrders(){

document.getElementById('adminOrderList').innerHTML=
orders.map(o=>`
<div class="item">
<b>${escapeHTML(o.offer)}</b><br>
নম্বর: ${escapeHTML(o.phone)}<br>
মূল্য: ৳${o.price}<br>
অবস্থা: ${escapeHTML(o.status)}
<br>
<button onclick="changeOrder(${o.id},'Successful')">সম্পন্ন</button>
<button onclick="changeOrder(${o.id},'Cancelled')">বাতিল</button>
</div>
`).join('') || 'কোনো অর্ডার নেই';

}

// PROFILE

function saveProfile(){

profile.name=document.getElementById('userName').value;
profile.phone=document.getElementById('userPhone').value;

save();

alert('প্রোফাইল সংরক্ষিত হয়েছে');

}

// NOTICE

function updateNotice(){

notice=document.getElementById('newNotice').value;

save();

renderAll();

alert('নোটিশ আপডেট হয়েছে');

}

// SECURITY: TEXT DISPLAY

function escapeHTML(value){

return String(value).replace(/[&<>"']/g,c=>({
'&':'&amp;',
'<':'&lt;',
'>':'&gt;',
'"':'&quot;',
"'":'&#39;'
})[c]);

}

// RENDER ALL

function renderAll(){

updateBalance();

renderHome();

renderOffers();

renderOrders();

renderAdminOffers();

renderRequests();

renderAdminOrders();

document.getElementById('notice').innerText=notice;

document.getElementById('userName').value=profile.name;
document.getElementById('userPhone').value=profile.phone;

document.getElementById('totalOrders').innerText=orders.length;

document.getElementById('adminOrders').innerText=orders.length;

document.getElementById('adminSales').innerText=
'৳'+orders.filter(o=>o.status==='Successful')
.reduce((s,o)=>s+o.price,0);

document.getElementById('adminRequests').innerText=
requests.filter(r=>r.status==='Pending').length;

document.getElementById('adminCustomers').innerText=
profile.phone?1:0;

}

renderAll();

</script>
<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/13.4.0/firebase-app.js";
import { getFirestore, doc, getDoc } from "https://www.gstatic.com/firebasejs/13.4.0/firebase-firestore.js";

const firebaseConfig = {
  apiKey: "AIzaSyCxCr4NkVhnFi2cFRcvA9v8Djr1Df9_76Y",
  authDomain: "fahim-ahmad-telecom.firebaseapp.com",
  projectId: "fahim-ahmad-telecom",
  storageBucket: "fahim-ahmad-telecom.firebasestorage.app",
  messagingSenderId: "965841120853",
  appId: "1:965841120853:web:7fc6a75769a0fdfbd0eedc",
  measurementId: "G-N325EFWEXN"
};

const app = initializeApp(firebaseConfig);
const db = getFirestore(app);

window.firebaseApp = app;
window.db = db;

console.log("Firebase Connected!");

try {
  const result = await getDoc(doc(db, "users", "admin"));
  console.log("Database Connected!", result.exists());
} catch (error) {
  console.error("Database Error:", error);
}
</script>
</body>
</html> Fahim-Ahmad-Telecom
