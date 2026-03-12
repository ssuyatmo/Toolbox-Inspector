<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<title>Buku Kas Online</title>

<style>
body{
    font-family: Arial;
    background:#f4f6f9;
    padding:20px;
}

.container{
    max-width:900px;
    margin:auto;
    background:white;
    padding:20px;
    border-radius:10px;
    box-shadow:0 0 10px rgba(0,0,0,0.1);
}

h2{
    text-align:center;
}

input,select,button{
    padding:8px;
    margin:5px;
}

table{
    width:100%;
    border-collapse:collapse;
    margin-top:20px;
}

table,th,td{
    border:1px solid #ccc;
}

th,td{
    padding:10px;
    text-align:center;
}

.pemasukan{
    color:green;
}

.pengeluaran{
    color:red;
}

.saldo{
    font-size:20px;
    font-weight:bold;
    text-align:right;
}
</style>
</head>

<body>

<div class="container">

<h2>Buku Kas Online</h2>

<input type="date" id="tanggal">
<input type="text" id="keterangan" placeholder="Keterangan">
<input type="number" id="jumlah" placeholder="Jumlah">

<select id="tipe">
<option value="pemasukan">Pemasukan</option>
<option value="pengeluaran">Pengeluaran</option>
</select>

<button onclick="tambahData()">Simpan</button>

<h3>Saldo: Rp <span id="saldo">0</span></h3>

<table>
<thead>
<tr>
<th>Tanggal</th>
<th>Keterangan</th>
<th>Pemasukan</th>
<th>Pengeluaran</th>
<th>Aksi</th>
</tr>
</thead>

<tbody id="tabelKas">
</tbody>
</table>

</div>

<script>

let dataKas = JSON.parse(localStorage.getItem("kas")) || [];

function tampilData(){

let tabel = document.getElementById("tabelKas");
tabel.innerHTML = "";

let saldo = 0;

dataKas.forEach((data,index)=>{

let pemasukan = "";
let pengeluaran = "";

if(data.tipe=="pemasukan"){
pemasukan = data.jumlah;
saldo += parseInt(data.jumlah);
}else{
pengeluaran = data.jumlah;
saldo -= parseInt(data.jumlah);
}

tabel.innerHTML += `
<tr>
<td>${data.tanggal}</td>
<td>${data.keterangan}</td>
<td class="pemasukan">${pemasukan}</td>
<td class="pengeluaran">${pengeluaran}</td>
<td>
<button onclick="hapusData(${index})">Hapus</button>
</td>
</tr>
`;

});

document.getElementById("saldo").innerText = saldo;

}

function tambahData(){

let tanggal = document.getElementById("tanggal").value;
let keterangan = document.getElementById("keterangan").value;
let jumlah = document.getElementById("jumlah").value;
let tipe = document.getElementById("tipe").value;

if(tanggal=="" || keterangan=="" || jumlah==""){
alert("Isi semua data");
return;
}

dataKas.push({
tanggal:tanggal,
keterangan:keterangan,
jumlah:jumlah,
tipe:tipe
});

localStorage.setItem("kas",JSON.stringify(dataKas));

tampilData();

document.getElementById("keterangan").value="";
document.getElementById("jumlah").value="";

}

function hapusData(index){

dataKas.splice(index,1);

localStorage.setItem("kas",JSON.stringify(dataKas));

tampilData();

}

tampilData();

</script>

</body>
</html>
