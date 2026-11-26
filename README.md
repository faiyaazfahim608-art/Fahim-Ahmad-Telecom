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
color:#173629;
}

button{
border:0;
padding:13px;
border-radius:10px;
background:#087b4e;
color:white;
font-size:15px;
cursor:pointer;
margin:5px 0;
}

input,select{
width:100%;
padding:14px;
margin:8px 0;
border:1px solid #ddd;
border-radius:10px;
font-size:15px;
}

#authScreen{
min-height:100vh;
display:flex;
align-items:center;
justify-content:center;
padding:20px;
background:linear-gradient(135deg,#043b29,#07945a);
}

.auth-card{
width:100%;
max-width:380px;
background:white;
padding:30px 25px;
border-radius:22px;
text-align:center;
}

.auth-card h2{color:#087b4e;margin-bottom:10px}
.auth-card button{width:100%}
#registerBtn{background:#0755aa}
#authMessage{margin-top:12px;color:#d33}

#appScreen{display:none;padding-bottom:85px}

header{
background:#06452f;
color:white;
padding:22px;
text-align:center;
}

.container{max-width:650px;margin:auto;padding:15px}

.card{
background:white;
padding:18px;
border-radius:16px;
margin-bottom:15px;
box-shadow:0 3px 12px #0001;
}

.title{font-size:18px;font-weight:bold;margin-bottom:15px}

.page{display:none}
.page.active{display:block}

.grid{
display:grid;
grid-template-columns:repeat(2,1fr);
gap:12px;
}

.operator{
background:#f1f8f3;
padding:20px 5px;
border-radius:12px;
text-align:center;
cursor:pointer;
font-weight:bold;
}

.operator span{display:block;font-size:25px;margin-bottom:8px}

.offer{
padding:15px;
border:1px solid #e1eee5;
border-radius:12px;
margin-bottom:12px;
}

.offer h3{color:#087b4e;margin-bottom:8px}

.item{padding:13px;border-bottom:1px solid #eee;font-size:14px}
.small{font-size:12px;color:#777}

nav{
position:fixed;
bottom:0;
left:0;
width:100%;
display:flex;
justify-content:space-around;
background:white;
padding:9px 2px;
box-shadow:0 -3px 12px #0002;
z-index:10;
}

nav button{
background:transparent;
color:#174c37;
font-size:11px;
padding:5px;
}

.danger{background:#d93636}
.orange{background:#df8b15}
.blue{background:#0755aa}
.logout{background:#d93636;width:100%}
.status{color:#087b4e;font-weight:bold}
.hidden{display:none!important}
</style>
</head>

<body>

<div id="authScreen">
<div class="auth-card">

<div style="font-size:45px">📱</div>
<h2>FN Telecom</h2>
<p>আপনার বিশ্বস্ত টেলিকম সেবা</p>

<br>

<input id="email" type="email" placeholder="আপনার Email">
<input id="password" type="password" placeholder="Password">

<button id="loginBtn">Login করুন</button>
<button id="registerBtn">নতুন Account খুলুন</button>

<p id="authMessage"></p>

</div>
</div>

<div id="appScreen">

<header>
<h1>🟢 FN Telecom</h1>
<p>আপনার বিশ্বস্ত টেলিকম সেবা</p>
</header>

<div class="container">

<!-- HOME -->

<div id="home" class="page active">

<div class="card">
<div class="title">📱 মোবাইল নম্বর</div>
<input id="mobile" type="tel" maxlength="11" placeholder="01XXXXXXXXX">
</div>

<div class="card">
<div class="title">📡 অপারেটর নির্বাচন</div>

<div class="grid">

<div class="operator" onclick="selectOperator('GP')">
<span>🟢</span>GP
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
<div class="title">📢 নোটিশ</div>
<p id="notice">স্বাগতম FN Telecom</p>
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

<p id="userEmail" class="small"></p>

<button onclick="saveProfile()">তথ্য সংরক্ষণ</button>
</div>

<div class="card">
<p>FN Telecom</p>
<p>WhatsApp: 01640592773</p>

<button onclick="window.open('https://wa.me/8801640592773')">
WhatsApp যোগাযোগ
</button>

<button class="logout" onclick="logoutUser()">Logout</button>
</div>

</div>

<!-- ADMIN -->

<div id="admin" class="page">

<div class="card">
<div class="title">⚙️ FN Telecom Admin</div>

<h3>মোট অর্ডার: <span id="adminOrders">0</span></h3>
<br>
<h3>সম্পন্ন অর্ডার: <span id="adminSuccess">0</span></h3>
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
<input id="newOfferPrice" type="number" min="0" placeholder="তোমার নির্ধারিত মূল্য">
<input id="newOfferValidity" placeholder="মেয়াদ">

<button onclick="addOffer()">অফার যোগ করুন</button>

</div>

<div class="card">
<div class="title">📦 অফার পরিচালনা</div>
<div id="adminOfferList"></div>
</div>

<div class="card">
<div class="title">📋 সকল কাস্টমার অর্ডার</div>
<div id="adminOrderList"></div>
</div>

<div class="card">
<div class="title">📢 নোটিশ পরিবর্তন</div>
<input id="newNotice" placeholder="নতুন নোটিশ">
<button onclick="updateNotice()">নোটিশ প্রকাশ</button>
</div>

</div>

</div>

<nav id="mainNav">

<button onclick="showPage('home')">🏠<br>হোম</button>
<button onclick="showPage('offers')">📦<br>অফার</button>
<button onclick="showPage('orders')">📋<br>অর্ডার</button>
<button onclick="showPage('profile')">👤<br>প্রোফাইল</button>

<button id="adminMenu" style="display:none"
onclick="showPage('admin')">⚙️<br>Admin</button>

</nav>

</div>

<script type="module">

import {initializeApp}
from "https://www.gstatic.com/firebasejs/13.4.0/firebase-app.js";

import {
getAuth,
createUserWithEmailAndPassword,
signInWithEmailAndPassword,
onAuthStateChanged,
signOut,
sendEmailVerification
}
from "https://www.gstatic.com/firebasejs/13.4.0/firebase-auth.js";

import {
getFirestore,
collection,
addDoc,
getDoc,
getDocs,
query,
where,
onSnapshot,
doc,
setDoc,
updateDoc,
deleteDoc,
serverTimestamp
}
from "https://www.gstatic.com/firebasejs/13.4.0/firebase-firestore.js";


/* FIREBASE CONFIG */

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
const auth = getAuth(app);
const db = getFirestore(app);


/* ADMIN */

const ADMIN_EMAIL = "faiyaazfahim608@gmail.com";

let currentUser = null;
let isAdmin = false;
let offers = [];
let orders = [];
let selectedOffer = null;

let unsubOffers = null;
let unsubOrders = null;
let unsubAdminOrders = null;
let unsubSettings = null;


/* REGISTER */

document.getElementById('registerBtn').onclick = async()=>{

try{

const email = document.getElementById('email').value.trim();
const password = document.getElementById('password').value;

if(!email || password.length<6){
alert('সঠিক Email এবং কমপক্ষে ৬ অক্ষরের Password দিন');
return;
}

const result = await createUserWithEmailAndPassword(auth,email,password);

await sendEmailVerification(result.user);

alert('Account তৈরি হয়েছে। Email যাচাই করে Login করুন।');

await signOut(auth);

}catch(e){
alert(e.message);
}

};


/* LOGIN */

document.getElementById('loginBtn').onclick = async()=>{

try{

const email = document.getElementById('email').value.trim();
const password = document.getElementById('password').value;

await signInWithEmailAndPassword(auth,email,password);

}catch(e){
alert(e.message);
}

};


/* AUTH STATE */

onAuthStateChanged(auth,async user=>{

cleanup();

if(!user){

currentUser=null;
isAdmin=false;

document.getElementById('authScreen').style.display='flex';
document.getElementById('appScreen').style.display='none';

return;

}

await user.reload();

currentUser=auth.currentUser;

isAdmin =
currentUser.email?.toLowerCase() === ADMIN_EMAIL.toLowerCase()
&& currentUser.emailVerified;

if(!currentUser.emailVerified){

alert('প্রথমে Email Verification সম্পন্ন করুন।');
await signOut(auth);
return;

}

document.getElementById('authScreen').style.display='none';
document.getElementById('appScreen').style.display='block';

document.getElementById('userEmail').innerText=currentUser.email;

document.getElementById('adminMenu').style.display=
isAdmin?'block':'none';

loadOffers();
loadMyOrders();
loadProfile();
loadNotice();

if(isAdmin){
loadAdminOrders();
}

showPage('home');

});


/* CLEANUP */

function cleanup(){

if(unsubOffers){unsubOffers();unsubOffers=null;}
if(unsubOrders){unsubOrders();unsubOrders=null;}
if(unsubAdminOrders){unsubAdminOrders();unsubAdminOrders=null;}
if(unsubSettings){unsubSettings();unsubSettings=null;}

}

window.logoutUser=()=>signOut(auth);


/* PAGE */

window.showPage=function(id){

if(id==='admin' && !isAdmin){
alert('Admin অনুমতি নেই');
return;
}

document.querySelectorAll('.page').forEach(p=>{
p.classList.remove('active');
});

document.getElementById(id).classList.add('active');

};


/* SAFE TEXT */

function esc(v){

return String(v??'').replace(/[&<>"']/g,c=>({
'&':'&amp;',
'<':'&lt;',
'>':'&gt;',
'"':'&quot;',
"'":'&#39;'
})[c]);

}


/* LOAD OFFERS */

function loadOffers(){

unsubOffers=onSnapshot(collection(db,'offers'),snapshot=>{

offers=snapshot.docs.map(d=>({
id:d.id,
...d.data()
}));

renderOffers();
renderHomeOffers();

if(isAdmin)renderAdminOffers();

},error=>alert('অফার লোড সমস্যা: '+error.message));

}


/* RENDER OFFERS */

window.renderOffers=function(){

const filter=document.getElementById('operatorFilter').value;

document.getElementById('offerList').innerHTML=

offers.filter(o=>
o.active!==false &&
(filter==='all'||o.operator===filter)
).map(o=>`

<div class="offer">

<h3>${esc(o.name)}</h3>
<p>অপারেটর: ${esc(o.operator)}</p>
<p>মেয়াদ: ${esc(o.validity)}</p>
<p><b>মূল্য: ৳${Number(o.price)}</b></p>

<button onclick="buyOffer('${o.id}')">অর্ডার করুন</button>

</div>

`).join('')||'কোনো অফার নেই।';

};


/* HOME OFFERS */

function renderHomeOffers(){

document.getElementById('homeOffers').innerHTML=

offers.filter(o=>o.active!==false).slice(0,3).map(o=>`

<div class="offer">

<h3>${esc(o.name)}</h3>
<p>${esc(o.operator)}</p>
<p>৳${Number(o.price)}</p>

<button onclick="buyOffer('${o.id}')">অর্ডার করুন</button>

</div>

`).join('')||'কোনো অফার নেই।';

}


/* OPERATOR */

window.selectOperator=function(op){

document.getElementById('operatorFilter').value=op;
showPage('offers');

};


/* BUY OFFER */

window.buyOffer=async function(id){

const offer=offers.find(o=>o.id===id && o.active!==false);

if(!offer)return;

const phone=document.getElementById('mobile').value.trim();

if(!/^01[3-9]\d{8}$/.test(phone)){
alert('সঠিক ১১ ডিজিটের মোবাইল নম্বর লিখুন।');
showPage('home');
return;
}

if(!confirm(offer.name+' অর্ডার করবেন?'))return;

try{

await addDoc(collection(db,'orders'),{

userId:currentUser.uid,
userEmail:currentUser.email,
offerId:id,
offer:offer.name,
operator:offer.operator,
phone:phone,
price:Number(offer.price),
status:'Pending',
createdAt:serverTimestamp()

});

alert('অর্ডার সফলভাবে জমা হয়েছে!');
showPage('orders');

}catch(e){
alert('অর্ডার জমা হয়নি: '+e.message);
}

};


/* MY ORDERS */

function loadMyOrders(){

const q=query(
collection(db,'orders'),
where('userId','==',currentUser.uid)
);

unsubOrders=onSnapshot(q,snapshot=>{

orders=snapshot.docs.map(d=>({
id:d.id,
...d.data()
}));

orders.sort((a,b)=>
(b.createdAt?.seconds||0)-(a.createdAt?.seconds||0)
);

renderMyOrders();

},error=>console.error(error));

}


function renderMyOrders(){

document.getElementById('orderList').innerHTML=

orders.map(o=>`

<div class="item">

<b>${esc(o.offer)}</b><br>
অপারেটর: ${esc(o.operator)}<br>
নম্বর: ${esc(o.phone)}<br>
মূল্য: ৳${Number(o.price)}<br>

অবস্থা: <span class="status">${esc(o.status)}</span>

</div>

`).join('')||'এখনো কোনো অর্ডার নেই।';

}


/* ADMIN ORDERS */

function loadAdminOrders(){

if(!isAdmin)return;

unsubAdminOrders=onSnapshot(collection(db,'orders'),snapshot=>{

const all=snapshot.docs.map(d=>({
id:d.id,
...d.data()
}));

all.sort((a,b)=>
(b.createdAt?.seconds||0)-(a.createdAt?.seconds||0)
);

document.getElementById('adminOrders').innerText=all.length;

document.getElementById('adminSuccess').innerText=
all.filter(o=>o.status==='Successful').length;

document.getElementById('adminOrderList').innerHTML=

all.map(o=>`

<div class="item">

<b>${esc(o.offer)}</b><br>
কাস্টমার: ${esc(o.userEmail)}<br>
মোবাইল: <b>${esc(o.phone)}</b><br>
অপারেটর: ${esc(o.operator)}<br>
মূল্য: ৳${Number(o.price)}<br>
অবস্থা: ${esc(o.status)}<br>

${o.status==='Pending'?`

<button onclick="changeOrder('${o.id}','Successful')">
MB পাঠানো হয়েছে - Confirm
</button>

<button class="danger" onclick="changeOrder('${o.id}','Cancelled')">
Cancel
</button>

`:''}

</div>

`).join('')||'কোনো অর্ডার নেই।';

},error=>alert('অর্ডার লোড সমস্যা: '+error.message));

}


/* UPDATE ORDER */

window.changeOrder=async function(id,status){

if(!isAdmin)return alert('অনুমতি নেই');

if(!confirm('অর্ডারের অবস্থা পরিবর্তন করবেন?'))return;

try{

await updateDoc(doc(db,'orders',id),{status});

alert('অর্ডার আপডেট হয়েছে');

}catch(e){
alert(e.message);
}

};


/* ADD OFFER */

window.addOffer=async function(){

if(!isAdmin)return;

const name=document.getElementById('newOfferName').value.trim();
const priceInput=document.getElementById('newOfferPrice').value;
const price=Number(priceInput);
const validity=document.getElementById('newOfferValidity').value.trim();
const operator=document.getElementById('newOperator').value;

if(!name||priceInput===''||!Number.isFinite(price)||price<0||!validity){
alert('সব তথ্য সঠিকভাবে পূরণ করুন।');
return;
}

try{

await addDoc(collection(db,'offers'),{

name,
price,
validity,
operator,
active:true,
createdAt:serverTimestamp()

});

document.getElementById('newOfferName').value='';
document.getElementById('newOfferPrice').value='';
document.getElementById('newOfferValidity').value='';

alert('নতুন অফার যোগ হয়েছে!');

}catch(e){
alert(e.message);
}

};


/* ADMIN OFFER LIST */

function renderAdminOffers(){

document.getElementById('adminOfferList').innerHTML=

offers.map(o=>`

<div class="offer">

<h3>${esc(o.name)}</h3>
<p>অপারেটর: ${esc(o.operator)}</p>
<p>দাম: ৳${Number(o.price)}</p>
<p>মেয়াদ: ${esc(o.validity)}</p>
<p>অবস্থা: ${o.active===false?'বন্ধ':'চালু'}</p>

<button class="blue" onclick="editOffer('${o.id}')">সম্পাদনা</button>

<button class="orange" onclick="toggleOffer('${o.id}',${o.active===false})">
${o.active===false?'চালু করুন':'বন্ধ করুন'}
</button>

<button class="danger" onclick="deleteOffer('${o.id}')">ডিলিট</button>

</div>

`).join('')||'কোনো অফার নেই।';

}


/* EDIT OFFER */

window.editOffer=async function(id){

if(!isAdmin)return;

const o=offers.find(x=>x.id===id);
if(!o)return;

const name=prompt('অফারের নাম:',o.name);
if(name===null)return;

const priceText=prompt('নতুন দাম:',o.price);
if(priceText===null)return;

const price=Number(priceText);

if(!name.trim()||priceText.trim()===''||!Number.isFinite(price)||price<0){
alert('সঠিক তথ্য দিন।');
return;
}

const validity=prompt('মেয়াদ:',o.validity);
if(validity===null)return;

try{

await updateDoc(doc(db,'offers',id),{
name:name.trim(),
price,
validity:validity.trim()
});

alert('অফার পরিবর্তন হয়েছে');

}catch(e){
alert(e.message);
}

};


/* TOGGLE OFFER */

window.toggleOffer=async function(id,value){

if(!isAdmin)return;

try{

await updateDoc(doc(db,'offers',id),{
active:value
});

}catch(e){
alert(e.message);
}

};


/* DELETE OFFER */

window.deleteOffer=async function(id){

if(!isAdmin)return;

if(!confirm('অফার ডিলিট করবেন?'))return;

try{

await deleteDoc(doc(db,'offers',id));

alert('অফার ডিলিট হয়েছে');

}catch(e){
alert(e.message);
}

};


/* PROFILE */

async function loadProfile(){

try{

const snap=await getDoc(doc(db,'users',currentUser.uid));

if(snap.exists()){

const data=snap.data();

document.getElementById('userName').value=data.name||'';
document.getElementById('userPhone').value=data.phone||'';

}

}catch(e){
console.error(e);
}

}


window.saveProfile=async function(){

try{

await setDoc(doc(db,'users',currentUser.uid),{

name:document.getElementById('userName').value.trim(),
phone:document.getElementById('userPhone').value.trim(),
email:currentUser.email

},{merge:true});

alert('প্রোফাইল সংরক্ষিত হয়েছে');

}catch(e){
alert(e.message);
}

};


/* NOTICE */

function loadNotice(){

unsubSettings=onSnapshot(doc(db,'settings','notice'),snap=>{

document.getElementById('notice').innerText=
snap.exists()?snap.data().text:'FN Telecom-এ আপনাকে স্বাগতম।';

},error=>console.error(error));

}


window.updateNotice=async function(){

if(!isAdmin)return;

const text=document.getElementById('newNotice').value.trim();

if(!text)return alert('নোটিশ লিখুন');

try{

await setDoc(doc(db,'settings','notice'),{text});

document.getElementById('newNotice').value='';

alert('নোটিশ প্রকাশ হয়েছে');

}catch(e){
alert(e.message);
}

};

</script>

</body>
</html>
