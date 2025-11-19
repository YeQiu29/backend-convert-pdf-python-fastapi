# 📄 BigPDF Backend API

![Python](https://img.shields.io/badge/python-3.9%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg?style=for-the-badge)

> **All-in-One PDF Manipulation Tool.**
> API Backend berkinerja tinggi untuk mengelola, mengonversi, dan memodifikasi file PDF. Dibangun dengan FastAPI dan pustaka Python modern untuk pemrosesan dokumen yang cepat dan akurat.

---

## 🏗️ Arsitektur & Alur Kerja

Berikut adalah gambaran teknis bagaimana **BigPDF** memproses dokumen:

```mermaid
graph LR
    A[👤 User / Client] -->|Upload PDF| B(🚀 FastAPI Server)
    B --> C{Router / Controller}
    C -->|/to-excel| D[📊 Camelot & PyMuPDF]
    C -->|/to-word| E[📝 pdf2docx]
    C -->|/merge| F[📚 pypdf]
    C -->|/watermark| G[💧 ReportLab]
    D & E & F & G --> H[💾 File Processing]
    H -->|StreamingResponse| A

📸 Demo & Preview
Aplikasi ini menyediakan antarmuka dokumentasi interaktif (Swagger UI) yang memudahkan pengujian API secara langsung tanpa perlu frontend.

(Antarmuka Swagger UI memungkinkan Anda menguji fitur seperti Konversi Excel, Watermark, dan Tanda Tangan secara real-time)

✨ Fitur Utama
Aplikasi ini menyediakan endpoint RESTful lengkap untuk berbagai kebutuhan dokumen:

Kategori,Fitur,Deskripsi
Konversi,🔄 PDF to Word,Konversi PDF ke .docx agar bisa diedit.
,🖼️ PDF to Images,Ekstrak setiap halaman menjadi gambar (ZIP).
,📊 PDF to Excel,"(Advanced) Ekstrak tabel PDF ke Excel, termasuk gambar dalam sel!"
,📽️ PDF to PPT,Konversi halaman PDF menjadi slide PowerPoint.
Organisasi,🧩 Merge PDF,Menggabungkan banyak file PDF menjadi satu.
,✂️ Split PDF,"Memisahkan PDF berdasarkan rentang halaman (cth: ""1-3, 5"")."
,🗑️ Delete Pages,Menghapus halaman yang tidak diinginkan.
,🔢 Arrange Pages,"Mengatur ulang urutan halaman (cth: ""3,1,2"")."
Edit & Keamanan,💧 Watermark,Menambahkan teks watermark transparan.
,✍️ Signature,"Menambahkan gambar tanda tangan presisi (X, Y coordinates)."
,🔄 Rotate,"Memutar halaman (90°, 180°, 270°)."
,🔒 Lock/Unlock,Enkripsi dan dekripsi file PDF dengan password.

🛠️ Teknologi yang Digunakan
Project ini memanfaatkan kekuatan ekosistem Python:

Framework: FastAPI & Uvicorn.

Core PDF: pypdf (Manipulasi dasar & Kriptografi).

Converters: * pdf2docx (Dokumen Word).

pdf2image (Rasterisasi Gambar).

Camelot & PyMuPDF (fitz) (Table Extraction Engine).

Graphics: ReportLab (Canvas drawing) & Pillow.

⚙️ Instalasi & Prasyarat
Karena aplikasi ini melakukan pemrosesan dokumen tingkat lanjut, diperlukan beberapa dependensi sistem.

1. System Dependencies (Wajib)
Poppler (Diperlukan untuk fitur PDF to Images/PPT):

Windows: Download Binary, ekstrak, dan tambahkan folder bin ke PATH Environment Variable.

Linux: sudo apt-get install poppler-utils

Ghostscript (Diperlukan untuk fitur PDF to Excel / Camelot):

Windows: Download installer dari Website Resmi Ghostscript.

Linux: sudo apt-get install ghostscript

2. Python Setup

# 1. Clone repository
git clone [https://github.com/username-anda/BigPDF-Backend.git](https://github.com/username-anda/BigPDF-Backend.git)
cd BigPDF-Backend

# 2. Buat Virtual Environment
python -m venv venv
# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate

# 3. Install Library Python
pip install fastapi uvicorn python-multipart pypdf pdf2docx pdf2image Pillow reportlab python-pptx camelot-py[cv] pandas openpyxl pymupdf

🚀 Cara Menjalankan
Jalankan server menggunakan Uvicorn (Server ASGI):
uvicorn convert_pdf:app --host 0.0.0.0 --port 8000 --reload

Setelah server berjalan, akses dokumentasi API di browser:

👉 http://localhost:8000/docs

📖 Contoh Penggunaan API
Anda dapat menggunakan cURL atau Postman. Berikut contoh menambahkan tanda tangan:
curl -X 'POST' \
  'http://localhost:8000/add-signature' \
  -H 'accept: application/pdf' \
  -H 'Content-Type: multipart/form-data' \
  -F 'file=@dokumen_kontrak.pdf;type=application/pdf' \
  -F 'signature_image=@ttd_saya.png;type=image/png' \
  -F 'page_number=1' \
  -F 'x_pos=100' \
  -F 'y_pos=200' \
  -F 'width=150'

🤝 Kontribusi
Kontribusi sangat diterima! Silakan fork repository ini dan buat Pull Request untuk fitur baru atau perbaikan bug.

1. Fork Project

2. Create Feature Branch (git checkout -b feature/AmazingFeature)

3. Commit Changes (git commit -m 'Add some AmazingFeature')

4. Push to Branch (git push origin feature/AmazingFeature)

5. Open Pull Request

📝 Lisensi
Didistribusikan di bawah lisensi MIT.

<div align="center"> Made with ❤️ by <a href="https://www.google.com/search?q=https://github.com/username-anda">Nama Anda</a> </div>
