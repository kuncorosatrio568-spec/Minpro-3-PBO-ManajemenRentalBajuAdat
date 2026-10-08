# Minpro-3-PBO-ManajemenRentalBajuAdat

## Deskripsi Singkat Program
Program **Sistem Manajemen Rental Baju Adat Tradisional** merupakan aplikasi berbasis CLI (Command Line Interface) yang dirancang untuk mengelola inventaris sewa baju adat. Sistem ini mendukung operasi CRUD (Create, Read, Update, Delete) serta kalkulasi estimasi biaya sewa dengan diskon.

## Penjelasan Struktur Package
Program ini menggunakan arsitektur **MVC (Model-View-Controller)** yang terbagi ke dalam paket-paket berikut:
* **`Model`**: Berisi entitas data dan logika bisnis (`BajuAdat`, `BajuAnak`, `BajuDewasa`, dan interface `Rentable`).
* **`Controller`**: Berisi `BajuController` yang mengelola manipulasi data (CRUD) dan menghubungkan View dengan Model.
* **`View`**: Berisi `BajuView` yang menangani antarmuka pengguna (input/output di terminal).
* **`rentalbaju`**: Berisi `Main.java` yang merupakan entry point utama dari aplikasi.

## Penjelasan Alur Program
1. **Inisialisasi**: `Main.java` menjalankan controller dan menyuntikkan data dummy awal.
2. **Menu Utama**: `BajuView` menampilkan opsi menu kepada pengguna (Tambah, Tampilkan, Ubah, Hapus, Hitung Sewa).
3. **Pemrosesan Request**:
   - Jika pengguna memilih menu, View meminta input dari pengguna dan meneruskannya ke `BajuController`.
   - `BajuController` mengelola objek model di dalam `ArrayList<BajuAdat>`.
4. **Respon/Output**: Controller mengembalikan status/data ke View untuk ditampilkan kembali ke terminal pengguna.

## Penjelasan Penerapan Encapsulation dan Inheritance
* **Encapsulation**: 
  - Seluruh atribut pada class `BajuAdat`, `BajuAnak`, dan `BajuDewasa` dideklarasikan dengan akses modifier `private`.
  - Akses data dilakukan secara aman menggunakan *getter* dan *setter*.
* **Inheritance**: 
  - Class `BajuAnak` dan `BajuDewasa` mewarisi (*extends*) seluruh atribut dan method dari superclass `BajuAdat`.

## Penjelasan Penerapan Polymorphism dan Abstraction
* **Abstraction**:
  - `BajuAdat` dideklarasikan sebagai **Abstract Class** yang tidak dapat diinstansiasi secara langsung.
  - Memiliki **Abstract Method** `public abstract void tampilkanDetail();` yang wajib diimplementasikan oleh subclass-nya.
* **Polymorphism**:
  - **Overriding**: Subclass `BajuAnak` dan `BajuDewasa` meng-override method `tampilkanDetail()` untuk mengkostumisasi tampilan data sesuai kategorinya.
  - **Overloading**: Terdapat method overloading `hitungTotalSewa(int jumlahHari)` dan `hitungTotalSewa(int jumlahHari, double diskon)` pada class `BajuAdat`.

## Penjelasan Letak Penerapan Nilai Tambah
* **Interface**:
  - Diterapkan pada interface `Rentable` di package `Model`.
  - Class `BajuAdat` mengimplementasikan interface `Rentable` (`implements Rentable`) untuk memaksakan perhitungan total harga sewa.
