# Pacmann.ai-PythonProject Super Cashier
Project membuat sistem kasir swalayan menggunakan Python

## Latar Belakang
Super cashier merupakan sistem kasir swalayan, di mana pelanggan dapat mencantumkan barang yang akan dibeli (nama, jumlah barang dengan harga yang telah ditentukan) disertai fitur lainnya.

Ketentuan yang diberlakukan yaitu: Modular code, clean code (PEP8), dokumentasi Docstring (menjelaskan makna code), try-error untuk track error, dapat menggunakan library Python

## Persyaratan atau Obyektif
Alur belanja pada Super Cashier adalah sebagai berikut:
1. Customer membuat ID transaksi customer;
2. Customer memasukkan nama, jumlah dan harga barang yang dibeli;
3. Jika terjadi kesalahan memasukkan nama, jumlah maupun harga barang, pelanggan bisa memperbaikinya dengan:
  a. mengubah nama: update_item_name;
  b. mengubah jumlah: update_item_qty;
  c. mengubah harga: update_item_price.
4. Jika batal membeli, pelanggan bisa:
  a. menghapus pilihan belanjanya dengan delete_item(), atau;
  b. reset seluruh transaksi dengan reset_transaction().
5. Jika customer sudah selesai berbelanja online, namun masih ragu apakah harga & nama barang sudah benar atau belum, bisa melakukan cek dengan check_order(), dengan ketentuan:
  a. mengeluarkan pesan "Jumlah & harga item sudah sesuai" berarti tidak ada kesalahan input;
  b. mengeluarkan pesan "Warning: Jumlah/Harga item tidak boleh minus!" berarti terdapat kesalahan input;
  c. mengeluarkan output pemesanan apa saja yang sudah dibeli.
6. Customer bisa menghitung total belanja yang sudah dibeli, dengan method total_price. Terdapat ketentuan:
  a. Jika total belanja <= Rp. 200.000, maka tidak mendapatkan diskon;
  a. total belanja > Rp. 200.000, maka mendapat diskon 5%;
  b. total belanja > Rp. 300.000, maka diskon 8%;
  c. total belanja  > Rp. 500.000, maka diskon 10%.
  
```mermaid
flowchart TD;
    A([Mulai])-->B[membuat ID transaksi: transaction];
    B-->C[memasukkan item: add_item];
    C-->D{ingin mengubah data?};
    D--Ya-->E[update nama/jumlah/harga: update_item];
    E-->TI(( ));
    D--Tidak-->TI;
    TI-->F{ingin membatalkan item?};
    F--Ya-->G[hapus item: delete_item, ulangi transaksi: reset_transaction];
    G-->U(( ));
    F--Tidak-->U;
    U-->H{ingin menambah item?};
    H--Ya-->C;
    H--Tidak-->I[mengecek dan menampilkan pesanan: check_order];
    I-->J{input sudah benar?};
    J--Ya, pemesanan sudah benar-->K[menghitung total belanja: total_price];
    J--Tidak, terdapat kesalahan input data-->E;
    K-->L{total belanja<200.000?};
    L--Ya-->M[tidak mendapatkan diskon];
    M-->V(( ));
    L--Tidak-->N{total belanja>200.000>=300.000?};
    N--Ya-->O[diskon 5%];
    O-->V;
    N--Tidak-->P{total belanja>300.000>=500.000?};
    P--Ya-->Q[diskon 8%]
    Q-->V;
    P--Tidak-->T{total belanja >500.000};
    T--Ya-->Z[diskon 10%];
    Z-->V;
    V-->R[menampilkan total belanja setelah diskon];
    R-->S([Selesai]);
```
## Fungsi yang dipakai

### 1. Customer membuat ID transaksi <br>
    trnsct_123 = Transaction(), memulai class Transaction
   
### 2. Menambah item yang akan dibeli <br>
    add_item([nama item, jumlah item, harga per item]), menambah barang yang akan dibeli:   
   * nama item(tipe: string)    = nama dari item yang hendak dibeli <br>
   * jumlah item(tipe: int)     = jumlah item yang akan dibeli <br>
   * harga per item(tipe: int)  = harga/item terkait <br>

### 3. Mengubah nama item: <br>
    update_item_name([nama item, update nama item])
   * nama item(string)          = nama item yang namanya ingin diganti <br>
   * update nama item(string)   = nama baru item <br>
    
### 4. Mengubah jumlah item: <br>
    update_item_qty([nama item, update jumlah item])
   * nama item(string)          = nama item yang jumlahnya ingin diganti <br>
   * update jumlah item(int)    = jumlah baru item <br>
  
### 5. Mengubah harga item <br>
    update_item_price([nama item, update harga item])
   * nama item(string)          = nama item yang harganya ingin diganti <br>
   * update harga item(int)     = harga baru item <br>
   
### 6. Menghapus item dari daftar belanjaan <br>
    delete_item(nama item)
   * nama item(string)         = nama item yang ingin dihapus <br>

### 7. Menghapus semua atau mengulang transaksi <br>
    reset_transaction() <br>
   
### 8. Melakukan cek / memvalidasi dan menampilkan semua pesanan dalam dictionary <br>
    check_order()
  Dengan ketentuan: <br>
  a. Jika tidak ada kesalahan input, maka muncul pesan "Jumlah & harga item sudah sesuai."; <br>
  b. Jika ada kesalahan input, maka muncul pesan "Warning: Jumlah item tidak boleh minus!" & "Warning: Harga item tidak boleh minus!"; <br>
  c. Setelah memvalidasi input, keluarlah output pesanan yang sudah dibeli. <br>
  
