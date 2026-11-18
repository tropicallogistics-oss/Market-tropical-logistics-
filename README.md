html
<!DOCTYPE html>
<html>
<head>
<title>Market + Tropical Logistics</title>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body{font-family:Arial;padding:0;margin:0;background:#f4f4f4}
header{background:#0a7a42;color:#fff;padding:20px;text-align:center}
.product{background:#fff;padding:15px;margin:10px;border-radius:10px}
button{background:#25D366;color:#fff;border:none;padding:10px 15px;border-radius:5px;cursor:pointer;width:100%}
input{width:95%;padding:10px;margin:5px}
.section{padding:10px}
</style>
</head>
<body>
<header>
<h1>MARKET + TROPICAL LOGISTICS</h1>
<p>Marketplace + Delivery | Eldoret & Nairobi</p>
</header>

<div class="section">
<h2>Bidhaa Zetu</h2>
<div id="products"></div>

<h2>Add Your Goods (Kwa Seller)</h2>
<input id="productName" placeholder="Jina la Bidhaa e.g Mchele 5kg">
<input id="price" placeholder="Bei e.g 750" type="number">
<input id="sellerName" placeholder="Jina lako">
<input id="location" placeholder="Location e.g Eldoret">
<button onclick="addProductLocal()">Add Product</button>
</div>

<script>
let products = [
  {name:"Mchele 5kg", price:750, seller:"Mama Njeri", location:"Eldoret"},
  {name:"Mafuta 2L", price:600, seller:"Njeri Store", location:"Eldoret"},
  {name:"Matunda Fresh Box", price:900, seller:"Tropical Farm", location:"Nairobi"}
];
function showProducts(){
  let html = "";
  products.forEach(p => {
    html += `<div class="product"><h3>${p.name} - Ksh ${p.price}</h3><p>Seller: ${p.seller} | ${p.location}</p><button onclick="orderWhatsApp('${p.name}')">Order via WhatsApp</button></div>`;
  });
  document.getElementById('products').innerHTML = html;
}
function addProductLocal(){
  let name = document.getElementById('productName').value;
  let price = document.getElementById('price').value;
  let seller = document.getElementById('sellerName').value;
  let loc = document.getElementById('location').value;
  if(!name || !price){alert("Jaza jina na bei"); return;}
  products.push({name:name, price:price, seller:seller, location:loc});
  showProducts();
  alert("Bidhaa imeongezwa!");
}
function orderWhatsApp(productName){
  let msg = "Habari Market + Tropical, nataka ku-order: " + productName;
  window.open("https://wa.me/254741841463?text=" + encodeURIComponent(msg));
}
showProducts();
</script>
</body>
</html>
