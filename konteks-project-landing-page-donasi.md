# Konteks Project & Dokumen Spesifikasi Teknis: Landing Page Donasi "Konsep Undangan Digital"

## 1. Ringkasan Eksekutif & Konsep Visual
Landing page ini dirancang dengan mengadopsi **UI/UX pola Web Undangan Pernikahan Digital (Digital Wedding Invitation)** yang diadaptasi penuh untuk kemanusiaan dan penggalangan dana (Fundraising). Konsep ini dipilih karena memiliki alur emosional yang kuat, visual yang elegan, serta fitur interaktif yang sangat memudahkan pengguna (donatur) untuk membaca kisah, menyalin rekening, hingga mengirimkan doa dan konfirmasi.

### Elemen Kunci Konsep "Undangan Digital" untuk Donasi:
1. **Screen Cover (Welcome Screen & Gate):** Layar pembuka berdesain elegan dengan tombol **"Buka Halaman Donasi" / "Mari Berbagi"**. Saat diklik, layar akan terbuka (scroll-enable) disertai transisi halus.
2. **Backsound Audio (Opsional):** Fitur pemutar instrumen Islami yang menenangkan atau lantunan shalawat (dengan kontrol mute/unmute floating).
3. **Desain Ornamen Islami Modern:** Penggunaan aksen lengkungan kubah (Islamic Arch), motif geometris halus, dan perpaduan warna hangat yang memberi kesan terpercaya dan menenangkan.
4. **Fitur "Amplop Digital" (Dompet Kebaikan):** Kartu rekening bank dengan tombol **"Salin Rekening" (Copy to Clipboard)** yang memberikan feedback visual instan (*"Nomor rekening berhasil disalin!"*) untuk memudahkan transfer mobile banking.
5. **Fitur "Buku Tamu / Doa & Harapan":** Kolom interaktif di mana donatur dapat menuliskan nama, doa, dan harapan bagi para santri serta pembangunan kobong.
6. **Integrasi Peta & Kontak Langsung:** Alamat lengkap yang terhubung dengan tautan navigasi Google Maps serta tombol Floating CTA menuju WhatsApp Panitia.

---

## 2. Desain Sistem (Design System & Branding)

### A. Palet Warna (Color Palette)
* **Primary (Emerald Green):** `#065f46` *(Melambangkan kedamaian, keislaman, dan pertumbuhan)*
* **Secondary (Warm Gold / Amber):** `#d97706` *(Melambangkan kemuliaan dan keberkahan)*
* **Background (Soft Cream / Sand):** `#fdfbf7` dan `#f3f4f6` *(Memberikan kenyamanan membaca pada layar HP)*
* **Text Primary (Deep Slate):** `#1e293b`
* **Text Muted:** `#64748b`

### B. Tipografi (Typography)
* **Teks Arab:** `Amiri` atau `Lateef` (Google Fonts) – Agar lafal Basmalah dan ayat terlihat indah dan mudah dibaca.
* **Heading / Judul:** `Playfair Display` atau `Cinzel` – Memberikan kesan elegan dan formal khas undangan.
* **Body / UI Text:** `Plus Jakarta Sans` atau `Inter` – Tampilan modern, bersih, dan optimal untuk keterbacaan di mobile.

---

## 3. Struktur Komponen & Alur Halaman (Page Structure)

```
[Landing Page Architecture]
 ├── 1. Hero Cover Gate (Fixed Overlay -> Fade Out on Click)
 │       ├── Judul Kampanye & Nama Pesantren
 │       └── Tombol "Buka Halaman / Mari Berbagi"
 ├── 2. Mukadimah & Salam
 │       ├── Kaligrafi Basmalah
 │       └── Salam & Pengantar Doa
 ├── 3. Tentang Pembangunan (The Story)
 │       ├── Detail Lokasi & Tujuan (Kobong Santri Putra Takhosus/Salafi & Penghapal Al-Qur'an)
 │       └── Filosofi Amal Jariyah
 ├── 4. Dompet Kebaikan / Amplop Digital (Donation Section)
 │       ├── Bank BJB (Ishaq Muhamad) + Tombol Salin
 │       ├── Bank BRI (Ishaq Muhamad) + Tombol Salin
 │       ├── Bank BRI (Yayasan Raudhatul Mubarakah) + Tombol Salin
 │       └── Bank BJB (Yayasan Raudhatul Mubarakah) + Tombol Salin
 ├── 5. Lokasi & Silaturahmi (Alamat & Google Maps)
 │       ├── Alamat Lengkap Sukabumi
 │       └── Tombol "Petunjuk Arah Google Maps"
 ├── 6. Doa & Harapan (Buku Tamu Digital)
 │       └── List Doa Para Dermawan (Real-time/Mock Component)
 ├── 7. Penutup & Jazakumullah
 └── 8. Floating Action Buttons (FAB)
         ├── Tombol Konfirmasi WhatsApp (085659401700)
         └── Kontrol Musik / Mute Audio
```

