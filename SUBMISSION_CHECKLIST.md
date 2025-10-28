# Checklist Submission Bookshelf API

## ✅ Kriteria yang Telah Dipenuhi

### ✅ Kriteria 1: Port 9000
- Server menggunakan port 9000
- Dapat dilihat di `src/server.js` line 6

### ✅ Kriteria 2: npm run start
- Script `start` tersedia di package.json
- Menggunakan `node src/server.js` (BUKAN nodemon)
- Script `start-dev` tersedia untuk development dengan nodemon

### ✅ Kriteria 3: API Menyimpan Buku
- Endpoint POST /books tersedia
- Handler di `src/handler.js` - function `addBookHandler`
- Validasi nama buku (wajib diisi)
- Validasi readPage tidak boleh lebih besar dari pageCount
- Generate ID unik menggunakan nanoid
- Generate finished, insertedAt, dan updatedAt otomatis
- Response sesuai spesifikasi (201 untuk sukses, 400 untuk gagal)

### ✅ Kriteria 4: API Menampilkan Semua Buku
- Endpoint GET /books tersedia
- Handler di `src/handler.js` - function `getAllBooksHandler`
- Response hanya menampilkan id, name, dan publisher
- Response 200 dengan array books (bisa kosong)

### ✅ Kriteria 5: API Menampilkan Detail Buku
- Endpoint GET /books/{bookId} tersedia
- Handler di `src/handler.js` - function `getBookByIdHandler`
- Response 404 jika buku tidak ditemukan
- Response 200 dengan detail lengkap buku jika ditemukan

### ✅ Kriteria 6: API Mengubah Data Buku
- Endpoint PUT /books/{bookId} tersedia
- Handler di `src/handler.js` - function `editBookByIdHandler`
- Validasi nama buku (wajib diisi)
- Validasi readPage tidak boleh lebih besar dari pageCount
- Validasi ID (404 jika tidak ditemukan)
- Update finished dan updatedAt otomatis
- Response sesuai spesifikasi

### ✅ Kriteria 7: API Menghapus Buku
- Endpoint DELETE /books/{bookId} tersedia
- Handler di `src/handler.js` - function `deleteBookByIdHandler`
- Response 404 jika ID tidak ditemukan
- Response 200 jika berhasil dihapus

### ✅ Fitur Tambahan: Query Parameters
- Filter berdasarkan `?name=` (case-insensitive)
- Filter berdasarkan `?reading=0` atau `?reading=1`
- Filter berdasarkan `?finished=0` atau `?finished=1`
- Implementasi di `src/handler.js` - function `getAllBooksHandler`

### ✅ ESLint
- ESLint sudah dikonfigurasi
- Menggunakan Airbnb Style Guide
- Perintah `npx eslint .` tidak menampilkan error
- Script lint tersedia: `npm run lint`

## 📋 Sebelum Submit

### Hal yang HARUS dilakukan:
1. ✅ Pastikan folder node_modules DIHAPUS
2. ✅ Pastikan file package.json ada
3. ✅ Test dengan perintah:
   ```bash
   npm install
   npm run start
   ```
4. ✅ Verifikasi ESLint:
   ```bash
   npx eslint .
   ```

### File yang akan di-submit:
```
Bookshelf API/
├── src/
│   ├── books.js
│   ├── handler.js
│   ├── routes.js
│   └── server.js
├── .eslintrc.js
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

### ⚠️ PENTING - Jangan Submit Jika:
- ❌ Ada folder node_modules
- ❌ Port bukan 9000
- ❌ Script start menggunakan nodemon
- ❌ Menggunakan database eksternal
- ❌ Menggunakan JSON file untuk storage
- ❌ npx eslint . menampilkan error

## 🧪 Testing

### Test Manual dengan curl/Postman:

1. **Tambah Buku**
```
POST http://localhost:9000/books
Body: {
  "name": "Buku A",
  "year": 2010,
  "author": "John Doe",
  "summary": "Lorem ipsum",
  "publisher": "Dicoding",
  "pageCount": 100,
  "readPage": 25,
  "reading": false
}
```

2. **Lihat Semua Buku**
```
GET http://localhost:9000/books
```

3. **Lihat Detail Buku**
```
GET http://localhost:9000/books/{bookId}
```

4. **Update Buku**
```
PUT http://localhost:9000/books/{bookId}
Body: (sama seperti POST)
```

5. **Hapus Buku**
```
DELETE http://localhost:9000/books/{bookId}
```

6. **Filter Buku**
```
GET http://localhost:9000/books?name=dicoding
GET http://localhost:9000/books?reading=1
GET http://localhost:9000/books?finished=0
```

## 📦 Cara Submit

1. Hapus folder node_modules:
   ```bash
   rmdir /s /q node_modules
   ```

2. Compress folder menjadi ZIP

3. Upload ke platform submission

## ✨ Framework yang Digunakan
- **Hapi Framework** (@hapi/hapi)
- Node.js version: LTS terbaru
- Penyimpanan: In-memory (array)

