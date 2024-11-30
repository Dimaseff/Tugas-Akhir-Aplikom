# Tugas Akhir Projek Aplikasi Komputer

Ini adalah kumpulan projek yang saya buat selama melakukan perkuliahan Aplikasi Komputer pada semester 3 di jurusan Matematika, Fakultas Matematika dan Ilmu Pengetahuan Alam, Universitas Negeri Yogyakarta. Semoga dengan adanya projek ini bisa membantu teman-teman untuk lebih memahami mata kuliah terkait.

## **File-file dalam laman ini terdiri atas:** ##
1. **FILE SETIAP MATERI DALAM FORMAT EMT (.en)**
2. **IMAGES SETIAP MATERI (.png)**
3. **FILE SETIAP MATERI DALAM FORMAT TEX DOCUMENT (.tex)**
4. **FILE SETIAP MATERI DALAM FORMAT MARKDOWN (.md)**
5. **FILE SETIAP MATERI DALAM FORMAT PDF (.pdf)**

### **Tentu! Mari kita bahas **EMT (Euler Math Toolbox)** , **LaTeX** , dan **Markdown** secara lebih mendetail.** ###  

---

### **EMT (Euler Math Toolbox)**

#### **Apa itu EMT?**
EMT adalah perangkat lunak matematika yang menggabungkan kekuatan perhitungan simbolik dan numerik. Ini seperti gabungan kalkulator ilmiah tingkat lanjut dengan kemampuan pemrograman. EMT dirancang untuk menyelesaikan masalah matematika kompleks dengan cara yang sederhana, cepat, dan efisien.

#### **Fitur Utama EMT:**
1. **Pemrograman Sederhana:**  
   EMT menggunakan sintaks yang mudah dipelajari untuk melakukan operasi matematika. Contoh:
   ```em
   a = 2
   b = 3
   c = a^2 + b^2
   print(c)
   ```
   Ini akan menghasilkan output: `13`.

2. **Matematika Numerik:**  
   - Analisis matriks, seperti invers, determinan, dan eigenvalue.  
   - Solusi numerik untuk persamaan diferensial atau integral.
   - Pemrosesan data dalam skala besar.

3. **Perhitungan Simbolik (melalui Maxima):**  
   EMT dapat memanfaatkan **Maxima** untuk melakukan manipulasi aljabar simbolik. Misalnya:
   ```em
   solve(x^2 - 4 = 0, x)
   ```
   Akan menghasilkan solusi simbolik: \( x = \pm 2 \).

4. **Grafik 2D dan 3D:**  
   EMT memungkinkan Anda membuat grafik matematika dengan mudah. Contoh:
   ```em
   plot2d("sin(x)", -2*pi, 2*pi)
   ```

5. **Kombinasi dengan Bahasa Lain:**  
   EMT bisa digabungkan dengan Python, MATLAB, atau LaTeX untuk dokumentasi atau analisis lanjutan.

#### **Kelebihan EMT:**
- Gratis dan open-source.
- Cocok untuk pendidikan dan penelitian.
- Mendukung berbagai jenis analisis matematis.

#### **Penggunaan EMT:**
- **Akademik**: Memecahkan soal matematika, membuat grafik fungsi.
- **Penelitian**: Menganalisis data numerik atau simbolik.
- **Industri**: Optimasi dan pemodelan matematika.

---

### **LaTeX**

#### **Apa itu LaTeX?**
LaTeX adalah sistem penyusunan dokumen berbasis markup yang dirancang untuk menghasilkan dokumen dengan kualitas tinggi. LaTeX sangat populer di kalangan akademisi, khususnya di bidang matematika, fisika, dan ilmu komputer.

#### **Cara Kerja LaTeX:**
Dokumen LaTeX dibuat dengan menulis kode dalam file teks biasa dengan ekstensi `.tex`, yang kemudian dikompilasi menjadi format PDF atau format lain.  

#### **Contoh Dasar LaTeX:**
```latex
\documentclass{article}
\begin{document}
Hello, this is a simple LaTeX document.

Here is an equation: 
\[ E = mc^2 \]

\end{document}
```
Kode di atas menghasilkan dokumen PDF yang berisi teks biasa dan satu persamaan \( E = mc^2 \).

