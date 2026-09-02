
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Toolbox Inspector Mobile</title>
    <style>
        :root {
            --primary: #007bff;
            --success: #25D366;
            --bg-app: #f0f2f5;
            --card-bg: #ffffff;
            --text-dark: #333333;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: #222;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
        }

        /* Container Simulasi HP */
        .mobile-frame {
            width: 100%;
            max-width: 414px; /* Ukuran standar Layar HP */
            height: 100vh;
            max-height: 896px;
            background-color: var(--bg-app);
            border-radius: 24px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.5);
            display: flex;
            flex-direction: column;
            overflow: hidden;
            position: relative;
        }

        /* Top Bar / App Header */
        .app-header {
            background: linear-gradient(135deg, #0056b3, #007bff);
            color: white;
            padding: 16px 20px;
            text-align: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .app-header h1 {
            font-size: 18px;
            font-weight: 700;
            letter-spacing: 0.5px;
        }

        /* Content Area */
        .app-content {
            flex: 1;
            overflow-y: auto;
            padding: 15px;
            padding-bottom: 80px; /* Space untuk bottom navbar */
        }

        /* Form & Cards UI */
        .mobile-card {
            background: var(--card-bg);
            border-radius: 12px;
            padding: 15px;
            margin-bottom: 15px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.08);
        }

        .mobile-card h2 {
            font-size: 14px;
            text-transform: uppercase;
            color: #666;
            margin-bottom: 12px;
            letter-spacing: 0.5px;
            border-bottom: 1px solid #eee;
            padding-bottom: 5px;
        }

        .form-group {
            margin-bottom: 12px;
        }

        .form-group label {
            display: block;
            font-size: 12px;
            font-weight: 600;
            color: var(--text-dark);
            margin-bottom: 4px;
        }

        .form-group input, .form-group select {
            width: 100%;
            padding: 10px;
            font-size: 14px;
            border: 1px solid #ddd;
            border-radius: 8px;
            background-color: #fafafa;
            outline: none;
        }

        .form-group input:focus, .form-group select:focus {
            border-color: var(--primary);
            background-color: #fff;
        }

        /* Quick Action Bar / Search */
        .search-box {
            position: sticky;
            top: 0;
            z-index: 10;
            background: var(--bg-app);
            padding-bottom: 10px;
        }

        .search-box input {
            width: 100%;
            padding: 10px 15px;
            border-radius: 20px;
            border: 1px solid #ccc;
            font-size: 13px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }

        /* Tool Item Row List */
        .tool-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 10px 0;
            border-bottom: 1px solid #f0f0f0;
        }

        .tool-item:last-child {
            border-bottom: none;
        }

        .tool-info {
            flex: 1;
            padding-right: 10px;
        }

        .tool-name {
            font-size: 13px;
            font-weight: 600;
            color: var(--text-dark);
        }

        .tool-meta {
            font-size: 11px;
            color: #888;
        }

        .tool-status select {
            padding: 6px;
            font-size: 12px;
            border-radius: 6px;
            border: 1px solid #ccc;
            font-weight: bold;
        }

        /* Floating Bottom Bar / Action */
        .bottom-action {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: #fff;
            padding: 12px 15px;
            box-shadow: 0 -2px 10px rgba(0,0,0,0.1);
            border-top-left-radius: 16px;
            border-top-right-radius: 16px;
        }

        .btn-wa {
            background-color: var(--success);
            color: white;
            border: none;
            width: 100%;
            padding: 12px;
            font-size: 15px;
            font-weight: bold;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(37, 211, 102, 0.3);
        }

        .btn-wa:active {
            transform: scale(0.98);
        }

        /* Badge Kondisi Colors */
        select.cond-B { color: #28a745; }
        select.cond-R { color: #dc3545; }
        select.cond-X { color: #fd7e14; }
        select.cond-N { color: #6c757d; }
    </style>
</head>
<body>

<div class="mobile-frame">
    <!-- Header App -->
    <div class="app-header">
        <h1>TOOLBOX INSPECTOR</h1>
    </div>

    <!-- Content Mobile -->
    <div class="app-content">
        <!-- Card Informasi Mekanik -->
        <div class="mobile-card">
            <h2>Informasi Pemeriksaan</h2>
            <div class="form-group">
                <label>Nama Mekanik</label>
                <select id="NamaMekanik">
                <option value="SUYATMO"</option>
                    <option value="ACHMAD MIRZA"</option>
                    <option value="ENRICO ATHA NARESWARA"</option>
                </select>
                <input type="text" id="namaMekanik" placeholder="Contoh: Ahmad">
            </div>
            <div class="form-group">
                <label>No. Tool Box</label>
                <select id="ToolBo">
                    <option value="BOX 05"</option>
                </select>
                <input type="text" id="noToolbox" placeholder="Contoh: TB-01">
            </div>
            <div class="form-group">
                <label>Status Waktu Inspeksi</label>
                <select id="waktuPengecekan">
                    <option value="SEBELUM PEMAKAIAN (PRE-USE)">SEBELUM PEMAKAIAN (PRE-USE)</option>
                    <option value="SESUDAH PEMAKAIAN (POST-USE)">SESUDAH PEMAKAIAN (POST-USE)</option>
                </select>
            </div>
        </div>

        <!-- Search Box -->
        <div class="search-box">
            <input type="text" id="searchInput" onkeyup="filterTools()" placeholder="🔍 Cari item kunci / ukuran...">
        </div>

        <!-- Card List Item Tools -->
        <div class="mobile-card">
            <h2>Daftar Tools (<span id="totalItems">0</span> Item)</h2>
            <div id="toolsListMobile">
                <!-- Data diisi otomatis oleh JavaScript -->
            </div>
        </div>
    </div>

    <!-- Floating Action Button di Bawah -->
    <div class="bottom-action">
        <button class="btn-wa" onclick="kirimKeWA()">
            📲 Kirim Laporan ke WA
        </button>
    </div>
</div>

<script>
const dataTools = [
    { no: 1, desc: "ADJUSTABLE WRENCH", size: "10\"", qty: 1 },
    { no: 2, desc: "OPEN END", size: "6X7", qty: 1 },
    { no: 2, desc: "OPEN END", size: "8X9", qty: 1 },
    { no: 2, desc: "OPEN END", size: "10X11", qty: 1 },
    { no: 2, desc: "OPEN END", size: "12X13", qty: 1 },
    { no: 2, desc: "OPEN END", size: "14X15", qty: 1 },
    { no: 2, desc: "OPEN END", size: "16X17", qty: 1 },
    { no: 2, desc: "OPEN END", size: "19X22", qty: 1 },
    { no: 2, desc: "OPEN END", size: "24X27", qty: 1 },
    { no: 2, desc: "OPEN END", size: "30X32", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "6X7", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "8X9", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "10X11", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "12X13", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "14X15", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "16X17", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "18X19", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "20X22", qty: 1 },
    { no: 3, desc: "RING SPANNER", size: "24X27", qty: 1 },
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
    { no: 5, desc: "HALFMOON WRENCH", size: "14X17", qty: 1 },
    { no: 5, desc: "HALFMOON WRENCH", size: "19X22", qty: 1 },
    { no: 6, desc: "FLARE NUT RING WRENCH", size: "17X19", qty: 1 },
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
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "24", qty: 1 },
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "25.5", qty: 1 },
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "27", qty: 1 },
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "30", qty: 1 },
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "32", qty: 1 },
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "36", qty: 1 },
    { no: 8, desc: "SOCKET WRENCH 3/4 INCH", size: "41", qty: 1 },
    { no: 9, desc: "SLIDING T HANDLE", size: "1/2\"", qty: 1 },
    { no: 10, desc: "REVERSIBLE RATCHET", size: "1/2\"", qty: 1 },
    { no: 11, desc: "EXTENSION BAR", size: "1/2X250", qty: 1 },
    { no: 12, desc: "EXTENSION BAR", size: "1/2X125", qty: 1 },
    { no: 13, desc: "CONVERTER", size: "1/2\"-3/4\"", qty: 1 },
    { no: 14, desc: "SLIDING T HANDLE", size: "3/4\"", qty: 1 },
    { no: 15, desc: "EXTENSION BAR", size: "3/4X400", qty: 1 },
    { no: 16, desc: "EXTENSION BAR", size: "3/4X200", qty: 1 },
    { no: 17, desc: "CARTRIDGE WRENCH", size: "-", qty: 1 },
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
    { no: 18, desc: "ALLENKEY SET", size: "2-12MM", qty: 1 },
    { no: 18, desc: "ALLENKEY SET", size: "14", qty: 1 },
    { no: 19, desc: "TORX BIT SET", size: "T9-T40", qty: "1 SET" },
    { no: 20, desc: "TES PEN", size: "2 PCS", qty: 2 },
    { no: 21, desc: "SCREW DRIVER", size: "(-)25", qty: 1 },
    { no: 21, desc: "SCREW DRIVER", size: "(+)25", qty: 1 },
    { no: 21, desc: "SCREW DRIVER", size: "(-)100", qty: 1 },
    { no: 21, desc: "SCREW DRIVER", size: "(+)100", qty: 1 },
    { no: 21, desc: "SCREW DRIVER", size: "(-)150", qty: 1 },
    { no: 21, desc: "SCREW DRIVER", size: "(+)150", qty: 1 },
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

