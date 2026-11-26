<!DOCTYPE html>
<html lang="bn">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>FN Telecom</title>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
}

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

.auth-card h2{
color:#087b4e;
margin-bottom:10px;
}

.auth-card button{
width:100%;
}

#registerBtn{
background:#0755aa;
}

#authMessage{
margin-top:12px;
color:#d33;
}

#appScreen{
display:none;
padding-bottom:85px;
}

header{
background:#06452f;
color:white;
padding:22px;
text-align:center;
}

.container{
max-width:650px;
margin:auto;
padding:15px;
}

.card{
background:white;
padding:18px;
border-radius:16px;
margin-bottom:15px;
box-shadow:0 3px 12px #0001;
}

.title{
font-size:18px;
font-weight:bold;
margin-bottom:15px;
}

.page{
display:none;
}

.page.active{
display:block;
}

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

.operator span{
display:block;
font-size:25px;
margin-bottom:8px;
}

.offer{
padding:15px;
border:1px solid #e1eee5;
border-radius:12px;
margin-bottom:12px;
}

.offer h3{
color:#087b4e;
margin-bottom:8px;
}

.item{
padding:13px;
border-bottom:1px solid #eee;
font-size:14px;
}

.small{
font-size:12px;
color:#777;
}

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

.danger{
background:#d93636;
}

.logout{
background:#d93636;
width:100%;
}

.status{
color:#087b4e;
font-weight:bold;
}

</style>

</head>

<body>

<!-- LOGIN -->

<div id="authScreen">

<div class="auth-card">

<div style="font-size:45px">📱</div>

<h2>FN Telecom</h2>

<p>আপনার বিশ্বস্ত টেলিকম সেবা</p>

<br>

<input id="email" type="email"
placeholder="আপনার Email">

<input id="password" type="password"
placeholder="Password">

<button id="loginBtn">Login করুন</button>

<button id="registerBtn">নতুন Account খুলুন</button>

<p id="authMessage"></p>

</div>

</div>


<!-- APP -->

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

<input id="mobile"
type="tel"
maxlength="11"
placeholder="01XXXXXXXXX">

</div>

<div class="card">

<div class="title">📡 অপারেটর নির্বাচন</div>

<div class="grid">

<div class="operator"
onclick="selectOperator('GP')">
<span>🟢</span>GP
</div>

<div class="operator"
onclick="selectOperator('Banglalink')">
<span>🟠</span>Banglalink
</div>

<div class="operator"
onclick="selectOperator('Robi')">
<span>🔴</span>Robi
</div>

<div class="operator"
onclick="selectOperator('Airtel')">
<span>🔴</span>Airtel
</div>

<div class="operator"
onclick="selectOperator('Teletalk')">
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

<p id="notice"></p>

</div>

</div>


<!-- OFFERS -->

<div id="offers" class="page">

<div class="card">

<div class="title">📦 সকল অফার</div>

<select id="operatorFilter"
onchange="renderOffers()">

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

<input id="userName"
placeholder="আপনার নাম">

<input id="userPhone"
placeholder="মোবাইল নম্বর">

<p id="userEmail" class="small"></p>

<button onclick="saveProfile()">
তথ্য সংরক্ষণ
</button>

</div>

<div class="card">

<p>FN Telecom</p>

<p>WhatsApp: 01640592773</p>

<button onclick="window.open(
'https://wa.me/8801640592773')">

WhatsApp যোগাযোগ

</button>

<button class="logout"
onclick="logoutUser()">

Logout

</button>

</div>

</div>


<!-- ADMIN -->

<div id="admin" class="page">

<div class="card">

<div class="title">⚙️ FN Telecom Admin</div>

<h3>মোট অর্ডার:
<span id="adminOrders">0</span>
</h3>

<br>

<h3>সম্পন্ন অর্ডার:
<span id="adminSuccess">0</span>
</h3>

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

<input id="newOfferName"
placeholder="অফারের নাম">

<input id="newOfferPrice"
type="number"
placeholder="মূল্য">

<input id="newOfferValidity"
placeholder="মেয়াদ">

<button onclick="addOffer()">
অফার যোগ করুন
</button>

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

