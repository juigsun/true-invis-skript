# True Invis - Anonymous Invisibility Death Messages

`True Invis` adalah sebuah script lightweight berbasis **Skript (Minecraft Plugin)** yang dirancang untuk menjaga kerahasiaan dan mekanik *stealth* dari Potion of Invisibility.

Secara default di vanilla Minecraft, ketika seorang pemain yang tidak terlihat (invisible) membunuh atau dibunuh, nama mereka tetap akan muncul di pesan kematian (death message) global chat. Script ini menyelesaikan masalah tersebut dengan menyamarkan nama pemain yang sedang menggunakan efek *Invisibility* menggunakan teks acak bergerak (`&k`) khas Minecraft.[cite: 1]

---

## 🚀 Fitur Utama (Features)

* **Dynamic Attacker Anonymization**: Jika pembunuh dalam kondisi tidak terlihat, nama pembunuh akan disamarkan menjadi efek teks bergerak (`&k123`), sementara nama korban tetap terlihat.[cite: 1]
* **Dynamic Victim Anonymization**: Jika korban dalam kondisi tidak terlihat saat mati, nama korban akan disamarkan, sementara nama pembunuh tetap terlihat.[cite: 1]
* **Full Stealth Coverage**: Jika kedua belah pihak (pembunuh dan korban) sama-sama menggunakan Potion of Invisibility, kedua nama mereka akan sepenuhnya disamarkan di dalam chat global.[cite: 1]
* **Native Formatting**: Menggunakan format warna bawaan Minecraft tanpa memerlukan addon tambahan, memberikan kesan estetik vanilla yang misterius.[cite: 1]

---

## ⭐ Keunggulan (Advantages)

* **Ultra Lightweight & No Lag**: Script ini ditulis dengan struktur yang sangat efisien dan hanya berjalan tepat saat event `on death of player` terpicu. Tidak membebani performa CPU server.[cite: 1]
* **Plug and Play**: Tanpa konfigurasi rumit. Cukup masukkan file ke folder server Anda, reload, dan sistem langsung aktif secara instan.
* **Meningkatkan Pengalaman PvP**: Sangat cocok untuk server bertema *Factions, Anarchy, Hardcore, Survival*, atau *Assassin-style minigames* di mana taktik mengendap-endap sangat krusial.

---

## 🛠️ Detail Logika Kode (Technical Details)

Script ini membagi kondisi pesan kematian menjadi 3 skenario logis:[cite: 1]

| Skenario | Kondisi Attacker | Kondisi Victim | Output Pesan Kematian |
| :--- | :--- | :--- | :--- |
| **1** | Invisible 👻 | Invisible 👻 | `&k123&r was slain by &k123` |
| **2** | Invisible 👻 | Terlihat 👤 | `%victim% was slain by &k123` |
| **3** | Terlihat 👤 | Invisible 👻 | `&k123&r was slain by %attacker%` |

> **Catatan Teknis:** Karakter `&k` di Minecraft akan mengubah teks biasa di belakangnya menjadi simbol acak yang terus berubah (obfuscated text), sehingga mustahil bagi pemain lain untuk membaca nama asli di balik efek tersebut melalui chat.[cite: 1]

---

## 📖 Tutorial Instalasi (Setup Guide)

Ikuti langkah-langkah berikut dari awal sampai akhir untuk memasang script ini di server Minecraft Anda:

### 1. Persyaratan Sistem (Prerequisites)
* Server Minecraft berbasis **Paper**, **Purpur**, atau Spigot.
* Plugin **Skript** sudah terinstall di folder `plugins` server Anda.

### 2. Langkah-Langkah Pemasangan
1. Masuk ke direktori server Minecraft Anda.
2. Buka folder `plugins` -> `Skript` -> `scripts`.
3. Buat sebuah file baru di dalam folder tersebut dengan nama `True Invis.sk`.
4. Buka file tersebut menggunakan text editor, lalu paste kode berikut:

```skript
# By bangsall

on death of player:
	if attacker has potion invisibility:
		if victim has potion invisibility:
			set death message to "&k123&r was slain by &k123"
		else:
			set death message to "%victim% was slain by &k123"
	else if victim has potion invisibility:
		set death message to "&k123&r was slain by %attacker%"