#### **Fitur Utama LaTeX:**
1. **Penulisan Matematis:**  
   LaTeX mendukung semua simbol dan operasi matematika. Contoh:
   ```latex
   \[ \int_{0}^{\infty} e^{-x^2} \, dx = \frac{\sqrt{\pi}}{2} \]
   ```
   Akan menghasilkan:
   \[
   \int_{0}^{\infty} e^{-x^2} \, dx = \frac{\sqrt{\pi}}{2}
   \]

2. **Format yang Konsisten:**  
   Dokumen LaTeX memiliki format yang rapi, terutama untuk dokumen ilmiah dengan banyak referensi, tabel, atau gambar.

3. **Fleksibilitas:**  
   LaTeX bisa digunakan untuk membuat:
   - Buku.
   - Tesis.
   - Artikel jurnal.
   - Slide presentasi (dengan Beamer).

4. **Manajemen Referensi:**  
   Dengan bantuan alat seperti **BibTeX** atau **biblatex**, LaTeX memudahkan pengelolaan daftar pustaka.

5. **Komunitas Besar:**  
   Banyak sumber daya, template, dan paket ekstensi yang tersedia untuk memperluas fungsionalitas LaTeX.

#### **Kelebihan LaTeX:**
- Sangat cocok untuk dokumen teknis dan ilmiah.
- Mendukung dokumen panjang dengan banyak bagian, referensi silang, dan indeks.
- Kualitas output sangat baik.

#### **Editor LaTeX:**
Untuk menulis dan mengkompilasi dokumen LaTeX, Anda bisa menggunakan editor seperti:
- **Overleaf**: Editor berbasis web.
- **TeXstudio**: Editor lokal yang lengkap.
- **MikTeX** atau **TeX Live**: Distribusi LaTeX yang berisi semua alat pendukung.

---
### **MARKDOWN**
#### **Apa itu Markdown?**
Markdown adalah bahasa markup ringan yang diciptakan oleh John Gruber dan dirilis pada tahun 2004. Tujuannya adalah membuat proses penulisan dan format dokumen lebih mudah dengan sintaks yang sederhana dan intuitif. Markdown dirancang agar teks yang belum dirender tetap mudah dibaca, berbeda dari bahasa markup lain seperti HTML yang cenderung memiliki sintaks panjang dan kompleks.

#### **Kelebihan Markdown:**
Kesederhanaan: Sintaks Markdown sangat mudah dipelajari, bahkan bagi pemula.
Mudah Dibaca: Dokumen Markdown tetap mudah dibaca, bahkan tanpa dirender.
Portabilitas: Markdown dapat diubah menjadi berbagai format lain seperti HTML, PDF, atau dokumen Word.
Ringan: File Markdown biasanya berukuran kecil karena hanya berupa teks biasa.
Didukung Luas: Banyak platform seperti GitHub, GitLab, dan editor teks modern mendukung Markdown secara langsung.

Contoh Sintaks Markdown
markdown
Salin kode
# Judul Besar (H1)
## Sub Judul (H2)
### Sub-sub Judul (H3)

**Teks Tebal**

*Teks Miring*

- Item pertama
- Item kedua

1. Langkah pertama
2. Langkah kedua


`Kode inline`

```python
# Blok kode Python
print("Hello, world!")
Ini adalah blok kutipan.

markdown
Salin kode

### Contoh Alat Edit Markdown
Berikut beberapa alat yang bisa digunakan untuk membuat dan mengedit Markdown:

1. **Editor Teks**:
   - **Notepad++** (Windows): Mendukung sintaks Markdown.
   - **Visual Studio Code**: Memiliki ekstensi untuk pratinjau Markdown secara langsung.
   - **Sublime Text**: Menyediakan dukungan Markdown dengan plugin.

2. **Editor Markdown Khusus**:
   - **Typora**: Editor Markdown WYSIWYG (What You See Is What You Get) populer.
   - **Mark Text**: Editor Markdown gratis dan open-source dengan pratinjau langsung.
   - **Obsidian**: Cocok untuk membuat catatan berbasis Markdown dengan fitur pengelolaan graf.

3. **Alat Online**:
   - **Dillinger**: Editor Markdown berbasis web dengan pratinjau langsung.
   - **StackEdit**: Editor Markdown online dengan fitur integrasi cloud.
   - **HackMD**: Editor Markdown kolaboratif untuk bekerja secara bersama-sama.

Markdown fleksibel dan menjadi standar de facto untuk menulis dokumen teks sederhana dengan struktur yang rapi dan konsisten.