<input id="newNotice"
placeholder="নতুন নোটিশ">

<button onclick="updateNotice()">
নোটিশ প্রকাশ
</button>

</div>


<button class="logout"
onclick="showPage('profile')">

প্রোফাইলে ফিরে যান

</button>

</div>

</div>


<!-- MENU -->

<nav id="mainNav">

<button onclick="showPage('home')">
🏠<br>হোম
</button>

<button onclick="showPage('offers')">
📦<br>অফার
</button>

<button onclick="showPage('orders')">
📋<br>অর্ডার
</button>

<button onclick="showPage('profile')">
👤<br>প্রোফাইল
</button>

<button id="adminMenu"
style="display:none"
onclick="showPage('admin')">

⚙️<br>Admin

</button>

</nav>


<script type="module">

import {
initializeApp
} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-app.js";

import {
getAuth,
createUserWithEmailAndPassword,
signInWithEmailAndPassword,
onAuthStateChanged,
signOut,
sendEmailVerification
} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-auth.js";

import {
getFirestore,
collection,
addDoc,
getDocs,
query,
where,
orderBy,
onSnapshot,
doc,
setDoc,
updateDoc,
deleteDoc,
serverTimestamp
} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-firestore.js";


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


/* VARIABLES */

let currentUser = null;

let isAdmin = false;

let offers = [];

let orders = [];

let selectedOperator = 'all';

let unsubOffers = null;
let unsubOrders = null;
let unsubAdminOrders = null;
let unsubSettings = null;


/* ELEMENTS */

const authScreen =
document.getElementById('authScreen');

const appScreen =
document.getElementById('appScreen');

const message =
document.getElementById('authMessage');


/* REGISTER */

document.getElementById('registerBtn')
.onclick = async () => {

try {

let email =
document.getElementById('email').value.trim();

let password =
document.getElementById('password').value;

if(!email || password.length < 6){

message.innerText =
'সঠিক Email এবং কমপক্ষে ৬ অক্ষরের Password দিন';

return;

}

let result =
await createUserWithEmailAndPassword(
auth,email,password
);

await sendEmailVerification(result.user);

message.innerText =
'Account তৈরি হয়েছে। Email যাচাই করে Login করুন।';

} catch(error){

message.innerText = error.message;

}

};


/* LOGIN */

document.getElementById('loginBtn')
.onclick = async () => {

try{

let email =
document.getElementById('email').value.trim();

let password =
document.getElementById('password').value;

await signInWithEmailAndPassword(
auth,email,password
);

message.innerText = '';

}catch(error){

message.innerText = error.message;

}

};


/* AUTH */

onAuthStateChanged(auth, async user => {

if(user){

currentUser = user;

await user.reload();

await user.getIdToken(true);

isAdmin =
user.email === 'faiyaazfahim608@gmail.com'
&& user.emailVerified;

authScreen.style.display = 'none';

appScreen.style.display = 'block';

document.getElementById('userEmail')
.innerText = user.email;

document.getElementById('adminMenu')
.style.display = isAdmin ? 'block' : 'none';

loadData();

showPage('home');

}else{

currentUser = null;

isAdmin = false;

cleanupListeners();

authScreen.style.display = 'flex';

appScreen.style.display = 'none';

}

});


/* CLEANUP */

function cleanupListeners(){

[
'unsubOffers',
'unsubOrders',
'unsubAdminOrders',
'unsubSettings'
].forEach(name => {

if(window[name]){
window[name]();
window[name] = null;
}

});

}


/* LOGOUT */

window.logoutUser = async () => {

await signOut(auth);

};


/* PAGE */

window.showPage = function(id){

if(id === 'admin' && !isAdmin){

alert('Admin অনুমতি নেই');

return;

}

document.querySelectorAll('.page')
.forEach(p => p.classList.remove('active'));

document.getElementById(id)
.classList.add('active');

};


/* LOAD DATA */

function loadData(){

cleanupListeners();

loadOffers();

loadMyOrders();

loadProfile();

loadNotice();

if(isAdmin){

loadAdminOrders();

}

}


/* OFFERS */

