<html>
<head>
  <style>
    * {
      box-sizing: border-box;
    }

    /* Create four columns of equal width */
    .columns {
      float: left;
      width: 25%;
      padding: 8px;
    }

    /* Style the list */
    .price {
      list-style-type: none;
      border: 1px solid #eee;
      margin: 0;
      padding: 0;
      -webkit-transition: 0.3s;
      transition: 0.3s;
    }

    /* Add shadows on hover */
    .price:hover {
      box-shadow: 0 8px 12px 0 rgba(0,0,0,0.2)
    }

    /* Pricing header */
    .price .header {
      background-color: #111;
      color: white;
      font-size: 25px;
    }

    /* List items */
    .price li {
      border-bottom: 1px solid #eee;
      padding: 20px;
      text-align: center;
    }

    /* Grey list item */
    .price .grey {
      background-color: #eee;
      font-size: 20px;
    }

    /* The "Sign Up" button */
    .button {
      background-color: #04AA6D;
      border: none;
      color: white;
      padding: 10px 25px;
      text-align: center;
      text-decoration: none;
      font-size: 18px;
    }

    /* Change the width of the four columns to 100% (to stack horizontally on small screens) */
    @media only screen and (max-width: 600px) {
      .columns {
        width: 100%;
      }
    }

    /* Add a toggle switch for monthly/yearly plans */
    .switch {
      position: relative;
      display: inline-block;
      width: 60px;
      height: 34px;
    }

    /* Hide default HTML checkbox */
    .switch input {
      opacity: 0;
      width: 0;
      height: 0;
    }

    /* The slider */
    .slider {
      position: absolute;
      cursor: pointer;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: #ccc;
      -webkit-transition: .4s;
      transition: .4s;
    }

    .slider:before {
      position: absolute;
      content: "";
      height: 26px;
      width: 26px;
      left: 4px;
      bottom: 4px;
      background-color: white;
      -webkit-transition: .4s;
      transition: .4s;
    }

    input:checked + .slider {
      background-color: #2196F3;
    }

    input:focus + .slider {
      box-shadow: 0 0 1px #2196F3;
    }

    input:checked + .slider:before {
      -webkit-transform: translateX(26px);
      -ms-transform: translateX(26px);
      transform: translateX(26px);
    }

    /* Rounded sliders */
    .slider.round {
      border-radius: 34px;
    }

    .slider.round:before {
      border-radius: 50%;
    }

    /* Add a select element for currency and unit customization */
    select {
      width: 100%;
      padding: 16px 20px;
      border: none;
      border-radius: 4px;
      background-color: #f1f1f1;
    }
  </style>
</head>
<body>

<h2>Pricing Table</h2>
<p>Switch between monthly and yearly plans:</p>

<label class="switch">
  <input type="checkbox" id="toggle" onclick="togglePrices()">
  <span class="slider round"></span>
</label>

<p>Select your preferred currency and unit:</p>

<select id="currency" onchange="changeCurrency()">
  <option value="$">$ USD</option>
  <option value="€">€ EUR</option>
  <option value="₹">₹ INR</option>
</select>

<select id="unit" onchange="changeUnit()">
  <option value="GB">GB</option>
  <option value="TB">TB</option>
  <option value="PB">PB</option>
</select>

<div class="columns">
  <ul class="price">
    <li class="header">Basic</li>
    <li class="grey" id="basic-price">$ 9.99 / month</li>
    <li id="basic-storage">10 GB Storage</li>
    <li id="basic-emails">10 Emails</li>
    <li id="basic-domains">10 Domains</li>
    <li id="basic-bandwidth">1 GB Bandwidth</li>
    <li class="grey"><a href="#" class="button">Sign Up</a></li>
  </ul>
</div>

