<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AUI DATA HUB - VTU</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:Arial}
body{background:#0a0e27;color:white;min-height:100vh}
.hidden{display:none!important}
.header{background:linear-gradient(135deg,#667eea,#764ba2);padding:20px;text-align:center;position:sticky;top:0;z-index:10}
.logo{font-size:26px;font-weight:bold}
.card{background:#151a33;margin:12px;padding:18px;border-radius:14px;border:1px solid #242c56}
.btn{background:#00ff88;color:#000;padding:13px;border:none;border-radius:10px;width:100%;font-weight:bold;font-size:16px;margin-top:10px;cursor:pointer}
.btn-dark{background:#2a335a;color:white}
input,select{width:100%;padding:13px;margin:8px 0;border-radius:10px;border:1px solid #2a335a;background:#0f1430;color:white}
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.service{background:#1d2342;padding:18px;border-radius:12px;text-align:center;border:1px solid #2a335a;cursor:pointer}
.balance-box{background:linear-gradient(135deg,#00ff88,#00cc6a);color:#000;padding:20px;border-radius:14px;margin:12px;text-align:center}
.balance-amount{font-size:32px;font-weight:bold}
.modal{position:fixed;top:0;left:0;right:0;bottom:0;background:rgba(0,0,0,0.85);display:flex;align-items:center;justify-content:center;padding:20px;z-index:100}
.modal-box{background:#151a33;width:100%;max-width:400px;padding:25px;border-radius:16px}
.tab{display:flex;gap:10px;margin:15px 0}
.tab div{flex:1;text-align:center;padding:10px;border-radius:8px;background:#1d2342;cursor:pointer}
.tab .active{background:#667eea}
.pin-dots{display:flex;gap:10px;justify-content:center;margin:15px 0}
.pin-dots span{width:14px;height:14px;border-radius:50%;background:#2a335a;display:block}
.pin-dots span.filled{background:#00ff88}
.num-pad{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-top:15px}
.num-pad button{padding:18px;font-size:20px;border-radius:10px;border:none;background:#1d2342;color:white;font-weight:bold}
</style>
</head>
<body>
<div id="authScreen">
<div class="header"><div class="logo">AUI DATA HUB</div><p>ATBU Azare VTU Center</p></div>
<div class="card">
<div class="tab"><div id="loginTab" class="active" onclick="switchAuth('login')">Login</div><div id="regTab" onclick="switchAuth('register')">Register</div></div>
<div id="loginForm"><input id="loginPhone" placeholder="Phone Number"><input id="loginPass" type="password" placeholder="Password"><button class="btn" onclick="doLogin()">Login</button></div>
<div id="regForm" class="hidden"><input id="regName" placeholder="Full Name"><input id="regPhone" placeholder="Phone 080..."><input id="regPass" type="password" placeholder="Create Password"><button class="btn" onclick="doRegister()">Create Account</button></div>
</div>
</div>
<div id="pinSetupScreen" class="hidden">
<div class="header"><div class="logo">Create Transaction PIN</div><p>4-digit PIN for payments</p></div>
<div class="card" style="text-align:center"><div class="pin-dots" id="pinDots"><span></span><span></span><span></span><span></span></div><div class="num-pad"><button onclick="addPin('1')">1</button><button onclick="addPin('2')">2</button><button onclick="addPin('3')">3</button><button onclick="addPin('4')">4</button><button onclick="addPin('5')">5</button><button onclick="addPin('6')">6</button><button onclick="addPin('7')">7</button><button onclick="addPin('8')">8</button><button onclick="addPin('9')">9</button><button onclick="clearPin()">C</button><button onclick="addPin('0')">0</button><button onclick="delPin()">⌫</button></div><button class="btn" onclick="savePin()">Save PIN</button></div>
</div>
<div id="mainApp" class="hidden">
<div class="header"><div style="display:flex;justify-content:space-between"><div class="logo" style="font-size:20