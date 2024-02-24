# Pacmann.ai-PythonProject Super Cashier
Project membuat sistem kasir swalayan menggunakan Python

## Latar Belakang
Super cashier merupakan sistem kasir swalayan, di mana pelanggan dapat mencantumkan barang yang akan dibeli (nama, jumlah barang dengan harga yang telah ditentukan) disertai fitur lainnya.

Ketentuan yang diberlakukan yaitu: Modular code, clean code (PEP8), dokumentasi Docstring (menjelaskan makna code), try-error untuk track error, dapat menggunakan library Python.

## Persyaratan
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
    K-->L{total belanja`&lt;`200.000?};
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
    add_item([nama item, jumlah item, harga per item])
   * nama item(tipe: string)    = nama dari item yang hendak dibeli <br>
   * jumlah item(tipe: int)     = jumlah item yang akan dibeli <br>
   * harga per item(tipe: int)  = harga/item terkait <br>

### 3. Mengubah nama item <br>
    update_item_name([nama item, update nama item])
   * nama item(string)          = nama item yang namanya ingin diganti <br>
   * update nama item(string)   = nama baru item <br>
    
### 4. Mengubah jumlah item <br>
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
    reset_transaction()
   
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
Import module & memasukkan ID transaksi: <br>
![Screenshot_1](https://user-images.githubusercontent.com/119667963/217313577-92261e1d-37d2-4089-a974-6a7be73e7887.png)<br>

  1. Menambah item: add_item() <br>
     input: <br>
![Screenshot_2](https://user-images.githubusercontent.com/119667963/217313621-1d7a0f26-fe67-4bc7-b767-898c1eadf3e7.png)
     output: <br>
![Screenshot_3](https://user-images.githubusercontent.com/119667963/217332054-17710519-7098-45bd-81ff-a9cbd09769b5.png)<br>

  2. Menghapus item: delete_item() <br>
      input: <br>
![Screenshot_4](https://user-images.githubusercontent.com/119667963/217314616-4124f607-091f-43a4-a82a-3bca9b105f63.png)<br>
      output: <br>
![Screenshot_5](https://user-images.githubusercontent.com/119667963/217314870-f235879b-4c7b-48a0-bd83-0379fe8f6af5.png)<br>
      
  3. Mengatur ulang transaksi: reset_transaction()<br>
      input:<br>
![Screenshot_6](https://user-images.githubusercontent.com/119667963/217316039-8dfaa3c9-efcd-4b97-b977-5f0bdf7a46cd.png)<br>
      output:<br>
![Screenshot_7](https://user-images.githubusercontent.com/119667963/217316090-06c08d4c-ca00-4e9d-970e-1623e940b55f.png)<br>
      
  4. Mengecek pesanan, memastikan sudah dikosongkan: check_order()<br>
      input:<br>
![Screenshot_8](https://user-images.githubusercontent.com/119667963/217316288-c8aee87a-7b49-4773-9164-62da49b62e06.png)<br>
      output:<br>
![Screenshot_9](https://user-images.githubusercontent.com/119667963/217316319-ce1b66ce-0b48-499b-8607-fceb4cba51a0.png)<br>
      
  5. Mengecek harga akhir & perolehan diskon<br>
     * Isi kembali pesanan<br>
      input:<br>
![Screenshot_10](https://user-images.githubusercontent.com/119667963/217317115-ad4d6ac4-e5cd-4dd7-a38f-beb4bc811f6c.png)<br>
      output:<br>
![Screenshot_11](https://user-images.githubusercontent.com/119667963/217317152-5d4b2a79-d995-4105-8d7a-eabcacf7f9b5.png)<br>
     * Melihat harga akhir & perolehan diskon: total_price()<br>
      input:<br>
![Screenshot_12](https://user-images.githubusercontent.com/119667963/217319069-f6a80565-aaa3-42ec-855e-98fe900ae875.png)<br>
      output:<br>
![Screenshot_13](https://user-images.githubusercontent.com/119667963/217319333-0e03609e-b6fe-41b0-91a3-601e1844365e.png)<br>
   
  6. Jika ada nilai belanjaan yang tidak wajar (misal jumlah atau harga minus)<br>
      input:<br>
![Screenshot_14](https://user-images.githubusercontent.com/119667963/217321660-d1731442-adb8-491f-8585-777c97cd3e0b.png)<br>
      output:<br>
![Screenshot_15](https://user-images.githubusercontent.com/119667963/217326356-d0f27c46-44e2-426a-84bd-b58ca42ba661.png)
       
  7. Memperbaiki nilai jumlah item: update_item_qty()<br>
      input:<br>
![Screenshot_16](https://user-images.githubusercontent.com/119667963/217322515-5dd8712e-0899-4a37-bcd9-0c757f1fd4e6.png)<br>
      output:<br>
![Screenshot_17](https://user-images.githubusercontent.com/119667963/217322544-ef6f4894-ea4a-453e-ad5a-d3b68f121c04.png)<br>
       
  8. Memperbaiki nilai harga item: update_item_price()<br>
      input:<br>
![Screenshot_18](https://user-images.githubusercontent.com/119667963/217322581-78db85c0-a935-421e-856a-101542fbec1b.png)<br>
      output:<br>
![Screenshot_19](https://user-images.githubusercontent.com/119667963/217322616-6e835b1d-e299-4bb0-9c5c-df1bf5591d26.png)<br>
      input:<br>
![Screenshot_20](https://user-images.githubusercontent.com/119667963/217323931-bf4f6078-3089-4518-ab46-62a5050100a5.png)<br>
      output:<br>
![Screenshot_21](https://user-images.githubusercontent.com/119667963/217323962-520361dd-19a0-42ec-8e5e-775e7f933f2b.png)<br>
  9. Menambahkan item dengan nama yang sudah ada sebelumnya<br>
      input:<br>
![Screenshot_22](https://user-images.githubusercontent.com/119667963/217333739-064cd982-48d6-4576-a36b-618a9570e936.png)<br>
      output:<br>
![Screenshot_23](https://user-images.githubusercontent.com/119667963/217335018-defacb35-32d0-4a43-8b02-02829e717400.png)



## Kesimpulan <br>
Modul supercashier.py yang telah dirancang dapat menjalankan berbagai method yang diperlukan sesuai dengan requirement yang diberikan, membantu baik pembeli maupun penjual mulai dari merekap aktifitas transaksinya, melakukan kroscek input, total belanja & capaian diskon dst., dengan catatan: <br>
* Setiap method yang telah dirancang dapat berjalan sesuai fungsi yang diharapkan;
* Try-branching yang dirancang dapat mengantisipasi nilai tidak wajar dan duplikat yang mungkin terjadi selama input transaksi;
* Code module dirancang dengan kaidah PEP8;
* Modular code (.py), yang terdiri dari berbagai fungsi dengan tugasnya masing-masing.
      