<div class="columns">
  <ul class="price">
    <li class="header" style="background-color:#04AA6D">Pro</li>
    <li class="grey" id="pro-price">$ 24.99 / month</li>
    <li id="pro-storage">25 GB Storage</li>
    <li id="pro-emails">25 Emails</li>
    <li id="pro-domains">25 Domains</li>
    <li id="pro-bandwidth">2 GB Bandwidth</li>
    <li class="grey"><a href="#" class="button">Sign Up</a></li>
  </ul>
</div>

<div class="columns">
  <ul class="price">
    <li class="header">Premium</li>
    <li class="grey" id="premium-price">$ 49.99 / month</li>
    <li id="premium-storage">50 GB Storage</li>
    <li id="premium-emails">50 Emails</li>
    <li id="premium-domains">50 Domains</li>
    <li id="premium-bandwidth">5 GB Bandwidth</li>
    <li class="grey"><a href="#" class="button">Sign Up</a></li>
  </ul>
</div>

<div class="columns">
  <ul class="price">
    <li class="header" style="background-color:#a9a9a9">Ultimate</li>
    <li class="grey" id="ultimate-price">$ 99.99 / month</li>
    <li id="ultimate-storage">100 GB Storage</li>
    <li id="ultimate-emails">100 Emails</li>
    <li id="ultimate-domains">100 Domains</li>
    <li id="ultimate-bandwidth">10 GB Bandwidth</li>
    <li class="grey"><a href="#" class="button">Sign Up</a></li>
  </ul>
</div>

<script>
  // A function to toggle between monthly and yearly prices
  function togglePrices() {
    var x = document.getElementById("toggle").checked;
    var basic = document.getElementById("basic-price");
    var pro = document.getElementById("pro-price");
    var premium = document.getElementById("premium-price");
    var ultimate = document.getElementById("ultimate-price");
    if (x) {
      basic.innerHTML = "$ 99.99 / year";
      pro.innerHTML = "$ 249.99 / year";
      premium.innerHTML = "$ 499.99 / year";
      ultimate.innerHTML = "$ 999.99 / year";
    } else {
      basic.innerHTML = "$ 9.99 / month";
      pro.innerHTML = "$ 24.99 / month";
      premium.innerHTML = "$ 49.99 / month";
      ultimate.innerHTML = "$ 99.99 / month";
    }
  }

  // A function to change the currency symbol
  function changeCurrency() {
    var y = document.getElementById("currency").value;
    var basic = document.getElementById("basic-price");
    var pro = document.getElementById("pro-price");
    var premium = document.getElementById("premium-price");
    var ultimate = document.getElementById("ultimate-price");
    basic.innerHTML = y + basic.innerHTML.slice(1);
    pro.innerHTML = y + pro.innerHTML.slice(1);
    premium.innerHTML = y + premium.innerHTML.slice(1);
    ultimate.innerHTML = y + ultimate.innerHTML.slice(1);
  }

  // A function to change the unit of storage and bandwidth
  function changeUnit() {
    var z = document.getElementById("unit").value;
    var basic_storage = document.getElementById("basic-storage");
    var pro_storage = document.getElementById("pro-storage");
    var premium_storage = document.getElementById("premium-storage");
    var ultimate_storage = document.getElementById("ultimate-storage");
    var basic_bandwidth = document.getElementById("basic-bandwidth");
    var pro_bandwidth = document.getElementById("pro-bandwidth");
    var premium_bandwidth = document.getElementById("premium-bandwidth");
    var ultimate_bandwidth = document.getElementById("ultimate-bandwidth");
    basic_storage.innerHTML = basic_storage.innerHTML.slice(0, -2) + z + " Storage";
    pro_storage.innerHTML = pro_storage.innerHTML.slice(0, -2) + z + " Storage";
    premium_storage.innerHTML = premium_storage.innerHTML.slice(0, -2) + z + " Storage";
    ultimate_storage.innerHTML = ultimate_storage.innerHTML.slice(0, -2) + z + " Storage";
    basic_bandwidth.innerHTML = basic_bandwidth.innerHTML.slice(0, -2)
