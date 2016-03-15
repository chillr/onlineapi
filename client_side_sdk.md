# Client Side SDK

This document explains the steps to implement the client side Chillr SDK widget onto a webpage.

## 1.Include the Javascript snippet

```javascript
(function(global) {
  function async_load(){
    var s = document.createElement("script");
    s.type = "text/javascript";
    s.async = true;
    var theUrl = "https://onlineapi.chillr.in//online-sdk/assets/js/init.min.js";
    s.src = theUrl;
    var embedder = document.getElementById("chillr-sdk-embedder-5b8cf3a4-b0f0-13e9-3737-d5a159268ae6");
    embedder.parentNode.insertBefore(s, embedder);
  }
  if (window.attachEvent){
    window.attachEvent("onload", async_load);
  }
  else{
    window.addEventListener("load", async_load, false);
  }
})(this);
```

## 2. Include the button & wrapper elements

```html
<a href="#" id="chillr-button">Pay using Chillr</a>

<div id="chillr-element-wrapper"></div>
```

| Element | Description |
| ------- | ------------|
| chillr-button| This is the element that the user clicks to initiate a payment.|
| chillr-element-wrapper | Chillr transaction card gets appended here.|


## 3. Initialize the widget

The merchant has to call the following method in order to initiate the widget. The values of the parameters _qr\_code_, _alpha_code_,_id_, _amount_, _expiry\_time_ and _created\_at_ are available from the response of [the server side API call](* [Chapter 1](chapter1.md).

```javascript
window.chillrOnlineSDK.chillrTransactionCreated(transaction_id, transaction_code, id, amount, expiry_time, created_at);
```

We also provide an interface to lock the pay with chillr button which has to be necessarily implemented by the merchant.

```javascript
window.chillrOnlineSDK.chillrButtonEnabled
```
