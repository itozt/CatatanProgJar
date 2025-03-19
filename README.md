# Catatan Pemrograman Jaringan
# Daftar Isi
-   [✨ Pertemuan 3 - Mengoperasikan Mesin](https://github.com/itozt/CatatanProgJar/blob/main/README.md#a-langkah---langkah-pengoperasian-mesin)
-   [✨ Pertemuan 3 - Komunikasi Mesin menggunakan Netcat](https://github.com/itozt/CatatanProgJar/blob/main/README.md#b-langkah---langkah-komunikasi-2-mesin-menggunakan-netcat)

# :herb: Pertemuan 3 - Mengoperasikan Mesin dan Melakukan Komunikasi 2 Mesin
### **A. Langkah - Langkah Pengoperasian Mesin** 
1. Buka Visual Studio Code
2. Pada bagian pojok kiri bawah, klik tombol berwarna biru. <br>
   ![image](https://github.com/user-attachments/assets/d36422cb-4505-434f-be6f-128c63ce906a)
3. Pilih "Connect to WSL", lalu tunggu loading <br>
   ![image](https://github.com/user-attachments/assets/c136f1a9-229d-4ea0-ad49-b39ee7e73a4a)
4. Pindah lokasi terminal ke direktori ```progjar/environtment/``` dengan menjalankan command berikut :
   ```
   cd progjar/environment/
   ```
5. Apabila docker compose belum terinstal, jalankan command berikut di terminal. <br>
   ```
   sudo apt install docker-compose
   ```
6. Aktifkan docker compose.
   ```
   docker-compose up -d
   ```
7. Jalankan program di browser Chrome sesuai keperluan tugas
8. Matikan docker compose setelah selesai digunakan
   ```
   docker-compose down
   ```

### **B. Langkah - Langkah Komunikasi 2 Mesin menggunakan Netcat**
1. Pastikan program (docker compose) sudah menyala seperti langkah-langkah di atas.
2. Buka browser Chrome
3. Karena komunikasi memerlukan 2 mesin, maka perlu mengakses 2 mesin berbeda pula. <br>
   Untuk mengakses mesin dengan web based jupyter lab : <br>
   - mesin1 : ```http://127.0.0.1:60001``` <br>
   - mesin2 : ```http://127.0.0.1:60002``` <br>
   - mesin3 : ```http://127.0.0.1:60003``` <br>
   Password : mesin1, mesin2, mesin3 (disesuaikan)
4. Pada masing-masing mesin, klik 'Terminal' <br>
   ![image](https://github.com/user-attachments/assets/caffa29b-32a4-41a3-bfd3-c3294f28014a)
5. Clone github progjar
   ```
   git clone https://github.com/rm77/progjar/
   ```
6. Install Netcat pada kedua mesin
   ```
   sudo apt install netcat
   ```
7. Nyalakan server pada mesin yang berperan sebagai penerima pesan, contoh di mesin1
   ```
   cd progjar/progjar1
   python3 server.py
   ```
8. Ajukan komunikasi netcat di mesin2 ke mesin1
   ```
   nc -vvv 172.16.16.101 10000
   ```
   Fungsi :
   - `nc` → Menjalankan Netcat (alat jaringan).
   - `vvv` → Mode verbose maksimal, menampilkan detail koneksi.
   - `172.16.16.101` → IP tujuan (mesin1).
   - `10000` → Port tujuan.
   IP tujuan berbeda-beda setiap mesin.
9. Kirimkan pesan yang diinginkan di mesin2. Pastikan pesan diterima di mesin1.
10. Akhiri komunikasi di kedua mesin dengan menjalankan command `Ctrl + C`. Maka server.py juga akan otomatis berhenti.