### 8. Setelah pengecekan, customer menghitung total belanja <br>
    total_price()
  Dengan ketentuan jika: <br>
  a. Total belanja <= Rp. 200.000, maka tidak mendapatkan diskon; <br>
  b. Total belanja >Rp. 200.000, maka diskon 5%; <br>
  c. Total belanja >Rp. 300.000, maka diskon 8%; <br>
  d. Total belanja >Rp. 500.000, maka diskon 10%. <br>
 
## Demonstrasi <br>
Memasukkan ID transaksi: <br>
id_1 = Transaction("Yudis") <br>

  1. Menambah item: add_item() <br>
     input: <br>
      id_1.add_item("Ayam Goreng", 2, 20_000) <br>
      id_1.add_item("Pasta Gigi", 3, 15_000) <br>
     output: <br>
            
            Nama item Jumlah item Harga item  Total harga
       1      Ayam Goreng         2.0    20000.0      40000.0
       2       Pasta Gigi         3.0    15000.0      45000.0
       Total            -           -          -      85000.0
       Item Pasta Gigi telah ditambahkan ke dalam daftar pesanan.
    
  2. Menghapus item: delete_item()
      input:
       id_1.delete_item("Pasta Gigi")
      output:
             Nama item Jumlah item Harga item  Total harga
       1      Ayam Goreng         2.0    20000.0      40000.0
       Total            -           -          -      40000.0
       Item Pasta Gigi telah dihapus dari daftar pesanan.
      
  3. Mengatur ulang transaksi: reset_transaction()
      input:
       id_1.reset_transaction("Yudis")
      output:
       Semua pesanan sudah dikosongkan.
      
  4. Mengecek pesanan, memastikan sudah dikosongkan: check_order()
      input:
       id_1.check_order("Yudis")
      output:
             Nama item Jumlah item Harga item  Total harga
       Total         -           -          -          0.0
      
  5. Mengecek harga akhir & perolehan diskon
     Isi kembali pesanan
      input:
       id_1.add_item("Ayam Kampung", 20, 85_000)
       id_1.add_item("Kambing", 10, 6_000_000)
       id_1.add_item("Lele", 500, 2_500)
      output:
              Nama item Jumlah item Harga item  Total harga
       1      Ayam Kampung        20.0    85000.0    1700000.0
       2           Kambing        10.0  6000000.0   60000000.0
       3              Lele       500.0     2500.0    1250000.0
       Total             -           -          -   62950000.0
       Item Lele telah ditambahkan ke dalam daftar pesanan.
      
      Melihat harga akhir & perolehan diskon: total_price()
       input:
        id_1.total_price("Yudis")
       output:
        Pesanan atas nama: Yudis     
        Selamat! Pembeli a/n Yudis mendapat diskon sebesar 10%
        Jumlah harga belanja sebelum diskon sebesar: Rp. 62,950,000
        Besar nominal diskon yang didapat sebesar  : Rp. 6,295,000.0
        Harga setelah diskon menjadi sebesar       : Rp. 56,655,000.0
   
  6. Jika ada nilai belanjaan yang tidak wajar (misal jumlah atau harga minus)
      input:
       id_1.add_item("Sapi", -20, -15_000_000)
       id_1.check_order("Yudis")
      output:
                 Nama item Jumlah item  Harga item  Total harga
       1      Ayam Kampung        20.0     85000.0    1700000.0
       2           Kambing        10.0   6000000.0   60000000.0
       3              Lele       500.0      2500.0    1250000.0
       4              Sapi       -20.0 -15000000.0  300000000.0
       Total             -           -           -  362950000.0
       Item Sapi telah ditambahkan ke dalam daftar pesanan.
       
                 Nama item Jumlah item  Harga item  Total harga
       1      Ayam Kampung        20.0     85000.0    1700000.0
       2           Kambing        10.0   6000000.0   60000000.0
       3              Lele       500.0      2500.0    1250000.0
       4              Sapi       -20.0 -15000000.0  300000000.0
       Total             -           -           -  362950000.0
       Warning: Jumlah item tidak boleh minus!
       Warning: Harga item tidak boleh minus!
       
  7. Memperbaiki nilai jumlah item: update_item_qty()
      input:
       id_1.update_item_qty("Sapi", 20)
      output:
                 Nama item Jumlah item  Harga item  Total harga
       1      Ayam Kampung        20.0     85000.0    1700000.0
       2           Kambing        10.0   6000000.0   60000000.0
       3              Lele       500.0      2500.0    1250000.0
       4              Sapi        20.0 -15000000.0 -300000000.0
       Total             -           -           - -237050000.0
       Jumlah item Sapi telah diubah menjadi sebanyak 20.
       
  8. Memperbaiki nilai harga item: update_item_price()
      input:
       id_1.update_item_price("Sapi", 15_000_000)
      output:
              Nama item Jumlah item  Harga item  Total harga
       1      Ayam Kampung        20.0     85000.0    1700000.0
       2           Kambing        10.0   6000000.0   60000000.0
       3              Lele       500.0      2500.0    1250000.0
       4              Sapi        20.0  15000000.0  300000000.0
       Total             -           -           -  362950000.0
       Harga item Sapi telah diubah menjadi sebesar Rp. 15,000,000.
     Cek kembali pesanan: check_order()
      input:
       id_1.check_order("Yudis")
      output:
              Nama item Jumlah item  Harga item  Total harga
       1      Ayam Kampung        20.0     85000.0    1700000.0
       2           Kambing        10.0   6000000.0   60000000.0
       3              Lele       500.0      2500.0    1250000.0
       4              Sapi        20.0  15000000.0  300000000.0
       Total             -           -           -  362950000.0
       Jumlah & harga item sudah sesuai.