function loadOffers(){

unsubOffers = onSnapshot(
collection(db,'offers'),

snapshot => {

offers = snapshot.docs.map(d => ({
id:d.id,
...d.data()
}));

renderOffers();

renderHomeOffers();

if(isAdmin) renderAdminOffers();

},

error => alert('অফার লোড হয়নি: '+error.message)

);

}


/* RENDER OFFERS */

window.renderOffers = function(){

let filter =
document.getElementById('operatorFilter').value;

document.getElementById('offerList')
.innerHTML = offers

.filter(o =>
filter === 'all' ||
o.operator === filter
)

.map(o => `

<div class="offer">

<h3>${escapeHTML(o.name)}</h3>

<p>অপারেটর: ${escapeHTML(o.operator)}</p>

<p>মেয়াদ: ${escapeHTML(o.validity)}</p>

<p>মূল্য: ৳${Number(o.price)}</p>

<button onclick="buyOffer('${o.id}')">

অর্ডার করুন

</button>

</div>

`).join('') || 'কোনো অফার নেই।';

};


/* HOME OFFERS */

function renderHomeOffers(){

document.getElementById('homeOffers')
.innerHTML = offers.slice(0,3)

.map(o => `

<div class="offer">

<h3>${escapeHTML(o.name)}</h3>

<p>${escapeHTML(o.operator)}</p>

<p>৳${Number(o.price)}</p>

<button onclick="buyOffer('${o.id}')">
অর্ডার করুন
</button>

</div>

`).join('') || 'কোনো অফার নেই।';

}


/* BUY OFFER */

window.buyOffer = async function(id){

let offer = offers.find(o => o.id === id);

if(!offer) return;

let phone =
document.getElementById('mobile').value.trim();

if(!/^01[3-9]\d{8}$/.test(phone)){

alert('সঠিক ১১ ডিজিটের মোবাইল নম্বর লিখুন');

showPage('home');

return;

}

if(!confirm(
offer.name+' অর্ডার করবেন?'
)) return;

try{

await addDoc(collection(db,'orders'),{

userId:currentUser.uid,

userEmail:currentUser.email,

offer:offer.name,

operator:offer.operator,

phone:phone,

price:Number(offer.price),

status:'Pending',

createdAt:serverTimestamp()

});

alert('অর্ডার সফলভাবে জমা হয়েছে!');

showPage('orders');

}catch(error){

alert('অর্ডার জমা হয়নি: '+error.message);

}

};


/* MY ORDERS */

function loadMyOrders(){

let q = query(

collection(db,'orders'),

where('userId','==',currentUser.uid),

orderBy('createdAt','desc')

);

unsubOrders = onSnapshot(q,snapshot => {

orders = snapshot.docs.map(d => ({
id:d.id,
...d.data()
}));

renderMyOrders();

},error => {

console.error(error);

});

}


function renderMyOrders(){

document.getElementById('orderList')
.innerHTML = orders.map(o => `

<div class="item">

<b>${escapeHTML(o.offer)}</b>

<br>

অপারেটর: ${escapeHTML(o.operator)}

<br>

নম্বর: ${escapeHTML(o.phone)}

<br>

মূল্য: ৳${Number(o.price)}

<br>

অবস্থা:

<span class="status">
${escapeHTML(o.status)}
</span>

</div>

`).join('') || 'এখনো কোনো অর্ডার নেই।';

}


/* ADMIN ORDERS */

function loadAdminOrders(){

unsubAdminOrders = onSnapshot(

query(
collection(db,'orders'),
orderBy('createdAt','desc')
),

snapshot => {

let all = snapshot.docs.map(d => ({
id:d.id,
...d.data()
}));

document.getElementById('adminOrders')
.innerText = all.length;

document.getElementById('adminSuccess')
.innerText = all.filter(
o => o.status === 'Successful'
).length;

document.getElementById('adminOrderList')
.innerHTML = all.map(o => `

<div class="item">

<b>${escapeHTML(o.offer)}</b>

<br>

কাস্টমার: ${escapeHTML(o.userEmail)}

<br>

মোবাইল: <b>${escapeHTML(o.phone)}</b>

<br>

অপারেটর: ${escapeHTML(o.operator)}

<br>

মূল্য: ৳${Number(o.price)}

<br>

অবস্থা: ${escapeHTML(o.status)}

<br>

${o.status === 'Pending' ? `

<button onclick="changeOrder('${o.id}','Successful')">
Successful
</button>

<button class="danger"
onclick="changeOrder('${o.id}','Cancelled')">
Cancelled
</button>

` : ''}

</div>

`).join('') || 'কোনো অর্ডার নেই।';

},

error => alert('Admin Order Error: '+error.message)

);

}


