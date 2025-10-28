# 📝 Todolist RESTful API

Todolist RESTful API adalah layanan yang menyediakan endpoint untuk mengelola data *todolist* seperti menampilkan daftar tugas, menambah tugas baru, memperbarui, dan menghapus tugas.  
Spesifikasi ini ditulis menggunakan **OpenAPI 3.1.0**.

---

## 📘 Informasi API

| Kunci | Nilai |
|-------|--------|
| **Title** | Todolist RESTful API |
| **Version** | 1 |
| **Description** | OpenAPI for Todolist RESTful API |
| **Terms of Service** | [https://www.indradwiprabowo.com](https://www.indradwiprabowo.com) |
| **Contact Name** | Indra Dwi Prabowo |
| **Email** | [indradwiprabowo27@gmail.com](mailto:indradwiprabowo27@gmail.com) |
| **Website** | [https://www.indradwiprabowo.com](https://www.indradwiprabowo.com) |
| **License** | [APACHE 2.0](https://www.apache.org/licenses/LICENSE-2.0) |

---

## 🌍 Server

Base URL:  
https://{environment}.indradwiprabowo.com/api/v1

yaml
Copy code

### 🔧 Environment Variables

| Nama | Default | Opsi | Deskripsi |
|------|----------|------|------------|
| `environment` | `dev` | `dev`, `qa`, `prod` | Server Environment |

---

## 📄 External Documentation

- **Reference Video:** [Programmer Zaman Now - OpenAPI](https://www.youtube.com/watch?v=o5b6TYSNK5c&t=1s)

---

## 🚀 Endpoints

### **1. GET /todolist**
**Deskripsi:**  
Menampilkan seluruh daftar todolist yang aktif secara default.

**Query Parameters:**
| Nama | Tipe | Wajib | Deskripsi |
|------|------|--------|------------|
| `include_done` | boolean | ❌ | Apakah daftar yang selesai (*done*) ikut ditampilkan |
| `name` | string | ❌ | Filter daftar todolist berdasarkan nama |

**Contoh Request:**
```bash
GET https://dev.indradwiprabowo.com/api/v1/todolist?include_done=true
Contoh Response (200 OK):

json
Copy code
[
  {
    "id": "1",
    "name": "Belajar OpenAPI",
    "status": "active",
    "created_at": "2025-10-28T10:00:00Z"
  },
  {
    "id": "2",
    "name": "Mengerjakan Tugas Kuliah",
    "status": "done",
    "created_at": "2025-10-28T09:00:00Z"
  }
]
2. POST /todolist
Deskripsi:
Menambahkan todolist baru ke dalam database.

Contoh Request:

bash
Copy code
POST https://dev.indradwiprabowo.com/api/v1/todolist
Content-Type: application/json

{
  "name": "Belajar OpenAPI",
  "description": "Menyelesaikan dokumentasi API"
}
Contoh Response (201 Created):

json
Copy code
{
  "id": "3",
  "name": "Belajar OpenAPI",
  "description": "Menyelesaikan dokumentasi API",
  "status": "active",
  "created_at": "2025-10-28T11:00:00Z"
}
3. PUT /todolist/{todolistId}
Deskripsi:
Memperbarui data todolist berdasarkan ID.

Path Parameter:

Nama	Tipe	Wajib	Deskripsi
todolistId	string	✅	ID todolist yang ingin diperbarui

Contoh Request:

bash
Copy code
PUT https://dev.indradwiprabowo.com/api/v1/todolist/3
Content-Type: application/json

{
  "name": "Belajar OpenAPI (Update)",
  "status": "done"
}
Contoh Response (200 OK):

json
Copy code
{
  "id": "3",
  "name": "Belajar OpenAPI (Update)",
  "status": "done",
  "updated_at": "2025-10-28T12:00:00Z"
}
4. DELETE /todolist/{todolistId}
Deskripsi:
Menghapus data todolist berdasarkan ID.

Path Parameter:

Nama	Tipe	Wajib	Deskripsi
todolistId	string	✅	ID todolist yang ingin dihapus

Contoh Request:

bash
Copy code
DELETE https://dev.indradwiprabowo.com/api/v1/todolist/3
Contoh Response (200 OK):

json
Copy code
{
  "message": "Todolist deleted successfully"
}
🧩 Status Response
Status	Deskripsi
200	Request berhasil
201	Data berhasil dibuat
400	Request tidak valid
404	Data tidak ditemukan
500	Terjadi kesalahan server

🧠 Tips Penggunaan
Gunakan environment dev untuk pengujian.

Pastikan setiap request yang memodifikasi data (POST, PUT, DELETE) memiliki header:

pgsql
Copy code
Content-Type: application/json
Gunakan tool seperti Postman atau Insomnia untuk mencoba endpoint secara langsung.

📚 Lisensi
Dilisensikan di bawah Apache License 2.0.

Dibuat oleh:
👨‍💻 Indra Dwi Prabowo
📧 indradwiprabowo27@gmail.com