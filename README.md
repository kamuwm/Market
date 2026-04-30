<!DOCTYPE html>
<html lang="sw">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Muble - Nunua Uza Online</title>
<style>
:root{--blue:#2563eb;--green:#16a34a;--bg:#f1f5f9;--card:#fff;--text:#1e293b;--gray:#64748b;--red:#dc2626}
*{margin:0;padding:0;box-sizing:border-box;font-family:'Segoe UI',Arial}
body{background:var(--bg);color:var(--text);padding-bottom:80px}
header{background:var(--card);padding:12px 4%;display:flex;justify-content:space-between;align-items:center;box-shadow:0 1px 3px rgba(0,0,0,0.1);position:sticky;top:0;z-index:50}
.logo{font-weight:800;font-size:22px;color:var(--blue)}
.profile{width:32px;height:32px;border-radius:50%;background:var(--blue);color:#fff;display:flex;align-items:center;justify-content:center;font-weight:bold;cursor:pointer}
.container{width:94%;max-width:1200px;margin:15px auto}
.page{display:none}
.page.active{display:block}
.hero{background:linear-gradient(135deg,var(--blue),#1e40af);color:#fff;padding:20px;border-radius:12px;margin-bottom:15px;box-shadow:0 4px 6px rgba(0,0,0,0.1)}
.hero h1{font-size:20px;margin-bottom:5px}
.hero p{opacity:0.9;font-size:14px}
.ad-box{background:#fef3c7;border:1px solid #fbbf24;padding:12px;border-radius:8px;margin-bottom:15px;font-size:14px}
.search-bar{width:100%;padding:12px 15px;border:1px solid #cbd5e1;border-radius:25px;font-size:15px;margin-bottom:15px;background:var(--card)}
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));gap:15px}
.product{background:var(--card);border-radius:12px;overflow:hidden;box-shadow:0 1px 3px rgba(0,0,0,0.1);cursor:pointer}
.product img{width:100%;height:140px;object-fit:cover}
.product-info{padding:10px}
.product-info h3{font-size:15px;margin-bottom:4px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.price{color:var(--blue);font-weight:700;font-size:16px}
.location{font-size:12px;color:var(--gray);margin-top:4px}
.bottom-nav{position:fixed;bottom:0;left:0;right:0;background:var(--card);display:flex;justify-content:space-around;padding:8px 0;box-shadow:0 -1px 3px rgba(0,0,0,0.1);z-index:50}
.nav-item{display:flex;flex-direction:column;align-items:center;font-size:11px;color:var(--gray);text-decoration:none;border:none;background:none}
.nav-item.active{color:var(--blue)}
.nav-item svg{width:24px;height:24px;margin-bottom:2px}
.add-btn{background:var(--blue);width:50px;height:50px;border-radius:50%;display:flex;align-items:center;justify-content:center;margin-top:-25px;border:4px solid var(--bg)}
.add-btn svg{color:#fff}
.modal{position:fixed;inset:0;background:rgba(0,0,0,0.5);display:none;align-items:center;justify-content:center;z-index:100;padding:15px}
.modal.active{display:flex}
.modal-content{background:var(--card);width:100%;max-width:500px;border-radius:12px;max-height:90vh;overflow-y:auto}
.modal-header{padding:15px;border-bottom:1px solid #e2e8f0;display:flex;justify-content:space-between;align-items:center}
.modal-body{padding:15px}
input,textarea,select{width:100%;padding:10px;margin:8px 0;border:1px solid #cbd5e1;border-radius:8px;font-size:15px}
textarea{resize:vertical;min-height:80px}
.btn{background:var(--blue);color:#fff;border:none;padding:12px;border-radius:8px;font-weight:600;cursor:pointer;width:100%}
.btn-green{background:var(--green)}
.btn-red{background:var(--red)}
.btn:disabled{background:#94a3b8}
.img-preview{display:flex;gap:8px;margin:10px 0;flex-wrap:wrap}
.img-preview img{width:70px;height:70px;object-fit:cover;border-radius:8px;border:2px solid #e2e8f0}
.img-box{position:relative}
.img-box button{position:absolute;top:-5px;right:-5px;background:red;color:#fff;border:none;border-radius:50%;width:20px;height:20px;font-size:12px;cursor:pointer}
.view-img{width:100%;height:250px;object-fit:cover;border-radius:8px}
.view-details h2{margin:10px 0 5px 0}
.view-meta{display:flex;gap:15px;margin:10px 0;font-size:14px;color:var(--gray);flex-wrap:wrap}
.contact-box{background:#eff6ff;padding:12px;border-radius:8px;margin:15px 0}
.contact-box a{color:var(--blue);text-decoration:none;font-weight:600}
.empty{text-align:center;padding:40px 20px;color:var(--gray)}
#msg{position:fixed;top:70px;left:50%;transform:translateX(-50%);background:#10b981;color:#fff;padding:10px 20px;border-radius:8px;z-index:200;display:none}
.tabs{display:flex;margin-bottom:15px;background:#e2e8f0;border-radius:8px;padding:3px}
.tab{flex:1;padding:8px;border:none;background:none;cursor:pointer;border-radius:6px;font-weight:600}
.tab.active{background:var(--card);color:var(--blue)}
.payment-methods{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin:15px 0}
.payment-item{border:2px solid #e2e8f0;padding:12px;border-radius:8px;cursor:pointer;text-align:center}
.payment-item.active{border-color:var(--blue);background:#eff6ff}
.profile-card{background:var(--card);padding:20px;border-radius:12px;margin-bottom:15px;text-align:center}
.profile-card h3{margin:10px 0 5px 0}
.profile-stats{display:flex;justify-content:space-around;margin:15px 0}
.my-product{border:1px solid #e2e8f0;padding:10px;border-radius:8px;margin:8px 0;display:flex;justify-content:space-between;align-items:center}
</style>
</head>
<body>
<header>
    <div class="logo">Muble</div>
    <div class="profile" id="profile-icon" onclick="checkProfileAccess()">U</div>
</header>

<div id="msg"></div>

<div class="container">
    <!-- HOME PAGE -->
    <div id="home" class="page active">
        <div class="hero">
            <h1>Muble Market</h1>
            <p>Nunua na uza bidhaa kwa urahisi Tanzania nzima</p>
        </div>
        <div class="ad-box">
            📢 <b>Matangazo ya Huduma:</b> Unauza bidhaa? Weka hapa bure! Wateja 2000+ wanatazama kila siku. Tuma bidhaa yako sasa kupitia + hapo chini. Muble inakusaidia kufikia wateja haraka.
        </div>
        <input type="text" class="search-bar" id="search" placeholder="🔍 Tafuta bidhaa, location..." onkeyup="searchProducts()">
        <h3 style="margin-bottom:10px">Bidhaa Mpya</h3>
        <div class="grid" id="products-grid"></div>
        <div id="home-empty" class="empty">Hakuna bidhaa bado. Bofya + kuongeza</div>
    </div>

    <!-- PRODUCTS PAGE -->
    <div id="products" class="page">
        <input type="text" class="search-bar" placeholder="🔍 Tafuta bidhaa..." onkeyup="searchProducts(this.value)">
        <h3 style="margin-bottom:10px">Bidhaa Zote</h3>
        <div class="grid" id="all-products-grid"></div>
        <div id="products-empty" class="empty">Hakuna bidhaa</div>
    </div>

    <!-- PROFILE PAGE -->
    <div id="profile" class="page">
        <div id="profile-content"></div>
    </div>

    <!-- NOTIFICATION PAGE -->
    <div id="notification" class="page">
        <h3 style="margin-bottom:10px">Notifications</h3>
        <div class="empty">Hakuna notification mpya</div>
    </div>
</div>

<!-- LOGIN/SIGNUP MODAL -->
<div id="auth-modal" class="modal">
    <div class="modal-content">
        <div class="modal-header">
            <h3 id="auth-title">Ingia Muble</h3>
            <button onclick="closeModal()" style="background:none;border:none;font-size:24px">&times;</button>
        </div>
        <div class="modal-body">
            <div class="tabs">
                <button class="tab active" onclick="showAuthTab('login',this)">Ingia</button>
                <button class="tab" onclick="showAuthTab('signup',this)">Jisajili</button>
            </div>
            <form id="login-form" onsubmit="handleLogin(event)">
                <input type="text" id="login-phone" placeholder="Namba: 0712345678" required>
                <input type="password" id="login-pass" placeholder="Password" required>
                <button type="submit" class="btn">Ingia</button>
            </form>
            <form id="signup-form" style="display:none" onsubmit="handleSignup(event)">
                <input type="text" id="signup-name" placeholder="Jina Kamili" required>
                <input type="text" id="signup-phone" placeholder="Namba ya Simu" required>
                <input type="password" id="signup-pass" placeholder="Password" required>
                <button type="submit" class="btn">Jisajili</button>
            </form>
        </div>
    </div>
</div>

<!-- ADD PRODUCT MODAL -->
<div id="add-modal" class="modal">
    <div class="modal-content">
        <div class="modal-header">
            <h3>Ongeza Bidhaa</h3>
            <button onclick="closeModal()" style="background:none;border:none;font-size:24px">&times;</button>
        </div>
        <div class="modal-body">
            <form id="product-form">
                <label>Picha Za Bidhaa - Max 3</label>
                <input type="file" id="images" accept="image/*" multiple>
                <div class="img-preview" id="img-preview"></div>
                <input type="text" id="name" placeholder="Jina la Bidhaa" required>
                <input type="number" id="price" placeholder="Bei TZS" required>
                <input type="text" id="location" placeholder="Location - Mfano: Kariakoo, Dar" required>
                <textarea id="description" placeholder="Maelezo ya bidhaa" required></textarea>
                <input type="text" id="contact" placeholder="Namba ya Simu au Email" required>
                <button type="submit" class="btn">Post Bidhaa</button>
            </form>
        </div>
    </div>
</div>

<!-- VIEW PRODUCT MODAL -->
<div id="view-modal" class="modal">
    <div class="modal-content">
        <div class="modal-header">
            <h3>Maelezo ya Bidhaa</h3>
            <button onclick="closeModal()" style="background:none;border:none;font-size:24px">&times;</button>
        </div>
        <div class="modal-body" id="view-body"></div>
    </div>
</div>

<!-- PAYMENT MODAL -->
<div id="payment-modal" class="modal">
    <div class="modal-content">
        <div class="modal-header">
            <h3>Lipa Sasa</h3>
            <button onclick="closeModal()" style="background:none;border:none;font-size:24px">&times;</button>
        </div>
        <div class="modal-body" id="payment-body"></div>
    </div>
</div>

<!-- BOTTOM NAV -->
<nav class="bottom-nav">
    <button class="nav-item active" onclick="showPage('home',this)">
        <svg fill="currentColor" viewBox="0 0 24 24"><path d="M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z"/></svg>
        Home
    </button>
    <button class="nav-item" onclick="showPage('products',this)">
        <svg fill="currentColor" viewBox="0 0 24 24"><path d="M4 8h4V4H4v4zm6 12h4v-4h-4v4zm-6 0h4v-4H4v4zm0-6h4v-4H4v4zm6 0h4v-4h-4v4zm6-10v4h4V4h-4zm-6 4h4V4h-4v4zm6 6h4v-4h-4v4zm0 6h4v-4h-4v4z"/></svg>
        Products
    </button>
    <button class="nav-item add-btn" onclick="checkLoginAndPost()">
        <svg fill="currentColor" viewBox="0 0 24 24"><path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z"/></svg>
    </button>
    <button class="nav-item" onclick="showPage('notification',this)">
        <svg fill="currentColor" viewBox="0 0 24 24"><path d="M12 22c1.1 0 2-.9 2-2h-4c0 1.1.9 2 2 2zm6-6v-5c0-3.07-1.63-5.64-4.5-6.32V4c0-.83-.67-1.5s-1.5.67-1.5 1.5v.68C7.64 5.36 6 7.92 6 11v5l-2 2v1h16v-1l-2-2zm-2 1H8v-6c0-2.48 1.51-4.5 4-4.5s4 2.02 4 4.5v6z"/></svg>
        Noti
    </button>
    <button class="nav-item" onclick="checkProfileAccess()">
        <svg fill="currentColor" viewBox="0 0 24 24"><path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/></svg>
        Profile
    </button>
</nav>

<script>
let products = JSON.parse(localStorage.getItem('muble_products') || '[]');
let users = JSON.parse(localStorage.getItem('muble_users') || '[]');
let currentUser = JSON.parse(localStorage.getItem('muble_current') || 'null');
let selectedImages = [];
let currentPayment = null;
let selectedPayMethod = 'mpesa';

function showMsg(text,color='#10b981'){
    const msg=document.getElementById('msg');
    msg.textContent=text;msg.style.background=color;msg.style.display='block';
    setTimeout(()=>msg.style.display='none',3000);
}

function updateProfileIcon(){
    document.getElementById('profile-icon').textContent=currentUser?currentUser.name.charAt(0).toUpperCase():'U';
}
updateProfileIcon();

function showPage(page,btn){
    document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
    document.getElementById(page).classList.add('active');
    document.querySelectorAll('.nav-item').forEach(i=>i.classList.remove('active'));
    if(btn) btn.classList.add('active');
    if(page==='home'||page==='products') renderProducts();
    if(page==='profile') renderProfile();
}

function closeModal(){
    document.querySelectorAll('.modal').forEach(m=>m.classList.remove('active'));
}

function checkLogin(){
    if(!currentUser){
        showMsg('Tafadhali ingia kwanza','var(--red)');
        document.getElementById('auth-modal').classList.add('active');
        return false;
    }
    return true;
}

function checkLoginAndPost(){
    if(checkLogin()) document.getElementById('add-modal').classList.add('active');
}

function checkProfileAccess(){
    if(!currentUser){
        document.getElementById('auth-modal').classList.add('active');
    }else{
        showPage('profile',document.querySelectorAll('.nav-item')[4]);
    }
}

function showAuthTab(tab,btn){
    document.getElementById('login-form').style.display=tab==='login'?'block':'none';
    document.getElementById('signup-form').style.display=tab==='signup'?'block':'none';
    document.querySelectorAll('.tab').forEach(t=>t.classList.remove('active'));
    btn.classList.add('active');
}

function handleSignup(e){
    e.preventDefault();
    const name=document.getElementById('signup-name').value;
    const phone=document.getElementById('signup-phone').value;
    const pass=document.getElementById('signup-pass').value;
    if(users.find(u=>u.phone===phone)){
        showMsg('Namba imeshatumika','var(--red)');
        return;
    }
    const user={id:Date.now(),name,phone,password:pass,date:new Date().toLocaleDateString('sw-TZ')};
    users.push(user);
    localStorage.setItem('muble_users',JSON.stringify(users));
    currentUser=user;
    localStorage.setItem('muble_current',JSON.stringify(user));
    updateProfileIcon();
    closeModal();
    showMsg('Umefanikiwa kujisajili!');
    showPage('profile',document.querySelectorAll('.nav-item')[4]);
}

function handleLogin(e){
    e.preventDefault();
    const phone=document.getElementById('login-phone').value;
    const pass=document.getElementById('login-pass').value;
    const user=users.find(u=>u.phone===phone&&u.password===pass);
    if(!user){
        showMsg('Namba au password sio sahihi','var(--red)');
        return;
    }
    currentUser=user;
    localStorage.setItem('muble_current',JSON.stringify(user));
    updateProfileIcon();
    closeModal();
    showMsg('Karibu '+user.name);
    showPage('home',document.querySelector('.nav-item'));
}

function logout(){
    currentUser=null;
    localStorage.removeItem('muble_current');
    updateProfileIcon();
    showMsg('Umetoka');
    showPage('home',document.querySelector('.nav-item'));
}

function renderProfile(){
    if(!currentUser) return;
    const myProducts=products.filter(p=>p.userId===currentUser.id);
    document.getElementById('profile-content').innerHTML=`
        <div class="profile-card">
            <div class="profile" style="width:60px;height:60px;font-size:24px;margin:0 auto">${currentUser.name.charAt(0)}</div>
            <h3>${currentUser.name}</h3>
            <p style="color:var(--gray)">${currentUser.phone}</p>
            <div class="profile-stats">
                <div><strong>${myProducts.length}</strong><br><span style="font-size:12px;color:var(--gray)">Bidhaa</span></div>
                <div><strong>0</strong><br><span style="font-size:12px;color:var(--gray)">Mauzo</span></div>
            </div>
            <button class="btn btn-red" onclick="logout()">Toka</button>
        </div>
        <h3 style="margin:15px 0 10px 0">Bidhaa Zangu</h3>
        ${myProducts.length?myProducts.map(p=>`
            <div class="my-product">
                <div>
                    <strong>${p.name}</strong><br>
                    <span style="font-size:12px;color:var(--gray)">TZS ${Number(p.price).toLocaleString()}</span>
                </div>
                <button class="btn-red" style="padding:6px 12px;width:auto" onclick="deleteProduct(${p.id})">Futa</button>
            </div>
        `).join(''):'<div class="empty">Hujapost bidhaa yoyote</div>'}
    `;
}

function deleteProduct(id){
    if(confirm('Una uhakika unataka kufuta bidhaa hii?')){
        products=products.filter(p=>p.id!==id);
        localStorage.setItem('muble_products',JSON.stringify(products));
        renderProfile();
        renderProducts();
        showMsg('Bidhaa imefutwa');
    }
}

document.getElementById('images').onchange=function(e){
    const files=Array.from(e.target.files);
    if(selectedImages.length+files.length>3){
        alert('Picha zisizidi 3');
        return;
    }
    files.forEach(file=>{
        const reader=new FileReader();
        reader.onload=ev=>{
            selectedImages.push(ev.target.result);
            renderPreview();
        };
        reader.readAsDataURL(file);
    });
};

function renderPreview(){
    document.getElementById('img-preview').innerHTML=selectedImages.map((img,i)=>`
        <div class="img-box"><img src="${img}"><button type="button" onclick="removeImg(${i})">×</button></div>
    `).join('');
}
function removeImg(i){selectedImages.splice(i,1);renderPreview();}

document.getElementById('product-form').onsubmit=function(e){
    e.preventDefault();
    if(!currentUser){showMsg('Ingia kwanza','var(--red)');return;}
    if(selectedImages.length===0){alert('Weka angalau picha 1');return;}
    const product={
        id:Date.now(),userId:currentUser.id,
        name:document.getElementById('name').value,
        price:document.getElementById('price').value,
        location:document.getElementById('location').value,
        description:document.getElementById('description').value,
        contact:document.getElementById('contact').value,
        images:selectedImages,
        date:new Date().toLocaleDateString('sw-TZ')
    };
    products.unshift(product);
    localStorage.setItem('muble_products',JSON.stringify(products));
    selectedImages=[];
    document.getElementById('product-form').reset();
    document.getElementById('img-preview').innerHTML='';
    closeModal();
    showMsg('Bidhaa imeongezwa!');
    renderProducts();
};

function searchProducts(val){
    const q=(val||document.getElementById('search').value).toLowerCase();
    const filtered=products.filter(p=>p.name.toLowerCase().includes(q)||p.location.toLowerCase().includes(q)||p.description.toLowerCase().includes(q));
    renderProducts(filtered);
}

function renderProducts(list=products){
    const html=list.map(p=>`
        <div class="product" onclick="viewProduct(${p.id})">
            <img src="${p.images[0]}" alt="${p.name}">
            <div class="product-info">
                <h3>${p.name}</h3>
                <div class="price">TZS ${Number(p.price).toLocaleString()}</div>
                <div class="location">📍 ${p.location}</div>
            </div>
        </div>
    `).join('');
    document.getElementById('products-grid').innerHTML=html;
    document.getElementById('all-products-grid').innerHTML=html;
    document.getElementById('home-empty').style.display=list.length?'none':'block';
    document.getElementById('products-empty').style.display=list.length?'none':'block';
}

function viewProduct(id){
    const p=products.find(x=>x.id===id);
    const isPhone=p.contact.match(/^[0-9+]+$/);
    const canBuy=currentUser&&currentUser.id!==p.userId;
    document.getElementById('view-body').innerHTML=`
        <img src="${p.images[0]}" class="view-img">
        <div style="display:flex;gap:5px;margin:10px 0;overflow-x:auto">
            ${p.images.map(img=>`<img src="${img}" style="width:60px;height:60px;object-fit:cover;border-radius:6px">`).join('')}
        </div>
        <h2>${p.name}</h2>
        <div class="price" style="font-size:24px">TZS ${Number(p.price).toLocaleString()}</div>
        <div class="view-meta">
            <span>📍 ${p.location}</span><span>📅 ${p.date}</span>
        </div>
        <p style="margin:15px 0;line-height:1.6">${p.description}</p>
        <div class="contact-box">
            <strong>Muuza:</strong><br>
            ${isPhone?`<a href="tel:${p.contact}">📞 ${p.contact}</a> | <a href="https://wa.me/255${p.contact.slice(-9)}" target="_blank">WhatsApp</a>`:`<a href="mailto:${p.contact}">✉️ ${p.contact}</a>`}
        </div>
        ${canBuy?`<button class="btn btn-green" onclick="openPayment(${p.id})">💰 Nunua Sasa - TZS ${Number(p.price).toLocaleString()}</button>`:
      !currentUser?`<button class="btn" onclick="checkLogin()">Ingia Ili Ununue</button>`:
        `<div style="text-align:center;color:var(--gray);padding:10px">Hii ni bidhaa yako</div>`}
    `;
    document.getElementById('view-modal').classList.add('active');
}

function openPayment(id){
    if(!checkLogin()) return;
    const p=products.find(x=>x.id===id);
    currentPayment=p;
    document.getElementById('payment-body').innerHTML=`
        <div style="text-align:center;margin-bottom:15px">
            <img src="${p.images[0]}" style="width:100px;height:100px;object-fit:cover;border-radius:8px">
            <h3 style="margin:10px 0 5px 0">${p.name}</h3>
            <div class="price">TZS ${Number(p.price).toLocaleString()}</div>
        </div>
        <h4>1. Jaza Taarifa Zako</h4>
        <input type="text" id="buyer-name" placeholder="Jina Lako Kamili" required>
        <input type="text" id="buyer-location" placeholder="Location - Mfano: Sinza, Dar" required>
        <h4 style="margin-top:15px">2. Chagua Njia ya Malipo</h4>
        <div class="payment-methods">
            <div class="payment-item active" onclick="selectPay('mpesa',this)">📱 M-Pesa</div>
            <div class="payment-item" onclick="selectPay('tigo',this)">📱 Tigo Pesa</div>
            <div class="payment-item" onclick="selectPay('airtel',this)">📱 Airtel Money</div>
            <div class="payment-item" onclick="selectPay('halo',this)">📱 HaloPesa</div>
            <div class="payment-item" onclick="selectPay('card',this)" style="grid-column:span 2">💳 Visa/Mastercard</div>
        </div>
        <div id="pay-fields"></div>
        <button class="btn btn-green" onclick="processPayment()">Lipa Sasa TZS ${Number(p.price).toLocaleString()}</button>
        <p style="font-size:11px;color:var(--gray);text-align:center;margin-top:10px">*Demo tu. Hakuna malipo halisi yanafanyika</p>
    `;
    selectPay('mpesa',document.querySelector('.payment-item'));
    document.getElementById('payment-modal').classList.add('active');
}

function selectPay(method,el){
    selectedPayMethod=method;
    document.querySelectorAll('.payment-item').forEach(i=>i.classList.remove('active'));
    el.classList.add('active');
    let html='';
    if(method==='card'){
        html=`<input type="text" placeholder="Namba ya Kadi - 1234 5678 9012 3456">
              <div style="display:flex;gap:10px">
                <input type="text" placeholder="MM/YY" style="flex:1">
                <input type="text" placeholder="CVV" style="flex:1">
              </div>`;
    }else{
        html=`<input type="text" id="pay-number" placeholder="Namba ya Simu ya Kulipia - 07XXXXXXXX">`;
    }
    document.getElementById('pay-fields').innerHTML=html;
}

function processPayment(){
    const name=document.getElementById('buyer-name').value;
    const loc=document.getElementById('buyer-location').value;
    if(!name||!loc){showMsg('Jaza jina na location','var(--red)');return;}
    closeModal();
    showMsg('Malipo yamefanikiwa! Muuzaji atawasiliana nawe.');
}

renderProducts();
</script>
</body>
</html>
