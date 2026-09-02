<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pengecekan Tool Box</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 15px; background-color: #f4f6f9; }
        .card { background: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 4px rgba(0,0,0,0.1); margin-bottom: 15px; }
        h2, h3 { text-align: center; color: #333; margin-top: 5px; }
        label { font-weight: bold; display: block; margin-top: 10px; }
        input, select { width: 100%; padding: 8px; margin-top: 5px; box-sizing: border-box; border: 1px solid #ccc; border-radius: 4px; }
        table { width: 100%; border-collapse: collapse; margin-top: 15px; background: white; font-size: 13px; }
        th, td { border: 1px solid #ddd; padding: 6px; text-align: left; }
        th { background-color: #007bff; color: white; text-align: center; }
        .btn-wa { background-color: #25D366; color: white; border: none; padding: 12px; width: 100%; font-size: 16px; font-weight: bold; border-radius: 5px; cursor: pointer; margin-top: 15px; }
        .btn-wa:hover { background-color: #1ebc57; }
    </style>
</head>
<body>

<div class="card">
    <h2>INSPEKSI TOOL BOX</h2>
    <label>Nama Mekanik:</label>
    <input type="text" id="namaMekanik" placeholder="Masukkan nama">
    
    <label>NRP:</label>
    <input type="text" id="nrp" placeholder="Masukkan NRP">
    
    <label>Nomor Tool Box:</label>
    <input type="text" id="noToolbox" placeholder="Contoh: TB-01">

    <label>Waktu Pengecekan:</label>
    <select id="waktuPengecekan">
        <option value="SEBELUM PEMAKAIAN (PRE-USE)">SEBELUM PEMAKAIAN (PRE-USE)</option>
        <option value="SESUDAH PEMAKAIAN (POST-USE)">SESUDAH PEMAKAIAN (POST-USE)</option>
    </select>
</div>

<div class="card">
    <h3>Daftar Item Tools</h3>
    <small>*Keterangan Kondisi: B (Baik), R (Rusak), X (Hilang), N (Nihil)</small>
    
    <table id="toolsTable">
        <thead>
            <tr>
                <th>No</th>
                <th>Deskripsi</th>
                <th>Ukuran</th>
                <th>Qty</th>
                <th>Kondisi</th>
            </tr>
        </thead>
        <tbody id="toolsList">
            <!-- Data tools diisi via JS -->
        </tbody>
    </table>

    <button class="btn-wa" onclick="kirimKeWA()">Kirim Laporan ke WA</button>
</div>

<script>
const dataTools = [
    { no: 1, desc: "Adjustable Wrench", size: "10\"", qty: 1 },
    { no: 2, desc: "Open End Wrench", size: "6x7", qty: 1 },
    { no: 2, desc: "Open End Wrench", size: "8x9", qty: 1 },
    { no: 2, desc: "Open End Wrench", size: "10x11", qty: 1 },
    { no: 2, desc: "Open End Wrench", size: "12x13", qty: 1 },
    { no: 2, desc: "Open End Wrench", size: "14x15", qty: 1 },
    { no: 2, desc: "Open End Wrench", size: "16x17", qty: 1 },
    { no: 2, desc: "Open End Wrench", size: "19x22", qty: 1 },
    { no: 2, desc: "Open End Wrench", size: "24x27", qty: 1 },
    { no: 2, desc: "Open End Wrench", size: "30x32", qty: 1 },
    { no: 3, desc: "Ring Spanner", size: "6x7", qty: 1 },
    { no: 3, desc: "Ring Spanner", size: "8x9", qty: 1 },
    { no: 3, desc: "Ring Spanner", size: "10x11", qty: 1 },
    { no: 3, desc: "Ring Spanner", size: "12x13", qty: 1 },
    { no: 3, desc: "Ring Spanner", size: "14x15", qty: 1 },
    { no: 3, desc: "Ring Spanner", size: "16x17", qty: 1 },
    { no: 3, desc: "Ring Spanner", size: "18x19", qty: 1 },
    { no: 3, desc: "Ring Spanner", size: "20x22", qty: 1 },
    { no: 3, desc: "Ring Spanner", size: "24x27", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "8", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "9", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "10", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "11", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "12", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "13", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "14", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "16", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "17", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "18", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "19", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "22", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "24", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "27", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "30", qty: 1 },
    { no: 4, desc: "Combination Wrench", size: "32", qty: 1 },
    { no: 5, desc: "Halfmoon Wrench", size: "14x17", qty: 1 },
    { no: 5, desc: "Halfmoon Wrench", size: "19x22", qty: 1 },
    { no: 6, desc: "Flare Nut Ring Wrench", size: "17x19", qty: 1 },
    { no: 7, desc: "Socket Wrench 1/2\"", size: "10-32 (13 Pcs)", qty: 13 },
    { no: 8, desc: "Socket Wrench 3/4\"", size: "24-41 (7 Pcs)", qty: 7 },
    { no: 9, desc: "Sliding T Handle", size: "1/2\"", qty: 1 },
    { no: 10, desc: "Reversible Ratchet", size: "1/2\"", qty: 1 },
    { no: 11, desc: "Extension Bar", size: "1/2x250", qty: 1 },
    { no: 12, desc: "Extension Bar", size: "1/2x125", qty: 1 },
    { no: 13, desc: "Converter", size: "1/2-3/4", qty: 1 },
    { no: 14, desc: "Sliding T Handle", size: "3/4\"", qty: 1 },
    { no: 15, desc: "Extension Bar", size: "3/4x400", qty: 1 },
    { no: 16, desc: "Extension Bar", size: "3/4x200", qty: 1 },
    { no: 17, desc: "Cartridge Wrench", size: "-", qty: 1 },
    { no: 18, desc: "Plier Set (Waterpump/Comb/Nose/Circlip)", size: "Variasi", qty: 9 },
    { no: 19, desc: "Allen Key Set", size: "2-12mm & 14", qty: 2 },
    { no: 20, desc: "Torx Bit Set", size: "T9-T40", qty: 1 },
    { no: 21, desc: "Tes Pen", size: "2 Pcs", qty: 2 },
    { no: 22, desc: "Screw Driver Set", size: "(-) & (+)", qty: 6 },
    { no: 23, desc: "File Flat / Round", size: "250", qty: 2 },
    { no: 24, desc: "Hammer Rubber / Nylon", size: "Variasi", qty: 2 },
    { no: 25, desc: "Pry Bar / Chisel / Scraper / Crimping", size: "Variasi", qty: 5 },
    { no: 26, desc: "Tool Box Unit", size: "-", qty: 1 }
];

function renderTable() {
    const tbody = document.getElementById("toolsList");
    tbody.innerHTML = "";
    dataTools.forEach((item, index) => {
        let row = `<tr>
            <td style="text-align:center">${index + 1}</td>
            <td>${item.desc}</td>
            <td>${item.size}</td>
            <td style="text-align:center">${item.qty}</td>
            <td>
                <select id="cond_${index}">
                    <option value="B">B (Baik)</option>
                    <option value="R">R (Rusak)</option>
                    <option value="X">X (Hilang)</option>
                    <option value="N">N (Nihil)</option>
                </select>
            </td>
        </tr>`;
        tbody.innerHTML += row;
    });
}

function kirimKeWA() {
    const mekanik = document.getElementById("namaMekanik").value;
    const nrp = document.getElementById("nrp").value;
    const toolbox = document.getElementById("noToolbox").value;
    const waktu = document.getElementById("waktuPengecekan").value;

    if (!mekanik || !nrp || !toolbox) {
        alert("Mohon isi Nama Mekanik, NRP, dan Nomor Tool Box terlebih dahulu!");
        return;
    }

    let pesan = `*LAPORAN CHECKLIST TOOLBOX*\n`;
    pesan += `-----------------------------------\n`;
    pesan += `*Status:* ${waktu}\n`;
    pesan += `*Nama Mekanik:* ${mekanik}\n`;
    pesan += `*NRP:* ${nrp}\n`;
    pesan += `*No. Tool Box:* ${toolbox}\n`;
    pesan += `-----------------------------------\n`;
    pesan += `*DETAIL KONDISI TOOLS:*\n\n`;

    let itemBermasalah = [];

    dataTools.forEach((item, index) => {
        const kondisi = document.getElementById(`cond_${index}`).value;
        if (kondisi !== "B") {
            itemBermasalah.push(`• ${item.desc} (${item.size}): *${kondisi}*`);
        }
    });

    if (itemBermasalah.length === 0) {
        pesan += `✅ *Semua item lengkap dan dalam kondisi BAIK (B).*\n`;
    } else {
        pesan += `⚠️ *Catatan Item Rusak/Hilang/Nihil:*\n`;
        pesan += itemBermasalah.join('\n') + `\n`;
    }

    pesan += `\n-----------------------------------\n`;
    pesan += `_Dikirim via Web App Toolbox Inspector_`;

    const urlWA = `https://api.whatsapp.com/send?text=${encodeURIComponent(pesan)}`;
    window.open(urlWA, '_blank');
}

renderTable();
</script>

</body>
</html>
