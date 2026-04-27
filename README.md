<!DOCTYPE html><html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Amberlay Store - Auto Closing System</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
  <style>
    body {font-family:Poppins; background:#020617; color:#fff; margin:0}
    .container {padding:40px; max-width:600px; margin:auto}
    h1 {color:#22c55e}
    input, select {width:100%; padding:12px; margin:10px 0; border-radius:8px; border:none}
    .btn {padding:15px; background:#22c55e; color:#000; border:none; width:100%; border-radius:10px; font-weight:bold}
    .price-box {margin-top:15px; padding:15px; background:#0f172a; border-radius:10px}
  </style>
</head>
<body><div class="container">
  <h1>Order Jersey - Amberlay</h1>  <input type="text" id="nama" placeholder="Nama">
  <input type="text" id="wa" placeholder="Nomor WhatsApp">  <select id="paket" onchange="hitung()">
    <option value="">Pilih Paket</option>
    <option value="85000">Basic (Rp85.000)</option>
    <option value="95000">Pro (Rp95.000)</option>
    <option value="110000">Elite (Rp110.000)</option>
  </select>  <input type="number" id="jumlah" placeholder="Jumlah" oninput="hitung()">  <div class="price-box">
    <p>Total Harga:</p>
    <h2 id="total">Rp0</h2>
  </div><button class="btn" onclick="kirimWA()">Order Sekarang</button>

</div><script>
function hitung(){
  var harga = document.getElementById('paket').value;
  var jumlah = document.getElementById('jumlah').value;
  var total = harga * jumlah;

  if(!total) total = 0;

  document.getElementById('total').innerText = 'Rp' + total.toLocaleString('id-ID');
}

function kirimWA(){
  var nama = document.getElementById('nama').value;
  var wa = document.getElementById('wa').value;
  var paket = document.getElementById('paket').options[document.getElementById('paket').selectedIndex].text;
  var jumlah = document.getElementById('jumlah').value;
  var total = document.getElementById('total').innerText;

  var text = `Halo Amberlay Store%0A%0AOrder:%0A`+
             `Nama: ${nama}%0A`+
             `No WA: ${wa}%0A`+
             `Paket: ${paket}%0A`+
             `Jumlah: ${jumlah}%0A`+
             `Total: ${total}`;

  var url = "https://wa.me/6283869384789?text=" + text;
  window.open(url, '_blank');
}
</script></body>
</html>
