// ==UserScript==
// @name         InvoicTitle
// @namespace    http://print.jiqinyun.com/
// @version      0.17
// @description  Invoice Title Change Private By hjg
// @author       HuangjianGuo
// @include        *://print.jiqinyun.com/html/erp/stockOrder*
// @include        *://yun.jiqinyun.com/erp*
// @grant        GM_setValue
// @license      MIT2.0
// ==/UserScript==

let flg=true;
let counter_fix=0;
let counter_cus=0;
let T_arr=new Array({"name": "svlis","desc": "福建西威联电气有限公司"},{"name": "zxwy","desc": "福州市闽侯振兴炜业机械有限公司"},{"name": "suel","desc": "福州速易联电气有限公司"});
let I_tail='(销售发货单)';
(function() {
    'use strict';
    setTimeout(function(){
    let invoice_fix_event=document.querySelector("h1.companyName.headTitle");
    if (!invoice_fix_event){
        console.log("fixed element not found");
    }else{
     invoice_fix_event.addEventListener("click",function(){
             let index=counter_fix%T_arr.length;
             invoice_fix_event.innerHTML=unescape(T_arr[index].desc);
             counter_fix++;
     })};
    let invoice_custom_event=document.querySelector("div.head>p.title");
    if(!invoice_custom_event){
        console.log("custom element not found");
    }else{
    console.log("custom found");
             invoice_custom_event.addEventListener("click",function(){
             let index=counter_cus%T_arr.length;
             invoice_custom_event.innerHTML=unescape(T_arr[index].desc+I_tail);
             counter_cus++;
     })
   } //end else
  },300)

})();
