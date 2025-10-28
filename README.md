<div align="center">

# 📚 Bookshelf API

### *Your Digital Library Manager*

![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)
![Hapi](https://img.shields.io/badge/Hapi.js-F26722?style=for-the-badge&logo=hapi&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![ESLint](https://img.shields.io/badge/ESLint-4B32C3?style=for-the-badge&logo=eslint&logoColor=white)

**A RESTful API for managing your book collection with style and efficiency**

[Features](#-features) • [Quick Start](#-quick-start) • [API Documentation](#-api-documentation) • [Examples](#-usage-examples) • [Contributing](#-connect-with-me)

</div>

---

## 🌟 Features

<table>
<tr>
<td width="50%">

### 📖 **Book Management**
- ✅ Add new books to your collection
- ✅ View all books with smart filtering
- ✅ Get detailed book information
- ✅ Update book details
- ✅ Remove books from collection

</td>
<td width="50%">

### 🎯 **Advanced Features**
- 🔍 Filter by name (case-insensitive)
- 📊 Filter by reading status
- ✔️ Filter by completion status
- 🚀 Fast and lightweight
- 🔐 Input validation & error handling

</td>
</tr>
</table>

---

## 🛠️ Tech Stack

| Technology | Purpose | Version |
|-----------|---------|---------|
| **Node.js** | Runtime Environment | LTS |
| **Hapi Framework** | Web Framework | ^21.3.2 |
| **nanoid** | Unique ID Generation | ^3.3.7 |
| **ESLint** | Code Quality | ^8.56.0 |
| **Airbnb Style Guide** | Code Standards | ^15.0.0 |

---

## 🚀 Quick Start

### Prerequisites
- Node.js (LTS version recommended)
- npm or yarn

### Installation

```bash
# Clone the repository
git clone <your-repo-url>

# Navigate to project directory
cd "Bookshelf API"

# Install dependencies
npm install

# Start the server
npm run start
```

🎉 **Server is running on** `http://localhost:9000`

### Development Mode

```bash
# Run with auto-reload (nodemon)
npm run start-dev
```

### Code Quality Check

```bash
# Run ESLint
npm run lint
```

---

## 📡 API Documentation

### Base URL
```
http://localhost:9000
```

### Endpoints Overview

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| `POST` | `/books` | Add a new book | ❌ |
| `GET` | `/books` | Get all books | ❌ |
| `GET` | `/books/{bookId}` | Get book details | ❌ |
| `PUT` | `/books/{bookId}` | Update a book | ❌ |
| `DELETE` | `/books/{bookId}` | Delete a book | ❌ |

---

### 📗 1. Add New Book

**Endpoint:** `POST /books`

**Request Body:**
```json
{
  "name": "Clean Code",
  "year": 2008,
  "author": "Robert C. Martin",
  "summary": "A Handbook of Agile Software Craftsmanship",
  "publisher": "Prentice Hall",
  "pageCount": 464,
  "readPage": 200,
  "reading": true
}
```

**Success Response (201):**
```json
{
  "status": "success",
  "message": "Buku berhasil ditambahkan",
  "data": {
    "bookId": "Qbax5Oy7L8WKf74l"
  }
}
```

**Error Responses:**

<details>
<summary>Missing Name (400)</summary>

```json
{
  "status": "fail",
  "message": "Gagal menambahkan buku. Mohon isi nama buku"
}
```
</details>

<details>
<summary>Invalid readPage (400)</summary>

```json
{
  "status": "fail",
  "message": "Gagal menambahkan buku. readPage tidak boleh lebih besar dari pageCount"
}
```
</details>

---

### 📘 2. Get All Books

**Endpoint:** `GET /books`

**Query Parameters:**

| Parameter | Type | Values | Description |
|-----------|------|--------|-------------|
| `name` | string | any text | Filter by book name (case-insensitive) |
| `reading` | number | 0 or 1 | 0 = not reading, 1 = currently reading |
| `finished` | number | 0 or 1 | 0 = unfinished, 1 = finished |

**Example Requests:**
```bash
GET /books
GET /books?name=dicoding
GET /books?reading=1
GET /books?finished=0
GET /books?name=clean&reading=1
```

**Success Response (200):**
```json
{
  "status": "success",
  "data": {
    "books": [
      {
        "id": "Qbax5Oy7L8WKf74l",
        "name": "Clean Code",
        "publisher": "Prentice Hall"
      },
      {
        "id": "1L7ZtDUFeGs7VlEt",
        "name": "Design Patterns",
        "publisher": "Addison-Wesley"
      }
    ]
  }
}
```

---

### 📙 3. Get Book Details

**Endpoint:** `GET /books/{bookId}`

**Success Response (200):**
```json
{
  "status": "success",
  "data": {
    "book": {
      "id": "Qbax5Oy7L8WKf74l",
      "name": "Clean Code",
      "year": 2008,
      "author": "Robert C. Martin",
      "summary": "A Handbook of Agile Software Craftsmanship",
      "publisher": "Prentice Hall",
      "pageCount": 464,
      "readPage": 200,
      "finished": false,
      "reading": true,
      "insertedAt": "2024-10-28T07:30:00.000Z",
      "updatedAt": "2024-10-28T07:30:00.000Z"
    }
  }
}
```

**Error Response (404):**
```json
{
  "status": "fail",
  "message": "Buku tidak ditemukan"
}
```

---

### 📕 4. Update Book

**Endpoint:** `PUT /books/{bookId}`

**Request Body:** (Same as POST /books)

**Success Response (200):**
```json
{
  "status": "success",
  "message": "Buku berhasil diperbarui"
}
```

**Error Responses:**

<details>
<summary>Missing Name (400)</summary>

```json
{
  "status": "fail",
  "message": "Gagal memperbarui buku. Mohon isi nama buku"
}
```
</details>

<details>
<summary>Invalid readPage (400)</summary>

```json
{
  "status": "fail",
  "message": "Gagal memperbarui buku. readPage tidak boleh lebih besar dari pageCount"
}
```
</details>

<details>
<summary>Book Not Found (404)</summary>

```json
{
  "status": "fail",
  "message": "Gagal memperbarui buku. Id tidak ditemukan"
}
```
</details>

---

### 🗑️ 5. Delete Book

**Endpoint:** `DELETE /books/{bookId}`

**Success Response (200):**
```json
{
  "status": "success",
  "message": "Buku berhasil dihapus"
}
```

**Error Response (404):**
```json
{
  "status": "fail",
  "message": "Buku gagal dihapus. Id tidak ditemukan"
}
```

---

## 💡 Usage Examples

### Using cURL

```bash
# Add a book
curl -X POST http://localhost:9000/books \
  -H "Content-Type: application/json" \
  -d '{
    "name": "The Pragmatic Programmer",
    "year": 1999,
    "author": "Andrew Hunt & David Thomas",
    "summary": "Your Journey to Mastery",
    "publisher": "Addison-Wesley",
    "pageCount": 352,
    "readPage": 100,
    "reading": true
  }'

# Get all books
curl http://localhost:9000/books

# Get books currently being read
curl http://localhost:9000/books?reading=1

# Get book by ID
curl http://localhost:9000/books/Qbax5Oy7L8WKf74l

# Update a book
curl -X PUT http://localhost:9000/books/Qbax5Oy7L8WKf74l \
  -H "Content-Type: application/json" \
  -d '{"name": "Updated Book Name", ...}'

# Delete a book
curl -X DELETE http://localhost:9000/books/Qbax5Oy7L8WKf74l
```

### Using JavaScript (Fetch API)

```javascript
// Add a book
const addBook = async () => {
  const response = await fetch('http://localhost:9000/books', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify({
      name: 'JavaScript: The Good Parts',
      year: 2008,
      author: 'Douglas Crockford',
      summary: 'Unearthing the Excellence in JavaScript',
      publisher: "O'Reilly Media",
      pageCount: 176,
      readPage: 176,
      reading: false
    })
  });
  
  const data = await response.json();
  console.log(data);
};

// Get all books with filter
const getBooks = async () => {
  const response = await fetch('http://localhost:9000/books?name=javascript');
  const data = await response.json();
  console.log(data.data.books);
};
```

---

## 📂 Project Structure

```
📦 Bookshelf API
├── 📁 src
│   ├── 📄 books.js          # In-memory data storage
│   ├── 📄 handler.js        # Request handlers & business logic
│   ├── 📄 routes.js         # API route definitions
│   └── 📄 server.js         # Server initialization & config
├── 📁 node_modules          # Dependencies (gitignored)
├── 📄 .eslintrc.js          # ESLint configuration
├── 📄 .gitignore            # Git ignore rules
├── 📄 package.json          # Project metadata & scripts
├── 📄 package-lock.json     # Dependency lock file
└── 📄 README.md             # You are here! 👋
```

---

## 🎯 Key Features Explained

### 🔄 Auto-Generated Fields

When you add a book, these fields are automatically generated:

- **`id`**: Unique identifier using nanoid (16 characters)
- **`finished`**: Boolean (`pageCount === readPage`)
- **`insertedAt`**: ISO timestamp of creation
- **`updatedAt`**: ISO timestamp of last update

### 🎨 Data Validation

The API includes robust validation:

- ✅ Book name is required
- ✅ `readPage` cannot exceed `pageCount`
- ✅ Proper error messages for debugging
- ✅ Consistent response format

### 🔍 Smart Filtering

Filter books intelligently:

- **Name**: Case-insensitive partial matching
- **Reading Status**: Boolean conversion from 0/1
- **Finished Status**: Boolean conversion from 0/1
- **Chainable**: Combine multiple filters

---

## 🧪 Testing

### Manual Testing with Postman

1. Import the collection (create your own or use the endpoints above)
2. Set base URL: `http://localhost:9000`
3. Test each endpoint with various scenarios

### Test Scenarios

- ✅ Add book with valid data
- ✅ Add book without name (should fail)
- ✅ Add book with readPage > pageCount (should fail)
- ✅ Get all books
- ✅ Get books with filters
- ✅ Get specific book by ID
- ✅ Get non-existent book (should return 404)
- ✅ Update book with valid data
- ✅ Update book with invalid data
- ✅ Delete book
- ✅ Delete non-existent book (should return 404)

---

## ⚙️ Configuration

### Port Configuration

Default port is `9000`. To change it, modify `src/server.js`:

```javascript
const server = Hapi.server({
  port: 9000, // Change this
  host: 'localhost',
  // ...
});
```

### CORS Configuration

CORS is enabled for all origins. To restrict, modify `src/server.js`:

```javascript
routes: {
  cors: {
    origin: ['http://localhost:3000'], // Specific origins
  },
}
```

---

## 📝 Notes & Limitations

> ⚠️ **Important**: This API uses **in-memory storage** (JavaScript array). All data will be lost when the server restarts. This design is intentional for:
> - Learning purposes
> - Easy testing without database setup
> - Lightweight deployment

For production use, consider implementing:
- 📊 Database integration (MongoDB, PostgreSQL, etc.)
- 🔐 Authentication & Authorization
- 📚 Pagination for large datasets
- 🔄 Data persistence
- 🛡️ Rate limiting
- 📝 Request logging

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

### Development Setup

```bash
# Install dependencies
npm install

# Run in development mode
npm run start-dev

# Check code quality
npm run lint

# Fix ESLint issues
npx eslint . --fix
```

### Code Style

This project follows the [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript).

---

## 📄 License

This project is open source and available under the [ISC License](LICENSE).

---

## 🌐 Connect With Me

Feel free to reach out for questions, suggestions, or collaborations!

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/surya-hanjaya/)
[![GitHub](https://img.shields.io/badge/GitHub-333333?style=for-the-badge&logo=github&logoColor=white)](https://github.com/suryahanjaya)
[![Instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/h4njy/)

---

**Made with ❤️ and ☕ by Surya Hanjaya**

⭐ **Star this repo if you find it helpful!**

</div>

