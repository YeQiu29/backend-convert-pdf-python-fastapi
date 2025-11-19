📄 BigPDF Backend API










All-in-One PDF Manipulation Tool
Backend API berkinerja tinggi untuk mengolah, mengonversi, dan memodifikasi PDF.
Dibangun dengan FastAPI & pustaka Python modern.

🏗️ Arsitektur & Alur Kerja
graph LR
    A[👤 User / Client] -->|Upload PDF| B(🚀 FastAPI Server)
    B --> C{Router / Controller}
    C -->|/to-excel| D[📊 Camelot & PyMuPDF]
    C -->|/to-word| E[📝 pdf2docx]
    C -->|/merge| F[📚 pypdf]
    C -->|/watermark| G[💧 ReportLab]
    D & E & F & G --> H[💾 File Processing]
    H -->|StreamingResponse| A

✨ Fitur Utama
🔄 Konversi
Fitur	Deskripsi
PDF → Word	Konversi PDF ke .docx.
PDF → Images	Ekstrak halaman menjadi gambar (ZIP).
PDF → Excel	Ekstrak tabel, termasuk gambar dalam sel.
PDF → PPT	Konversi halaman PDF ke slide PowerPoint.
🧩 Organisasi
Fitur	Deskripsi
Merge PDF	Menggabungkan banyak PDF.
Split PDF	Memisahkan PDF berdasarkan rentang halaman (1-3,5).
Delete Pages	Menghapus halaman tertentu.
Arrange Pages	Mengatur ulang urutan halaman (3,1,2).
🛡️ Edit & Keamanan
Fitur	Deskripsi
Watermark	Tambah watermark teks transparan.
Signature	Tambah gambar tanda tangan (koordinat X,Y).
Rotate	Putar halaman 90°, 180°, 270°.
Lock/Unlock	Enkripsi dan dekripsi PDF.
🛠️ Teknologi yang Digunakan

FastAPI, Uvicorn

pypdf (manipulasi PDF & enkripsi)

pdf2docx

pdf2image

Camelot + PyMuPDF

ReportLab, Pillow

python-pptx

⚙️ Instalasi & Prasyarat
1️⃣ System Dependencies
Poppler (untuk PDF → Images / PPT)

Windows: download binary Poppler, tambahkan bin/ ke PATH

Linux:

sudo apt-get install poppler-utils

Ghostscript (untuk PDF → Excel)

Windows: download installer resmi Ghostscript

Linux:

sudo apt-get install ghostscript

2️⃣ Python Setup
# Clone repository
git clone https://github.com/username-anda/BigPDF-Backend.git
cd BigPDF-Backend

# Buat virtual environment
python -m venv venv

# Aktivasi
# Windows:
venv\Scripts\activate
# Linux/Mac:
source venv/bin/activate

# Install dependency
pip install fastapi uvicorn python-multipart pypdf pdf2docx pdf2image Pillow reportlab python-pptx camelot-py[cv] pandas openpyxl pymupdf

🚀 Menjalankan Server
uvicorn convert_pdf:app --host 0.0.0.0 --port 8000 --reload


Buka dokumentasi API (Swagger UI):
👉 http://localhost:8000/docs

📖 Contoh Penggunaan API
➕ Tambah Tanda Tangan ke PDF
curl -X POST "http://localhost:8000/add-signature" \
  -H "accept: application/pdf" \
  -H "Content-Type: multipart/form-data" \
  -F "file=@dokumen_kontrak.pdf;type=application/pdf" \
  -F "signature_image=@ttd_saya.png;type=image/png" \
  -F "page_number=1" \
  -F "x_pos=100" \
  -F "y_pos=200" \
  -F "width=150"

🤝 Kontribusi

Fork repository

Buat branch fitur

Commit perubahan

Push ke branch

Buat Pull Request

📝 Lisensi

Dirilis di bawah lisensi MIT.

<div align="center"> Made with ❤️ by <a href="https://github.com/username-anda">Nama Anda</a> </div>
