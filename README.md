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

## ✨ Fitur Utama

Aplikasi ini menyediakan endpoint RESTful lengkap untuk berbagai kebutuhan dokumen:

| Kategori | Fitur | Deskripsi |
| :--- | :--- | :--- |
| **Konversi** | 🔄 **PDF to Word** | Konversi PDF ke `.docx` editable. |
| | 🖼️ **PDF to Images** | Ekstrak setiap halaman menjadi gambar dalam file `.zip`. |
| | 📊 **PDF to Excel** | **(Advanced)** Ekstrak tabel PDF ke Excel, *termasuk gambar di dalam sel!* |
| | 📽️ **PDF to PPT** | Konversi halaman PDF menjadi slide PowerPoint. |
| **Organisasi** | 🧩 **Merge PDF** | Menggabungkan banyak file PDF menjadi satu. |
| | ✂️ **Split PDF** | Memisahkan PDF berdasarkan rentang halaman tertentu. |
| | 🗑️ **Delete Pages** | Menghapus halaman yang tidak diinginkan. |
| | 🔢 **Arrange Pages** | Mengatur ulang urutan halaman. |
| **Edit & Keamanan** | 💧 **Watermark** | Menambahkan teks watermark transparan. |
| | ✍️ **Signature** | Menambahkan gambar tanda tangan presisi (X, Y coordinates). |
| | 🔄 **Rotate** | Memutar halaman (90°, 180°, 270°). |
| | 🔒 **Lock/Unlock** | Enkripsi dan dekripsi file PDF dengan password. |

---

## 🛠️ Tech Stack

Project ini dibangun menggunakan teknologi open-source terbaik:

* **Core Framework:** [FastAPI](https://fastapi.tiangolo.com/) (High performance, easy to learn).
* **Server:** Uvicorn.
* **PDF Engines:**
    * `pypdf` (Manipulasi dasar & Kriptografi).
    * `pdf2docx` (Konversi Word).
    * `pdf2image` (Konversi Raster/Image).
    * `Camelot` & `PyMuPDF (fitz)` (Ekstraksi Tabel & Gambar Excel).
    * `ReportLab` (Canvas drawing untuk Watermark/Signature).

---

## ⚙️ Instalasi & Prasyarat

Karena project ini menggunakan manipulasi gambar dan tabel tingkat lanjut, Anda memerlukan beberapa *system dependencies*.

### 1. System Dependencies

Pastikan tool berikut terinstall di OS Anda:

* **Poppler** (Wajib untuk `pdf2image` / PDF to PPT)
    * *Windows:* Download binary, ekstrak, dan tambahkan folder `bin` ke PATH environment variable.
    * *Linux:* `sudo apt-get install poppler-utils`
    * *Mac:* `brew install poppler`
* **Ghostscript** (Wajib untuk `camelot` / PDF to Excel)
    * *Windows:* Download installer dari website resmi Ghostscript.
    * *Linux:* `sudo apt-get install ghostscript`

### 2. Clone & Install Python Packages

```bash
# Clone repository
git clone [https://github.com/username-anda/BigPDF-Backend.git](https://github.com/username-anda/BigPDF-Backend.git)
cd BigPDF-Backend

# Buat Virtual Environment (Recommended)
python -m venv venv
source venv/bin/activate  # Atau `venv\Scripts\activate` di Windows

# Install Dependencies
pip install -r requirements.txt