/* CHANGE ORDER */

window.changeOrder = async function(id,status){

if(!isAdmin){

alert('অনুমতি নেই');

return;

}

try{

await updateDoc(doc(db,'orders',id),{

status:status

});

alert('অর্ডার আপডেট হয়েছে');

}catch(error){

alert(error.message);

}

};


/* ADD OFFER */

window.addOffer = async function(){

if(!isAdmin) return;

let name =
document.getElementById('newOfferName').value.trim();

let price =
Number(document.getElementById('newOfferPrice').value);

let validity =
document.getElementById('newOfferValidity').value.trim();

let operator =
document.getElementById('newOperator').value;

if(!name || price <= 0 || !validity){

alert('সব তথ্য পূরণ করুন');

return;

}

try{

await addDoc(collection(db,'offers'),{

name,
price,
validity,
operator,
createdAt:serverTimestamp()

});

document.getElementById('newOfferName').value='';

document.getElementById('newOfferPrice').value='';

document.getElementById('newOfferValidity').value='';

alert('নতুন অফার যোগ হয়েছে');

}catch(error){

alert(error.message);

}

};


/* ADMIN OFFER LIST */

function renderAdminOffers(){

document.getElementById('adminOfferList')
.innerHTML = offers.map(o => `

<div class="item">

${escapeHTML(o.name)}

<br>

${escapeHTML(o.operator)}

<br>

৳${Number(o.price)}

<button class="danger"
onclick="deleteOffer('${o.id}')">

ডিলিট

</button>

</div>

`).join('') || 'কোনো অফার নেই।';

}


/* DELETE OFFER */

window.deleteOffer = async function(id){

if(!isAdmin) return;

if(!confirm('অফার মুছে ফেলবেন?')) return;

try{

await deleteDoc(doc(db,'offers',id));

alert('অফার মুছে ফেলা হয়েছে');

}catch(error){

alert(error.message);

}

};


/* PROFILE */

async function loadProfile(){

let ref = doc(db,'users',currentUser.uid);

let snap = await getDoc(ref);

if(snap.exists()){

let data = snap.data();

document.getElementById('userName').value =
data.name || '';

document.getElementById('userPhone').value =
data.phone || '';

}

}


window.saveProfile = async function(){

let name =
document.getElementById('userName').value.trim();

let phone =
document.getElementById('userPhone').value.trim();

try{

await setDoc(
doc(db,'users',currentUser.uid),

{
name,
phone,
email:currentUser.email
},

{merge:true}

);

alert('প্রোফাইল সংরক্ষিত হয়েছে');

}catch(error){

alert(error.message);

}

};


/* NOTICE */

function loadNotice(){

unsubSettings = onSnapshot(
doc(db,'settings','notice'),

snap => {

document.getElementById('notice')
.innerText = snap.exists()
? snap.data().text
: 'FN Telecom-এ আপনাকে স্বাগতম।';

}

);


}


window.updateNotice = async function(){

if(!isAdmin) return;

let text =
document.getElementById('newNotice').value.trim();

if(!text) return alert('নোটিশ লিখুন');

try{

await setDoc(
doc(db,'settings','notice'),
{text}
);

alert('নোটিশ প্রকাশ হয়েছে');

}catch(error){

alert(error.message);

}

};


/* HTML SECURITY */

function escapeHTML(v){

return String(v ?? '').replace(/[&<>"']/g,c=>({

'&':'&amp;',
'<':'&lt;',
'>':'&gt;',
'"':'&quot;',
"'":'&#39;'

})[c]);

}


/* OPERATOR */

window.selectOperator = function(op){

document.getElementById('operatorFilter').value = op;

showPage('offers');

};

</script>

</body>
</html>
