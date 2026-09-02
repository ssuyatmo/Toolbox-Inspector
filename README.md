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
        table { width: 100%; border-collapse: collapse; margin-top: 15px; background: white; font-size: 12px; }
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
    // 1. ADJUSTABLE WRENCH
    { no: 1, desc: "ADJUSTABLE WRENCH", size: "10\"", qty: 1 },
    
    // 2. OPEN END
    { no: 2, desc: "OPEN END", size: "6X7", qty: 1 },
    { no: 2, desc: "OPEN END", size: "8X9", qty: 1 },
    { no: 2, desc: "OPEN END", size: "10X11", qty: 1 },
    { no: 2, desc: "OPEN END", size: "12X13", qty: 1 },
    { no: 2, desc: "OPEN END", size: "14X15", qty: 1 },
    { no: 2, desc: "OPEN END", size: "16X17", qty: 1 },
    { no: 2, desc: "OPEN END", size: "19X22", qty: 1 },
    { no: 2, desc: "OPEN END", size: "24X27", qty: 1 },
    { no: 2, desc: "OPEN END", size: "30X32", qty: 1 },
    
    // 3. RING SPANNER
    { no: 3, desc: "RING SPANNER", size: "6X7", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "8X9", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "10X11", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "12X13", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "14X15", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "16X17", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "18X19", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "20X22", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "24X27", qty: 1 },
    
    // 4. COMBINATION WRENCH
    { no: 4, desc: "COMBINATION WRENCH", size: "8", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "9", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "10", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "11", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "12", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "13", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "14", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "16", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "17", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "18", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "19", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "22", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "24", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "27", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "30", qty: 1 },
    { no: 4, desc: "COMBINATION WRENCH", size: "32", qty: 1 },
    
    // 5. HALFMOON WRENCH
    { no: 5, desc: "HALFMOON WRENCH", size: "14X17", qty: 1 },
    { no: 5, desc: "HALFMOON WRENCH", size: "19X22", qty: 1 },
    
    // 6. FLARE NUT RING WRENCH
    { no: 6, desc: "FLARE NUT RING WRENCH", size: "17X19", qty: 1 },
    
    // 7. SOCKET WRENCH 1/2 INCH
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "10", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "11", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "12", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "13", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "14", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "15", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "16", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "17", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "19", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "22", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "24", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "27", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "29", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "30", qty: 1 },
    { no: 7, desc: "SOCKET WRENCH 1/2 INCH", size: "32", qty: 1 },
    
    // 8. SOCKET WRENCH 3/4 INCH
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "24", qty: 1 },
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "25.5", qty: 1 },
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "27", qty: 1 },
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "30", qty: 1 },
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "32", qty: 1 },
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "36", qty: 1 },
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "41", qty: 1 },
    
    // 9-17. ACCESSORIES & SPECIAL WRENCHES
    { no: 9, desc: "SLIDING T HANDLE", size: "1/2\"", qty: 1 },
    { no: 10, desc: "REVERSIBLE RATCHET", size: "1/2\"", qty: 1 },
    { no: 11, desc: "EXTENSION BAR", size: "1/2X250", qty: 1 },
    { no: 12, desc: "EXTENSION BAR", size: "1/2X125", qty: 1 },
    { no: 13, desc: "CONVERTER", size: "1/2\"-3/4\"", qty: 1 },
    { no: 14, desc: "SLIDING T HANDLE", size: "3/4\"", qty: 1 },
    { no: 15, desc: "EXTENSION BAR", size: "3/4X400", qty: 1 },
    { no: 16, desc: "EXTENSION BAR", size: "3/4X200", qty: 1 },
    { no: 17, desc: "CARTRIDGE WRENCH", size: "-", qty: 1 },
    
    // PLIERS
    { no: 17, desc: "PLIER, WATER PUMP", size: "240", qty: 1 },
    { no: 17, desc: "PLIER, COMBINATION", size: "185", qty: 1 },
    { no: 17, desc: "PLIER, GRIP UNIVERSAL", size: "250", qty: 1 },
    { no: 17, desc: "PLIER SNIPE NOSE", size: "160", qty: 1 },
    { no: 17, desc: "PLIER, ROUND LONG NOSE", size: "160", qty: 1 },
    { no: 17, desc: "DIAGONAL CUTTING NIPPER", size: "165", qty: 1 },
    { no: 17, desc: "PLIER, CIRCLIP STRIGHT EX", size: "175", qty: 1 },
    { no: 17, desc: "PLIER, CIRCLIP ANGLE EX", size: "165", qty: 1 },
    { no: 17, desc: "PLIER, CIRCLIP STRIGHT IN", size: "180", qty: 1 },
    { no: 17, desc: "PLIER CIRCLIP ANGLE IN", size: "170", qty: 1 },
    
    // 18. ALLENKEY SET
    { no: 18, desc: "ALLENKEY SET", size: "2-12MM", qty: 1 },
    { no: 18, desc: "ALLENKEY SET", size: "14", qty: 1 },
    
    // 19. TORX BIT SET
    { no: 19, desc: "TORX BIT SET", size: "T9-T40", qty: "1 SET" },
    
    // 20. TES PEN
    { no: 20, desc: "TES PEN", size: "2 PCS", qty: 2 },
    
    // 21. SCREW DRIVER
    { no: 21, desc: "SCREW DRIVER", size: "(-)25", qty: 1 },
    { no: 21, desc: "SCREW DRIVER", size: "(+)25", qty: 1 },
    { no: 21, desc: "SCREW DRIVER", size: "(-)100", qty: 1 },
    { no: 21, desc: "SCREW DRIVER", size: "(+)100", qty: 1 },
    { no: 21, desc: "SCREW DRIVER", size: "(-)150", qty: 1 },
    { no: 21, desc: "SCREW DRIVER", size: "(+)150", qty: 1 },
    
    // 22-29. OTHER TOOLS
    { no: 22, desc: "FILE FLAT", size: "250", qty: 1 },
    { no: 23, desc: "FILE ROUND", size: "250", qty: 1 },
    { no: 24, desc: "HAMMER RUBBER", size: "3LBS", qty: 1 },
    { no: 24, desc: "HAMMER NYLON", size: "40 MM", qty: 1 },
    { no: 25, desc: "PRY BAR", size: "450", qty: 1 },
    { no: 26, desc: "CHISEL PUNCH SET", size: "6 PCS", qty: 1 },
    { no: 27, desc: "SCRAPER, FLAT", size: "50", qty: 1 },
    { no: 27, desc: "SCRAPER TRINGULAR", size: "-", qty: 1 },
    { no: 28, desc: "CRIMPING TOOL", size: "-", qty: 1 },
    { no: 29, desc: "TOOL BOX", size: "-", qty: 1 }
];

function renderTable() {
    const tbody = document.getElementById("toolsList");
    tbody.innerHTML = "";
    dataTools.forEach((item, index) => {
        let row = `<tr>
            <td style="text-align:center">${item.no}</td>
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
