<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Apna Samosa — Jamui</title>
<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@400;600;700;800;900&family=Noto+Sans+Devanagari:wght@400;700&display=swap" rel="stylesheet">
<style>
:root {
  --fire:#FF6A00; --saffron:#FF8C00; --gold:#FFA500; --cream:#0A0A0A;
  --deep:#000000; --brown:#111111; --green:#1B6B3A; --red:#C0392B;
  --light:#1A1A1A; --chat:#0D0D0D; --purple:#6C3483;
  --card:#141414; --border:#2A2A2A; --text:#EEEEEE; --subtext:#888888;
  --r:16px;
}
*{margin:0;padding:0;box-sizing:border-box;}
body{font-family:'Baloo 2',cursive;background:var(--cream);min-height:100vh;overflow-x:hidden;color:var(--text);}

/* NAV */
.nav{display:flex;background:var(--deep);position:sticky;top:0;z-index:300;box-shadow:0 4px 20px rgba(0,0,0,0.6);}
.nb{flex:1;padding:8px 2px;background:none;border:none;color:#555;font-family:'Baloo 2',cursive;font-size:10px;font-weight:700;cursor:pointer;transition:all .3s;border-bottom:3px solid transparent;display:flex;flex-direction:column;align-items:center;gap:1px;}
.nb i{font-size:18px;font-style:normal;}
.nb.active{color:var(--gold);border-bottom-color:var(--fire);}
.page{display:none;min-height:calc(100vh - 52px);padding-bottom:20px;}
.page.active{display:block;}

/* HERO */
.hero{background:#000;padding:0 0 20px;text-align:center;position:relative;overflow:hidden;}
.hero-img-wrap{width:100%;height:200px;overflow:hidden;position:relative;}
.hero-img-wrap::after{content:'';position:absolute;inset:0;background:linear-gradient(to bottom,rgba(0,0,0,0.1) 0%,rgba(0,0,0,0.85) 100%);}
.hero-img{width:100%;height:100%;object-fit:cover;display:block;}
.hero-content{position:relative;z-index:1;padding:0 16px;}
.flame{font-size:42px;display:block;animation:flicker 1.8s infinite alternate;margin-top:-30px;position:relative;z-index:2;}
@keyframes flicker{0%{transform:scale(1) rotate(-2deg)}100%{transform:scale(1.1) rotate(2deg)}}
.hero h1{font-size:30px;font-weight:900;color:#fff;text-shadow:0 0 20px rgba(255,106,0,0.8);position:relative;z-index:1;background:linear-gradient(to right,#FF6A00,#FFA500);-webkit-background-clip:text;-webkit-text-fill-color:transparent;}
.hero-sub{color:#FF8C00;font-size:12px;margin-top:3px;font-weight:600;position:relative;z-index:1;}
.hero-addr{color:#555;font-size:11px;margin-top:4px;position:relative;z-index:1;}
.timing-badge{display:inline-flex;align-items:center;gap:6px;background:rgba(255,106,0,0.15);border:1px solid rgba(255,106,0,0.4);color:var(--gold);padding:5px 14px;border-radius:20px;font-size:12px;font-weight:700;margin-top:10px;position:relative;z-index:1;}
.open-dot{width:8px;height:8px;border-radius:50%;animation:blink 1s infinite;}
.open-dot.open{background:#4CAF50;}
.open-dot.closed{background:#f44336;}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.3}}

/* WEATHER BANNER */
.weather-banner{padding:10px 16px;display:flex;align-items:center;gap:10px;font-size:13px;font-weight:600;border-bottom:1px solid #222;background:#111;}

/* LOYALTY */
.loyalty-card{background:#141414;margin:12px 16px;border-radius:14px;padding:14px 16px;box-shadow:0 2px 12px rgba(255,106,0,.1);border:1px solid #2A2A2A;}
.loy-top{display:flex;align-items:center;gap:12px;margin-bottom:10px;}
.loy-pts{font-size:26px;font-weight:900;color:var(--fire);}
.loy-label{font-size:11px;color:#666;}
.loy-next{font-size:12px;color:#aaa;font-weight:600;}
.prog-bar{height:10px;background:#222;border-radius:5px;overflow:hidden;}
.prog-fill{height:100%;background:linear-gradient(to right,var(--fire),var(--gold));border-radius:5px;transition:width .6s ease;}
.reward-chips{display:flex;gap:8px;margin-top:10px;flex-wrap:wrap;}
.reward-chip{background:#1E1E1E;border:1.5px solid #FF8C00;border-radius:20px;padding:4px 12px;font-size:11px;font-weight:700;color:#FF8C00;}
.reward-chip.earned{background:var(--gold);color:#000;}

/* SECTION */
.sec{padding:14px 16px;}
.sec-title{font-size:15px;font-weight:800;color:#fff;margin-bottom:10px;display:flex;align-items:center;gap:8px;}
.sec-title::after{content:'';flex:1;height:2px;background:linear-gradient(to right,var(--fire),transparent);}

/* MENU ITEM */
.mitem{background:#141414;border-radius:12px;padding:11px 13px;display:flex;align-items:center;gap:10px;margin-bottom:8px;box-shadow:0 2px 8px rgba(0,0,0,.3);border:1px solid #222;transition:all .2s;}
.mitem:hover{border-color:var(--fire);box-shadow:0 0 12px rgba(255,106,0,.2);}
.mitem.unavail{opacity:.4;}
.item-em{font-size:30px;}
.item-inf{flex:1;}
.item-nm{font-size:13px;font-weight:700;color:#eee;}
.item-pr{font-size:14px;font-weight:900;color:var(--fire);}
.item-pt{font-size:10px;color:#4CAF50;font-weight:700;}
.qc{display:flex;align-items:center;gap:6px;}
.qb{width:28px;height:28px;border-radius:50%;border:2px solid var(--fire);background:#000;color:var(--fire);font-size:15px;font-weight:800;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .2s;line-height:1;}
.qb:hover{background:var(--fire);color:#fff;}
.qn{font-size:14px;font-weight:800;color:#fff;min-width:16px;text-align:center;}

/* CART */
.cart-box{background:#141414;border-radius:14px;padding:14px;margin-bottom:12px;border:1px dashed #FF6A00;}
.cart-empty{text-align:center;color:#444;font-size:13px;padding:6px;}
.cart-row{display:flex;justify-content:space-between;font-size:13px;color:#ccc;margin-bottom:4px;}
.cart-total{display:flex;justify-content:space-between;font-size:16px;font-weight:900;color:var(--fire);border-top:1px solid #2A2A2A;padding-top:8px;margin-top:6px;}

/* FORM */
.finput{width:100%;padding:11px 13px;border:1px solid #2A2A2A;border-radius:10px;font-family:'Baloo 2',cursive;font-size:14px;color:#eee;outline:none;transition:border-color .2s;background:#141414;}
.finput:focus{border-color:var(--fire);}
.flabel{display:block;font-size:12px;font-weight:700;color:#aaa;margin-bottom:5px;}
.fg{margin-bottom:12px;}
.ftoggle{display:flex;gap:8px;margin-bottom:12px;}
.ftog-btn{flex:1;padding:10px;border:1px solid #2A2A2A;border-radius:10px;background:#141414;font-family:'Baloo 2',cursive;font-size:13px;font-weight:700;color:#555;cursor:pointer;transition:all .2s;}
.ftog-btn.active{border-color:var(--fire);color:var(--fire);background:#1A0A00;}

/* BUTTONS */
.btn-main{width:100%;padding:15px;background:linear-gradient(135deg,var(--fire),#FF8C00);color:#fff;border:none;border-radius:12px;font-family:'Baloo 2',cursive;font-size:16px;font-weight:800;cursor:pointer;box-shadow:0 4px 20px rgba(255,106,0,.4);transition:all .2s;}
.btn-main:hover{transform:translateY(-2px);box-shadow:0 6px 25px rgba(255,106,0,.5);}
.btn-main:disabled{background:#222;box-shadow:none;transform:none;cursor:not-allowed;color:#555;}
.btn-green{background:var(--green);width:100%;padding:14px;border:none;border-radius:12px;font-family:'Baloo 2',cursive;font-size:15px;font-weight:800;color:#fff;cursor:pointer;}
.btn-ghost{width:100%;padding:11px;background:none;border:1px solid #2A2A2A;border-radius:12px;font-family:'Baloo 2',cursive;font-size:13px;color:#555;cursor:pointer;margin-top:8px;}

/* MODAL */
.modal-wrap{display:none;position:fixed;inset:0;background:rgba(0,0,0,.9);z-index:500;align-items:flex-end;justify-content:center;}
.modal-wrap.show{display:flex;}
.modal{background:#141414;border-radius:24px 24px 0 0;padding:24px 18px 36px;width:100%;max-width:480px;animation:slideUp .3s ease;border-top:2px solid #2A2A2A;}
@keyframes slideUp{from{transform:translateY(100%)}to{transform:translateY(0)}}
.modal-title{font-size:20px;font-weight:800;color:#fff;text-align:center;margin-bottom:4px;}
.modal-sub{text-align:center;color:#555;font-size:12px;margin-bottom:16px;}

/* PAYMENT BOX */
.pay-box{background:#1A1A1A;border-radius:14px;padding:16px;text-align:center;margin-bottom:14px;border:1px solid #FF6A00;}
.pay-amt{display:inline-block;background:linear-gradient(135deg,var(--fire),#FF8C00);color:#fff;padding:6px 20px;border-radius:20px;font-size:20px;font-weight:900;margin-bottom:10px;}
.pay-qr{width:150px;height:150px;margin:0 auto 10px;border-radius:10px;overflow:hidden;border:3px solid #FF6A00;box-shadow:0 0 20px rgba(255,106,0,.3);}
.pay-qr img{width:100%;height:100%;object-fit:contain;}
.pay-upi{font-size:13px;font-weight:800;color:#FF8C00;background:#0A0A0A;padding:6px 14px;border-radius:8px;display:inline-block;margin-top:6px;border:1px solid #2A2A2A;}

/* SCREENSHOT UPLOAD */
.upload-area{border:1px dashed #FF6A00;border-radius:12px;padding:20px;text-align:center;cursor:pointer;background:#1A1A1A;margin-bottom:14px;transition:all .2s;}
.upload-area:hover{background:#200E00;}
.upload-area.has-file{border-color:var(--green);background:#0A1A0A;}
.upload-icon{font-size:36px;}
.upload-text{font-size:13px;color:#555;margin-top:6px;}
#ss-input{display:none;}

/* SUCCESS */
.success-page{display:none;text-align:center;padding:30px 16px;background:#0A0A0A;min-height:100vh;}
.success-page.show{display:block;}
.s-emoji{font-size:72px;animation:pop .5s ease;}
@keyframes pop{0%{transform:scale(0)}80%{transform:scale(1.2)}100%{transform:scale(1)}}
.s-title{font-size:24px;font-weight:900;color:#4CAF50;margin:14px 0 6px;}
.s-msg{font-size:14px;color:#666;line-height:1.6;}
.ticket{background:#141414;border-radius:14px;padding:16px;margin:16px 0;box-shadow:0 4px 15px rgba(0,0,0,.5);border-top:3px solid var(--fire);text-align:left;}
.t-row{display:flex;justify-content:space-between;font-size:13px;margin-bottom:7px;}
.t-row span:first-child{color:#555;}
.t-row span:last-child{font-weight:700;color:#eee;}
.token-badge{background:linear-gradient(135deg,var(--fire),#FF8C00);color:#fff;font-size:28px;font-weight:900;padding:8px 24px;border-radius:14px;display:inline-block;margin:10px 0;box-shadow:0 4px 15px rgba(255,106,0,.4);}
.wa-btn{display:flex;align-items:center;justify-content:center;gap:8px;width:100%;padding:15px;background:#25D366;color:#fff;border:none;border-radius:12px;font-family:'Baloo 2',cursive;font-size:15px;font-weight:800;cursor:pointer;text-decoration:none;}

/* ===== KITCHEN ===== */
.kitchen-top{background:#000;padding:16px;display:flex;justify-content:space-between;align-items:center;border-bottom:1px solid #222;}
.kitchen-top h2{font-size:18px;font-weight:800;color:#fff;}
.live-pill{background:var(--red);color:#fff;padding:4px 12px;border-radius:20px;font-size:11px;font-weight:700;display:flex;align-items:center;gap:5px;}
.live-dot{width:7px;height:7px;background:#fff;border-radius:50%;animation:blink 1s infinite;}
.stats-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;padding:12px 16px;}
.stat{background:#141414;border-radius:12px;padding:12px 8px;text-align:center;border:1px solid #222;}
.stat-n{font-size:26px;font-weight:900;color:var(--fire);line-height:1;}
.stat-l{font-size:10px;color:#555;margin-top:3px;font-weight:700;}
.ocard{background:#141414;border-radius:14px;padding:14px;margin:0 16px 10px;border:1px solid #222;border-left:4px solid var(--gold);animation:fadeIn .4s ease;}
@keyframes fadeIn{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:translateY(0)}}
.ocard.preparing{border-left-color:var(--fire);}
.ocard.ready{border-left-color:#4CAF50;}
.ocard.done{border-left-color:#333;opacity:.5;}
.ocard.pending-verify{border-left-color:var(--purple);}
.otop{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:8px;}
.oname{font-size:15px;font-weight:800;color:#eee;}
.ophone{font-size:11px;color:#555;margin-top:1px;}
.ostatus{padding:3px 10px;border-radius:20px;font-size:10px;font-weight:700;text-transform:uppercase;}
.s-verify{background:#2D1B4E;color:#B39DDB;}
.s-new{background:#2A1F00;color:#FFB300;}
.s-prep{background:#2A1000;color:#FF8C00;}
.s-ready{background:#0A2A0A;color:#4CAF50;}
.s-done{background:#1A1A1A;color:#444;}
.oitems{font-size:12px;color:#666;margin-bottom:8px;}
.oitems span{display:inline-block;background:#1E1E1E;padding:2px 8px;border-radius:6px;margin:2px;font-weight:600;color:#aaa;}
.ofooter{display:flex;justify-content:space-between;align-items:center;}
.oamt{font-size:14px;font-weight:900;color:var(--fire);}
.otime{font-size:11px;color:#444;}
.action-row{display:flex;gap:6px;margin-top:10px;}
.abtn{flex:1;padding:9px;border:none;border-radius:9px;font-family:'Baloo 2',cursive;font-size:12px;font-weight:700;cursor:pointer;}
.ab-verify{background:var(--purple);color:#fff;}
.ab-start{background:var(--fire);color:#fff;}
.ab-ready{background:var(--green);color:#fff;}
.ab-done{background:#1A1A1A;color:#444;}
.delivery-badge{background:var(--red);color:#fff;font-size:10px;padding:2px 8px;border-radius:10px;font-weight:700;margin-left:6px;}
.ss-preview{width:60px;height:60px;border-radius:8px;object-fit:cover;border:2px solid var(--purple);cursor:pointer;}

/* ===== ANALYTICS ===== */
.analytics-header{background:#000;padding:16px;color:#fff;border-bottom:1px solid #222;}
.analytics-header h2{font-size:18px;font-weight:800;}
.analytics-header p{font-size:12px;color:#555;margin-top:2px;}
.ana-cards{display:grid;grid-template-columns:repeat(2,1fr);gap:10px;padding:14px 16px;}
.ana-card{background:#141414;border-radius:14px;padding:16px;border:1px solid #222;}
.ana-card.full{grid-column:1/-1;}
.ana-num{font-size:30px;font-weight:900;color:var(--fire);}
.ana-label{font-size:11px;color:#555;font-weight:700;margin-top:2px;}
.ana-sub{font-size:12px;color:#4CAF50;font-weight:700;margin-top:4px;}
.chart-bar-wrap{margin-top:12px;}
.chart-row{display:flex;align-items:center;gap:8px;margin-bottom:6px;}
.chart-label{font-size:11px;color:#555;width:60px;text-align:right;flex-shrink:0;}
.chart-bar-bg{flex:1;background:#1A1A1A;border-radius:4px;height:18px;overflow:hidden;}
.chart-bar-fill{height:100%;background:linear-gradient(to right,var(--fire),var(--gold));border-radius:4px;transition:width .8s ease;}
.chart-val{font-size:11px;font-weight:700;color:#aaa;width:36px;}
.top-item{display:flex;align-items:center;gap:10px;padding:8px 0;border-bottom:1px solid #1A1A1A;}
.top-item:last-child{border:none;}
.top-rank{font-size:18px;font-weight:900;color:var(--gold);width:24px;}
.top-name{flex:1;font-size:13px;font-weight:700;color:#eee;}
.top-cnt{font-size:13px;font-weight:900;color:var(--fire);}

/* ===== ADMIN ===== */
.admin-lock{text-align:center;padding:60px 20px;background:#0A0A0A;min-height:100vh;}
.admin-lock h2{font-size:22px;font-weight:800;color:#eee;margin:16px 0 8px;}
.admin-lock p{font-size:14px;color:#555;margin-bottom:20px;}
.admin-panel{display:none;}
.admin-panel.unlocked{display:block;}
.admin-header{background:#000;padding:14px 16px;display:flex;justify-content:space-between;align-items:center;border-bottom:1px solid #222;}
.admin-header h2{font-size:17px;font-weight:800;color:#fff;}
.logout-btn{background:#1A1A1A;border:1px solid #333;color:#666;font-family:'Baloo 2',cursive;font-size:12px;padding:6px 12px;border-radius:8px;cursor:pointer;}
.admin-sec{padding:14px 16px;}
.admin-sec h3{font-size:14px;font-weight:800;color:#aaa;margin-bottom:10px;padding-bottom:6px;border-bottom:1px solid #1A1A1A;}
.edit-item-row{display:flex;align-items:center;gap:8px;background:#141414;border-radius:10px;padding:10px 12px;margin-bottom:8px;border:1px solid #222;}
.edit-item-row .name{flex:1;font-size:13px;font-weight:700;color:#eee;}
.edit-price-input{width:70px;padding:6px 8px;border:1px solid #333;border-radius:8px;font-family:'Baloo 2',cursive;font-size:14px;font-weight:800;color:var(--fire);text-align:center;outline:none;background:#0A0A0A;}
.edit-price-input:focus{border-color:var(--fire);}
.toggle-sw{position:relative;width:40px;height:22px;background:#222;border-radius:11px;cursor:pointer;transition:background .3s;flex-shrink:0;}
.toggle-sw.on{background:var(--green);}
.toggle-sw::after{content:'';position:absolute;width:18px;height:18px;background:#fff;border-radius:50%;top:2px;left:2px;transition:left .3s;}
.toggle-sw.on::after{left:20px;}
.save-btn{width:100%;padding:12px;background:linear-gradient(135deg,var(--fire),#FF8C00);color:#fff;border:none;border-radius:10px;font-family:'Baloo 2',cursive;font-size:14px;font-weight:800;cursor:pointer;margin-top:8px;}
.notice-area{width:100%;padding:10px 12px;border:1px solid #2A2A2A;border-radius:10px;font-family:'Baloo 2',cursive;font-size:13px;color:#eee;outline:none;resize:none;min-height:70px;background:#141414;}
.notice-area:focus{border-color:var(--fire);}
.reward-edit-row{display:flex;align-items:center;gap:8px;margin-bottom:10px;font-size:13px;color:#aaa;}
.reward-edit-row input{width:55px;padding:6px 8px;border:1px solid #333;border-radius:8px;font-family:'Baloo 2',cursive;font-size:14px;font-weight:800;color:var(--fire);text-align:center;outline:none;background:#0A0A0A;}
.reward-edit-row input:focus{border-color:var(--fire);}

/* NOTICE BANNER */
.notice-bar{background:linear-gradient(135deg,#1A0A00,var(--fire));color:#fff;padding:10px 16px;font-size:13px;font-weight:600;display:none;}
.notice-bar.show{display:block;}
#page-chat{background:var(--chat-bg);}
.chat-header{background:linear-gradient(135deg,var(--brown),var(--deep));padding:16px;display:flex;align-items:center;gap:12px;}
.chat-avatar{width:44px;height:44px;border-radius:50%;background:linear-gradient(135deg,var(--saffron),var(--gold));display:flex;align-items:center;justify-content:center;font-size:22px;}
.chat-info h3{font-size:15px;font-weight:800;color:#fff;}
.chat-status{font-size:11px;color:#4CAF50;font-weight:600;}
.chat-msgs{padding:16px;min-height:calc(100vh - 200px);display:flex;flex-direction:column;gap:10px;overflow-y:auto;}
.msg{max-width:80%;animation:msgIn .3s ease;}
@keyframes msgIn{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:translateY(0)}}
.msg.bot{align-self:flex-start;}
.msg.user{align-self:flex-end;}
.msg-bubble{padding:10px 14px;border-radius:16px;font-size:14px;line-height:1.5;}
.msg.bot .msg-bubble{background:#1E1E1E;color:#eee;border-bottom-left-radius:4px;}
.msg.user .msg-bubble{background:linear-gradient(135deg,var(--saffron),var(--fire));color:#fff;border-bottom-right-radius:4px;}
.msg-time{font-size:10px;color:#555;margin-top:3px;text-align:right;}
.msg.bot .msg-time{text-align:left;}
.typing{display:flex;gap:4px;padding:12px 14px;background:#1E1E1E;border-radius:16px;border-bottom-left-radius:4px;width:fit-content;}
.typing span{width:6px;height:6px;background:#666;border-radius:50%;animation:type .8s infinite;}
.typing span:nth-child(2){animation-delay:.2s;}
.typing span:nth-child(3){animation-delay:.4s;}
@keyframes type{0%,100%{transform:translateY(0)}50%{transform:translateY(-4px)}}
.chat-input-area{position:sticky;bottom:0;background:#111;padding:12px 16px;display:flex;gap:8px;border-top:1px solid #222;}
.chat-input{flex:1;background:#1E1E1E;border:1.5px solid #333;border-radius:24px;padding:10px 16px;color:#fff;font-family:'Baloo 2',cursive;font-size:14px;outline:none;}
.chat-input:focus{border-color:var(--saffron);}
.chat-send{width:42px;height:42px;border-radius:50%;background:linear-gradient(135deg,var(--saffron),var(--fire));border:none;color:#fff;font-size:18px;cursor:pointer;display:flex;align-items:center;justify-content:center;}
.quick-replies{display:flex;gap:6px;padding:0 16px 10px;flex-wrap:wrap;}
.qr-btn{background:#1A1A1A;border:1.5px solid #333;border-radius:20px;padding:6px 12px;color:#aaa;font-family:'Baloo 2',cursive;font-size:12px;cursor:pointer;transition:all .2s;white-space:nowrap;}
.qr-btn:hover{border-color:var(--saffron);color:var(--gold);}

/* ===== AI CHATBOT ===== */
</style>
</head>
<body>

<!-- NAV -->
<div class="nav">
  <button class="nb active" onclick="goPage('order',this)"><i>🛒</i>Order</button>
  <button class="nb" onclick="goPage('chat',this)"><i>🤖</i>AI Chat</button>
  <button class="nb" onclick="goPage('kitchen',this)"><i>👨‍🍳</i>Kitchen</button>
  <button class="nb" onclick="goPage('analytics',this)"><i>📊</i>Report</button>
  <button class="nb" onclick="goPage('admin',this)"><i>⚙️</i>Admin</butt
