# Bookshelf API

API sederhana untuk mengelola koleksi buku menggunakan Hapi Framework.

## Fitur

- Menambahkan buku baru
- Menampilkan semua buku
- Menampilkan detail buku berdasarkan ID
- Mengubah data buku
- Menghapus buku
- Filter buku berdasarkan nama, status reading, dan status finished

## Teknologi

- Node.js
- Hapi Framework
- nanoid
- ESLint (Airbnb Style Guide)

## Instalasi

1. Clone repository ini
2. Install dependencies:
```bash
npm install
```

## Menjalankan Aplikasi

### Mode Production
```bash
npm run start
```

### Mode Development (dengan nodemon)
```bash
npm run start-dev
```

Server akan berjalan di `http://localhost:9000`

## API Endpoints

### 1. Menambahkan Buku
- **Method**: POST
- **URL**: `/books`
- **Body**:
```json
{
  "name": "string",
  "year": "number",
  "author": "string",
  "summary": "string",
  "publisher": "string",
  "pageCount": "number",
  "readPage": "number",
  "reading": "boolean"
}
```

### 2. Menampilkan Semua Buku
- **Method**: GET
- **URL**: `/books`
- **Query Parameters**:
  - `name`: Filter berdasarkan nama (case-insensitive)
  - `reading`: 0 (tidak dibaca) atau 1 (sedang dibaca)
  - `finished`: 0 (belum selesai) atau 1 (sudah selesai)

### 3. Menampilkan Detail Buku
- **Method**: GET
- **URL**: `/books/{bookId}`

### 4. Mengubah Data Buku
- **Method**: PUT
- **URL**: `/books/{bookId}`
- **Body**: Sama seperti saat menambahkan buku

### 5. Menghapus Buku
- **Method**: DELETE
- **URL**: `/books/{bookId}`

## Linting

Untuk memeriksa kualitas kode:
```bash
npm run lint
```

## Struktur Proyek

```
Bookshelf API/
├── src/
│   ├── books.js      # Data storage
│   ├── handler.js    # Request handlers
│   ├── routes.js     # Route definitions
│   └── server.js     # Server initialization
├── .eslintrc.js      # ESLint configuration
├── .gitignore
├── package.json
└── README.md
```

## Catatan

- Data disimpan di memory (array), sehingga akan hilang saat server direstart
- Port default: 9000
- CORS diaktifkan untuk semua origin