---

## 4. Implementasi Kode Lengkap (Single-File HTML + Tailwind CSS + Vanilla JS)

Berikut adalah implementasi statis lengkap dalam 1 file HTML siap pakai. Kode ini menggunakan **Tailwind CSS CDN**, font dari Google Fonts, serta script Vanilla JS untuk animasi buka sampul, fitur *copy to clipboard*, dan interaksi tombol WhatsApp.

```html
<!DOCTYPE html>
<html lang="id" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Donasi Pembangunan Kobong - PP Raudhatul Mubarakah</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Amiri:ital,wght@0,400;0,700;1,400&family=Playfair+Display:wght@600;700&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#065f46',
                        secondary: '#d97706',
                        cream: '#fdfbf7',
                    },
                    fontFamily: {
                        arabic: ['Amiri', 'serif'],
                        heading: ['Playfair Display', 'serif'],
                        sans: ['Plus Jakarta Sans', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        .bg-pattern {
            background-color: #fdfbf7;
            background-image: radial-gradient(#065f46 0.5px, transparent 0.5px), radial-gradient(#065f46 0.5px, #fdfbf7 0.5px);
            background-size: 20px 20px;
            background-position: 0 0, 10px 10px;
            background-opacity: 0.05;
        }
        .arch-shape {
            border-top-left-radius: 50rem;
            border-top-right-radius: 50rem;
        }
    </style>
</head>
<body class="font-sans bg-cream text-slate-800 antialiased selection:bg-primary selection:text-white overflow-hidden" id="body-root">

    <!-- 1. SCREEN COVER / WELCOME GATE (Desain Undangan) -->
    <div id="cover-screen" class="fixed inset-0 z-50 bg-primary text-white flex flex-col justify-between items-center p-6 text-center transition-all duration-1000 ease-in-out">
        <!-- Ornamen Atas -->
        <div class="w-full pt-8 opacity-40">
            <div class="w-16 h-1 bg-secondary mx-auto mb-2 rounded-full"></div>
            <p class="text-xs uppercase tracking-widest text-emerald-200">Undangan Berbagi Kebaikan</p>
        </div>

        <!-- Konten Utama Cover -->
        <div class="max-w-md my-auto px-4 py-8 border border-emerald-700/50 rounded-3xl bg-emerald-900/40 backdrop-blur-sm shadow-2xl">
            <p class="font-arabic text-2xl md:text-3xl text-amber-300 mb-4 tracking-wide">بِسْمِ اللهِ الرَّحْمٰنِ الرَّحِيْمِ</p>
            <h1 class="font-heading text-2xl md:text-3xl font-bold mb-3 leading-snug">Pembangunan Kobong Santri Putra</h1>
            <p class="text-emerald-100 text-sm md:text-base font-light mb-6">Takhosus / Salafi & Penghapal Al-Qur'an<br><strong class="text-white font-medium">Pondok Pesantren Raudhatul Mubarakah</strong></p>
            
            <div class="py-3 px-4 bg-emerald-800/60 rounded-xl mb-6 text-xs text-emerald-200 border border-emerald-600/30">
                "Setiap batu yang terpasang insyaAllah akan menjadi jalan lahirnya para penerus umat."
            </div>

            <button onclick="openInvitation()" class="group relative inline-flex items-center gap-2 px-8 py-3.5 bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-600 hover:to-amber-700 text-white font-semibold rounded-full shadow-lg shadow-amber-600/30 transform transition active:scale-95 duration-200">
                <span>Buka Halaman Donasi</span>
                <svg class="w-4 h-4 transition-transform group-hover:translate-y-1" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
            </button>
        </div>

        <!-- Footer Cover -->
        <div class="pb-6 text-xs text-emerald-300 opacity-75">
            Kp. Cigadog, Sagaranten - Sukabumi
        </div>
    </div>

    <!-- MAIN CONTENT WRAPPER -->
    <main class="min-h-screen max-w-2xl mx-auto bg-white shadow-2xl relative pb-24">
        
        <!-- Header Banner -->
        <header class="relative bg-primary text-white pt-16 pb-24 px-6 text-center arch-shape mx-2 mt-2 shadow-inner">
            <p class="text-amber-300 font-arabic text-3xl mb-3">بِسْمِ اللهِ الرَّحْمٰنِ الرَّحِيْمِ</p>
            <h2 class="font-heading text-2xl md:text-3xl font-bold tracking-wide">Pondok Pesantren<br>Raudhatul Mubarakah</h2>
            <p class="text-emerald-200 text-sm mt-2 font-light">Kp. Cigadog, Sagaranten, Sukabumi</p>
            
            <!-- Floating Badge -->
            <div class="absolute -bottom-6 left-1/2 -translate-x-1/2 bg-white text-primary px-6 py-2.5 rounded-full shadow-md border border-emerald-100 flex items-center gap-2 text-xs md:text-sm font-semibold whitespace-nowrap">
                <span class="w-2 h-2 rounded-full bg-amber-500 animate-pulse"></span>
                Peluang Amal Jariyah & Wakaf
            </div>
        </header>

        <!-- 2. MUKADIMAH & SALAM -->
        <section class="pt-14 pb-10 px-6 md:px-10 text-center">
            <h3 class="font-heading text-xl font-bold text-slate-800 mb-4">Assalamu’alaikum Wr. Wb.</h3>
            <p class="text-slate-600 text-sm md:text-base leading-relaxed mb-4 font-light">
                Segala puji bagi Allah SWT yang telah melimpahkan nikmat kesehatan, keberkahan, serta kesempatan kepada kita semua untuk terus menebar kebaikan. Shalawat dan salam semoga senantiasa tercurah kepada Nabi Muhammad SAW, keluarga, sahabat, dan seluruh umatnya hingga akhir zaman.
            </p>
            <div class="w-12 h-0.5 bg-amber-500 mx-auto my-6"></div>
            <p class="text-slate-700 text-sm md:text-base leading-relaxed">
                Dengan penuh harap kepada Allah SWT, kami dari <strong class="text-primary font-semibold">PONDOK PESANTREN RAUDHATUL MUBARAKAH</strong> mengajak bapak/ibu serta para dermawan untuk bersama-sama mengambil bagian dalam amal kebaikan melalui donasi pembangunan kobong santri putra takhosus/salafi dan para penghapal Al Qur'an.
            </p>
        </section>

        <!-- 3. TENTANG PEMBANGUNAN -->
        <section class="py-10 px-6 md:px-10 bg-emerald-50/60 border-y border-emerald-100">
            <div class="max-w-lg mx-auto text-center">
                <div class="inline-block p-3 bg-primary/10 rounded-2xl text-primary mb-4">
                    <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.8" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4"></path></svg>
                </div>
                <h4 class="font-heading text-xl font-bold text-primary mb-3">Tempat Tumbuhnya Generasi Qur'ani</h4>
                <p class="text-slate-600 text-sm md:text-base leading-relaxed mb-6 font-light">
                    Pondok pesantren adalah tempat tumbuhnya generasi yang belajar Al-Qur’an, ilmu agama, dan akhlak mulia. Setiap batu yang terpasang, setiap ruang yang terbangun, dan setiap fasilitas yang tersedia <em class="text-slate-800 font-medium">insyaAllah akan menjadi jalan lahirnya para penerus umat.</em>
                </p>
                <div class="bg-white p-5 rounded-2xl shadow-sm border border-emerald-100 text-left relative overflow-hidden">
                    <div class="absolute top-0 left-0 w-1.5 h-full bg-amber-500"></div>
                    <p class="text-xs md:text-sm text-slate-700 italic leading-relaxed pl-2">
                        "Dan saat ini kami tengah berikhtiar untuk memulai pembangunan kobong tersebut. Untuk itu, kami mengajak bapak/ibu dan rekan-rekan semua dalam kebaikan ini, baik berupa dana maupun bentuk dukungan lainnya. Tidaklah kecil sebuah kebaikan yang dilakukan dengan keikhlasan. Karena di sisi Allah, yang dinilai bukan hanya besar kecilnya pemberian, tetapi ketulusan hati dalam berbagi."
                    </p>
                </div>
            </div>
        </section>

        <!-- 4. DOMPET KEBAIKAN (AMPLOP DIGITAL / REKENING) -->
        <section class="py-12 px-6 md:px-10" id="rekening-section">
            <div class="text-center mb-8">
                <span class="text-xs font-bold uppercase tracking-widest text-amber-600 bg-amber-50 px-3 py-1 rounded-full border border-amber-200">Dompet Kebaikan</span>
                <h3 class="font-heading text-2xl font-bold text-slate-800 mt-2">Saluran Donasi & Wakaf</h3>
                <p class="text-xs md:text-sm text-slate-500 mt-1">Bagi bapak/ibu yang ingin ikut serta dalam pembangunan ini, donasi dapat disalurkan melalui rekening berikut:</p>
            </div>

            <!-- Toast Notification -->
            <div id="copy-toast" class="fixed top-5 left-1/2 -translate-x-1/2 z-50 bg-slate-900 text-white px-5 py-3 rounded-full shadow-xl text-xs md:text-sm font-medium flex items-center gap-2 opacity-0 pointer-events-none transition-all duration-300">
                <svg class="w-4 h-4 text-emerald-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                <span id="toast-text">Nomor rekening berhasil disalin!</span>
            </div>

            <!-- Grid Rekening Cards -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                
                <!-- Bank BJB - Ishaq -->
                <div class="p-5 rounded-2xl border border-slate-200 hover:border-emerald-500 transition-all bg-gradient-to-br from-white to-slate-50 relative group shadow-sm hover:shadow">
                    <div class="flex justify-between items-start mb-3">
                        <span class="font-bold text-blue-800 bg-blue-50 px-2.5 py-1 rounded text-xs border border-blue-200">BANK BJB</span>
                        <span class="text-[10px] text-slate-400 font-mono">Kode Bank: 110</span>
                    </div>
                    <p class="text-xs text-slate-500">Nomor Rekening:</p>
                    <p class="text-lg font-bold font-mono text-slate-800 tracking-wider my-0.5" id="rek-1">0160777151100</p>
                    <p class="text-xs font-semibold text-slate-600 mb-4">a.n ISHAQ MUHAMAD</p>
                    <button onclick="copyToClipboard('0160777151100', 'BANK BJB (Ishaq Muhamad)')" class="w-full py-2 bg-slate-100 hover:bg-primary hover:text-white text-slate-700 font-medium text-xs rounded-xl transition duration-200 flex items-center justify-center gap-1.5 border border-slate-200 hover:border-primary">
                        <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 16H6a2 2 0 01-2-2V6a2 2 0 012-2h8a2 2 0 012 2v2m-6 12h8a2 2 0 002-2v-8a2 2 0 00-2-2h-8a2 2 0 00-2 2v8a2 2 0 002 2z"></path></svg>
                        <span>Salin Nomor Rekening</span>
                    </button>
                </div>

                <!-- Bank BRI - Ishaq -->
                <div class="p-5 rounded-2xl border border-slate-200 hover:border-emerald-500 transition-all bg-gradient-to-br from-white to-slate-50 relative group shadow-sm hover:shadow">
                    <div class="flex justify-between items-start mb-3">
                        <span class="font-bold text-blue-700 bg-blue-50 px-2.5 py-1 rounded text-xs border border-blue-200">BANK BRI</span>
                        <span class="text-[10px] text-slate-400 font-mono">Kode Bank: 002</span>
                    </div>
                    <p class="text-xs text-slate-500">Nomor Rekening:</p>
                    <p class="text-lg font-bold font-mono text-slate-800 tracking-wider my-0.5" id="rek-2">440901054875530</p>
                    <p class="text-xs font-semibold text-slate-600 mb-4">a.n ISHAQ MUHAMAD</p>
                    <button onclick="copyToClipboard('440901054875530', 'BANK BRI (Ishaq Muhamad)')" class="w-full py-2 bg-slate-100 hover:bg-primary hover:text-white text-slate-700 font-medium text-xs rounded-xl transition duration-200 flex items-center justify-center gap-1.5 border border-slate-200 hover:border-primary">
                        <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 16H6a2 2 0 01-2-2V6a2 2 0 012-2h8a2 2 0 012-2v2m-6 12h8a2 2 0 002-2v-8a2 2 0 00-2-2h-8a2 2 0 00-2 2v8a2 2 0 002 2z"></path></svg>
                        <span>Salin Nomor Rekening</span>
                    </button>
                </div>

                <!-- Bank BRI - Yayasan -->
                <div class="p-5 rounded-2xl border border-slate-200 hover:border-emerald-500 transition-all bg-gradient-to-br from-white to-slate-50 relative group shadow-sm hover:shadow">
                    <div class="flex justify-between items-start mb-3">
                        <span class="font-bold text-blue-700 bg-blue-50 px-2.5 py-1 rounded text-xs border border-blue-200">BANK BRI</span>
                        <span class="text-[10px] text-slate-400 font-mono">Kode Bank: 002</span>
                    </div>
                    <p class="text-xs text-slate-500">Nomor Rekening:</p>
                    <p class="text-lg font-bold font-mono text-slate-800 tracking-wider my-0.5" id="rek-3">440901027171533</p>
                    <p class="text-xs font-semibold text-slate-600 mb-4 truncate" title="Yayasan Raudhatul Mubarakah">a.n YAYASAN RAUDHATUL MUBARAKAH</p>
                    <button onclick="copyToClipboard('440901027171533', 'BANK BRI (Yayasan)')" class="w-full py-2 bg-slate-100 hover:bg-primary hover:text-white text-slate-700 font-medium text-xs rounded-xl transition duration-200 flex items-center justify-center gap-1.5 border border-slate-200 hover:border-primary">
                        <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 16H6a2 2 0 01-2-2V6a2 2 0 012-2h8a2 2 0 012-2v2m-6 12h8a2 2 0 002-2v-8a2 2 0 00-2-2h-8a2 2 0 00-2 2v8a2 2 0 002 2z"></path></svg>
                        <span>Salin Nomor Rekening</span>
                    </button>
                </div>

                <!-- Bank BJB - Yayasan -->
                <div class="p-5 rounded-2xl border border-slate-200 hover:border-emerald-500 transition-all bg-gradient-to-br from-white to-slate-50 relative group shadow-sm hover:shadow">
                    <div class="flex justify-between items-start mb-3">
                        <span class="font-bold text-blue-800 bg-blue-50 px-2.5 py-1 rounded text-xs border border-blue-200">BANK BJB</span>
                        <span class="text-[10px] text-slate-400 font-mono">Kode Bank: 110</span>
                    </div>
                    <p class="text-xs text-slate-500">Nomor Rekening:</p>
                    <p class="text-lg font-bold font-mono text-slate-800 tracking-wider my-0.5" id="rek-4">0077273492100</p>
                    <p class="text-xs font-semibold text-slate-600 mb-4 truncate" title="Yayasan Raudhatul Mubarakah">a.n YAYASAN RAUDHATUL MUBARAKAH</p>
                    <button onclick="copyToClipboard('0077273492100', 'BANK BJB (Yayasan)')" class="w-full py-2 bg-slate-100 hover:bg-primary hover:text-white text-slate-700 font-medium text-xs rounded-xl transition duration-200 flex items-center justify-center gap-1.5 border border-slate-200 hover:border-primary">
                        <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 16H6a2 2 0 01-2-2V6a2 2 0 012-2h8a2 2 0 012-2v2m-6 12h8a2 2 0 002-2v-8a2 2 0 00-2-2h-8a2 2 0 00-2 2v8a2 2 0 002 2z"></path></svg>
                        <span>Salin Nomor Rekening</span>
                    </button>
                </div>

            </div>
        </section>

        <!-- 5. LOKASI & KUNJUNGAN -->
        <section class="py-12 px-6 md:px-10 bg-slate-50 border-t border-slate-100 text-center">
            <h3 class="font-heading text-2xl font-bold text-slate-800 mb-3">Silaturahmi & Kunjungan</h3>
            <p class="text-slate-600 text-xs md:text-sm max-w-md mx-auto mb-6 leading-relaxed">
                Atau bagi yang berkesempatan, kami sangat berbahagia apabila bapak/ibu dapat berkunjung langsung ke Pondok Pesantren Raudhatul Mubarakah.
            </p>
            
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 max-w-md mx-auto mb-6 text-left flex items-start gap-4">
                <div class="p-3 bg-emerald-100 text-primary rounded-xl shrink-0 mt-0.5">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                </div>
                <div>
                    <h5 class="font-bold text-slate-800 text-sm mb-1">Alamat Pondok Pesantren:</h5>
                    <p class="text-xs text-slate-600 leading-relaxed">
                        Kp. Cigadog RT 025 / RW 006<br>
                        Desa Sagaranten, Kecamatan Sagaranten<br>
                        Kabupaten Sukabumi, Jawa Barat
                    </p>
                </div>
            </div>

            <a href="https://maps.google.com/?q=Sagaranten+Sukabumi" target="_blank" class="inline-flex items-center gap-2 px-6 py-2.5 bg-white border border-slate-300 hover:border-primary hover:text-primary text-slate-700 text-xs font-semibold rounded-full shadow-sm transition duration-200">
                <svg class="w-4 h-4 text-red-500" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/></svg>
                <span>Buka di Google Maps</span>
            </a>
        </section>

        <!-- 6. DOA & HARAPAN (BUKU TAMU DIGITAL) -->
        <section class="py-12 px-6 md:px-10 bg-white">
            <div class="max-w-lg mx-auto">
                <div class="text-center mb-6">
                    <h3 class="font-heading text-xl font-bold text-slate-800">Doa & Dukungan Kebaikan</h3>
                    <p class="text-xs text-slate-500 mt-1">Tuliskan doa dan harapan untuk santri dan pembangunan pondok</p>
                </div>

                <!-- Form Doa (Simulasi Statis) -->
                <form onsubmit="handleDoaSubmit(event)" class="space-y-3 mb-8 bg-slate-50 p-4 rounded-2xl border border-slate-200">
                    <input type="text" id="donor-name" required placeholder="Nama Anda (cth: Hamba Allah / Bpk. Ahmad)" class="w-full px-3.5 py-2.5 text-xs rounded-xl border border-slate-300 focus:outline-none focus:border-primary bg-white">
                    <textarea id="donor-message" required rows="3" placeholder="Tuliskan doa atau dukungan Anda..." class="w-full px-3.5 py-2.5 text-xs rounded-xl border border-slate-300 focus:outline-none focus:border-primary bg-white"></textarea>
                    <button type="submit" class="w-full py-2.5 bg-primary hover:bg-emerald-800 text-white font-semibold text-xs rounded-xl transition duration-200 shadow">
                        Kirim Doa & Harapan
                    </button>
                </form>

                <!-- List Doa Container -->
                <div id="doa-list" class="space-y-3 max-h-72 overflow-y-auto pr-1">
                    <div class="p-3.5 bg-emerald-50/50 border border-emerald-100 rounded-xl">
                        <div class="flex items-center justify-between mb-1">
                            <span class="font-bold text-xs text-primary">Keluarga Bapak H. Usman</span>
                            <span class="text-[10px] text-slate-400">Baru saja</span>
                        </div>
                        <p class="text-xs text-slate-600 italic">"Bismillah, semoga pembangunannya lancar dan berkah. Semoga menjadi amal jariyah dan santri-santrinya kelak menjadi ulama besar yang bermanfaat bagi umat. Aamiin."</p>
                    </div>
                    <div class="p-3.5 bg-slate-50 border border-slate-100 rounded-xl">
                        <div class="flex items-center justify-between mb-1">
                            <span class="font-bold text-xs text-slate-700">Hamba Allah</span>
                            <span class="text-[10px] text-slate-400">1 jam yang lalu</span>
                        </div>
                        <p class="text-xs text-slate-600 italic">"Semoga sedikit rezeki yang dititipkan dapat membantu mendirikan tempat berteduh para penghapal Al-Qur'an. Berkah selalu untuk pengasuh dan santri PP Raudhatul Mubarakah."</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- 7. PENUTUP & JAZAKUMULLAH -->
        <section class="py-14 px-6 md:px-10 bg-primary text-white text-center relative overflow-hidden">
            <div class="max-w-md mx-auto relative z-10">
                <p class="text-xs md:text-sm leading-relaxed mb-6 font-light text-emerald-100">
                    "Semoga setiap rupiah yang diberikan, setiap doa yang dipanjatkan, dan setiap dukungan yang disampaikan menjadi amal jariyah yang terus mengalir pahalanya, serta Allah SWT menggantinya dengan keberkahan yang berlipat ganda."
                </p>
                <h4 class="font-heading text-lg md:text-xl font-bold text-amber-300 mb-6 tracking-wide">
                    Jazakumullahu khairan katsiran atas perhatian, kepedulian, dan partisipasinya.
                </h4>
                <p class="text-sm font-semibold mb-2">Wassalamu’alaikum Wr. Wb.</p>
                <p class="text-xs text-emerald-200">Panitia Pembangunan Kobong<br><strong class="text-white">PP Raudhatul Mubarakah</strong></p>
            </div>
        </section>

        <!-- Copyright Footer -->
        <footer class="py-6 text-center text-[11px] text-slate-400 bg-slate-900">
            <p>© 2026 Pondok Pesantren Raudhatul Mubarakah - Sagaranten, Sukabumi.<br>Dibuat untuk kebaikan & amal jariyah.</p>
        </footer>

    </main>

    <!-- 8. FLOATING WHATSAPP CTA BUTTON -->
    <div class="fixed bottom-6 right-6 z-40">
        <a href="https://wa.me/6285659401700?text=Assalamu'%0Aalaikum%20Wr.%20Wb.%20Saya%20ingin%20konfirmasi%20donasi/bertanya%20terkait%20pembangunan%20kobong%20PP%20Raudhatul%20Mubarakah." target="_blank" class="flex items-center gap-2 px-4 py-3 bg-emerald-600 hover:bg-emerald-700 text-white font-semibold text-xs md:text-sm rounded-full shadow-2xl hover:scale-105 transition-all duration-200 border-2 border-white">
            <svg class="w-5 h-5 fill-current" viewBox="0 0 24 24"><path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.582 2.128 2.182-.573c.978.58 1.911.928 3.145.929 3.178 0 5.767-2.587 5.768-5.766.001-3.187-2.575-5.77-5.764-5.771zm3.392 8.244c-.144.405-.837.774-1.17.824-.299.045-.677.063-1.092-.069-.252-.08-.575-.187-.988-.365-1.739-.751-2.874-2.502-2.961-2.617-.087-.116-.708-.94-.708-1.793s.448-1.273.607-1.446c.159-.173.346-.217.462-.217l.332.006c.106.005.249-.04.39.298.144.347.491 1.2.534 1.287.043.087.072.188.014.304-.058.116-.087.188-.173.289l-.26.304c-.087.086-.177.18-.076.354.101.174.449.741.964 1.201.662.591 1.221.774 1.394.86s.289.072.39-.043c.101-.116.433-.506.549-.68.116-.173.231-.145.39-.087s1.011.477 1.184.564.289.13.332.202c.045.072.045.419-.1.824zm-3.423-14.416c-6.627 0-12 5.373-12 12 0 2.131.563 4.141 1.554 5.882l-1.651 6.036 6.191-1.623c1.685.918 3.616 1.445 5.674 1.445 6.627 0 12-5.373 12-12 0-6.627-5.373-12-12-12z"/></svg>
            <span>Konfirmasi / Hubungi (085659401700)</span>
        </a>
    </div>

    <!-- SCRIPT INTERAKTIF (VANILLA JS) -->
    <script>
        // 1. Fungsi Buka Sampul (Undangan Gate)
        function openInvitation() {
            const cover = document.getElementById('cover-screen');
            const body = document.getElementById('body-root');
            
            cover.classList.add('opacity-0', '-translate-y-full');
            body.classList.remove('overflow-hidden');
            
            setTimeout(() => {
                cover.style.display = 'none';
            }, 1000);
        }

        // 2. Fungsi Copy Nomor Rekening + Feedback Toast
        function copyToClipboard(text, bankName) {
            navigator.clipboard.writeText(text).then(() => {
                const toast = document.getElementById('copy-toast');
                const toastText = document.getElementById('toast-text');
                
                toastText.innerText = `Rekening ${bankName} berhasil disalin!`;
                toast.classList.remove('opacity-0', 'pointer-events-none');
                toast.classList.add('opacity-100', '-translate-y-2');
                
                setTimeout(() => {
                    toast.classList.remove('opacity-100', '-translate-y-2');
                    toast.classList.add('opacity-0', 'pointer-events-none');
                }, 3000);
            }).catch(err => {
                alert('Gagal menyalin nomor rekening. Silakan salin manual: ' + text);
            });
        }

        // 3. Simulasi Kirim Doa Buku Tamu
        function handleDoaSubmit(e) {
            e.preventDefault();
            const nameInput = document.getElementById('donor-name');
            const msgInput = document.getElementById('donor-message');
            const list = document.getElementById('doa-list');

            if (!nameInput.value || !msgInput.value) return;

            const newCard = document.createElement('div');
            newCard.className = 'p-3.5 bg-emerald-50/80 border border-emerald-200 rounded-xl animate-fade-in';
            newCard.innerHTML = `
                <div class="flex items-center justify-between mb-1">
                    <span class="font-bold text-xs text-primary">${nameInput.value}</span>
                    <span class="text-[10px] text-emerald-600 font-semibold">Baru saja (Anda)</span>
                </div>
                <p class="text-xs text-slate-700 italic">"${msgInput.value}"</p>
            `;

            list.prepend(newCard);
            nameInput.value = '';
            msgInput.value = '';
            alert('Jazakumullah khairan! Doa dan harapan Anda berhasil ditambahkan.');
        }
    </script>
</body>
</html>
```

