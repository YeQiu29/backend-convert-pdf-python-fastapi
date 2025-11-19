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