function renderToolsList() {
    const container = document.getElementById("toolsListMobile");
    document.getElementById("totalItems").innerText = dataTools.length;
    container.innerHTML = "";

    dataTools.forEach((item, index) => {
        const itemHtml = `
            <div class="tool-item" id="item_${index}">
                <div class="tool-info">
                    <div class="tool-name">#${item.no} ${item.desc}</div>
                    <div class="tool-meta">Ukuran: ${item.size} | Qty: ${item.qty}</div>
                </div>
                <div class="tool-status">
                    <select id="cond_${index}" class="cond-B" onchange="updateColor(this)">
                        <option value="B">B (Baik)</option>
                        <option value="R">R (Rusak)</option>
                        <option value="X">X (Hilang)</option>
                        <option value="N">N (Nihil)</option>
                    </select>
                </div>
            </div>
        `;
        container.innerHTML += itemHtml;
    });
}

function updateColor(selectElem) {
    selectElem.className = 'cond-' + selectElem.value;
}

function filterTools() {
    const query = document.getElementById("searchInput").value.toLowerCase();
    dataTools.forEach((item, index) => {
        const elem = document.getElementById(`item_${index}`);
        const text = `${item.desc} ${item.size}`.toLowerCase();
        if (text.includes(query)) {
            elem.style.display = "flex";
        } else {
            elem.style.display = "none";
        }
    });
}

function kirimKeWA() {
    const mekanik = document.getElementById("namaMekanik").value;
    const toolbox = document.getElementById("noToolbox").value;
    const waktu = document.getElementById("waktuPengecekan").value;

    if (!mekanik || !toolbox) {
        alert("Mohon lengkapi Nama Mekanik dan Nomor Tool Box terlebih dahulu!");
        return;
    }

    let pesan = `*LAPORAN CHECKLIST TOOLBOX*\n`;
    pesan += `-----------------------------------\n`;
    pesan += `*Status:* ${waktu}\n`;
    pesan += `*Nama Mekanik:* ${mekanik}\n`;
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
    pesan += `_Dikirim via Mobile Toolbox Inspector App_`;

    const urlWA = `https://api.whatsapp.com/send?text=${encodeURIComponent(pesan)}`;
    window.open(urlWA, '_blank');
}

renderToolsList();
</script>

</body>
</html>
