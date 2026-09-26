# Library App — Latihan Kuis Mobile

Aplikasi Flutter sederhana sesuai ketentuan `Latihan Kuis Mobile.md`:
Login Page → Library Page → Book Detail Page.

## Struktur Proyek

```
library_app/
├── pubspec.yaml
└── lib/
    ├── main.dart                  # Entry point, tema, home = LoginPage
    ├── models/
    │   └── book_model.dart        # class BookModel + bookList (dari bookModels.dart kamu)
    └── pages/
        ├── login_page.dart        # Halaman login dengan akun dummy
        ├── library_page.dart      # GridView daftar buku
        └── book_detail_page.dart  # Detail lengkap satu buku
```

## Cara Menjalankan

1. Buat proyek Flutter baru (jika belum ada):
   ```
   flutter create library_app
   ```
2. Salin isi folder `lib/` dari sini ke folder `lib/` proyekmu (timpa `main.dart`).
3. Jalankan:
   ```
   flutter pub get
   flutter run
   ```

## Akun Dummy Login

- Email: `admin@mail.com`
- Password: `123456`

Jika email/password salah, akan muncul pesan **"Email atau password tidak sesuai"**.

## Alur Navigasi (sesuai ketentuan bagian D)

- **Login Page → Library Page**: `Navigator.pushReplacement` setelah login berhasil (memakai `pushReplacement` supaya user tidak bisa "back" ke halaman login).
- **Library Page → Book Detail Page**: `Navigator.push`, objek `BookModel` yang dipilih dikirim langsung lewat constructor `BookDetailPage(book: book)`.
- **Book Detail Page → kembali ke Library Page**: tombol back bawaan `AppBar` (otomatis muncul karena halaman ini di-push, cukup `Navigator.pop`).

## Catatan

- Setiap kartu buku di Library Page memakai `InkWell` agar bisa ditekan dan menampilkan cover (`imageUrl`), judul, penulis, dan tahun terbit.
- Beberapa `imageUrl` dari `bookModels.dart` adalah link Amazon yang bisa saja gagal dimuat — sudah ditangani dengan `errorBuilder` sehingga menampilkan ikon placeholder, bukan crash.
- Semua data buku diambil dari `bookList` yang ada di `lib/models/book_model.dart` (isinya sama persis dengan `bookModels.dart` yang kamu kirim, hanya dipindahkan ke struktur folder `lib/models/`).