---

## 5. Rekomendasi Struktur Komponen untuk React / Next.js (Opsional)
Jika ingin dikembangkan ke dalam ekosistem **React / Next.js** dengan Tailwind CSS untuk kemudahan maintenance dan integrasi API (misalnya dengan database Supabase atau Firebase untuk menyimpan list doa buku tamu secara real-time), berikut adalah struktur arsitektur filenya:

```bash
src/
├── app/
│   ├── layout.tsx         # Root layout dengan konfigurasi font (Amiri & Plus Jakarta Sans)
│   └── page.tsx           # Main Landing Page assembling all components
├── components/
│   ├── HeroCover.tsx      # Welcome Screen Gate dengan Framer Motion (slide up / fade out)
│   ├── Mukadimah.tsx      # Bagian Salam, Basmalah & Pengantar Kata
│   ├── ProjectStory.tsx   # Penjelasan urgensi & tujuan pembangunan kobong
│   ├── BankCard.tsx       # Reusable component kartu rekening dengan hook useCopyToClipboard
│   ├── DonationGrid.tsx   # Grid container untuk 4 rekening (BJB & BRI)
│   ├── LocationMap.tsx    # Kartu alamat & tombol navigasi Google Maps
│   ├── GuestBook.tsx      # Form buku tamu doa & harapan (bisa dihubungkan ke backend DB)
│   └── FloatingCTA.tsx    # Tombol WhatsApp melayang (085659401700)
├── data/
│   └── accounts.ts        # File konstanta berisi daftar rekening dan alamat
└── types/
    └── index.ts           # TypeScript interface untuk doa dan props rekening
```

### Tips Optimasi Tambahan:
1. **Peningkatan Emosional (Social Proof):** Anda dapat menambahkan foto atau dokumentasi visual progres pembangunan kobong atau kegiatan santri menghafal Al-Qur'an dalam bentuk *Carousel / Image Grid* tepat di bawah bagian "Tentang Pembangunan".
2. **Audio Shalawat (Opsional):** Untuk memperkuat nuansa undangan digital, bisa ditambahkan elemen `<audio>` dengan kontrol floating *"Putar / Hentikan Audio"* menggunakan lantunan shalawat atau murottal berirama lembut.
